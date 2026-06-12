---
title: "dual booting vista and ubuntu"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by gibson81 on 2008-08-06
I have been trying to dual boot vista and ubuntu and as far as I have gotten is I burned the disk i need and booted it and i got to this screen [http://www.justlookdifferent.com/wp-includes/images/postpics/Ubuntu%20screens/just_look_different_ubuntu_boot_menu.jpg]("http://www.justlookdifferent.com/wp-includes/images/postpics/Ubuntu%20screens/just_look_different_ubuntu_boot_menu.jpg") And when i try to select install ubuntu or any other option my cd drive starts and nothing happens, he only option that works is boot from local disk which starts vista. Any help?

---

### Post by overdrank on 2008-08-06
> **gibson81 said:**
> I have been trying to dual boot vista and ubuntu and as far as I have gotten is I burned the disk i need and booted it and i got to this screen [http://www.justlookdifferent.com/wp-includes/images/postpics/Ubuntu%20screens/just_look_different_ubuntu_boot_menu.jpg]("http://www.justlookdifferent.com/wp-includes/images/postpics/Ubuntu%20screens/just_look_different_ubuntu_boot_menu.jpg") And when i try to select install ubuntu or any other option my cd drive starts and nothing happens, he only option that works is boot from local disk which starts vista. Any help?

Hi and welcome, did you check the cd for errors, of does that option not work also
Then you may want to do a checksum on the iso
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
 this link I think may help 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by gibson81 on 2008-08-06
thank you, but im pretty new to this and im a little confused, do you think you could explain how to do the md5sum a little simpler

---

### Post by cgkades on 2008-08-06
> **gibson81 said:**
> thank you, but im pretty new to this and im a little confused, do you think you could explain how to do the md5sum a little simpler

Did you scroll down to the windows section?
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

---

### Post by gibson81 on 2008-08-06
woops didn't see that but, now i know the md5sums are different...:( anyway to change that or do i have to burn a new disk

---

### Post by overdrank on 2008-08-06
> **gibson81 said:**
> woops didn't see that but, now i know the md5sums are different...:( anyway to change that or do i have to burn a new disk

You will have to download the ISO from a different source I believe till you have a match on the iso before you burn.

---

### Post by gibson81 on 2008-08-06
*sigh* thank you..:(

---

### Post by gibson81 on 2008-08-06
I got the right iso and then i tried to burn a new one and had the same problem.

But when using  isorecorder it got 50% of the way through and popped up with the message "insert writable media or press cancel to stop" what am i supposed to do if it doesn't accept my disk?

---

### Post by gibson81 on 2008-08-06
bump- Need help please

---

### Post by Lazy-buntu on 2008-08-06
Hey. I multi-boot Vista, Ubuntu, and PCLOS 2008 Gnome. Here's what I did:

note: defrag your Windows Vista install multiple times before continuing

1. Inside Vista, click the menu button, right-click computer, and go to manage.

2. Go down to disk management and shrink your Windows Vista partition (to the size you would like)--say you shrink C: drive to 40GB, then the rest is unallocated

3. Boot into the live CD of Ubuntu

4. Install Ubuntu: Set up your partitioning MANUALLY, if you do automatic, chances are you will lose your Vista install

5. Create a 2GB Swap partition, and the rest of the unallocated space as ext3 (without touching your C:)

6. When setting up the bootloader (GRUB), install it only to the dev/sda2 (if this is you Ubuntu partition)

7. In Vista, google "EasyBCD" it should be by NeoSmart Technologies, download + install

8. Run EasyBCD, go to Add/Remove entries, go to add entry, click the Linux tab, pick you dev/sda2 (if that's your drive for ubuntu), and the entry

You can also rename the entries (from--NeoSmart Linux--to--Ubuntu)

Reboot your computer, you should see a black and white screen with two choices: Vista or Ubuntu

Pick Ubuntu, this will load GRUB, then hit enter again.

You should be ready to rock and roll :guitar:

---

### Post by Deep Biz on 2008-08-06
Hello Gibson81

 Looks to me that you are having problems downloading the Ubuntu ISO Image. Do this 

  1> Try downloading the ISO image from a computer with a faster net connection than yours, check the md5sums, burn the the image and try. 
   If this fails , you may resort to other methods of getting Ubuntu.

See here 
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Cheers !

Deep Biz

---

### Post by gibson81 on 2008-08-06
I've gotten past that, I downloaded the iso and checked the md5sums and they were correct.
Now, the isorecorder isn't working is their a different one i can use?

---

### Post by gibson81 on 2008-08-06
would i be able to create a bootable disk by using the ubuntu iso file and using the create disk from iso disk image file?

---

### Post by dhughes on 2008-08-06
> **gibson81 said:**
> would i be able to create a bootable disk by using the ubuntu iso file and using the create disk from iso disk image file?

 Using what, a Vista disc burning application? I've never used Vista so I can't really say. If it makes a bootable iso disc I'd say sure give it a try.

 Alex Feinman's ISO Recorder Version 3 (for Vista) is pretty good I'm surprised it failed on you, did you download version 3, the one for Vista? There's a Vista version one 32-bit and one for the 64-bit.

[http://isorecorder.alexfeinman.com/Vista.htm](http://isorecorder.alexfeinman.com/Vista.htm)

---

### Post by gibson81 on 2008-08-06
would it make a difference if i dled the 32 bit version vs the 64 it version, the 64 didn't work?

i hate to try and make another disk before im sure because i ve already wasted 4. :(

---

### Post by dhughes on 2008-08-06
> **gibson81 said:**
> would it make a difference if i dled the 32 bit version vs the 64 it version, the 64 didn't work?

i hate to try and make another disk before im sure because i ve already wasted 4. :(

 The 64-bit wouldn't work at all on 32-bit Vista but the 32-bit may work on 64-bit Vista, I think they do but I'm never sure about that.

 Go into Control Panel>System Properties and click where it says something about if you want to know about your CPU and RAM, it'll show you if your system is 32 or 64-bit. Then download the correct version of ISO Recorder for Vista (you are doing this on a Vista system you said?) since it seems as if the Vista version is entirely different, it's version 3 the 32-bit is still version 2.

---

### Post by prosperysbeer on 2008-08-24
tis lik user mandriva but i think using ubuntu instead might just do the trick 

[http://nerdstock.org/acer_vista_mandriva.en]("http://nerdstock.org/acer_vista_mandriva.en")

---

