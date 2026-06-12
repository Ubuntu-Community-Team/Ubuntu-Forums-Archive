---
title: "[SOLVED] Wireless &amp;amp; VGA solution."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by liquerLOVER on 2008-06-07
:)Actually, this is a guide for Aspire 4520 laptop. Since a lot of people having problems with wireless (especially AR 5007EG) & graphic card, so I just post this to SHARE how I settle both of the problems. I'm a total newbie so forgive me if I have make any mistake.

My Acer Aspire 4520 only have problem with wireless (AR 5007EG) & screen resolution stuck at 800x600 (GeForce 7000m) on Hardy Heron 32-bit. So, here what I had done to settle all those problems:

For wireless, with this kind of installation, you doesn't need to connected to internet. Just download the “madwifi” file from any computer. Since my only way to connected to internet is only with Wi-Fi, I have to go to cyber cafe to download the “madwifi” & install it manually in my laptop. Just after I settle my wireless, then i'm able to connect to internet with my wireless & settle my graphic card. For graphic card, you must connected to internet.

Wireless:

First, download this madwifi from this link:

[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

Secondly, extract it to your home folder. (just copy the “madwifi” file to your home folder & extract it there.

Third, you need to add your install CD as an installation source. Just follow the instruction below:

System – Administration - Synaptic Package Manager – Settings – Repositories - Third Party Software - Add CD-ROM.

Next, just wait for a few minutes until the package manager have finish working. You will notice a grey colour "gear" beside the wireless network symbol on the top panel when it still working. If you place the cursor on that gear, it will saying "a package manager is working." After the package manager had finish, it will disappear automatically.

For the next step:

sudo apt-get install g++

Then, it will ask conformation from you to install or not. Just type "y" and press enter.

Next step:

cd madwifi-nr-r3366+ar5007/
sudo make
sudo make install

After that, reboot and PRESTO !!!

However, you will notice that the wireless LED are not functioning. Beside, you must make “iwconfig”, “ifconfig” & “sudo modprobe ath_pci” before you can detect & connect to a wireless network. I don’t even at all know why because i’m a TOTAL NEWBIE to Linux. I'm not too sure whether this work for other laptop with AR5007EG or other AR5007. It don't bother me because as long as my laptop can detect & connect to internet with wireless, it's okay. However, I hope I can settle it because sometimes I wish I can go for wireless without typing this & that in terminals. Anyway, there is some post & treads that I read twhich is able to settle the LED. Check it out by yourself. If some of you can settle the LED, just reply & teach me. Okay???


For next step, you need an internet connection to do the update & to install the graphic card. When I connected to internet, I update my Ubuntu with “Update Manager”. So, here it is: 

System – Administration – Update Manager – Check – Install Updates

After have finish your update, restart again. I read in some other threads & post that restarting after update is vital. So, as a newbie, I just follow since the one who post the treads is an experienced Linux user. Just after I updated my Ubuntu, I settle my graphic card. I don’t know whether you can install your Nvidia driver before you update your Ubuntu. Maybe you can try it on your own. So... this is how I settle my graphic card.

First step, enable the restricted Nvidia driver:

System - Administration - Hardware Drivers - Enable the "Nvidia accelerated graphics driver (latest cards)"

After you enable the driver, it SHOULD automatically download the Nvidia & install it. After install, it will request for restart.

Next step, restart your laptop & your Ubuntu SHOULD come out with 1280x800 resolution. 

Some other laptop or PC may work with this installation but it doesn't change the resolution automatically. So, this mean you have to adjust the resolution manually. So, here it is...

System – Preferences – Main Menu – Other (click on it) – Enable Screen & Graphics.

Applications – Other – Screen & Resolution – Adjust by selecting your monitor model, manufacturer, size, & resolution.

I think this may settle other laptop (with Nvidia driver). If this works, BRAVO. I took about a month  to settle all this problem. Too long isn't it but like I told you just now, i'm a TOTAL NEWBIE to Linux.

Ha!!! Almost forget. For my laptop, just after I install my Nvidia, my laptop can't detect or connect any wireless. So, u have to install your wireless again. Here it is again:

cd madwifi-nr-r3366+ar5007/
sudo make
sudo make install

After that, reboot and your wireless functioning like before including the not-functioning LED. Don't ask me why this happen because like I told you, i'm a TOTAL NEWBIE in Linux. Maybe you can ask other experienced Linux user in this forum.

Chowlobetty...

---

