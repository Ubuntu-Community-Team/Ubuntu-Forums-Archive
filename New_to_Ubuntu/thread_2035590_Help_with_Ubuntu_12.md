---
title: "Help with Ubuntu 12"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by Faron on 2012-07-30
Hello,I Am trying to wipe/format my HDD,However,when i did,it still said 18MB of something is on it.I Suspect its grub,and im trying to COMPLETELY Wipe the HDD.Whenever i try  to boot from hdd,the grub rescue thing always comes up.Please help me in resolving this Issue.

---

### Post by levlaz on 2012-07-30
> **Faron said:**
> Hello,I Am trying to wipe/format my HDD,However,when i did,it still said 18MB of something is on it.I Suspect its grub,and im trying to COMPLETELY Wipe the HDD.Whenever i try  to boot from hdd,the grub rescue thing always comes up.Please help me in resolving this Issue.

Get the [gparted live CD]("http://gparted.sourceforge.net/livecd.php"). 

Boot to it and use the tools to wipe the drive.

---

### Post by Bashing-om on 2012-07-30
ok, I am somewhat of a new beginner. But, I just did the same thing. Here is my advise .
from a live cd ...go to the try ubuntu option.
bring up a CLI (terminal)
this next command is VERY  much fraught with danger; suggest research the command and insure what i relay to you is valid !
from the terminal type ```
dd if=/dev/zero of=/dev/sda bs=1M

```
sda is the first disk on your system, change it to other (as in 2nd disk sdb) if not.
this code zeros out the entire disk. you will get no output/status on the terminal;
but, be patient. my 500G disk took two hours to wipe, (there is a way to get a status, but is rather tedious for a beginner... iffen ya want will comply at your request.
when it finally completes.. choose install ubuntu... follow the prompts and shud be good to go!
HTH

---

### Post by UltimateCat on 2012-07-30
> **Faron said:**
> Hello,I Am trying to wipe/format my HDD,However,when i did,it still said 18MB of something is on it.I Suspect its grub,and im trying to COMPLETELY Wipe the HDD.Whenever i try  to boot from hdd,the grub rescue thing always comes up.Please help me in resolving this Issue.

If you delete the 18 MB ( which is probably grub ) your current distro will fail-

Ubuntu comes with G-pared if you want to delete a partition.

---

### Post by Faron on 2012-07-31
Im trying to Reinstall Window on it,then install Ubuntu to dualboot.Ubuntu IS Gone on it,but Grub remains.And this Computer ha no CD Drive,I Will Mount,using ISO-USB,And try gparted.I Will post results when I Do that.Thanks for your time :p

---

### Post by Faron on 2012-07-31
Its still ther!Ive used DBAN,Gparted live CD,And its not gone!I have also used the dd command.

---

### Post by Bashing-om on 2012-07-31
welp, Iffen ya did the dd thing from alternate access and did not wipe the drive ,I am at a loss .... maybe EFFI or GPT boot partition? Maybe maybe ...cud it be that dd can not over-write ? some-one else advise us huh ???

     where there is a problem; there is a solution !

---

### Post by joco1500 on 2012-07-31
[FONT=monospace]This command will completely wipe your hdd

USE WITH CAUTION!!!!


[/FONT]dd if=/dev/zero of=/dev/sda bs=1M

---

### Post by Faron on 2012-07-31
> **joco1500 said:**
> [FONT=monospace]This command will completely wipe your hdd

USE WITH CAUTION!!!!


[/FONT]dd if=/dev/zero of=/dev/sda bs=1M


Ive already tried that!I Have already stated that.

---

### Post by joco1500 on 2012-07-31
I'm sorry man

i didn't look at the other responses.

---

### Post by Faron on 2012-07-31
> **joco1500 said:**
> I'm sorry man

i didn't look at the other responses.

Its alright,I Just want GRUB Off already :mad:

---

