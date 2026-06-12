---
title: "Networking Issues"
date: 2015-04-25
forum: New to Ubuntu
---

### Post by Jerid_Hill on 2015-04-25
I am new to Ubuntu (common phrase in these parts) and I had some questions that may or may not be easily answered in a thread based format, but here it goes.

I built a computer and was running Ubuntu on it. I decided to convert it to a server instead, so I installed Ubuntu 14.04 LTS. I then installed the desktop GUI so I could work in a somewhat familiar environment. I've dabbled in Ubuntu in the past but decided recently to really begin learning it. My children wanted a Minecraft server so I felt this was a great opportunity to add this to my linux box and give their friends the ability to play with them.

I've installed everything and it was working well. I believe the problems all began when I was trying to setup a port so I could connect to my computer from outside my network. I chose a port that was midrange, nothing to high and nothing too low. No one could connect to the Minecraft server any longer. After doing more research, the only way I can get anyone to connect is with the command sudo iptables -F which with research also appears to not be a great idea. I have to do this anytime I physically boot the system.

I was also running the network as DHCP. My server's IP changed so I decided to make it a static IP. Network Manager didn't seem to be fully functioning since I couldn't edit or add settings so I went to edit the /etc/network/interfaces file. I changed it to make it static and through the process, I had lost the ability to connect to localhost.

So I attempted to correct some of this and in the process, I could no longer have anyone connect. The great thing is, this is part of my normal learning experience. Break it until it's unusable and figure out a way to fix it! I decided to remove network-manager then reinstall it. After the reinstall, I can now actually use it under the system settings whereas I couldn't before. Unfortunately, I still need to use the command sudo iptables -F to allow folks from the outside world reach my server.

There is so much information on the internet about networking in linux and since I'm still green, I really need to understand the basics of what is happening and how to correct it. If it's too much to go into, is there a solid write up somewhere regarding this? I've seen many, but most of them are for linux users who have an intimate understanding of networking. I can network OSX and Windows, but Linux is more of a hands-on system. I can see the power behind it and why they try to dumb it down. I'd love to have a solid understanding so eventually I'm on the giving end!

Thanks in advance.

---

### Post by The Cog on 2015-04-25
So it's the firewall rules and setup you are having trouble with - right? 

Can you explain how the iptables rules got in there in the first place? A default install doesn't have any iptables rules, so iptables -F will have no effect. You must have done something.

It may help to see your existing firewall rules. Can you post the output of the command **sudo iptables-save -c**? If they contain your public IP address and you prefer to keep that secret, replace it with 1.2.3.4.

---

### Post by dino99 on 2015-04-25
here is a recent howto that works with all kind of client/server, and is able to do its job even with low bandwidth
When you need to use a port, that one needs to be one already not use by the system indeed, and both router & firewall have to be set to allow it (gufw on ubuntu)

As many tweaks have been made on your system, maybe its better to start with a fresh new install, as finding/fixing a borked one can be a nightmare if you are not yet skilled
 [https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/](https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/)

---

### Post by Jerid_Hill on 2015-04-25
In my effort to setup a connection so I can access from outside the network, I'm sure I had done something with iptables. I don't remember doing it and I've heard conflicting information on different discussions stating 14.04 has it doesn't have it etc. I would bet I did something, though.

I think I have limitations being a new user, I couldn't copy and paste, it stated I had to many tags (paraphrase).....

I saved them as a text document, compressed and am attaching.

---

### Post by Jerid_Hill on 2015-04-25
> **dino99 said:**
> here is a recent howto that works with all kind of client/server, and is able to do its job even with low bandwidth
When you need to use a port, that one needs to be one already not use by the system indeed, and both router & firewall have to be set to allow it (gufw on ubuntu)

As many tweaks have been made on your system, maybe its better to start with a fresh new install, as finding/fixing a borked one can be a nightmare if you are not yet skilled
 [https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/](https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/)

Thanks. I told my wife last night I'll probably just end up doing a complete reinstall from scratch. The strange thing is, it was a fresh install and I never could access network manager via GUI until I uninstalled and reinstalled network manager. So this morning, I figured I'd tackle it one last time. It's only a week old, so I think I'm not too far down that path, mostly everything I had done was related to what was mentioned in this thread and I do believe it all started when I attempted to allow for remote access.

---

### Post by Jerid_Hill on 2015-04-25
The Cog: The output was for my system in it's current state. Should I have rebooted and output this before sudo iptables -F or does it matter?

---

### Post by The Cog on 2015-04-25
That's enough info for the moment thanks. 
I don't recognise the names of the iptables chains there. Again, how did they get there? Did you install some kind of firewall program or script?

