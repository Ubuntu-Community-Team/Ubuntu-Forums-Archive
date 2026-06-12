---
title: "Changing Permissions on a Shared Folder"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by kc5hwb on 2013-03-29
Hi All,
I've tried to make this as precise as possible, without getting long-winded, but also wanted to give as much detail as possible.  I've been using Ubuntu off and on for several years, so I am not new to it, but I also know that I still have a lot to learn about it.



**Objective:**
I have a folder shared from my Ubuntu box with full open access, CHMOD -777, that I can access from all my Windows boxes, but cannot access from my 2nd Ubuntu box.  I want to change the level of access to this folder so that ONLY my own user account can access it, but I want to be able to do it from any Windows or Ubuntu machine on my network.

**Current Setup:  **
Currently I have 2 Ubuntu 12.04 boxes, both running SAMBA, on my home network.  I also have about 6 different Windows boxes.  
I have ran a CHMOD -777 on the share folder on my first Ubuntu box, and I can access it fine from my Windows boxes, but not from my 2nd Ubuntu box.  As stated, I want to change this and only let MY user account FULL access to this network share, hosted on the Ubuntu box.
One thing I tried is right-clicking on the shared folder and removing the checkbox from the "Guests access (those without a user account)" 
but this eliminates my ability to access the folder, even with my own account.  I've tried entering my username and password, and also entering the IP to the host box in front of my username (192.168.x.x\username) but none of these allow me access.

**Current problems I've noticed:**
From my 2nd Ubuntu box, the share on the main Ubuntu box is read-only.  I can see it, but cannot make any changes.  
In the GUI on my main Ubuntu box, when I right-click on the shared folder, go to properties, choose the Share tab, and remove the checkbox for "Guest Access (for people without a user account)" it changes the entire folder to read-only, even when I am entering my account credentials.

**Change I want to make:**
1.  I want to remove the "guest login OK" from the smb.conf file (easy to do) and remove the checkbox from the permissions on the shared folder, and I want to require that my user account be used each time this share is accessed.
2.  I want to be able to share this folder from my main Ubuntu box to my 2nd Ubuntu box.

---

### Post by Morbius1 on 2013-03-29
Post the output of the following commands so we can all see how your shares are set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by kc5hwb on 2013-04-01
```
jape@JOSEPHUS:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Global parameter usershare owner only found in service section!
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = JUDEA
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                                                                             * %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        usershare owner only = No
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

[share]
        comment = Tonido Raid
        path = /home/jape/Raid
        read only = No
        create mask = 0777
        guest ok = Yes
```


```
jape@JOSEPHUS:~$ net usershare info --long
[TonidoCloud]
path=/home/jape/Raid
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Josephus]
path=/home/jape/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

---

### Post by Morbius1 on 2013-04-01
There are 2 ways to create a samba share and you are using both on the same folder even though they have different share names:
This is a Samba Usershare:
> [TonidoCloud]
path=/home/jape/Raid
comment=
usershare_acl=Everyone:F,
guest_ok=y
If you want access only to you I would go back into Nautilus and unshare it.

This is a Samba Classic share:
> [share]
        comment = Tonido Raid
        path = /home/jape/Raid
        read only = No
        create mask = 0777
        guest ok = Yes
If you want to deny access to anyone but you remove the "guest ok = yes" and replace it with a "valid users = jape" if jape is your user name:
> [share]
        comment = Tonido Raid
        path = /home/jape/Raid
        read only = No
        create mask = 0777
        [COLOR=#0000cd]**valid users = jape**[/COLOR]
Then restart samba:
```
sudo service smbd restart
```
[COLOR=#0000cd]**EDIT**[/COLOR]: I'm assuming you added yourself to the samba password database:
```
 sudo smbpasswd -a jape
```

---

### Post by kc5hwb on 2013-04-01
That top code I posted is the smb.conf file, I recognize that.  But how am I using both?  Maybe I setup something twice?  Should I remove one of them?

---

### Post by Morbius1 on 2013-04-01
This samba share ( called a Samba usershare ) was created from Nautilus > Sharing Options:
```
[TonidoCloud]
path=/home/jape/Raid
comment=
usershare_acl=Everyone:F,
guest_ok=y 			 		
```
Remove it by going back into Nautilus and reversing the steps you used to create it.

---

### Post by kc5hwb on 2013-04-02
So, in other words, just remove the check-marks from Sharing Options in the Nautilus Window.... ?

---

### Post by Morbius1 on 2013-04-02
Yes. Then run the following command again and make sure the only output is for your "Public" share - [Josephus]:
```
net usershare info --long
```

---

### Post by kc5hwb on 2013-04-02
[http://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&docid=umIkwyY119JuRM&tbnid=F6sm_4Pj1jBlhM:&ved=&url=http%3A%2F%2Frillmar.wordpress.com%2F2008%2F08%2F15%2Fmultiple-connections-to-server-or-shared-resource-error%2F&ei=A2lbUfTHIsHb2AWHhIHYDg&bvm=bv.44697112,d.b2I&psig=AFQjCNGC4_hiIo_t5JCP79U6Qj1LaVuWUA&ust=1365031546966248]("http://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&docid=umIkwyY119JuRM&tbnid=F6sm_4Pj1jBlhM:&ved=&url=http%3A%2F%2Frillmar.wordpress.com%2F2008%2F08%2F15%2Fmultiple-connections-to-server-or-shared-resource-error%2F&ei=A2lbUfTHIsHb2AWHhIHYDg&bvm=bv.44697112,d.b2I&psig=AFQjCNGC4_hiIo_t5JCP79U6Qj1LaVuWUA&ust=1365031546966248")

Getting this error after performing the steps above.  I am logged into the Ubuntu machine locally, but have killed all other remote sessions.

Additionally, this command now returns nothing at all

```
net usershare info --long
```

---

### Post by Morbius1 on 2013-04-03
You did not get the following error by removing all of your samba usershares:
> [FONT=Verdana][SIZE=1]Multiple connections to a server or  shared resource by the same user, using more than one user name, are not  allowed. Disconnect all previous connections to the server or shared  resource and try again[/SIZE][/FONT]
You did something else on your Windows machine to induce that error.

---

### Post by kc5hwb on 2013-04-03
> **Morbius1 said:**
> You did not get the following error by removing all of your samba usershares:

You did something else on your Windows machine to induce that error.

I didn't remove all of my Samba shares, I removed the check boxes in Nautilus, and then added the line "valid user = jape" to my smb.conf file.  Nothing else was changed, including on my Windows boxes.

---

### Post by kc5hwb on 2013-04-03
OK, I went back into /etc/samba/smb.conf and removed all the share info:
```
[share]
comment = Tonido Raid
path = /home/jape/Raid
read only = No
create mask = 0777
valid users = jape
```


Then I went into Nautilus and made these changes:
[IMG]http://aints.net/images/share.jpg[/IMG]
This is working now, but I am not sure its exactly what I was going for.  However, when I connected from my Windows box, it did prompt me for my username and password, which I typed as "<ubuntu.computer.name\jape> and my password.  This connected and I am able to make changed, create folders, etc.

---

### Post by kc5hwb on 2013-04-03
I think I found the rogue connection.  It wasn't anything I changed, however;  it's existed for some time.  But I removed the check-marks from Nautilus, then re-applied the code lines to smb.conf and restarted Samba; all seems to be working as expected now.  I want to test for the rest of the day and from a couple of other boxes on my network when I get home, but I think we are done.

Thanks for your help, Morbius1.

---

