---
title: "Ubuntu Lockup"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by eye812 on 2013-02-12
I am new to Ubuntu and I am having some issues.With in the first two minutes after booting, Ubuntu seems to totally and irretrevably lock up.  I recently installed version 12.04 LTS 64 bit to dual boot with Windows 7 home premium using a Wubi install. I put Ubuntu on its own 80GB NTFS partition. My machine is a two year old Lenovo laptop with an AMD E-350 processor and 3 GB RAM. 
I have tried to recover using the REISUB method (holding printscrn+alt then r-e-i-s-u-b). This didn't do anything. I also tried unsuccesfully to get to a terminal by pressing ctrl+alt+f1, Not that I would know what to do if the terminal would have opned anyhow.  Any help would be much appreciated

---

### Post by fdrake on 2013-02-12
> **eye812 said:**
> I am new to Ubuntu and I am having some issues.With in the first two minutes after booting, Ubuntu seems to totally and irretrevably lock up. 
what do yo mean?  You cannot login or ubuntu does not boot when you select it at GRUB selection?  It is not clear what is the problem

---

### Post by eye812 on 2013-02-13
Ubuntu seems to complete the boot process but locks up within the first two minutes or so after booting. It does this sporadically. Some times it boots and runs fine for the duration of my session.  Some times it locks up at the login screen and at other times it locks up when I try to open an application. The only consistency among these incidents is that they have all seemed to occur shortly after booting.

---

### Post by fdrake on 2013-02-13
> **eye812 said:**
> Ubuntu seems to complete the boot process but locks up within the first two minutes or so after booting. It does this sporadically. Some times it boots and runs fine for the duration of my session.  Some times it locks up at the login screen and at other times it locks up when I try to open an application. The only consistency among these incidents is that they have all seemed to occur shortly after booting.

boot into ubuntu (do not login). Press ctrl + alt f1 ;
login with your user and pass into the cosole;
and type:
```

df -h  /home

```
you may have assigned very little space  to your home dir during installation!
post here the results. Since this is a wubi install I suggest you to boot into windows >> control pannel >> add/remove software >> uninstall Ubuntu;

 and re-install ubuntu again giving it at leas 4-5 gigs of space.

---

### Post by 3rdalbum on 2013-02-13
It sounds like you have faulty memory - something I am very familiar with. First, try taking your RAM out and putting it back in to ensure it is well-seated. If this doesnt fix things, try taking a stick of Ram out of your system and see if this helps, then try another stick if it doesn't work.

If still no luck, remove the Wubi Ubuntu and actually install Ubuntu on the partition by booting from the Ubuntu CD and running the installer from there.

---

### Post by mörgæs on 2013-02-13
Or run Memtest from the boot menu. Give it a few hours.

---

### Post by 3rdalbum on 2013-02-13
> **mörgæs said:**
> Or run Memtest from the boot menu. Give it a few hours.

True, but I've had faulty RAM before that still passes Memtest.

Phoronix Test Suite's memory benchmarks used yo be pretty reliable at crashing the computer with the dud sticks installed, you could try that too.

---

### Post by eye812 on 2013-02-13
As to fdrakes suggestion this is the result:

file system   1k blocks   used     available   use%   mounted on
/dev/loop0    17596475    3986592   13609883   23%        /

All though I could be wrong, I do not think this is a RAM issue because the problem is only occuring in Ubuntu and not Windows 7.

---

### Post by eye812 on 2013-02-16
Any other suggestions?

---

### Post by JuhazOne on 2013-02-18
Have you been using this laptop successfully before? Using Windows? If yes I guess it could be a driver issue.

I just updated my Kubuntu to 12.10 and I still experience GPU lockups. I guess I'll have to report a bug at some point... My symptom is that the graphics gets corrupted in a funny way and the only thing changing on the display is the mouse. Sometimes I can use ctrl+alt+f1 to switch to a terminal and bring everything down in a controlled fashion (the graphics at the terminal are corrupted too but I can still see myself typing), sometimes ctrl+alt+f1 doesn't work but alt+sysrq+reisub does and sometimes the keyboard won't work at all.

Of course I have no idea if your problem is a GPU lockup (or even a driver issue, that was just a suggestion). In any case I'd suggest looking under /var/log if you successfully boot the system sometimes. Type this to check the log files that have been modified lately, the latest logfile last:

```
cd /var/log
ls -ltr
```

To view a log file I'd suggest opening it up in an editor. Type something like:

```
sudo gedit <filename>
```

(You can do the same in a file manager, too, but I don't know how to instruct that since I rarely do that myself.)

What should you look for? Difficult to say, something out of ordinary. If you feel like you can't tell if everything looks normal then you might post here the contents of your /var/log/syslog file.

---

