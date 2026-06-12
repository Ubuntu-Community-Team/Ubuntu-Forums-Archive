---
title: "brother hl2230 driver for ubuntu or kubuntu"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by stoobers on 2012-08-10
I couldn't find any step-by-step instruction for installing the brother printer drivers for the brother hl2230
So... once I figured out how to install the driver, I thought I would create this howto.

Look over these steps.  Don't run anything you don't understand.  I have Ubuntu 10.04.4 LTS installed, then I added kubuntu on top, because I prefer kde.  So the steps about the menu and how to find the config are in kde, not gnome.

------------------------------

#this page shows Brother hl 2230 is supported by ubuntu 10.02 lts
#[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html)
#this page shows Brother hl 2230 has a few steps to run before it will cooperate.
#[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html)
#[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

#i have to run these things multiple times to get rid of errors...
sudo apt-get update
sudo apt-get update
sudo apt-get upgrade
#wait an hour...
#reboot computer
sudo apt-get update
sudo apt-get update
sudo apt-get upgrade #this will do little, so that means upgrade worked.

sudo aa-complain cupsd #this is from the brother site.
sudo mkdir /usr/share/cups/model #also from brother site.

#here is where i download the drivers in firefox
#[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2230](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2230)
#then you download BOTH 'LPR driver' and 'cupswrapper driver' .deb's


#go to the download directory and run this command from the download directory
sudo dpkg -i --force-all ./hl2230lpr-2.1.0-1.i386.deb
sudo dpkg -i --force-all ./cupswrapperHL2230-2.0.4-2.i386.deb
#run this to make sure BOTH drivers installed:
sudo dpkg -l | grep Brother

#if you are an American
#start -> system settings -> printer configuration -> local printers -> HL2230 -> options -> media size -> letter
#media size -> toner save -> on
#HL2230 -> job options -> media -> na_letter_8.5x11in

#if you make any changes in this setup, be sure to click 'apply' at the bottom right!!!

#make this the default printer, if you want.
#start -> system settings -> printer configuration -> local printers -> HL2230 -> check 'this is the default printer'
#now test the printer
#HL2230 -> settings -> print test page

#I hope this helps someone out!

---

### Post by pdc on 2012-08-11
very good; very helpful

Brother released an install tool 

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

that should automate the procedure for folks as an alternative

---

