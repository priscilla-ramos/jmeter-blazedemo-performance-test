# Teste de Performance – BlazeDemo

## Objetivo

Avaliar o desempenho do fluxo de compra de passagens do BlazeDemo
sob carga constante, com objetivo de atingir até \*\*250 requisições por segundo\*\*
e verificar se o \*\*P90 (90th percentile) permanece abaixo de 2 segundos\*\*.

## Ferramentas

- Apache JMeter 5.6.3

- Execução em modo non-GUI (CLI)

- Relatório HTML nativo do JMeter

## Cenário Testado

Fluxo completo de compra de passagens:

1. Acesso à Home

2. Busca de Voos

3. Compra de Passagem

4. Confirmação da Compra

## Configuração do Teste

- Threads (usuários virtuais): 200

- Ramp-up: 60 segundos

- Duração: 5 minutos (controlada via Scheduler do Thread Group)

- Constant Throughput Timer: 15000 samples/min

- Valor equivalente a \~250 requisições por segundo

## Execução

O teste foi executado em modo non-GUI, garantindo menor consumo de recursos
e maior precisão nos resultados.  
A duração foi controlada automaticamente por meio do \*\*Specify Thread lifetime\*\*
do Thread Group, assegurando reprodutibilidade.

## Resultados

- Throughput médio: \*\*157,52 req/s\*\*

- P90 (90% Line): \*\*1386,90 ms\*\*

- Taxa de erro: \*\*0,12%\*\*

## Análise dos Resultados

- O critério de \*\*latência (P90 < 2s)\*\* foi \*\*atendido\*\*, indicando bom tempo
de resposta para a maioria das requisições mesmo sob carga.

- O critério de \*\*vazão (250 req/s)\*\* não foi atingido. A aplicação sustentou
aproximadamente 157 req/s durante o período de teste.

- A taxa de erro permaneceu baixa, sugerindo boa estabilidade durante a execução.

## Conclusão

O teste demonstrou que, embora a aplicação BlazeDemo apresente tempos de resposta
adequados sob carga constante, ela não conseguiu sustentar a vazão alvo de
250 requisições por segundo, atingindo seu limite de capacidade antes desse ponto.
Considerando que o BlazeDemo é uma aplicação de demonstração e não projetada
para cenários de alta concorrência em ambiente produtivo, o comportamento observado
é esperado e fornece uma boa referência dos limites de desempenho do sistema.



