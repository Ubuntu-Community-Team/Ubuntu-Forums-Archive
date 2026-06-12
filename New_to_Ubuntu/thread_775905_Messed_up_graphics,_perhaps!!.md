---
title: "Messed up graphics, perhaps!?!"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-04-30
OK, You all helped me decide that it would be best to reinstall 8.04 as I have only been running Ubuntu for less than a month.  I did it successfully!!  Thank you. 

Now the stupid part of me.  As I was playing late into the night and figuring that this is a new install, "what could I hurt"?  I started playing.  I went into Terminal, and knowing that "sudo" means "run" or at least that what I think.  Anyway, in terminal I typed "sudo compiz"  and it did something.  I don't know what, but it did something.  Next thing I know I had to hit CTRL C because whatever that something is made nothing happen, it froze.
Then I had to force my computer to shut down, or maybe I just hit restart. When I started back up it did the following:

[####:######]ata2.00: exception Emask0X0 SAct 0X0 serr 0X0 action 0X2 frozen
[####:######]ata2.00:cmd a 0/00:00:24:00/00:00:00:00:00/a0 tag 0 plo 36in
[####:######]ata2.00: status:{DRDY}

please note the [####:######] is represent of real #'s counting up, the first set of 4 is moving slower than the second set of 6. It just keeps repeating it. 

Do I need to start over and reinstall?  

Did I mention that I did all this while drinking beer?  That is probably where I got the nerve to play in terminal.

Thanks for any possible help.

---

### Post by Het Irv on 2008-04-30
sudo means "run as root", which means you can do anything you want. 
Sudo + Linux n00b + Beer = BAD!

To run compiz you should be able to just type compiz in the terminal.  

Can you boot into Recovery Mode?  It is the second option in GRUB

---

### Post by drrwhistle3 on 2008-04-30
I probably can.  Not sure until I get home but then what do I do to undo what I did.  Or if not should I boot off CD?  But still don't know what to do to fix.

Somewhere at the beginning of everything someone should permanantly put you quote of  sudo+lnx+beer = BAD!  I will never forget these words of wisdom.

---

### Post by Het Irv on 2008-04-30
Just doing some quick research, and if you have a Dell Computer, then I have good news.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)

If you need any help with those instructions, tell me.

---

### Post by drrwhistle3 on 2008-04-30
Just a few questions:

1. Do I do this in safe mode (if possible) or use the startup disk?
2. What do I use to create the script?  
3. Does the spacing matter or can I copy and paste the script?
4. I have a Dell Vostro 200, should these same instructions work?

---

### Post by Het Irv on 2008-04-30
I got that Link from [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702").

1. However you can get in, from reading the launchpad thread it looks like its tough to get it to boot, neither recovery or Live CD will work unless you tweak them
2. Use gedit, or text editor as it is called in the menus
3. Copy and Paste away, that would actually be the best way to do it.
4. If you read the Launchpad thread, It mentions a Dell V200 a couple of times

> switching the SATA mode in the BIOS from "IDE" to "RAID" allowed it to boot normally.
I don't know what your BIOS looks like exactly, but if you can find that setting and switch it you should be able to boot to the normal Ubuntu, add the script and switch it back.

---

