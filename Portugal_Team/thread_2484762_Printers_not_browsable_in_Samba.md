---
title: "Printers not browsable in Samba"
date: 2023-03-09
forum: Portugal Team
---

### Post by evaristorocha on 2023-03-09
Na saida do comando testparm esta assim:
[printers]
        browseable = No
        comment = Compartilhamento de Impressoras
        path = /var/spool/samba
        printable = Yes

Mas no arquivo de configuração esta dessa forma:
[printers]
   comment = Compartilhamento de Impressoras
   path = /var/spool/samba
   printable = yes
   ;guest ok = no
   ;read only = yes
   ;create mask = 0700
   browseable = Yes

Este problema impede a visualização das impressoras instaladas no cups, algue pode me ajudar com isso? Versão do SO: Ubuntu 22.04.2 Versão do Samba-4.15.13

---

### Post by slickymaster on 2023-03-09
*Thread moved to **Portugal Team**.*

---

### Post by evaristorocha on 2023-03-10
Good Monrning! slickymaster
thanks for the guidance, I have no experience with forum

---

### Post by slickymaster on 2023-03-10
O meu conselho seria iniciar uma nova thread, relativamente ao seu problema, em inglês no seguinte sub-forum: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331)

O fórum da equipa de Portugal está praticamente sem tráfego nos últimos anos.

---

### Post by evaristorocha on 2023-03-15
Thanks! Slickymaster. I managed to identify a solution, when I restarted samba via daemon the printers did not appear because the browseable parameter always appears as No in the testparm output, however, when I executed the command "smbcontrol all reload-config" the printers appear.

---

