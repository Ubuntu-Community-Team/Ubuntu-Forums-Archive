---
title: "Ubuntu 12.04 LTS Freezing on Acer Aspire One 722-BZ454"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by NobleYorkshire on 2013-01-30
I am posting in the beginners section because I have a lot of noob questions to ask along with my problem.

I am running Ubuntu 12.04 LTS on my Acer Aspire One 722-BZ454.  I have nothing special installed, just Ubuntu with the updates.

The problem occurs either on start up, or a few minutes after start up.  It freezes to the point where I cannot move the mouse or do anything, so I have to restart it.  Opening software center will also make it freeze.

Spec wise, this laptop should be able to run Ubuntu:

AMD C-50 Processor

4 Gigs of RAM (I upgraded) (1 stick)

32 Bit Operating System

320 Gig harddrive (80 gig partitioned for Ubuntu).  The other partitions are Windows 7 (works perfectly) and Mint (which, oddly enough, works perfectly).

Video card is nothing special, but it is rated as average by Windows 7 and is able to run the 32 bit edition perfectly. 

I made a partition and installed Ubuntu on that way (has Ubuntu GRUB).  I did not use WUBI.


My questions are:

How can I stop the freezing?

I noticed some people post error messages and error logs.  How do you find out where the error log is and how to get them if the computer freezes and you have to restart?

Is it a hardware issue that is causing Ubuntu to freeze? (would be hard to believe since Windows 7 and Mint work).


also...

If I am asking this in the wrong area, where is the best place to ask his question?

Thanks!

---

### Post by mapes12 on 2013-01-30
Does the machine work OK up until the point where you launch FF?

---

### Post by frank604 on 2013-01-30
Let's monitor the processes. Install htop.
```
sudo apt-get install htop
```

Start htop.  alt+f2, type "htop".  Or write "htop" in terminal.

Press f6 (sort by).  Select cpu%

When it starts to get sluggish, monitor the cpu%.  Look at top of the list.  Write down the text under "command".  Read the cpu %.  

What made my netbook get sluggish was apport.  A system report tool to send info to Ubuntu.  As much as I would like to contribute, it was locking up my system everytime it was running in the background.

In case it is the same for you:
```
sudo gedit /etc/default/apport
```
change the value 1 to 0

You can notice the change after rebooting or by typing in
```
sudo service apport stop
```

Information at [http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport]("http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport")

edit: Just realized your not using a netbook like me.  This observation is probably not what you are experiencing then.

---

### Post by NobleYorkshire on 2013-01-30
Thank you for your replies.

The computer never stayed operational enough to run FF (firefox right)?

Thank you for Htop--I am finding it extremely helpful.

I am sorry for not realizing this sooner but I realized when I connect wirelessly, that is when the computer locks up.

I have been connected by wired ethernet all this time. 

What I am doing now is running updates on it (seeing if that perhaps will fix the wireless driver issue?) and then I am going to install Htop and run it on it and post the results.

Thank you!!!

---

### Post by NobleYorkshire on 2013-01-30
This is no doubt the problem.  The second I connect to the wireless network it freezes.

When it's connected by a wire, it works fine.

How can I go about fixing this?

(Also if I disable the wireless interface, it works fine).

---

### Post by NobleYorkshire on 2013-02-01
I've tried updating it more and searching around but I can't seem to find the problem.

Do I have the incorrect drivers installed for the wireless?  How do I find the correct ones?

---

### Post by Outlooker on 2013-02-05
Try this:

[http://askubuntu.com/questions/82724/aspire-one-freezing-due-to-network](http://askubuntu.com/questions/82724/aspire-one-freezing-due-to-network)

---

### Post by NobleYorkshire on 2013-02-05
> **Outlooker said:**
> Try this:

[http://askubuntu.com/questions/82724/aspire-one-freezing-due-to-network](http://askubuntu.com/questions/82724/aspire-one-freezing-due-to-network)

WOW!  Thank you!  I had given up!  But this fixed it!!! Thank you very much!

---

