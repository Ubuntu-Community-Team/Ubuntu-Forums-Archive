---
title: "Too Hardy for a newbie like me"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by dowkeith on 2008-04-26
I just upgraded fron Gutsy to Hardy and either lost my Gnome GUI or it is running undetected. When I boot up, I don't get the GUI sign on. Instead I get a command line login prompt (dowkeith-laptop login: When I enter my name and password, I remain in a terminal mode (dowkeith@dowkeith-laptop:~ $ 

I have tried to solve this on my own. I hope to learn Linux, but right now I am lost without my GUI. Based on the little I know, I tried the command startx and got a fatal error message back. I have tried control-alt-and various F keys and different Linux options when I boot up. Nothing works. Can someone get me back to my trusty GUI?

---

### Post by SunnyRabbiera on 2008-04-26
huh, did you try to type in sudo apt-get ubuntu desktop?

its possible with the servers going nuts right now something messed up in your upgrade

---

### Post by riven0 on 2008-04-26
I agree. It sounds like the ubuntu-desktop wasn't installed.

---

### Post by Peter09 on 2008-04-26
What happens if you type startx at the command prompt?

PC

---

### Post by 3rdalbum on 2008-04-26
What is the fatal error message? Is it "no screens found"?

You might need to run a live CD and copy /etc/X11/xorg.conf from there onto your new system. But you're right in thinking that this shouldn't normally happen.

---

### Post by dowkeith on 2008-04-27
This is for closure. I thank you for helping me get Gnome installed. Gnome seems to be running but is depressed like me. When I try to exit from the terminal mode (I do have to power down), I get a message: "stopping gnome display manager." When I log on in the terminal mode, I get three sets of these messages: "Cannot allocate res region 7 of bridge. Then follow the same messages for regions 8 and 9 of bridge. This set of messages repeats three times." Does this mean anything? Thanks again. Keith

---

### Post by dowkeith on 2008-04-27
I had already tried startx. It didn't work. Thanks to some dvice I got in the forum I was able to download gnome with the: "sudo apt-get install gnome" command. Now it seems to be running, but I am still in a command mode when Ubuntu boots up. I get a series of messages when it is bootomg up that say: "cannot allocate res region 7 of bridge"; "cannot allocate res region 8 of bridge" and "cannot allocate res region 9 of bridge." I am clueless as to what this means or what is happening to gnome.
Thanks for your interest.

---

### Post by encompass on 2008-04-27
Interesting... could you tell us about your computer... for example the model?  And how old is it?  Did it have a working OS on there before?

---

### Post by encompass on 2008-04-27
I would also recommend trying... sudo apt-get install ubuntu-desktop
I just want to make sure everything that is supposed to be installed is.
Thanks.

---

### Post by riven0 on 2008-04-27
> **dowkeith said:**
> I had already tried startx. It didn't work. Thanks to some dvice I got in the forum I was able to download gnome with the: "sudo apt-get install gnome" command. Now it seems to be running, but I am still in a command mode when Ubuntu boots up. I get a series of messages when it is bootomg up that say: "cannot allocate res region 7 of bridge"; "cannot allocate res region 8 of bridge" and "cannot allocate res region 9 of bridge." I am clueless as to what this means or what is happening to gnome.
Thanks for your interest.

Is it possible the login manager, GDM, is not installed? Try installing that: sudo apt-get install gdm. Choose it as the default login manager when it asks. Also, try installing ubuntu-desktop as someone else mentioned.

---

### Post by dowkeith on 2008-04-28
You are right, At first the GUI hadn't downloaded. I was able to download gnome with this command: sudo apt-get install gnome. The problem is that gnome still doesn't boot up when I turn my compuer on. I tried startx gnome, and I get the fatal error, no screens response.

---

### Post by encompass on 2008-04-28
I keep asking, but you don't respond.
Did you run this?
```
sudo apt-get install ubuntu-desktop
```
if not... and you needed too... then you would have gnome installed but you wouldn't have it come to a graphical login.
That's why I keep pestering you.

---

