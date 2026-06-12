---
title: "Issue booting live image on Lenovo Miix320 x5"
date: 2018-05-05
forum: New to Ubuntu
---

### Post by unix1adm on 2018-05-05
Hi All, 

I am sort of new to Ubuntu. But not new to Linux. 
I had Ubuntu 10.x a long time ago and have been working in CentOS/Red Hat for a while. 

So one quick question about this site. Is there a reason Firefox does not work with it? I had to use IE on windows box to be able to post. Just wondering. Some of the buttons are missing etc. 


On to my question:

I have a Lenovo Miix 320 running Windows 10. Hate windows 10. Want to put Linux on this machine. 
This is a 2 in 1 device and a touch screen. 
4G memory and 128 Internal drive with 48G of that taken up by windows 10. 

I followed these to links to build a bootable UEFI USB stick. 

[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#4](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#4)
[https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
[https://ubuntuforums.org/showthread.php?t=2342097](https://ubuntuforums.org/showthread.php?t=2342097)

The USB works on my Lenovo  R61 laptop. So I know it is a good image. 

When I tried to boot the 2 in 1 device it takes a very long time. I get the option to run from the USB or install. I select run from the USB. 

Ubuntu logo goes on the screen but then the screen goes blank and the machine never comes up in the Ubuntu OS. 

The USB has a light on it showing it was accessed but nothing happens. 


Any ideas what could be going wrong? 

Will Ubuntu support the touch screen and tablet mode etc? 
Can I put Ubuntu on and keep the Windows 10 image too? 

Thank you in advance for your help. 

CJ

---

### Post by unix1adm on 2018-05-07
[ATTACH=CONFIG]279611[/ATTACH]After several tries I managed to get this out of the system.

Sorry it is a bit blury. My phone camera is not th best any more. Don't know if it will help or not.

---

### Post by dino99 on 2018-05-07
'blank screen' : which graphic driver is installed / used ? for which chipset/card ?
Also glance at 'errors' (red lines) & 'warnings' (bright lines) from 'journalctl -b' you can grab from a terminal

---

### Post by unix1adm on 2018-05-07
No sorry the device does not respond. screen goes black. 
you can do nothing with it to get any information out of it.

---

### Post by unix1adm on 2018-05-08
So I have tried Ubuntu and mint Linux with no success.

My device doesn't seem to want to boot.

See the attached screen shot I was finally able to get from it.

Also I followed these instruction. This guy did a nice write up for sure.

[https://esc.sh/blog/linux-on-lenovo-miix-320/](https://esc.sh/blog/linux-on-lenovo-miix-320/)

I have checked ont he Lenovo forums and they say this should all work. 

 

This is all it does.

---

### Post by unix1adm on 2018-05-08
So I decided to repartition my drive and do the install as the USB boot was not working.

Well the installer wont work either. Gets to a point then just hangs.

 

Ubuntu logo in the wrong orientation and I did add the :

set gfxpayload=keep

linux        /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash nomodeset i915.modeset=1 fbcon=rotate:1 ---

 

line to the boot. Just gets to a certain point and hangs on the logo.

USB is solid red light on it.




About to give up and send it back. Buy a dell. Good price on this but if it won't work it load Linux useless to me. 



At least costco give me 90 day to mess with it.

---

### Post by yancek on 2018-05-08
> linux        /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed  boot=casper quiet splash nomodeset i915.modeset=1 fbcon=rotate:1 ---


How exactly are you trying to boot your Ubuntu?  Are you booting the iso directly from another Linux with Grub2, some other method.  If you are using 18.04, the kernel is vmlinuz not vmlinuz.efi.

---

### Post by unix1adm on 2018-05-08
I downloaded the iso from ubuntu and put it on a USB stick the booted into BIOS and sdelected teh USB to boot. 

I followed the documentaiton in the link I listed above.
This system is running win 10 not any other Linux. 
i wanted to boot USB then Install Ubuntu on a partation on the internal ssd drive.

---

### Post by yancek on 2018-05-08
Did you verify the download from the Ubuntu site with either shasum or md5 checksum.  Are you able to test the usb on another computer.

---

### Post by unix1adm on 2018-05-09
From initial posting 

The USB works on my Lenovo R61 laptop. So I know it is a good image.

---

### Post by unix1adm on 2018-05-09
I tried this again after updating the bios
usb is blinking and Ubuntu logo is alternating red and white dots. 
I pressed fn 1 and got a screen. i was looking to see what it was doing but all it says is ... See screen shot.

This is more than i saw before.

---

### Post by unix1adm on 2018-05-12
Still no luck getting ANY Linux to run on this.

 

I was able to build my Lenovo R61 with Ubuntu just fine so I know the USB is good.

---

### Post by unix1adm on 2018-05-13
is there any way to get below the boot screen to see what is it doing or not doing? I tried all the F keys and nothing drops me into a command prompt to see what it hanging. 
All i ever see ind the sideways Ubuntu screen and 3 red and 2 white dots on it. 

This tells me nothing. 

I also tried this link but no luck. 

[https://askubuntu.com/questions/935657/how-to-install-ubuntu-on-miix-320](https://askubuntu.com/questions/935657/how-to-install-ubuntu-on-miix-320)

---

### Post by unix1adm on 2018-05-14
update. I was able to boot Xubuntu live usb. 

Thisis progress. 

now if I load Xubuntu can I load Ubuntu after the fact? 

I read it uses the same repos. but as i write this short lived joy. 

I just saw an error of "Sorry , Ubuntu 18.04 has experienced and internal error

a bunch of code 

executable path 
/lib/systemd/systemd-journald
package
systemd 237-ubuntu10
problem type 
crash

etc... 

no way to save the full file. 

But the laptop is still running.

sadly the lt crashed and kicked me out. locked the screen and rotated it. but at least it did boot.

update: 
I have a Lenovo Miix 320. I loaded xubuntu live usb. I am getting errors about this driver and then my system hangs/crashes. 
 axp288_fuel_gauge axp288_fuel_guage: driver failed to report `charge_now` property: -6
axp288_fuel_gauge axp288_fuel_guage: capacity measurement not valid
axp288_fuel_gauge axp288_fuel_guage: Error reg 0xe2 contents not valid

Keep repeating over and over. 
Is this something you can help with?

---

### Post by unix1adm on 2018-05-16
I tried a different download from daily and now see this screen error. 

really hoping to get this working soon as I need it for travel in the near future. Dont want to risk using windows and getting virus etc on unknown networks.

---

### Post by unix1adm on 2018-05-30
i see no one has ideas on this. I have been trying for about a month to get this to work like others have. 
About to give up on this device and just buy a laptop and load CentOS on it.

---

### Post by unix1adm on 2018-05-30
Well i tried to install the Xubuntu now , not just run it from the USB.

I get the power supply error message 1/2 way into the install. Wont power off do had to hold power button 20 sec to power down.

I have a feeling ill be sending this back and getting a dell.

Appears the latest code does not work on this device.
This has nothing to do with me not trying everything under the sun to get it to work.


Keeps erroring out with powerfupply akp288_fuel_gauge: driver failed to report 'charge now' property: -6
over and over. from what i read this is a bug. Dont know when or if it will ever be resolved.


update : Tried it again stuck on creating user for 1.5 hrs now. Me thinks its not working.

---

### Post by unix1adm on 2018-05-31
solution for me is to return this system and get a dell. Lenovo just wont support Linux for everything i have done.

---

