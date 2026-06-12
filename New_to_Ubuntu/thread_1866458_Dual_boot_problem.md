---
title: "Dual boot problem"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by dahliaobrien7@gmail.com on 2011-10-21
1.  I have an Compaq nx5000 laptop.
2.  It came to me with XP Pro installed
3.  This computer will be used in a Christian school
4.  I installed Ubuntu, the latest one as a dual boot.
6.  It dual boots very nice
7.  I accidently deleted the guest account on the XP Pro side of the computer.
8.  It wants a password to get into XP Pro at boot time 
9.  It wants the administrators password
10. I do not have it
11. I downloaded Optcheck iso and made a boot CD.
12. When I try to get the laptop to boot from the CD, I cannot. It passes right over it
13. The CD I made works on other Dual boot machines
14.  I went to the BIOS settings to make it look for a CD drive and the BIOS is so elementary, there is none.
15.  I cnnot get the machine to boot from a flash drive or CD, AFTER I INSTALLED UBUNTU AS A DUAL BOOT.
 
CAN ANYONE OUT THERE TELL ME HOW TO REMOVE UBUNTU OR HOW TO MAKE THE PRESENT CONFIGURATION INTO A DULA BOOT.
 
EVEN WHEN i TRY TO GO TO SAFE MODE IT ASK ME FOR THE PASSWORD.
 
HELP AND HELP SOON.

---

### Post by MG&amp;TL on 2011-10-21
If optcheck works, you have no problem-what you put on the hard drive does not affect the BIOS-or if it does, you have a more fundamental problem than XP passwords.


If the BIOS is "elementary", how did you dual-boot in the first place? If you mean it cannot boot from cd, try a USB instead. You have, I presume, changed the boot order? You need unetbootin or similiar to boot a USB:

```
sudo apt-get install unetbootin
```

in the Ubuntu partition, then look for unetbootin in the unity menu. It's intuitive.

---

### Post by satanselbow on 2011-10-21
> **dahliaobrien7@gmail.com said:**
> 
7.  I accidently deleted the guest account on the XP Pro side of the computer.
8.  It wants a password to get into XP Pro at boot time 
9.  It wants the administrators password
10. I do not have it


Have you tried a blank password or asked the people you got the machine from what it might be?

Seems silly to start mashing your otherwise good installation when there may be more obvious solutions ;)

---

### Post by dahliaobrien7@gmail.com on 2011-10-21
The BIOS gives few choices.  
The boot choices are  A> Boot from the hard Drive B> Boot from (I forget the expression)
 
Those are the only boot choices.  That is why I used the word Elementary 
I  put the Ubuntu CD in the CD drive and let it boot from the CD.  It came up with the message to press any key if you want to boot from the CD drive.
Now that I have Ubuntu on it, the message no longer comes up.
The first message  that comes up is 
Do you want to boot from the hard drive or do you want to boot from the Multibay. (I think)
Pressing either one will get the choice of booting into Ubuntu  or into XP Pro.
 
The CD in the drive bay and or in an external drive (Asus) is completely bypassed.
 
One of the boot options is Linux recovery mode which gets me into something similar to Dos and I can bring up Fdisk.  
But I need to get it to boot from the cd drive and when I installed the dual boot system, that option seems to be gone, on this computer.  
Can you help me?

---

### Post by MG&amp;TL on 2011-10-21
That seems to be "Boot options" not BIOS. In BIOS you should be able tochange a LOAD of things.

My computer has 3 boot options and over 50 BIOS options.

You will need to use a different key to access BIOS. Look for your computer menual if you can't find it.

---

### Post by Shazaam on 2011-10-21
If you say you used the Ubuntu LIVECD to install tells me that the cd for Optcheck.iso is either a bad burn or wasn't burnt as a CD IMAGE to disk (or the disk drive itself has gone bad).

There are a few standard keys to press during bootup to get to your bios. These are usually...
F2 key.
Press and hold the DELETE key.
ESC key.
F12 is usually for basic boot order choice.

What you may come across is the bios being password protected. You will have to go to the manufacturers website to get info on that.

---

### Post by dahliaobrien7@gmail.com on 2011-10-21
I tested the Opcrack.iso on another computer and it works just fine.  I downloaded the manual for the laptop and it said if I forgot my password, take the computer apart and take out the small round battery for at least 5 minutes.  I will try that tomorrow.  But before I do I will try what you were talking about with the function keys to see if it makes any different.  If nothing else work, I might try FDSK the disk and/or put the drive in another computer and format the darn thing.  Thanks for your suggestions.

---

