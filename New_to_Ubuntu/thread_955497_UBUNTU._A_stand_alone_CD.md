---
title: "UBUNTU. A stand alone CD?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by cypher000 on 2008-10-22
Hi guy's. Thank for letting me come in on this great forum. Once a long time ago it seems. I had a CD with Linux and it would run Linux without actually having to install it on my computer. This was very convenient for me at the time. I have not done anything with Linux since then as the software seemed to be much inferior to Windows. However after reading so much about Ubuntu I feel that I would like to try again, if there is a similar Ubuntu CD which I can run the software with and without having to actually install it on my hard drive. At least till I have given it a through checking out. Does anyone know of such a CD or am I not making sense? Many thanks for any help. Regards Walt.:lolflag:

---

### Post by perlluver on 2008-10-22
That is called a live cd, and yes Ubuntu does offer that as the normal download from there site.  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), download it from there, you will most likely want the top option, of 32 bit.  Be sure to burn it at 4x, then reboot with it in the machine, and pick, try Ubuntu without changes to computer.

---

### Post by Murph223 on 2008-10-22
forgive a noob question here, but if i chose the "try without any changes" option from the Live CD, then any files i might move around or copy will essentially appear as if it never happened when i boot back into Windows, right?

---

### Post by perlluver on 2008-10-22
Right, depends on what you are moving, but if you create a document, and save it, it will not save.  If you move a file on your hard drive, or delete one, that will be permanent.

---

### Post by Murph223 on 2008-10-22
...thanks.  And if i copy and paste, will that also be permanent?

---

### Post by northern lights on 2008-10-22
yup.

---

### Post by perlluver on 2008-10-22
> **Murph223 said:**
> ...thanks.  And if i copy and paste, will that also be permanent?

If you copy and paste from your hard drive, to the ubuntu Desktop no.  If you copy and paste to another folder on the hard drive, yes.  As the CD is not able to be written to, it will act as it never happened.

---

### Post by Murph223 on 2008-10-22
Ok thanks, i'll give it another shot.  I tried earlier to copy/paste a couple of system files out of the system32 directory but didn't see them when i got back into Windows.

---

### Post by perlluver on 2008-10-22
> **Murph223 said:**
> Ok thanks, i'll give it another shot.  I tried earlier to copy/paste a couple of system files out of the system32 directory but didn't see them when i got back into Windows.

What did you copy and where did you try to paste them?

---

### Post by Murph223 on 2008-10-22
i'm trying to get the SAM and SYSTEM files out of system32/config and paste into another existing directory.  I have to get a forgotten admin password for a family member...

---

### Post by perlluver on 2008-10-22
> **Murph223 said:**
> i'm trying to get the SAM and SYSTEM files out of system32/config and paste into another existing directory.  I have to get a forgotten admin password for a family member...

Oh then the hard drive containing Windows has to be mounted so you can copy and paste them, and be careful when doing that, you could delete important things.

---

### Post by Murph223 on 2008-10-22
AH.  ok then.  although it may be an obvious enough task, is it something fairly simple that you could explain to me please?

---

### Post by perlluver on 2008-10-22
When you are logged into the CD, at the top, under places, it should have the Windows hard drive listed, click on it, it should load up.  When you are in there, you can do what you need to do.  Sorry can't help more than that.  As I can't see what you are doing.

---

### Post by Murph223 on 2008-10-22
oh, ok then its as simple as being able to see the Windows disk under "places".  Thanks for the tip...i'll give it another shot.

---

### Post by Murph223 on 2008-10-22
alright, it worked.  i must not have been holding my mouth right the first time!  :rolleyes::rolleyes::rolleyes:

---

### Post by Murph223 on 2008-10-22
Actually i spoke too soon.  I'm getting an error on the copied files that they are corrupted and unreadable.

SO, next question:  from within the "test" run of the LiveCD, can i run an application that is installed on the windows disk?

---

### Post by northern lights on 2008-10-22
> **Murph223 said:**
> SO, next question:  from within the "test" run of the LiveCD, can i run an application that is installed on the windows disk?
Out of the box you can't - neither with the LiveCD ("test run") or from a regular install. While some apps are available for both systems (most Windows free / open source apps are actually ports from GNU/Linux), Linux binaries are different. I.e. Linux cannot run .exe executables...

On a regular install you could add Wine, a Windows emulator, and run .exes if there's no Linux alternative. Or run XP in a virtual machine. But for now, the answer is No.

---

### Post by Murph223 on 2008-10-22
hmm.  ok thanks, at least i've learned something today.  I just wish i knew why the files were corrupted.  i wonder if i could just phsyically move them out of the dir, do what i need to do in windows, then re-boot the LiveCd and put them back...

---

### Post by northern lights on 2008-10-22
I understood where the files are from (C:\Windows\system32\...) but other than that I haven't really understood what you're trying to accomplish. Exactly what files are you handling and what do you need to do with them?
Just read them?
Modify 'em?
Execute 'em? (as explained above, that most likely won't work)

---

### Post by stalkingwolf on 2008-10-22
The files you are working with might have been corupted by a virus,malware,
or trojan.

In Windows you can try running Norton System works to fix them.  Another
option would be to try Backtrack linux.

---

### Post by Duck2006 on 2008-10-22
Why not install ubuntu to a usb flash drive so any changes you make will be saved and come up on the next time you use the drive.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://www.blog.solarwind.metafy.org/2008/02/17/setting-up-a-usb-stick-on-windows-to-act-like-an-ubuntu-installation-cd/](http://www.blog.solarwind.metafy.org/2008/02/17/setting-up-a-usb-stick-on-windows-to-act-like-an-ubuntu-installation-cd/)

---

