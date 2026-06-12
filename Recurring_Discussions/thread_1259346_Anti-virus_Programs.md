---
title: "Anti-virus Programs"
date: 2009-09-06
forum: Recurring Discussions
---

### Post by yildiz.a on 2009-09-06
Hi,

There are many types of files which are not used on Windows but used by Linux or Unix, though how the anti-virus program knows that file got infected?

Thanks.

---

### Post by lovinglinux on 2009-09-06
There are no virus for Linux in the wild, so you don't need an anti-virus.

See [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

---

### Post by yildiz.a on 2009-09-06
> **lovinglinux said:**
> There are no virus for Linux in the wild, so you don't need an anti-virus.

See [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

I know. I asked for Windows. How does it know a Linux file which is infected in Windows?

---

### Post by Hosmion on 2009-09-06
> **lovinglinux said:**
> There are no virus for Linux in the wild, so you don't need an anti-virus.

See [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=765421") tutorial.
Then why would people upload Anti Virus programs?

---

### Post by Liolikas on 2009-09-06
> **Hosmion said:**
> Then why would people upload Anti Virus programs?

They are adicted to windows virus hunting have shared files with windows and want to scan them. many reasons really, but 0 really important ones. 

Maybe one important reason is windows partition virus epic disaster fix from Linux.

---

### Post by dagoth_pie on 2009-09-06
I always thought that the antivirus for Linux mostly scanned for the same virus'  as the windows version, mainly for the sake of things like email servers and file shares, to protect windows.

In answer to the original question, if I understand it right, Linux can still read the files the same as Windows does, it's just a matter of the database the antivirus scanner uses to scan for them, eg. the AVG antivirus program, would use the same database, for both Windows and Linux versions.

Also, I may be wrong, but isn't there somewhere around the number of 300-400 Linux virus's in the wild, only they've been rendered obsolete because the vulnerabilities they take advantage of have been patched, so only a very out of date Linux distro would be vulnerable.

Although, keep in mind when installing anything that isn't from the repositories (except in wine, technically that's seperate from your system), that it is possible that it could be malicious software, Ubuntu isn't immune, it just needs your permission to install any virus's should any serious threats exist

---

### Post by meomike2000 on 2009-09-06
i have a related question,,,   my wife has one of those social networking accounts....  we wont say no names.... she still uses hardy heron.... and one day, and other times since then, while on that site, a page redirected and gave her a pop up about a virus and when she canceled the popup the page appeared to look like it was scanning a windows file system and was telling her she had viruses...

i checked the system and couldnt find not problems but i have traced the name of the file that redirect as p.php..... i couldnt find this file on her system no where. 

should i do more??????

---

### Post by dagoth_pie on 2009-09-06
You shouldn't have anything to worry about, especially not on Ubuntu from web browsing. Fortunately, I was reading the other day, and I can tell you that php files, while they are an executable script, are processed by the server, not by your computer so it only has a copy on your computer, for the sake of loading it up faster the second time. You shouldn't need to take any other action, my guess would be that the popup was trying to get you to buy a fake antivirus program, that really does nothing, except make you feel a little bit safer, essentially I think it was an attempt at a scam.

---

### Post by lovinglinux on 2009-09-06
> **meomike2000 said:**
> i have a related question,,,   my wife has one of those social networking accounts....  we wont say no names.... she still uses hardy heron.... and one day, and other times since then, while on that site, a page redirected and gave her a pop up about a virus and when she canceled the popup the page appeared to look like it was scanning a windows file system and was telling her she had viruses...

i checked the system and couldnt find not problems but i have traced the name of the file that redirect as p.php..... i couldnt find this file on her system no where. 

should i do more??????

It is just a scam to install Windows malware disguised as anti-virus. I wouldn't worry about it. She would have to actively download and install the software on a Windows machine to get infected. That scanning thingy is fake, as everything else mimicking the Windows interface.

---

