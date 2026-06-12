---
title: "Do I need a firewall and virus checker on 12.04"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by parcdulas on 2012-08-31
Hi,

I have just got an internet connection on my desktop system running 12.04 with a mobile dongle from O2 in the UK. In my location in mid Wales I can only get a very slow connection. The 'connection information' in Network Manager shows "speed unknown" is this normal?

My Questions are, do I need a fire wall and if so what is recommended. Do I need a virus checker and again if so what is recommrnded

Thanks

---

### Post by tartalo on 2012-08-31
A firewall is a good idea, the default Linux firefall is called iptables, Ubuntu has an iptalbes front-end called ufw (Uncomplicated Firewall) that is good enough for a simple configuration, start with that and if you need something more sophisticated you'll have to learn about iptables.

You don't need an antivirus unless you want to protect a Windows machine through Linux. There are no known viruses for Linux on the wild.

No idea about your internet speed.

EDIT: The graphical front-end of ufw is called gufw

---

### Post by coldcritter64 on 2012-08-31
Ubuntu has a firewall installed, ufw (uncomplicated firewall), but it is turned off by default. You can control it from the terminal or install the package "gufw". If I were to have your setup (laptop and usb dongle) gufw would be one of the first things I add. But don't worry about it _too much_ unless you have added apps that open ports. Ubuntu is secure on install, ie no ports are opened by default. You can be "seen" from the internet but still can't be accessed (ports closed, but visible). Note though, as soon as you connect to the net some ports are opened and are capable of 2 way traffic (of an unwanted nature) if visible, best to turn ufw on an configure it.

I can't comment on NM, I use wicd ;).

Viruses are not such a worry on Ubuntu, if you share data with Windows machines, it is a good idea to install an "on demand" type virus scanner. You really only need to scan files prior to sending them. I have used Avast for Linux in the past, there is an open source scanner available, clamAV.

Some links for general security info are below, they cover much more than what you ask here, but are a good start on understanding the situation in Ubuntu for you. The "Linux Vulnerabilities" section of the Basic security guide covers viruses.

