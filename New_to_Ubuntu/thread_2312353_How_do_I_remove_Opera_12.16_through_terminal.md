---
title: "How do I remove Opera 12.16 through terminal?"
date: 2016-02-03
forum: New to Ubuntu
---

### Post by SciGuy1872 on 2016-02-03
Hi.  I removed Opera 36 (I knew the package was opera-stable and used Synaptic), but I haven't found the name of the 12.16 package; I want to use the terminal to remove it because of the age impacting security.  Everything I saw was how to install Opera.  Thanks for your help!

---

### Post by haplorrhine on 2016-02-03
apt-get remove/purge <program>

right?

---

### Post by SciGuy1872 on 2016-02-03
Thanks for the reply.  I I know that part of the command--I just need the name <program>   When I enter "sudo apt-get remove opera", the terminal tells me that "Virtual packages like 'opera' can't be removed".  I have also tried to add the version numbers.

---

### Post by sandyd on 2016-02-03
Hi,

Use 
```

dpkg -l
``` to list all installed packages.

As a result, you can combine it with grep to find all opera packages

for example:
```

dpkg-l | grep opera
```

---

### Post by Vladlenin5000 on 2016-02-03
What makes you think you have it installed? Considering you already had a much newer version installed then it's highly unlikely there's cruft left from the old one as it is usually updated.
Also, if you already used Synaptic, why didn't you searched Opera/opera there? It should show you all related packages - if any - still in your system.

---

### Post by SciGuy1872 on 2016-02-03
I did install today the beta version 36, it didn't allow grouping of the tabs anymore, so I wanted to remove it.  I assumed the program didn't overwrite because they both (Opera 12.16 and 36) still looked like two different programs, and they had two different icons--the familiar "O" I set a long time ago, and the icon designated by the Software Center for 36.
     In Synaptic, I did search under "All" for "Opera" for the 12.16 (after 36 was gone), but I didn't find anything that looked like what I was looking for.  I entered the text "web browser" because I didn't see a heading for that category; I also went to three other headings--World Wide Web (it mentioned nothing but three entries for adobe flash plugin), Internet and Web Server.  As you can tell, I tried to solve my problem about 12.16 myself--also Google searches for "removing Opera 12.16 in Linux terminal".  I just didn't know what the program name was--sudo apt-get remove <program>

---

### Post by Vladlenin5000 on 2016-02-03
You can also try post#4 instructions, just to be sure.

---

### Post by SciGuy1872 on 2016-02-03
Hi.  Thanks for the very powerful knowledge!  I think that as a result I won't need to post about some things.
Have a great day,
                 Anthony

---

### Post by CantankRus on 2016-02-03
If you install the newer version called **opera-stable** it will remove the older version just called **opera**.
For this reason I install and use **opera-beta** which does not remove the older "opera 12.xx version.

I only use the inbuilt mail and feed client in the old version.

---

