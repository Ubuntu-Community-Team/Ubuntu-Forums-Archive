---
title: "Grub no longer lists Ubuntu, but will load Windows... Corrupt config?"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by scott.bouch on 2013-12-10
Hi all, my first post here..

Not a total novice, but quite green, have been playing with Ubuntu 10.04 and 13.04 for about a year now, plus use a Raspberry Pi.
[B][I]

The issue:[/I][/B]

Samsung Laptop, came with Windows7. I instaled **Ubuntu 13.04** and have been using both OS's quite happily with **Grub 2**. 


***Grub Customizer, and idiot user:***

I used Grub Customizer to edit the list of options presented by Grub, to bring Ubuntu up to the second in the list. 

Upon saving the changes, I had a little **finger-trouble** -> I stupidly closed Grub Customizer while it was still saving, doh! Just as I'd prepeared a nice playlist in rythmbox for our daughters christening... the following day!!! Of course this did not go down well with wifey who doesn't see much point in messing around with Linux when Windows seems to just work...

So when I now boot the laptop, Grub presents me with Windows 7 and a couple of memory test options, no Ubuntu...

I believe I may have corrupted the Grub config file, but I can't get to it from Windows as it doesn't See the partition due to it being an EXT format, not FAT or NTFS. So fixing it through Windows seems to be out of the question.

I have the CD that I installed Ubuntu from, this allows me to "Try Ubuntu", is there a way I can recover or reset my Grub config file through this instance of Live-CD Ubuntu? I have tried [COLOR=#4b0082][FONT=courier new]sudo update-grub[/FONT][/COLOR] in this Live-CD instance, but it doesn't work. Hopefully this is a simeple fix, maybe able to manually edit the config file, or replace it witha  fresh one? Hope it doesn't result in a full re-install..

Looking forward to a knowledgeable soul to offer some guidance...

Many, many thanks in advance, Scott.

---

### Post by fantab on 2013-12-10
You can use Ubuntu DVD/USB to re-install Grub.
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Do NOT use 'Grub-Customizer', as its known to cause problems.
If you need to customize the Grub then follow the following:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
You can also follow the thread: [http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by scott.bouch on 2013-12-10
Hi Fantab,

Thank you very much for the pointers, I'd only used Grub Customizer as it was the first GUI I'd come across for it, I will research how to uninstall software from Ubuntu.

I'll have a go this evening with the guide you shared, currently digging fencepost holes after the high winds we had a few days ago... urghh, could think of better things to be doing..

Thank you..

---

### Post by scott.bouch on 2013-12-10
Hi again,

Semi-great news, i followed the guidance in the first link, and Ubuntu loads fine, but Windows has not vanished from the options! All I have is Windows Recovery Environemnt. 

[ATTACH=CONFIG]248494[/ATTACH]

I have gone through this selection, it's a Samsung recovery solution which can restore / repair certain Windows components, I went through the most basic recovery, as didn't want to lose any data, just repair Windows' main componenets.

But Windows didn't re-appear in Grub.

Any more help will be awesome!

Thanks, Scott

---

### Post by fantab on 2013-12-10
I hope you have purged 'grub-customizer'.
Update grub from the installed Ubuntu and see if it helps:
```
sudo update-grub
```
Reboot to check.

If the above does not help then, Install '[**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair")' either in LiveDVD/USB or installed Ubuntu, and create a '**BootInfo Summary**'. 
Post the generated LINK to the summary here.

Do you have a Windows '*System Repair Disc*'? Or *Windows Install Disc*?
Because, if Winodws is 'damaged' then you will need either to 'fix' the issue. I am NOT talking about OEM Recovery. 
However, if 'Samsung Recovery' offers an option to repair 'startup'/'boot' then use the option to fix windows.

---

