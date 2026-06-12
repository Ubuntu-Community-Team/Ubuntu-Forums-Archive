---
title: "Installed 15 minutes ago, wireless card not working"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by usmcfirebat on 2008-09-29
its running on my 5 year old laptop, with the wireless card Linksys WPC54GS.  i searched google and came up with a couple threads, only problem is that i dont understand what half of them are saying.

sry to be such a noob, but my experience in linux is like, 20 minutes.

any idea how i would go about getting wireless internet to work?

i can plug the ethernet in and im sure it would work, but i am gonna be taking this laptop with me tommorow and would like to have the wireless work.

also, in the near future im going to be wanting to install or activate compiz fusion.  

im running the latest ubuntu, if that helps.

---

### Post by Peter09 on 2008-09-29
In a terminal type
```
ifconfig
```
and post the output here

---

### Post by anewguy on 2008-09-29
First, to address the wireless issue.  Please read through the instructions on the following link, then post back with questions you might have.  You can ignore the part about actually installing with Synaptic.  Instead, just put in the livecd you installed from.  A explorer-like window should open.  Navigate to pool/main/n and then ndiswrapper.  There should be 2 installation files there.  Double click the first one and let it install, then double click the second and let it install.

[http://kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php]("http://kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php")

The rest of the initial post there walks you through the installation.  There is an additional step not listed there you must do AFTER you complete all of the steps there:

in a terminal window:

cd /etc <enter>

sudo gedit modules <enter> and type your password when prompted

go to the bottom of the file.  If it is not a blank line, go to the end of the line and press <enter>.

Type in the following:

ndiswrapper

Now, save the file, exit the editor and REBOOT.


Second, regarding the desire for compiz:  it is highly unlikely that a 5 year old laptop has a video processor that can run compiz.  Do a "lspci" in a terminal window and copy/paste the output from that back here as well.

Please post back if you have any questions before beginning, during the process, or after.

Dave :)

---

### Post by usmcfirebat on 2008-09-29
> **anewguy said:**
> First, to address the wireless issue.  Please read through the instructions on the following link, then post back with questions you might have.  You can ignore the part about actually installing with Synaptic.  Instead, just put in the livecd you installed from.  A explorer-like window should open.  Navigate to pool/main/n and then ndiswrapper.  There should be 2 installation files there.  Double click the first one and let it install, then double click the second and let it install.

[http://kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php]("http://kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php")

The rest of the initial post there walks you through the installation.  There is an additional step not listed there you must do AFTER you complete all of the steps there:

in a terminal window:

cd /etc <enter>

sudo gedit modules <enter> and type your password when prompted

go to the bottom of the file.  If it is not a blank line, go to the end of the line and press <enter>.

Type in the following:

ndiswrapper

Now, save the file, exit the editor and REBOOT.


Second, regarding the desire for compiz:  it is highly unlikely that a 5 year old laptop has a video processor that can run compiz.  Do a "lspci" in a terminal window and copy/paste the output from that back here as well.

Please post back if you have any questions before beginning, during the process, or after.

Dave :)

thanks for the in depth response, but it seems like my unfamiliarness with linux is making it hard for me to fully understand and do what it is you are suggesting.

i got through installing those two files from the cd, and then the next thing i did was skip to step 3 in that guide/page and when i type in exactly what it said, it returns to me: "couldnt open /cdrom/etc, etc, no such file etc.


edit: also to the previous poster,
when i type ipconfig in the terminal, it just says "bash: ipconfig: command not found"

---

### Post by kpkeerthi on 2008-09-29
It is **ifconfig** as the post says and not **ipconfig**

---

### Post by usmcfirebat on 2008-09-29
oh woops, well.

when i type in ifconfig it gives me:

me-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:19:b9:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59084 (57.6 KB)  TX bytes:59084 (57.6 KB)


really haven't the faintest idea what to make of that.

---

### Post by Peter09 on 2008-09-29
Just a couple of things,
Your card has not been recognised, the driver is is not installed.

