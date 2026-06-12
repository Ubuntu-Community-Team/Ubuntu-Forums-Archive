---
title: "[SOLVED] Is resizing necessary w/ 8.04 now?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by t-molli on 2008-05-14
I just installed a clean copy of 8.04. Went pretty smoothly and all seems good. I went to install flash and got an error that there wasn't enough room to install it. I thought "what!?"

Sure enough, my / partition is full. So, I deleted some .deb files to make room and installed flash...

So, now I'm thinking I need to resize the / and /home partitions to give some extra room to the / partition. However, I don't have the option to do that because it's greyed out. 

I don't remember it being a problem to resize the OS partitions from within the OS when using 7.10, but I could be wrong since I haven't done that in a long time.

Q1: Does the 8.04 / partition require that much more space than 7.10? If so, what's the going size we're telling everyone to use now for /?

Q2: Can I resize while running the OS or do I have to run gparted (partition editor) while using the Live CD? If not, why were my partitions greyed out and unavailable for resizing? 

Thanks...

---

### Post by Thingymebob on 2008-05-14
you can't make changes to a mounted partition, so you will have to boot the livecd and do it from there.

---

### Post by Oldsoldier2003 on 2008-05-14
8.10 is a little fatter than 7.04 but honestly the difference isnt that huge. Most of the time when you are running out of space on an older install it just means its time to sudo apt-get clean and to empty out /var/log

---

### Post by t-molli on 2008-05-14
Oh... I forgot to mention. I formatted the / partition and gave it 10 gigs. It's saying it's full now and I just installed 8.04 and a few programs.

Is 8.04 that big? I can't imagine it is. Any ideas then..

---

### Post by Thingymebob on 2008-05-14
my / contains 12.5g but I do have quite a bit installed
/home is huge but is full of music, photos etc

---

### Post by maybeway36 on 2008-05-14
If you have a Knoppix CD, boot from it, mount the hard drive and run the "fsview" program on it:
```
fsview /media/xxx
```
Alternatively, use a Kubuntu live CD, install the konq-plugins package, then do the above.FSView is a KDE program that graphically represents the sizes of files on your hard drive.

---

### Post by logos34 on 2008-05-14
> **t-molli said:**
> Oh... I forgot to mention. I formatted the / partition and gave it 10 gigs. It's saying it's full now and I just installed 8.04 and a few programs.

Is 8.04 that big? I can't imagine it is. Any ideas then..

that can't be right, not 10 gb worth of stuff

---

### Post by Thingymebob on 2008-05-14
> If you have a Knoppix CD, boot from it, mount the hard drive and run the "fsview" program on it:
Code:

fsview /media/xxx

Alternatively, use a Kubuntu live CD, install the konq-plugins package, then do the above.FSView is a KDE program that graphically represents the sizes of files on your hard drive.
or just accessories->disk usage analyzer in Gnome

---

### Post by Thingymebob on 2008-05-14
> that can't be right, not 10 gb worth of stuff
Yep mine is, & it wasn't much different before upgrade

---

### Post by t-molli on 2008-05-14
> **logos34 said:**
> that can't be right, not 10 gb worth of stuff

exactly.... that can't be right, but when I do a 'df' it says my sda2 is at 100%. I'm looking at my laptop for comparison and it's only at 4.8 gigs right now, but I didn't load those programs on it. However, these programs I'm talking about are small like ntp, alltray, devede, firestarter, k3b, k9copy, and build-essential. Something is/has gone wrong I think...

---

### Post by nowshining on 2008-05-14
hmmm do you have others in ur home using ur computer? or just others in ur home? esp. kids, etc..

+

try enabling the showing of hidden files ctrl +. in kde and ctrl+h in gnome. From there find any files using a huge amount of space such as txt files, etc..

+

by default ur drive isn't full exactly - as ubuntu, etc.. keeps a bit reserved so u can log in, just incase something bad goes wrong. :) there is a way to disable that and to regain that space.

+

post the output of 

df -h

in the CLI.

---

### Post by Thingymebob on 2008-05-14
Ok, you guys have got me looking harder at mine now, attached are my disk analysis maps, I can't see anything surprising here, I've expanded the /usr/share as this is what's using 50%ish of my / partition

---

### Post by ajgreeny on 2008-05-14
Just out of interest, my root (/) partition of a new install of Hardy is 2.6GB.  Home is separate and about 29GB, so you must have a home folder that takes up a lot of space.  OK, I haven't added any packages so far to a vanilla ubuntu, but that should give you some idea of the size of a full, unamended installation.

---

### Post by t-molli on 2008-05-14
> **ajgreeny said:**
> Just out of interest, my root (/) partition of a new install of Hardy is 2.6GB.  Home is separate and about 29GB, so you must have a home folder that takes up a lot of space.  OK, I haven't added any packages so far to a vanilla ubuntu, but that should give you some idea of the size of a full, unamended installation.

thanks for that. it's what I needed to see something had gone wrong. I couldn't find it though, so I just reinstalled everything and started over. I'm done now and this time it's right with a / partition that's around 3 gigs. Much better.

Thanks for everyone's input.

---

### Post by louieb on 2008-05-14
Hardy is using something new called **gvfs**. Seen some post that indicated there is a bug that sometimes will  cause space usage to be incorrectly reported. 

```
df -h
```

Don't know much more than that.

---

