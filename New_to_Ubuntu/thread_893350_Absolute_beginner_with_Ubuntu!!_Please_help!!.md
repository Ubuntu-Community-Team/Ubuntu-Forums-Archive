---
title: "Absolute beginner with Ubuntu!! Please help!!"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Stygian_Plethora on 2008-08-18
Hey there all Ubuntu users!

I have just installed Ubuntu Linux as my new and main OS on my AMD Athlon 64. In short, it's fantastic! Already it has boosted my pc's perfomance exponentially! I do, however have a couple of questions:

1) I would like to install my old OS (Microsoft Wind XP SP2) as a virtual PC (have already installed the correct driver for the accelerated graphics) on my desktop so that I can run all my old applications (like photoshop and microsoft word) and games when I want to. I have seen it done as a demo in several different videos on youtube and other sites but I can't seem to find a tutorial on how to do it myself. So... the question relating to this is: can someone please give me instructions or point me in the right direction towards a video or text tutorial on how to do this?

2) I can't get the firewall (firestarter) to start up, it keeps telling me that the device eth0 is not ready, whatever that may mean. I run 1 wireless router and 1 ISP modem. I have no idea what I'm doing with it in terms of this OS as on XP it just set everything up automatically.

3) I would like find the equivalent of Grisoft's AVG to run as an anti-virus program, but don't know if I can use that or if I need to find the Ubuntu equivalent.

and lastly, 4) How do I get Skype on there?

Thank you for your patience!!

Ben

---

### Post by thestig_992 on 2008-08-18
Well, as for your first question, i followed a tutorial to install virtualbox from here [http://ubuntuforums.org/showthread.php?t=433359]("http://ubuntuforums.org/showthread.php?t=433359"). Virtual box is an opensource version of VMware, and it works fine, infact it runs faster than my real windows does, and it has 1/4 of the ram..XD
question 3: i use a program imaginatively called virus scanner. just search for it in the repositries...having said that i dont think that your under much threat so long as you keep to to the official repositries, and they have everything that yu need...

---

### Post by hyper_ch on 2008-08-18
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by amo-ej1 on 2008-08-18
- eth0 is your first ethernet card (probably the wired one) which is not connected since you're on wireless. But since you're behind a wifi router which probably does NATting for  you, isn't it pointless to configure a firewall ? 

- most viruses, worms, and other nasty things are targeted towards windows users, you're pretty safe under Linux without an antivirus to slow your system down.

---

### Post by meindian523 on 2008-08-18
> **Stygian_Plethora said:**
> 
1) I would like to install my old OS (Microsoft Wind XP SP2) as a virtual PC (have already installed the correct driver for the accelerated graphics) on my desktop so that I can run all my old applications (like photoshop and microsoft word) and games when I want to. I have seen it done as a demo in several different videos on youtube and other sites but I can't seem to find a tutorial on how to do it myself. So... the question relating to this is: can someone please give me instructions or point me in the right direction towards a video or text tutorial on how to do this?
You need a virtualization software,Xen,VMWare and some other softwares are available,which I can't remember off the top of my head. 
> **Stygian_Plethora said:**
> 
2) I can't get the firewall (firestarter) to start up, it keeps telling me that the device eth0 is not ready, whatever that may mean. I run 1 wireless router and 1 ISP modem. I have no idea what I'm doing with it in terms of this OS as on XP it just set everything up automatically.
Quit firestarter.
```
gksudo gedit /etc/firestarter/firestarter.sh
```
Place a hash(#) in front of the following lines,and ONLY the following lines,don't touch any of the others:
> 
if [ "$MASK" = "" -a "$1" != "stop" ]; then
	echo "External network device $IF is not ready. Aborting.."
	exit 2
fi
Restart firestarter.
> **Stygian_Plethora said:**
> 
3) I would like find the equivalent of Grisoft's AVG to run as an anti-virus program, but don't know if I can use that or if I need to find the Ubuntu equivalent.
You don't need an antivirus,unless you are networked with Windows machines and want to protect them,because Ubuntu won't get a virus unless you install it with full knowledge.
> **Stygian_Plethora said:**
> 
and lastly, 4) How do I get Skype on there?

Thank you for your patience!!

Ben

I believe Skype has a Linux version,but I've heard of problems too.You will have to wait for other people to help you out on this.

---

### Post by stalkingwolf on 2008-08-18
> (like photoshop and microsoft word) 

IMO openoffice is much better than word.  You can save and
read microsoft formats.  Gimp is equal to photoshop.  However
as I recall photoshop will run in wine or crossoverLinux.  Games,
some will run in Wine, Some in Cedega, and some in crossover.

One of the beauties of this OS is choices.

---

### Post by fiddler616 on 2008-08-18
> **Stygian_Plethora said:**
> Hey there all Ubuntu users!

I have just installed Ubuntu Linux as my new and main OS on my AMD Athlon 64. In short, it's fantastic! Already it has boosted my pc's perfomance exponentially! I do, however have a couple of questions:
Welcome!
> **Stygian_Plethora said:**
> 
1) I would like to install my old OS (Microsoft Wind XP SP2) as a virtual PC (have already installed the correct driver for the accelerated graphics) on my desktop so that I can run all my old applications (like photoshop and microsoft word) and games when I want to. I have seen it done as a demo in several different videos on youtube and other sites but I can't seem to find a tutorial on how to do it myself. So... the question relating to this is: can someone please give me instructions or point me in the right direction towards a video or text tutorial on how to do this?

I'd recommend this:[http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu](http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu)
Except install Windows on Ubuntu, not Ubuntu on Windows.