Before you go much further,
what version of Ubuntu are you running and have you attempted to connect through a hard wired link.

It is worth getting connected as soon as you can because you will get a large number of updates come down and this may solve your problem. 

Also the error concerning the CD not found is due to the fact that you have not installed with an internet connection.

I would suggest that you get a wired connect and also go to

Administration->synaptic->Setup->Settings->Repositories

and untick the CDROM and tick the other boxes, except those for source code.(Assumes that you can get an internet connection)

Look for other posts in the forum to check the correct repositories.

---

### Post by theRightNee on 2008-09-29
also, as you are new to ubuntu, you may like to install ndsigtk (the graphical version of ndiswrapper) to faciliate in the installation of the wireless drivers
to install:
1. make sure that the CD-rom is listed as a repository
2. type sudo apt-get update (just to make sure)
3. then type sudo apt-get install ndisgtk
4. select the desired .inf file and you should be ready to go

---

### Post by anewguy on 2008-09-29
The instructions assumed you had the original CD that came with the device and has the windows drivers on it.  If not, go to linksys and find the appropriate Windows XP (not Vista) drivers for your device and download them.  If they are "packed" (an exe) then post back and I'll work around that for you.  If they are zipped, just double-click on the download to start the unzipping.

Once you have done that, post back again.  I want to do this one step at a time since you are new to Linux.

Also, as mentioned by theRightKnee, ndisgtk is a gui'd front end to ndiswrapper and can be easier for new users to use, so I would install it as he suggested.

Once you have done those things, and decided if you want to use ndiswrapper via the command line or via the gui'd app ndisgtk, post back and we'll help you from there.

Dave :)

---

### Post by usmcfirebat on 2008-09-30
hey there guys,

so i followed as much of the advice as i could in here.

ive completed what the last two posts have asked.
the driver that i downloaded from the linksys for my card (WPC54GS v2) came in a zip format, which kind of confused me even when i tried to install it on XP.  i dont remember what exactly i did on XP to get it to work.

heres what the main folder in the zip file for the driver looks like: 
ive looked around, i dont see any inf files that I could use with the GUI installer that i installed

[IMG]http://img34.picoodle.com/img/img34/3/9/30/f_Screenshotwm_1de94bf.png[/IMG]

inside the 'driver' folder there are two folders: NT and 9x.  
that doesnt give me a good feeling.

---

### Post by anewguy on 2008-09-30
Look in the 9x folder in the drivers folder.  I would try those first - if it doesn't work you can always use ndiswrapper to remove it and then try the NT drivers.

If you have any questions at all, please post back.  I may not be the quickest here at getting an answer back to you as last week, this week and next week I am extremely busy, but I do try to look once or twice a day.

Dave :)

---

### Post by usmcfirebat on 2008-10-03
thanks for taking an interest in my case, but i think this one might prove to be too dificult to overcome without being in front of my computer.

a friend of my roomates (who knows what hes doing) tried to get it to work, but in the end couldnt get it to work.

he did the whole ndiswrapper deal, and even went so far to blacklist a few drivers that were loading up before the supposed correct one.

in the end he said the correct driver was loading, but for some reason when he tried to check the cards status, there was no IRQ information given.  This is where we left it and gave up.  

the final conclusion he came to was the driver was not right.  I have a card that says version 2 on the bottom, and I downloaded the version 2 driver from linksys.com, thats the driver i am using and should work.  But i remember having troubles getting this card to work even with XP (which i consider myself very proficient at using) and think in the end i had resigned to using the windows auto set up thing instead of the driver cd that it came with or the one on the internet.  I dont know, maybe ill just get a newer card.

thanks for your help though.

not sure what else i could try

---

### Post by handydan918 on 2008-10-03
You said:
"inside the 'driver' folder there are two folders: NT and 9x.
that doesnt give me a good feeling."

I can't understand why not. That is all you are going to see on any installation cd; windows files.

You might try posting the output of ```
lspci
```
just to see what  card/chip you are dealing with.

---

