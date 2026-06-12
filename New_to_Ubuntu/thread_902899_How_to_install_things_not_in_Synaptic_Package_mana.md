---
title: "How to install things not in Synaptic Package manager?"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by tc101 on 2008-08-27
I have only installed stuff using Synaptic Package manager.  There are manay things that just let you download them from the website, but are not in Synaptic.  Are there instructions somewhere that tell you how to install these once you have downloaded them?

---

### Post by RATM_Owns on 2008-08-27
If it ends in .deb, double click it. Obvious from there on.

If it ends in .tar.gz, extract the archive, cd into where you extracted it, type "./configure" If there isn't one, it's fine. Then type "make" and "sudo make install"

---

### Post by tuxxy on 2008-08-27
Yes you can manually install them but the method would depend on the file types you are reffering to, heres a good guide on installing software in ubuntu

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by AxiomShell on 2008-08-27
> **tc101 said:**
> I have only installed stuff using Synaptic Package manager.  There are manay things that just let you download them from the website, but are not in Synaptic.  Are there instructions somewhere that tell you how to install these once you have downloaded them?

There is no *universal* way of installing programs.
It is always advised that you read the installation documentation for what you plan on installing. Search the website for instructions, or typically files named *INSTALL* or *README*.
If you don't find what you need on synaptic, IMHO you should at least find it as a debian package.
If you do, and assuming you don't have depencies problems, you simply install it by running

```
sudo dpkg -i package_name.deb
```

---

### Post by Lexicon101 on 2008-08-27
same as .deb with .rpm packages.
Also, some things use automake, which you can install (almost ironically) via synaptic.. Some things (blender being one) require scons.. for each of these, I believe you just type the commands after cd-ing to the directory of the sources..
(which just involves something like "cd /media/disk/Linprogs/aMSN/" or something..)

---

### Post by tc101 on 2008-09-08
I want to install Adobe Flash player.  This is where I am downloading it:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P5_Language=English](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P5_Language=English)

They have 3 formats to download;  .tar.gz  , .rpm , and .YUM

Is there any reason to use one over the other?  I read the instructions at  [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

It calls these last resorts.  Which would you use?

---

### Post by deb_untu on 2008-09-08
> **tc101 said:**
> I want to install Adobe Flash player.  This is where I am downloading it:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P5_Language=English](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P5_Language=English)

They have 3 formats to download;  .tar.gz  , .rpm , and .YUM

Is there any reason to use one over the other?  I read the instructions at  [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

It calls these last resorts.  Which would you use?


since .deb is not available use tar.gz & follow the instructions.

       1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage(tar -xvzf *filename)* the file. A directory called install_flash_player_9_linux will be created.
       4. In terminal, navigate to this directory and type _sh flashplayer-installer_ to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.
                                 OR
[http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

---

### Post by bumanie on 2008-09-08
Out of those three options the only one that will work with ubuntu is the .tar.gz .rpm and .yum work with non-debian based linux distro's.

---

### Post by gjoellee on 2008-09-08
> **tc101 said:**
> I want to install Adobe Flash player.  This is where I am downloading it:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P5_Language=English](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P5_Language=English)

They have 3 formats to download;  .tar.gz  , .rpm , and .YUM

Is there any reason to use one over the other?  I read the instructions at  [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

It calls these last resorts.  Which would you use?

I have a .deb on my website:) 
check it out here: [http://www.kshoster.net/?c=downloads&h=deb](http://www.kshoster.net/?c=downloads&h=deb)

---

