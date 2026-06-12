---
title: "HowTo: Broadcom 4306 w/ndiswrapper"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by deathbyswiftwind on 2006-06-04
Here is how Ive got my broadcom 4306 to work with ndiswrapper everytime Ive done it.

Things you need
*Broadcom 4306 chipset wifi card
*Ndiswrapper
*WEP Key (if required by the network)

First download ndiswrapper. Also if you want to download the ndiswrapper gui installer. I find this much easier to explain to the new guys.

Open a terminal and enter the following command

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

It will ask you for your root password enter it and hit enter

Now enter the following command

```
sudo rmmod bcm43xx
```

Go to your system menu and go to administration>Windows Wireless Drivers

Once again it should ask you for your root password enter it and hit enter

Now just go and find where your drivers are and double click on the ****.inf file. Hit install

Next open a terminal and enter these following command

```
sudo modprobe ndiswrapper
```

```
sudo ndiswrapper -m
```

Reboot

Apon the restart you should see your wireless light turn on. After your system is up and running go to your system menu Administration>Networking

Select your wireless network and enter in your wep key if needed.

I prefer to use a static ip for my connections since I need to forward ports. Some people dont need to worry about it so you can just leave it as DHCP unless you need more. Click okay and you should be just peachy. 

I personally have never had a problem with installing mine so I dont think Ill be much help if you have any problems.

[B]UPDATE:

Make sure you do not set up networking before you restart I did it apon a fresh install (for testing purposes) and when I rebooted everything was all messed up and I had to hunt for a few hours deleteing all of ndiswrappers mess. Apon the install of my drivers my card was labeled wlan0. After rebooting it was renamed to eth0. Talk about a headache![/B]

[B]UPDATE:

A few people have asked my why apon reboot they have to re-modprobe ndiswrapper. This is an easy solution enter the following command in a terminal

```

sudo gedit /etc/modules

```

And put ndiswrapper in there. Save and exit.[/B]

---

### Post by iitywygms on 2006-06-18
Dude.
Anyone with the 4306 card should use this method.  I have been pulling my hair out for 2 days.  Your method worked perfectly.  Thanks!

---

### Post by deathbyswiftwind on 2006-06-18
Im glad it helped you. And to anyone else who might stumble apon this it also works for the BT Voyager 1060. I just recently helped a guy in the forums. It to uses the bcmwl5 driver.

Also I would recommend putting those commands into a text file and saving it on a cdrom along with the ndiswrapper and your driver and such that way if you have to format and only have web via wireless you wont be asking yourself what do I do?!

Plus please pass this along I hope it helps everyone!

---

### Post by Scotty562 on 2006-06-19
I'd just like to mention four  things.

1. THANK YOU!!!!!1111!!11

2. Make SURE you get both the .inf and .sys files. If you're missing one... this won't work.

3. [http://spohlenz.blogspot.com/](http://spohlenz.blogspot.com/) for the gui

4. Make sure you do this after a fresh install... It took me too many hours to figure this out = /.

Best of luck.

---

### Post by deathbyswiftwind on 2006-06-19
For anyone who wants to know how to use ndiswrapper through the terminal you need to first copy the .sys and the .inf file to your desktop then inside your terminal issue the following command

```
sudo ndiswrapper -i ~/Desktop/*******.inf
```

This will install the driver for your card. I prefer the other method but hey its up to you,

---

### Post by ubuntuuser on 2006-06-21
Great work, thank you.

---

### Post by Hg80 on 2006-06-23
This was a great help to me and installed my wifi in a few mins, 10 out of 10

---

### Post by Novek on 2006-11-15
Does this method need the RadioState|1/RadioState|0/ code? I have tried many different howto's... One have worked so i've managed to get my wireless card light turn on. But setting essid, WEP key and connecting is the thing which fails...

Any idea why i cant set my essid in iwconfig?

---

### Post by mckatch on 2006-11-16
Great guide - managed to get it to work far easier than others I have used to date. Many thanks

---

### Post by woopud on 2006-11-24
I understand the Ndiswrapper won't work with AMD 64 chip sets ?
I have an HP Pavilion zv5466cl with the Broadcom 4306.

Bert

---

### Post by th3negotiator on 2006-12-12
BEST FREAKING HOW-TO EVER!

took me 3 days but i finally got my broadcom card to work with ndiswrapper, on an amd 64 no less :P

anyway, many many thanks for the how-to, through out all the ones i tried and re-installations i had to go through, this is the only how-to that worked.

and again, great work:D

Will

---

