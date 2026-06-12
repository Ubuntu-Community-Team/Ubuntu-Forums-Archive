---
title: "HP Dv6 7040tx: Clean Installation of Ubuntu"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by dinesh2707 on 2014-04-22
I have been using ubuntu in VirtualBox for a very long time. I have been forced to use Windows for the past years due to my University projects and bleh bleh. So, basically I know how to use Ubuntu :o

Now, with my college days ending this month, I'm very excited to switch over completely from Windows to Ubuntu (I personally hate Windows!) :popcorn:. I know basic steps to install along side windows. But, I need to COMPLETELY switch over. So, I'm asking for your guide!

My laptop is [B]HP Dv6 7040tx
[/B]
Here are my specs:
[LIST]
[*]i7 3610QM
[*]6GB RAM
[*]750GB HDD
[*]Dual GPU (Intel 4000 + Nvidia 630M 2GB)
[*]Beats Audio (Quad Speakers + subwoofer) - 4.1
[*]Broadcom 4313 Wireless card
[*]HP Cool sense included (I don't know whether an equivalent is available in ubuntu)
[*]Finger print sensor (from VALIDITYINC. with PID=0018
[/LIST]

Please give me some basic guide for installing Ubuntu 14.04.

Also, for wireless card I have read up the driver from Broadcom. They support only till 12.04. There are no drivers for 14.04. I'm pretty sure it won't work in 14.04 as i have tried booting up as guest OS. And, as far as I have read about 4313 card, I know it's bit complex to activate the card.

Considering the fingerprint sensor, I read that Fingerprint sensors aren't supported in ubuntu. Is there a way to make use of that sensor in ubuntu? (Coz, if it didn't work it's a waste of money for me)

Thanks and I'm eagerly waiting for your Guide! :D

---

### Post by Ubi_one_2014 on 2014-04-22
i recommend to bootup from the dvd, and familiarise yourself with ubuntu, and check if everything is working
if so, you can start the installation, and let ubuntu guide you trought the process

the installation process is very self explaining.

---

### Post by dinesh2707 on 2014-04-22
> **Ubi_one_2014 said:**
> i recommend to bootup from the dvd, and familiarise yourself with ubuntu, and check if everything is working
if so, you can start the installation, and let ubuntu guide you trought the process


the installation process is very self explaining.
I tried the Ubuntu from USB stick! I faced the issues of Wifi, Overheating due to dual Graphics Card, No Fingerprint and No BEATS AUDIO!

---

### Post by PotatoHead007 on 2014-04-22
Personally i hate HP for Linux, never had a good experience with it. But awesome system specs :P
If you really want to leave Windows, maybe go to Ubuntu 12.04.4? it is very stable and supported. And the only thing you are missing is some eyecandy ;)

---

### Post by Jordan_Cameron on 2014-04-22
I second PotatoHead007, try 12.04.4 first.  While 14.04 is a LTS, it's still fresh out of the oven, whereas 12.04.4 has a couple years of support backing it already.

---

### Post by mörgæs on 2014-04-22
There's better hardware support in 14.04, especially for the graphics card. 

The netcard is easy to get working once you have done a real install (using wired internet access).

Dv6's are infamous for overheating. Best is that you do a thorough search on the issue.

---

### Post by SeijiSensei on 2014-04-22
I'm running Kubuntu 14.04 on a dv6t as I write this posting.  However this machine has an ATI card, not an NVIDIA.  Before I could install Ubuntu, I had to force the graphics into "fixed mode" via a setting in the BIOS.  Then I ran the "Additional Drivers" application, and it installed the ATI proprietary driver.

However if you want to retain Windows and set up a "dual-boot" arrangement, you're in for a bumpy ride.  HP uses all four primary disk partitions leaving no place to install Linux.  (I sometimes wonder if that's exactly why they use all four partitions rather than an extended one, but perhaps that's just paranoia.)  I posted the steps I used to deal with this problem and install Ubuntu at: [http://ubuntuforums.org/showthread.php?t=1852213&p=11299287#post11299287](http://ubuntuforums.org/showthread.php?t=1852213&p=11299287#post11299287).

There will never be support for the fingerprint reader; if that's a deal-breaker, you should probably stick to Windows.  I don't care about Beats Audio since I have the machine connected directly to my home audio system.  However you [should not expect to see support for Beats]("http://www.linux.org/threads/beats-audio-on-linux.4443/") in Linux either.  There is a workaround described in that posting, but it appears pretty complex.

I would suggest replacing the Broadcom card, but HP's BIOS will not boot any machine whose parts are not listed in the product's service manual.  To see what your options may be, take a look at [http://h30434.www3.hp.com/t5/Wireless-Internet-Home-Networking/want-to-replace-the-faulty-wireless-card-in-dv6/m-p/876945#M18567](http://h30434.www3.hp.com/t5/Wireless-Internet-Home-Networking/want-to-replace-the-faulty-wireless-card-in-dv6/m-p/876945#M18567).  If I were you, I'd look into replacing the Broadcom with a Centrino like I have in this machine.  Mine reports its identity as "Centrino Wireless-N 1000 [Condor Peak]."

The other option is to buy a USB wifi adapter and disable the onboard Broadcom.  The tiny [Edimax](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091) device works in 14.04.  Running tests at speedtest.net shows the Edimax is considerably slower on downloads (~17 Mbit/sec) than the Centrino (~50 Mbit/sec), but I have a big pipe from Verizon Fios. The Centrino is faster uploading as well, but the difference is much smaller.

The one item I pay the most attention to when buying laptops is the wifi card.  I always choose Intel adapters if they are available because they have had reliable support for well over a decade.  The drivers themselves are [open-source]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm").

---

