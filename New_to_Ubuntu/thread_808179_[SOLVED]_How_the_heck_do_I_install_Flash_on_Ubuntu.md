---
title: "[SOLVED] How the heck do I install Flash on Ubuntu 8.04 (Hardy Heron)??!"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-26
Went to youtube.com and went to see a video. It says that either java is turned off (which isn't) or I don't have flash player. Went and got the file for Linux Adobe flash player. Got the tar.gz. version. Once I download the file I go to youtube again and it STILL says the same thing! check my desktop and im like...wtf? it's there on my desktop as a partially open box called! went to adobe.com/downloads and went to adobe flash player and went to installation instructions and i read the instruction but DIDNT understand em! HEEELP!

P.S. - The instructions i saw on adobe.com were as the following:


       1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by Joeb454 on 2008-05-26
Did you follow those instructions?

Edit:

My mistake! Didn't read the whole post :p

Right click the .tar.gz file, and choose extract here. Then open a terminal from Applications > Accessories > Terminal, and type ```
cd ~/Desktop
cd install_flash_player_9_linux
./flashplayer-installer

```

Hope this helps :)

---

### Post by drs305 on 2008-05-26
If you are running 32-bit hardy, just install the restricted extras. That's all you should have to do to get flash working.
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by Joeb454 on 2008-05-26
> **drs305 said:**
> If you are running 32-bit hardy, just install the restricted extras. That's all you should have to do to get flash working.
```
sudo aptitude install ubuntu-restricted-extras
```

I think Ubuntu Restricted Extras is a little overkill just for Flash ;) And also you don't have to be running 32-bit to install that, I installed it on my 64 bit install :)

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-26
Hey dude, I'm eleven and I'm a red alert newbie on this kind of stuff...I couldnt even understand the last three ones! Anyway...there is a file called install_flash_player_9_linux.tar.gz.

The only problem...I don't even know how to navigate to the file or "unpack" which I have a nasty feeling I've already done it and is related to the file looking like an OPENED box(well, partialy) and so I need some help for every single step! Sorry for being such a pain!


Armageddon

---

### Post by philinux on 2008-05-26
Just double click it then select extract here.

---

### Post by mbaker824 on 2008-05-26
> **@_R_|\/|_@_G_E_|)_|)_0|\| said:**
> went to adobe.com/downloads and went to adobe flash player and went to installation instructions and i read the instruction but DIDNT understand em! HEEELP!

P.S. - The instructions i saw on adobe.com were as the following:


       1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.


Luckily, it's easier than that.  You have two options - you can install gnash (a free flash player, which might not be completely compatible in all cases), or the read Adobe Flash.  I'm assuming you want the latter, so do this in a terminal window:

```
sudo apt-get install flashplugin-nonfree
```

If you prefer, you can search for it in Synaptic and install it that way. 

This also assumes you have the multiverse repository enabled - to check, run Synaptic and go to Settings->Repositories.  On the Ubuntu Software tab, make sure "Software restricted by copyright or legal issues (multiverse)" is checked.  If not, check it, click Close, then click the Reload button in the main Synaptic window.

Good luck,
Mark

---

### Post by Joeb454 on 2008-05-26
Did you try the option in my 2nd post?

Also from a terminal you could run ```
sudo apt-get install flashplugin-nonfree
``` though personally I do the method I 1st posted :)

---

### Post by drs305 on 2008-05-26
> **Joeb454 said:**
> I think Ubuntu Restricted Extras is a little overkill just for Flash ;) And also you don't have to be running 32-bit to install that, I installed it on my 64 bit install :)

You are correct. I have the restricted-extras on my 64-bit machine but didn't remember that the flash problem in 64-bit was solved in hardy. As for overkill, perhaps so, but it is a lot easier than compiling Adobe. Sometimes I'm just lazy ...  ;-)

---

### Post by Joeb454 on 2008-05-26
True - Ubuntu-restricted-extras now uses nspluginwrapper for the 64-bit deb's :)

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-26
Thanks for the help guys!:):)My flash is up and running! I tried all of your suggestions and its working now! Again, thanks a lot!:KS

---

### Post by unclejac on 2008-05-28
While running 7.10 64 bit,  

If you get the message:

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

What is the cure for that ?

---

### Post by Joeb454 on 2008-05-28
You need to install nspluginwrapper. There's a sticky in the x86_64 section of the forum :)

Here's the thread: [Flash on AMD64 Machines]("http://ubuntuforums.org/showthread.php?t=772490")

---

### Post by unclejac on 2008-05-28
cheers joe!! That did the trick. . . :)

---

### Post by badgethefarmer on 2008-06-08
> **Joeb454 said:**
> Did you follow those instructions?

Edit:

My mistake! Didn't read the whole post :p

Right click the .tar.gz file, and choose extract here. Then open a terminal from Applications > Accessories > Terminal, and type ```
cd ~/Desktop
cd install_flash_player_9_linux
./flashplayer-installer

```

Hope this helps :)

this one helped bigtime.
thanks

---

