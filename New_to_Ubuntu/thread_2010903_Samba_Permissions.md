---
title: "Samba Permissions"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by chesc on 2012-06-26
So Ive been trying to get a samba share working on ubuntu for 2 years now and I have finally had some limited success. The idea is a simple file server that I can access from my Mac and windows PC's.

I have managed to get it so that I can log into the server with my mac but all the files created on ubuntu are read only on my mac and all the files created on my mac are read only in ubuntu. I really just want it to work like a network drive so no matter which computer creates a file both can edit and save documents. 

I have been able to view the /etc/samba/smb.conf: but every instructional I have found on google tells me create a new section on the file or edit the file. When I scroll up and find a part of the file I think I should edit (although I don't really know if i should) the text wont change when I highlight it and type. I really have no idea how to edit this file so every instructional I have found isn't helping me. 

Does anyone know how to edit the file and perhaps what part of it should be edited?

Thanks in advance
Richard

---

### Post by Morbius1 on 2012-06-26
The folks here that can help you need to know how you are set up on your Linux box so please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by chesc on 2012-06-26
This is what I get


chesc@chesc-cortana:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[JayShare90]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = JAYSHARE
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
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

[JayShare90]
    path = /home/chesc/JayShare90
    valid users = avahi, chesc, root
    read only = No


chesc@chesc-cortana:~$ net usershare info --long
chesc@chesc-cortana:~$

---

### Post by audiomick on 2012-06-26
I have absolutely no idea what you need to put into the config file, but it sounds like you are not starting the editor with root privileges when you have been trying to edit it.

Try opening it with

```
gksu gedit /etc/samba/smb.conf
```

You will be asked for your password, then you should see an instance of the editor gedit with the file open and not write protected.

---

### Post by Morbius1 on 2012-06-26
I don't know why you would ever have root or avahi as a valid user but I have a suggestion that will simplify things if this is all you want:
> I really just want it to work like a network drive so no matter which computer creates a file both can edit and save documents.Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```And add a line to your share definition so that it looks like this:
> [JayShare90]
    path = /home/chesc/JayShare90
    valid users = avahi, chesc, root
[COLOR=Blue]**force user = chesc**[/COLOR]
    read only = No[COLOR=Blue]*Samba will prevent anyone other than avahi,chesc, and root from gaining access. But after they are allowed in the "force user" line will convert them to chesc. All new files will be saved with chesc as owner so all remote users will have read / write access to the files as well as the Linux user named chesc.*[/COLOR]

[COLOR=Black]After you make the change to smb.conf restart the samba service:
[/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black]
Wait a few minutes before trying to access the server from the mac since a restart of samba causes the network to have a minor tantrum.

[COLOR=Blue]***EDIT***[/COLOR]: And if you really want anyone to have access to that share eliminate the "valid users" line entirely and replace it with "guest ok = yes":
[/COLOR]> [JayShare90]
    path = /home/chesc/JayShare90
[COLOR=Blue]**     guest ok = yes**[/COLOR]
[COLOR=Blue]**force user = chesc**[/COLOR]
    read only = No

---

### Post by chesc on 2012-06-26
> **Morbius1 said:**
> I don't know why you would ever have root or avahi as a valid user but I have a suggestion that will simplify things if this is all you want:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```And add a line to your share definition so that it looks like this:
[COLOR=Blue]*Samba will prevent anyone other than avahi,chesc, and root from gaining access. But after they are allowed in the "force user" line will convert them to chesc. All new files will be saved with chesc as owner so all remote users will have read / write access to the files as well as the Linux user named chesc.*[/COLOR]

[COLOR=Black]After you make the change to smb.conf restart the samba service:
[/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black]
Wait a few minutes before trying to access the server from the mac since a restart of samba causes the network to have a minor tantrum.

[COLOR=Blue]***EDIT***[/COLOR]: And if you really want anyone to have access to that share eliminate the "valid users" line entirely and replace it with "guest ok = yes":
[/COLOR]
Thanks.. [audiomick]("http://ubuntuforums.org/member.php?u=553389") and [Morbius1]("http://ubuntuforums.org/member.php?u=982144"). I was able to edit the config file and add that extra line 

[JayShare90]
    path = /home/chesc/JayShare90
[COLOR=Blue]**     guest ok = yes**[/COLOR]
[COLOR=Blue]**force user = chesc**[/COLOR]
    read only = No

I REALLY appreciate the help from both of you. Thank you for your time.

---

### Post by mapes12 on 2012-06-26
If you just want to share files between machines on your own network then why not right click the folder where the files are located and enable the sharing option. You should then be able to access them without any problems. A system restart may be required.

In my experience Samba is a nightmare.......

---

### Post by Morbius1 on 2012-06-26
> **mapes12 said:**
> If you just want to share files between machines on your own network then why not right click the folder where the files are located and enable the sharing option. You should then be able to access them without any problems. A system restart may be required.

In my experience Samba is a nightmare.......
Well, first of all "Sharing Options" is Samba.

Second, He already created an Samba Classic share in smb.conf. If he creates another one using Samba Usershare ( Sharing Options ) then he'll have created 2 samba shares using 2 different methods, with share definitions in 2 different locations for the same folder. That really should be avoided.

Third, he would have had to add "force user" to smb.conf anyway - just in a different location in smb.conf.

---

### Post by mapes12 on 2012-06-26
> Well, first of all "Sharing Options" is Samba.I know. So why get into all the configuration piece, and editing system files. Where is the added value?  Have I missed something?

---

### Post by Morbius1 on 2012-06-26
> **mapes12 said:**
> I know. So why get into all the configuration piece, and editing system files. Where is the added value?  Have I missed something?
Yes, I believe you did miss something.
> I really just want it to work like a network drive so no matter  which computer creates a file both can edit and save documents. Let say he created a guest accessible share, which is what he ended up doing with a Classic share, of his folder using Nautilus. When I asked him for the output of this command:
```
net usershare info --long
```It would have returned this:
> [JayShare90]
path=/home/chesc/JayShare90
comment=
usershare_acl=Everyone:F,
guest_ok=yEvery remote user will have the ability to add a file to that folder. But chesc on the server itself will not have the ability to write to that file because it's owned by "nobody" with a group of "nogroup". 

There are 101 different ways around this problem but one way is to add a "force user = chesc" just like before. But there is no share definition is smb.conf when you use Nautilus to create the share and you can't add it to the file that does have the definition so you end up having to add it to the [global] section of smb.conf.

Same amount of editing of a system file - just in a different place in smb.conf.

Don't get me wrong, I advocate Usershares a lot but I asked him in the first post to provide output of those commands so I could see what method he was using. He used Classic shares so I gave him a suggestion pertaining to that method.

[COLOR=Blue]**EDIT**[/COLOR]: One more thing before I shut down for the day. The original share looked like this:
> [JayShare90]
    path = /home/chesc/JayShare90
[COLOR=Blue]     valid users = avahi, chesc, root[/COLOR]
    read only = No
There is no way to create a limited set of "valid users" using Nautilus. You can do it via the command line using a butt ugly syntax but at that point you might as well use the classic method through smb.conf.

---

