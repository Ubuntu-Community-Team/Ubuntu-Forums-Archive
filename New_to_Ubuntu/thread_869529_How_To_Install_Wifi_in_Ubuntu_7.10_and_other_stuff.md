---
title: "How To Install Wifi in Ubuntu 7.10 and other stuff?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by mogui_666 on 2008-07-24
Hi,

I have recently got a Acer Aspire 2920Z. This laptop come with Windows Vista and I don't really like it, so I have install Ubuntu 7.10 into it and now I have encounter a few problems.

Below are the list of problems I am facing now. Please help as I dont even know how to install software or driver or anything in Ubuntu 7.10. I use to use Windows XP.

- How to I install wifi?
- my Blue Tooth on the laptop doesn't work.
- when i connect my laptop to the Internet via a Cat 5 cable, I realise that I can't watch Youtube and other Internet streaming video.

I have found a blog call [Spica]("http://spicifer.blogspot.com/2007/12/acer-aspire-2920z-and-ubuntu-710-gutsy.html") that teaches amateur like me to install stuff in Ubuntu. But i have no idea what the hell is the whole thing talking about.

Please help!!!!!

Thanks in advance=)

---

### Post by thschiavo on 2008-07-24
I have the same problem with blue tooth, but I can't help you. About Wifi, it should work when ubuntu is installed. Please, put here the output of "iwconfig".

About Youtube, you should try downloading flash. I have a Acer Aspire 4720 and I wasn't able to install anything but maromedia flash player, downloading from the site. If you want more help, I can post a more detailed "tutorial" on how install flash on Ubuntu.

Hope this help you.

---

### Post by Bucky Ball on 2008-07-24
For flash, open a terminal and ...

> cd /tmp
wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz)
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer

Just copy and paste the above, line by line obviously, not all at once. That should deal with the flash issue. Good luck.

---

### Post by thschiavo on 2008-07-24
... Yes, this is what I was talking about... and the only way I can see Youtube and flash stuff.

---

### Post by mogui_666 on 2008-07-24
> **thschiavo said:**
> Please, put here the output of "iwconfig"
Hope this help you.

where do i find the "iwconfig"?

once i can get into the net then I will install Flash. 

Thanks

---

### Post by thschiavo on 2008-07-24
> **mogui_666 said:**
> 
where do i find the "iwconfig"?


In terminal. Open Applications/Acessories/Terminal and type

iwconfig

---

### Post by thschiavo on 2008-07-24
I was reading that link you post in your original post. 

"Support for this chipset with the official Madwifi-drivers is incomplete. So, you have two choices: either you use Windows drivers with Ndiswrapper or you try the Madwifi-drivers anyway. I have tried them both and both eventually worked for me. Now I'm using Madwifi, which is more native and hopefully a bit faster solution."

I believe, in the end, you will just do the same as he did.

---

