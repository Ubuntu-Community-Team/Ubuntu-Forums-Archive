---
title: "BlueJ GUI not responding"
date: 2009-12-12
forum: Programming Talk
---

### Post by Jonwenger on 2009-12-12
I need to work with *BlueJ* in my new Computer Science class. I am using* Xubuntu 9.10* and *JDK 6* (working with *NetBeans* and* Eclipse*).

I had *BlueJ* installed in the software center before my upgrade to *Karmic Koala*; and it was working perfectly. Now I could not see it in the Ubuntu Software Center, so I installed it via .deb image.
I cannot do anything except look at the preferences and the help menu. All the other options are disabled. I also tried to load an old project, but it does not work. :sad:

Any ideas?

---

### Post by froggyswamp on 2009-12-12
I didn't try the .deb version, but the "all other systems" installed and worked fine, using Karmic x64 with Java 6.
[http://www.bluej.org/download/download.html](http://www.bluej.org/download/download.html)

---

### Post by Jonwenger on 2009-12-14
The .jar archive does not solve the issue. I think the problem is that I had BlueJ installed through the Ubuntu Software Center and after I installed Karmic BlueJ disappeared out of the Software Center. It was still on my system (=> applications => programming tools => BlueJ), but it was broken (not starting), so I reinstalled like I told you above...

---

### Post by Zugzwang on 2009-12-14
Try running it from the terminal and watch out for error messages.

---

### Post by Jonwenger on 2009-12-14
Unfortunately I am not very used to working with the terminal. Can you give me the commands please?
Thanks.

---

### Post by Zugzwang on 2009-12-15
> **Jonwenger said:**
> Unfortunately I am not very used to working with the terminal. Can you give me the commands please?
Thanks.

Start the terminal by choosing "Applications->Accessories->Terminal". Then type the command:
```

bluej <ENTER>

```
to start BlueJ.

---

### Post by Jonwenger on 2009-12-15
The error message I am getting is: 
```
class Boot: tools.jar not found. Potential problem for execution.
```
Appearantly this archive is missing. I could not find it in synaptic.

---

### Post by Zugzwang on 2009-12-16
> **Jonwenger said:**
> The error message I am getting is: 
```
class Boot: tools.jar not found. Potential problem for execution.
```
Appearantly this archive is missing. I could not find it in synaptic.

Is it the only error message you are getting? You should probably report your problems to some more specialized discussion group.

---

### Post by Jonwenger on 2009-12-16
> **Zugzwang said:**
> Is it the only error message you are getting? You should probably report your problems to some more specialized discussion group.
 
yeah. I am going to look for a bluej problems thread. Thank You.

---

### Post by Jonwenger on 2009-12-20
Problem solved. For people with same problems: [http://ubuntuforums.org/showthread.php?t=357361](http://ubuntuforums.org/showthread.php?t=357361)

---

