---
title: "Waste P2P Darknet"
date: 2005-03-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Pirate_Will on 2005-03-26
This is my first thread, so if ive messed something up please correct me. 

Way back when I was still using Win$lows, I found Waste a great program to share odd files with friends, I only got a very small network going and the transfer speeds are nothing to write home about but its good at what it does.

Heres the website : [http://waste.sourceforge.net/](http://waste.sourceforge.net/)

Anyway after a lot of waiting they have finally released a client for linux. 

First of all you will need to compile the wxAll package available here:

[http://www.wxwindows.org/](http://www.wxwindows.org/)

(Package availible directly here)
[http://prdownloads.sourceforge.net/wxwindows/wxAll-2.5.4.tar.gz](http://prdownloads.sourceforge.net/wxwindows/wxAll-2.5.4.tar.gz)

WARNING - This is a development snapshot and while ive not had any problems with mine at least be aware that you could run into difficulties

I then picked up the Waste crossplatform source from here:

[http://prdownloads.sourceforge.net/waste/waste-source-wxwidgets-1.5-beta-3.zip?download](http://prdownloads.sourceforge.net/waste/waste-source-wxwidgets-1.5-beta-3.zip?download)

Again compiling this was not a great problem, however when it came to running the finished product I (and many others) got the error:

./waste: error while loading shared libraries: libwx_gtk2u_xrc-2.5.so.3: cannot open shared object file: No such file or directory  

Anyway on to the How-To proper

you will need to create several symbolic links and then all should be peachy

$ cd /usr/lib
$ sudo ln -s libwx_gtku_xrc-2.5.so.3 libwx_gtk_xrc-2.5.so.3 
$ sudo ln -s /usr/local/lib/libwx_gtk2_xrc-2.5.so.4 libwx_gtk2_xrc-2.5.so.4
$ sudo ln -s /usr/local/lib/libwx_gtk2_html-2.5.so.4 libwx_gtk2_html-2.5.so.4
$ sudo ln -s /usr/local/lib/libwx_gtk2_adv-2.5.so.4 libwx_gtk2_adv-2.5.so.4
$ sudo ln -s /usr/local/lib/libwx_gtk2_core-2.5.so.4 libwx_gtk2_core-2.5.so.4
$ sudo ln -s /usr/local/lib/libwx_base_xml-2.5.so.4 libwx_base_xml-2.5.so.4
$ sudo ln -s /usr/local/lib/libwx_base_net-2.5.so.4 libwx_base_net-2.5.so.4
$ sudo ln -s /usr/local/lib/libwx_base-2.5.so.4 libwx_base-2.5.so.4

then just 

$ waste

Then its a case of generating a public/private key pair and starting a network,
 
have fun!

---

### Post by Pirate_Will on 2005-03-27
Just in case anyone is trying this, there is one other small problem I've had with the waste client. It seems that adding and viewing other peoples public keys won't work automatically. Luckily its really easy to add them manually:

all you need to do is create a text file called Deault.pr3 and paste the keys of those you want to connect to in that.

---

### Post by garcia on 2005-03-28
Did you try
"LD_LIBRARY_PATH=/usr/lib waste"
?
It seems as though linking those /usr/local/lib files to /usr/lib can get smelly.

---

### Post by Pirate_Will on 2005-03-28
Hi Garcia, 

Thanks for pointing this out to me, i hadnt even though of it to be honest. I've just tried it myself, removing the symbolic links and then executing the command you gave. For some reason it didnt work, giving the original errors about not being able to find the libraries. 

Does this work for you? It would be a much easier and more elegant solution if it did, and certainly not the first time i had failed to make something work first time. 

Cheers, 

Will

---

### Post by ups on 2005-03-28
[QUOTE=Pirate_Will]Hi Garcia, 

Thanks for pointing this out to me, i hadnt even though of it to be honest. I've just tried it myself, removing the symbolic links and then executing the command you gave. For some reason it didnt work, giving the original errors about not being able to find the libraries. 

Does this work for you? It would be a much easier and more elegant solution if it did, and certainly not the first time i had failed to make something work first time. 

Cheers, 

Will[/QUOTE]
 If you had compiled the wxAll libs with ./configure --prefix=/usr, they would have installed in /usr/lib instead of /usr/local/lib. It is not recommended to install things in /usr though, but perhaps it is better than creating manual symlinks.

---

### Post by cfa on 2005-03-28
apt-get install libwxgtk2.5-dev 
gunzip waste-beta.zip 
and make / make install should do the trick also :)

---

### Post by bored2k on 2005-03-28
"Share odd files with friends"

Nicotine is doing wonders for me on this one .

---

### Post by Pirate_Will on 2005-03-28
I don't think that waste is for everyone and is certainly more hassle than most other file sharing apps, I use it to create encrypted private networks with my friends. 

One of my favourite features is the ability to send someone files without their approval (this is optional), which might not appeal to some, but if a friend gets a picture or some music he or she thinks i might like, they just send it.

Its not a particularly fast method of transfering files but its pretty light on resources and i dont worry about anyone suing me  ;)

---

### Post by Pahanilmanlintu on 2006-03-17
Thanks for the HowTo, altough i haven't managed to install it yet.

There's nowadays also a linux port available from waste.sourceforge.net with an installer, but i can't get it to run. There's no information about dependencies or installation in general, so if anyone has successfully installed it, please share the know-how. :)

Edit: This is the error i get when i try to run it: > bash: ELF: command not foundIt kinda makes me think the executable is in a different charset or something?

Edit: M'kay, i learned a few commands (i'm a total noob :)) and found out that it won't run because libwx_gtk2u_xrc-2.5.so.3 is not installed. This is a part of an obsolete wxgtk version, so i guess a version of waste using a newer one should be compiled...

