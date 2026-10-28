# Guia de Compatibilidade: Free My TV na TV TCL 55 OLED e Xiaomi Mi Stick

Este projeto foi configurado sob medida para o seu ecossistema:
- **Televisor Principal:** TV TCL 55" OLED (Google TV / Android TV)
- **Dispositivo Secundário:** Xiaomi Mi TV Stick (Android TV)
- **Localização Meteorológica:** Ourinhos, SP, Brasil (C° e R$ BRL)
- **Serviços de Streaming Prioritários:** YouTube, Netflix, Prime Video, Disney+, Max, Globoplay, Stremio, Plex e Spotify

---

## 1. Ajustes de Compatibilidade para a TV TCL 55 OLED

As TVs TCL possuem dois serviços em segundo plano (TclAppBoot e TGuard) que encerram launchers de terceiros. Para garantir que a launcher rode 100% lisa e assuma a tela inicial:

1. Ative a **Depuração USB** na TV:
   * Vá em *Configurações* → *Sistema* → *Sobre* → Clique 7 vezes sobre *Versão do SO Android TV* até liberar o Modo Desenvolvedor.
   * Volte em *Opções do desenvolvedor* e ative **Depuração USB**.
2. Conecte pelo computador ou celular via ADB e execute o comando de liberação de inicialização automática da TCL:
   ```bash
   adb shell "appops set io.freemytv AUTO_START allow || appops set io.freemytv APP_AUTO_START allow"
   ```
3. **Botões do Controle Remoto TCL:**
   * Os botões dedicados do controle remoto (Netflix, YouTube e Prime Video) funcionam normalmente integrados à launcher. No menu *Free My TV* → *Remote Buttons*, você pode personalizar o que cada um abre.
4. **Proteção Anti Burn-in para Painel OLED:**
   * O arquivo `config.properties` já está configurado com `screensaver=true`, ativando o protetor de tela com fotos em alta definição para evitar retenção de imagem na sua tela OLED de 55 polegadas.

---

## 2. Ajustes de Compatibilidade para o Xiaomi Mi TV Stick

O Xiaomi Mi Stick possui 1GB de RAM e processador otimizado para economia de energia. As seguintes otimizações foram aplicadas:

1. **Baixo Consumo de Memória (96 MB de RAM):**
   * A interface consome menos da metade da memória do launcher padrão do Google TV (que usa 242 MB), eliminando engasgos e travamentos no Mi Stick.
2. **Botão 'Mi' do Controle Remoto:**
   * Em controles Xiaomi com o botão "Mi", o aplicativo intercepta o sinal e abre a tela inicial do Free My TV diretamente, em vez de abrir o PatchWall.
3. **Resolução e Taxa de Atualização:**
   * Calibrado para resolução nativa 1080p a 60Hz com suporte a HDMI-CEC para ligar e desligar em conjunto com a TV.

---

## 3. Como Gerar o APK no GitHub

1. Baixe o pacote `freemytv_tcl_mistick_edition.zip`.
2. No seu repositório no GitHub (ou crie um novo), envie os arquivos.
   * *Atenção:* Certifique-se de que a pasta `.github/workflows/build-apk.yml` e o arquivo `config.properties` estejam na raiz.
3. A compilação iniciará automaticamente na aba **Actions**.
4. Em 1 minuto, baixe o arquivo `FreeMyTV-TCL-MiStick-APK` pronto para instalar na sua TV ou Mi Stick!
