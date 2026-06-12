---
title: "konsole and adept problems"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by JLahm on 2008-05-20
I installed the latest kubuntu with kde4 on my dad's PC. He's 81 and loving using kubuntu! But, we have 2 strange problems which I believe are related.

First, we are having problems with konsole. When it fills up the screen and the cursor gets to the last line, it won't display anything further until the window is resized a fraction. For example, if the prompt is at the bottom of the screen and I enter "clear", nothing happens until I resize the screen slightly. Once the screen fills, nothing works until I resize it. Any ideas?

The second problem is related, I believe. We went to install a program using the adept package manager. We had already installed numerous programs without issue until we installed one (java) that required a response to a license agreement in the Details window. No matter how hard we pressed the Return key, it wouldn't accept any input. :-) Since the adept manager appears to use the konsole routine to display the Details, I suspect we are again hitting the same issue as above. Now we cannot install any additional software as adept/apt-get/dpkg first tries to install the problem java software, which then puts up the license prompt and we are locked up again. Is there any way to remove this uninstalled package from the queue so we can get adept working again?

Any help would be appreciated! Thanks everyone.

Jim

---

### Post by Xiong Chiamiov on 2008-05-21
I once had a similar problem with the license agreement and Java.  What happens if you try to install the package again from the command line, eg
```

sudo aptitude install sun-java6-jre

```
or whatever package it was.
Also, you could try 
```

sudo aptitude safe-upgrade -f

```

---

### Post by JLahm on 2008-05-21
I managed to get adept working by using the following commands:

   sudo dpkg --configure -a
   sudo dpkg --remove --force-remove-reinstreq sun-java6-jre
   sudo dpkg --remove --force-remove-reinstreq sun-java6-bin

This removed the broken Java installations from the install queue and allowed adept to now install programs again. 

I have not figured out the konsole problem. However, xterm does work fine. In fact, it appears that the kde3 version of konsole works fine (although the kde4 version has the display issues).

Jim

---

### Post by Jonathan Harford on 2008-07-02
Apparently this problem of adept locking its database when java is installed has been fixed in Adept 3.0. Here's the bug report:
[http://bugs.kde.org/show_bug.cgi?id=151433](http://bugs.kde.org/show_bug.cgi?id=151433)

(Yes, I just upgraded java and broke my adept database, too.)

---

### Post by ellgor on 2008-07-02
Hi,

Just a suuggestion, when the agreement page comes up use the arrow keys to move (I believe you have to have read the agreement through?) when you reach the bottom use the right or left key's which will highlight your acceptance, the press Enter, ok, hope this is of help.

Regards, Ellgor

---

### Post by Saur0m on 2009-01-17
I had the same problem with konsole. I was getting mad googleing about it but found nothing.

Until I resized the window a little bit. I suspect the following:
- konsole calculates window size based on font size (it isn't the same with 80x24 than 80x50 by example).
- Later, I changed the KDE theme. Some toolbars or other components has different sizes.
- Now, the last line doesn't fit for a few pixels, so it can't be displayed (until you hit Enter or resize the window).

I don't know if it's a bug....

Hope it helps.

---

### Post by rahaman.naik on 2009-06-08
I am facing the similar problem with the Konsole. Can any body tell me is it a bug in konsole ? Are there any work aorounds? Same problem with the gnome terminal too.

---

