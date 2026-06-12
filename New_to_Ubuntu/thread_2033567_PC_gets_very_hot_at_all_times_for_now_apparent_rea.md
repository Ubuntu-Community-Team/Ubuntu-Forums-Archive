---
title: "PC gets very hot at all times for now apparent reason"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by frodetb on 2012-07-26
Hello. I am an utter newb when it comes to linux, so I just hope that you'll have some patience with my rambling. I just don't know what you'll need to know.

I have been trying to migrate from Windows to Ubuntu for some time now, via wubi and dual booting, but there is always something that scares me away. There is always one or two problems too many. I have one major problem, which has always been there, and its cause is hopeless for me to pinpoint on my own. My computer runs extremely warm almost immediately after booting, and bacause of this the fan can be heard at full speed at all times.

I come to the ubuntu boards because this is a problem that I do not have when booting into Windows 7. Since this only occurs when using Ubuntu, I'm guessing the problem lies here somewhere.

I own a HP Pavilion dv7, and though I don't know much about the components inside, I guess can find out more if you tell me how. I know I have a AMD Phenom II P960 Quad-Core processor, which is my main suspect for the ungodly temperature, but then again my thoughts here might not be wourth much.

---

### Post by Mark Phelps on 2012-07-26
Is it extremely warm under BOTH Windows and Ubuntu? Or, is it only warm when running Ubuntu?

If it's warm under both and is (I presume) a laptop, then it's likely that there is gunk that is impeding airflow through the fan.  You direct one of the cans of compressed air into the fan exhaust port to clean that out a bit.

If it's only hot under Ubuntu, that is most likely due to a known bug with the recent kernel versions that has not yet been fixed.

You can read the link below about installing Jupiter: 

