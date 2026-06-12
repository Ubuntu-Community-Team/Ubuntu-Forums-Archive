---
title: "Software Center problem with wireless connection"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by midjie on 2011-09-23
Hi,I'm still new to the ubuntu 11.04.had it dual boot with windows 7.I had installed all the necessary addons.Im using unity bcoz Gnome3 crashed when I installed it.the problem started when I installed the update using the update manager.I can't use the software centre to download anything.I'm using wifi connection.it display "Failed to download package,check internet connection".but I can surf the internet just fine (I'm writing this question).I'm using Acer Aspire 4738G laptop.iwconfig status:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"360@KSKB3"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:15:6D:B0:B1:BE   
          Bit Rate=78 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:74   Missed beacon:0
(I don't know if it means  something)
p/s : please show me step-by-step solving.really appreciate that.

---

### Post by bradleypariah on 2011-09-23
I've actually had this problem before.  I remember Synaptic working fine, meanwhile the USC wasn't working at all.  

If this is the case, you could completely uninstall and re-install the software center from the Synaptic Package Manager.  

Just search for "software center", mark it for complete removal, then restart your machine, go back to Synaptic and re-install USC.

If that doesn't work (please forgive the shabby advice), but you may want to consider backing up your valuables in your home directory and just re-installing Ubuntu - that's if no one comes along with much smarter advice ;-)

---

### Post by midjie on 2011-09-23
woah...thats sounds too risky for me.I had already uninstall Ubuntu 2 times already.bcoz of the Gnome3, of course.and you have to start it over again,costing me internet bills.addons,apps...any other advice?

---

### Post by wildmanne39 on 2011-09-23
Hi, welcome to the forum! please run this command in the terminal and post the complete error message here.
```
sudo apt-get update && sudo apt-get upgrade
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by midjie on 2011-09-23
hm...nope,no errors found.everything is fine.

---

### Post by wildmanne39 on 2011-09-23
Hi, then it is likely that the server was just down, because if you were having errors because of a problem with your computer either connections wise or other you would have received errors, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by midjie on 2011-09-23
U might be right...now its working again.but the funny part is that,all the browser were fine.thanks.

---

### Post by wildmanne39 on 2011-09-23
Hi, that is because it was the server where the updates where located on there end not yours.
Thank you

---