---

### Post by hpklett on 2006-10-11
Or you could do it the *right way*, and make it easier to boot.

```
sudo apt-get install libwxgtk2.6-dev
```

Download the latest waste-source-wxwidgets package from waste.sf.net.  Right click -> Extract Here.  Then

```
./configure
make && make install
```

That installs to /usr/local, which is fine, /usr/local is for exactly this kind of stuff, but I like to use a prefix in my home directory:

```
./configure --prefix=/home/me/where/I/want/waste
make && make install
```

---

### Post by rvernica on 2006-11-23
Hi,

I managed to install waste without compiling anything.

I got **waste-linux-1.5-beta-3.zip** from here:
[http://sourceforge.net/project/showfiles.php?group_id=82356&package_id=147272](http://sourceforge.net/project/showfiles.php?group_id=82356&package_id=147272)

I added the following line to **/etc/apt/sources.list**
**deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse**

Then
**sudo apt-get install libwxgtk2.5.3**

and
**./waste**

Ray

---

### Post by marksutherland on 2007-07-25
Hi, I just compiled waste using hpklett's method, and I thought I should mention that you need wxrc from the wx-common package for it to work (I built waste using wxwaste_1.5_beta_4.tar.gz) . As such the apt-get line should probably be

```
sudo apt-get install libwxgtk2.6-dev wx-common
```

in order to make sure you have all the dependencies. This certainly gets waste running, but I've yet to use it properly.

---

### Post by johndoe32102002 on 2008-12-19
The latest version of waste is found here:
[http://wasteagain.sourceforge.net/downloads.shtml](http://wasteagain.sourceforge.net/downloads.shtml)

It is NOT backwards compatible with the last versions.

Wine runs Waste find on Ubuntu for those that do not wish to run it natively on linux.

---

### Post by chambernug on 2009-11-30
> **johndoe32102002 said:**
> It is NOT backwards compatible with the last versions.

Actually, it's QUITE compatible with older versions, and is running fine under WINE on Karmic.  ;)

I ran into problems getting the old beta to install on Karmic, so I finally just went this route.  It was easy and fast, and the new client is a lot better than the old crappy Linux version.

---

### Post by johndoe32102002 on 2009-12-07
I have found bug in sending messages in all versions.  Can you tell me and link me to which version you found to run stably?

---

### Post by king vash on 2009-12-13
I was also unable to find a version of WASTE that worked in Ubuntu 9.10 if some one knows of one that would be most appreciated.

---

### Post by chambernug on 2009-12-15
1.7.4 build 437 works great for me via WINE.  The only issue that I've found is that when chat text gets long, every new line causes the chat window to "re-paint".  That's annoying, but workable.  I have this version working perfectly with my existing network that is running the *old* windows branch.  Note that when setting it up, I used 1536 bit encryption, rather than the new default 2048 bit.

---

