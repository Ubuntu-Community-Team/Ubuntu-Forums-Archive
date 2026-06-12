---
title: "[SOLVED] Removed Firestarter"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Georgia boy on 2008-08-23
I had installed Firestarter using the Applications Add/Remove. After reading in all of the Firewall Sections of the Forum I decided to remove it  because of everyone saying that it was dead and no longer supported. I removed it by the same way I had installed it.


Now, lets see if I'm understanding this right. Ubuntu comes with a firewall installed already called IPtables. All ports are opened. Coming from XP I'm kind of confused about these kind of things. With XP I use the free Zone Alarm which blocks incoming and asks about something trying to go out. Guess I got kind of used to that and when I read about everything being opened I got lost.

So after removing the Firestarter the way I did, everything should be the same as before since I hadn't gone into Firestarter and changed any settings right? All it was doing was telling about some things being blocked from coming in. 

So, that would put me back at where I had started with open ports. Won't that leave me out in the open where everyone and anyone can get into my system or no? I'm safe?

I know, stupid questions but I'm crossing over from Windows and am constantly learning about the many differences between Ubuntu and Windows. Boy is this fun. :)

Go ahead, hit me over the head with the rolling pin.  :lolflag:

Thanks for all of the help that I have been getting from the forum. You guys and gals just don't know how much you have helped me with my questions. Yes, you can teach an old dog new tricks. I'm constantly learning. :)

Thank you in advance everyone!!!!!!!!!!!
Tom

---

### Post by ayenack on 2008-08-23
No you've got it the wrong way round. On Ubuntu all ports are closed by default you have or a program you are running has to open a port. Take a look at this it'll give you an idea on what's going on.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Scroll down to Firewall for info on firewalls. The rest also makes good reading.

---

### Post by Sef on 2008-08-23
Firestarter is simpley a front-end GUI for IPTables.

---

### Post by mcduck on 2008-08-24
> **ayenack said:**
> No you've got it the wrong way round. On Ubuntu all ports are closed by default you have or a program you are running has to open a port. Take a look at this it'll give you an idea on what's going on.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Scroll down to Firewall for info on firewalls. The rest also makes good reading.

Actually they are open, in the sense that there is no additional program preventing connections. **But** they are closed in the sense that there is no running programs that would respond to any incoming connections. And that is the reason why a firewall is not needed with the default setup. Iptables, by itself, doesn't work as firewall. Not before you give it some rules to work with, and you ened to do that on every boot. So just having iptables as part of the Linux itself doesn't mean that you would actually have a working firewall. You also need some script or other way to load the firewall rules on every biot before iptables does anything.

It makes no difference if a port is open or closed if there is nothing listening to that port. Unlike Windows, Ubuntu doesn't run any services that would do this unless you instal them yourself. If you then install some server application that listens to incoming connections you should of course also configure the firewall.

The talk about Firestarter not being supported any more is nonsense. If it's in the repositories, it's supported. It might not be very actively developed these days, but that's just normal in open-source world, when a program does what it needs to do and has no more bugs to fix it's ready. There is no need to provide new versions every year because nobody is trying to make money with the program.

It's true that Ubuntu developers added another firewall configuration tool, UFW, but that doesn't mean that you couldn't use Firestarter instead if you rather use a GUI tool. UFW is a command-line program, anyway, and because of that definitely not the tool for everyone.

---

### Post by ayenack on 2008-08-24
> **mcduck said:**
> Actually they are open, in the sense that there is no additional program preventing connections. **But** they are closed in the sense that there is no running programs that would respond to any incoming connections. And that is the reason why a firewall is not needed with the default setup. Iptables, by itself, doesn't work as firewall. Not before you give it some rules to work with, and you ened to do that on every boot. So just having iptables as part of the Linux itself doesn't mean that you would actually have a working firewall. You also need some script or other way to load the firewall rules on every biot before iptables does anything.

It makes no difference if a port is open or closed if there is nothing listening to that port. Unlike Windows, Ubuntu doesn't run any services that would do this unless you instal them yourself. If you then install some server application that listens to incoming connections you should of course also configure the firewall.


Ho-Hum.

Moving on. You could use Ubuntu Firewall and its GUI. Take a look at this. 

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

If you scroll to the very bottom there's a GUI .deb file so it's nice and easy to install and use you just have to enable the firewall and use the GUI to configure it. If you read the instructions on the Wiki it'll give you the basic commands to do this also read the link I posted earlier for a more in-depth description on how to set up a firewall. As mcduck and Sef pointed out Firestarter is just a front end (GUI) fo IPTables as is Ubuntu Firewall they pretty much work the same.

---

