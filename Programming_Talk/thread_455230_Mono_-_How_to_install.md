---
title: "Mono - How to install"
date: 2007-05-26
forum: Programming Talk
---

### Post by ade234uk on 2007-05-26
I know not many like mono for various reasons, but I would like to learn something new so I can create applications in Ubuntu.

I all started today when I created some shorcuts on my Desktop to start and stop Apace and thought, that would be good if I could create a GUI for it.

So does anyone know how I install Mono in Ubuntu which will allow me to create small applications.

Thanks

---

### Post by ankursethi on 2007-05-26
In terminal do :
> sudo apt-get install monodevelop monodoc

This will install the IDE and all the required libraries. It's listed under Applications -> Programming

---

### Post by ade234uk on 2007-05-27
Brilliant, thank you very much.

---

### Post by Jacquers on 2007-06-06
I installed mono v1.2.4 by using the generic .bin download from the mono site and just double clicking the file. (I'm running Ubuntu on a VM without internet connection so I cant use the "normal" method off getting it). The version that came installed with mono was 1.2.3. 

The new one installed to a folder in my home folder and it's working fine. There is just one thing bothering me:
In the terminal I type mono -V and it shows that it's version 1.2.4. If I go to /usr/bin and type mono -V then it says 1.2.3. Is this because of the way I installed it or perhaps the location, or maybe because my desktop user does not have write permissions for the /usr/bin folder?

How should I have installed it from the .bin?

---

