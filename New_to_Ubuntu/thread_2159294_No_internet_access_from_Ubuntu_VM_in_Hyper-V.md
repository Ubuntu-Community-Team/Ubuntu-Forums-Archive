---
title: "No internet access from Ubuntu VM in Hyper-V"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by follerie on 2013-07-02
Hello,
I installed Ubuntu 12.04 as a VM under Hyper-V in windows 8 pro 64. The installation works fine the only problem being I have no wifi internet access. I didn't try direct cable connection but I really want wifi. I created the external virtual switch. My other windows VM easily connect to internet but when I repeat the same steps with Ubuntu, I have no luck. It is my first time using linux, may be I missed something obvious...

I don't know if that would be useful but I append below the output of ipconfig /all

Thank you for your help!

Microsoft Windows [version 6.2.9200]
(c) 2012 Microsoft Corporation. Tous droits réservés.


C:\WINDOWS\system32>ipconfig /all


Configuration IP de Windows


   Nom de l'hôte . . . . . . . . . . : ARCHIMEDE
   Suffixe DNS principal . . . . . . :
   Type de noeud. . . . . . . . . .  : Hybride
   Routage IP activé . . . . . . . . : Non
   Proxy WINS activé . . . . . . . . : Non


Carte Ethernet vEthernet (Nouveau commutateur virtuel pour Videotron) :


   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Carte Ethernet virtuelle Hyper-V #2
   Adresse physique . . . . . . . . . . . : 00-18-E7-D7-BA-84
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2002:b8a0:9b24:0:2419:b215:df42:1625
(préféré)
   Adresse IPv6 temporaire . . . . . . . .: 2002:b8a0:9b24:0:40b2:bbb2:e549:a871
(préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::2419:b215:df42:1625%43(préféré
)
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.1.106(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Bail obtenu. . . . . . . . . . . . . . : 30 juin 2013 12:13:11
   Bail expirant. . . . . . . . . . . . . : 3 juillet 2013 02:10:12
   Passerelle par défaut. . . . . . . . . : fe80::6a7f:74ff:fed5:fae2%43
                                       192.168.1.1
   Serveur DHCP . . . . . . . . . . . . . : 192.168.1.1
   IAID DHCPv6 . . . . . . . . . . . : 721426663
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-18-87-75-4E-00-18-E7-D7-BA
-84
   Serveurs DNS. . .  . . . . . . . . . . : 24.200.241.37
                                       24.201.245.77
                                       24.200.243.189
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé


Carte réseau sans fil Connexion au réseau local* 1 :


   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Carte virtuelle directe Wi-Fi Micros
oft
   Adresse physique . . . . . . . . . . . : 12-18-E7-D7-BA-84
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui


Carte Ethernet Ethernet :


   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Contrôleur Realtek PCIe GBE Family
   Adresse physique . . . . . . . . . . . : E0-CB-4E-5E-17-F9
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui


Carte Tunnel isatap.{2F833C66-F3D5-4CF9-88A7-1AD46D4B44FD} :


   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Carte Microsoft ISATAP
   Adresse physique . . . . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui


Carte Tunnel Connexion au réseau local* 13 :


   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Adresse physique . . . . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2001:0:9d38:6ab8:200a:30b:475f:64db(
préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::200a:30b:475f:64db%16(préféré)


   Passerelle par défaut. . . . . . . . . :
   NetBIOS sur TCPIP. . . . . . . . . . . : Désactivé


C:\WINDOWS\system32>

---

### Post by TheFu on 2013-07-02
I know absolutely NOTHING about v-whatever from Microsoft, but in all other VM hosts, you have to connect the network on the host PC to the specific network you'd like to use on the clientOS running inside the VM.  The clientOS doesn't see any of the real hardware, just the virtual network card that the V-whatever provides.  Usually, that is an Intel PRO/1000 NIC ... regardless of which actual connection the VM-host connects to the first ethernet card.

The actual hardware on the PC doesn't matter to the virtual environments.  If the wifi adapter is connected to the VM-client, then that will be used. No wifi drivers needed.

I hope that is clear.

---

