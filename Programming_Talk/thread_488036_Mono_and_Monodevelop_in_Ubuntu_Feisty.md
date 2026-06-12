---
title: "Mono and Monodevelop in Ubuntu Feisty"
date: 2007-06-29
forum: Programming Talk
---

### Post by aquiles_caigo on 2007-06-29
Hello everybody!
I've been asking around the internet, but never seem to find a good answer!
perhaps you can help me!.

The thing is im trying to install mono along with monodevelop under Ubuntu Fesity.
I want to program using C# and Gtk along with database accessibility (maybe Mysql if possible) ... and i dont know which packages are needed... 
It is frustrating that there is no documentation available for Ubuntu users who want to program using mono (updated documentation)

---

### Post by asmweb on 2007-06-29
well i think that mono is already available on the system as default ... check it on /etc/mono/ on the other side you have to download the monodevelop tool through apt-get install monodevelop. It will get you automatically the other packages. On this site [http://www.go-mono.com/docs/](http://www.go-mono.com/docs/) you can get the api-s

hope it helped

---

### Post by Yoooder on 2007-06-29
you might also be interested in the monodoc packages, it provides mono documentation and a viewer for it:

sudo apt-get install monodoc

---

### Post by aquiles_caigo on 2007-06-29
so do you mean that just by installing monodevelop i have all what is needed to program? using gtk# and c#?
dont i need like a c# compiler or something? or Gtk# package ??
Well.. thats what really confuses me!

anyway thanks for your quick answers!!

---

### Post by asmweb on 2007-06-30
well the mono complier is installed by default as I said earlier and I you miss any package synaptic will get it for you... I don't see why that creates you confusion. By the way mono is not 100% of what you might get from c# ... take a look at the api's

---

### Post by ankursethi on 2007-06-30
The version of Monodevelop in the repositories is old. You can get the newest version as a deb from GetDeb.net, along with the SQL support. All dependencies will be resolved when you install the packages (just double click the deb files you download).

---

