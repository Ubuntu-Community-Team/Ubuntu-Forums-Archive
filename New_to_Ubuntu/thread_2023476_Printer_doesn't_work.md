---
title: "Printer doesn't work"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by cheatos on 2012-07-12
Hi,

I wanted to print something today and I received an error message in CUPS saying:
[I]"File '/System/Library/ColorSync/Profiles/sRGB Profile.icc' not found"

[/I]A quick google search didn't give me quite the results that helped me... 
I only saw that afew other guys already had this problem too, but don't really understand their solutions.

Thanks to all your help!

---

### Post by jmfal on 2012-07-12
What version of ubuntu are you using, and what kind of printer do you have??

---

### Post by cheatos on 2012-08-14
I'm running a 32-bit 11.04 lubuntu and the printer is a hp laserjet4

---

### Post by cheatos on 2012-08-17
hmm, bumping because problem still occurs and still have no clue about how to do anything about it...

If you need anymore info, let me know.

---

### Post by gordintoronto on 2012-08-17
Did you try uninstalling the printer and installing it again?

---

### Post by NikTh on 2012-08-17
Hi , 
as you have an HP printer , maybe hp software for Linux , help you.. 

Do you have it ? 

```
sudo apt-get install hplip hplip-gui
```
Thanks

---

### Post by cheatos on 2012-08-19
Thanks for your replys, I haven't tried uninstalling the printer. How do you do that?
Installing that hp-thing seems good, I'll try that.

---

### Post by unevenflow on 2012-08-19
Hey. find printer settings and remove printer from there then add it back
then in terminal type 

```
sudo apt-get install hplip hplip-gui
```

which is agui for HP printers

---

### Post by cheatos on 2012-08-20
ok, so pretty much the same as NikTH already supposed. Thank you, I'll try that as soon as I have some time and/or need the printer ;)

---

### Post by cheatos on 2012-08-21
Hi,

so I installed hplip and the hplip-gui but still its the same. I also tried hp-setup but that didn't work either.
I have it connected via serial port but that is not an option in the hp-setup thing...

Have I screwed up my driver completely or is it even the internal driver in my printer?

---

### Post by gordintoronto on 2012-08-21
Did you try "making pdftoraster-poppler a symlink to pdftoraster"?

Or is that one of the solutions you didn't understand? (I would need to do some research to figure out how to create a symlink.)

What program are you printing from, or does it affect all programs which might print?

---

### Post by cheatos on 2012-08-22
Hi gordintorono, so I see what a symlink is but haven't yet made one by myself. 

"Did you try "making pdftoraster-poppler a symlink to pdftoraster"?"

I haven't really seen that tip in the previous posts, so I think if it's there I didn't understand it ;)

However the problem with printing appears in gnumeric and Abiword, haven't tried any other programs yet.

---

### Post by cheatos on 2012-09-20
bumpidibump

---

