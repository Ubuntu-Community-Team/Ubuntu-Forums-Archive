---
title: "Problems with Unifi"
date: 2021-08-03
forum: New to Ubuntu
---

### Post by edrivas on 2021-08-03
I can see the file and when I try and remove it even with sudo it looks like it is removed but i check and it is still there. I am very new to ubuntu and all the commands I have found and used have failed. Most fail because I use them wrong. Last time I used command line was with basicA.

---

### Post by scorp123 on 2021-08-04
Since we dont't have crystal balls can you please provide more details?? e.g. what's the name of the file, where it is located (I mean the exact path, e.g. /path/to/file/ ...) and what command exactly you used to try and delete it??

---

### Post by ActionParsnip on 2021-08-04
What file? Where? What file system? Which release of Ubuntu?

Details please....

---

### Post by TheFu on 2021-08-04
> **edrivas said:**
> I can see the file and when I try and remove it even with sudo it looks like it is removed but i check and it is still there. I am very new to ubuntu and all the commands I have found and used have failed. Most fail because I use them wrong. Last time I used command line was with basicA.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has the necessary information you need.

A file not being removed could be caused by 500 different issues.  The ten most likely issues are easy to spot if we can see the exact permissions for the file, the exact command used, and the exact error messages output.

---

### Post by edrivas on 2021-08-04
Well I finally figured out that Ubuntu just did not want a *.unf and had to delete them individually. I was successful there. Now I still cannot get the unifi service to start. Is there a repair command to repair a service?

