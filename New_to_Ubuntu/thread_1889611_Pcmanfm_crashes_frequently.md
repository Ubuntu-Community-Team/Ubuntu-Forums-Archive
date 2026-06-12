---
title: "Pcmanfm crashes frequently"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by susanne260 on 2011-12-01
If I navigate between folders, the PCManFM file manager crashes quite frequently. About 3 or 4 times per hour.

There's no error messages or anything, the file manager window just dissapears and I have to start it up again.

I tried to google the problem, but didn't find anything relevant.

I'm using the 32-bit version of Lubuntu 11.10

---

### Post by mikewhatever on 2011-12-01
Try launching it from a terminal window with 'pcmanfm'. Hopefully when it closes, the terminal will have some helpful messages to show.

---

### Post by susanne260 on 2011-12-01
If I type "pcmanfm" into the terminal, it accepts the command and launches the pcmanfm file browser, but the command prompt goes to the next line, as if I had never entered the command in the first place.

(Just like if I type "uname" into the terminal, it says "Linux" and allows me to use the same terminal window.)

Even if I close the terminal window, the pcmanfm window launched from that terminal stays open.

In contrast, if I type "firefox" into the terminal, I can see some messages and I can't use that same terminal while Firefox is open.

How can I make it so that I can see the error message in the terminal if pcmanfm crashes?

---

### Post by MG&amp;TL on 2011-12-01
you're OK-it's *backgrounded* the process so you can keep working (you can do this with any program by suffixing the & sign in bash). Any debugging output should appear regardless.

---

### Post by susanne260 on 2011-12-11
> **MG&TL said:**
> you're OK-it's *backgrounded* the process so you can keep working (you can do this with any program by suffixing the & sign in bash). Any debugging output should appear regardless.

I started PCmanFM from the terminal and kept the terminal window open. For some reason, starting it from the terminal every single time worked and it never crashed... until today. When it crashed, there was no debugging output in that terminal, even though I kept that terminal window open and didn't use it for any other commands. :(

Any suggestions?

---

### Post by ac_d600 on 2011-12-12
Mine crashes too when I have multiple tabs open. You seem to be crashing
alot more than mine does (couple times a week), hopefully things will be
better when 12.04 comes out. :confused:

---

### Post by amjjawad on 2011-12-16
> **susanne260 said:**
> I started PCmanFM from the terminal and kept the terminal window open. For some reason, starting it from the terminal every single time worked and it never crashed... until today. When it crashed, there was no debugging output in that terminal, even though I kept that terminal window open and didn't use it for any other commands. :(

Any suggestions?

Hi there,

Few questions for you if you don't mind:
[http://ubuntuforums.org/showpost.php?p=11532952&postcount=349](http://ubuntuforums.org/showpost.php?p=11532952&postcount=349)


1- How did you install Lubuntu? is this a normal installation or Virtual Box Installation?

2- Is this the only problem you have so far?

3- Hardware Details/Specifications of the machine?
```
sudo lshw
```
CPU and RAM will be enough.

4- What Kernel?
```
uname -r

```

5- How often does it crash? is it easy to produce that crash?

Thank you!

---

### Post by amjjawad on 2011-12-16
> **ac_d600 said:**
> Mine crashes too when I have multiple tabs open. You seem to be crashing
alot more than mine does (couple times a week), hopefully things will be
better when 12.04 comes out. :confused:

Hi,

If you still have this issue, please start a new thread and then send me the link please.

I just posted to reply the OP so please, have a look at my post and follow the same steps ([http://ubuntuforums.org/showpost.php?p=11532952&postcount=349](http://ubuntuforums.org/showpost.php?p=11532952&postcount=349)) in case you want to start your own thread :)

Thank you!

---

### Post by susanne260 on 2011-12-17
> **amjjawad said:**
> 
1- How did you install Lubuntu? is this a normal installation or Virtual Box Installation?

2- Is this the only problem you have so far?

3- Hardware Details/Specifications of the machine?
```
sudo lshw
```
CPU and RAM will be enough.

4- What Kernel?
```
uname -r

```

5- How often does it crash? is it easy to produce that crash?

Thank you!

1. It's a normal clean installation on a logical partition.

2. So far, yes.

3. The CPU is: AMD Athlon 64 X2 Dual Core 3800+
I have 2GB of RAM.

I attached the entire output of "sudo lshw" to this post by a text file.

4. The current kernel version is 3.0.0-14-generic. I recently upgraded to a new kernel, but it didn't make any difference.

5. I've tried to figure out what exactly makes it crash, but it appears to crash completely randomly. It doesn't matter if I have multiple tabs open. And it doesn't matter if I have external USB devices connected or not. It still crashes.

I've used PCManFM for about 10 minutes today and it has crashed twice.

---

### Post by amjjawad on 2011-12-17
Hello,

Thanks for the answers :)

> **susanne260 said:**
> 5. I've tried to figure out what exactly makes it crash, but it appears to crash completely randomly. It doesn't matter if I have multiple tabs open. And it doesn't matter if I have external USB devices connected or not. It still crashes.

I've used PCManFM for about 10 minutes today and it has crashed twice.

Right after or during the crash, please run this command from LXTerminal:

```
ubuntu-bug pcmanfm

```

I suggest to keep the LXTerminal opened and once it happens, send the report.

---

### Post by Lockheed on 2011-12-25
I use pcmanfm as desktop manager and file manager on Arch 64, and it crashes often on me, too, for no reason other than entering a random folder.

It appears this is normal and the program is buggy. It should be fixed by the developer but I am under the impression he no longer maintains PCmanFM.

---

### Post by MG&amp;TL on 2011-12-25
No disrespect, but where did you get the "not maintained" info from? I get regular mailing-list emails about it from PCMan himself...

---

### Post by Lockheed on 2011-12-25
From the fact that the buggy version 0.9.10 has not been upgraded in over a year.

---

### Post by MG&amp;TL on 2011-12-25
Meh, we get it in from debian, so if they haven't updated...<shrugs>. I guess you could run the dev release if you really wanted.

---

### Post by Lockheed on 2011-12-26
That is the thing - there is no newer releases (dev or otherwise) than mid 2010. 
This usually is a good indicator the project is dead.

---

