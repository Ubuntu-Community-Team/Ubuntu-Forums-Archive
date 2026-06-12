---
title: "Load SSH key at logon"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by teranex on 2008-11-23
Using the 'Passwords and Encryption keys'-tool i have created a SSH-key to login to my webhost. Now everytime when i logon, i'm presented with a window that tells my an application wants to use this key (and i need to unlock the key). Now i'd like to know which application does this request, because i use this key only to login to my host with Nautilus and SSH, but no other programs should be using it i guess.

I have the following apps added to my session for automatic startup:
- pidgin
- thunderbird
- gnome-do
- beagle
- deskbar-applet

i also have a bookmark in nautilus to my webhost (sftp://...)

is it somehow possible to see which program is asking to unlock the key?

thx!

---

### Post by teranex on 2008-11-24
Nobody has a clue how i can see which program is asking me to unlock my key? Or is my question not very clear?

---

### Post by Dr Small on 2008-11-24
It's probably gnome-keyring.

---

### Post by teranex on 2008-11-24
> **Dr Small said:**
> It's probably gnome-keyring.

thanks! I think i found why i'm asked to unlock the key as soon as i log on:
[http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh)
> The SSH agent automatically loads files in ~/.ssh having names starting with id_rsa or id_dsa, e.g. ~/.ssh/id_rsa_gnome or just ~/.ssh/id_rsa. Other X.509 private keys marked with the 'ssh-authentication' purpose are also usable. 
The key that i generated was indeed called 'id_rsa'. When i renamed, the files (both the private and the public key), and logged-on again, i'm not asked anymore to unlock the key. However in that case i can't log-in to the server anymore with my key. I tried to let the tool configure the server again, but it added the exact same public key to the authorized_hosts on the server... i'l need to play a bit more with that, at least now i know where to look :)

---

