---
title: "Disable Anonymous Mode In PROFTPD"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by guillaumesoucy on 2013-10-05
Hi, 

How I can disable the Anonymous mode of the PROFTPD Ftp server? I cannot login. 

Please see the log. 

Statut :    Connexion à 192.168.2.22:21...
Statut :    Connexion établie, attente du message d'accueil...
Réponse :    220 Zawack
Commande :    USER guillaumesoucy1
Réponse :    331 Password required for guillaumesoucy1
Commande :    PASS ************
Réponse :    230 Anonymous access granted, restrictions apply
Commande :    SYST
Réponse :    215 UNIX Type: L8
Commande :    FEAT
Réponse :    211-Features:
Réponse :     MDTM
Réponse :     MFMT
Réponse :     LANG zh-CN.UTF-8;zh-CN;en-US.UTF-8;en-US;fr-FR.UTF-8;fr-FR
Réponse :     TVFS
Réponse :     UTF8
Réponse :     MFF modify;UNIX.group;UNIX.mode;
Réponse :     MLST modify*;perm*;size*;type*;unique*;UNIX.group*;UNIX.mode*;UNIX.owner*;
Réponse :     REST STREAM
Réponse :     SIZE
Réponse :    211 End
Commande :    OPTS UTF8 ON
Réponse :    200 UTF8 set to on
Statut :    Connecté
Statut :    Récupération du contenu du dossier...
Commande :    PWD
Réponse :    257 "/" is the current directory
Commande :    TYPE I
Réponse :    200 Type set to I
Commande :    PASV
Réponse :    227 Entering Passive Mode (192,168,2,22,203,18).
Commande :    MLSD
Erreur :    Connexion interrompue par le serveur
Erreur :    Impossible de récupérer le contenu du dossier

I need help, I dont know what do with that. 

Thanks in advance. 

Guillaume

---

### Post by Kevin McCready on 2013-10-06
An advanced seach on this forum for titles only containing: anonymous PROFTPD
gives
[http://ubuntuforums.org/search.php?searchid=1024740](http://ubuntuforums.org/search.php?searchid=1024740)

---

### Post by guillaumesoucy on 2013-10-06
Hi, 

I make a search but I understand nothing.

This is the config file. 

> ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.2.22"
ServerIdent on "Zawack"
ServerAdmin [email]email@example.org[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49155 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 999999
MaxLoginAttempts 9999
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 999999
TransferRate STOR 999999
TransferRate STOU 999999
TransferRate APPE 999999
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
TLSOptions AllowClientRenegotiation
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser guillaumesoucy1
  DenyALL
</Limit>

<Anonymous /home/FTP-shared>
User guillaumesoucy1
Group ftp
AnonRequirePassword on
MaxClients 999999 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayChdir .msg
<Limit LOGIN>
Allow from All
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Global>
AllowStoreRestart on
MaxClients none
MaxClientsPerHost none
MaxLoginAttempts 999999
</Global>

Whats wrong with it?

Guillaume

---

### Post by Kevin McCready on 2013-10-08
Would it be useful to check /var/log/proftpd_tls.log

---

