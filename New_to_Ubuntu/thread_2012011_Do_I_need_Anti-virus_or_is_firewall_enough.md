---
title: "Do I need Anti-virus or is firewall enough?"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by Sarys on 2012-06-28
So do I need anti-virus program if I dual-boot Ubuntu? Or is firewall enough to keep my linux safe? I know there might be threads about this but I'm not used to navigate in forums to find them so sorry about that.

---

### Post by Shadius on 2012-06-28
I'd say, for Linux, a firewall is good enough as I don't think there are any viruses for Linux or the chances of acquiring one are slim to none. As for Windows, if that's what you're dual-booting, an antivirus is definitely needed as well as a firewall! That being said, you can never be too careful with things that are on the internet though. 

Here's some information about Linux's firewall, UFW (Uncomplicated Firewall): [UFW]("https://help.ubuntu.com/community/UFW"). To enable it, just run:
```
sudo ufw enable
```

---

### Post by Lemuriano on 2012-06-28
Hi,

I have been using Gnu/Linux for a few years just with my firewall and never encounter a virus. Gnu/Linux is pretty save on that respect. If you want more security my suggestion is to just open the ports you need and close the rest, using perhaps ufw and or gufw. 
(That being said most users are ok by just enable ufw.)

Regards.

---

### Post by Shadius on 2012-06-28
You should also take a look at the stickies in the Security Discussions section. [Click Here]("http://ubuntuforums.org/forumdisplay.php?f=338")

---

### Post by Sarys on 2012-06-28
> **Shadius said:**
> I'd say, for Linux, a firewall is good enough as I don't think there are any viruses for Linux or the chances of acquiring one are slim to none. As for Windows, if that's what you're dual-booting, an antivirus is definitely needed as well as a firewall! That being said, you can never be too careful with things that are on the internet though. 

Here's some information about Linux's firewall, UFW (Uncomplicated Firewall): [UFW]("https://help.ubuntu.com/community/UFW"). To enable it, just run:
```
sudo ufw enable
```

I have win7 and I'd like to dual-boot Ubuntu. But you mean that with that code I get firewall? Where do I input that code anyway I know nothing about the code side of linux.

EDIT: I don't know anything about those ports either.

---

### Post by Shadius on 2012-06-28
> **Sarys said:**
> I have win7 and I'd like to dual-boot Ubuntu. But you mean that with that code I get firewall? Where do I input that code anyway I know nothing about the code side of linux.

Yes, with that code, you enable Linux's firewall from within Ubuntu. You input that code from the Terminal. A keyboard shortcut for the Terminal is *Ctrl+Alt+T*, then you simply input that code and press *Enter*. Here's a screenshot of enabling UFW. Here's some documentation on using the Terminal as well. [Using The Terminal]("https://help.ubuntu.com/community/UsingTheTerminal/"). The Terminal can become your best friend! Get familiar with it.

---

### Post by Curtis6767 on 2012-06-28
> **Sarys said:**
> So do I need anti-virus program if I dual-boot Ubuntu? Or is firewall enough to keep my linux safe? I know there might be threads about this but I'm not used to navigate in forums to find them so sorry about that.

