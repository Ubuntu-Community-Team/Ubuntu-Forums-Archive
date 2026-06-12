---
title: "Windows cannot access Linux share"
date: 2019-07-15
forum: New to Ubuntu
---

### Post by mwoosley on 2019-07-15
Hello again everyone.  I am again in need of help from you subject matter experts.  

I recently had some problems with my 18.04 (server) instance so I scrapped it and reinstalled the desktop version.

Quite frankly, I think I like it better than the server version as many of the problems I had before are now less and less.

What I'm having difficulty with now is getting Windows 10 to recognize my shares on the Linux box.  

I had to install Samba and once that was complete, I was able (from the GUI) to create a local network share.  After doing this, I went into the smb.conf file to verify that the share was added, and it WAS NOT.  So, I opened it and added the share at the end of the file.

After reading a few posts, I discovered that I had forgotten to add myself as a Samba user (thinking this was going to fix me up).  However, after adding myself, I still couldn't access the folder share via Windows10.

So, my questions are, what am I potentially doing wrong?  AND Why didn't the GUI 'share local network' modify the smb.conf file after setting it from the desktop?

---

### Post by dino99 on 2019-07-16
Here is a detailed howto [https://www.technig.com/share-file-between-ubuntu-and-windows/](https://www.technig.com/share-file-between-ubuntu-and-windows/)
but you can find more yourself digging around "ubuntu windows 10 share" on the net.

---

### Post by mastablasta on 2019-07-16
you need to be in same workgroup. then it should work pretty much out of the box. you create a folder and it will appear in the network. if it doesn't sometimes you can get to it manually by typing in the server address and server folder..

---

### Post by SeijiSensei on 2019-07-16
Windows also understands "UNC" names like \\servername\share or \\ip.addr.of.server\share.

"servername" can also be a fully-qualified hostname that can be found with DNS, e.g.,
"\\server.example.com\share".

---

### Post by mwoosley on 2019-07-16
Alright, no matter what I do, I continue to get a "Windows cannot access \\192.168.1.100\downloads" error message.

On my Windows10 PC, I have the workgroup set to WORKGROUP

I have the Windows hosts file set to...

192.168.1.100    myserver
127.0.0.1           localhost
::1                     localhost

On my physical Linux machine, Ubuntu Desktop 18.04, I have the following set in the "/etc/hosts file...

192.168.1.100    myserver
127.0.0.1           localhost
::1                     localhost



and  the /etc/samba/smb.conf" file... 

[global]

workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
wins support = yes
dns proxy = no

##Networking##

##Debugging/Accounting##
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

##Authentication##
server role = standalone server
passdb backend = tdbsam
obey pam restrictions = yes
encrypt passwords = true
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\sne\s*\spassword:* %n\n Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

##Domains##

##Misc##
usershare allow guests = yes

##Share definitions##
[homes]
comment = home directory
browseable = no
read only = no
create mask = 0700
directory mask = 0700

[profiles]
comment = User profiles
path = /home/samba/profiles
guest ok = no
browseable = no
create mask = 0600
directory mask = 0600

[printers]
comment = printer drivers
path = /var/spool/samba
printable = yes
guest ok = no
read only = yes
create mask = 0700

[downloads]
path = /home/me/downloads
guest ok = no
guest only = no
writable = yes
read only = no
valid user = me

I'm assuming I have all the parameters set right, but for the life of me, I cannot get Windows to recognize the Linux share... instead, providing the above listed error.

---

### Post by mastablasta on 2019-07-17
```
[COLOR=#000000][downloads][/COLOR]
[COLOR=#000000]path = /home/me/downloads[/COLOR]
[COLOR=#000000]guest ok = no[/COLOR]
[COLOR=#000000]guest only = no[/COLOR]
[COLOR=#000000]writable = yes[/COLOR]
[COLOR=#000000]read only = no[/COLOR]
[COLOR=#000000]valid user = me[/COLOR]
```

so who can access it then? user called "me"? is user from windows also called "me"? does it even ask for password?

i would give full access to public folder (using right click in file manager), put a small .txt file inside (just for testing). then try to access it. if it works, then start adding restrictions.

---

### Post by Morbius1 on 2019-07-17
These are more housekeeping observations but I would suggest cleaning them up first:

> Why didn't the GUI 'share local network' modify the smb.conf file after setting it from the desktop?         
Ubuntu provides two different ways to create samba shares. One is through smb.conf and the other is through Nautilus ( Files ) which creates the share definition in /var/lib/samba/usershares . You likely have a duplicate share definition which might cause conflicts with the one you have in smb.conf. Run the following command to see if you have a duplicate. Then decide which of the two you want to keep :
```
net usershare info --long
```

> [COLOR=#000000][downloads][/COLOR]
[COLOR=#000000]path = /home/me/downloads[/COLOR]
[COLOR=#000000]guest ok = no[/COLOR]
[COLOR=#000000]guest only = no[/COLOR]
[COLOR=#000000]writable = yes[/COLOR]
[COLOR=#000000]read only = no[/COLOR]
[COLOR=#000000]valid user = me[/COLOR]
[COLOR=#0000cd]**First**[/COLOR]: What mastablaster said. I never know if a user actually means "me" because that's the silly thing Nautilus shows, if he doesn't want us to know what his real user name is, or if he actually has a user named "me" but it needs to be a real user name.

[COLOR=#0000cd]**Second**[/COLOR]: There is no such samba paramater as "**valid user**". It's "**valid user[COLOR=#0000cd]s[/COLOR]**" - plural user.

These are just questions:

*** What's with the [profiles] section of smb.conf. Is this just a home network with you and a Win10 box or is this some convoluted Active Directory thing you've created?

*** Is your home directory encrypted?

---

### Post by mwoosley on 2019-07-17
Thanks mastablasta.  me is the substitute name I used just for this thread... I actually have a nickname I appropriately use :lolflag: .  Between you and Morbius1, I've decided to comment out the shares in the smb.conf file and let the system use the Nautilus generated file.  When I right click on a folder and create a share and then view my shares with the command from Morbius1 ([COLOR=#000000][FONT=&quot]net usershare info --long), I see where the /var/lib/samba/usershares folder share files are created.  As far as I'm concerned, at this point, while the switches look differently than the manually generated ones in smb.conf, I think I can live with this until I get better at setting things up.

After commenting out the share definitions in smb.conf and using Nautilus share config, and sharing the "Public" folder in my home directory, I still get the dreaded "Windows cannot access \\myserver\Public folder.  I placed a zero byte file in there as well with no change in outcome.  

It seems that Windows10 is preventing me from accessing the shared file and I don't understand why.[/FONT][/COLOR]

---

### Post by mwoosley on 2019-07-17
Thanks Morbius1.  

me is the substitute name I used just for this thread... I actually have a nickname I appropriately use :lolflag: .  Between you and mastablasta, I've decided to comment out the shares in the smb.conf file and let the system use the Nautilus generated file.  When I right click on a folder and create a share and then view my shares with the command from Morbius1 ([COLOR=#000000][FONT=&quot]net usershare info --long), I see where the /var/lib/samba/usershares folder share files are created.  As far as I'm concerned, at this point, while the switches look differently than the manually generated ones in smb.conf, I think I can live with this until I get better at setting things up.

After commenting out the share definitions in smb.conf and using Nautilus share config, and sharing the "Public" folder in my home directory, I still get the dreaded "Windows cannot access \\myserver\Public folder.  I placed a zero byte file in there as well with no change in outcome.  

It seems that Windows10 is preventing me from accessing the shared file and I don't understand why.

I really don't have a [Profiles] share... it was in a sample config file and I included it only to solicit comments on in and whether it is needed.  I'm assuming you believe it is unnecessary.  

Lastly, what should be done with the smb.conf file?  Should I comment out EVERY line and let the Nautilus config file take care of everything, or should I only comment out the share definitions?

Thank you very much for your assistance with this... I hope to get to the bottom of it soon.  My luck there is something wrong with the Windows environment, which I've seen some subtle hints (from a few months ago) that sharing was having issues.[/FONT][/COLOR]

---

### Post by Morbius1 on 2019-07-17
> [COLOR=#000000][FONT=&amp]Lastly, what  should be done with the smb.conf file?  Should I comment out EVERY line  and let the Nautilus config file take care of everything, or should I  only comment out the share definitions?[/FONT][/COLOR]
smb.conf controls how your samba server operates. It is in control of how the shares you create in Nautilus are interpreted - for example the "usershare allow guests = yes" determines if you can create a guest accessible share from Nautilus. You cannot have a samba server without it.

> [COLOR=#000000][FONT=&amp]I still get the dreaded "Windows cannot access \\myserver\Public folder.[/FONT][/COLOR]
What is the next line in the error message:

Is it a "You do not have permissions to access ...."

Or is it a "Check the spelling of the name ..." type of message.

Those are two different problems.

---

### Post by mastablasta on 2019-07-18
in general the windows user needs the permit to access the server. which is why (and just to see if it works) i suggested that access should be enabled to anyone on the LAN, just to see if it works.

also i suggest to at least add a letter to the test file.

by the way, safest method is actually sFTP protocol with keys, but for that you need filezilla or similar on windows and OpenSSH on linux. i find samba ok to move files inside LAN. i know it works easily on Win7 and XP but i never tried it on windows 10, however it should work just as easy. i doubt they did any changes to this part of the windows OS.

---

### Post by SeijiSensei on 2019-07-19
By default, the Downloads folder in Ubuntu begins with a capital "D". Linux is case-sensitive. So perhaps what you have as 

```

[downloads]
path = /home/me/downloads

```

should be

```

[downloads]
path = /home/me/Downloads

``` 

The share name can be whatever you want it to be, but the "path" has to point to a valid directory name.

---