> **Stygian_Plethora said:**
> 
2) I can't get the firewall (firestarter) to start up, it keeps telling me that the device eth0 is not ready, whatever that may mean. I run 1 wireless router and 1 ISP modem. I have no idea what I'm doing with it in terms of this OS as on XP it just set everything up automatically.

3) I would like find the equivalent of Grisoft's AVG to run as an anti-virus program, but don't know if I can use that or if I need to find the Ubuntu equivalent.

You really don't need it--Ubuntu is much more secure than anything Gates can cook up. However, if you have your heart set on it:
2) I really don't know...sorry
3) Either search anti-virus in Synaptic Package Manager, or these forums, or anti-virus Ubuntu in Google. I've seen articles before, I just forget where. Don't expect an AVG clone though--it'll be the FOSS community's own brand of sweetness.

> **Stygian_Plethora said:**
> 
and lastly, 4) How do I get Skype on there?

Thank you for your patience!!

Ben
I've heard good things about Ekiga Softphone as an alternative, but if Skype's the thing for you, then check out the Wine Application Database:
[http://appdb.winehq.org/](http://appdb.winehq.org/)
or just run Skype through the virtual Windows machine you made in step one :)
Good luck!

Edit: Dang, I thought I was the first poster! The things that happen while you type a reply...Oh well.

---

### Post by LarsW_Tierp on 2008-08-18
I've been running skype for some time now on Ubuntu Hardy.
Go to: [Skype.com]("http://www.skype.com/go/getskype-linux-ubuntu")Save the file on your desktop, double click the file and Let the packetinstaller install the .deb file for you and you should be up and running in notime.

---

### Post by Stygian_Plethora on 2008-08-18
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.
Hey thanks for the tip!! will keep it in mind! sorry for the mistake!! :D

---

### Post by Stygian_Plethora on 2008-08-18
> **Stygian_Plethora said:**
> Hey there all Ubuntu users!

I have just installed Ubuntu Linux as my new and main OS on my AMD Athlon 64. In short, it's fantastic! Already it has boosted my pc's perfomance exponentially! I do, however have a couple of questions:

1) I would like to install my old OS (Microsoft Wind XP SP2) as a virtual PC (have already installed the correct driver for the accelerated graphics) on my desktop so that I can run all my old applications (like photoshop and microsoft word) and games when I want to. I have seen it done as a demo in several different videos on youtube and other sites but I can't seem to find a tutorial on how to do it myself. So... the question relating to this is: can someone please give me instructions or point me in the right direction towards a video or text tutorial on how to do this?

2) I can't get the firewall (firestarter) to start up, it keeps telling me that the device eth0 is not ready, whatever that may mean. I run 1 wireless router and 1 ISP modem. I have no idea what I'm doing with it in terms of this OS as on XP it just set everything up automatically.

3) I would like find the equivalent of Grisoft's AVG to run as an anti-virus program, but don't know if I can use that or if I need to find the Ubuntu equivalent.

and lastly, 4) How do I get Skype on there?

Thank you for your patience!!

Ben
I just want to say a BIG THANKYOU to everybody who has given me advice!! i would reply to you all individually, but as there were so many of you that did reply to this thread that I wouldn't actually get all the things done that you suggested for lack of time!! :D

But many thanks again, it's highly appreciated and I hope that when I get more proficient I can be just as much help to other noobies!!

:D :D

---

### Post by Stygian_Plethora on 2008-08-18
Heya all again...

right, this VMware, I need to find one that I can use for my gaming (such as Oblivion, Fear, Doom 3 and so on) I know that some won't support the 3d power needed for a lot of them, but apparently some will!! What am I looking for, or more pointedly do I Dual-boot?

---

### Post by MacDuff on 2008-08-18
As suggested, you might get more replies if you ask a single specific question but here are some thoughts on Virtual Operating Systems:

If you want to run your applications natively on Windows you can dual boot but if you want to be able to quickly switch back and forth between Windows and Linux the best method is to install a virtual windows system in a Linux install. 

The two Virtual systems that I have used are VMWare Server and VirtualBox.  Both have free versions and both work well for me.  You can search for them using any search engine.  Virtualbox (Note that it is one word) is available from the Ubuntu repositories.  

If you need to use a usb device on your virtual machine, confirm that VMWare Server free version supports it or use the hack on Virtualbox to make USB devices pass through.  Search for "USB on Virtualbox" to find instructions.

To use a virtual machine you must have a copy of the OS that you want to install on it after you install the virtual machine application.  There are many tutorials on how to do this.  If you have a reasonably fast computer with enough RAM (I have one computer with 1Gb and one with 2Gb, both run well) the virtual Windows will run almost as fast as a native Windows application; some apps actually seem to run faster.

---

### Post by The Cog on 2008-08-18
Doom3 has a native Linux installer. I don't remember exactly how I did it though- it was a while ago. Try googling for "doom2 linux installer". The installer might even be on the CD/DVD. 

It's much more tense and edge-of-the-seat jumpy than any other shoot-em-up I ever played. Plain scary, really. If that's any recommendation.

---

### Post by Stygian_Plethora on 2008-08-19
Macduff, thanks, I'll have a look at what you suggested!! In fact, I will be checking everything out, that every1 has suggested when I have the time!

TheCog, thanks for the tip! I'm an ooooooooooooooooold Doom 1, 2 & 3 veteran, I love that game soooooooo much, as I used to play it and others like it when my machine was primarily XP! And yea, for scary, it nearly can't be beaten,
but F.E.A.R. gives it a damn good run for it's money! V.V. Scary!! Works best in the dark with headphones and a surround audio card!

Anyway!! Thanks again to everybody!! :D You all rock!! ;)

---