### Post by powerpleb on 2008-07-24
If iwconfig produces "no wireless extensions" try typing this into the terminal:
```
lspci
```
This will be a list of your PCI devices. The wireless interface should be there. If it isn't (or your wireless device is USB) try ```
lsusb
```

Once you find out what chipset you have then we help your find the correct way to install them.

I recently purchased an Acer laptop too and it came with a Atheros 5007 chipset which Ubuntu claimed to support, but didn't. If this is your chipset have a look here for instructions on how to get it working: [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

---

### Post by mogui_666 on 2008-07-24
> **powerpleb said:**
> If iwconfig produces "no wireless extensions" try typing this into the terminal:
```
lspci
```
This will be a list of your PCI devices. The wireless interface should be there. If it isn't (or your wireless device is USB) try ```
lsusb
```

Once you find out what chipset you have then we help your find the correct way to install them.

I recently purchased an Acer laptop too and it came with a Atheros 5007 chipset which Ubuntu claimed to support, but didn't. If this is your chipset have a look here for instructions on how to get it working: [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

here is the screen shot...

[[IMG]http://img67.imageshack.us/img67/79/screenshotli6.png[/IMG]](http://imageshack.us)
[[IMG]http://img67.imageshack.us/img67/79/screenshotli6.72d820b40a.jpg[/IMG]](http://g.imageshack.us/g.php?h=67&i=screenshotli6.png)

I don't understand what is it talking about...

Please help thanks...

---

### Post by thschiavo on 2008-07-24
I can see no wireless device. Am I wrong? Is it everything that lspci outputs?

---

### Post by Bucky Ball on 2008-07-24
Your card is the Broadcom BCM5787M Gigabit Ethernet PCI Express by the looks. Thats a start.

---

### Post by powerpleb on 2008-07-24
Can you do it again and copy and paste the text into a post (much better than a screenshot).
I can't see a wireless device in that list, but the bottom of the output is chopped off.

I am pretty sure that 'Broadcom BCM5787M Gigabit Ethernet PCI Express' is a wired ethernet card.

---

### Post by thschiavo on 2008-07-24
> **powerpleb said:**
> 
I pretty sure that 'Broadcom BCM5787M Gigabit Ethernet PCI Express' is a wired ethernet card.
It's for sure.

---

### Post by mogui_666 on 2008-07-24
> **Bucky Ball said:**
> Your card is the Broadcom BCM5787M Gigabit Ethernet PCI Express by the looks. Thats a start.

ok so what do i do after that?

Thanks...

---

### Post by thschiavo on 2008-07-24
> **powerpleb said:**
> Can you do it again and copy and paste the text into a post (much better than a screenshot).
I can't see a wireless device in that list, but the bottom of the output is chopped off.


Would you mind doing this? type "lspci" in terminal, so copy and past the text into a post.

---

### Post by mogui_666 on 2008-07-25
> **thschiavo said:**
> Would you mind doing this? type "lspci" in terminal, so copy and past the text into a post.

Hi,

here is a screenshot..

[[IMG]http://img70.imageshack.us/img70/10/35194316af1.png[/IMG]](http://imageshack.us)
[[IMG]http://img70.imageshack.us/img70/10/35194316af1.23146b8a3f.jpg[/IMG]](http://g.imageshack.us/g.php?h=70&i=35194316af1.png)

thanks a million people=)

---

### Post by thschiavo on 2008-07-25
Now we know that it's a Atheros AR~ something. Maybe you could try the same that powerpleb suggested you. If this doesn't work, maybe it's time to try madwifi.

> **powerpleb said:**
> 
I recently purchased an Acer laptop too and it came with a Atheros 5007 chipset which Ubuntu claimed to support, but didn't. If this is your chipset have a look here for instructions on how to get it working: [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

---

### Post by mogui_666 on 2008-07-25
Hi thschiavo,

thanks. will try that out later..

Peace!!!

---

### Post by Digiter on 2008-07-25
We have viewed this ubunt profile. It also comes along with Windows vista. So can any suggestions for the rectification of the problem that you have encountered and how comes the problem. A detailed note is required.
---------------------
Digiter
[Social Media Marketing](http://www.inspire-itsolutions.com)

---

### Post by powerpleb on 2008-07-25
> **thschiavo said:**
> Now we know that it's a Atheros AR~ something. Maybe you could try the same that powerpleb suggested you. If this doesn't work, maybe it's time to try madwifi.

And if this doesn't work you can use the Windows drivers and ndiswrapper: [http://ubuntuforums.org/showthread.php?p=5453721#post5453721](http://ubuntuforums.org/showthread.php?p=5453721#post5453721)

---

### Post by thschiavo on 2008-07-25
> **Digiter said:**
> We have viewed this ubunt profile. It also comes along with Windows vista. So can any suggestions for the rectification of the problem that you have encountered and how comes the problem. A detailed note is required.
[Social Media Marketing](http://www.inspire-itsolutions.com)

Hm?:confused:

---

### Post by phidia on 2008-07-25
> lshw -C network Is often a simpiler way to get the device.
My Atheros card which is a AR5007EG is misreported as a 5006 card by lspci & lshw, and others at the forums here have mentioned that too.

There's a how to & thread on Atheros in Ubuntu [here]("http://ubuntuforums.org/showthread.php?t=792158&highlight=atheros").

---

### Post by germanix on 2008-07-25
[http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)
go to the above link and follow the instructions. You should have wifi in no time. If I can do it (the dumbest user of all) you can certainly do it.
This is a linux mint page but it worked wonderfully on my Ubuntu. I had my wifi going in 10 minutes.

---

### Post by mogui_666 on 2008-07-30
Hi guy, 

thanks for the helps. I have manage to install WIFI in my laptop. 

Now I have another problem. when i try to install FLASH in terminal, its just show me this message

> 
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.


Is there any solutions for this?

Thanks=)

---

### Post by Bucky Ball on 2008-07-30
> cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz](http://download.macromedia.com/pub/l..._070208.tar.gz)
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer

Try that. Worked a treat for me (each line individually of course!).

If it doesn't work, you may have more luck asking in a different forum topic, you will get more specific help. :)

---

### Post by mogui_666 on 2008-07-30
Hi Bucky Ball,

I have try that and its give me the error msg.

Thanks anyway=)

---

### Post by SunnyRabbiera on 2008-07-30
you dont install flash like you do in windows, you will need to use the repositories.
There is a program called synaptic that can help.
Also enable extra repositories.

---

### Post by mogui_666 on 2008-07-30
> **SunnyRabbiera said:**
> you dont install flash like you do in windows, you will need to use the repositories.
There is a program called synaptic that can help.
Also enable extra repositories.

Hi Sunny Rabbiera,

may i know how do i use repositories and where do i download synaptic?

Thanks

---

### Post by germanix on 2008-07-31
Repositories is where Ubuntu keeps a large selection of software to be downloaded. These are downloaded in packages by the Synaptic PackageManager. You do not need to download and install this package manager, it is already installed on your system. Just go to: System-Administration-Synaptic Package Manager. To find what you need you can either use the search function (flash player), or click on "section" then go to "multimedia" and find what you want. After you found what you were looking for, click the box in front of the application you wish to install. Then click the "apply" button on the top. Installation follows automatically.
Alternatively you can also use this code for your terminal.

Code:

sudo apt-get install flashplugin-nonfree

---

