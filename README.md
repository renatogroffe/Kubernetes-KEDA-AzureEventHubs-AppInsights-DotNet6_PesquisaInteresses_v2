# Kubernetes-KEDA-AzureEventHubs-AppInsights-DotNet6_PesquisaInteresses_v2
Objetos para Deployment de um Worker Service (apuração de votos sobre interesses pessoais) no Kubernetes utilizando KEDA + Azure Event Hubs, Helm, monitoramento com Azure Application Insights e .NET 6.

Worker Service para consumo de **mensagens vinculadas a um Event Hub/Tópico do Azure Event Hubs** (imagem **renatogroffe/worker-pesquisainteresses-appinsightsconnstring-dotnet6:latest**) - é justamente esta aplicação que será escalada via **KEDA**:

**https://github.com/renatogroffe/DotNet6-Worker-AzureEventHubs-SqlServer-Dapper-AppInsightsConnString-Processor_PesquisaInteresses**

Projeto que serviu de base para o **envio de mensagens a um Event Hub/Tópico do Azure Event Hubs** (imagem **renatogroffe/sitepesquisainteresses-eventhubs-appinsightsconnstring-dotnet6:latest**):

**https://github.com/renatogroffe/ASPNETCore6-MVC-AzureEventHubs-AppInsightsConnString_SitePesquisaInteresses**

No arquivo **keda-instalacao&sdot;sh** estão as instruções para instalação do KEDA **(Kubernetes Event-driven Autoscaling)** em um **cluster Kubernetes**.

Para os testes de carga que escalam a aplicação utilizei o pacote npm [**loadtest**](https://www.npmjs.com/package/loadtest). O exemplo a seguir procederá com o envio de **5 mil requisições**, simulando **70 usuários concorrentes**:

**loadtest -c 70 -n 5000 -k** ***ENDPOINT***

E o Pipeline a seguir (Azure DevOps) com a execução de testes randômicos com a ferramenta **k6**:

**https://github.com/renatogroffe/k6-LoadTests-Reports-AzureDevOps_VotacaoPesquisaInteresses**