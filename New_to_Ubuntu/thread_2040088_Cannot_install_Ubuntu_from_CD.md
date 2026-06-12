---
title: "Cannot install Ubuntu from CD"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by intoutdoor on 2012-08-10
Hi guys, this is my first time attempting to install any linux distro. I have the iso on the cd, and have changed my BIOS to boot from the CD first, when I turn on the computer, it goes to the ASUS screen, the goes black with a blinking cursor for about 45 seconds (it seems like it wants to boot) then it just boots Windows.  I would greatly appreciate any ideas as to a possible solution.

Thank you very much

---

### Post by chadk5utc on 2012-08-10
when you say you have the ISO on CD did you burn image to disk? or simply burn the ISO to disk? when you load the CD in another computer what happens? does it load?

---

### Post by Moif_Murphy on 2012-08-10
I'm guessing the computer isn't recognising that the CD is bootable. I'd recommend using something like Imgburn to burn the ISO.
 
Or try a different brand of CD?

---

### Post by drmrgd on 2012-08-10
Would you mind also providing a little more information about the version of the .iso you downloaded (32-it or 64-bit), your system specs in terms of architecture, and your hard drives (1 drive or two, is Windows already loaded on the drive(s))?  Finally do you happen to know if the system is currently set up as UEFI or BIOS?

---

### Post by HoCo xXSamXx on 2012-08-10
I agree with the above. You probably need to burn the ISO properly. I use MagicISO

---

### Post by marlow59 on 2012-08-10
After you check that the image is properly burned to the cd, reboot your computer and when you see the ASUS Logo type F2 (or F4,  try both alternatively) then you will be on your BIOS menu, go to the 3rd tab, and change the boot order to put the cd at the top, then type F10 to save and reboot.

---

### Post by duckslems on 2012-08-10
After you've changed the BIOS option 'Boot from CD', the booting CD must be in CD-ROM of your ASUS PC.

---

### Post by johnathansmith on 2012-08-10
Sometime even if you choose boot from cdrom first, you have to before you OS loaded press F2-F12 (depend which one bring you the boot option menu) and select boot from cd manually.

---

### Post by intoutdoor on 2012-08-10
Hi, thanks for the quick response. I downloaded the 64 bit version. The computer has windows 7 currently installed on one of 2 drives. My machine has 4gig ram, and I believe I set it up as UEFI (though I'm not sure what that means, that seemed like the only option whilst in BIOS to get it to boot from the CD?). 

Thank you, I didn't expect so much feedback so quickly, I'm going to try to load manually and try downloading again. Though I'm a bit confused when you mention the ISO or the ISO image; I simply downloaded Ubuntu from the website (64 bit) then downloaded Cyberlink Power to go, when I opened that program, Ubuntu was already loaded in it, and I just hit "Burn"

---

### Post by Egonosaur on 2012-08-10
Hello there!

I think I had a similar problem when I installed ubuntu on my laptop, I burned it from another laptop with windows vista.
I think I downloaded a program for just burning ISO images, then I burned the ISO image on the CD, and I read somewhere that if you burn with the lowest possible speed, you minimize risks of corrupt data.

---

### Post by intoutdoor on 2012-08-10
Ok. Thanks Ergo, I appreciate it, I will give that a shot. I just figured that all burners were created equal, apparently not.  My BIOS is very strange, as for the boot options, #1 is labeled "BD Slim followed by a bunch of numbers" option 2 is Pfollowed by a bunch of numbers. I believe BD Slim is the CD drive. I will get a dedicated ISO burner and try again.

Thank you all, you've been incredibly helpful.

---

### Post by westcoast01 on 2012-08-10
Howdy, go to the Ubuntu home page and read the directions on how to make a ISO image to CD, (I have better luck using a flash drive). Pretty straight forward ... [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) ...  You are correct to change the bios to "boot from cd" but I also need to 'enable' the device on any of my Asus products. While this might not pertain to you while changing the boot order check to see what is enabled or disabled. Don't forget if you do changes you might need to re-enable your hdd after install. Hope this helps, best of luck. PS. Make sure your machine is capable of 64 bit.

---

