---
title: "[SOLVED] flash player - help a n00b!!"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by ykewea on 2008-10-27
I installed the flash player 10 for linux following the instructions from adobe and I get a confirmation message, but videos still won't play.
any ideas??
please explain as if I were a very stupid little kid, LOL.
thanks.

---

### Post by kansasnoob on 2008-10-27
What version of Ubuntu are you using?

8.04? Ubuntu? Kubuntu? etc.

---

### Post by Keen101 on 2008-10-27
where did you install to?

It usually needs to go in usr/lib/firefox-3.0.2 or whatever version firefox you are running. Just browse using nautilus, and find the folder first.

on my system it is /usr/lib/firefox-3.0.3

(**if using the tar install file**)


The easy way is to use the repository. 

```
sudo apt-get install flasplugin-nonfree
```

your not using the 64bit version are you?

---

### Post by redbob on 2008-10-27
Hi, ykewea...
If you have installed a *.deb Adobe Flash player, it shoud be the reason of the problem. The best option to do is *.tar.gz. Follow these:

a) Download the tar.gz version:
> [http://www.adobe.com/go/getflashplayer](http://www.adobe.com/go/getflashplayer)

b) Unpack it:
> tar zvxf install_flash_player_10_linux.tar.gz

c) open the directory within you unpacked your download and execute the following command:
> sudo ./flashplayer-installer

You must execute it by sudo, so your instalation will work for all users you have in your computer.

---

### Post by SunnyRabbiera on 2008-10-27
Yeh sometimes the .deb installer doesnt work, especially with 64 bit systems

---

### Post by ykewea on 2008-10-27
> **kansasnoob said:**
> What version of Ubuntu are you using?

8.04? Ubuntu? Kubuntu? etc.

yes, ubuntu 8.04

---

### Post by ykewea on 2008-10-27
> **Keen101 said:**
> where did you install to?

It usually needs to go in usr/lib/firefox-3.0.2 or whatever version firefox you are running. Just browse using nautilus, and find the folder first.

on my system it is /usr/lib/firefox-3.0.3

(**if using the tar install file**)


The easy way is to use the repository. 

```
sudo apt-get install flasplugin-nonfree
```

your not using the 64bit version are you?

not sure where i installed it. i'm still trying.
i'm gonna try the repository.

and no, as far as i know it's the 32 bit.

---

### Post by ykewea on 2008-10-27
> **redbob said:**
> Hi, ykewea...
If you have installed a *.deb Adobe Flash player, it shoud be the reason of the problem. The best option to do is *.tar.gz. Follow these:

a) Download the tar.gz version:


b) Unpack it:


c) open the directory within you unpacked your download and execute the following command:


You must execute it by sudo, so your instalation will work for all users you have in your computer.

yes, i tried the deb.
still trying. i'll keep you guys posted, thanks for the help.

---

### Post by ykewea on 2008-10-27
how do I turn on java script? or how do I know if it's turned on?

---

### Post by kansasnoob on 2008-10-27
Well, you also need some java, gstreamer, etc so do this at the terminal:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Then:

```
sudo apt-get remove --purge flashplugin-nonfree
```

Then:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

That last one may take a minute to run! If it shows errors that's OK! If it asks you any questions (y-n) just say Y.

Then reinstall the ,deb from here:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Then restart Firefox with > mouse point to File > click Quit and when you restart firefox you should have Flash.

Occasionally I've had to reboot.

---

### Post by redbob on 2008-10-27
Normally, Some Internet Banking sites use Java code.
Another way to know if Java is working is by downloading and installing Frostwire. It runs by Java.

---

### Post by ykewea on 2008-10-27
never mind guys... I got it.
I ran the update and it fixed itself, LOL.
thanks for your help.

---

### Post by selehka on 2008-10-27
Ok - as someone who has constantly lurked in the forums and lived in the Search box, I ran into the same problem.

What I found worked to get it all work was add Open Office package from the Synaptic Package Manager.  Since I wasn't interested in Office (yah - I'm thinking of MS Office programs) I didn't add/enable it.  When I did - YouTube, Bill Moyers Journal, Frontline etc all became enabled with video and sound.  So - a duh moment for me. o.0

Now lurking to solve my next problem - which I'm sure is going to be another 'duh' moment.

---

