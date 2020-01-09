# projeto Marco Civil para Provedores de Aplicacões
Este é um projeto colaborativo com informações e tutoriais de como implementar a Lei 12965/2014 - Marco Civil em servidores brasileiros, em diferentes servicos

Sinta-se a vontade para realizar um fork e enviar pull requests, iremos adicionar novos tutoriais aqui na medida em que forem surgindo

O conteúdo é de livre distribuição, apenas pedimos que cite o endereço do github de nosso projeto original https://github.com/underinternet/marcocivil/ para que o público possa se atualizar

Caso queira discutir algum ponto dessa FAQ ou do projeto participe de nosso grupo de discussões
https://groups.google.com/forum/#!forum/marco-civil-aplicacoes


# FAQ Marco Civil para Provedores de Aplicacões

## para quem é esse projeto no github?
para quem gerencia um servidor, seja físico ou virtual ou até mesmo para quem cria aplicações de internet

## quem deve guardar o log?
* se você contratou uma hospedagem compartilhada, a princípio seu provedor vai guardar os logs, exceto se você subir um serviço em uma porta que não passe pelo servidor web (apache, nginx, IIS)

* se você contratou um servidor virtual / cloud ou um servidor dedicado em uma nuvem, como a da Under (www.under.com.br), AWS, Google Cloud, etc, então você mesmo deve configurar seu servidor para guardar os logs corretamente

* se você contratou um servidor 100% gerenciado, no qual você não possui acesso root / administrator, então provavelmente seu fornecedor de gerenciamento irá configurar a guarda de logs por você

## quanto tempo tenho que guardar os logs?
* o prazo para guarda de logs é de 6 meses, conforme a Lei 12965 artigo 15. 
* recomendamos guardar por até 12 meses

## se migrar servidor para outro preciso guardar logs?
* sim

## devo realizar backup dos logs também?
* sim, pois o artigo 15 fala em guardar em ambiente seguro

## é preferível guardar os logs fora do servidor?
* sim, pois assim separa as funções do servidor, como no caso de servidor virtual stateless, na qual se deseja aumentar ou reduzir o número de vms, ou então para não precisar realizar backup do servidor em vm stateless. Podemos sugerir algumas técnicas como
  * enviar os logs para storage NAS (NFS, CIFS)
  * utilizar um concentrador de logs como o Elasticsearch
  * enviar os logs periodicamente para Object Storage

## quais informações tem que constar nos logs?
* data e qual timezone
* IP de origem, assim a justiça poderá identificar qual é o usuário 
* porta de origem (porta que foi usada do lado do usuário), assim a justiça poderá identificar qual é o usuário
* qual conteúdo o usuário acessou, exemplo, no caso de HTTP (https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) qual o hostname (https://en.wikipedia.org/wiki/Hostname) e a URI (https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)
* opcionalmente podemos constar o Protocolo (https://en.wikipedia.org/wiki/Transport_layer) (UDP/TCP) e a porta de destino, caso isso seja relevante

## quais informações não podem constar nos logs?
* no art 16 da lei, diz que não podemos guardar logs de saída, ou seja, o que a aplicação acessa em outras aplicações de internet, ou de dados pessoais dos usuários


## como aumento o tempo de guarda de logs do sistema operacional?
* No linux você deve configurar o logrotate
* No windows server você deve configurar o event viewer para não apagar os logs

## onde encontro os tutoriais
* Cada arquivo txt é um tutorial para um serviço. Iniciaremos com os serviços mais comuns como Apache, Nginx, IIS, etc, e iremos adicionando novos serviços na medida em que o projeto for crescendo ou recebamos colaborações.

