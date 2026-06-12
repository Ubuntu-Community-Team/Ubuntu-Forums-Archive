---
title: "Samba and Windows"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by waterrr on 2008-07-10
How can I access the Samba on my Ubuntu Server from a Windows pc?

---

### Post by tech9 on 2008-07-10
> **waterrr said:**
> How can I access the Samba on my Ubuntu Server from a Windows pc?

  	 	 	 	 	 	  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=6]**simple setup samba ubuntu**[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]With samba, you can pretty much setup a configuration in a matter of 10 minutes. Especially if you are using Ubuntu. (Note: this applies to Breezy and Dapper)[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]Couple of things of note. I recommend using a different user than your default user. For example, you might setup a 'samba' user.[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]Go ahead and create a user 'samba' (Easy with the Ubuntu UI). You won't need to modify access levels.[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]Perform the install:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]**apt-get install samba**[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]cd /etc/samba[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]Edit the 'smb.conf' to the configuration that you might want. I simply went with editing the writable share definitions with the following: (See section '[homes]')[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]**writable = yes**[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]Next, you want to add your user through 'smbpasswd' which you can do with:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]**smbpasswd -a samba**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2] 
Where 'samba' represents the username.[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]On the windows side (or mac?) Map the network drive with the ip. You might do the following:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]\10.0.0.0\samba\samba 
(Actually there is an extra samba with the directory I created 'cd samba && mkdir samba')[/SIZE][/FONT][/COLOR]

---

### Post by waterrr on 2008-07-10
So I just map it with \ip\username\drive ?

---

### Post by waterrr on 2008-07-10
I created a samba user but it won't allow me to do smdpasswd -a samba - it gives me an error

::EDIT::
I'm able to add the user samba now

---

### Post by tech9 on 2008-07-10
> **waterrr said:**
> So I just map it with \ip\username\drive ?

you want to create a share in Linux ... example /home/username

so you should be able to map to it via \\ip\home\username from windows

also make sure you edit the [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]smb.conf file to make your share writable otherwise it will not work[/SIZE][/FONT][/COLOR]

---

### Post by tech9 on 2008-07-10
> **waterrr said:**
> I created a samba user but it won't allow me to do smdpasswd -a samba - it gives me an error

::EDIT::
I'm able to add the user samba now

remember to use sudo 'commmand'

try this 

```
sudo smbpasswd -a admin
```  where admin is the user name you are using with your linux account...

Then you should have prompt like this...
[sudo] password for admin:

enter any password that you want for your samba account.


Then when connecting to your linux box from windows

\\ip\home\admin

use your username
and password that you just created.

Let me know how this works for you

---

### Post by waterrr on 2008-07-10
admin is my default account - do I have to add that by sudo smbpasswd -a admin? and then I tried to connect (via mac) smb://the ip/home/admin/docs with docs being the shared folder and it wasn't able to connect

---

### Post by tech9 on 2008-07-10
> **waterrr said:**
> admin is my default account - do I have to add that by sudo smbpasswd -a admin? and then I tried to connect (via mac) smb://the ip/home/admin/docs with docs being the shared folder and it wasn't able to connect

on a share you should be able to access it from \\ip\share

see 3rd post above from here. I added a lot more thorough instructions

---

### Post by waterrr on 2008-07-10
I did sudo smbpasswd -a admin and created a password.
Then I tried to connect and input the username admin and input the password, then I received an error saying "The operation cannot be completed because one or more required items cannot be found. (Error Code -43).

---

### Post by waterrr on 2008-07-10
from the mac I clicked on go->connect to server then I input the server address as smb://ipaddress/home/admin

---

### Post by tech9 on 2008-07-10
> **waterrr said:**
> from the mac I clicked on go->connect to server then I input the server address as smb://ipaddress/home/admin


hmmm.. did you edit the samba.cfg file 

and make sure that the file are writable

[COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2][B]writable = yes

I have to go, but I can check back later - good luck
[/B][/SIZE][/FONT][/COLOR]

---

### Post by tech9 on 2008-07-11
> **waterrr said:**
> from the mac I clicked on go->connect to server then I input the server address as smb://ipaddress/home/admin

I am not sure about this from a mac perspective, but I don't think you need to include smb://

just try //ip/home/admin

---

### Post by waterrr on 2008-07-14
I changed the writeable=yes from the very beginning and without the smb:// it goes nowhere - It's just the log up screen pops up and I get an error

---

### Post by waterrr on 2008-07-14
This is my error, as I've stated before:

"The operation cannot be completed because one or more required items cannot be found. (Error Code -43)."

---

### Post by waterrr on 2008-07-14
The samba on the Ubuntu is able to recognize a printer on a windows computer via samba, but when I try to connect to the sambia via windows...I am not sucessful (still not able to connect from the mac either)

---

### Post by waterrr on 2008-07-14
I'm still getting the error code -43 on the mac - can anybody help?

---

### Post by waterrr on 2008-07-14
Problem solved, just used the direct IP instead of trying to map it to a address

---

### Post by Thelasko on 2008-07-14
I found the 'system-config-samba' package to be a big help.  But I'm one of those poor souls that prefers a GUI.

---

### Post by tech9 on 2008-07-15
> **waterrr said:**
> Problem solved, just used the direct IP instead of trying to map it to a address

excellent!

---

