---
title: "Installing AVG Antivirus on Ubuntu to scan a Windows machine for viruses"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by John_Patrick_Mason on 2014-06-22
Hi everyone,

I'm trying to install the antivirus program AVG on  my dual boot Ubuntu/Windows machine to scan for viruses on my Windows  drive, but I can't seem to get it to work.
I downloaded the .deb file here: [http://free.avg.com/download.prd-alf](http://free.avg.com/download.prd-alf)  but when I use the Ubuntu Software Center to install it, prior to  install, I get this warning: "The package is of bad quality: The  installation of a package which violates the quality standards isn't  allowed. This could cause serious problems on your computer. Please  contact the person or organisation who provided this package file and  include the details beneath." Can somebody explain what this message  means? Is it because the package is too old for my version of Ubuntu?
Or  perhaps I should install ClamAV instead, what do you suggest? I just find  the instructions on how to install ClamAV unreadable from a newbie  standpoint.

Thanks in advance,

Mason

---

### Post by Vladlenin5000 on 2014-06-22
You can install ClamAV from the Software Center. What is so unreadable about that?

---

### Post by John_Patrick_Mason on 2014-06-22
I would only I can't find it. You mean ClamTk*? And I was only reading what was written directly on ClamAV's website here: [http://www.clamav.net/lang/en/download/packages/packages-linux/](http://www.clamav.net/lang/en/download/packages/packages-linux/).

---

### Post by John_Patrick_Mason on 2014-06-22
I would only I can't find it. You mean ClamTk*? And I was only reading what was written directly on ClamAV's website here: [http://www.clamav.net/lang/en/download/packages/packages-linux/](http://www.clamav.net/lang/en/download/packages/packages-linux/). And what about that message earlier what does it mean?

---

### Post by Vladlenin5000 on 2014-06-22
Yes, ClamTK is a graphical frontend for ClamAV which is CLI only. Just install the former and you'll get ClamAV (as well as all the packages needed) plus integrated updates. That's what the ClamAV's website mentions: *ClamAV has been officially included in the Ubuntu distribution since the first Ubuntu release*. You can find any software *officially included in the Ubuntu distribution* in Ubuntu's repositories, hence the Software Center suggestion. 

The error message you got with AVG can have many causes but probably the main one is, as you suspected, old age.

---

### Post by John_Patrick_Mason on 2014-06-22
OK, I downloaded ClamTk but it reads that my virus definitions are  outdated, so I click on help in the menu bar -> check updates ->  GUI updates. It then says N/A (non available). How can I update my virus definitions  using the GUI? Or am I now forced to use the CLI to get the lastest updates?

---

### Post by Vladlenin5000 on 2014-06-22
The GUI version and the virus definitions versions are two different things. You don't need to update the GUI (graphical user interface) and you won't be able to for the time being because that's the only version available at Ubuntu's repositories. 
The virus definitions will be updated along your regular updates.

---

### Post by lisati on 2014-06-22
I'm assuming that you have ClamAV/ClamTk installed. You should be able to apply updates to the definitions by running the following from the command line:
```
sudo freshclam
```
Don't be alarmed if it prompts for your password and the password doesn't show, type your password as normal.

---

### Post by John_Patrick_Mason on 2014-06-22
"The virus definitions will be updated along your regular updates." You mean through the Software Updater? I understood the part about ClamAV being officially included in the Ubuntu distribution, and I suspected it was CLI only, since I couldn't find it in the Dash, and that there would be a graphical user interface available out there. I just wasn't sure what "front-end" meant. Personally I would have prefered if they had said a GUI, that would have been much clearer. Also, right after I mount my Windows drive, when I select the relevant Windows directory to scan, I get a message that says no files were scanned. What am I supposed to do? Scans don't happen that quickly.

---

### Post by John_Patrick_Mason on 2014-06-22
Thanks for the command line, lisati. The GUI now says my virus definitions are up to date.

---

### Post by John_Patrick_Mason on 2014-06-23
Bump

---

### Post by Bucky Ball on 2014-06-23
Please wait twenty-four hours before bumping your threads. I see your ClamAV virus definitions are up to date; you are still wanting to know how to get AVG running?

---

### Post by John_Patrick_Mason on 2014-06-23
OK, no problem. I did read Ubuntu's Code of Conduct, so if there was something in there about bumps I would have known about it. I did manage to get ClamTk to work, I just have a quick question that will probably lead to a follow up question if the answer is yes, since I'd like to learn a little about how Ubuntu works, not just solve a problem. When Vladlenin5000 writes, "The virus definitions will be updated along your regular updates," does he mean through the Software Updater?

---

### Post by Bucky Ball on 2014-06-23
> **John_Patrick_Mason said:**
>  I did read Ubuntu's Code of Conduct, so if there was something in there about bumps I would have known about it.

True. It's actually in a sticky here:

[http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)

> Do not bump your thread more than once in any 24 hour period. Consider waiting longer than that before bumping - this may help to catch the attention of users outside of your timezone.

As we are an international forum populated by volunteers news can sometimes take a while to get around. ;)

Now where were we? As we were ...

---

### Post by John_Patrick_Mason on 2014-06-29
Thanks everybody. I marked the thread as solved.

---

### Post by Rob Sayer on 2014-07-01
The reason you scanned a directory but it didn't scan anything within is that you have to go into clamtk settings and enable recursive scanning.  Why this isn't on by default is beyond me.

---

### Post by gagtrix.com on 2014-07-01
Hi.... was facing the same issue...thanks for the command line... :):):) .. was helpful!!!

---

### Post by John_Patrick_Mason on 2014-07-01
Hi gagtrix.com,

Glad you found this thread helpful. A lot of people are asking the same question in the Ubuntu Software Center. There's also another way to update your virus definitions that I haven't tested yet using the GUI. When under ClamTk, click on advanced/rerun setup wizard, click on   manual under av signature options, then go to help/check for updates,   then tick signature updates, then click the check for updates box   beneath and it should update. See here for more information: [http://ubuntuforums.org/showthread.php?t=2231969&page=2](http://ubuntuforums.org/showthread.php?t=2231969&page=2)

---

