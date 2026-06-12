---
title: "[SOLVED] 8.10 Intrepid hangs at startup"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by person8451 on 2008-11-01
Well so far I have burned 3 CD's, (one regular, two alternate-install, checked md5sums, burned at slow speeds), and tried installing 8.10 on two different computers, and tried booting from the LiveCD, and in each case I get the same result.

It boots up, then after the login screen, there is just a black screen with a mouse pointer in the middle and nothing happens.  

I have an old Compaq and an older Dell with no video cards, and I am assuming at this point that Ubuntu has passed me by and I won't be able to run it on old machines with just onboard graphics.  

I have no idea how to change options or anything when it just hangs after booting, and I am not sure how to tell what is holding it up.  

I am hoping I will not have to go back to Hardy, and upgrading my system at this point is not really an option.  So I am hoping there is some way to work around this issue.

Any help would be greatly appreciated.

---

### Post by nhasian on 2008-11-01
can you give us more details on on the specs of your computer?  does it meet the minimum requirements for Ubuntu?  If not, you can try Xubuntu

[https://help.ubuntu.com/community/Installation/SystemRequirements#Low-spec%20computers%20(Xubuntu](https://help.ubuntu.com/community/Installation/SystemRequirements#Low-spec%20computers%20(Xubuntu))

---

### Post by person8451 on 2008-11-01
Well let's see...

Compaq Evo 510 sff  
2.0 GHz processor
1 GB RAM 

Dell Dimension 2400
2.4 GHz 
768 MB RAM

Excellent machines for the price (both free lol)

---

### Post by jerrylamos on 2008-11-01
8.10 Ubuntu runs fine on this 1 gHz IBM Thinkpad R31 with 512 mb memory.  Full screen BBC videos perfectly usable (O.K., a bit jerky but easily livable).

That is, now it runs fine.  From August 13 until today, booting up would give a "black screen of death" when the desktop should have loaded.

So I would install (doesn't use compiz)
Boot in rescue mode (doesn't use compiz)
At the selection menu
root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot.

So the "official fix" came in.  See Launchpad Bug #259385.  With compiz version 1:0.7.8-0ubuntu4.1 it simply "blacklists" a number of Intel video chips including mine and then compiz won't be run.  Now it should have just dropped back to the 8.04 level of compiz which ran, however it did use up CPU cycles and on this older computer I'd select Visual Effects None.

The "official fix" is just like removing compiz except of course compiz code still takes up hard drive space, just never executed.

Jerry

---

### Post by jerrylamos on 2008-11-01
If you get going, could you run in a terminal window:
lspci
and paste in the video hardware info, for example mine is

VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)

Thanks much, Jerry

---

### Post by person8451 on 2008-11-02
DELL--

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

COMPAQ--

Intel(R) 82845G/GL/GE/PE/GV Graphics Controller


I have managed to get Intrepid up by removing compiz/compiz-core (I am posting this with it right now).  It works for now, thanks :)

---

### Post by Phil Airtime on 2008-11-30
I have the same issue with Intrepid on a Compaq Evo D510 with onboard graphics. On lspci, the graphics come out as:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

It seems a little counterproductive to enable Compiz by default when it hangs some machines on the first boot. Can't it be off by default and turned on if a flash graphics card is detected during install?

---

### Post by bardophile on 2009-04-02
Thank you, thank you, thank you! I have now finally been able to move beyond the blank tan screen. Just beginning with Linux, so was pretty disappointed to be stuck at login. :)

---

