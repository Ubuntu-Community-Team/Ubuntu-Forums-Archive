---
title: "Envy Error"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by 124C41+ on 2008-04-28
When I ran Envy in 7,10 lastnight it gave me a 
"Error: Dependency is not satisfiable:debhelp" error. 

Today when I bring it up in 8.10 it gives me 
 "Error: Dependency is not satisfiable: libstdc++5"

Im trying to run envy for a X1950 PCI-E card. 

Whats my next step. Thanks

---

### Post by tamoneya on 2008-04-28
try this```
sudo apt-get install libstdc++5
```

---

### Post by 124C41+ on 2008-04-28
Return looked like this. 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5


---

### Post by Oldsoldier2003 on 2008-04-28
are you using Envy NG (the latest version and the proper version to use for Hardy) also have a look at the FAQ's over at the [ENVY]("http://albertomilone.com/nvidia_scripts1.html") site or file a bug if they don't help you out.

Enyvy is a pretty good tool but honestly for third party scripts such as this you generally get much better support in the developers own venue. All most of us can say is yeah I tried it and it worked/didn't work or maybe point you to a possible workaround.

---

### Post by 124C41+ on 2008-04-28
O.K I am goign to try EnvyNG

When I type
sudo apt-get install envyng-gtk
 
I get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk

I get the same thing every time I try and apt-get something. How do I fix it.

---

### Post by 124C41+ on 2008-04-28
Is there anybody out there?

---

### Post by sdlyr8 on 2008-06-08
Has anyone had any luck with this? I am getting the same error when I try to install envyng-gtk. 
```
$ sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk

```

I have all the repositories enabled so I know that's not it but I don't know what else to try.

---

### Post by prvteprts on 2009-03-01
I have the same problem:

sudo apt-get install envyg-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyg-gtk

Seems as if the Envy package disappeared from the repository.

---

### Post by binbash on 2009-03-01
sudo apt-cache search envy
alsa-tools-gui - GUI based ALSA utilities for specific hardware
envyng-core - install the ATI or the NVIDIA driver
envyng-gtk - dummy package to envyng-core


Are you using intrepid?

---

### Post by kelvin spratt on 2009-03-01
Try sudo apt-get update before trying to download anything then see what happens, envy has never been a problem in the past.

---

