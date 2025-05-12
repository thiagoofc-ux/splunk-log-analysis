# splunk-log-analysis
 Projeto de Análise de Logs com Splunk para Segurança da Informação.

Este projeto simula a análise de logs utilizando o Splunk, com foco em segurança da informação. A ideia é demonstrar como detectar comportamentos suspeitos através da visualização de dados e criação de alertas com o Splunk.

## Objetivo

- Coletar logs (Apache, SSH, Windows Event Logs)
- Criar dashboards para monitoramento
- Detectar comportamentos suspeitos (ex: múltiplas falhas de login, acessos fora do horário)
- Aprender na prática como utilizar o Splunk em cenários de segurança

## Estrutura do Projeto

splunk-log-analysis/
dashboards/ # Dashboards criados no Splunk (com screenshots)
queries/ # Queries de detecção (SPL - Search Processing Language)
logs/ # Exemplos de logs utilizados
setup/ # Instruções para instalação do ambiente


## Requisitos

- Splunk Free ou Splunk Cloud Trial
- Máquina com Windows/Linux para gerar logs
- Navegador moderno

## Como Usar

1. Instale o Splunk seguindo as instruções em `setup/splunk_install.md`
2. Faça upload dos logs da pasta `logs/` no Splunk
3. Importe ou recrie os dashboards com base nas imagens em `dashboards/screenshots/`
4. Use os arquivos em `queries/` para explorar os dados

## Dashboards Criados

- Falhas de login por IP
- Acessos por horário
- Requisições suspeitas no Apache
- Usuários com muitos acessos em curto tempo

## Queries SPL de Exemplo

```spl
index=main sourcetype=access_combined status=404
| stats count by clientip, uri_path
| sort -count