### Post by dowkeith on 2008-04-29
Hi encompass:
Thanks for your intest. It appears that gnome originally didn't get downloaded when I upgraded from Gutsy to Hardy. I did the sudo apt-get gnome command -- after ubuntuy desktop didn't work. That seemed to have downloaded gnome, but it still doesn't come up when I turn my computer on. I tried to jumpstart it myself with the command: startx gnome. I got the response: fata server error. no scres found. xio fatal error 104 (connection reset by peer) on X ":0,0"

When I sign off with the sudo halt command, I get the response: stopping gnome display manager. Tat makes me think gnome was downloaded sucesfully. But the computer is in terminal moe every time I start it up. I have an Acer 5570 2067 notebook. I have a dual boo system. Somewhere, I think I read that starting from scratch with Ubuntu could compromise the Windows side.

thanks:
dowkeith

---

### Post by dowkeith on 2008-04-29
Hi Peter09

I have typed startx gnome. I get a "fatal server error" message. No screens found xio fatal io error 104 (connection reset by peer)on x ":o,0"

dowkeith

---

### Post by dowkeith on 2008-04-29
Hi encompass:

I can't remember if I responded to this or not. I have an Acer 5570 2067 notebook that I bought last summer. It came with Windows Vista installed. I hated Vista so much I turned to linux in September but took the cowardly way of going to a dual boot system. As things turned out, that may have been a good thing. I am pretty tusre the install worked because I get "stopping gnome display manager" when I give a halt command.

---

### Post by bilal.17 on 2008-04-29
try re-installing ubuntu, for the easiest way to solve it

---

### Post by dowkeith on 2008-04-29
Hi Riven0

I did the command sudo apt-get gdm and got an inalid operation response. I think I already have gdm, as my system tells me it stopped gnome display manager every time I give a sudo halt command. The display manager appears to come up, but I never get out of terminal mode.

---

### Post by dowkeith on 2008-04-29
Hi bilal.17

I thought about reinstalling. My only concern is that I have a dual boot system. Somewhere, I think I read that if you uninstall Ubuntu, Windows on the other side could collapse with it. If I reinstall Ubuntu, would this threaten Windows? I use Ubuntu 99% of the time. I only go to Windows to move money to my checking account and to pay bills online. I use Ubuntuy for all other browsing. I think Vista sucks, but if I have a second system for financial transactions only, it seems safer.

---

### Post by lazyart on 2008-04-29
Try reconfiguring X:```
sudo dpkg-reconfigure xserver-xorg
```follow the prompts, restart and see if it helps.

I presume you're using some software for your bank transactions?  I do all that stuff from ubuntu.

---

### Post by dowkeith on 2008-04-30
Hi lazyart:
Would it make sense to get my old Fesity Fawn disc out, reinstall and then update to Hardy Heron? I haven't figured out how to do this in terminal mode yet. What does the reconfigure command do.

Re: the other question. For some reason, my bank's online account works better on bill paying with Windows. I am also used to sweeping for viruses and sypware with Webroot. I don't have that same feeling wi Linux. I once had Avast, but it gummed up my system. I have heard there are few viruses or spyware items with Linux. It just seemed like a good idea to do general web browsing on one platoform and all other browsing on the other. Make any sense?

---