Ubuntu Anti-Virus: [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by Sarys on 2012-06-28
> **Shadius said:**
> Yes, with that code, you enable Linux's firewall from within Ubuntu. You input that code from the Terminal. A keyboard shortcut for the Terminal is *Ctrl+Alt+T*, then you simply input that code and press *Enter*. Here's a screenshot of enabling UFW. Here's some documentation on using the Terminal as well. [Using The Terminal]("https://help.ubuntu.com/community/UsingTheTerminal/"). The Terminal can become your best friend! Get familiar with it.

Ok but what are those ports anyway?

---

### Post by Lemuriano on 2012-06-28
Remember that when you input the code, the system will ask for your password, after that just hit enter and your done.

Regards.

---

### Post by kaffekanne on 2012-06-28
> **Shadius said:**
> I'd say, for Linux, a firewall is good enough as I don't think there are any viruses for Linux or the chances of acquiring one are slim to none. As for Windows, if that's what you're dual-booting, an antivirus is definitely needed as well as a firewall! That being said, you can never be too careful with things that are on the internet though. 
 
Here's some information about Linux's firewall, UFW (Uncomplicated Firewall): [UFW]("https://help.ubuntu.com/community/UFW"). To enable it, just run:
```
sudo ufw enable
```
Neat!
 
EDIT:
Yay first bean

---

### Post by Lemuriano on 2012-06-28
This thread will help you to setup your firewall with more detail if you choose that and will also help you understand about ports. But if you want to keep things simple but secure at the same time just enable ufw.

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

Regards.

---

### Post by Shadius on 2012-06-28
> **kaffekanne said:**
> Neat!
 
EDIT:
Yay first bean

:lolflag: Congratulations! 

I've updated the screenshot to show that you will need to input your  password after inputting the code
```
sudo ufw enable
```
I don't know exactly what ports are open. Maybe Lemuriano can shed some light on that part of it.

---

### Post by Sarys on 2012-06-28
I knew linux is hard but this hard? Geez......maybe I just should stick with my windows.

---

### Post by Shadius on 2012-06-28
> **Lemuriano said:**
> This thread will help you to setup your firewall with more detail if you choose that and will also help you understand about ports. But if you want to keep things simple but secure at the same time just enable ufw.

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

Regars.

Very good thread! I was just about to mention the GUI version of UFW, which is GUFW. Sarys, if you're not comfortable with the command-line way of doing things yet, I definitely advise you to read that thread and install GUFW.

---

### Post by Sarys on 2012-06-28
> **Shadius said:**
> Very good thread! I was just about to mention the GUI version of UFW, which is GUFW. Sarys, if you're not comfortable with the command-line way of doing things yet, I definitely advise you to read that thread and install GUFW.

Hmm. Well I guess I have to check that out but I still need to learn the command-line sooner or laiter anyway.

---

### Post by Shadius on 2012-06-28
> **Sarys said:**
> I knew linux is hard but this hard? Geez......maybe I just should stick with my windows.

It's not hard at all. Just different ways of doing things. Maybe I'm making it seem hard with all my talk of command-line interface. Sorry about that, but Linux can be ***very*** easy, in my opinion. Since you're more comfortable with the GUI-method of things, I'll stick to that. I assume you know how to use the Ubuntu Software Center to install applications?

---

### Post by Sarys on 2012-06-28
> **Shadius said:**
> It's not hard at all. Just different ways of doing things. Maybe I'm making it seem hard with all my talk of command-line interface. Sorry about that, but Linux can be ***very*** easy, in my opinion. Since you're more comfortable with the GUI-method of things, I'll stick to that. I assume you know how to use the Ubuntu Software Center to install applications?

Yeah I know how the Software Center works. BTW what's GUI?

---

### Post by haqking on 2012-06-28
> **Sarys said:**
> I knew linux is hard but this hard? Geez......maybe I just should stick with my windows.

It is not hard, it is unfamiliar, there is a difference.

Feel free to use whatever you like, use what works for you or what you can make work.

Ports are ports, firewalls are firewalls, they are platform agnostic.

Whatever OS you choose to use, to make steps towards a secure system you need to control outgoing and incoming traffic using a firewall and controlling port activity, it is not unique to any OS.

Read the links and security stickies.

I suggest this for a beginner [ Basic Security Wiki]("https://wiki.ubuntu.com/BasicSecurity")

Peace

---

### Post by haqking on 2012-06-28
> **Sarys said:**
> Yeah I know how the Software Center works. BTW what's GUI?

Graphical User Interface (the point and click stuff with a mouse that looks pretty) as oppose to typing something into a terminal (similar to windows command prompt)

---

### Post by Sarys on 2012-06-28
> **haqking said:**
> Graphical User Interface (the point and click stuff with a mouse that looks pretty) as oppose to typing something into a terminal (similar to windows command prompt)

So terminal is bit like DOS? I know it's more like windows command prompt like you said but still.

---

### Post by haqking on 2012-06-28
> **Sarys said:**
> So terminal is bit like DOS? I know it's more like windows command prompt like you said but still.

Similar looking yes.

The command prompt in modern Windows is not DOS though.  In older windows versions it is the DOS prompt.

The terminal in Linux is how you would interact with it using text instead of funky graphics drivers and mouse clicks, however you can access the terminal in a window whilst running a GUI just like using the command prompt in windows (to try to explain it simply ;-)

Peace

---

### Post by Sarys on 2012-06-28
> **haqking said:**
> Similar looking yes.

The command prompt in modern Windows is not DOS though.  In older windows versions it is the DOS prompt.

The terminal in Linux is how you would interact with it using text instead of funky graphics drivers and mouse clicks, however you can access the terminal in a window whilst running a GUI just like using the command prompt in windows (to try to explain it simply ;-)

Peace

Oh I see

---

### Post by nipunshakya on 2012-06-28
i would like to add my opinion here too... 
until now, i honestly didn't know about starting the firewall until shadius shared to us... its not that i am careless regarding security.. its because i had no concerns of enabling it in my ubuntu coz I feel secured with ubuntu... it means that my system was(maybe ) running without any security !!! 
Till this time, i know that my ubuntu is safe... but with shadius's piece of info, i will enable my firewall too, but i don't think an antivirus is that necessary...

---

### Post by nipunshakya on 2012-06-28
> **Sarys said:**
> I knew linux is hard but this hard? Geez......maybe I just should stick with my windows.
  I used to think that way, and i would often be ON and OFF ubuntu with a gap on every release(6-months).. but slowly, from virtual box installation of ubuntu , to the dual boot and finally only ubuntu in my machine, here i am suggesting you not to feel hard to use ubuntu.... Terminal isn't that necessary for you to use ubuntu.... sometimes, when few things get screwed up, you might need terminal.. but in most of the cases, GUI is good...
Linux assumes that you know what u are doing in your machine, and to do so, you might need terminal... but not all the time... Just don't step back when it comes to ubuntu.... its great and im loving it... Hope u do too....


Happy Linuxing):P

