---
title: "Updating from 12.04 to 14.04"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by 393 on 2014-04-23
I am currently using 12.04 ubuntu  and I would like to update to 14.04.  How do I do this without destroying information on my harddrive and keep all my software?

---

### Post by jdeca57 on 2014-04-23
I didn't do that myself, but [http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04](http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04) seems convincing. Do make a backup (one never knows) and be aware that some packages will be removed, UbuntuOne for example.

---

### Post by cwmoser on 2014-04-23
Hi, I am doing the same thing  ....  running Ubuntu 12.04 and simultaneously setting up 14.04.

I configured my hard drive like this:
/dev/sda1  15GB for Ubuntu 14.04
/dev/sda2  Swap
/dev/sda3  /home
/dev/sda4  15GB for my Ubuntu 12.04


While testing I shared /home with both 12.04 and 14.04 but ran into some problems.
The biggest problem was that when I booted 14.04 it clobbered my Evolution Mail program
and I had to load my Evolution data from backup.

To continue, I modified 14.04's  /etc/fstab  file so that its home was on my second hard drive -- /dev/sda3.
This made 14.04 to leave my Evolution email alone.

What I am going to do is to continue configuring 14.04 and when done combine the two /home partitions
by selectively copying certain data to my /home on /dev/sda3.  I have a Solid State Drive for /dev/sda and
want to eventually have my /home on that drive.

I did not realize all the configurations I had made to 12.04 ... gonna take some time.

I did run this command to geta list of all packages I installed with 12.04:
$  **dpkg  --get-selections  |  grep  -v  deinstall  >  installed-software**

On 14.04, I'm going to edit the **installed-software** file and then install everything using this command:
$  sudo  dpkg  --set-selections  <  installed-software
$  sudo  apt-get  autoremove
$  sudo  apt-get  update

Carl

---

### Post by cwmoser on 2014-04-23
That does look interesting to just upgrade 12.04 to 14.04 as mentioned in post #2.
Like to hear from some users who have done this though.
Wonder what the pros/cons of that approach?

Carl

---

### Post by edeneen on 2014-04-23
I have just done this, just boot from CD or USB and select "upgrade ubuntu" option, it kept all my files and stuff, but I did have to reinstall a few app. packages

---

### Post by cwmoser on 2014-04-23
> **edeneen said:**
> I have just done this, just boot from CD or USB and select "upgrade ubuntu" option, it kept all my files and stuff, but I did have to reinstall a few app. packages

Looks like I'm doing it the hard way.
I'm also documenting how I customized 14.04 to my liking.

BTW, is your Places -> Connect to Server working?
In 14.04, I cannot get this to work.

Carl

---

### Post by 393 on 2014-04-23
wow, I am amazed it it that easy.  What packages did you lose?  Anything in particular?  What was spared destruction?

---

### Post by edeneen on 2014-04-23
> **393 said:**
> wow, I am amazed it it that easy.  What packages did you lose?  Anything in particular?  What was spared destruction?

well I remember I had to reinstall my music player

---

