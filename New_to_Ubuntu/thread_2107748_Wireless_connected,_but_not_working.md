---
title: "Wireless connected, but not working?"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by petefic on 2013-01-22
I just installed Ubuntu 12.04LTS on my HP Pavilion G6 1D60US laptop.

I connected to the wifi in my home and it says that it is connected yet when I open up a browser I get a "server not found" error.

In the additional drivers window, I see "Broadcom STA wireless driver" but when I try to activate it I get the error "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"

the log file is too big for me to attach.

---

### Post by roger_1960 on 2013-01-22
Hi

It is quite possible that your in house wifi network is working without access to the Internet.   Can you access the Internet with any other devices on your wifi network?

---

### Post by petefic on 2013-01-22
> **roger_1960 said:**
> Hi

It is quite possible that your in house wifi network is working without access to the Internet.   Can you access the Internet with any other devices on your wifi network?

Yes, the laptop is dual booted with windows 7 and when I'm in windows 7 it works fine. It also works fine on my desktop windows machine and iphone.

---

### Post by TOMBSTONEV2 on 2013-01-22
Is your wireless network adapter a broadcom bcm43xx? Please open up a terminal and paste:

```
lspci
```to determine which card you have.

---

### Post by petefic on 2013-01-22
> **TOMBSTONEV2 said:**
> Is your wireless network adapter a broadcom bcm43xx? Please open up a terminal and paste:

```
lspci
```to determine which card you have.

Yes. It is Broadcom Corporation BCM4313

---

### Post by TOMBSTONEV2 on 2013-01-22
Than I shall refer you to this:
```
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx
```
Pretty much you have to install the b43-fwcutter firmware, then install the b43 wifi drivers. If you don't have internet access scroll down to b43 - No Internet Access  If you need any help let me know. I will be happy to assist.

---

### Post by bkratz on 2013-01-22
The BCM4313 should actually work with the STA driver not b43. Please hook up an ethernet cable and

sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl

and let us know.



supporting documentation

[http://ubuntuforums.org/showpost.php?p=12436520&postcount=4](http://ubuntuforums.org/showpost.php?p=12436520&postcount=4)

---

### Post by TOMBSTONEV2 on 2013-01-22
More often than not I see people having various network issues with the STA driver. While the STA driver is technically better on systems in which it works, I find the b43 driver works much better on systems that have issues with the STA driver. So technically I should have started off with:

sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl

Then suggested b43 if it did not work.

---

### Post by petefic on 2013-01-22
> **bkratz said:**
> The BCM4313 should actually work with the STA driver not b43. Please hook up an ethernet cable and

sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl

and let us know.



supporting documentation

[http://ubuntuforums.org/showpost.php?p=12436520&postcount=4](http://ubuntuforums.org/showpost.php?p=12436520&postcount=4)

When you say hook up an ethernet cable, do you mean connect it to the laptop and the modem, or just plug it into the laptop and not connect it to anything.

I say this because my modem is in my attic, not very easy to get to.

---

### Post by bkratz on 2013-01-22
Actually it does require internet access, so it might be a problem.  I will look to see if there may be an option.

---

### Post by TOMBSTONEV2 on 2013-01-22
Is there a location in which someone can download the latest linux headers on a different pc then move them to the linux machine?

---

### Post by petefic on 2013-01-22
Is it possible to download them on my windows desktop and transfer it via flash drive?

---

### Post by TOMBSTONEV2 on 2013-01-22
I was just wondering the same thing. I know you can do the b43 driver method off line, but the STA drivers I cannot seem to find some good information on if it is possible to get the headers from a different location.

---

### Post by bkratz on 2013-01-22
It is possible to do it from the installation CD you used when you installed the system.  It sure would be easier with internet access!

See this under STA -no internet access

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by petefic on 2013-01-22
OK I stopped being lazy and climbed up and connected via ethernet. Ran the 3 commands listed earlier and everything works fine now. Thanks everyone.

---

### Post by bkratz on 2013-01-22
> **petefic said:**
> OK I stopped being lazy and climbed up and connected via ethernet. Ran the 3 commands listed earlier and everything works fine now. Thanks everyone.




I'm sure glad it worked!



and please go to the thread tools above and mark as solved, in case it helps someone else.

---

### Post by audiomick on 2013-01-22
> **petefic said:**
> OK I stopped being lazy and climbed up and connected via ethernet.

Well done. Sometimes that is the only way... ;)

---

### Post by petefic on 2013-01-22
OK, I seemed to have found the real problem. I am only able to connect to the internet if I am right next to the router. When I went back to the room I usually sit in I again couldn't connect. When I'm in windows I get the same speeds in this room that I do next to the router.

The problem isn't that I can't connect to the wireless, it's that for some reason my wifi card's range sucks when I'm in ubuntu. Is there a possible fix for this? When I was next to the router and connected I installed the drivers in the additonal drivers menu.

EDIT: I installed the b43-fwcutter drivers and now everything is working perfectly. Thanks again everyone.

---

### Post by audiomick on 2013-01-23
Please mark the thread as solved. The option is in the "thread tools" menu at the top of the thread.

---