### Post by Georgia boy on 2008-08-24
Okay. So, Itables just are sitting in the OS not doing anything until we set them up with commands as with the UFW  if we go that route. And with Firestarter you would have to do the same right? In actuality then nothing leaves out of Ubuntu to go out to the web. And nothing should be trying to get into our system or am I getting turned around in my thinking again? :confused:

If we just leave it where it's at then everything should be okay. Sounds like having to tell it properties each time on boot up is a pain in the buns. 

So, if just left alone then all should be fine. But, I guess I should eventually get a hardware firewall. Lot of my friends are always telling me that I should get one for between the modem ad computer. 

Thanks guys. Always appreciate your great help and advice. Constantly learning and having questions.

Tom

---

### Post by mcduck on 2008-08-25
> **Georgia boy said:**
> Sounds like having to tell it properties each time on boot up is a pain in the buns. 

Well, it's usually doen using some script configured to load when the computer is started. Both UFW and Firestarter have their own scripts that load the iptables rules on boot. The script may also runa s services, changing the firewall rules automatically depending on the situation.

It's also possible to just write your own firewall script, and there are several ready-made ones available like the excellent Arno's IP-tables-firewall.

Edit: Yes, as log as you install software only from truested sources (like Ubuntu's repositories) there is no need to worry about programs "calling home". So monitoring/limiting outbound traffic is not needed. And incoming traffic doesn't need limiting if there's nothing listening to it.

---

### Post by ayenack on 2008-08-25
Many people do not use a firewall on Ubuntu and basically trust their routers firewall to keep out the bad guys. The way to think about it is as soon as you open an internet browser such as Firefox you are opening a port (Port80 in most cases) then if you were to install an news reader or e-mail client it's possible that other ports might be opened. For instance if you were to install Gnump3d (a music streamer) it'll open port 8888 if I remember correctly and listen for incoming connections, if you were to install SSH it'd open port 22 and listen for incoming connections. Then it's down to you to restrict the the people who are allowed to connect to these ports either by installing and configuring a firewall (not as hard as it seems) or manually editing the IPTables rules to deny and allow connections or using the program that's listening on the port to allow certain connections with password/IP Address rules etc. 

You can change what port programs listen on to avoid some risk also. If you had SSH installed you'd edit the config file in **/home/Your_User_Name_Here/.ssh/config** and put **port=22222** for instance.

If you use Firestarter from the repo's it should automatically load at boot and you would not need to start it yourself.

To make sure this is happening start your computer and type this in a terminal.

**sudo /etc/init.d/firestarter status**

It'll tell you if the firewall is running or not. The GUI is to show alerts visually in real time rather than looking at the log files.

If you go the UFW way you'll need to start it yourself every boot as far as I know or you could use Sessions from System>Preferences>Sessions to have it start at boot. There may also be a command to make it start at boot you'll have to look on the Wiki for that.

Two way's to start UFW the easiest is to install the GUI for it and then start it with that. The second involves opening a terminal like so.

**sudo ufw enable**

Then for a status report on the firewall do this.

**sudo ufw status verbose**

This all seems very complicated but it really is not if, you are running a standard desktop install. If you have a network it becomes slightly more complicated but not rocket science. In my experience most complications come from running server applications on a standard desktop that is used as the family computer rather than a dedicated server that can be monitored and firewalled very specifically.

Phew long reply. Hope it helps a bit.

---

### Post by Takmadeus on 2008-08-25
So, given the case that with that command firestarter tells you that it is not running, what do you do?

---

### Post by robert shearer on 2008-08-25
I have used Guarddog as the gui front end to ip tables.
Needs to be setup using  "sudo guarddog" in a terminal to bring up the gui.
It does install several KDE libraries but has a most excellent website c/w manual.
Should be installable using synaptic.

---

### Post by ayenack on 2008-08-25
> **Takmadeus said:**
> So, given the case that with that command firestarter tells you that it is not running, what do you do?

Apologies. I totally miss read your question. There are a few things you can do. Make sure it's installed is the most obvious. Then from terminal do this.

**sudo /etc/init.d/firestarter start** (will start it once your system is up. Or you could use the GUI to start it.)

Might be an idea to re-install to make sure it's the repo's install by doing this.

**sudo apt-get remove --purge firestarter**
**sudo apt-get install firestarter**

There's also a way to make it start at boot but I can't remember exactly how to do it. I think it's something like this, sudo update-rc.d firestarter add or sudo update-rc.d firestarter default but can't remember so would not advise using these commands. Take a look here for more info.

 [http://www.fs-security.com/docs/](http://www.fs-security.com/docs/)

------------------------------------------------------------------------------------------
Depends on your setup. Let's say you use Samba (smb) to stream content from your server you might want to change the firewall settings to only allow Samba connections from its specific IP Address and over a certain port. The easiest way to do this would be to start the GUI of Firestarter and click on the policy tab then right click in the **Allow service Port For** which will bring up a drop down menu select **Add Rule** this will bring up a config window then you'd do something like this.

1, Name **Samba (smb)**
2, Port **137-139 445** ( If these are the ports Samba is listening on.)
3, IP, host or network **192.168.1.2** (If this is the address of the server.)
4, Comment **My Samba connection**

That should do it. You could also set it up to allow connections from a specific IP Address in roughly the same way.

---

### Post by whitethorn on 2008-08-25
I personally had some problems using Firestarter because it didn't allow VPN tunneling which I need to use to be able to connect to some of my universities websites. I also found a nice GUI for ufw called GUFW..  Found here.

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

It's pretty straightforward.

---

### Post by Takmadeus on 2008-08-25
> Depends on your setup. Let's say you use Samba (smb) to stream content from your server you might want to change the firewall settings to only allow Samba connections from its specific IP Address and over a certain port. The easiest way to do this would be to start the GUI of Firestarter and click on the policy tab then right click in the Allow service Port For which will bring up a drop down menu select Add Rule this will bring up a config window then you'd do something like this.

1, Name Samba (smb)
2, Port 137-139 445 ( If these are the ports Samba is listening on.)
3, IP, host or network 192.168.1.2 (If this is the address of the server.)
4, Comment My Samba connection

That should do it. You could also set it up to allow connections from a specific IP Address in roughly the same way.

Nevermind, it was a problem at startuip when firestarter did not recognize the network as ready, so it would just think it was not necesary to start the daemon. 

I fixed it using this guide:

[http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)

Thanks though ;)

---

### Post by ayenack on 2008-08-25
> **Takmadeus said:**
> Nevermind, it was a problem at startuip when firestarter did not recognize the network as ready, so it would just think it was not necesary to start the daemon. 

I fixed it using this guide:

[http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)

Thanks though ;)

