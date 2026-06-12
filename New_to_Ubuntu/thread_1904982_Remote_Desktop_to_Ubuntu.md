---
title: "Remote Desktop to Ubuntu"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by 8kjelbr on 2012-01-05
Hi there,

I am new to Ubuntu, and so far - really enjoying it.
I managed to install Ubuntu 11.10.

My background is, like others, Windows and Server environments, but I've decided to start using Ubuntu/Linux for other applications that I need, e.g. Nagios, NTOP - all of which I have installed.

I have two questions though that I'd like some help on.

1) Is it possible to remote to an Ubuntu box similar to what I would use Remote Desktop to log onto a Windows box.

2) If there is a service on Ubuntu that I want to start, and I am using a Windows machine, because I cannot access the Ubuntu box physically, how do I do this? (what tools do I use?)

Thanks so much,

---

### Post by lechien73 on 2012-01-05
Hi and welcome to the forums,

In answer to your first question, for servers on the same network, I use X11VNC Server, which can be installed through the Ubuntu Software Centre, or apt-get. All you need on your Windows box is a freely available VNC viewer.

With regard to the second - I would probably use SSH, so install OpenSSH server on your Ubuntu box:

```
sudo apt-get install openssh-server
```

You can then get a remote terminal window (command prompt on your Ubuntu server) from a Windows box by using an ssh client, such as putty.

---

### Post by bluexrider on 2012-01-05
> **8kjelbr said:**
> Hi there,

I am new to Ubuntu, and so far - really enjoying it.
I managed to install Ubuntu 11.10.

My background is, like others, Windows and Server environments, but I've decided to start using Ubuntu/Linux for other applications that I need, e.g. Nagios, NTOP - all of which I have installed.

I have two questions though that I'd like some help on.

1) Is it possible to remote to an Ubuntu box similar to what I would use Remote Desktop to log onto a Windows box.

2) If there is a service on Ubuntu that I want to start, and I am using a Windows machine, because I cannot access the Ubuntu box physically, how do I do this? (what tools do I use?)

Thanks so much,
1. You are going to want to install a program on the Windows machine such as TightVNC to view the Ubuntu machine.
2.  In the Remote Desktop Preferences window,  you can configure the remote desktop connection. If you want others to  just see your desktop, but not be able to make changes, enable Allow other users to view your desktop only.

---

### Post by cbanakis on 2012-01-05
Not sure about connecting to Ubuntu, 
But I can easy remote to windows using "Remmina"  (Found In The Software Center)

If you look in your system preferences, there is a tool there for setting your computer up to accept remote connections, so you can obviously do it, but I'm not sure what windows remote desktop clients are capable of connecting to Ubuntu.

Judging my how easy it was for me to remote to a windows server using ubuntu, I assume it will just work, without issues.

---

### Post by 8kjelbr on 2012-01-05
Thank you everyone for your help, really appreciate it.

Matt, lechien73

You mentioned using putty in Windows to connect to it.
What sort of command do I enter in putty to remote start a service on my Ubuntu box?

---

### Post by lechien73 on 2012-01-06
> **8kjelbr said:**
> Thank you everyone for your help, really appreciate it.

Matt, lechien73

You mentioned using putty in Windows to connect to it.
What sort of command do I enter in putty to remote start a service on my Ubuntu box?

Using putty, you can ssh into your Ubuntu box and then you'll have a command prompt, so you can stop and start services from there. This looks just the same as if you'd opened a terminal window on your Ubuntu box (black screen, $ prompt and flashing cursor).

If you're looking for something a bit more point-and-click, then you could install ebox (now renamed to Zentyal), which allows you to manage the server through a web interface.

