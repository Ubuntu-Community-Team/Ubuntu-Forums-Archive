---
title: "errors after sudo apt-get update"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by cyclone_ on 2011-10-26
Hi, 
My system has been working somewhat slower the last few days and I dont know why.
I recently tried to install[ crebs]("http://www.obfuscatepenguin.net/crebs/"), and during the installation:

sudo add-apt-repository ppa:crebs/ppa 
sudo apt-get update 
sudo apt-get install crebs

I noted these error messages:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources 404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages 404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources 404  Not Found

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US             Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages 404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

I am a newbie so I dont really know how to problem search in linux nor do I know the significance of various error messages. I thought the first 5 errors sounded significant so I they are perhaps worth asking about.
Any help would be really great, thanks!!

---

### Post by airplanesimen on 2011-10-26
> **cyclone_ said:**
> Hi, 
My system has been working somewhat slower the last few days and I dont know why.
I recently tried to install[ crebs]("http://www.obfuscatepenguin.net/crebs/"), and during the installation:
sudo add-apt-repository ppa:crebs/ppa sudo apt-get update sudo apt-get install crebsI noted these error messages:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources 404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages 404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources 404  Not Found

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US             Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages 404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

I am a newbie so I dont really know how to problem search in linux nor do I know the significance of various error messages. I thought the first 5 errors sounded significant so I they are perhaps worth asking about.
Any help would be really great, thanks!!

are you using a proxy? It seemes to be an error for ur network connection. try to check your settings:P go to your menu, and type: "proxy" (if u have a new ubuntu)

---

### Post by cyclone_ on 2011-10-26
I am not intentionally using a proxy. When typing proxy into terminal I get:

The program 'proxy' is currently not installed.  You can install it by typing:
sudo apt-get install libproxy-tools

When typing it into 'Dash home' I dont find anything. 
Perhaps I am misunderstanding? But you are probably onto something, I got an error message the other day saying something incomprehensible about network settings.

---

### Post by Elfy on 2011-10-26
It's those 3 ppa's 

Go to Software Sources via either Update Manager Settings or Synaptic - Settings - Repositories and disable them

2 only have repos to Lucid and the other for Natty

---

### Post by airplanesimen on 2011-10-26
> **cyclone_ said:**
> I am not intentionally using a proxy. When typing proxy into terminal I get:

The program 'proxy' is currently not installed.  You can install it by typing:
sudo apt-get install libproxy-tools

When typing it into 'Dash home' I dont find anything. 
Perhaps I am misunderstanding? But you are probably onto something, I got an error message the other day saying something incomprehensible about network settings.

ok :P I meant in dash home, but it didnt work for me as well, so sorry!:guitar:

---

### Post by cyclone_ on 2011-10-26
I am sorry, I find the tab 'Other software' in 'software sources'. But there I could only find these:

 [http://ppa.launchpad.net/rvm/smplaye...source/Sources]("http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/source/Sources")
  [http://ppa.launchpad.net/rvm/smplaye...-i386/Packages]("http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/oneiric/main/binary-i386/Packages") 
  [http://ppa.launchpad.net/crebs/ppa/u...source/Sources]("http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources") 

is that enough?

---

### Post by Elfy on 2011-10-26
Yep - those are the ones.
Untick them and reload.

---

### Post by raja.genupula on 2011-10-26
after doing as above post try to update your system 
with **sudo apt-get udpate** and post what you got . If any error still exists then from **update manager-> settings change your server** and then try update . 

Let us know what you got.

all the best.

---

### Post by cyclone_ on 2011-10-26
I am no longer getting any error messages when running sudo apt-get update! Thank you so much for your help!!!

---

### Post by Elfy on 2011-10-26
Welcome :)

---

