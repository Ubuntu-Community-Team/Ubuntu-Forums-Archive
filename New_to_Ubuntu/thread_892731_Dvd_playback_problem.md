---
title: "Dvd playback problem"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by itsvan on 2008-08-17
Hey guys,,i have a problem that has been storming THE HARDY HERON users,,,,im having problems when i try to play my DVDs data,,for example i try to listen to a song burned on a dvd,,and it will play for a couple of seconds and then it will abruptly stop,,and a message will say "Could not read from resource",,or when i try to copy the file to my desktop it will say "Error reading from file: Input/output error" ive been looking around and it seems to be prominent with us Hardy Heron users,,and even though it doesnt happen with all of my dvds,,or some files,,ive noticed its happening alot lately,,can someone try to help me with this bug?? :confused:

---

### Post by wolfen69 on 2008-08-17
do you have libdvdread installed?

---

### Post by nicedude on 2008-08-17
I don't fully understand your problem so I am sure others wont either. Please give me some more info.

1. Can you play store bought DVD videos, If not then you need to enable the Medibuntu repositories for your Ubuntu and then install libdvdcss at a minimum and I would suggest VLC as the player to use to watch them.

2. Did you burn the DVD's you are having problems with in Ubuntu ? If so with what utility as I have found some of them to be spotty at best and with my drive at least have burned some "coasters"

3. When you say song burned to a DVD I am assuming you mean you burned it as data and are trying to play or copy that data file and getting errors? If so then the disk burn either failed originally or is scratched etc. you could also get a different outcome with a different DVD drive if you stuck it in that and that might mean it is a problem related to your DVD drive.

Please give me some more details about the origin of the disk in question and I can advise further on what to try.

---

### Post by Sinkingships7 on 2008-08-17
Run this and see if it helps:```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by itsvan on 2008-08-17
Ya my problem is with Burned DVD's,,,as i try to play the file of that burned DVD,(yes burned as a Data),ubuntu keeps on bringing errors that i cant open them,,
and im not sure if i have libdvdread installed, how can i find out? and if not how do i install it??

I burn my data discs with "K3B",,and i thought that maybe the burn whould be falty,or the disc scratched,,but it works on other computers just fine,the dvd is new ,the problem seems to be with UBUNTU trying to read it.

---

### Post by nicedude on 2008-08-17
Thats strange if they will read in another PC but not the one that burned them. But my laptops CD/DVD burner doesn't like k3b or brassero etc either. It just burned worthless coasters half the time. My only solution for my particular device was to install NERO for linux, it has not messed up a disk using that and everything I burn works the way it should. Now that said my CD/DVD will read disks I burned with another PC with a LITEON DVD drive and k3b so I just took it that my laptops combo drive doesn't play to well with linux. Oh well thank god for NERO LINUX as it makes my laptop drive behave quite nicely.


To install libdvdnav etc you can use synaptic package manager which is the most powerfull GUI based software installation program in your Ubuntu. Open it by going to the top menubar then System -> Administration -> Synaptic Package Manager

Once there you can search by name or name & description to see what is available then anything you find that you want to try out, you just click on it and select INSTALL. Once your done choosing stuff to install you click the green checkmark icon to apply your choices. I don't remember if you mentioned it but if you havn't added the medibuntu sources to your sources you should do that as well so you can get CODECS ( they are what allows a player to play video ) & some other cool stuff that Ubuntu can't for legal reasons include in the repositories ( like google earth & libdvdcss which decodes store bought DVD's so you can watch them :-) )

hope this helps you figure it all out.

---

### Post by kansasnoob on 2008-08-17
Well if it were only a sound issue I'd suggest this:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

But since you're having trouble with even data DVD's I'd suspect a bad or dirty drive.

---

### Post by itsvan on 2008-08-17
what does error wrong architecture mean?

---

### Post by nicedude on 2008-08-17
If you are using 64bit Ubuntu then yes you would need 64bit NERO. I have a 64bit AMD laptop and I still use 32bit Ubuntu because there is more support in general for the 32bit version, as in some software there may only be 32bit versions. But then again I install allot of software from source so I am kinda different from most casual users. One thing to keep in mind though is that you can't even tell a difference in the speed between the two unless you are performing some not so common tasks, like high level mathmatic calculations I believe so to me the 32bit is the better version. One day when/if everyone & everything is written for 64bit then I will switch but until then I am quite happy with 32bit on my 64bit machine :-)

---

### Post by jakejas on 2008-08-30
> **Sinkingships7 said:**
> Run this and see if it helps:```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
I had the message pop up while trying to play store bought DVDs, I had tried 3 different DVD readers, tried different slave, master, cable select options, had all of the codecs installed, and after I ran the code above (sudo /usr/share/doc/libdvdread3/install-css.sh), it started working. Thanks!

---

### Post by billgoldberg on 2008-08-30
Are you sure the disk (the cd-rom/dvd drive) is still working good?

It sounds like an hardware issue to me.

---

