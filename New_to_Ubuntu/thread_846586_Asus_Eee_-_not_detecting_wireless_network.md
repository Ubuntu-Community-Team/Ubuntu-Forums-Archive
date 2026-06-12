---
title: "Asus Eee - not detecting wireless network"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by jam1492 on 2008-07-01
I've just installed ubuntu hardy on an Asus Eee series, but it detects no wireless networks. Wired networks work fine. Also the laptop was pre-loaded with a different variant of linux, so it would seem that wireless out to be able to work on ubuntu but I'm not sure how.

I have two questions:

1. How do I pull the information on the wireless card or other diagnostic information?

2. Do you have any suggestions for fixing this?

I'd be greateful for any suggestions you might have.

Alex

---

### Post by jingo811 on 2008-07-01
> 1. How do I pull the information on the wireless card or other diagnostic information?

Does the hard copy box that came with your laptop say anything about your WiFi specs or maybe the manual that came with it?

I wrote a little **"Make your Wireless work on any distro"** some time ago haven't been able to re-check what I've written so try follow it and tell me where you get stuck so I can revise my tutorial in the near future.
[http://virtualseafarer.com/witch/ndiswrapper/index.html](http://virtualseafarer.com/witch/ndiswrapper/index.html)

---

### Post by aysiu on 2008-07-01
Try [this](https://help.ubuntu.com/community/EeePC/Fixes#Wireless).

I'd actually recommend *ndiswrapper* instead of MadWifi. I had no luck with MadWifi.

---

### Post by jam1492 on 2008-07-01
Thanks very much for the suggestions and link.  I went though all the steps without getting errors, but somehow it didn't work for me. I'm not sure why. 

Alex

After downloading the driver file from the web page and copying it to a directory called /.utility/config/ here is what I ran, in case you spot any obvious errors (I put in a script in case I need to reinstall and run again)

  echo First we need to remove and blacklist any existing madwifi drivers;
  sudo modprobe -r ath_pci
  echo copy the following 
  echo 
  echo blacklist ath_pci
  echo 
  echo Copy this to the bottom of the following file
  echo
  echo press return twice to continue
  read junk
  read junk
  sudo emacs /etc/modprobe.d/blacklist file
  echo
  echo Next we need to install the ndiswrapper utilities:
  sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
  #echo next we download the windows drivers that we use for this method from the Asus website.
  #mkdir /home/amaynard/tempasus
  #wget 'http://dlsvr01.asus.com/pub/ASUS/EeePC/EeePC4G(701)/Wireless_XP_071011.zip'
  # mv Wireless_XP_071011.zip /home/amaynard/tempasus/
  # sudo unzip /home/amaynard/tempasus/Wireless_XP_071011.zip  
  #echo Navigate to the folder containing the net5211.inf and run these commands:

  #sudo ndiswrapper -i /home/amaynard/Wireless/ndis5x/net5211.inf
  sudo ndiswrapper -i /.utility/config/net5211.inf

  #echo You should then be able to load the ndiswrapper module:

   sudo ndiswrapper -m

  echo Finally, set the ndiswrapper module to load at each boot:

  echo sudo ndiswrapper -ma && sudo ndiswrapper -mi

  echo You may need to reboot for everything to take effect, but you should have a working wireless connection at this point.

---

### Post by aysiu on 2008-07-02
I don't know. I just used *ndisgtk*, the graphical version of *ndiswrapper* and found the appropriate .inf file, and it worked right away (no need to reboot).

---

### Post by jingo811 on 2008-07-02
Well aysius Ndiswrapper solution link said this:
[https://help.ubuntu.com/community/EeePC/Fixes#Wireless](https://help.ubuntu.com/community/EeePC/Fixes#Wireless)
> The windows drivers that we'll use for this method are either available on the EeePC DVD that should have accompanied your machine, or are available from the Asus website.

[LIST]
[*]The drivers are located on the **DVD** in: /Drivers/Wireless/ndis5x/. You will certainly need the net5211.inf and ar5211.sys files, but it's probably best to copy the entire folder.
[/LIST]


Even though it told you to install drivers from the Asus website I don't recommend you do.   The Asus people maintaining the website/support don't know if the drivers are working or not they don't seem to double check their materials.  They don't even make sense when you ask simple questions.

**Just get the drivers from the DVD** I say then the margin for errors will only be on your side not theirs as well.  Their website/support have like 80% error factor :) trust me on this even if I don't have an Asus Eee.

---

### Post by ZootNerper on 2008-07-02
Hi,

Have you tried the [www.eeeuser.com](www.eeeuser.com) site. It has some forums that may help and certainly some help on using wireless with other distros of Linux aside from the Xandros the eee comes with.

I have an eee 701 and installed eeeXbuntu on a SD disk. This eeeXbuntu has some additions to the Xbuntu distro specifically for the eee. I found the wireless didn't work as well as with Xandros. I could get a signal but weaker than with Xandros. Apparently the drivers with Xandros are proprietary to Asus. The generic ones don't work so well.

Sorry, I can't help more.

-- Zoot

---

