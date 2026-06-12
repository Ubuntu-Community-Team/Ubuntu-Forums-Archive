---
title: "Total n00b Install Problems, Please Help"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by lgoldberg on 2008-06-19
(originally posted last night, apparently in the wrong discussion)

Just downloaded the software today, and trying to install. My ThinkPad didn't boot from the CD, so I let the Ubuntu installation software create the entry on the boot menu, so I then rebooted, and the choice came up (Windows XP Pro or Ubuntu). I selected Ubuntu, and I got an 'error 15', at which point the only thing I could do was pop the CD out and reboot again.

Okay, so I decided to do the "install within windows" option, but when I do that, it tries to download the whole 699 MB off the internet again!! If that's correct, then what's the 699 MB on the CD for?? Frustrated.

What do I do?

---

### Post by radiocognition on 2008-06-19
It would be more helpful for us if you gave us a more detailed description of what you did to your machine.  I take it that this your one of your first times using Linux, so we want to help users like you.  Telling us that "my install didnt work" wont allow us to identify your proplem as fast as if you had given a little more information.

Anyways, one of the first things I do after downloading an ISO from the internet is verify that it was downloaded correctly.  An old unix trick from the darkages called md5sum gives us a way to check the integrety of a file downloaded from anywhere.  Try to take an md5sum of your downloaded ubuntu ISO with [Advanced CheckSum Verifier]("http://www.irnis.net/gloss/md5sum-windows.shtml") for windows.  If your calculated checksum matches the sums listed on the [ubuntu page]("http://releases.ubuntu.com/8.04/MD5SUMS") for your ubuntu cd, then you know you have a good copy.

Here are the sums for Hardy Heron:

```
7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe
```

I am pretty sure that the live CD should boot on your hardware (which is why I think you need to check to see if you downloaded the ISO correctly).  If not, it would be helpful if you posted more about your computer and any unusual components that it might have.

---

### Post by lgoldberg on 2008-06-19
Thanks for your response!  I did just download that application, and ran the checksum.  My values matched.

I have a ThinkPad, Windows XP, 1278 MB RAM, Pentium 1300MHx processor. Everything on it is stock (it's a company laptop) and the only peripherals I have installed are a 250 GB external HD and a wireless mouse.

What other info would you need?

---

### Post by mikeyphi on 2008-06-19
> **lgoldberg said:**
> (originally posted last night, apparently in the wrong discussion)

Just downloaded the software today, and trying to install. My ThinkPad didn't boot from the CD, so I let the Ubuntu installation software create the entry on the boot menu, so I then rebooted, and the choice came up (Windows XP Pro or Ubuntu). I selected Ubuntu, and I got an 'error 15', at which point the only thing I could do was pop the CD out and reboot again.

Okay, so I decided to do the "install within windows" option, but when I do that, it tries to download the whole 699 MB off the internet again!! If that's correct, then what's the 699 MB on the CD for?? Frustrated.

What do I do?

You might need to set your BIOS to boot from CD....there's usually an option to enter the BIOS screen during the normal boot sequence...such as "Press 'Del'..."   before the MS system starts loading.

---

### Post by radiocognition on 2008-06-19
I have to agree with mikeyphi, check your BIOS settings and make sure its set to boot from CD before boot from hardrive.  You should be able to use Ubuntu as a live cd and go through the installer that way.

I personally have never used Wubi (install within windows option) so I am not entirely sure what you did earlier when you "let the Ubuntu software create the entry on the boot menu".  Do you know if Ubuntu has allready reformatted and repartitioned your disc to make room for the linux install?

But by looking at your hardware that you have listed, I can't see any reason why the live cd would not boot.  Doesn't look like its too exotic, and I personally have installed Ubuntu on crazier hardware than that (just did today in fact).  Hang in there, we will make sure we get it running for you.

---

### Post by lgoldberg on 2008-06-20
Well, golly - the little blue "Access IBM" button on the laptop keyboard came in handy for the first time.  I pressed it on bootup, and it gave me a little windows-esque interface to change various system settings, including the boot drive!  Yes, I got it to work, and enjoyed it.

But actually, I think I will install it as the exclusive OS on an idle tower I have sitting in the basement.  We need another machine at home for web surfing, and I noticed that even running off the CD drive, Ubuntu and Firefox are a LOT quicker than XP/IE, or even XP/Firefox.

Thanks for everyone's help!! :-)

OH, there was another thing.  When I got booted up on the CD, I tried to run the partition utility, and after grinding for about half an hour, it failed.  Any ideas why that would happen?

---

### Post by avtolle on 2008-06-20
Did you defrag the HDD first (I recommend running whatever defragging tool you have twice, BTW) before trying to install? A thought for your consideration.

---

### Post by radiocognition on 2008-06-20
Here is another thread on the exact same problem.  You may be able to get better help there

[http://ubuntuforums.org/showthread.php?t=835699]("http://ubuntuforums.org/showthread.php?t=835699")

---

