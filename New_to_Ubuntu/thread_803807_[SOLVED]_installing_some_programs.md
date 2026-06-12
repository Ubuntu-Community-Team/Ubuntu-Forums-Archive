---
title: "[SOLVED] installing some programs"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by RefinersFire on 2008-05-22
I cannot install various programs, such as RealPlayer (for Linux) or HelixPlayer. Also, RPMs & BINs I cannot install. No instructions are provided with the program. I tried sudo ./RealPlayer11GOLD.bin, which did not work.

How do I install programs that are only available as .rpm or .bin?

Thanks.

---

### Post by benevolent on 2008-05-22
hmm... first of all try searching for .deb packages instead of .rpm!


second, Try ```
sudo chmod 755 <file.bin>
``` and then ```
sudo ./file.bin
```


edit: A very good site for deb packages is [www.getdeb.net](www.getdeb.net) . Also you can use add/remove or synaptic to search through repositories for more programs.

---

### Post by CanadianLinux on 2008-05-22
I "was" a windows user before I met Ubuntu. Here is where you will find all your install questions.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by shifty_powers on 2008-05-22
rpm's are designed for a different distro, i.e. any based on redhat. ubuntu is based on debain and uses .deb files.

as for real player, why do you need it?

---

### Post by Maestro23 on 2008-05-22
Install anything in Ubuntu: 

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)


> .bin files

sudo chmod +x filename.bin

sudo ./filename.bin

> .rpm (need to get alien from repos 1st) (Not recommended, try and find .deb)

sudo apt-get install alien

sudo alien -i package_file.rpm


---

### Post by shifty_powers on 2008-05-22
the use of alien isn't advised if possible, can do nasty things ;)

---

### Post by Maestro23 on 2008-05-22
> **shifty_powers said:**
> the use of alien isn't advised if possible, can do nasty things ;)

Yeah, hence my warning. :wink:

---

### Post by billgoldberg on 2008-05-22
.rpm package won't work with Ubuntu.

They are made for another set of distro's based on red hat.

You can easily install a .bin, but first you must make it executable.

You could use chmod for that, but you can also just right-click it, go to properties. Then in one of the tabs mark "allow executing file as program".

If you need help to install real player (NOT ADVISED!!!), look here:

[http://linuxowns.wordpress.com/2008/04/15/real-player-11/](http://linuxowns.wordpress.com/2008/04/15/real-player-11/)

---

### Post by RefinersFire on 2008-05-22
The reason that I need Real Player is because I like to listen to online sermons, which are only available in .ram (Real Player file), and I would like to phase out my Windows PC as much as possible. 
I have used the Windows system today to listen to sermons, but I would like to start using my Ubuntu system.

Thank you.

---

### Post by RefinersFire on 2008-05-25
Does anyone have any ideas or suggestions that will allow me to listen to .ram files on this system? Real Player or otherwise.

Thanks.

---

