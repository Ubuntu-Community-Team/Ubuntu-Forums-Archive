---
title: "Unable to install Wireless adapter on old HP Pavilion"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by dgomez2 on 2014-03-19
I am completely new to Linux and just installed Lubuntu 13 on a very old  HP Pavilion zv5200 laptop. I understand I need to install NDISWRAPPER  in order to make the Broadcom 4306 WiFi work. I already have the Windows  .inf and .sys files for the wireless adapter.

I downloaded ndiswrapper-1.59.tar in another PC and copied it to to the Linux laptop. 
I extracted the file but when I tried to build it using 'make' it told me 'make' was not installed. 
I found out I had to install 'build-essential' but when I tried this  (sudo apt-get install build-essential) it just said there were no  candidates.
I tried looking in the Software Center and Package Manager but found no mention of ndiswrapper, make, or build-essential.
I am getting really frustrated as I do not understand how to install or even find these commands.

I would appreciate it very much if someone would be patient enough to  show me the way to get ndiswrapper and my wifi adapter working.

Thanks!

---

### Post by westie457 on 2014-03-19
You already have an answer to this question in your other thread.

[http://ubuntuforums.org/showthread.php?t=2212034](http://ubuntuforums.org/showthread.php?t=2212034)

Ndiswrapper will not work.

---

### Post by Rex Bouwense on 2014-03-19
Forget  Ndiswrapper.  Look here.
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by dgomez2 on 2014-03-19
Thank for the reply. Sorry, I wasn't paying attention. I'm going to look over them now. 
Rex, thanks for the links. I'll look into them right away.

---

### Post by Rex Bouwense on 2014-03-19
I have on old Dell with a 4306 Broadcom card and it is a pain.  You just have to keep plugging.  Let us know how it comes out.

---

### Post by dgomez2 on 2014-03-20
Solved!! I followed the steps suggested in the other post by Varunendra and now I have a working wlan adapter.
First, I downloaded the firmware package from this link : [http://mirrors.kernel.org/ubuntu/poo...buntu1_all.deb]("http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb")
Then I ran: 
sudo dpkg -i Desktop/linux-firmware*.deb

Rebooted, created a wifi connection with my router's info and now I have Internet access.

Thanks for the info and help!!

---

### Post by mörgæs on 2014-03-20
Next time please open only one thread.

---

