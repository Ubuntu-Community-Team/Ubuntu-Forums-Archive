---
title: "I can see wireless network, but it won't connect (ubuntu 10.10)"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by yon yonson on 2012-01-20
Hey guys, I'm very new to Ubuntu and I'm having trouble figuring out how to make my wireless work. I am able to connect to the internet through an ethernet cable and I really like how it all works. It'd be great to solve the wireless issue though. I'm on a Dell XPS M1210 laptop. It's got an Intel Pro/Wireless 3945ABG card. It recongnizes my wireless network (my router is Netgear N600 Wireless Dual Band WNDR3400), but when I try to connect to it, it thinks about it for a while and never really does anything. I've spent the last day and a half researching and trying to figure it out, but I've come to the point where I'm kinda at a loss and would really appreciate some help.

I've also noticed that the Additional Drivers window doesn't show any drivers... I've tried to update it using sudo apt-get update to no avail (it doesn't end up downloading anything)

any ideas? thanks in advance!

---

### Post by lechien73 on 2012-01-20
Hi and welcome to the forums,

Please could you open a terminal window and run the following commands:

```
rfkill list all
dmesg | grep iwl

```
Then post their output here? This Intel card should work with Ubuntu.

Thanks

---

### Post by yon yonson on 2012-01-20
thanks for the help lechien!

rfkill list all:
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

nothing happens when i type in the second one... maybe i did that wrong?

---

### Post by lechien73 on 2012-01-21
Ok...so that indicates that the iwl3945 driver isn't loaded.

Could you try:

```
sudo rmmod -f dell-laptop
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```

This removes the dell laptop WiFi driver, and replaces it with the Intel 3945 driver.

---

### Post by yon yonson on 2012-01-21
so i tried the first command and it asked for a password which i gave. then it didn't noticeably do anything. so i tried again and it said: 

ERROR: Removing 'dell_laptop': No such file or directory

i tried the other two commands too with nothing noticeable happening after. Wireless still doesn't work... did I do that wrong? thanks so much for your help lechien. anything else i should try?

---

### Post by SuaSwe on 2012-01-21
Hi guys,

Am I understanding correctly that you can see your wireless network in the list when clicking on the wireless icon? If so, I would think the driver is already loaded and that there is some other problem causing you not to be able to connect - could you verify whether this is the case?

---

### Post by GregA on 2012-01-21
Support for Intel wireless should already be in the kernel (you don't need any drivers to install).   You might try to download and burn the current version of Kubuntu 11.10, and boot into it (live CD concept).   See if it can connect with the default network tool ("Network Manager" I believe)

Also, from your description,  (trying to connect), perhaps you didn't type in your WPA2 password correctly - - resulting in the no response.  The password is case and space sensitive.

Also as info, when you use sudo, and are prompted for password, you won't see any characters/markers upon typing.   That's how it's designed - but the system is still accepting your input.

If you have success with the Kubuntu Live CD, you might consider installing it, and then later adding other Desktop Environments (gnome 3x, xfce, etc.)

---

### Post by Djesurun1 on 2012-02-18
Hello all! Sorry if I'm not supposed to ask this in someone else's thread but I am having the same problem here. I have ubuntu 11.10 and my wireless card (netgear Wg311t) will find my network prompt me for the password and then keep asking after I put it in. I have AT&T uverse and their tech support is a joke so I don't know what else to try. Could it still be a driver issue even though it can find my network? I connected via Ethernet and got all of the available updates already. Thanks in advance, I'm completely new to linux and looking forward to learning! 
This computer I built just for fun but the hard drive on my MacBook just died. So now my little hobby has turned into a necessity for schoolwork!

---

### Post by Bartender on 2012-02-18
I found this very disconcerting, but apparently Intel wi-fi cards, which "just worked" for several versions of Ubuntu, are now on shaky ground.

I asked about [this problem]("http://ubuntuforums.org/showthread.php?t=1901351") a few weeks ago.  You might want to try what Wildmanne suggests in that thread.  It worked for me.

The nice thing about Wildmanne's directions is that you can go back into that modprobe/options file and delete the addition.  In other words, it's totally reversible.  I'm always nervous about changing things willy-nilly because I'm not very good with the command line and rarely know for sure if I can "go back" after making changes.  For example, I have no idea how you would reverse the directions given in post #4.

Djesurun1, your problem is NOT the same.  You're trying to use a USB external antenna thingie.  The answer - if there is one - to your situation will not be the same as the OP's.

---

### Post by Djesurun1 on 2012-02-20
Thats interesting...where did you pick up that it was a on a usb? It isn't actually...maybe that's my problem? I am using a netgear PCI card.

> **Bartender said:**
> I found this very disconcerting, but apparently Intel wi-fi cards, which "just worked" for several versions of Ubuntu, are now on shaky ground.

I asked about [this problem]("http://ubuntuforums.org/showthread.php?t=1901351") a few weeks ago.  You might want to try what Wildmanne suggests in that thread.  It worked for me.

The nice thing about Wildmanne's directions is that you can go back into that modprobe/options file and delete the addition.  In other words, it's totally reversible.  I'm always nervous about changing things willy-nilly because I'm not very good with the command line and rarely know for sure if I can "go back" after making changes.  For example, I have no idea how you would reverse the directions given in post #4.

Djesurun1, your problem is NOT the same.  You're trying to use a USB external antenna thingie.  The answer - if there is one - to your situation will not be the same as the OP's.

---

### Post by Bartender on 2012-02-20
OOPS, sorry, I assumed it was a USB external.

From what I understand, when you're researching something like this, the key is to figure out what the actual chipset is on the card you're using.

Take a look [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") to see lists of cards that are supposed to work.  Unfortunately you'll see that lots of the cards don't work, and most of the info is dated.

The WG311T shows up in [this list]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear").  You can see that people got it to work by using madwifi.  At least they did in older versions of Ubuntu, which may or may not help you.

The WG311T shows up again [here]("http://madwifi-project.org/wiki/Compatibility/Netgear").

I personally have not had much luck with these programs that try to get a Windows-compatible wifi chipset to work.  The one time I was successful, the laptop saw a connection and updated to a new kernel, which broke the work-around and I had to do it all over again.  

You may want to search for something that works "out of the box".  I have a (discontinued now) Gigabyte GN-WP01GS PCI card that "just worked" in several different Ubuntu installs.  I don't have any info on which ones work OOTB today.

You might have better luck browsing the "Networking & Wireless" sub-forum than this one.

---

### Post by Djesurun1 on 2012-02-20
Thanks for doing that search bartender! I've seen my card listed on the working cards list before, im just not sure where to go from here. Ive made a few posts in the forums so hopefully i get responses in the near future. I'm curious what does "Detected in Network Settings as ath0 and started working once the WAP details were input." mean in the description on the working cards list? What WAP details would need to be input...and where would i put it?

---

