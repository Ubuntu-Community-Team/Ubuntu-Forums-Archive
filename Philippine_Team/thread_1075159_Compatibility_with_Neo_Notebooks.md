---
title: "Compatibility with Neo Notebooks"
date: 2009-02-20
forum: Philippine Team
---

### Post by randytan on 2009-02-20
Hi Guys and Gals!

Kumusta na?

My friend has a Neo Notebook M54SE that he would like to convert over to Ubuntu.

The thing is, he tried a dual boot first and when the program starts up, it freezes at the Ubuntu logo page with the status bar. Sometimes, it doesn't even reach there.

Is the hardware compatible with Ubuntu or is there something that is in conflict with it?

Tulong naman. Matagal na niya kasi gustong i-Ubuntu yung unit niya kaya lang marami siyang data. Now that it is all backed up, he tried installing Ubuntu with the results stated above.

Can anyone help us out?

If his installation is successful, we're planning on getting rid of windows in the office and all go Ubuntu!

Thanks.

Hope to hear from y'all again soon.

Best regards!

---

### Post by detorresrc on 2009-02-20
Pre try mo nga yung live CD kung pde.

---

### Post by loell on 2009-02-20
i think there are neo laptops that works out of the box with ubuntu, there are others though that needs tweaking.

as detorresrc suggested, try the live cd, with different options like safe graphics mode and also the verbose mode.

---

### Post by ragadanga63 on 2009-02-20
First make sure that you had an error-free download and a good burn.  Most problems of that nature is due to either error in downloading or in burning the liveCD.

---

### Post by killer_d76 on 2009-02-20
i had issues running live Ubuntu 8.10 cd on my friends Neo Laptop as well but when i tried running live cd of older version of ubuntu (well it was just the 8.04) and runs pretty well!.. ;)

---

### Post by randytan on 2009-02-21
Hi Guys!

He tried to go the live CD route but the thing freezes up on him before the whole thing loads as well. We just see video noise on the screen.

Before trying out Ubuntu, I should mention that his copy of windows xp was REALLY slow.

Could that have something to do with it?

He would really like to ditch xp and go Ubuntu just like me.

Once his is done, the rest of the office can follow. ;)

Keep them suggestions coming!

Thanks!

---

### Post by loell on 2009-02-21
tried searching the specs, it has 512 mb of ram?

so it's strange that even his xp is slow, di kaya may nagpalit nang memory? na di lang nalaman ng may-ari?

---

### Post by gimmejimmy on 2009-02-21
As others suggested above can you confirm that you have a good download and a good burn?  Sumakit ulo ko dati sa pag-install (sa desktop) yun pala bad burn.

---

### Post by dodimar on 2009-02-22
Check out the real specs of the system (use dxdiag of XP)... some NEO laptops doesn't contain the specs written on its papers..

had the same problem too with our church's laptop.. tried running the live cd but it freezes... even on xp it is slow... 

I checked out the specs and iba ang laman sa nakasulat... yun lang donated lang yung laptop (pero walang pinalitan kasi fresh yung screws..)..

---

### Post by randytan on 2009-02-22
Thanks for the input guys.

I'll try and get the specs from my friend and post them here for your review.

---

### Post by perbiu on 2009-08-03
I have a NEO laptop. Its cheap, you can have a full fast laptop (dual core, 2gib mem, 250gb hdd), where with that budget if you buy a branded one you will end up with just a small netbook. And NEO is a filipino company, even though its components are china made.

The freezing problem is caused by ACPI problems. Just press F6 on boot and F6 again to crossout the ACPI to acpi=off or noacpi. You also have to edit the grub to disable acpi permanently after installation.

---

### Post by Lila_IT_CMU on 2009-08-07
> **randytan said:**
> Thanks for the input guys.

I'll try and get the specs from my friend and post them here for your review.

I have NEO laptop. I have that problem when I first tried Ubuntu 8.10 

heres what I did:

Go to your BIOS then change the installed OS from **Vista or XP** to **LINUX** then save your new BIOS Settings then restart
Just read everything in your BIOS so that you can locate The "Installed OS"

It works on any Ubuntu version

---

### Post by perbiu on 2009-08-10
Compatibility of Ubuntu 9.04 on Neo Basic B2140-N

Everything important works after few configurations.

**Problem Encountered 1:** Boot up, Loading Bar Freezes/Hangup.
**Solution:** Add this line **nohz=off** while in boot grub menu selection  by pressing F6, press ESC to remove the pop up and just type ahead along the lines. Using **acpi=off noacpi** is overkill and will disable a lot of your laptop features such as battery duration/savings/ac adaptor, soft power button and also the Fn keys that access wireless activation, touchpad on/off, sleep, hibernation and brightness control.

