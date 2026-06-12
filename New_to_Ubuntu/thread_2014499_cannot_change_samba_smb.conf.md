---
title: "cannot change samba smb.conf"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by paul1945 on 2012-07-02
Have been trying to change smb.conf located in /etc/samba so I can have the Ubuntu shared folder accessible to my Windows network, but no luck. I can copy it, then edit it but cannot copy it back. Interestingly I backed up smb.conf to smb.conf.bkup from the command line, and that seems to have replaced the smb.conf that was originally there, rather than copy it.
I tried to stop the samba service by following some instructions I got from another Ubuntu user by accessing samba in /etc/init.d/ from the command line, but it did not work. On inspection I found that nothing called samba was present there.
It's all very complicated and frustrating. Any idea as to what I am doing wrong?

---

### Post by Morbius1 on 2012-07-02
** To edit smb.conf you need to do so as root:
```
gksu gedit /etc/samba/smb.conf
```** To start, restart, or stop samba:
```
sudo service smbd start
sudo service smbd restart
sudo service smbd stop
```

---

### Post by paul1945 on 2012-07-02
Yes, that worked a treat, thank you.:p

---

### Post by paul1945 on 2012-07-02
It appears I am not there yet. 
I can now see my Ubuntu machine on my Windows XP machines, and transfer files back and forth to a shared folder from an XP machine onto the Ubuntu machine, but cannot browse my shared folders on my Windows XP machines from Ubuntu over the Wireless Network, even though there is no problem with accessing the Web on the Ubuntu machine, and the Windows XP machines communicate fine with each other. I have tried smb4k but although this shows the network, it did not allow access to the shares, even though I put in the location etc.
I have tried some other things, including setting up a Windows network, but now I have my XP machines showing under "network" in Ubuntu, and another folder called Windows that shows the same again when opened.
It seems I have screwed things up rather than helped them.
Any suggestions?:confused:

---

### Post by Morbius1 on 2012-07-03
>  It seems I have screwed things up rather than helped them.No you haven't because you can do this:
> I can now see my Ubuntu machine on my Windows XP machines, and transfer  files back and forth to a shared folder from an XP machine onto the  Ubuntu machineThe problem appears to me to be on the Windows end:
> but cannot browse my shared folders on my Windows XP machines from UbuntuJust to be sure that nothing is wacky on the Linux end post the output of the following command:
```
testparm -s
```And to find out how Linux sees the LAN post the output of this command:
```
smbtree
```

---

### Post by dvks on 2012-07-03
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]If the problem viewing windows shared folders on UBUNTU[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]You may try activating wins:[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]Open command terminal.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]Open the network config file nsswitch.config:[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]gksu gedit /etc/nsswitch.conf[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]Look for this line: [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]Add "wins" so the line looks like this: [/FONT][/SIZE][/FONT][/COLOR]
[SIZE=3][FONT=Calibri][COLOR=#333333][FONT=Calibri]hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4[/FONT][/COLOR][/FONT][/SIZE]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]Install the "winbind" package: [/FONT][/SIZE][/FONT][/COLOR]
[SIZE=3][FONT=Calibri][COLOR=#333333][FONT=Calibri]sudo apt-get install winbind[/FONT][/COLOR][/FONT][/SIZE]
[COLOR=#333333][FONT=Calibri][SIZE=3][FONT=Calibri]Reboot or restart your network[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by Morbius1 on 2012-07-03
If you do the above with winbind and nsswitch you most likely will make a mess of things. 

I would recommend taking this step by step instead and make sure everything is set up properly on your end.  "testparm -s" will tell us how you are set up and "smbtree" will list of all the workgroups, and within each workgroup all it's hosts, and within each host all it's shares. If it finds something wrong with listing the Windows shares for example it will produce error messages that can be used in the diagnosis.

---

### Post by paul1945 on 2012-07-03
Hi, thanks for your assistance thus far.
I tried the "testparm -s", and the output is below.
I also tried "smbtree", but this gave no visible output. 
Regards,
Paul.

ï»¿paul@paul-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = MSHOME
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by Morbius1 on 2012-07-04
>  I also tried "smbtree", but this gave no visible output. Well, that's not good. In fact, that's a show stopper. At a minimum it should show the shares on the Ubuntu machine itself. I would go through the following steps:

[1] Add a line to smb.conf:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line - right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```Then restart all the samba services:
```
sudo service smbd restart
``````
sudo service nmbd restart
```Then try smbtree again.

[2] If that doesn't resolve it outright then disable everyone's firewall if you have one implemented and see if smbtree has output.

[COLOR=Blue]**BTW**[/COLOR]: You earlier said you created shares in Ubuntu that Windows could access but testparm shows none. You may have created them though Nautilus so please post the output of the following command so we can see how they are configured:
```
net usershare info --long
```[COLOR=Blue]**BTW2**[/COLOR]: Until we resolve this and just to make sure that samba itself is working you could circumvent all this and connect to the Windows machine directly by ip address and not by browsing:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the Windows machine.*[/COLOR]

---

### Post by paul1945 on 2012-07-04
Hello Morbius1, did as instructed and can now not only see the network but browse and copy/save files on my Windows machines and Linux NAS.
Initially I could only browse the Windows machines, but when I set wins support to "no" in smb.conf I was able to access the Linux NAS too (I am not sure that this was the right thing to do).
Nevertheless, there is still no visible output when I type "smbtree";
but "net usershare info --long" gave the following output:

paul@paul-desktop:~$ net usershare info --long
[Ubuntu]
path=/home/paul/Desktop/Network
comment=
usershare_acl=Everyone:F,
guest_ok=y

Regards,
Paul.:p

---

### Post by Morbius1 on 2012-07-05
>  Nevertheless, there is still no visible output when I type "smbtree";It's not clear to me why there is no output from smbtree but from the sound of it it doesn't matter since you can now do everything you wanted to do:
        > Hello Morbius1, did as instructed and can now not only see the network  but browse and copy/save files on my Windows machines and Linux NAS.> Initially I could only browse the Windows machines, but when I set wins  support to "no" in smb.conf I was able to access the Linux NAS too (I am  not sure that this was the right thing to do).Another strange anomily. The default in samba has "wins support = no" so setting it back to that is fine. Here's the thing though, setting it to yes meant that you had converted your machine to a WINS server. It will only function as that though if you had altered the network settings on every machine on your lan pointing them to this server. Had you not done that then setting it to yes should have had no affect at all.

As an ordained minister in the "Church of if it works don't mess with it" I'd say this all works now.

---

### Post by paul1945 on 2012-07-06
Agreed. Thanks for the help. Paul.

---