Sorry. I totally miss read your question first off. Edited the post with some more relevant info.

---

### Post by wgrant on 2008-08-25
> **ayenack said:**
> Many people do not use a firewall on Ubuntu and basically trust their routers firewall to keep out the bad guys. The way to think about it is as soon as you open an internet browser such as Firefox you are opening a port (Port80 in most cases) then if you were to install an news reader or e-mail client it's possible that other ports might be opened. For instance if you were to install Gnump3d (a music streamer) it'll open port 8888 if I remember correctly and listen for incoming connections, if you were to install SSH it'd open port 22 and listen for incoming connections. Then it's down to you to restrict the the people who are allowed to connect to these ports either by installing and configuring a firewall (not as hard as it seems) or manually editing the IPTables rules to deny and allow connections or using the program that's listening on the port to allow certain connections with password/IP Address rules etc. 

Er, no. Using Firefox won't open any ports - it will make an outgoing connection on a somewhat random port, but it's not a security risk as it won't accept new connections! The same applies to news readers, email clients, and pretty much anything that is not a daemon.

Unless you install strange servery apps, you don't need a firewall on your Ubuntu machine.

---

### Post by ayenack on 2008-08-25
> **fujitsu said:**
> Er, no. Using Firefox won't open any ports - it will make an outgoing connection on a somewhat random port, but it's not a security risk as it won't accept new connections! The same applies to news readers, email clients, and pretty much anything that is not a daemon.

Unless you install strange servery apps, you don't need a firewall on your Ubuntu machine.

You're right of course. As you say it's more down to installing server type apps that normally cause a problem.

About an E-mail/News readers client if you have it set up to retrieve new mail is it not opening and listening on a port? I know many people do not do this but many do also.

---

### Post by wgrant on 2008-08-25
> **ayenack said:**
> You're right of course. As you say it's more down to installing server type apps that normally cause a problem.

About an E-mail/News readers client if you have it set up to retrieve new mail is it not opening and listening on a port? I know many people do not do this but many do also.

No, why would it? That would greatly limit its usability behind a NAT.

---

### Post by OrangeCrate on 2008-08-25
Regarding whether a new user needs to configure a firewall or not, this is one of the best, if not the best, I've seen on the forums. It should be required reading for all new converts from Windows. Excellent, sane, and rational discussion, thanks to all who've contributed.

---

### Post by Georgia boy on 2008-08-25
Hi! Looks like I opened up a great discussion here. I like what I'm reading. A lot of learning in this for me. A lot to decipher and think about. 

I agree with OrangeCrate, this is a vast of knowledge that you guys and gals have been contributing here. I know that I can come here and count on your ideas and suggestions to help me along. I am a newbie and think that something like this should be set up for reading.

Maybe a sticky or a tutorial could be aranged for someone like me who is in the dark a lot on trying to learn what to do and what not to do?

