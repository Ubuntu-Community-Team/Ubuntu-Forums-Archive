---
title: "Usuario FTP con acceso de visualizacion solo a su HOME"
date: 2022-04-01
forum: New to Ubuntu
---

### Post by eschwartzo on 2022-04-01
[COLOR=#1A1A1A][FONT=&amp]Estimados, permitanme una consulta, instale vsftpd en ubuntu server, y luego estuve creando unos usuarios para acceso FTP de esta manera: (lo encontre en una pagina web)
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]sudo adduser --home /home/usuario usuario[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]sudo passwd usuario[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]sudo chown usuario:usuario -R /home/usuario/[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]sudo echo "usuario" | sudo tee -a /etc/vsftpd.userlist[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]sudo systemctl restart vsftpd[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=&amp]he generado varios usuarios asi (usuario, usuario 1, usuario2)[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]pero lo que no he podido es hacer que cada usuario solo tenga acceso de visualizacion a su propio directorio, si bien es cierto cada usuario solo puede grabar archivos dentro de su home, lo que he podido observar es que al acceder con un cliente como filezilla este puede subir de nivel de directorio y ver los demas directorios HOME de los demas usuarios, incluso pueden subir de nivel hasta ver los directorios /etc/ y demas directorios.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]como podria hacer para evitar que esto suceda y que al acceder cada usuario a traves de algun cliente ftp solo tenga acceso a su home directory no pueda subir a un nivel superior de directorios.
[/FONT][/COLOR]o alguna manera de crear los usuarios de una manera distinta que me permita hacer esto?

[COLOR=#1A1A1A][FONT=&amp]Datos: Ubuntu Server 20.4 TLS[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]Servidor FTP: VSVFTPD[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=&amp]Muchas gracias, cualquier apoyo es bien recibido.[/FONT][/COLOR]

---

### Post by QIII on 2022-04-01
Hello!

You have posted in an English-speaking area of the forum.  Please either translate your post into English, or see if one of the sub-forums [here]("https://ubuntuforums.org/forumdisplay.php?f=183") support your native language.  Unfortunately, many of those forums are nearly inactive.

If you are able to use English at all, even with difficulty, we will do our very best to understand and help.  If you need to, use Google translate or similar.

---

### Post by eschwartzo on 2022-04-01
Sorry..:(

---

