---
title: "Compiz - 3D desktop ???"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by eopi on 2008-06-19
How to I install Compiz for 3D desktop and effects?  I read on other threads that it's already installed but.

System -> Preferences -> Visual Effects.  On my laptop there is **no Visual Effects**.

I have Hardy. 

So I go to System -> Admin - > Synaptic PAckage Manager  

Then what? 

Thank you for help/.

---

### Post by Hamchan on 2008-06-19
I just used the terminal to get the appropriate application:

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by tjwoosta on 2008-06-19
yes, compiz is already installed on ubuntu, but you cant configure the settings untill you install the "compiz config settings manager" or CCSM for short

installing this will give you the "advanced desktop effects settings" option on the system-preferences menu

to enable compiz you need to go to System-Preferences-Appearance (not advanced, advanced settings is only for configuring it)

in appearance click the visual effects tab then choose extra

---

### Post by eopi on 2008-06-19
> **Hamchan said:**
> I just used the terminal to get the appropriate application:

```
sudo apt-get install compizconfig-settings-manager
```

Ok I did that and now what?

---

### Post by tjwoosta on 2008-06-19
> to enable compiz you need to go to System-Preferences-Appearance (not the advanced settings, advanced settings is only for configuring it)

in appearance click the visual effects tab then choose extra

after enabeling it you go to advanced and then setup everything

---

### Post by eopi on 2008-06-19
> **tjwoosta said:**
> after enabeling it you go to advanced and then setup everything

Well 0-2 Ubuntu is winning and im losing. 

An ERROR occured:

Failed to fetch  YADA YADA YADA nvidia-glx-new_169.12

!!#$%^#@&*  $%&*@#)(

DESKTOP effects could not be enabled.

Microsoft has destroyed large database of mine but that isn't even as infuriating as Ubuntu. I have yet to do anything successful here.  

No wireless conncection and now no 3D effects.

:)  trying to much to keep it cool.

---

### Post by EXCiD3 on 2008-06-19
You also have to make sure your video drivers support 3D. What video card do you have? Check System > Hardware Drivers to enable the drivers capable of 3D.

---

### Post by eopi on 2008-06-19
> **EXCiD3 said:**
> You also have to make sure your video drivers support 3D. What video card do you have? Check System > Hardware Drivers to enable the drivers capable of 3D.

I did that and I see NVIDIA accelerated graphics driver (latest cards)  Not in use.  I check the box to Enable but then I get the Error. 

FAILED to fetch something.

---

### Post by tjwoosta on 2008-06-19
if your card has good 3d support and it still dont work it is possible that your video card is blacklisted

sometimes you can skip the check and force the card to work but its risky

see here[http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist")

---

### Post by tjwoosta on 2008-06-19
ahh, ok you have an nvidia card  so you will probably need restricted drivers

never actually had to use before so i cant really help

hope this at least points you in the right direction

here is help topic for nvidia drivers
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by EXCiD3 on 2008-06-19
Since that doesnt work you can either install the drivers from source (somewhat of a pain for new users) or you can download and install Envy-gtk from Synaptic or apt-get. Run it from Applications > System Tools > Envy and it iwll take care of your drivers for you.

---

### Post by sicofante on 2008-06-19
> **eopi said:**
> I did that and I see NVIDIA accelerated graphics driver (latest cards)  Not in use.  I check the box to Enable but then I get the Error. 

FAILED to fetch something.
Sorry if it sounds silly but are you connected to the internet?

Are you able to install any piece of software at all? To check it out you might want to select "Add/Remove" from the Applications menu and try installing some application.

---

### Post by EXCiD3 on 2008-06-19
> **sicofante said:**
> Sorry if it sounds silly but are you connected to the internet?

Are you able to install any piece of software at all? To check it out you might want to select "Add/Remove" from the Applications menu and try installing some application.

Good call on the internet...could be the problem, i over looked that, but ive also had the Hardware Drivers fail to install them...actually almost every time it has failed. Envy has turned out to be the best option aside from compiling by hand but its always best to recommend the official supported way (hardware drivers) first off.

---

### Post by eopi on 2008-06-19
Ok it sounds like good adivce but now I need to unconnect the internet from my desktop running Microsoft Windows XP and cable up my Laptop with Ubuntu (unable to get wireless connection with ubuntu).

Btw, Best Quote in the world ***"(somewhat of a pain for new users)"***.  :)

I shall return, hopefully with some good news.
  

> **EXCiD3 said:**
> Good call on the internet...could be the problem, i over looked that, but ive also had the Hardware Drivers fail to install them...actually almost every time it has failed. Envy has turned out to be the best option aside from compiling by hand but its always best to recommend the official supported way (hardware drivers) first off.

---

### Post by EXCiD3 on 2008-06-19
> **eopi said:**
> Ok it sounds like good adivce but now I need to unconnect the internet from my desktop running Microsoft Windows XP and cable up my Laptop with Ubuntu (unable to get wireless connection with ubuntu).

Btw, Best Quote in the world ***"(somewhat of a pain for new users)"***.  :)

I shall return, hopefully with some good news.

haha, thanks ;) reason i said that is because doing it by hand requires you to shut down all your graphical applications and work from the command prompt.

Post the graphics card you have (run lspci in terminal to display it) and then we can get that up and running for you too! :)

---

### Post by eopi on 2008-06-19
Sorry to disappoint. I don't have internet connection on my laptop with my wire. But earlier it was working.  :confused:

So I restarted Ubuntu laptop and still no connection.  I check the Desktop computer and I get internet.  Then I reconnect to laptop, still no connection. 

I was messing with my wireless network yesterday but I don't think I destroyed anything, cable was working yesterday. 

So I guess I can go no further today.  

But thanks for your help.  

Trying so much to have a positive attitude towards Linux.


> **EXCiD3 said:**
> haha, thanks ;) reason i said that is because doing it by hand requires you to shut down all your graphical applications and work from the command prompt.

Post the graphics card you have (run lspci in terminal to display it) and then we can get that up and running for you too! :)

---

### Post by EXCiD3 on 2008-06-19
Whoops i meant to ask which wireless card you had...not graphics. Run lspci in terminal on your laptop if you arent sure.

One thing you can do...is the hard way of installing the driver.. haha ;) This is the best guide for it, just save the driver to a usb drive and you will need to make sure you have the packages installed for building it...which you can download the .deb's to your flash drive from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then follow this guide: [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6) Sometimes you may have to do this more than once...doesnt always work the first time for some reason but its the most reliable tutorial ive found. Good luck and let me know if you have any questions, im heading off to bed but ill be back online tomorrow. Feel free to contact me over IM, links are on my profile. :)

---