So, if I reinstall Firestarter, or Guarddog as Robert did it will automatically configure the IPtables and I don't have to do anything? 

I haven't done any installation of any software except for the ones in the applications-add/remove section. Oops. I forgot, I did download a gallery extension for OpenOffice.org. Also downloaded a gstreamer so that Totem would work. Other than that I haven't downloaded anything except what is open source in the download area.

I only have the one desktop comoputer, so there won't be server or network installations. 

Again I thank everyone who has contributed to this thread. It is a great releif knowing that I can count on you guys and gals for help on my learning. The saying that you can't teach an old dog new tricks went out the window when coming over to Ubuntu and this wonderful formu. I'm old and am constantly learning. No slamming or putting down here, just wonderful help.

Thanks everyone in advance for your help!! :)

Tom

---

### Post by coffeecat on 2008-08-25
> **mcduck said:**
> The talk about Firestarter not being supported any more is nonsense. If it's in the repositories, it's supported. It might not be very actively developed these days, but that's just normal in open-source world, when a program does what it needs to do and has no more bugs to fix it's ready. There is no need to provide new versions every year because nobody is trying to make money with the program.

I want to pick up on this. To say that an application is supported because it is in the repositories is missing the point. And to say that there is no need to provide new versions is missing an even bigger point. My understanding is that Firestarter has problems with the netfilter code in the versions of the kernel that have appeared after it stopped being actively developed. There has been considerable development of the kernel over the last couple of years which means that any issues are likely to be getting worse. [This link]("http://article.gmane.org/gmane.comp.security.firewalls.firestarter.user/1342") is over a year old, but it makes a valid point. I accept that there seems to have been some activity on the Firestarter website since then, but has that been translated into updated code? I don't know. Certainly, my recent experience with FS in Hardy is that it is buggy and troublesome, and worse - not doing what it says it is doing. Which is a great pity. It has a good GUI interface. I wish someone could rescue it from the doldrums.

In the meantime, thanks to those who pointed out Gufw.

---

### Post by billgoldberg on 2008-08-25
> **Georgia boy said:**
> Okay. So, Itables just are sitting in the OS not doing anything until we set them up with commands as with the UFW  if we go that route. And with Firestarter you would have to do the same right? In actuality then nothing leaves out of Ubuntu to go out to the web. And nothing should be trying to get into our system or am I getting turned around in my thinking again? :confused:

If we just leave it where it's at then everything should be okay. Sounds like having to tell it properties each time on boot up is a pain in the buns. 

So, if just left alone then all should be fine. But, I guess I should eventually get a hardware firewall. Lot of my friends are always telling me that I should get one for between the modem ad computer. 

Thanks guys. Always appreciate your great help and advice. Constantly learning and having questions.

Tom

Just get a router to replace your modem and you should be good.

Any modern router will have a decent hardware firewall.

If you just have a modem and you are not running any kind of server software, you should also be good.

But I would configure firestarter anyway if I were you. You just have to set it once, not every time you start the pc.

---

### Post by robert shearer on 2008-08-25
Quote;
So, if I reinstall Firestarter, or Guarddog as Robert did it will automatically configure the IPtables and I don't have to do anything?

Guarddog will need to be configured.

Handbook is here:

[http://www.simonzone.com/software/guarddog/manual2/](http://www.simonzone.com/software/guarddog/manual2/)

---

### Post by ayenack on 2008-08-25
> **Georgia boy said:**
> 
So, if I reinstall Firestarter, or Guarddog as Robert did it will automatically configure the IPtables and I don't have to do anything? 


If you install firestarter from the repo's it'll ask you a few questions when you first start it and then you should be set.

To install do this in a Terminal.

**sudo apt-get install firestarter**

Then once it's all installed and set up do this to make sure it's running.

**sudo /etc/init.d/firestarter status** (It should say *** Firestarter is running...** .)

That's it. [UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall") and it's [GUI]("http://gufw.tuxfamily.org/index.html") are very similar to firestarter and may be the way to as it's going to be incorporated into and supported by the Ubuntu team in the long term as far as I know. I believe it's going to be enabled by default in the next release of Ubuntu.

---

### Post by Georgia boy on 2008-08-26
When is the new release due out? So, the new release will supposedly be all set up? Great!!!!!

Tom

---

### Post by ayenack on 2008-08-27
> **Georgia boy said:**
> When is the new release due out? So, the new release will supposedly be all set up? Great!!!!!

Tom

A new version of Ubuntu is released every six months. The numbers 8.04 after the Ubuntu name indicate year of release and then the month of release so 8.04 was released April 2008. The next release will be October 2008.

You can use UbuntuFirewall on Ubuntu 8.04.1 Check out the links I posted in my previous post for details on how to do this.

---

