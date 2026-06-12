---
title: "PAP authentication failed"
date: 2007-10-22
forum: Programming Talk
---

### Post by jeremi99 on 2007-10-22
Hi Forum,
 I seek somebody's assistance so I can connect my new Acer Computer to the Internet using Ubuntu 7.04.
 I just succesfully installed Ubuntu 7.04 on my Acer Aspire 9300 Laptop.
 I installed a dual boot with Ubuntu or Windows Vista Basic.
 Not bad for a free operating system, but with Ubuntu, I cannot connect to Internet at all, while with Vista, I can connect every time I try. So the hardware is Ok.
 I am using a PPPOE modem over a home telephone line, connected to the Laptop with an Ethernet cable . No router, only one connexion at a time.
 I followed the ADSL connections in the Help menu and did :
   sudo pppoeconf
 I entred my user name like "someone@somewhere.com", my password like "*****" and answered to all the questions with YES. At the end of this procedure, I was supposed to be connected but I was not.
  A window appears saying “ Sorry, I scanned 3 interfaces but the access concentrator of your provider did not respond.  …..
  Then I did :
  sudo pon dsl-provider
 But no luck either.
 After, as suggested in a window, I used:
  plog
 Here is what came back:
 Oct 22 19:27:40 Jean-Laptop pppd [6949] Plugin rp-pppoe.so loaded
 Oct 22 19:27:40 Jean-Laptop pppd [6951] pppd 2.4.4 strated by root, uid 0
 Oct 22 19:27:40 Jean-Laptop pppd [6951] PPP session is 2805
 Oct 22 19:27:40 Jean-Laptop pppd [6951] Using Interface ppp0
 Oct 22 19:27:40 Jean-Laptop pppd [6951] Connect: ppp0 <--> eth0
 Oct 22 19:27:42 Jean-Laptop pppd [6951] PAP authentication failed
 Oct 22 19:27:48 Jean-Laptop pppd [6951] Connection terminated
 Oct 22 19:27:48 Jean-Laptop pppd [6951] Modem Hangup
  
  What does PAP authentication failed means ? How can I avoid this ?
  Does anyone know what I did wrong ?
  Many Thanks in advance.
  With kind regards
  jeremi99

---

### Post by jeremi99 on 2007-11-01
Hello Forum.
I can now connect to the internet and here is what I did:
First, it is necessary to have your ethernet cable connected to the pppoe modem and to the computer ( the modem must be turned on of course), before  the Laptop is booted.
Second, it is necessary to backspace off all the characters on the username line when in the "sudo pppoeconf" menu, then enter ONLY your user name.
Third, I configured the Network using the System -> Administration -> Network. In the connections tab, I selected "Wired Connection" and clicked "Properties". In the configuration setting, I selected the  "Local Zeroconf Network" and Ok that.
That's it !!  When the computer is booting, you can check the  "Activity LED" flicker on the modem.
Thanks to Info-Click who provided the hints to me.
I hope this helps.
Ubuntu is a lot of fun !
Regards.
jeremi99

---

