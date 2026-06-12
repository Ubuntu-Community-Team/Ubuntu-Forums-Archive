---
title: "Need Internet to update, need internet to get internet"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Azurkan on 2008-10-24
Ok, so this is a weird dilemma lol.  I have just installed Ubuntu on my CPU so it dual boots XP and Ubuntu, it is custom made so it is not a Dell, HP, Gateway etc.  I use a NETGEAR RangeMax USB Adapter WP111 to get internet because our house is wireless, but in order to get the OS to recognize it I need to use WINE correct? Well how am I suppose to download WINE when I can't get on the internet.... I tried downloading the RangeMax Driver and installing it that way but it didn't work :( so if anyone has any ideas that would be AWESOME!!!

---

### Post by OldGrey on 2008-10-24
Can you temporarily plug the pc into the modem router via and ethernet cable?

---

### Post by DFord425 on 2008-10-24
Can you boot in windows and download the drivers? Or can you bring your computer close enough to the router to plug it in with an ethernet cable?

---

### Post by Azurkan on 2008-10-24
I tried downloading the drivers in Windows then installing them in Ubuntu and it was a no go :( and I can't plug my PC in to a router without taking it somewhere else other than my house to do so

---

### Post by michaelbogardus on 2008-10-24
I'm not sure if this will solve your dilema, but I have DSL, and whenever I need to go on the internet I open the terminal and type:
> sudo pppoeconf
Pretty much hit yes, except where it asks you for the email address your ISP gave you, like [email]myname@aliant.net[/email], and thne for your password. Just click yes through it from there, and hopefully it will get you online.

---

### Post by Azurkan on 2008-10-24
> **michaelbogardus said:**
> I'm not sure if this will solve your dilema, but I have DSL, and whenever I need to go on the internet I open the terminal and type:

Pretty much hit yes, except where it asks you for the email address your ISP gave you, like [email]myname@aliant.net[/email], and thne for your password. Just click yes through it from there, and hopefully it will get you online.

I would do that but the problem is that the computer does not recognize the USB adapter so it says that I do not have any internet connection at all...

---

### Post by Patricrawley on 2008-10-24
You have the wpn111, right? Because if you do what you need to do is install ndiswrapper, which you can do from your live disk. To do this you go to system>administration>software sources. Then you put a check mark next to the cd at the bottom and close the window. It will ask you if you want to update, do it. Don't mind the error message you get because that will be for the internet software repositories that you cannot connect to yet. Then open Synaptic Package Manager and install ndiswrapper, there is a gui for ndiswrapper that is available too if you want to use that to make your life a little easier. Then once you have all that installed, you need to install the necessary drivers for your usb wifi card. The drivers for the wpn111 are netwpn11.inf and athfmwdl.inf. I will attach these to this post so you can get them to your computer with a flash drive. I know for a fact that the install cd also has netwpn11.inf on it however, I am not positive if it has the second driver that you need to install. Once you have both of these drivers onto your new computer, open terminal, applications>accessories>terminal. Enter in the following once you have navigated to the folders where you have saved the drivers. 

```
sudo ndiswrapper -i netwpn11.inf
sudo ndiswrapper -i athfmwdl.inf
```

To make sure that you have correctly installed your drivers you enter:

```
ndiswrapper -l
```

If the text that it displays after you entered the code tells you that both of the drivers you have installed are there and that the device is available for netwpn11.inf than you have installed them correctly.

To make the drivers work and your computer connect to the internet, you will want to type this into the terminal as well.

```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

If you are not connected once you reboot your computer, open terminal and type in:

```
sudo modprobe ndiswrapper
```

That should get your wifi card working.

Also, if you are ever disconnected for reasons that you cannot explain try the following command:

```
sudo rmmod ndsiwrapper
```

Unplug your wifi card and plug it back in and then enter:

```
sudo modprobe ndiswrapper
```

---

### Post by Patricrawley on 2008-10-24
I forgot to upload the files.

---

### Post by Azurkan on 2008-10-24
Wow lol ok thank you :) I will definitly give that a try when I get back to my house...I have to go to class now ;), but thank you this seems like it should do the trick :-D

---

### Post by Patricrawley on 2008-10-24
Also, for future knowledge, WINE is not what you think it is. WINE is so you can run a Windows program in Linux, like Office or a game if you want. As far as I know, you can't use WINE to run a driver for a device. I may be wrong though.

---

