---
title: "Ubuntu and windows"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by Ton Baars on 2011-11-29
Just installed ubuntu after earlier aborted attempts.Used the option to install it alongside window 7. Now I am working on the computer using Ubuntu. And I have no idea how I can go to the window section....And how to share folders. 
any help is appreciated
ton

---

### Post by Bennetto on 2011-11-29
Are you looking on how to boot into windows or just view the partition?

---

### Post by spiky001 on 2011-11-29
You should be able to access them from Nautilus in the side pane they will be labeled as a file system mine is labled 10gig file system.  Try double clicking 1

---

### Post by JRV on 2011-11-29
You need to reboot to change between Windows and Ubuntu.  After a restart you should see a boot menu.

You can mount your Windows partition in Ubuntu, but Windows can not see your Ubuntu installation.

Is this a WUBI install?

---

### Post by Megaptera on 2011-11-29
Which version of Ubuntu? In 10.04 just click on 'Places' in the menu and your Windows partition will show a a series of numbers or size of the partition.

Not sure about 11.04 / 11.10 but I think you need to click on the 'Files' icon?
Another option here [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by Ton Baars on 2011-11-29
Thanks for your suggestions. I am new to all of this, not good with jargon so it will take some time. Where I am it's late so i will close down. It is Ubuntu 11.10 and i used the Wubi. Now it opened in ubuntu and I can go to guest user and back to myself but I have no idea wher my Windows plus all applications are.
If I look at the partitioned hard drives ( I am sure I didn't do all as it should) I can find some documents. 
Before I installed Ubuntu, I had Windows on the C drive. I partitioned the D Drive in 2 even parts, each around 250 gigabytes. Now i find that my drives are divided like this:
a 640 GB hard drive into a 262 filesystem where  only 155 MB is used,
 and a 271 filesytem where 35 GB is used
and there is another partition , 105 MB capacity called System reserved, only 23 MB used.

I am wondering if the files are there but can not be seen by Ubuntu.

When i wanted to close Ubuntu and computer, it wouldn't do so at first it stayed open for 10 minutes. i forgot how it eventually closed. Restarted and again only In Ubuntu. 
What can i try, and I am not very computer savy.

hopefully tomorrow

---

### Post by Mark Phelps on 2011-11-29
In Wubi installs, the Windows filesystem is automatically mounted under /host in the Linux filesystem.  Look there for your Windows files.

---

### Post by Ton Baars on 2011-11-29
Please help me to get out of Ubuntu. It is really something I like to use, but I also realise that whenever I look at something new on a computer, I can not find the most simple things. I need to do this with a person next to me.
Now I can not log out, I shut it of last night only to find it open, and  again just the ubuntu page with the User selection: me and guest.
I can not even find the /host files that is mentioned, it took me for ages to find my own question as I have no idea that User CP means User C.... P.....
I am sure everything is easy and done with that in mind, it is just that for me it doesn't work. I also try to find information on other threads and forum, but it is not easy, even the search buttons seem slow and end up with slightly related threads. Maybe nobody ever had my problem....

So please, tell me how to uninstall Ubuntu, in a way that my Window stuff and files is still there, and I promise to give it another try later. Tomorrow I should get back to my students, and a lot of work is now hidden somewhere.
thanks ton

---

### Post by Ton Baars on 2011-11-29
Mmm, reading a thread about dealing with first time users,
[http://ubuntuforums.org/showthread.php?t=698105&highlight=linux+file+system](http://ubuntuforums.org/showthread.php?t=698105&highlight=linux+file+system)
I did some searching and now I have found the /host thing and a lot of things related Window. Still need to know how to log out and change the operating system, :) well a little smile on my face, and a cup of coffee next to me

---

### Post by Megaptera on 2011-11-30
Try re-boot ( or re-start) instead of log out ... and when it re-boots you should get a simple menu giving you a choice of Ubuntu or Windows.

---

### Post by mastablasta on 2011-11-30
you don't just log out you need to reboot computer. when you reboot you should get an option to boot either to ubuntu or to windows. and then you choose windows. when you get to windows you can uninstall ubuntu just like any other programme.
 
what you did (if you installeld it via Wubi) is you installed it as a programme. this is ment for new users so they can try it out. it is not ment as permanent install. it all runs inside a virtual file, so if that file would get corrupted (or part of it) oyu could loose everythign done in thiy type of Ubuntu installation.
read this thread for more explanation regarding your type of install and some solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
 
The most easy and yet at same time extreeme is to restore the bootsector of hard disk. this will overwrite it with windows default boot. so you will loose Wubi install but gain windows onyl boot.

---

### Post by Ton Baars on 2011-11-30
Thanks again for all of you who have responded. I left home some time ago and during that time the computer battery run empty, so when I restarted the computer, to my surprise and joy and whatever, it opened like before with Window. For the first time in my life, I was actually happy to see window......
Reading about the fact that my Ubuntu was a program meant as a try out, now I don't know what i still have and if I can switch between the two, and if that is advisable for me. I might leave it for now until I have a Ubuntu user sitting next to me. I like what I did see in my day in ubuntu land, although there is lots to learn, and hope to come back some day.
Thanks again for your input, I have learned a few things.
ton

---

### Post by Megaptera on 2011-11-30
You're welcome!

---

### Post by mastablasta on 2011-11-30
> **Ton Baars said:**
> Thanks again for all of you who have responded. I left home some time ago and during that time the computer battery run empty, so when I restarted the computer, to my surprise and joy and whatever, it opened like before with Window. For the first time in my life, I was actually happy to see window......
Reading about the fact that my Ubuntu was a program meant as a try out, now I don't know what i still have and if I can switch between the two, and if that is advisable for me. I might leave it for now until I have a Ubuntu user sitting next to me. I like what I did see in my day in ubuntu land, although there is lots to learn, and hope to come back some day.
Thanks again for your input, I have learned a few things.
ton
 
 
i guess empty battery works too. but otherwise shutdown and then turn computer on again aor reboot would bring up the boot menu that is shown before OS are loaded. it's done similary if you had installed linux next to windows on a separate partition (part) of the disk. Only that way is a bit more complicated (not too much) but both systems then run side by side independent of eachother (appart from bootloader where the one from linux is used to choose the system on computer startup).
 
anyway if oyu want to do side by side: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
you can ask here for tips & tricks & traps :D
 
or if you get an Ubuntu user to help you while sitting next to you is even better.

---

