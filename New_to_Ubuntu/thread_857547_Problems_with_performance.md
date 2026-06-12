---
title: "Problems with performance"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by zamadatix on 2008-07-12
i just installed ubuntu on my second hard drive in the primary partition (20gb) when i first booted it up i would type the login information and it would start the login play the sound and go back to the login screen so i googled and found if you go into failsafe mode you can log in. im running on a 2ghz 512 mb am and it is slow as vista! when it starts i open firefox and can do things then teh file browser opens and the firefox window turns gray and it starts to go really slow/

i think this may be because of failsafe mode if not i dont know but if it is how do i ix it so i can login?

---

### Post by finer recliner on 2008-07-12
something is using a lot of your resources.

when your computer starts acting really slow (applications turn gray and such) do the following:

1. switch to tty1 (command line mode) by hitting ctrl+alt+F1
2. log in
3. type the command```
 top  
``` top will display all the applications running in order of who is using the most resources (at the top). take note of which application(s) are taking up too much resources. for example if you notice firefox is taking 90% of your CPU you should probably kill it.
4. to kill an application, type the letter 'k' (while still in top). and enter the PID (number in the first column) of the application you want to kill and hit enter. you can exit top by hitting the letter 'q' (for quit)
5. return your normal desktop by hitting ctrl+alt+F7

hopefully this will help you get a better idea of why your computer is acting slow.

---

### Post by zamadatix on 2008-07-12
thanks i was wondering what the ctrl alt del was in ubuntu. i found out that its not just any applications that fail but it is firefox. i loaded in non failsafe gnome btw.  every time i open firefox i can load a few pages or do a few things then it either causes my system to gray out and freeze. maybe if i opened it in safe mode but i dont know how to do that.

also random question but where is the equivalent of program files?

---

### Post by ctarwater on 2008-07-12
If by 'user files' you mean the equivalent of .exe files I've found mine in /home/usr/bin.

I'm still new here though so there may be another/better answer.

---

### Post by finer recliner on 2008-07-12
> **zamadatix said:**
> where is the equivalent of program files?

[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

---

### Post by MarcG on 2008-07-31
I'm getting the same performance problems, but top doesn't show any resource pigs. Firefox is at around 8%. Running Performance Monitor shows the disk at around 90% use and the processor down around 20%.

The most recent problem was with update-manager. There were a few updates, maybe 7 or 8, but this took nearly a 1/2 hour to complete. During this time the laptop is useless. Any open windows gray out and mouse movements get very jerky. It may take a minute to activate any window. One thing I see is the hard drive is continuously active.

But it's not just Update-Manager. Sometimes just opening Nautilus can take 30 - 40 seconds.

I've got a Compaq Presario V2000 running Hardy. An AMD Sempron 3000 at 1800MHz. 384Mb RAM and a 40G drive. This was a clean install of Hardy.

So what do I look for? I tried changing swappiness, but saw no differences.

---

### Post by cariboo on 2008-07-31
Your best bet would be to upgrade your ram to at least 512MB, if that isn't possible, try a lighter weight Desktop manager, like Xubuntu. I use Linux Mint Light, which is based on Ubuntu, on my HP laptop and it runs circles around Ubuntu on the same equipment.

Jim

---

### Post by MarcG on 2008-08-01
Would I need to do a full install of Xubuntu, or is just installing xfce enough? Adding memory isn't all that expensive, but xfce is free and I can try it tonight.

---

### Post by davidpeace on 2008-08-01
I get extremely slow performance at times. When using  Seamonkey, I usually have two or three tabs open, one of theme to streaming music. But just before a reboot a couple of minutes ago I was watching Firestarter activity and it was below 10 kb/s! I tried using the top function  mentioned above and there were no serious resource hogs either. I have the utility unhide and used it and it shows several "hidden PID"s but they are displayed as just numbers. How do I find out what those processes, or whatever they are, are doing and whether they are critical or not before I kill them? There were no man pages for them. Also I have nearly 2 Gb of ram and it is only being used up to about 20%, info from sysinfo. The only other thing is that I am on a public server (New York Public Library).:confused:

---

### Post by MarcG on 2008-08-01
Switching to xubuntu seems to have done the trick. It's pretty easy to install, basically install xubuntu-desktop. The log out and pick a new session from the login screen.

Thanks!

---

