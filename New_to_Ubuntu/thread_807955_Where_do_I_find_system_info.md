---
title: "Where do I find system info?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by javafiend on 2008-05-26
I guess like the title says, where do I find information about the hardware installed on my system?

I saw this post [http://ubuntuforums.org/showthread.php?t=800435&highlight=find+system+info%3F](http://ubuntuforums.org/showthread.php?t=800435&highlight=find+system+info%3F), but was looking for a gui method.

Thanks!

---

### Post by meborc on 2008-05-26
> **javafiend said:**
> I guess like the title says, where do I find information about the hardware installed on my system?

I saw this post [http://ubuntuforums.org/showthread.php?t=800435&highlight=find+system+info%3F](http://ubuntuforums.org/showthread.php?t=800435&highlight=find+system+info%3F), but was looking for a gui method.

Thanks!

there is a program called sysinfo

install it from add/remove , synaptic, or from terminal **sudo apt-get install sysinfo**

it will appear in applications -> system tools

---

### Post by JAYCEE1 on 2008-05-26
Some info is available at System>Administration>System Monitor. Click the system info tab.

---

### Post by garyed on 2008-05-26
For GUI I use:
Applications>System Tools>Hardinfo

If its not there then go:

Applications>Add Remove>System Tools  & select Hardinfo

---

### Post by meborc on 2008-05-26
> **garyed said:**
> For GUI I use:
Applications>System Tools>Hardinfo

If its not there then go:

Applications>Add Remove>System Tools  & select Hardinfo

yeah, hardinfo is even better... more sophisticated... and you can let it generate a nice report :)

---

### Post by javafiend on 2008-05-26
Well, I installed sysinfo and looked for Hardinfo.  I wasn't able to find the package for Hardinfo, though.  So far Sysinfo was able to show me what I was looking for.  How do I get Hardinfo?

Thanks!

---

### Post by meborc on 2008-05-26
> **javafiend said:**
> Well, I installed sysinfo and looked for Hardinfo.  I wasn't able to find the package for Hardinfo, though.  So far Sysinfo was able to show me what I was looking for.  How do I get Hardinfo?

Thanks!

**sudo apt-get install hardinfo**

you might want to check if you have enabled the extra repositories (since you didn't find it before)

---

### Post by javafiend on 2008-05-26
Hmm... still can't find it.  Which repository do I need to look in and how do I get to the tool to select the repository?

---

### Post by meborc on 2008-05-27
hmm... in synaptic package manager... go to settings and repositories... be sure you tick all repositories official and third-party

now reload/refresh the package list in synaptic

try to search for **hardinfo**

packages.ubuntu.com website shows that the hardinfo package is in the universe...

---