Documentation about ebox on Ubuntu is here: [https://help.ubuntu.com/community/eBox](https://help.ubuntu.com/community/eBox)

And there are some screenshots to give you an idea of the interface here: [http://doc.zentyal.org/en/firststeps.html](http://doc.zentyal.org/en/firststeps.html)

---

### Post by abirkoff on 2012-12-17
Hi all,
I'm dealing with similar problem regarding migration from windows and using a Remote Desktop feature and I still don't happy with any remote session functionality in Ubuntu (I'm using 12.04 LTS).

I have one machine, which I'm using both remotely and locally. I have following requirement which are offered by rdp in windows.

1. I usually have opened many applications, then I lock the station, go home, connect to station remotely and I need to continue with all opened apps.
2. I need to have the station still locked to prevent physical access of someone else.
3. Suppose the station is running, but no user has opened any session yet (login screen). I need to connect the station remotely and open new session, then lock it and access this session locally again.

This is default functionality which is offered by Windows RDP. Does exist any equivalent in Ubuntu? I tried vnc, xrdp but it covers only part of the functionality I need.

Any advice?
Thank you.

---

### Post by ags0082 on 2013-01-01
[QUOTE=abirkoff]
Hi all,
I'm dealing with similar problem regarding migration from windows and  using a Remote Desktop feature and I still don't happy with any remote  session functionality in Ubuntu (I'm using 12.04 LTS).

I have one machine, which I'm using both remotely and locally. I have following requirement which are offered by rdp in windows.

1. I usually have opened many applications, then I lock the station, go  home, connect to station remotely and I need to continue with all opened  apps.
2. I need to have the station still locked to prevent physical access of someone else.
3. Suppose the station is running, but no user has opened any session  yet (login screen). I need to connect the station remotely and open new  session, then lock it and access this session locally again.

This is default functionality which is offered by Windows RDP. Does  exist any equivalent in Ubuntu? I tried vnc, xrdp but it covers only  part of the functionality I need.

Any advice?
Thank you.     [/QUOTE]

I'm in the same boat and would love to see some development towards a better remote desktop solution.

-AGS

---

### Post by ivicks on 2013-01-01
Not sure if anyone is still looking at this thread. It sounds like your setting up a network monitoring server and thought I would share a link with some guides on nagios [http://www.thegeekstuff.com/tag/nagios/](http://www.thegeekstuff.com/tag/nagios/) They are kind of dated but they will give a good idea of what you can do.

---

### Post by Fahim Abdun-Nur on 2013-01-02
There's another thread referring to NoMachine NX [http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

---

### Post by CharlesA on 2013-01-02
> **Fahim Abdun-Nur said:**
> There's another thread referring to NoMachine NX [http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)
I use NX myself, and while it is similar to Windows Remote Desktop, it isn't exactly the same.

It gets the job done better than VNC, though.

---

### Post by ags0082 on 2013-01-02
> **CharlesA said:**
> I use NX myself, and while it is similar to Windows Remote Desktop, it isn't exactly the same.

It gets the job done better than VNC, though.

Agreed.

-AGS

---

### Post by vv1984 on 2013-01-03
> **ags0082 said:**
> Agreed.

-AGS

It can be used in full-screen mode too?
I'm experiencing some issues with VNC Clients (for example, arrow keys are not working properly in terminal window on X.. so i can't access commands history.. )

Thank you

---

### Post by CharlesA on 2013-01-03
> **vv1984 said:**
> It can be used in full-screen mode too?
I'm experiencing some issues with VNC Clients (for example, arrow keys are not working properly in terminal window on X.. so i can't access commands history.. )

Thank you

Not from what I have seen. You can open it as a maximized window, though.

---

### Post by ags0082 on 2013-01-03
> **vv1984 said:**
> It can be used in full-screen mode too?
I'm experiencing some issues with VNC Clients (for example, arrow keys are not working properly in terminal window on X.. so i can't access commands history.. )

Thank you

I'm using the NoMachine client on Windows 7 to connect to my Ubuntu box and it does have a full-screen mode.  No issues with the arrow keys either.

-AGS

---

### Post by RottNKorpse on 2013-01-03
I think the best method of Remote Desktop is to use TeamViewer...I know it is not a genuine Linux app but it is cross-platform compatible with almost any platform even Android. It's FREE. It simply works.

TeamViewer is technically a Windows app ported to Linux via a custom embedded WINE but it works and works well so that is what is important.

If you are looking for Open Source only or something with VNC or SSH then, yea nevermind. :)

---

### Post by ags0082 on 2013-01-04
> **RottNKorpse said:**
> I think the best method of Remote Desktop is to use TeamViewer...I know it is not a genuine Linux app but it is cross-platform compatible with almost any platform even Android. It's FREE. It simply works.

TeamViewer is technically a Windows app ported to Linux via a custom embedded WINE but it works and works well so that is what is important.

If you are looking for Open Source only or something with VNC or SSH then, yea nevermind. :)

Unfortunately while I was able to use/connect with TeamViewer, it left the same issues & concerns I had with VNC and NoMachine.  Several of the options in the Linux port didn't appear to work (e.g. show blank screen) which is to be expected if the original features are dependent on Windows functionality.

-AGS

---

### Post by mysteriousdarren on 2013-01-11
I've always had good luck with Teamviewer and have been a proud supporter since first dipping my foot in it. Other remote desktop option have not worked as well as for me(VNC, TightVNC) and others.

---

