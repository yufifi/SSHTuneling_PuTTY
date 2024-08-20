# Configurando um Túnel SSH com PuTTY e FoxyProxy no Windows 11
Este guia fornece instruções passo a passo para configurar um túnel SSH usando PuTTY no Windows 11 e configurar o FoxyProxy para redirecionar o tráfego da web pelo túnel SSH.

<div align="center">
    <img src="https://e7.pngegg.com/pngimages/504/729/png-clipart-internet-logo-putty-icon-icons-logos-emojis-tech-companies-thumbnail.png" alt="logo do PuTTY">
</div>

--- 
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes itens:

Uma VM configurada na Oracle Cloud (ou outro serviço de hospedagem).
Chave SSH privada (.ppk) configurada para acesso à VM.
PuTTY instalado no seu Windows 11. Baixar PuTTY.
Extensão FoxyProxy instalada no seu navegador (Firefox ou Chrome).
Passo 1: Converter a Chave SSH (Se necessário)
Caso sua chave SSH esteja em formato OpenSSH (.pem), você precisará convertê-la para o formato .ppk usado pelo PuTTY.

Abra o PuTTYgen (parte da instalação do PuTTY).
Clique em Load e selecione sua chave privada (.pem).
Clique em Save private key para salvar a chave no formato .ppk.
Captura de Tela: [Inserir captura de tela da interface do PuTTYgen]

Passo 2: Configurar o PuTTY
Abra o PuTTY.

No campo Host Name (or IP address), insira o endereço IP público da sua VM.

No campo Port, insira 22.

Em Connection type, selecione SSH.

Captura de Tela: [Inserir captura de tela da interface principal do PuTTY]

Configurar o Túnel SSH
No menu à esquerda, expanda Connection > SSH > Tunnels.

Em Source port, insira 9999.

Selecione Dynamic e Auto.

Clique em Add.

No menu à esquerda, vá para Connection > SSH > Auth e clique em Browse para selecionar sua chave privada .ppk.

Volte para o menu Session, dê um nome para sua sessão em Saved Sessions (por exemplo, OracleCloudSSH) e clique em Save.

Clique em Open para iniciar a conexão SSH.

Captura de Tela: [Inserir captura de tela da configuração de túnel no PuTTY]

Passo 3: Configurar o FoxyProxy
Abra o navegador e acesse as configurações do FoxyProxy.

Adicione um novo proxy com as seguintes configurações:

Nome: SSH Proxy
Tipo de Proxy: SOCKS5
Host: localhost
Porta: 9999
Salve a configuração e ative o proxy.

Captura de Tela: [Inserir captura de tela da configuração do FoxyProxy]

Passo 4: Testar a Conexão
Abra o navegador com o FoxyProxy ativo.
Navegue em um site de verificação de IP, como whatismyip.com, para verificar se o seu tráfego está sendo redirecionado pela VM da Oracle Cloud.
Captura de Tela: [Inserir captura de tela mostrando o IP alterado]

Passo 5: Configurar o Sistema para Usar o Túnel (Opcional)
Caso deseje que outros aplicativos, como o Steam, utilizem o túnel SSH, configure as definições de proxy no Windows:

Abra Configurações > Rede e Internet > Proxy.

Em Configuração manual de proxy, ative a opção e insira:

Endereço: localhost
Porta: 9999
Salve as alterações.

Captura de Tela: [Inserir captura de tela das configurações de proxy no Windows]