If you add this line prior to installation, it will be permanently there. But if you already installed Ubuntu using **acpi=off** and **noacpi** instead, you have to edit your /boot/grub/menu.lst and remove those line **acpi=off noacpi** and replace it with the **nohz=off**

Other lines to add in case if the problem persist; this will also be helpful in other laptop models without killing the acpi: **nohz=off ide=nodma apm=off noresume nosmp maxcpus=0 edd=off**
I found this fix with Opensuse's Failsafe. It's failsafe option does not resort to acpi=off noacpi nolapic.

My basic laptop's BIOS is restricted, you can only edit the date&time and boot priority. So acpi problems cannot be fixed there.

**Problem Encountered 2:** Low resolution after installation
**Solution:** Download the driver here- SIS Mirage3 M-672[here]("http://www.zshare.net/download/63891757263e27ec/"), and install it, then restart Xserver when you log out or just reboot.

**Problem Encountered 3:** Fn volume controls and mute goes crazy when pressed. 
**Solution:** Reassign the Mute and volume +/- shortcut keys at System>Preferences>Keyboard Shortcuts. I reassign mine at ctrl +, -, 0(for mute).

The built-in Webcam, 4-in-1 Card Reader and Wi-Fi (Realtek RTL8187B Wireless 802.11g) works out of the box if activated. Audio works including the earphone transfer. Monitor-out works except the Monitor-out transfer so the laptop screen will remain on. You can install cheese in the Add/Remove to verify the Webcam is working.

**Problem Encountered 4:** The Wi-Fi Realtek RTL8187B can connect to the router but there is no internet connection.
**Solution:** You can go here for the fix [http://ubuntuforums.org/showthread.php?p=7798209#post7798209](http://ubuntuforums.org/showthread.php?p=7798209#post7798209)

Even though Neo laptops received a lot of bad comments in blogs, I really like mine. No OS included, they stated in their website that they put Linux on systems that do not have Windows pre-installed, this one has Freedos instead.

---

### Post by Script Warlock on 2009-08-10
im satisfied with my neo elan with U9.04 installed.....no headaches

hmm si perbiu tumatalas na sa ubuntu hah...nice:P

---

### Post by killer_d76 on 2009-08-10
***[SIZE="5"]Neo Empriva 531 CVS[/SIZE]***

(specs)
[B]
1.6 Ghz Intel Celerom M processor
512MB ram (upgraded mine to 2GB)
80GB HDD (upgraded to 160GB)
Broadcom wireless card
1.3 MP built-in webcam[/B]

[B][SIZE="5"][COLOR="Orange"]Ubunty Jaunty 9.04[/COLOR]
[/SIZE][/B]
**Everything works perfectly!**.. except for the **webcam** you need to install microdia-dkms.

> 

add this to your software source

[B]deb [http://ppa.launchpad.net/nickel62metal/ubuntu](http://ppa.launchpad.net/nickel62metal/ubuntu) jaunty main
[/B]
Install by:

sudo apt-get install microdia-dkms

as for the wireless card.. Jaunty will automatically detects the wireless card and you need to activate the driver.. but i recently found out that there was an issue with the Broadcom wireless, the reception was shortrange!.. but installing WICD fixed the issue.

> **sudo apt-get install wicd**

---

### Post by sieg06 on 2009-08-13
I've been using Neo M3S laptop with jaunty jackalope since its release last april. i didn't encounter any problem with jaunty. maybe the software you downloaded have the problem. my specs of my laptop is intel 1300 mhz with 1 gb ram.

---

### Post by bubwitmaingay on 2009-10-13
I have tried the LiveCD lately, but I haven't tested much of those things - webcam and wireless. Thanks for the reminder guys, I'll run a test again just to be sure. I'll dual-boot it anyway.

---

### Post by zeroseven0183 on 2009-11-11
Hi!

I have a friend that has a Neo B2230 notebook. He installed Ubuntu 9.10, worked very good except for the graphics. The resolution is only 800x600. We followed the instructions, downloading the xorg driver but to no avail.

Is there any way to correct this?

---

### Post by zeroseven0183 on 2009-11-11
Never mind. We were able to resolve this by installing a later version of the driver.
Thanks to **perbiu** for posting the link ([Screen Resolution thread]("http://ubuntuway.wordpress.com/2009/07/13/drivers-de-sis-771671-para-jaunty/")).

Now we have to find a way to enable the "effects". No drivers yet for the Cube or the wobbly window.

---

