---
title: "[SOLVED] How to use scp?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by fredscripts on 2008-10-30
Hi!

I have two computers connected to the same router by Ethernet cables.


I want to send a file from computer A to computer B.

ifconfig in B says local ip is 192.168.2.2 (if it is important) and the username and hostname (if those are the parameters of ubuntu instalation of computer name and user name) are foo, bar
so how should I use the scp command to send a file from A to B?

I've tried:
```

scp somefile.txt foo@bar:~
```

getting
```

ssh: connect to host foo port 22: Connection refused
lost connection
```

I'm total newbie on network stuff.  How should I run the command properly? there are any commands to open port 22 of computer B? (I hope I don't have to enter within the router configuration because last time I did it I messed up my internet connection).

Thank you very much in advance!!!

---

### Post by bodhi.zazen on 2008-10-30
did you install openssh server on the second box ?

This is a good start for learning SSH :

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

If you run a ssh server, be sure to secure it :

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

You will need to configure your router only if you are connecting over the internet. If both boxes are on a LAN you should be fine.

---

### Post by Sarmacid on 2008-10-30
He's right, you need ssh to connect to port 22```
sudo apt-get install ssh
```

You might want to google around for file transfers with nc, I've done transfers with it and you don't need to download anything.

---

### Post by fredscripts on 2008-10-30
Thanks for the info. One question, following the first link, after installing openssh-server from apt-get and typing

```
ssh localhost
```

I am suppossed to enter to a shell, but...
```

diffredential@fredlab:~$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 55:9d:ec:d6:e0:df:9b:9b:10:80:8c:64:e1:06:43:0d.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
diffredential@localhost's password: 
Linux fredlab 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
diffredential@fredlab:~$

```

I'm running this in computer A (the one from I want to send the file).

Where's the shell where I have to type "exit" as the fist guide says?

Thanks!

---

### Post by handydan918 on 2008-10-30
> **fredscripts said:**
> Thanks for the info. One question, following the first link, after installing openssh-server from apt-get and typing

```
ssh localhost
```

I am suppossed to enter to a shell, but...
```

diffredential@fredlab:~$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 55:9d:ec:d6:e0:df:9b:9b:10:80:8c:64:e1:06:43:0d.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
diffredential@localhost's password: 
Linux fredlab 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
diffredential@fredlab:~$

```

I'm running this in computer A (the one from I want to send the file).

Where's the shell where I have to type "exit" as the fist guide says?

Thanks!
Since you did ```
ssh localhost
```
you didn't "go" anywhere. You are still on the same physical machine. If you do ```
ssh 192.168.1.4
``` (or whatever the ip address of the target machine is) then the shell you end up in will be "on" the other machine.
here is an example of the scp syntax, here "pushing" a file from the working directory.

```
scp bookmarks.html 192.168.1.16:/home/sameusername
```

---

### Post by fredscripts on 2008-10-30
Thanks for answering, I was just worried followed this link:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

that tells that after running ssh localhost I should enter a shell and type "exit" to exit. As I don't see any shell I'm wondering if I did something wrong.

I will install ssh on the B computer (the one which will receive the file) after it has been upgraded (upgrading to 8.10 :)) and will let you know about trying to copy the file.

Thanks!

---

### Post by jbrown96 on 2008-10-30
If you are on the computer where the files are, then use this command ```
ssh /THE/FILE USERNAME_ON_OTHER_COMPUTER@LOCALIP_FOR_OTHER_COMPUTER:/DESTINATION_ON_OTHER_COMPUTER
```

---

### Post by bodhi.zazen on 2008-10-30
The command line is a "shell"

When you ssh localhost you start a new bash session, or shell (although it looks the same as your normal shell as it is on the same machine).

Just type exit to close the ssh session.

---

### Post by fredscripts on 2008-10-30
Oh thanks now I understand :) Will tell you when trying to send the file. Thanks so much for the explanations :)

---

### Post by fredscripts on 2008-10-30
> **jbrown96 said:**
> If you are on the computer where the files are, then use this command ```
ssh /THE/FILE USERNAME_ON_OTHER_COMPUTER@LOCALIP_FOR_OTHER_COMPUTER:/DESTINATION_ON_OTHER_COMPUTER
```

okay I have ssh installed and running properly on both computers.

Then I run from one:
```

diffredential@fredlab:~$ scp usefulcommands.txt 192.168.2.2:/home/diffred
diffredential@192.168.2.2's password: 
scp: /home/diffred/usefulcommands.txt: Permission denied
```

Should I change some permissions on the computer that is suppossed to receive the file?

Thanks!

---

### Post by spiderbatdad on 2008-10-30
now that all the tools are installed, you can also access the other machine graphically with the connect to server tool under the places menu...just select ssh, host name, and port...password if necessary. You dont need to select folder. It will launch with -X option and you will get nautilus file browser. Drag and drop to your heart's content.

---

### Post by saj0577 on 2008-10-30
You dont need to tell it the hostname and user of the local user as you are logged in.

Try:

```
scp usefulcommands.txt diffred@192.168.2.2:/home/diffred/
```


Saj

---

### Post by fredscripts on 2008-10-30
> **saj0577 said:**
> You dont need to tell it the hostname and user of the local user as you are logged in.

Try:

```
scp usefulcommands.txt diffred@192.168.2.2:/home/diffred/
```


Saj

Yep!! That was the right command!!! Thanks buddy :)


Thank you all very much for your help!!! :)

---

### Post by bodhi.zazen on 2008-10-30
If you like that, you might alwo like sshfs

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

Nice pictures spiderbatdad

---

