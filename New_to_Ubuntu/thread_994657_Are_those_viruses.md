---
title: "Are those viruses?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Goutam Roy on 2008-11-27
I am using both Windows xp and Ubuntu 8.10. When I work on Ubuntu, each time I find some unwanted files like as autorun.ini, ij.bat, m2nl.bat and sq.com in all drives. I delete those files time to time and do empty the trash, but after restarting those come back. Noted that I can not see those files on windows. I also scan whole laptop using AVG free antivirus but nothing is found. I cannot understand what type of problem it is.

Again, I cannot delete a folder which contain BENZAMIN.exe from Ubuntu trash. This showed a message 'There was an error deleting BENZAMIN.exe.

What should I do?

---

### Post by orbitaldecay on 2008-11-27
> I am using both Windows xp and Ubuntu 8.10. When I work on Ubuntu, each time I find some unwanted files like as autorun.ini, ij.bat, m2nl.bat and sq.com in all drives.

Where are you finding these files?  What directories?  What drives?

> I delete those files time to time and do empty the trash, but after restarting those come back.

After restarting into Windows, or restarting into Linux?  If you delete them while running Linux and reboot into Linux, are they still there?

> Again, I cannot delete a folder which contain BENZAMIN.exe from Ubuntu trash. This showed a message 'There was an error deleting BENZAMIN.exe.

This one I really couldn't tell you, I've never encountered any such error.  In general, sounds like virus / malware activity to me.  I'd back up my files and do a fresh install if it's a serious problem.

---

### Post by Goutam Roy on 2008-11-27
I have four dives/directories (is there any difference) like c: d: e: and f: in my laptops and in each drives, I find all the mentioned files.

and I find those file after restarting into ubuntu. and yes, when I delete those from linux and then reboot into linux, those are still there. I also remove those from trash.

Thank you dear.

---

### Post by FreewheelinFrank on 2008-11-27
Submit the files to VirusTotal for analysis. This will give you a better indication if they are malicious or not. (VirusTotal analyses files using most of the anti-virus engines available.)

[http://www.virustotal.com/](http://www.virustotal.com/)

See here for deleting files in the deleted items folder that refuse to delete:

[http://ubuntuforums.org/showthread.php?t=818800](http://ubuntuforums.org/showthread.php?t=818800)

---

### Post by Dedoimedo on 2008-11-27
Hello,

If you've deleted a file as root, then you must access trash as a root and delete the files from there.

I do recommend you scan the troublesome files with an anti-virus software (uploading them as recommended is a very good idea). Furthermore, open the .bat files in a text editor while inside Ubuntu and try to understand what it says in those files.

Dedoimedo

---

### Post by sad19440 on 2009-01-20
hi.my name is sadegh.i have to say that your system has trojan but you can not see them in windows because they are super hidden, and you have to use winNc.exe. it is a good program that shows you hidden file. but for deleting them you have to find the source file that is in your drive c. to fint it you can use process explorer or use a good anti virus like nod32,mcafee.
IF YOU HAVE ANY PROBLEM YOU CAM EMAIL ME. [EMAIL="sad19440@yahoo.com"]<snip>
[/EMAIL]

---

### Post by Goutam Roy on 2009-01-20
Thank you sadegh. Yes, u r right and the problem has been solved.

---

### Post by Joe computer on 2009-01-20
sad19440, what is that program?  WinNc.exe?  I tried to find it and couldn't

> **Goutam Roy said:**
> Thank you sadegh. Yes, u r right and the problem has been solved.

Goutam, would you mind explaining how to fix this problem?  Did you use WinNc.exe?

---

### Post by Goutam Roy on 2009-01-20
I did not use WinNc.exe. I had installed Kaspersky antivirus and cleaned all the viruses. Besides, now, when I find some unusual or unwanted .exe files in my computer, I just deleted those.

That's all.

---

### Post by Joe computer on 2009-01-21
Ok cool, thanks

---

### Post by Captain_tux on 2009-01-21
So, yes... those are virus files/infected files... but they are/were in Windows, not in Ubuntu.

---

