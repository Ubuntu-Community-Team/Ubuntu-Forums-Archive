---
title: "Failed boot"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by tburntburn on 2011-10-14
Hi all, 
Just installed Ubuntu desktop 11.10 32bit.
Installation went fine from live usb.
But when booting from harddrive it stopped at 
 
"Stopping userspace bootsplash" [Failed]
 
but then i re-installed and now it stops at
"Checking battery state [Ok]"
 
when it stops nothing happens. Ive left it for half an hour but nothing.
 
Any ideas? 
I'm a ubuntu noob i'm afraid but any ideas would be great!!
 
Thanks all

---

### Post by tburntburn on 2011-10-14
[*Bump*]
 
No one have any ideas?
 
I appreciate any ideas anyone has.
 
Thanks again

---

### Post by TeoBigusGeekus on 2011-10-14
After you boot the usb, have you checked it for defects? (It's an option alongside Install, Try, etc.)

---

### Post by WasMeHere on 2011-10-14
Hi tburntburn,

I recently posted the following thread 
[[COLOR="RoyalBlue"]_Welcome newcomer, start with a stable version_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859702")
to help avoid problems with a brand new version of Ubuntu. So I suggest that you download Ubuntu 10.04 LTS and make a boot CD or USB drive. If you want advice about which flavour to select, please reply with information about

- how you intend to use your computer
- hardware specification

Have fun finding out :-)
Olle

---

### Post by tburntburn on 2011-10-14
> **TeoBigusGeekus said:**
> After you boot the usb, have you checked it for defects? (It's an option alongside Install, Try, etc.)
 
Hi, 
could you remind me where that is please? i'll check later as am away from my laptop at the mo. (As far as i remember when installing i only had the two large options of try and install.

---

### Post by TeoBigusGeekus on 2011-10-14
It should be under the Try and Install options; something like "check installation medium for defects".

---

### Post by tburntburn on 2011-10-14
> **TeoBigusGeekus said:**
> It should be under the Try and Install options; something like "check installation medium for defects".
 
Ah ok. i'll check later this afternon. (Perhaps after i've had a go on Forza 4 though!!)
Thanks.

---

### Post by tburntburn on 2011-10-14
> **Olle Wiklund said:**
>  If you want advice about which flavour to select, please reply with information about
 
- how you intend to use your computer
- hardware specification

 
 
I'm familliar with ubuntu's gui but windows is my main os so i don't use ubuntu much. (I like using it simply because it's a really nice place to be, as opposed to it being functional, lack of ms office (libre office looks like office 95), sibelius and cubase etc.)
 
I love 11.10 though!! It looks so smart when i run it from usb!!:P
 
For this reason i am reluctant to go back to 10.04 LTS, that is a much less friendly place to be.

---

### Post by tburntburn on 2011-10-14
> **TeoBigusGeekus said:**
> It should be under the Try and Install options; something like "check installation medium for defects".
Hi, I had a look and there is no option to check for defects. just the option to try or install it.

Have i downloadesd the wrong one??

---

### Post by ru2044 on 2011-10-14
Hi,
I, ve got the same problem with 64bit version. I've got AMD APU 3850 (with Radeon 6550D integrated). After switchinh on my computer everything ends on "checking battery state" and "starting automatic crash report generation" is failed.
I had to cope with 'nomodeset' problem, but I got through it
This is my last chance for solution...

---

### Post by WasMeHere on 2011-10-14
One important step is to check the md5sum of the downloaded iso file. Use the appropriate file name
```
md5sum filename.iso
```
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/UbuntuHashes_[/COLOR]]("https://help.ubuntu.com/community/UbuntuHashes")
and for Oneiric
[[COLOR="RoyalBlue"]*http://releases.ubuntu.com/**oneiric**/*[/COLOR]]("http://releases.ubuntu.com/oneiric/")

---

### Post by cryptotheslow on 2011-10-14
Also check the install media (CD or USB) for defects once you have made it.

As you boot up from the CD / USB as soon as you see the white line of text appear at the top of the screen starting with ISOLINUX........ then hit the left Shift key. This will drop you to a prompt with just "boot:" and a blinking cursor. Wait a few seconds or hit return and you should be presented a language selection menu - so use the cursor keys to select the appropriate one.

Then hit F6 for "Other Options" - which will popup another menu - one of the options there is "Check Media For Defects" (or words to that effect). Let that do it's thing and it will tell you whether the disk / USB is good or not.

Can take a few attempts to get that Shift key hit at the exact right time on a fast booting machine.... so if you end up at the desktop, you've gone to far and will need to restart and try again :D

---

