<properties
   pageTitle="Introdução ao Azure Container Service | Microsoft Azure"
   description="Azure Container Service (ACS) fornece um meio de simplificar a criação, configuração e gerenciamento de um cluster de máquinas virtuais que estão pré-configuradas para executar aplicações conteinerizadas."
   services="container-service"
   documentationCenter=""
   authors="rgardler"
   manager="timlt"
   editor=""
   tags="acs, azure-container-service"
   keywords="Docker, Containers, Micro-services, Mesos, Azure"/>
   
<tags
   ms.service="container-service"
   ms.devlang="na"
   ms.topic="article"
   ms.tgt_pltfrm="na"
   ms.workload="na"
   ms.date="02/16/2016"
   ms.author="rogardle"/>

# Introdução ao Azure Container Service

Azure Container Service (ACS) fornece um meio de simplificar a criação, configuração e gerenciamento de um cluster de máquinas virtuais que estão pré-configuradas para executar aplicações containerizadas. Usando uma configuração otimizada de uma popular ferramenta open-source de agendamento e orquestração, ACS habilita você a usar suas habilidades ou basear-se em conhecimentos de uma crescente comunidade para publicar e gerenciar aplicações baseadas em containers no Microsoft Azure.

<br />
![ACS fornece um meio de gerenciar aplicações em containers em vários tipos de hospedagem no Azure.](./media/acs-intro/acs-cluster.png)
<br /><br />

ACS aproveita o Docker para garantir que os containers da sua aplicação são totalmente portáveis. Ele também suporta sua escolha entre Marathon, Chronos e Apache Mesos ou Docker Swarm para garantir que essas aplicações podem escalar para milhares, ou até mesmo centenas de milhares de containers.

O Azure Container Service permite que você a tire vantagem 
dos recursos corporativos do Azure mantendo aplicação, portabilidade, 
inclusive nas camadas de orquestração.

Utilizando o Azure Container Service
-----------------------------

Nosso objetivo com o Azure Container Service é fornecer um ambiente 
para hospedagem de containers, usando ferramentas e tecnologias 
open sourse, que são populares aos clientes hoje em dia. 
Para isto, nós expomos os endpoints padrões das API's
para o Docker e o orquestrador de sua escolha. 
Usando estes endpoints você pode utilizar qualquer software que seja capaz
de falar com estes endpoints. Por exemplo, no caso do endpoint do Docker 
Swarm você pode usar Docker Compose, enquanto para Apache Mesos você pode
escolher utilizar o CLI DCOS.

Criando um cluster Docker usando Azure Container Service
-------------------------------------------------------

Para começar a utilizar o Azure Container Sercice, um cluster ACS será publicado usando um template Azure Resource Manager. Este deployment pode ser configurado com diferentes tamanhos e opções de disponibilidade, e será configurado com Apache Mesos ou Docker Swarm.
Templates do Azure Resource Manager podem ser publicados através de portas do Azure, usando CLI do Azure, ou PowerShell. Os templates também podem ser alterados para incluir configurações avançadas ou adicionais. Para mais informações sobre publicações de cluster ACS, veja [Publicando um cluster no Azure Container Service](./container-service-deployment.md).

Publicando uma aplicação
------------------------

Durante a avaliação nós fornecemos uma escolha de Docker Swarm ou
Apache Mesos (com DCOS Marathon e frameworks DCOS Chronos) para orquestração. 

### Usando o Apache Mesos

Apache Mesos é um projeto open source hospedado na Apache Software 
Foundation. Ela lista alguns do maiores nomes (http://mesos.apache.org/documentation/latest/powered-by-mesos/) 
como usuários e colaboradores.

![ACS configurado para Swarm exibindo agentes e mestres.](media/acs-intro/acs-mesos.png)

Mesos empacota um conjunto impressionante de características.

-   Escalabilidade para 10.000 nós

-   Tolerância à falhas replicadas em master e slaves usando ZooKeeper

-   Suporte para containers Docker

-   Isolamento nativo entre tarefas com containers Linux

-   Agendamento multi recurso (memória, CPU, disco, e portas)

-   APIs em Java, Python e C++ para desenvolvimento de novas aplicações paralelas

-   Interface de Usuário Web para visualização do estado do cluster

Mesos possui suporte a um vasto número de 
[frameworks](http://mesos.apache.org/documentation/latest/frameworks/)
que podem ser usados para agendar processamento no Azure Container
Service. Por padrão, ACS inclui frameworks Marathon e Chronos.

#### Usando Marathon e Chronos

Marathon é um cluster de inicialização e controle de sistema para
serviços e cgroups ou, no caso do ACS, containers Docker. Ele um parceiro
ideal ao Chronos, um agendador de tarefas com tolerância à falhas para Mesos
que controla dependências e agendamentos de horários.

Marathon e Chrones fornecem uma interface Web para você publicar suas
aplicações. Você pode acessá-lo usando uma URL parecida com
`http://PREFIXO\_DNS.REGIAO.cloudapp.azure.com`
onde PREFIXO\_DNS e REGIAO são ambos definidos em tempo de publicação. 
Naturalmente, você também pode fornecer seu próprio nome DNS. Para mais informações sobre executar um container usando a interface web Marathon, veja [Gerenciamento de container utilizando interface web](./container-service-mesos-marathon-ui.md).

Você também pode usar APIs REST para se comunicar com Marathon e Chronos.
Existem diversas bibliotecas clientes disponíveis para cada ferramenta,
cobriando uma variedade de linguagens e, naturalmente, você pode usar o 
protocolo HTTP em qualquer linguagem. Além disso, diversas ferramentas 
DevOps fornecem suporte para estes agendadores. Isso fornece maior
flexibilidade para seu time de operações ao trabalhar com um cluster ACS.
Para mais informações sobre executar um container usando REST API do Marathon, veja [Gerenciamento de Container com REST API](./container-service-mesos-marathon-rest.md).

### Usando Docker Swarm

Docker Swarm fornece clusterização nativa para Docker. Como Docker Swarm
serve a API Docker padrão, qualquer ferramenta que já se comunica com
um daemon Docker pode usar Swarm para dimensionar de forma transparente para vários hosts
no Azure Container Service.

![ACS configurado para usar Apache Mesos, exibindo jumpbox, agentes e masters.](media/acs-intro/acs-swarm.png)

Ferramentas suportadas para gerenciar containers em um cluester Swarm incluem, mas não estão limitadas, às seguintes:

-   Dokku

-   Docker CLI e Docker Compose

-   Krane

-   Jenkins

Videos
------
Anúncio AzureCon:

> [AZURE.VIDEO azurecon-2015-deep-dive-on-the-azure-container-service-with-mesos]  

Começando com ACS:  

> [AZURE.VIDEO connect-2015-getting-started-developing-with-docker-and-azure-container-service]
