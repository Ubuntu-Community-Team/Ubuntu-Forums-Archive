---
title: "Ubuntu Laptop installation Help"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by novi2 on 2013-09-05
hi, 
I'm new here. I've purchased  a Lenovo thikpad E431 (i5 3230m, 2.6 GHz, 2gb Ram, 500gb HDD) laptop without an OS. I purchased this laptop because its user friendly track pad, keyboard and its giving 5-6 hours battery backup.Currently I'm using windows 7. I'm planning to install ubuntu as my primary OS. I did search in lenovo site for Linux drivers, but drivers are not available. Is it possible to install Ubuntu without any driver software and Will trackpad work perfectly? 

(sorry for my poor English)

Thanks in advance
 Novi

---

### Post by claracc on 2013-09-05
You can try ubuntu in your laptop without installing by running the live ubuntu CD: [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD). In the link provided, there are the details for booting from live CD without installing.

In this way, you can see if your trackpad works with the default ubuntu drivers

---

### Post by r_avital on 2013-09-05
Hi, and welcome,

Most of the time, drivers are not an issue in Ubuntu, but there are always exceptions.  One possible issue would be video drivers.  There will be a pretty good generic driver in your installation of Ubuntu, and once Ubuntu is running, you can install different video drivers according to your needs.  Those are proprietary drivers -- what that means is that the developers of Ubuntu have no access to the source-code and cannot fix bugs, but if they are provided, they will come with a clear indication that they have been tested by the Ubuntu developers.

As for your trackpad, it should work.  "Perfectly?" That gets into specific features and functionality that you might have to troubleshoot, but basic trackpad functionality should work ok (I have an HP laptop, not a Lenovo, my trackpad worked as soon as Ubuntu -- older version -- was installed, so if you install 13.04 or 13.10, chances are your trackpad should work fine).

If you have any trouble with video, trackpad, mouse, Wi-Fi, etc., there are hardware-specific forums here where you can find help to address such issues.

As mentioned above, you can try Ubuntu before you install it.  If you're planning to dual-boot, please make sure you follow this guide for a successful installation:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Good luck, and let us know.

---

### Post by oldrocker99 on 2013-09-05
Re: drivers in Linux

I have only had two instances when I **had** to download and install drivers for a GNU/Linux installation: (1) graphics card drivers (obviously), and (2) 4 years ago, when I had a Broadcom wireless chip in a laptop, for which I had to download specific drivers. The Broadcom drivers were added in a later kernel. In five plus years of of using GNU/Linux, those have honestly been the only times I have ever had to install extra drivers.

---

### Post by novi2 on 2013-09-06
hi R_Avital,


Thank you for the reply. I've  tried the live boot option and Ubuntu 13.04(i386) is running without any problem. But trackpad's full features aren't available, right click isn't working. Is there any driver available for my machine (Thinkpad E431, i5 2.4GHz 3230m)? I've searched in google, no result. If the driver is avaiable, please let me know. Anyway Ubuntu  is  faster than windows.



Thanks.

---

### Post by grahammechanical on 2013-09-06
In the live session you can install drivers but they will only be available during the live session. But at least you can find out if there are drviers available. Open System Settings. You should see a cog wheel and spanner icon on the Launcher (left side panel). With System Settings open go to Spftware and Updates and open the Additional Drivers tab. You will see additional video drivers but you may also see a driver for the trackpad. Who knows. It is worth a try.

By the way Ubuntu i386 is a 32bit version of Ubuntu. Does your machine have a 64bit CPU. You might want to install Ubuntu 64bit. It is called amd64 and it will run on Intel CPUs. I am running Ubuntu amd64 on an Intel Core 2 Duo.

Regards.

---

### Post by Besmir_Zekaj on 2013-09-06
To install Ubuntu 13.04 in your Lenovo laptop u must select (OEM install) for manufacturers.

[IMG]https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview?action=AttachFile&do=get&target=oem000.png[/IMG]

Wait for the installation process to finish.

[IMG]https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview?action=AttachFile&do=get&target=oem006a.png[/IMG]

Now you can install addition software, drivers or configure the system as desired. When you're done doing that click on the **Prepare for shipping to end user** icon on the desktop.

[IMG]https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview?action=AttachFile&do=get&target=oem007a.png[/IMG]

Once the computer was shipped to the end user and he finnaly boots for  the first time he will be taken to the system setup wizard where he will  be able to set his location, keyboard layout, user name etc.
And then the ubuntu must be installed. Best Regards
Zekaj Developer

---

### Post by Pepe Lebuntu on 2013-09-27
Hi there,



I'm also getting a  Thinkpad E431 (not the touch version, by the way), and noticed that on  Ubuntu's certification hardware page, there's an option (somewhere in  the world) to get Ubuntu pre-installed. I'm in Australia, and that's  never going to happen. So that leaves me with two questions:


[LIST=1]
[*]Is  there any way I can get the certified Ubuntu version for the E431? Is  it available on a lenovo support site anywhere, for example?
[*]Do I need the the certified version, or will the regular Ubuntu version work fine out of the box?
[/LIST]
Any help you could give me would be much appreciated.

---

### Post by mastablasta on 2013-09-27
> **Pepe Lebuntu said:**
> Hi there,



I'm also getting a Thinkpad E431 (not the touch version, by the way), and noticed that on Ubuntu's certification hardware page, there's an option (somewhere in the world) to get Ubuntu pre-installed. I'm in Australia, and that's never going to happen. So that leaves me with two questions:


[LIST=1]
[*]Is there any way I can get the certified Ubuntu version for the E431? Is it available on a lenovo support site anywhere, for example?
[*]Do I need the the certified version, or will the regular Ubuntu version work fine out of the box?
[/LIST]
Any help you could give me would be much appreciated.

1. no.
2. certified means if you install the version, it will work out of the box.instalation is easy and has only a few steps (such as selecting username, password, keyboard and time zone).

maybe they have it in Indonesia.

---

### Post by arai on 2013-09-27
I have been using ubuntu in lenovo for more than a year. Trackpad works much better in Ubuntu than in Windows 8 for me.

---

### Post by sebastianrimbaud on 2013-09-27
I juste received the Thinkpad E431 and have Ubuntu 12.04 install on it. I'm also looking for some tips on working the right-click function. I've managed to make it work a couple of times, but it's very frustrating and not working consistently. I'm not experienced with using the ThinkPad mouse-pad, but I feel that the right-click should be much easier and wonder if its a hardware issue or just me. Anyone have suggestions or fixes for this? I use the right-click function for work and it's been pretty annoying trying to figure it out.

---

### Post by Suplab_Debnath on 2014-08-19
Sorry for posting in an old thread, but any of the e431 users facing battery drain (I mean faster than expected)? Have you guys installed the proprietory graphics drivers? for the

---

### Post by Joo_Costa on 2014-08-19
I had the same problem but with this computer ( [http://www.clickplus.pt/p69416](http://www.clickplus.pt/p69416) ) the second solution from claracc worked fine :) thank you

---

