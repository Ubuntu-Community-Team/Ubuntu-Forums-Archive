---
title: "Please Help! Just installed updates. Cant boot up my computer anymore"
date: 2015-12-26
forum: New to Ubuntu
---

### Post by MatsN on 2015-12-26
I have used Ubuntu since v 14.. and then I updated to 15.10. All went well.
I have also Windows 7 (loader)....

But today during upgrades af Firefox and som other stuff. This happened and look like this, in the wrong language:


1: GNU GRUB version 2.02~beta2-29ubuntu0.2
    *Ubuntu
      Avancerade flaggor f?r Ubuntu  (the word f?r should be för)
      Memory test (memtest86+)
      Memory test (memtest 86+, serial console 115200)
      Windows 7 (loader) (p? /dev/sda1)

2. NOTHING HAPPENS at all and it is impossable to log in.

When trying all the Ubuntu stuff I get this:

error: can´t find command `[´
error: can´t find command `[´
error: can´t find command `save_env´.
error: can´t find command `[´
error: can´t find command `[´
error: ELF header smaller than expected.
error: can´t find command `[´
error: ELF header smaller than expected.
error: can´t find command `[´
error: can´t find command `search´.
error: can´t find command `linux´.
error: can´t find command `initrd´

Press any key to continue...


When I start Windows 7 I get this message:
error: can´t find command `[´
error: can´t find command `search´.
error: can´t find command `parttool´.
error: can´t find command `chainloader´.

I have tried everything this whole day and this is my only laptop I have.
Makes me very sad  :-(

Please help!!

---

### Post by DuckHook on 2015-12-26
It is likely that you have a corrupted GRUB. This is not necessarily a big problem, but you will have to learn how to use boot repair. The simplest yet most complete instructions I could find online are [here]("http://askubuntu.com/questions/401105/elf-header-smaller-than-expected").

You will need access to a working computer to download and make the USB. Of course, if you still have the USB that you used to install originally, it will work too.

---

### Post by MatsN on 2016-01-12
Hello my friend. I just come home after a travel (without a computer  :x )
I do not have a USB with the original installation. However I have a DVD with the original installation with Ubuntu [COLOR=#ff0000]**15.04**[/COLOR].
Can I use that DVD to try to recover?
I read all the other suggestions that You gave me. BUT! It is very contradictive and gave me TOO many suggestions how to recover. Sooo, now I don't know what to do before destroying all my data... :sad: which would be a catastrophe...

---

### Post by sotiris2 on 2016-01-12
You should be able to use the 15.04 DVD to follow the instructions. But you should do so before the end of January since that is the end of support for 15.04 which could cause some issues (the repair tool would be unable to download grub). 

You need to boot from the DVD, select Try Ubuntu, connect to the internet (i.e. join your wifi network or plugin your ethernet cable) and open a terminal. Copy paste there the following and run it (press enter). ```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

[COLOR=#111111][FONT=Consolas] 
[/FONT][/COLOR]```
sudo apt-get install -y boot-repair && (boot-repair &)
``` 

Then try the recommended repair.

---

### Post by MatsN on 2016-01-12
Thanks for Your help.

GULP!! Running now....:-({|=

"sotiris2"
[COLOR=#ff0000][B]
PROBLEM SOLVED!!![/B][/COLOR]

I am up and running now!! Yihaaa ):P

Your tricks and Your code made it!

Thanks a lot!!
May I kiss You - hrm, your feet... :biggrin:

I still have just a small tiny problem right now.
When booting the comp. I got 2 Windows 7 to select.
1: ***** /dev/sda1
2: *****/dev/sda2

All are connect to the same device and still running okay.
Can i delete one of the, safe? And how to delete one of them.

Thanks are lot for Your solution. It works! :D

EDIT: I found a solution how to fix my Grub problem. It's called "Grub Customizer v4.06" and it works perfectly.

---

