# Bootcamp-Santander-Code-Girls-2025
Desafios desenvolvidos durante o curso de preparação para certificação AWS Cloud Practitioner do bootcamp Santander Code Girls 2025.

# Desafio Gerenciamento de Instâncias AWS EC2

## Amazon EC2: Infraestrutura como Serviço (IaaS)

O Amazon EC2 (Elastic Compute Cloud) é o serviço fundamental da AWS que oferece capacidade de computação redimensionável na nuvem.

* **EC2 como IaaS:** O EC2 é um tipo de **Infraestrutura como Serviço (IaaS)**. Isso significa que a AWS fornece o hardware, a rede e a virtualização (a infraestrutura subjacente), mas o **usuário-cliente** é responsável pela configuração, pelo sistema operacional, aplicações, e segurança na camada de software.
* **Modelo de Responsabilidade Compartilhada:**
    * **Responsabilidade da AWS (Segurança *da* Nuvem):** Manter a infraestrutura global, hardware, rede, e a segurança física.
    * **Responsabilidade do Cliente (Segurança *na* Nuvem):** Configurar o sistema operacional, *patches*, *firewall* (Security Groups), IAM, e os dados armazenados.

### Tipos de Instâncias EC2 (Otimização de Hardware)

É crucial entender a **necessidade da aplicação** para escolher o tipo de instância correto, otimizando desempenho e custo:

| Família de Instâncias | Otimizado Para | Exemplo de Uso |
| :--- | :--- | :--- |
| **Geral (M, T)** | Uso equilibrado de CPU, memória e rede. | Servidores web, aplicações de pequeno porte. |
| **Computação (C)** | Processamento intensivo (alta performance de CPU). | Servidores de jogos, *batch processing* e *data analysis*. |
| **Memória (R)** | Cargas de trabalho que consomem muita RAM. | Bancos de dados de alto desempenho, caches distribuídos. |

## **Otimização de Recursos e Custos**

### **Otimização de Instâncias EC2**

A gestão de custos envolve a correspondência do consumo com a capacidade real, evitando desperdício:

* **Monitoramento:** Utilizar o CloudWatch para monitorar a utilização da CPU e RAM.
* ***Right-Sizing* (Dimensionamento Correto):** Se a CPU da instância estiver consistentemente baixa (ex: menos de 10%), é recomendado fazer o *down-sizing* (diminuir a classe) para uma instância menor (Ex: de `m5.large` para `t3.medium`).
* **Desligamento (Stopped) Agendado:** Para ambientes de teste e desenvolvimento, as instâncias devem ser **desligadas automaticamente** fora do horário comercial, pois o cliente só é cobrado pelo tempo em que a instância está no estado **Running** (executando).

## **Estratégias de Armazenamento na Nuvem**

### **AWS EBS (Elastic Block Store)**

* **Natureza:** Armazenamento em **bloco** (semelhante a um disco rígido ou SSD local) que deve ser **anexado** a uma instância EC2.
* **Uso:** É ideal para o **disco raiz (boot)** e para volumes que requerem baixa latência e persistência (como volumes de dados para bancos de dados).
* **Snapshots EBS:** Um **Snapshot** é uma cópia de segurança pontual (point-in-time) do seu volume EBS, armazenada de forma durável no S3. Snapshots são essenciais para backup, recuperação de desastres e para migrar dados entre volumes ou regiões.

### **Amazon S3 (Simple Storage Service)**

* **Natureza:** Armazenamento de **objetos** (arquivos), projetado para ser massivamente escalável e de alta disponibilidade.
* **Uso:** É ideal para arquivos estáticos, backups de longo prazo, *logs* e arquivos de mídia. **Não pode ser usado** para instalar sistemas operacionais ou bancos de dados que exigem acesso em bloco.

Link de apoio: https://docs.aws.amazon.com/pt_br/toolkit-for-visual-studio/latest/user-guide/tkv-ec2-ami.html
