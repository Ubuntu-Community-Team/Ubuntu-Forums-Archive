---
title: "Absolute Newbie Attempting a relatively simple project"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by Curteis_slade on 2014-05-31
Hi,

This is my first post so please be patient with me. I am 14 yrs old and have been looking and experimenting with unbunto on my windows PC. I have installed it to run with windows 7 and made a boot up disk. I am attempting to create a flash drive just like the one at ninjastik.com. One where it connects via firefox automatically to tor using visalia. I can't afford the stik itself and figured it would make a good place to start. I can create a start flash drive but nothing else. Ive jet spent this week tinkering with it and finally thought I was ready to do it. After attempting to start the project I appear to have deleted a drive partition which (stupidly) I deleted. I am now re installing windows. Youtube videos are all well and good but nothing beats either someone showing you how to do it or a list of what to do. I then can work backwards and see each step and what it does. I hope this makes sense. Thanks for your time. Curteis

---

### Post by cariboo on 2014-06-01
I haven't tried building one of this all in one privacy usb drives, because in today's world, there is no such thing as internet privacy. I'd suggest that if you system has the resources, set up the system in a vm, using virtual box, available in the repositories, before trying to set it up on a usb stick. The DIY instruction on the [ninjastik.com]("http://www.ninjastik.com/get-it-free/") page seem pretty sparse, but using a vm, you can create a snapshot after you've installed Lubuntu, then make changes, if you fail, you can always go back to the snapshot and restart.

---

### Post by Vladlenin5000 on 2014-06-01
I haven't read the instructions mentioned but considering its purpose I think there's an already made distro - TAILS - that can be installed in a USB flash (or run from a CD) just like any other distro. It's intended to access Tor directly and to not leave any trace in the host PC. If this is what you're looking for perhaps you should give Tails a try.

---

### Post by sudodus on 2014-06-01
Welcome to the Ubuntu Forums *Curteis*         :-)

> **cariboo907 said:**
> ... in today's world, there is no such thing as internet privacy.

+1 

So avoid doing things that you wouldn't do when people are watching.

> **Vladlenin5000 said:**
> I haven't read the instructions mentioned but considering its purpose I think there's an already made distro - TAILS - that can be installed in a USB flash (or run from a CD) just like any other distro. It's intended to access Tor directly and to not leave any trace in the host PC. If this is what you're looking for perhaps you should give Tails a try.

You can try Tails, but its purpose is more to help dissidents in countries without democracy. And it should be run from internet cafés and similar places, only once from each place to avoid being tracked and hunted down.

If you want to exchange secret information with friends (or for business people with colleagues and customers), you can use encrypted mail, or mail with encrypted attached files. Pretty Good Privacy with the ***gpg*** program is a good alternative. There is a plugin, ***Enigmail***, in Thunderbird which makes it more convenient. The most difficult part is often to make the gal/guy at the other end to install and use the corresponding software.

The national security agencies can track with whom you exchange information, but there can be a pretty good privacy for love letters and other secret things that are legal.

---

### Post by stalkingwolf on 2014-06-01
i am unclear as to what you want to do.  Are you wanting a dual boot stick? if not what OS are you planning on using?
This is what I did. I installed my os of choice (mint 13 maya currently). I did it on my bench computer where i could unplug the primary drive and just leave the usb stick.
after install was complete i did all the usual stuff , updates, installed the packages and drivers i wanted and downloaded tor browser bundle.  its on a 16gb stick and is only using about 8.  i just plug it in let it boot then click start tor

---

### Post by Curteis_slade on 2014-06-01
Thanks everyone for the help and advise. Ive borrowed a friends mac for the weekend and tried to run unbent on that but i keep getting no mountable file systems every time so I am 1 step further and 10 steps back. I did finally reinstall windows after I deleted the partitions but now when I reboot I get the choice of 2 operating systems (Windows 7) one of which works and 2 Unbuntu's of which none work. All I was aiming to do was have a nice usb plugin interface that automatically connected to tor on startup. None of which has happened and I am no closer. It was all down to seeing the ninjastik usb device. I thought it would be cool to share it with my friends and learn something along the way. Guess I will continue using another project. When I have something I can use I will take everyones advice.Thanks Curteis

---

### Post by sudodus on 2014-06-02
If you want Ubuntu, you'd better reinstall that too and you should get a good dual boot system again. It is usually easier to reinstall than to repair a broken system. But the best thing is to have a complete ***backup***. Take a backup of the whole drive (as a compressed image by Clonezilla) or backup all your important files (personal files and setting files) with a 'backup program'. There are many such programs in linux.

With a good backup, it is easy to restore your system after a crash.

---