### Post by encompass on 2008-04-30
no... a hardy heron install is the best bet and it seems the install didn't work.  you can verify the disc before installing to check for errors in the disk.  That would probably be your best bet.  Just install from a hardy live cd.  Your getting some very funky errors. Upgrading is pointless if you have the full on cd.
And about antivirus... I highly doubt you will need that any time soon.  You have to really try to ruin your computer with a virus in linux.
[http://www.securityfocus.com/columnists/188](http://www.securityfocus.com/columnists/188)
This is a good article to give you an idea of the difference.
Also... providing repositories of all the programs you would want to use is another way for your computer to not get malware, and virus's.

---

### Post by Jeffrey Tooker on 2008-04-30
[QUOTE=encompass;4849320]no... a hardy heron install is the best bet and it seems the install didn't work.  you can verify the disc before installing to check for errors in the disk.  That would probably be your best bet.  Just install from a hardy live cd.  Your getting some very funky errors. Upgrading is pointless if you have the full on cd.>>>

I am very new to this but IMHO I have figured something out.  I started out on Ubuntu Users list just before Hardy came out.  That list is on the opposite end of the spectrum from "Beginner Talk".  They were working in the Hardy Beta, and were having fitts.  I came to this list where I may have a chance of getting up to speed.  I have decided to stay with Gutsy untill I get a bit more up to speed.  I will let the super Ubuntu people clean up Hardy.  In a few months it will be much better than it is now. And I may have a better understanding of Ubuntu.  gutsy is still supported for another 12 months.  I do not need to fight the learning curve and the problems in Hardy.

Jeffrey Tooker
Paynes Ck. Ca.

---

### Post by encompass on 2008-05-01
That's just fine.
You will also find the developers do nothing but complain.  There is always something wrong.  (I would know, I am one.)  So it's common to hear these issues.  You can do that, it's just fine.
So I am a little lost though. Could you give us a status update?
Is your system working?
Did you run sudo apt-get install ubuntu-desktop?  You said you have run apt-get install gdm.  But I wanted to know the output of sudo apt-get install ubuntu-desktop.

---

### Post by dowkeith on 2008-05-01
Hello SunnyRabbiera

Just a note to thnank you for your help. A variation of your sudo install ubuntu desktop command plus a reconfiguration command got me back with a GUI. I'm not 100% back, but I am satsfied and think I an get back on my own. For some reason, I left Ubuntu and wound up with Kobuntu. Places doesn't work -- it justy winks on and off -- apparently because I don't hsve Navigator. But I do have Konquerer, which does the same thing. The most irritating thing is that I can't move or resize windows, but I expect to solve this.
dowkeith

---

### Post by dowkeith on 2008-05-01
Hello Riven0

I just wanted to thank you for responding to my query. I have a GUI again. Even though I am not 100% back, I feel confident I can get there now. Fo some reason, I came back in Kubuntu and not Ubuntu. What worked was a combination of sudo apt-get install gnome comand and a second reconfigure command. The only problems now are that places don't work because I don't have Navigator, but I do have Konquerer.  For some reason, I can't resize or move windows, and some come up in bad places. In addition, "suspend" doesn't seem to work properly. All these are minor compared to what I went through. I am going to work on switching back to Ubuntu.
Keith

---

### Post by dowkeith on 2008-05-01
Peter09

I just wanted to thank you for responding to my query. I have a GUI again. Even though I am not 100% back, I feel confident I can get there now. Fo some reason, I came back in Kubuntu and not Ubuntu. What worked was a combination of sudo apt-get install gnome comand and a second reconfigure command. The only problems now are that places don't work because I don't have Navigator, but I do have Konquerer.  For some reason, I can't resize or move windows, and some come up in bad places. In addition, "suspend" doesn't seem to work properly. All these are minor compared to what I went through. I am going to work on switching back to Ubuntu.
Keith

---

### Post by dowkeith on 2008-05-01
Hi 3rdalbum:

I just wanted to thank you for responding to my query. I have a GUI again. Even though I am not 100% back, I feel confident I can get there now. Fo some reason, I came back in Kubuntu and not Ubuntu. What worked was a combination of sudo apt-get install gnome comand and a second reconfigure command. The only problems now are that places don't work because I don't have Navigator, but I do have Konquerer.  For some reason, I can't resize or move windows, and some come up in bad places. In addition, "suspend" doesn't seem to work properly. All these are minor compared to what I went through. I am going to work on switching back to Ubuntu.
Keith

---

### Post by dowkeith on 2008-05-01
Hi encompass:
I just wanted to thank you for responding to my query. I have a GUI again. Even though I am not 100% back, I feel confident I can get there now. Fo some reason, I came back in Kubuntu and not Ubuntu. What worked was a combination of sudo apt-get install gnome comand and a second reconfigure command. The only problems now are that places don't work because I don't have Navigator, but I do have Konquerer.  For some reason, I can't resize or move windows, and some come up in bad places. In addition, "suspend" doesn't seem to work properly. All these are minor compared to what I went through. I am going to work on switching back to Ubuntu.
Keith

---

### Post by dowkeith on 2008-05-01
Hi Bilal.17
I just wanted to thank you for responding to my query. I have a GUI again. Even though I am not 100% back, I feel confident I can get there now. Fo some reason, I came back in Kubuntu and not Ubuntu. What worked was a combination of sudo apt-get install gnome comand and a second reconfigure command. The only problems now are that places don't work because I don't have Navigator, but I do have Konquerer.  For some reason, I can't resize or move windows, and some come up in bad places. In addition, "suspend" doesn't seem to work properly. All these are minor compared to what I went through. I am going to work on switching back to Ubuntu.
Keith

---

### Post by dowkeith on 2008-05-01
Hi lazyart:

I just wanted to thank you for responding to my query. I have a GUI again. Even though I am not 100% back, I feel confident I can get there now. Fo some reason, I came back in Kubuntu and not Ubuntu. What worked was a combination of sudo apt-get install gnome comand and a second reconfigure command. The only problems now are that places don't work because I don't have Navigator, but I do have Konquerer.  For some reason, I can't resize or move windows, and some come up in bad places. In addition, "suspend" doesn't seem to work properly. All these are minor compared to what I went through. I am going to work on switching back to Ubuntu.
Keith

---

### Post by dowkeith on 2008-05-01
Hi Jeffrey:
You are smart to stay with Gutsy. That's when my problems began. I will never upgrade right away again. What worked for me was a combination of sudo apt-get install gnome and a second reconfiguration command. Oddly, though, I came back -- not in Ubuntu where I was -- but in a limping Kubuntu platform. Places doesn't work because I have Konquerer and not Navigator, and I can't move or resize windows. Finally, "suspend" apparently doesn't work either. Gutsy worked great for me. So did Feisty, the prior release. Still, I think I am on the way back and am so haqppy I am no longer in permanent terminal mode.
Keith

---

### Post by encompass on 2008-05-01
Interesting way to thank people. umm... I am not sure how you did it... but that desktop is NOT the way it should be.  You may want to really consider a reinstall.  Runing kubuntu when you told it to run ubuntu and other what not is one crazy setup.  And if you don't have any window borders then it sounds like you have a problem with the window manager.  Very interesting indeed.

---

### Post by dowkeith on 2008-05-03
Wish I had known what you know before I upgraded to Hardy.
Keith Jones
Old Bridge, NJ

---

### Post by dowkeith on 2008-05-03
I am not sure how this happened, but I seem to have an odd mixture of Ubuntu and Kubuntu. The logo at the top is Ubuntu red instead of Kubuntu blue. Navigator just wigs on and off before it dies. But Kongueror works. What I miss most is the toolbar with the bookmarks on it in Firefox. I can live with the unresponsive windows, since I can maximize and close them from the bottom tabs. Someone else told me there are a lot of bugs in hardy and said he is waiting a few months. I think I will do the same. 

I have several Linux books I can read in the meantime. I also bought a Dell recently (the problems are on an Acer notebook). I will get an external drive for it and run Linux from there. I think the only answer is to reinstall Linux on this notebook, but I am wary because I have a dual-boot system. I don't even know how to delete Linux from the partition before reinstalling. 

I feel like a traitor still having a dual-boot. Here are my excuses. It is terrific doing nothing but financial stuff on the Vista side so that I never see spyware there. All my regular browsing is in Linux. Besides, I have a language program and audio tape resoration program that both require Linux. I have been on Linux since last September and have loved every minute of it until now. I have no plans to go back to the dark side.

---

### Post by encompass on 2008-05-04
Well, I would recommend that if you want everything restored to the way it should be backup your data and do a full resinstall.
This time try it this way.
Give your system about 7-10GB oh "/" for your installed files... Then make another partition for swap (At least as much as your ram if you have more than 1 GB, and at about double if you have less than 1 GB) and then one your "/home/"
that way, when ever there is a new version of linux that you would like to try... you can simply format "/" and not format "/home/" and make the computer aware that you want that as your "/home/" then all your personal settings are still there and all you have to do is install your extra software.. all of which can be does automatically too, because your using a package manager.
So... I say you backup your data somewhere, then format the drive and go that way.  Not much more I can say about it.
Good luck...(You have to PM me from this point on... I will be unsubscribing from this thread.)

---