---

### Post by Sarys on 2012-06-28
> **WinuxUser said:**
> i would like to add my opinion here too... 
until now, i honestly didn't know about starting the firewall until shadius shared to us... its not that i am careless regarding security.. its because i had no concerns of enabling it in my ubuntu coz I feel secured with ubuntu... it means that my system was(maybe ) running without any security !!! 
Till this time, i know that my ubuntu is safe... but with shadius's piece of info, i will enable my firewall too, but i don't think an antivirus is that necessary...

Yeah that's what I've heard as well. I read some where that "normal user" only needs firewall and "business user" might want to use anti-virus as well. (or something like that)

---

### Post by nipunshakya on 2012-06-28
an example on where u might need antivirus for ubuntu:
U plug in a USB in an infected Windows installed machine... you get virus.
 Now if you bring it to ubuntu and exchange files to and from the USB, it won't cause any harm... coz u won't know if its a virus in there or not..
 But if u plug in the USB to other person's drive who has windows, he/she might get their machine affected unknowingly...

---

### Post by haqking on 2012-06-28
> **Sarys said:**
> Yeah that's what I've heard as well. I read some where that "normal user" only needs firewall and "business user" might want to use anti-virus as well. (or something like that)

Again i refer you to the [Basic Security Wiki]("https://wiki.ubuntu.com/BasicSecurity")

Read this and all its links and you will be more informed.

Peace

---

### Post by Sarys on 2012-06-28
> **WinuxUser said:**
> an example on where u might need antivirus for ubuntu:
U plug in a USB in an infected Windows installed machine... you get virus.
 Now if you bring it to ubuntu and exchange files to and from the USB, it won't cause any harm... coz u won't know if its a virus in there or not..
 But if u plug in the USB to other person's drive who has windows, he/she might get their machine affected unknowingly...

Yeah so I don't get problems but other might.

---

### Post by uRock on 2012-06-28
I have not messed with any AVs on ubuntu in a while. I do not feel the need, as the only files I share with my Windows machines are file I created myself.

If you prefer not to use the command line to work with the firewall, then open Ubuntu Software Center and search for GUFW and install it. Once installed you will be able to use it to turn on/off the firewall as well as set up rules to block/allow traffic, though the default is perfect in most home user situations.

---

### Post by nipunshakya on 2012-06-28
> **Sarys said:**
> Yeah so I don't get problems but other might.

yes.. if u carry infected USB with u...:guitar:

---

