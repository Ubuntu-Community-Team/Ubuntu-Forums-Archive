---
title: "DVD/CD drive"
date: 2017-12-14
forum: Portugal Team
---

### Post by aelico on 2017-12-14
A minha drive de dvd não toca cds de música.
Alguma dica? Obrigado.
António Lico

---

### Post by lapis on 2017-12-14
> **aelico said:**
> A minha drive de dvd não toca cds de música.
Alguma dica? Obrigado.
António Lico

A drive tem um botão para tocar os cd's ou não consegues usar um programa para tocar as músicas? Ela reconhece os CD's? Quando colocas um CD na drive o que acontece? Tens o volume de som num valor audivel?

---

### Post by slickymaster on 2017-12-14
O pacote **ubuntu-restricted-extras** existe no sistema?

Qual é o retorno obtido correndo num terminal o comando ```
apt-cache policy ubuntu-restricted-extras
```

---

### Post by aelico on 2017-12-14
Obrigado.
Este é o retorno dado no terminal:
```
aelico@aelico-HP-G56-Notebook-PC:~$ apt-cache policy ubuntu-restricted-extras
ubuntu-restricted-extras:
  Instalado: (nenhum)
  Candidato: 66
  Tabela de Versão:
     66 500
        500 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) artful/multiverse amd64 Packages
```

---

### Post by aelico on 2017-12-14
Obrigado.
Não acontece nada. A drive existe, mas não reconhece os CD's.

---

### Post by slickymaster on 2017-12-14
Ainda no terminal, qual é o retorno obtido de```
lsb_release -a && uname -r
```

Por favor, cole o resultado obtido entre tags de código: [ code] ...output...[ /code ] sem os espaços dentro dos parênteses rectos. Link a consultar em caso de dúvidas: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by aelico on 2017-12-14
> **slickymaster said:**
> Ainda no terminal, qual é o retorno obtido de```
lsb_release -a && uname -r
```

Por favor, cole o resultado obtido entre tags de código: ```
...output...
``` Link a consultar em caso de dúvidas: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)
```
aelico@aelico-HP-G56-Notebook-PC:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful
4.13.0-19-generic
```

---

### Post by slickymaster on 2017-12-14
Assumindo que a distribuição em causa é o Ubuntu regular, no terminal executar```
sudo apt update && sudo apt install ubuntu-restricted-extras
```Caso a distribuição usada seja o Xubuntu, então executar```
sudo apt update && sudo apt install xubuntu-restricted-extras
```Se for o Lubuntu```
sudo apt update && sudo apt install lubuntu-restricted-extras
```No caso de ser Kubuntu```
sudo apt update && sudo apt install kubuntu-restricted-extras
```

---

### Post by aelico on 2017-12-14
> **slickymaster said:**
> Assumindo que a distribuição em causa é o Ubuntu regular, no terminal executar```
sudo apt update && sudo apt install ubuntu-restricted-extras
```Caso a distribuição usada seja o Xubuntu, então executar```
sudo apt update && sudo apt install xubuntu-restricted-extras
```Se for o Lubuntu```
sudo apt update && sudo apt install lubuntu-restricted-extras
```No caso de ser Kubuntu```
sudo apt update && sudo apt install kubuntu-restricted-extras
```

Obrigado pela ajuda. Estou a proceder à execução.

---

### Post by aelico on 2017-12-25
> **aelico said:**
> Obrigado pela ajuda. Estou a proceder à execução.

Por manifesta falta de tempo em virtude de ter saído para fora, não me foi possível referir o andamento da resolução do problema que aqui apresentei, e pelo qu pço desculpa.
Como disse procedi como me foi referido, mas o problema não foi resolvido. Pode ser que seja algo relacionado com o firmware, ou qualquer outra coisa...
Obrigado pela ajuda recebida, e mais uma vez apresento as minhas desculpas pelo atraso em referir o resultado.
Votos de Boas Festas para todos os membros do Forum.
António Lico.

---

### Post by slickymaster on 2017-12-27
Se se tratar de um problema de firmware, por favor verificar em [http://binflash.cdfreaks.com/](http://binflash.cdfreaks.com/) se o seu drive está lá listado. Caso esteja o problema poderá ser resolvido.

---

