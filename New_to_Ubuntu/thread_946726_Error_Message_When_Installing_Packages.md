---
title: "Error Message When Installing Packages"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by wmichaelb on 2008-10-13
Hi, I got my Hardy machine running, and successfully downloaded many software packages. However, when I tried to install Streamtuner and XMMS, I got the following error message:

E: python-pyexiv2: subprocess post-installation script returned error exit status 1 
E: phatch: dependency problems - leaving unconfigured 

Has anyone else had this problem with Streamtuner/XMMS or other packages that they've tried to install? Have you found a solution?

Thanks!

---

### Post by JeeZiTsDave on 2008-10-13
I had the same exact problem.  Here was my solution:

First: Go to Applications>Accessories>Terminal

Second: Run The Command
```
sudo apt-get remove python-pyexiv2
```

Third: After that command has been properly executed, Run:
```
sudo apt-get install python-pyexiv2
```

Done!

Then try to reinstall the applications that you were trying to install previously.

---

### Post by wmichaelb on 2008-10-13
Thanks, JeezItsDave; I uninstalled and reinstalled Streamtuner without incident. But when I tried to run it, I got:

Failed to execute child process "xmms" (no such file or directory).

I couldn't find XMMS in the Ubuntu directory, so I tried to install it from the Synaptic Package Manager, only to find out that it had already been installed (although there is no icon in the list of Ubuntu apps). So I tried installing all the plug-ins that are available for XMMS. The install went ok, but I still get the above message. ????!!?!?!?!

Does anyone have a next suggestion? Thanks in advance.
 :confused:

---

### Post by JeeZiTsDave on 2008-10-13
XMMS is just codecs, isn't it?

I would just go and install VLC or MPlayer.  That's was I use and they are great.

---

### Post by wmichaelb on 2008-10-14
Basically, I do use the MPlayer package for the occasional video; but I spend much more time listening to internet radio. Amorak plays these streams well, but keeps putting up this annoying banner with information about the currently playing song. Streamtuner doesn't do this, and only seems to work with XMMS. In addition, Amorak doesn't sort by genre. One of the joys of open software is that there's something for every taste, and I'd really rather get Streamtuner working. 

Thanks, but does anyone else have a suggestion?

---

### Post by SteveNorman on 2008-10-14
I would try and remove everything that is not working and reinstall all of it again. Do a thorough search for all the components

```
sudo updatedb
locate streamtuner
```

remove everything by hand then reinstall

If this doesnt work you may need to do the same with xmms

---

