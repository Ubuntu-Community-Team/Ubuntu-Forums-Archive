---
title: "Where can I download the PPOECONF package"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by chuckk2619 on 2008-04-29
Hi Folks,

Have had Ubuntu running for about 3 days now - installed a treat and has worked well (apart from the resolution which is my next fix after this one).

I am running ADSL on a Siemens Speedstream 4200 modem/router - the internet runs fine on my dualboot XP.   Funny thing is, when Ubuntu boots, the ethernet light on the modem goes out.   I have searched for some info and have [COLOR="Red"]guessed[/COLOR] that I need to configure the PPOECONF package to get Ubuntu to recognise the ethernet card (an onboard REALTEK RTL8168/8111 PCI-E Gigabit card).

Trouble is, after typing in dpkg -s ppoeconf into the terminal, it states that the package is not installed.   The forums say you can find it on the Ubuntu CD, but I don't think the system looks in the right drive to find the CD (it says CD not found or something similar).   I've even tried to add my CD to the software repositories by typing sudo apt-cdrom add, but no go.

I then found a line in an Ubuntu forum that said I could download the PPOECONF package from [http://packages.ubuntu.com](http://packages.ubuntu.com).   Unfortunately the URL came up with an error, indicating the site was either down or no longer existed.

Questions I have are:

Will the PPOECONF package solve the problem and eventually allow me to connect to the net?

If it is the panacea, where can I get my hands on it?

I have all the necessary DNS info after doing an ipconfig /all command within XP.   So hopefully that won't hold me up.

Grateful for any help on offer :)

---

### Post by plucky on 2008-04-29
See the last post in the [link](http://ubuntuforums.org/showthread.php?p=2901884) might help as you are dual booting.

Are you connected directly to the modem/router by a cable?

Can you post the outputs of ```
lspci
``` and ```
ifconf
``` after you have the ethernet card working.

The code you require for pppoeconf is ```
sudo pppoeconf
``` to set up your ethernet card for **pppoe** communication.

Good Luck

---

### Post by chuckk2619 on 2008-04-30
Hey Plucky,

Thanks for the advice....seems that the XP driver that was installed by a Windows update was the cause of all the problems.   It shut down the NIC when XP shut down, so Ubuntu didn't even know a card was there when it booted up!   I reinstalled the manufacturer's driver and voila!   Worked like a charm...the ethernet light remained on and Ubuntu now allows me access to the net via Firefox.   The light at the end of the tunnel wasn't a train!

Thanks again for your help :)

---

