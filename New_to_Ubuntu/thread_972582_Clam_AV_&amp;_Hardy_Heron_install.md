---
title: "Clam AV &amp; Hardy Heron install?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Giradman on 2008-11-05
Just upgraded from Ubuntu 7.10 to 8.04, and just checking out some of my security software - have several questions concerning *Clam AV*:

1) My *ClamAV* installation was out of date (0.94 vs. 0.92) when running 'Sudo Freshclam' in the terminal window in Gusty Gibbon; now having updated to Hardy Heron, I still receive the same terminal message - is this important as long as the 'virus definitions' are updated; if not, 'how' to I get ClamAV's newest version on my 8.04 upgrade?

2) After my Hardy Heron install, I ran ClamAV (using the ClamTK GUI interface) on my 'home directory' - two viruses were detected (see the attachment) - I cannot seem to view 'which' files are affected and 'what' is the best way to handle these?  

Would appreciate any help in these issues - thanks all! :)

---

### Post by cariboo on 2008-11-05
The only thing you have to look for in your home directory is windows files, as clamav only scans and detects windows viruses.

There are no native linux virus scanners as there are no Linux viruses in the wild.

Jim

---

### Post by Giradman on 2008-11-07
**Jim** - thanks for your response - I understand that ClamAV is checking for 'Windows' viruses - of course, the issue is whether the 'infected' files might be sent via e-mail to those running Windows, hence the reason for their elimination; not a big issue for me on this machine, but probably for those running a server w/ Ubuntu? :(

I have plenty of files in the 'home' directory (music, pics, docs, etc.) that could be related to Windows, but there is still no indication as to 'which' of the two files that I indicated previously might be infected?  I fail to understand why the ClamAV program will not easily state which files are infected - may just be my ignorance, but I'm more curious about an answer to this question than 'worrowing' about whether I might infect a Windows computer.

And still not sure about this ClamAV version issue - I was pretty sure that Hardy Heron would have solved the update - oh well? :confused:

Dave

---

