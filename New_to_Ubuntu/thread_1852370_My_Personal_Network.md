---
title: "My Personal Network"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by ki3gz on 2011-09-30
so as a beginner to the world of ubuntu, i want to apologize for any noob comments you may want to make.. i really would like to get this figured out.

I have multiple machines, my desktop which i have been replacing components in for years now has had Windows XP on it until i recently (deep breath) installed ubuntu 10.10 on it.. from a flashdrive.
which brings us to my new laptop, which im on now, that has the same ubuntu 10.10 on it.. running pretty smoothly.. i even moved all my data from my desktop to this guy, setting up for the big goal..
this goal being creating a "server" out of my desktop that i can access from my laptop from anywhere on the local network, with my removable drive hooked up..
i have heard of putty, but as ive been playing with linux for awhile now im beginning to think that i may have to do some preliminary stuff, which im sure i wont understand if i try to figure out myself.. 

so in order to save myself the frustration and eventual hopeless defeat, im asking for help.. any details about anything i have mentioned would be great.. please remember i am a newbie

thanks

---

### Post by LowSky on 2011-09-30
Look into SAMBA
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Lets you look share files and folders over the network with both Linux and Windows 9in case you need that too).

---

### Post by Drenriza on 2011-09-30
So i understand you want a server. But what do you want the server to do? That is not 100% clear.
Do you want it to be a share? Do you want to stream music / video from it to devices? Also should you be able to reach the server from the Wide area network (the web)?

---

### Post by ki3gz on 2011-09-30
first of all i would like to thank you guys for helping me by responding.
what i would like for my machine to do is to host certain files and for me to be able to access them from within the network, and eventually across the web.
a music stream would be good, as music is part of what i want to accomplish.. i would also like to start playing with programming and it would be awesome to be able to access apps i made on devices. that last part coincides with where i want to end up, but i thought i would toss it in to help explain.

---

### Post by Drenriza on 2011-10-03
> **ki3gz said:**
> first of all i would like to thank you guys for helping me by responding.
what i would like for my machine to do is to host certain files and for me to be able to access them from within the network, and eventually across the web.
a music stream would be good, as music is part of what i want to accomplish.. i would also like to start playing with programming and it would be awesome to be able to access apps i made on devices. that last part coincides with where i want to end up, but i thought i would toss it in to help explain.

To host files, Samba is a good choice as suggested in #2. To access your server from the web, make port forwarding from your router to your server. If you have a decent router their is nothing to it and can be accomplished in minuts.

As for music streaming......looking try look at this [http://www.gnu.org/s/gnump3d/](http://www.gnu.org/s/gnump3d/) i have no personal experience with it.

---