---

### Post by Jerid_Hill on 2015-04-25
I did install Firewall then removed it, then installed Firewall Configuration (all from Ubuntu Software Center). I know I had disabled firewall because of the issues but still have to sudo iptables -F.

---

### Post by The Cog on 2015-04-25
Hmm. I don't know Firewall Configuration and can't find it in synaptic. Sorry, but I can't help you with that one.

UFW is the recommended firewall program for those that feel they need one. You may get more help if you uninstall Firewall Configuration and install UFW instead.

---

### Post by dino99 on 2015-04-25
UFW is the default installed choice with ubuntu; but to get a more user friendly experience, install gufw; and let the default settings choice. Only add what you need.

---

### Post by The Cog on 2015-04-25
Well, it looks as though Firewall Configuration has left some configuration on the server, even though it has been uninstalled. 

Can any readers suggest how to get all the configuration removed? I would apt-get install the package and then apt-get purge it again, but I don't know the package name. (Purge removes both the application and its configuration files.)

Failing that, it may need another re-install to get rid of whatever it has done to your machine.

EDIT:
Oh! I found the software center on my PC (I didn't know I had it until just now) and it seems that "Firewall Configuration" is actually gufw - the GUI front end to ufw.

Knowing this, the question then becomes - how to configure UFW or GUFW to allow whichever port or ports this minecraft server needs. 
Jerid_Hill: Can you tell us which port numbers you need enabled? If so, it's probably a one-line command to allow the port through - something like **[FONT=Courier New]sudo ufw allow 12345[/FONT]** perhaps.

You will probably have to reinstall gufw or ufw before you can do that command though.

---

### Post by Jerid_Hill on 2015-04-25
Thanks everyone, I'll give it a go and see what happens.

---

### Post by Jerid_Hill on 2015-04-25
> **The Cog said:**
> Well, it looks as though Firewall Configuration has left some configuration on the server, even though it has been uninstalled. 

Can any readers suggest how to get all the configuration removed? I would apt-get install the package and then apt-get purge it again, but I don't know the package name. (Purge removes both the application and its configuration files.)

Failing that, it may need another re-install to get rid of whatever it has done to your machine.

EDIT:
Oh! I found the software center on my PC (I didn't know I had it until just now) and it seems that "Firewall Configuration" is actually gufw - the GUI front end to ufw.

Knowing this, the question then becomes - how to configure UFW or GUFW to allow whichever port or ports this minecraft server needs. 
Jerid_Hill: Can you tell us which port numbers you need enabled? If so, it's probably a one-line command to allow the port through - something like **[FONT=Courier New]sudo ufw allow 12345[/FONT]** perhaps.

You will probably have to reinstall gufw or ufw before you can do that command though.

Sorry, I don't know how I overlooked your post. Yes, later I realized that Firewall Configuration was actually gufw. I found this out by uninstalling it, then going in to Ubuntu Software Center and installing gufw. It ended up being the same GUI. Needless to say, I felt like an idiot, but that's a whole different story. ;)

I installed 2 ports. 22 was already installed by default, so I installed a port to allow myself to get into, which at this point just simply states access denied using x2go. I even tried it on port 22 just in case I set something up incorrectly. No explanations and no other errors. I've followed the tutorial linked earlier and can't get in on a different computer locally or across the web. I also installed the Minecraft port 25565 which works fine as long as I do a sudo iptables -F. That's where I'm currently at. Strange. It's a simple workaround, but one I know isn't ideal.

---

### Post by The Cog on 2015-04-26
> Needless to say, I felt like an idiot, but that's a whole different story.
Yeah, well I'm feeling dumb for not knowing I had the software center on my PC. Doh! We're all learning.

I've never seen gufw or used ufw but a quick google turned up a page [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) that gives basic ufw commands. 
I also found a page [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw) on using gufw.

I don't know if you can switch between which you use, so it's probably best to choose one and stick with it.

I imagine that simply
```
sudo ufw allow 25565
```
would get minecraft working with ufw. 
For gufw, you would probably have to configure a protocol called minecraft, with tcp and udp port 25565 and then allow minecraft through.

I don't know what ports x2go uses. It may be worth running this command and looking to see which ports x2go is listening on:
```
sudo lsof -nPi
```

---

### Post by Jerid_Hill on 2015-04-27
Very strange. I can't seem to get in using x2go. It simply states access denied. I looked to see the open ports. Minecraft's is there and working. 22 is there and says it's assigned to root. Do I need to give port 22 access to my username in order for me to gain log in remotely? Or is there a suggestion on a different way to remote in? I want to remote in using either a Mac or PC.

---

