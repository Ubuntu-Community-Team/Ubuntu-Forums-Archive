---
title: "I cannot install any program"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by ahmed_nasr on 2008-06-07
Hi ,

I am trying to install VLC media player

I type the command : 

> sudo apt-get update

and I get this  :
> 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i get it too when i type the install command :

> sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc


also when i try to use synaptic manager i get this :

[IMG]http://b.imagehost.org/0021/Screenshot-synaptic.png[/IMG]

so can anybody help me plz ?

---

### Post by kansasnoob on 2008-06-07
I had the same problem (I think) and got the answer here:

[http://ubuntuforums.org/showthread.php?t=772186](http://ubuntuforums.org/showthread.php?t=772186)

---

### Post by kansasnoob on 2008-06-07
Oh, and you may have to use this command, BUT I"M NOT SURE:

sudo dpkg --configure -a

it may be:

sudo dpkg --configure -a && sudo apt-get -f install

Just wait a tiny bit and see if these commands are recommended by anyone else, OK?

---

### Post by Level367 on 2008-06-07
Hi There,

Use the sound and video option in Ubuntu. Ti work fine.
Otherwise doubleclick on the file and let Ubuntu search for the file or add on that needs to be install to play your video etc. VLC is a good application but Ubuntu has a solution.

---

### Post by ahmed_nasr on 2008-06-07
that solved only the first part of the problem which is :
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

but i still get this :
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


and when i run  'dpkg --configure -a'

i get :
> dpkg: requested operation requires superuser privilege

---

### Post by ahmed_nasr on 2008-06-07
it's not about VLC ... it's about installing applications ...

---

### Post by st33med on 2008-06-07
do:
```
sudo dpkg --configure -a
```

---

### Post by avtolle on 2008-06-07
You must type```
sudo dpkg --configure -a
```

---

### Post by ahmed_nasr on 2008-06-07
thanks this worked

but what is 'sudo' anyway ?

---

### Post by st33med on 2008-06-07
sudo gives you root privileges. Use it sparingly, however, because you could bork a program by altering its file permissions to root. EG: 'sudo firefox' would make it so that firefox possibly could not run or that it will not use any of your plugins.

---

