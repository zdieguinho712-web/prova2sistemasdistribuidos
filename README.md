# ETAPA-1-

foi editado a MAXIMO_SIMULTANEO = 2 
estava como 3 por isso o programa estava dando errado <img width="1152" height="864" alt="Captura de Tela (1)" src="https://github.com/user-attachments/assets/0c59a284-505a-454f-8011-e1cfee635bbd" />

EVIDENCIA 3 def processar_pedido(numero):
    with semafaro:
        time.sleep(0.1)
        with trava:
            if principal["online"] and principal["estoque"] > 0:
                principal["estoque"] -= 1
                pedidos_confirmados.append(numero)

                TOLERANCIA E FALHAS 

                === CENTRAL DE PEDIDOS ===
limite simultaneo: 2
estoque inicial: 10
pedidos confirmados: [101, 102, 103]
estoque principal: 7
replica antes: 10
replica depois: 7
Traceback (most recent call last):

<img width="1279" height="1023" alt="DD22" src="https://github.com/user-attachments/assets/1bbc1e72-631f-4240-a52b-d027e07a6bcd" />

EVIDENCIA 5 
<img width="1279" height="1017" alt="DD03" src="https://github.com/user-attachments/assets/882f365c-d6cd-424c-9f81-5146adf02054" />


                

                # Atualização imediata da réplica (replicação síncrona)
                if replica["online"]:
                    replica["estoque"] = principal["estoque"]<img width="1279" height="1023" alt="DD" src="https://github.com/user-attachments/assets/939e0d74-6d66-4c9f-88e4-01355b90bbed" />

                    qual e a funçao do semafaro no processo dos pedidos 
                    por que e necessario sincronizar os dados entre o servidor principal e a replica
                    o que significa tolerancias a falhas e como o controle de aceeso aos recursos ajuda a prewvinirt problemas de concorrencia 
                    
 Função do semáforo no processo de pedidos

O semáforo atua como um mecanismo de sincronização que controla quantos processos ou threads podem acessar um recurso compartilhado ao mesmo tempo.
• Na prática: Em um sistema de pedidos, se houver apenas 1 unidade de um produto em estoque e dois clientes tentarem comprar juntos, o semáforo garante que apenas um pedido processe a baixa no estoque por vez. O segundo pedido aguarda a liberação do primeiro, evitando que o mesmo item seja vendido duas vezes.

2. Por que sincronizar dados entre o servidor principal e a réplica?

A sincronização (replicação de dados) garante que a cópia de segurança (réplica) tenha exatamente as mesmas informações atualizadas que o servidor principal.
• Disponibilidade e continuidade: Se o servidor principal cair, a réplica assume imediatamente sem que o sistema pare ou perca pedidos recentes.
• Distribuição de carga: Permite dividir as consultas (como clientes visualizando o catálogo) entre vários servidores, deixando o servidor principal livre para processar novas vendas.

3. O que significa tolerância a falhas?

Tolerância a falhas é a capacidade de um sistema continuar operando normalmente (ou com perda mínima de desempenho) mesmo quando um ou mais de seus componentes físicos ou de software falham.
• Exemplo: Se um disco rígido queimar, a energia cair em um servidor ou a rede oscilar, o sistema redireciona automaticamente o tráfego para servidores saudáveis e mantém o serviço no ar para o usuário final.

4. Como o controle de acesso previne problemas de concorrência?

O controle de acesso (por meio de bloqueios/locks, filas ou semáforos) impõe uma ordem na leitura e escrita de dados compartilhados, evitando que múltiplos processos alterem a mesma informação simultaneamente de forma desordenada.