[[COLOR=Blue]Basic Security Wiki[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

[[COLOR=Blue]Security Features,[/COLOR]]("https://wiki.ubuntu.com/Security/Features#Configuration") specifically for Configuration section (no open ports)

[[COLOR=Blue]Security - Community Documentation[/COLOR]]("https://help.ubuntu.com/community/Security") see section 2. for firewall and 13. for antivirus (in the second part "Security Tools")

---

### Post by Bashing-om on 2012-08-31
parcdulas;

  In response to your queries.

"speed unknown" => unable to advise /maybe the slower connections do not register ?
   I am fortunate to finally have a high speed connection (what a joy!)..when my speed does drop (momentarily) then I also get the "speed unknown" advisement on downloads until the connections speed picks back up. 

firewall: depends on how you use your internet connection. Ubuntu is a closed system and any ports opened are at your discretion. So long as you are a stand alone system, not sharing files and resources with the outside world, no estranged applications running, then no firewall is required.
 
Virus protection: At this time there are no known linux viruses in the wild. Ubuntu being a closed system is prohibitive for attacks. If one does not inter-relate with windows or other virus prone systems there again is no requirement for virus protection. But, if you do pass e-mails and files between windows and other systems to protect THEM you should run some form of virus detection/protection.. Clam av is one I am aware of as highly recommended.

the above said... I have been running Ubuntu's for years with out the same and have never experienced any problems// My LAN is closed to the outside world! and I am  aware of what I download from the net and have installed on my systems//

In the event you employ some from of ssh and other forms of traffic/// The firewall is recommended (ubuntu based iptables =>several front ends) 


[INDENT]my 2 cents worth <==BDQ
[/INDENT]

---

### Post by parcdulas on 2012-09-01
Many thanks!, I'll pursue those links and I think I'll try gufw for now and see how I get on. Thanks again.

---

### Post by 3rdalbum on 2012-09-01
> **parcdulas said:**
> Many thanks!, I'll pursue those links and I think I'll try gufw for now and see how I get on. Thanks again.

On Windows, you need a firewall because components (services) of Windows actually listen for incoming connections. A remote attacker can connect to those services. A firewall stops the connections from going through.

On Ubuntu, by default, no services listen for incoming connections. If an attacker tried to connect, they simply wouldn't find anything to connect to. Therefore, a firewall won't make you safer.

I wouldn't bother too much about the personal firewall; just use Ubuntu. It's designed to be secure out-of-the-box so you don't have to worry about all that stuff.

---

### Post by tienlbhoc on 2012-09-01
I think don't need but if you are careful, you can use some free app.

---

### Post by coldcritter64 on 2012-09-01
From the wiki,

> Firewall There  is a lot of existing information about firewalls - along with a  long-term raging debate on the need of a firewall on Ubuntu. ** We  recommend you enable it because you have ports open if you are reading  this page**. Traffic can go in and out of that port unhindered without a  firewall. Malicious programs can open arbitrary ports unless you have a  firewall to prevent that. A NAT router can add a layer of protection,  but it will not protect you in lieu of a firewall. [This additional guide]("http://ubuntuforums.org/showthread.php?t=1871177") will provide more information.  
 
Use your firewall PROPERLY.  Don't set it and forget it, learn how it works, set decent rules.[Here]("http://ubuntuforums.org/showthread.php?t=1876124")  is a tutorial showing how to enable a firewall in Ubuntu. However,  adding port numbers can feel confusing. It if helps, think of it this  way - currently you're reading this guide because you accessed a webpage  hosted by wiki.ubuntu.com. To make the connection (and therefore to see  the content) you have to connect your browser to that website by  accessing Port 80. Another example is when you pick up your email. Your  computer makes a connection to your mail server on Port 110. The other  port numbers that you add provide similar functions.and

> 
[LIST]
[*]**Myth**: I don't need a firewall because Ubuntu has no open ports by default.
[*]**Reality**:  **This is a matter of risk tolerance**. Added protection, particularly that  which takes only a few minutes to set up, is always worth it. Firewalls  are discussed in more depth later in this document.
[/LIST]
Bolding for emphasis by me, personally I am not using a firewall on my desktop being behind 2 router firewalls, though doing that even carries a small risk (I tolerate that for convenience). In your situation OP your install is directly connected and not behind any routers with a dongle, so your risk factor is increased imo. Cheers.

---

### Post by Segofam on 2012-09-01
I have been using Ubuntu as my main OS for a few years, without Firewalls or Antivirus protection, and have not had any REAL issues.
In fact, I purposely sourced out some Viruses that are designed to effect Linux OS's, and found that at most, all I had to do was reload a program.
I have just updated to Precise Pangolian, and I have faith that, after a few tweak and preference settings be made, I will enjoy the freedom that I have found with Ubuntu :)

---

### Post by priority on 2012-09-01
i thought linux doesnt have any virus :/ am i wrong ?

---

### Post by TheFu on 2012-09-01
There are viruses for every OS.  If your PC happens to be at the wrong place and the wrong time with the wrong config, then you can be hacked.

There are linux worms, spyware, and other non-virus nasties .... with any complex system, there will be accidental *back doors* and it just takes 1 tiny config mistake to let someone have access on any platform.  I've been hit with an "internet worm" before.  It broke into my machine, changed the root password and deleted my user account.  Was that a virus?

Many java and Adobe Acrobat and Javascript  vulnerabilities impact all operating systems.

Linux is safer, but only because we aren't as large a group to make attacks useful.  I honestly do not believe that the OS is any safer because of some magical underlying design choice.

Google "script kiddie" for more.

Oh and yes, we all need a software firewall.  Home router firewalls allow more traffic than you want.  There are techniques to trick the firewall into opening a port when you don't intend for that connection to happen. The router is fooled, but the firewall on Linux is not - provided it is enabled.

**ufw** is fine. **Firestarter** is more like what someone coming from Windows expects. Both are just interfaces over the same kernel module - iptables. iptables does the work, but using it directly is cumbersome.

---

### Post by coldcritter64 on 2012-09-01
> **priority said:**
> i thought linux doesnt have any virus :/ am i wrong ?
Not entirely correct, there are no known viruses "in the wild" that can affect linux.
But there are viruses for linux, see [[COLOR=Blue]--here--[/COLOR]]("http://en.wikipedia.org/wiki/Linux_malware") for a partial list - section 3.2.

---

