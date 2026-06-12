---
title: "DOES NOT SEND BACKUP to the HOSTING - NO ENVIA BACKUP al HOSTING"
date: 2021-09-10
forum: New to Ubuntu
---

### Post by davidrlz on 2021-09-10
No envia backup al hosting desde script, tengo otro script en el cual genera el backup y en este encuentra mi backup pero no lo envia, no sè en que esta fallando este script, pero ya le he hecho de todo y sincermanete no he podido.


les pido por favor ayuda.




It does not send backup to the hosting from script, I have another script in which it generates the backup and in this it finds my backup but it does not send it, I do not know what this script is failing, but I have already done everything and sincerely I have not been able to.


I ask you please help.



SCRIPT 

#!/bin/bash


echo "Conectando y autenticando con el servidor de FTP"
FECHA=`date +%Y%m%d%H`
HOST='ftp.paginaprueba.com.co'
USER='eLpelr'
PASSWD='pass@@4DFLZ'


echo "Buscando Archivo"


cd /backups
find . -name "*tar.gz" -type f -mmin -10




echo "Archivo Encontrado"


echo "Enviando Backup de la BD"
ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
binary


put backup$FECHA.tar.gz


quit
END_SCRIPT
echo "Archivo enviado Correctamente"

---

### Post by TheFu on 2021-09-10
Best never to use plain ftp.  Use sftp OR use a real backup tool.  If you just want to push .tgz files, use **rsync**.

Scripts should not care what their CWD is.  

Tar isn't a very good backup tool if the amount of data backed up is over 500MB.

Before pushing any backup to any cloudy location, always encrypt it.  This can be done in-line with openssl or gpg.

sftp uses the same interface as plain FTP, but both the authentication AND transmission of the data is encrypted via ssh.  It can also use the ~/.netrc file for credentials (last time I looked).

If your host doesn't support ssh or rsync and only supports plain FTP, since 2002, it has been time to fire them. In 2021, using plain FTP is unacceptable.
A simple rsync command would look like this:
```
$ rsync /backups/backup-$(/usr/bin/date "+%Y%m%d%H").tar.gz     eLpelr@ftp.paginaprueba.com.co:
```
The "+%Y%m%d%H" must be quoted.  I prefer to use the "+%F" myself, but everyone has different needs.
If you want to mirror the backup-*tgz files and automatically remove them on the target, then you could add the *-delete-after* option to the rsync command. That will remove any files from the target that aren't in the source.

Rsync will use ssh-keys, so you can setup a ~/.ssh/config file to specify a different ssh-key to ftp.paginaprueba.com.co.  BTW, ftp.paginaprueba.com.co doesn't have the FTP port open - at least not from here.  I'm seeing only 25, 80, and 443 ports open. No ssh. No FTP.  If you are running this server, just install
```
sudo apt install ssh fail2ban rsync
```
and that will get rsync, ssh, and a brute force attack protection installed and configured.

BTW, this is an English language forum.  There are Spanish language areas for different regions here. If you are more comfortable with Spanish, there won't be as many people looking there, that's the downside.  My Spanish is terrible and didn't cover technical terms.

---

