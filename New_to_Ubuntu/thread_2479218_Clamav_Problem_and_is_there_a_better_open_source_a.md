---
title: "Clamav Problem and is there a better open source anti-virus toolkit?"
date: 2022-09-18
forum: New to Ubuntu
---

### Post by bhubunt on 2022-09-18
Hi,
I installed Clamav on this internet-connected Thinkpad Lenovo laptop that I am using right now, OS 20.04 LTS, but I get the following output when I type clamscan into the terminal: 
Scanned files: 4
Data scanned: 0.00 MB
Data read: 0.00 MB

I wonder if any of you can recommend a better open source anti-virus toolkit? I do not have a server, just a desktop.

Thanks.

---

### Post by ajgreeny on 2022-09-18
> **bhubunt said:**
> Hi,
I installed Clamav on this internet-connected Thinkpad Lenovo laptop that I am using right now, OS 20.04 LTS, but I get the following output when I type clamscan into the terminal: 
Scanned files: 4
Data scanned: 0.00 MB
Data read: 0.00 MB

I wonder if any of you can recommend a better open source anti-virus toolkit? I do not have a server, just a desktop.

Thanks.
I would suggest that as you are just running a desktop system and not a server you have no reason to run or even install any antivirus system on your computer.

I will, however, point you to the security section of the forum which can show you a great deal more detail of how best to deal with your OS's security including virus checks.
[https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338)
[https://ubuntuforums.org/search.php?searchid=27227133](https://ubuntuforums.org/search.php?searchid=27227133)

---

### Post by bhubunt on 2022-09-18
I have come across several websites encouraging the installation of Clamav, also on simple laptops or desktops. 

Also, is there an easy fix for clamscan reading and scanning 0.00 MB? Clamscan the app worked fine for scanning individual folders, but not the entire OS. That's why I am considering switching to another system, but I am not sure which would be better.

---

### Post by #&amp;thj^% on 2022-09-18
This is a waste but here:
Some Usage Examples:

    To check all files on the computer, displaying the name of each file:
```
clamscan -r /
```

    To check all files on the computer, but only display infected files and ring a bell when found:

```
clamscan -r --bell -i /
```

    To scan all files on the computer but only display infected files when found and have this run in the background:

```
clamscan -r -i / &
```

    Note - Display background process's status by running the jobs command.

    To check files in the all users home directories:

```
clamscan -r /home
```

    To check files in the USER home directory and move infected files to another folder:

```
clamscan -r --move=/home/USER/VIRUS /home/USER
```

    To check files in the USER home directory and remove infected files [COLOR="#FF0000"](WARNING: Your User Files are now gone.):
[/COLOR]
```
clamscan -r --remove /home/USER
```

    To see more options:

```
clamscan --help
```

---

### Post by Autodave on 2022-09-18
You really don't need an antivirus on Linux.  I have been running up to 13 machines at the same time since 2009 and have never used an antivirus and have never had a virus.  2 of my machines are pretty much open to anyone that wants to use them, but no viruses.

---

### Post by SeijiSensei on 2022-09-19
I haven't used an antivirus program in over twenty years. 

ClamAV is not designed for endusers. I run it on my mail servers to screen incoming messages for malware.

ClamAV is also known to generate false positives on some Linux systems.

---

### Post by #&amp;thj^% on 2022-09-19
> **SeijiSensei said:**
> I haven't used an antivirus program in over twenty years. 

ClamAV is not designed for endusers.[B][U] I run it on my mail servers to screen incoming messages for malware.
[/U][/B]
ClamAV is also known to generate false positives on some Linux systems.

+1
Your second line is about the only way I'd use it..:D
And I second the thought it shows to many false positives.

---

### Post by ipv2 on 2022-09-19
> **bhubunt said:**
> That's why I am considering switching to another system, but I am not sure which would be better.

did i read this right?

you are planning to change the operating system because you are unhappy with clamav / clamscan :shock:

---

