---
title: "[SOLVED] Wher does clamav store quarantined files?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by bhadotia on 2008-09-06
Last night I did a complete scan of the system. And all the 10 viruses it found were actually not viruses but some over-sized or over-compressed zips or somethings like that. One peculiar file that it quarantined was gdm . I returned all the other files to their home directories but this file did not do that and gave some error I cannot remember (Iwas getting sleepy). So , I left it there (thinking it was not something related to the GDM) and went to sleep. Now when I logged into ubuntu I was greeted by an error message saying that the /var/lib/gdm was not found. So that now I can't access my GUI.

So I think I don't need to explain any further. I did some google searching for the above question but no luck. I do remember reading the README's in /usr/share/doc/clamav* folders and I had known what that directoy was (can't remember now) and can't seem to find that README with the cli also (not very good with that).

So please help me.

Thanks in advance.

---

### Post by Cypher on 2008-09-06
I don't knoww here ClamAV keeps the quaratined files, but you don't really need an anti-virus software in Linux as there are no viruses for Linux that can screw up your machine. So really don't even bother with it..

---

### Post by bhadotia on 2008-09-06
> **Cypher said:**
> I don't knoww here ClamAV keeps the quaratined files, but you don't really need an anti-virus software in Linux as there are no viruses for Linux that can screw up your machine. So really don't even bother with it..
Yeah, of course we don't need an anti-virus with linux but I dual boot with windows and my data partition is NTFS which I share between the two so that if I download some program that I need in win it is good to scan it beforehand.

---

### Post by bhadotia on 2008-09-06
Well I found that as I ran ClamAV as root ., all the quarantined files (which I eventually restored) were placed in my (root's) home directory.
I have restored the gdm directory to its place and everything seems to be fine.
I'll mark the thread as solved now.
Thanks (even if there were no useful replies:)).

---

