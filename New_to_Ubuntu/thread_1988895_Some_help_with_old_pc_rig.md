---
title: "Some help with old pc rig"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by timewyrm on 2012-05-28
Hi,

first of all, I'd like to be totally honest, and say that although I've now decided to go with ubuntu server, it wasn't primarily my first choice. A few years ago I used to have ubuntu on a laptop for my wife (so that she couldn't get any viruses, lol), but honestly it was a lot of hassle (compared to windows). For example, the laptop used to have problems connection to my home network, as I have my ssid hidden (windows on the laptop did not have this issue). Also, having to input my password every time I wanted to make a change was very annoying (yes, I know that this is a strength that makes the system more secure!). I also wasn't (and still am not) very adept at using the cli. I can do all the basic stuff via cli, but thats about it.


Anyway fast forward to today. I've got an old pc lying around (q660, 4gb ram, ati 4850, 1tb hdd), and I decided I wanted to use it as a learning tool and as a development/testing server.

The approach I took at the beginning was installing CentOS (as it seems to be one of the mostly widely used OS's for servers). I got stuck near the beginning, when deciding to install Chrome as a browser, because that has to be done via Yum (?) installler, and that requires some changes to me made to a few files, and I couldn't get that done, yadda yadda yadda. Anyway, I decided that if I was having such a hard time installing something simple a browser, I didnt stand a chance right now, and so I uninstalled it, and went to a trial version of Windows 2008 Server r2.

This brought it's own problems, as I couldn't even detect the old pc with my new pc. I thought connecting both to the same domain would help, but then all this technospeak about Active Directory and forests etc got me even more confused. Finally, I scrapped that to, and decided to try Lion. I managed to get it installed and running, but it has problems recognising my ati 4850 (apparently a very common problem with Mac OSX and the 4850). Everything's running fine, but I dont want the gpu only have working.

This has brought me to Ubuntu Server. I read an article recently that taled about how Weta rendered Avatar on a Ubuntu Server farm, and that led me to further research into the possibilities of an Ubuntu Server farm (obviously not at the same scale as Weta's, lol).


So, here I am, with a copy of Ubuntu Server on my usb stick, ready to install, but there are a few issues that I'd like info on first:

1. Somebody else advised me to go for a non server specific OS, and just use teamviewer to connect to the old pc. Is this really the easiest way to do that ?

2. Is there an idiot proof way to make sure that I can detect my old pc on the network (without having to fiddle with the ip address, subnet, dns settings etc (preferably)) ?

3. Any idea how I'd use my Ubuntu pc as a render node ? (e.g., would I just point to it in Blender for example and label it as a render node) ?

4. Is there any reason for me to go with the server edition over a desktop edition ? (I want to use it for web development, android app development (eventually), learning c++, Java , LAMP etc. Bascially, I want to take the load off my new pc.)

5. I want to split my 1tb into possibly 5 separate drives,

(1 ubuntu, one with an img backup of ubuntu; one with a virtual machine that I want to install via windows, so that I can have a vm version of Lion running (for ios app development); 1 to backup Lion, and 1 (ntfs) to store a copy of my Windows backup image) 

which I want to be able to access with my new pc, via my new pc. Will that be possible ?

6. Is there any way to automatically login to Ubuntu, so that the pc can be a headless unit ?

7. Is there anyway to disable the password popup window that pops up every time I want to do something ?


I'm sorry, I know that this is a long thread. I'd really appreciate any help that you could give me, thank you.

---

### Post by steeldriver on 2012-05-28
I'm a bit confused by your requirements so forgive me if I am misunderstanding

1. I see a lot of people use Teamviewer - however there is a native VNC server (x11vnc) which allows you to connect remotely from Windows (or other Linux boxes) using a regular VNC client (I use UltraVNC)

2. it depends what you mean by 'connect to' - modern Ubuntu distributions do a pretty good job of handling Windows shares out of the box. For remote desktop I just point my VNC client at the LAN IP of the remote box; I imagine Teamviewer will be just as simple. NFS is a little more complicated but there are folks on this board who can help you.

3. no idea

4. I don't actually know anything about the Server editions, but nothing you've mentioned stands out as something you couldn't do with a standard Desktop edition - I am running an essentially headless Xubuntu box (laptop with a broken screen) using the standard 11.10 install and it all works fine

5. yes, easiest way would be to select 'Do something else' (I think I'm remembering that right) when prompted during the install and manually partition however you want

6. for sure if you use x11vnc (and being linux there are likely other ways too)

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

7. or less controversially you could increase the timeout so it at least asks you less frequently

---

### Post by timewyrm on 2012-05-28
Hi steeldriver, thank you for your response.

In terms of requirements, I'm mainly looking at having a system which allows me to use it as both a rendering device, and as tool I can practice, learn on (I guess you could say it will be a sandox).

I'm just going to have a read about some of the suggestions you've made, and I'll get back to you!

---

### Post by timewyrm on 2012-05-28
So, I've been having a read about x11vnc, and it does sound like a possible alternative, although it may require some tweaking to make it as responsive as Teamviewer (from what I read). 

Referring to "connect to", I'd like (if possible) to have my Windows PC connect with my Ubuntu one in two ways: via vnc, and also I'd like to have the Ubuntu pc show up under "network" on Windows, so that I can make a shortcut to it, and link to it from applications.

Also, regarding the password, I would like to get rid of it competely. Saying that, is there any way to disable incoming connections to ubuntu, from the outside world, but allow connections from my home network ?

---

### Post by Avaritia on 2012-05-28
Just so you know the default server install doesnt come with a GUI (desktop enviroment or window manager), though a Windows Server core installation doesn't either since fancy graphics are not really needed on a server.

---

### Post by timewyrm on 2012-05-28
> **Avaritia said:**
> Just so you know the default server install doesnt come with a GUI (desktop enviroment or window manager), though a Windows Server core installation doesn't either since fancy graphics are not really needed on a server.

Yeah I know, but thanks for pointing that out. 

I installed the "desktop experience" on windows server, and was reading about upgrading ubuntu server via cli to make it more "desktop like".

---

### Post by Avaritia on 2012-05-28
Here is a guide my friend used before to set up a render farm: 
[http://blendingwithforbes.blogspot.co.uk/2010/03/blender-25-network-render.html](http://blendingwithforbes.blogspot.co.uk/2010/03/blender-25-network-render.html)

If you have a look at the blender forums some people have made scripts to help automate the process.

To make the server install more 'user friendly' you could install something lightweight like Openbox (always had soft spot for Openbox) or Enlightenment, stay away from things with fancy desktop effects if your doing a lot of graphics rendering, every cycle will count.

---

### Post by timewyrm on 2012-05-28
Thanks for all your advice Avaritia, it's really helpful!

---

### Post by timewyrm on 2012-05-28
Right, I'm having some problems.

I installed Ubuntu Server, and when it completed and rebooted, all I had was a black screen. I tried this 5 or 6 times and keep having the same problem. So. I tried installing Ubuntu, and I cant even get to the install screen. The disc runs, and all I see is an image of a keyboard and a person at the bottom of the screen for about 30 seconds, and then the screen goes completely black, and my monitor goes to sleep.

---

### Post by timewyrm on 2012-05-29
So, I managed to sort out the black screen problem with Ubuntu Server, but I don't think it's recognising my 4850, or my monitor. I keep getting out of range errors after Grub boots, and I'm not sure why.

Also, I tried burning another copy of Ubuntu desktop, and that didnt work either. I had a look at what's on the disc, and it has a file called wubi.exe. Is there a specific version of ubuntu desktop that's meant to be used on new installs ?

---

### Post by mastablasta on 2012-05-29
> **timewyrm said:**
>  
Also, I tried burning another copy of Ubuntu desktop, and that didnt work either. I had a look at what's on the disc, and it has a file called wubi.exe. Is there a specific version of ubuntu desktop that's meant to be used on new installs ?
 
no, wubi.exe is ment to try it out the OS by creationg a virtual file in windows. it install OS like a programme inside windows and can later be removed as any other programme.
 
did you check the md5sum of the downloaded iso? also you should be able to boto into live mode before install. does that work? additionally you may need to use nomodeset boot parameter (when grub loads i think it's F6 or something to select it).
 
edit: yup it's F6: [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
 
after install is done you might need to install proprietary drivers from AMD/ati to solve your graphics issues and that is it.
 
after install works you can install more stuff using software center or synaptic package manager. for server stuff a nice tool tasksel can be used. 
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)
 
otherwise i think apt-get (in Ubuntu) is similar to yum (used in red hat linux).

---

