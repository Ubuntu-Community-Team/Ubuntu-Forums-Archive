---
title: "Wireless predicament"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Dark006 on 2008-07-01
Ndiswrapper is installed correctly, and so is the driver (or so it says) and it still doesn't work. 

Ok, I'll list everything I have and that I would think is important.

**Linksys WMP300N** - This PCI Adapter is on the list (on Documents/Wiki on ndiswrapper's website)of cards *known* to work.

**lspci** outputs: 02:0a.0 Broadcom Corp BCM43XG(rev 01)

**lspci -n** outputs: 14e4:4329(rev 01)

I have ndiswrapper-1.52 installed, located in /usr/sbin/ndiswrapper and /etc/ndiswrapper (thats what "**whereis**" told me)

Driver I downloaded was WMP300N_20071019, which as been put in the /etc/ndiswrapper directory.

I then ran **ndiswrapper -i bcmwl5.inf** which then said it was installing. I followed up by running **ndiswrapper -m** then it gave me an error. So I ran the same command with **sudo** in front of it and I told me I should not do that. I did say it added the alias wlan0 to ndiswrapper though.

So at this point I thought I was all done. I ran **ifconfig wlan0 up** and it gave me an error saying..

**wlan0: ERROR while getting interface flags: No such device**

So lastly, I ran "ndiswrapper -l" to show installed drivers and it came back with, "bcmwl5 : driver installed, device (14e4:4329) present". But 2 lines below that it says WMP300N_20071019 : invalid driver! (and) WMP300N_20071019.exe : invalid driver!

I'm really sorry if thats to long or confusing of a post, but I'm in desperate need right now. Any input would be greatly appreciated.

---

### Post by Dark006 on 2008-07-01
Haha, nevermind, I figured it out after posting this. There were extra files in the /etc/ndiswrapper directory (and they were stubborn, I had to run 'sudo rm -rf file_name' to get rid of them. 

It appears to be seeing all the wireless networks available when I type 'iwlist wlan0 s'. Now, my only question is, how do I connect to my network? The encryption is WPA also by the way.

---

### Post by Miljet on 2008-07-01
Click on internet icon at top right of screen, select your network, enter passkey when prompted, select yes when it offers to store your passkey in the keyring. You should be good to go.

---

