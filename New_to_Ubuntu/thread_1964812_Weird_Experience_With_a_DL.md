---
title: "Weird Experience With a DL"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by edeneen on 2012-04-24
I was downloading all kinds of stuff, anyhow, as I was extracting things in my package manager I noticed a weird file name, an .EXE file !!!  what the heck was that doing there, turns out it was mrtstub.exe;  ([http://www.tech-faq.com/mrtstub-exe.html](http://www.tech-faq.com/mrtstub-exe.html))  What the heck is windows malware doing in my package manager and how did it get here ???

thanks

---

### Post by audiomick on 2012-04-24
> **edeneen said:**
>  What the heck is windows malware doing in my package manager and how did it get here ???

thanks

The only thing I can think of is that you have added a package source that isn't what it claims to be.

---

### Post by strask on 2012-04-24
Have you added any possibly-bad sources to your apt configuration? You can go to system settings, and select "Software Sources", look on the "other software" tab and see what might have been added there.

Can you look at your log files to find out what package contained the malware, and what repository it came from? It would be good (if it's a legitimate repository) to warn the repository maintainers that they have malware on their server.

---

