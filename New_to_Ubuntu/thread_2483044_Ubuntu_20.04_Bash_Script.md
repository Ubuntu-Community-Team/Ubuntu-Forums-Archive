---
title: "Ubuntu 20.04 Bash Script"
date: 2023-01-18
forum: New to Ubuntu
---

### Post by tony68 on 2023-01-18
Hi all

I am hoping someone can help with this script I am trying to create. I am posting this here as this is the first time I have tried to create a script and could do with some pointers / syntax help.

The scenario is this - I need to write a script which will be run as a cronjob to download a couple of files from a suppliers SFTP server. I have to authenticate with a password, so what I came up with was this - which works from the command line - but not as a script;

```
#!/bin/bashsftp [username]@[sftp server address]
get FILE1.ZIP /var/www/datafiles/
cd DIRECTORY2
get FILE2.ZIP /var/www/datafiles/
bye
```

I then saved it and used ```
chmod +x filename.sh
``` so it could be called.

Obviously this is far too simple as, I dont think you can connect to SFTP in the way you can with FTP (ftp [password]:[username]@[ftp server address]) - also while the first line opens a connection to the SFTP server and prompts for a password, the next lines are not passed as commands to the connected server... so, is anyone able to help with some pointers?

Many thanks in advance

---

### Post by MAFoElffen on 2023-01-18
> **tony68 said:**
> Hi all

I am hoping someone can help with this script I am trying to create. I am posting this here as this is the first time I have tried to create a script and could do with some pointers / syntax help.

The scenario is this - I need to write a script which will be run as a cronjob to download a couple of files from a suppliers SFTP server. I have to authenticate with a password, so what I came up with was this - which works from the command line - but not as a script;

```
#!/bin/bashsftp [username]@[sftp server address]
get FILE1.ZIP /var/www/datafiles/
cd DIRECTORY2
get FILE2.ZIP /var/www/datafiles/
bye
```

I then saved it and used ```
chmod +x filename.sh
``` so it could be called.

Obviously this is far too simple as, I dont think you can connect to SFTP in the way you can with FTP (ftp [password]:[username]@[ftp server address]) - also while the first line opens a connection to the SFTP server and prompts for a password, the next lines are not passed as commands to the connected server... so, is anyone able to help with some pointers?

Many thanks in advance
RE: [https://www.ssh.com/academy/ssh/sftp-ssh-file-transfer-protocol](https://www.ssh.com/academy/ssh/sftp-ssh-file-transfer-protocol)
```

#!/bin/bash
# Automate sftp transaction through cron
# (Abstract code)
File1=/path/to/File1.zip
File2/path/to/File1.zip

# Initiate connection
/usr/bin/sftp [username]@[sftp server address]

# sftp converstion
get FILE1.ZIP /var/www/datafiles/  # modify this to write the file to a specific path to...
cd DIRECTORY2
get FILE2.ZIP /var/www/datafiles/  # modify this to write the file to a specific path to...
bye
```

When writing a script to be ran by cron, you have to include the path to any executable's... Because cron scripts are executed by Root...

I am not familiar with exit codes on sftp transactions, and cron scripts are executed by Root, so if it were me, I would add the path to where you want the files to download to... and then check to see if they were actually downloaded, then add that transaction to a log...
```

### added code

if [ "$(ls -lh $File1 | awk '{print $6 " " $7}')" == "$(date | awk '{print $2 " " $3}')" ]
then
   echo -e "$File1 was downloaded" >> /var/logs/sftp.log
else
  echo -e "$ERROR: $File1 was NOT downloaded" >> /var/log/sftp.log
fi

if [ "$(ls -lh $File2 | awk '{print $6 " " $7}')" == "$(date | awk '{print $2 " " $3}')" ]
then
   echo -e "$File2 was downloaded" >> /var/logs/sftp.log
else
  echo -e "$ERROR: $File2 was NOT downloaded" >> /var/log/sftp.log
fi

```

---

### Post by LHammonds on 2023-01-19
You are not going to get data in the way of return codes from the FTP client.   A general overall success exit code of the client means nothing about the success / failure of each individual command you issue once the connection is established.

As MAFoElffen pointed out, you need to do your validation checks outside of the FTP client to see if the files exist before and after you execute the FTP commands.   If the files exist before you run the FTP commands, what are you doing to do?   If they do not exist after the FTP commands, what are you going to do?  Your script needs to handle these kinds of situations.

With SFTP, you don't want to expose the password as part of the commandline because anyone connected to your server can run a process list and see that password directly in the list of processes running.

You can export the password to a shell variable to be utilized by the login process with sshpass and sftp.

Here is one of several examples on my github account that does this: [ftp-bank2emr-835.sh](https://github.com/LHammonds/ubuntu-bash/blob/master/ftp-bank2emr-835.sh)

You can ignore everything after the FTP connection since those are just "my" business rules for handling what happens if there is or is not files to process after the commands.  But they are still examples of what "can" be done such as mounting remote storage, moving the files around, archiving, sending email notifications, etc.

LHammonds

---

### Post by MAFoElffen on 2023-01-19
+1 with LHammonds. Lots on things were spinning through my head on writing that response, as my wife and I were in the process of heading out the door on errands. (My day off routines.)

Some of my old business rules were signed-script execution policys, and sceduled-job emails sent via stmp from scripts to an Admin Email account, on reportable stats and any errors. Logs are great, but I wanted to know immediately if there was any pending, that needed immediate attention. Was I close to running out of storage? Did a job not run? Etc.

Another was security... how to handle passwords in scripts for 'external connections'.

I think LHammonds covered those well.

---

### Post by TheFu on 2023-01-19
Do you have other options for the protocol to be used, perhaps scp or rsync over ssh?
When using any ssh-based protocol (sftp, ssh, scp, rsync), you can setup ssh-keys that don't require a password prompt to be used only by automatic tasks.  It is just 2 commands to do it.

But if you only have sftp, know that the sftp interface was designed as a clone of the plain ftp interface.  I'd use mget if I were stuck with sftp, but I'd use scp or rsync if those were possible.

```
scp joe@{remote-IP-or-DNS-name}:FILE[12].ZIP /var/www/datafiles/
```

Much easier. Of course, the target directory must exist and the files to be pulled must be spelled exactly correct AND be in the location. The command avoid will look in ~joe/FILE[12].ZIP on the remote system.  If the files are large and may not have changed, use rsync.
```
rsync -zv --progress --stats    joe@{remote-IP-or-DNS-name}:FILE[12].ZIP /var/www/datafiles/
```


To create an ssh-key (1-time setup):
   ```
$ ssh-keygen -t ed25519
```
To push the public ssh-key to the remote system:
   ```
$ ssh-copy-id -i ~/.ssh/id_ed25519.pub joe@{remote-IP-or-DNS-name}
```

Like I said above, all ssh-based tools will honor the key. ssh keys without a passphrase to unlock them should only be used for very specific automation.

---