~$ sudo service unifi status
&#9679; unifi.service - unifi
   Loaded: loaded (/lib/systemd/system/unifi.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2021-08-04 16:16:03 EDT; 2min 25s ago
  Process: 22253 ExecStop=/usr/lib/unifi/bin/unifi.init stop (code=exited, status=0/SUCCESS)
  Process: 23365 ExecStart=/usr/lib/unifi/bin/unifi.init start (code=exited, status=0/SUCCESS)
    Tasks: 35
   Memory: 258.2M
      CPU: 4.245s
   CGroup: /system.slice/unifi.service
           &#9500;&#9472;22470 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-amd64 -cp /usr/share/java/commons-daemon.j
           &#9500;&#9472;22472 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-amd64 -cp /usr/share/java/commons-daemon.j
           &#9500;&#9472;22473 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-amd64 -cp /usr/share/java/commons-daemon.j
           &#9500;&#9472;22489 /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java -Dfile.encoding=UTF-8 -Djava.awt.headless=true -Dapple.
           &#9492;&#9472;22514 curl -s --connect-timeout 1 -o /dev/null -w %{http_code} [http://localhost:8080/status](http://localhost:8080/status)


Aug 04 16:16:03 Hospman-Unifi systemd[1]: unifi.service: Service hold-off time over, scheduling restart.
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Stopped unifi.
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Starting unifi...
Aug 04 16:16:03 Hospman-Unifi unifi.init[23365]:  * Starting Ubiquiti UniFi Controller unifi
Aug 04 16:16:03 Hospman-Unifi unifi.init[23365]:    ...fail!
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Started unifi.
lines 1-21/21 (END)

---

### Post by QIII on 2021-08-04
What do you mean by "Ubuntu didn't want a .unf file"?  What makes you think Ubuntu "didn't want" that file?  Was that part of some exception message?

As I understand it, that file extension indicates a file produced by Unifi.

 How did you remove it?

---

### Post by edrivas on 2021-08-04
I meant ubuntu did not want to delete all files with .unf extension. I had to delete them individually. So there was about 17 files with the .unf extension and the same command with a complete file name did remove the files.

sudo su
sudo cd /usr/lib/unifi/data/backup/autobackup/
sudo rm --force *.unf

I used 


sudo su
sudo rm --force /usr/lib/unifi/data/backup/autobackup/<filename>.unf

---

### Post by TheFu on 2021-08-04
That's because the regex/file globbing happens before the sudo and my userid cannot read what's happening inside the /tmp/FOO directory.  This is expected behavior.

If the /usr/lib/unifi/data/backup/autobackup/ directory permissions don't allow your normal userid to 'read' the directory, then the file globbing by /usr/lib/unifi/data/backup/autobackup/*unf  doesn't work.

I just tested this.
```
$ ls -dl FOO
drwx[COLOR="#FF0000"]------[/COLOR] 2 [COLOR="#FF0000"]root[/COLOR] root 4096 Aug  4 19:35 FOO/
```

I put {1..4}.unf into the FOO directory with permissions:```

-rw-------  1 root root    0 Aug  4 19:35 1.unf
-rw-------  1 root root    0 Aug  4 19:35 2.unf
-rw-------  1 root root    0 Aug  4 19:35 3.unf
-rw-------  1 root root    0 Aug  4 19:35 4.unf
```

If I run as my userid 
```
sudo rm -f /tmp/FOO/*nf
```
nothing happens. Sometimes it might say no files found.
It is all about the 700 permissions on the directory and it being owned by root.

Maybe this will be clearer? Running as my normal userid:
```
$ ls -l /tmp/FOO/
ls: cannot open directory '/tmp/FOO/': Permission denied

$ ls -l /tmp/FOO/*f
ls: cannot access '/tmp/FOO/*f': Permission denied

$ sudo ls -l /tmp/FOO/*f
ls: cannot access '/tmp/FOO/*f': No such file or directory

```

Is that clearer?

---

### Post by Holger_Gehrke on 2021-08-04
The problem is your attempt to do 'sudo cd'. You should have got an error message like 'sudo: cd: command not found'. 'cd' is not a program, it's an internal command of the shell so you can't execute it with 'sudo'. So your working directory didn't change and the 'rm' failed because you weren't in the right directory and because you used the option '--force' you didn't even get an error message by 'rm'. Also, after running 'sudo su' you're working as root so no need to prefix further commands with 'sudo'. If you had just given the commands without 'sudo' it would have worked. Or you could just do 'sudo rm --force /usr/lib/unifi/data/backup/autobackup/*.unf' without the 'sudo su' and that would have worked, too.

Holger

---

### Post by edrivas on 2021-08-04
Thank You all for the explanation. It makes tons of sense. I will learn a few more things soon. I now still cannot start the unifi service. It fails. Is there a way to find out what is causing it to fail. I tried to use the Mongo ([https://help.ui.com/hc/en-us/articles/204911424-UniFi-How-to-Remove-Prune-Older-Data-and-Adjust-Mongo-Database-Size](https://help.ui.com/hc/en-us/articles/204911424-UniFi-How-to-Remove-Prune-Older-Data-and-Adjust-Mongo-Database-Size)). It says it cannot connect to 127.0.0.1:27117. I think that may fix it. Still not sure.

```
Welcome to Ubuntu 16.04.7 LTS (GNU/Linux 4.4.0-210-generic x86_64)


 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


UA Infra: Extended Security Maintenance (ESM) is not enabled.


1 update can be applied immediately.
To see these additional updates run: apt list --upgradable


39 additional security updates can be applied with UA Infra: ESM
Learn more about enabling UA Infra: ESM service for Ubuntu 16.04 at
[https://ubuntu.com/16-04](https://ubuntu.com/16-04)


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.




Last login: Wed Aug  4 15:14:51 2021 from 108.xxx.xxx.xxx
```
```
edrivas@Hospman-Unifi:~$ sudo service unifi status
[sudo] password for edrivas:
&#9679; unifi.service - unifi
   Loaded: loaded (/lib/systemd/system/unifi.service; enabled; vendor preset: en
   Active: active (running) since Wed 2021-08-04 16:16:03 EDT; 3h 31min ago
  Process: 22253 ExecStop=/usr/lib/unifi/bin/unifi.init stop (code=exited, statu
  Process: 23365 ExecStart=/usr/lib/unifi/bin/unifi.init start (code=exited, sta
    Tasks: 37
   Memory: 288.6M
      CPU: 5min 35.665s
   CGroup: /system.slice/unifi.service
           &#9500;&#9472;22470 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-a
           &#9500;&#9472;22472 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-a
           &#9500;&#9472;22473 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-a
           &#9500;&#9472;22489 /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java -Dfile.encodin
           &#9492;&#9472;22514 curl -s --connect-timeout 1 -o /dev/null -w %{http_code} http


Aug 04 16:16:03 Hospman-Unifi systemd[1]: unifi.service: Service hold-off time o
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Stopped unifi.
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Starting unifi...
Aug 04 16:16:03 Hospman-Unifi unifi.init[23365]:  * Starting Ubiquiti UniFi Cont
Aug 04 16:16:03 Hospman-Unifi unifi.init[23365]:    ...fail!
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Started unifi.
lines 1-21/21 (END)
```
```
edrivas@Hospman-Unifi:~$ sudo su
root@Hospman-Unifi:/home/edrivas# cd ~
root@Hospman-Unifi:~# ls
root@Hospman-Unifi:~# sudo wget [https://help.ui.com/hc/article_attachments/115024095828/mongo_prune_js.js](https://help.ui.com/hc/article_attachments/115024095828/mongo_prune_js.js)
--2021-08-04 19:48:50--  [https://help.ui.com/hc/article_attachments/115024095828/mongo_prune_js.js](https://help.ui.com/hc/article_attachments/115024095828/mongo_prune_js.js)
Resolving help.ui.com (help.ui.com)... 104.16.53.111, 104.16.51.111
Connecting to help.ui.com (help.ui.com)|104.16.53.111|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/javascript]
Saving to: &#8216;mongo_prune_js.js&#8217;


mongo_prune_js.js       [ <=>                ]   2.60K  --.-KB/s    in 0s


2021-08-04 19:48:50 (45.4 MB/s) - &#8216;mongo_prune_js.js&#8217; saved [2664]
```


```
root@Hospman-Unifi:~# mongo --port 27117 < mongo_prune_js.js
MongoDB shell version: 2.6.10
connecting to: 127.0.0.1:27117/test
2021-08-04T19:49:02.395-0400 warning: Failed to connect to 127.0.0.1:27117, reason: errno:111 Connection refused
2021-08-04T19:49:02.395-0400 Error: couldn't connect to server 127.0.0.1:27117 (127.0.0.1), connection attempt failed at src/mongo/shell/mongo.js:148
exception: connect failed
root@Hospman-Unifi:~#
```

---

### Post by TheFu on 2021-08-04
16.04 support ended unless you have a paid support contract.

Please move to a supported release.

---

### Post by edrivas on 2021-08-05
I still cannot start the unifi service. It fails. Is there a way to find out what is causing it to fail. I tried to use the Mongo ([https://help.ui.com/hc/en-us/article...-Database-Size]("https://help.ui.com/hc/en-us/articles/204911424-UniFi-How-to-Remove-Prune-Older-Data-and-Adjust-Mongo-Database-Size")). It says it cannot connect to 127.0.0.1:27117. I think that may fix it. Still not sure.

```
Welcome to Ubuntu 16.04.7 LTS (GNU/Linux 4.4.0-210-generic x86_64)


 * Documentation:  [https://help.ubuntu.com]("https://help.ubuntu.com/")
 * Management:     [https://landscape.canonical.com]("https://landscape.canonical.com/")
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


UA Infra: Extended Security Maintenance (ESM) is not enabled.


1 update can be applied immediately.
To see these additional updates run: apt list --upgradable


39 additional security updates can be applied with UA Infra: ESM
Learn more about enabling UA Infra: ESM service for Ubuntu 16.04 at
[https://ubuntu.com/16-04](https://ubuntu.com/16-04)


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
```


```
Unifi:~$ sudo service unifi status
[sudo] password for 
&#9679; unifi.service - unifi
   Loaded: loaded (/lib/systemd/system/unifi.service; enabled; vendor preset: en
   Active: active (running) since Wed 2021-08-04 16:16:03 EDT; 3h 31min ago
  Process: 22253 ExecStop=/usr/lib/unifi/bin/unifi.init stop (code=exited, statu
  Process: 23365 ExecStart=/usr/lib/unifi/bin/unifi.init start (code=exited, sta
    Tasks: 37
   Memory: 288.6M
      CPU: 5min 35.665s
   CGroup: /system.slice/unifi.service
           &#9500;&#9472;22470 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-a
           &#9500;&#9472;22472 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-a
           &#9500;&#9472;22473 unifi -cwd /usr/lib/unifi -home /usr/lib/jvm/java-8-openjdk-a
           &#9500;&#9472;22489 /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java -Dfile.encodin
           &#9492;&#9472;22514 curl -s --connect-timeout 1 -o /dev/null -w %{http_code} http


Aug 04 16:16:03 Hospman-Unifi systemd[1]: unifi.service: Service hold-off time o
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Stopped unifi.
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Starting unifi...
Aug 04 16:16:03 Hospman-Unifi unifi.init[23365]:  * Starting Ubiquiti UniFi Cont
Aug 04 16:16:03 Hospman-Unifi unifi.init[23365]:    ...fail!
Aug 04 16:16:03 Hospman-Unifi systemd[1]: Started unifi.

```



```
Unifi:~$ sudo su
root@Hospman-Unifi:/home/# cd ~
root@Hospman-Unifi:~# ls
root@Hospman-Unifi:~# sudo wget [https://help.ui.com/hc/article_attac...go_prune_js.js]("https://help.ui.com/hc/article_attachments/115024095828/mongo_prune_js.js")
--2021-08-04 19:48:50--  [https://help.ui.com/hc/article_attac...go_prune_js.js]("https://help.ui.com/hc/article_attachments/115024095828/mongo_prune_js.js")
Resolving help.ui.com (help.ui.com)... 104.16.53.111, 104.16.51.111
Connecting to help.ui.com (help.ui.com)|104.16.53.111|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/javascript]
Saving to: ‘mongo_prune_js.js’


mongo_prune_js.js       [ <=>                ]   2.60K  --.-KB/s    in 0s


2021-08-04 19:48:50 (45.4 MB/s) - ‘mongo_prune_js.js’ saved [2664]
```


```
root@Hospman-Unifi:~# mongo --port 27117 < mongo_prune_js.js
MongoDB shell version: 2.6.10
connecting to: 127.0.0.1:27117/test
2021-08-04T19:49:02.395-0400 warning: Failed to connect to 127.0.0.1:27117, reason: errno:111 Connection refused
2021-08-04T19:49:02.395-0400 Error: couldn't connect to server 127.0.0.1:27117 (127.0.0.1), connection attempt failed at src/mongo/shell/mongo.js:148
exception: connect failed
root@Hospman-Unifi:~#
```

---

### Post by QIII on 2021-08-05
Threads merged.

---

### Post by QIII on 2021-08-05
@edrivas --

Please use the default font, size and color unless you have a very good reason to draw attention to a particular portion of your post.  The color of URLs will be automatically set by the Forum software.

Also, please enclose all terminal commands and their results in code tags.  That will preserve formatting and make your posts easier to read.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by edrivas on 2021-08-05
With my limited knowledge of Ubuntu and the inheritance of these networks, I am just pushing through to get this fixed and then research on what to do to upgrade and correct what looks like years of neglect. One of the networks is located on youtube under FiberNinja. It is the Florida trip when I cleaned it up. We installed a Ubiquiti network for the IT there and now I have inherited everything he has done. A gorgeous cleanup and I have to correct that also since it looks like we never went to clean it up.

---

### Post by TheFu on 2021-08-05
Until it runs a supported release, there is little to be done. Good luck.

---