[http://ubuntuforums.org/showthread.php?t=1854019]("http://ubuntuforums.org/showthread.php?t=1854019")

---

### Post by d4m1r on 2012-07-26
Please provide the full specs of the machine, the HP DV7 is not a full model number.

My guess is a fan controller driver is missing under Ubuntu so heat is not being dissipated like it is under Windows 7...Also, try listening to the laptop through the boot and login process when going into Windows 7, and then do it again going into Ubuntu, does everything sound the same? Is Windows 7 boot louder?

---

### Post by sid0972 on 2012-07-26
it may be possible that you havent installed the additional drivers, the video drivers, because of which your CPU is responsible for the display, causing it to run hotter than under windows

---

### Post by frodetb on 2012-07-27
> **d4m1r said:**
> Please provide the full specs of the machine, the HP DV7 is not a full model number.

I just downloaded Speccy in windows, and this is what it had to say:

Operating System
	MS Windows 7 Home Premium 64-bit

CPU
	AMD Phenom II P960	66 °C
	Caspian 45nm Technology

RAM
	8,00 GB Dual-Channel DDR3 @ 532MHz (7-7-7-20)

Motherboard
	Hewlett-Packard 164E (Socket S1G4)	66 °C

Graphics
	Generic PnP Monitor (1600x900@60Hz)
	AMD M880G with ATI Mobility Radeon HD 4250 (HP)
	AMD Radeon HD 6650M (HP)	68 °C
	Cross Display Enabled
	CrossFire Disabled

Hard Drives
	932GB TOSHIBA TOSHIBA MK1059GSM ATA Device (SATA)

Optical Drives
	hp CDDVDW TS-L633R ATA Device

Audio
	IDT High Definition Audio CODEC

---

### Post by frodetb on 2012-07-27
> **sid0972 said:**
> it may be possible that you havent installed the additional drivers, the video drivers, because of which your CPU is responsible for the display, causing it to run hotter than under windows

How do I install them? Do I just search for my the name of my graphics card in the Software Center?

---

### Post by miguelpires on 2012-07-27
> **frodetb said:**
> How do I install them? Do I just search for my the name of my graphics card in the Software Center?

Have you try to see in Jockey if you have aditional drivers to install?

---

### Post by frodetb on 2012-07-27
> **Mark Phelps said:**
> Is it extremely warm under BOTH Windows and Ubuntu? Or, is it only warm when running Ubuntu?

If it's warm under both and is (I presume) a laptop, then it's likely that there is gunk that is impeding airflow through the fan.  You direct one of the cans of compressed air into the fan exhaust port to clean that out a bit.

If it's only hot under Ubuntu, that is most likely due to a known bug with the recent kernel versions that has not yet been fixed.

You can read the link below about installing Jupiter: 

[http://ubuntuforums.org/showthread.php?t=1854019]("http://ubuntuforums.org/showthread.php?t=1854019")

As I mentioned, It only gets that hot for no reason when I run Ubuntu. When using Windows, it takes longer for the fan to even start, and even then it isn't nearly as warm. The fan starts running sooner and louder in Ubuntu than in Windows.

---

### Post by frodetb on 2012-07-27
> **miguelpires said:**
> Have you try to see in Jockey if you have aditional drivers to install?

What is Jockey? I suspect this is something everyone should know, but I am absolutely new to this.

---

### Post by miguelpires on 2012-07-27
> **frodetb said:**
> As I mentioned, It only gets that hot for no reason when I run Ubuntu. When using Windows, it takes longer for the fan to even start, and even then it isn't nearly as warm. The fan starts running sooner and louder in Ubuntu than in Windows.

Install Jupiter. I've the same problems with my Toshiba and with my Alienware. Jupiter solve the problems. Aditional try to see if you need aditional drivers with Jockey.

---

### Post by miguelpires on 2012-07-27
> **frodetb said:**
> What is Jockey? I suspect this is something everyone should know, but I am absolutely new to this.

In the dash type jockey (aditional drivers) open the aplication and the aplication going to show you if are any aditional drivers to your machine. If yes install them.

Something like this image:

---

### Post by frodetb on 2012-07-27
> **miguelpires said:**
> Have you try to see in Jockey if you have aditional drivers to install?

I just booted ubuntu, searched for jockey in the app-tray, and found the Additional Drivers application. Turns out you were right, and there was an uninstalled graphics card driver. I hopw this works. If it doesn't I will download Jupiter like the other guy recommended.

---

### Post by frodetb on 2012-07-27
I just tried installing the driver, but at the end it just jaid

"Sorry, installation of this driver failed.

Please have a look at the log files for details: /var/log/jockey.log"

Okay, so now what do I do?

---

### Post by miguelpires on 2012-07-27
> **frodetb said:**
> I just booted ubuntu, searched for jockey in the app-tray, and found the Additional Drivers application. Turns out you were right, and there was an uninstalled graphics card driver. I hopw this works. If it doesn't I will download Jupiter like the other guy recommended.

In my humeble opinion you should install jupiter.  Another good reason is the whay batery is manage, and that is very important in laptops to....

You may be interested in see this:

[http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html](http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html)

---

### Post by miguelpires on 2012-07-27
> **frodetb said:**
> I just tried installing the driver, but at the end it just jaid

"Sorry, installation of this driver failed.

Please have a look at the log files for details: /var/log/jockey.log"

Okay, so now what do I do?

Can you please post the jockey.log to us to see what's wrong?

---

### Post by sid0972 on 2012-07-27
i think there is a driver conflict between your dedicated card and onboard, and the display is being controlled by onboard chipset, a not by your dedicated GPU

But in windows you have the drivers installed, which is why it runs cool
i know this is based on the theory that if onboard is used pc runs hotter, but in my opinion this is most likely

i dont know yet how to solve this issue, but let me get back to you after some googling

---

### Post by QIII on 2012-07-27
Jockey sometimes simply does not work and the driver fails to install.

With your hybrid graphics, it would be easiest just to install from the command line from the repo.  The graphics chips are designed to run with the proprietary driver.  I like the open source driver and recommend that as the best first option.  vga_switcheroo, which can only be used with the open source Radeon driver, may (or may not) work for switching between integrated and discrete.

But when it comes to overheating, the proprietary driver is simply the best solution.

See the ATI driver wiki in my signature.  In the table of contents, click "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)"

When you get to the part about initialization, be sure to use
```
sudo aticonfig --adapter=all --initial
```If you don't want hardware acceleration (item 8 in the instructions), you can skip item 8.

When you are all done and have finally rebooted, the Catalyst Control Center should give you the option to switch between the integrated and discrete graphics.  You will have to change the setting and then log out and back in.  Sometimes users report that a reboot is necessary.  The switch does not occur dynamically with the Linux driver as it does when you go from battery to power adapter in Windows.

I have only been able to test this on one machine personally and it worked as expected.

Your mileage may vary.  But PLEASE report back with your results because I edit the wiki as often as I get users' experience.

Although the lastest proprietary driver (12.6 at this time) can be installed as instructed in the wiki, I recommend the repo for newer users because the manual install requires reinstallation whenever your normal updates update or replace the kernel.  Seasoned users generally like to keep up with the latest driver and don't mind that.

---

