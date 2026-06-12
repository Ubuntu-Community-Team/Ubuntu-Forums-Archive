---
title: "Help - Unlock default keyring password"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by natsonice on 2011-11-18
Hi 

I am not a computer wizz and i'm totally new to Ubuntu so any help would be really appreciated.

I bought a second hand dell netbook with Ubuntu on it, only i don't have the password to unlock the default keyring. The person i bought it from can't remember  it. Its currently running a really old version and i can't install programs or even upgrade ubuntu because without this password it wont let me do anything. Im at a total loss as to what to do.How do i change or delete the password so i can install and upgrade programs? i cant even take a screen print when it pops up, but it states the following:

enter password for default keyring to unlock

Help!!!

N

---

### Post by Megaptera on 2011-11-18
I hope this guide with screenshots is of help? 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by natsonice on 2011-11-18
> **Megaptera said:**
> I hope this guide with screenshots is of help? 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Hi

THanks for th link. Unfortunately when i hold in the shift key it just comes up with a black screen and MBR 2FA: in the top left corner. Any ideas?

---

### Post by haqking on 2011-11-18
Are you talking about the keyring password or the sudo/login password ? they are different things.

---

### Post by natsonice on 2011-11-18
> **haqking said:**
> Are you talking about the keyring password or the sudo/login password ? they are different things.
Its the keyring password. i can log on to the netbook fine, its just this keyring is stopping me from downloading any programs. i hope this is the right answer, like i say im totally useless when it comes to computers!

---

### Post by haqking on 2011-11-18
> **natsonice said:**
> Its the keyring password. i can log on to the netbook fine, its just this keyring is stopping me from downloading any programs. i hope this is the right answer, like i say im totally useless when it comes to computers!

OK well the keyring password is likely preventing you from downloading as it is needed to unlock say your wireless key.

If you logged in ok and are a member of the sudo group you can delete the keyring.

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

or to delete it then Or just open /home/<username>, click "show hidden file" go to .gnome2 , open it and delete the folder keyring

but make sure you know the passwords/keys to anything in here.

Have you tried entering your login password to the keyring though ?

then just set a new one to be blank or whatever password you want

---

### Post by natsonice on 2011-11-18
This may be a really stupid question, but what is the sudo group?

I don't need to enter a password at start up, it automatically just loads and brings up the desktop.

just checking out your link now

Ta

---

### Post by natsonice on 2011-11-18
this gets weirder - there are no keys in there! totally lost ! i get what the keyring does now.

when it pops up i keep clicking deny and i can log on to the internet, but thats abuot the only thing. when i want to download anything i need to enter the password, hitting deny refuses me to download.

---

### Post by haqking on 2011-11-18
> **natsonice said:**
> This may be a really stupid question, but what is the sudo group?

I don't need to enter a password at start up, it automatically just loads and brings up the desktop.

just checking out your link now

Ta

ok so you have automatic login enabled then.

sudo is to allow a normal user perform admin tasks, see [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

if you type 

```
groups
```

in terminal it will tell you if you are in the sudo group

as for the mbr 2fa message, trying pressing 2 when you get that message.

---

### Post by haqking on 2011-11-18
> **natsonice said:**
> this gets weirder - there are no keys in there! totally lost ! i get what the keyring does now.

when it pops up i keep clicking deny and i can log on to the internet, but thats abuot the only thing. when i want to download anything i need to enter the password, hitting deny refuses me to download.

downloading asks for the keyring password ?

or you mean when trying to install with downloading it asks for a password ? this would be the sudo password which apparently you dont know so you need to reset it.

---

### Post by natsonice on 2011-11-18
when i type in groups it comes up with the following

lauren adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse

sorry my lack of is knowledge is probably infuriating and making things worse

---

