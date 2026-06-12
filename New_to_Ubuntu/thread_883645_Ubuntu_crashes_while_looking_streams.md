---
title: "Ubuntu crashes while looking streams"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Rohbart on 2008-08-08
Hello, 
my Ubuntu crashes quite often while I'm looking streams for example from cnn.com
The last sound before it crashes is repeated constantly and I cannot 
even move the cursor. The keiybord is neither responding. So I have to break the system manually. Can someone tell me how to fix this problem?

---

### Post by spiderbatdad on 2008-08-08
Hard to sure what is happening. Are you getting a lot of disk activity at the time your system becomes unresponsive? Have you tried waiting  a while to see if the system returns to normal? Is your system up to date...all updates applied? What version of Ubuntu are you running?

Sorry for all the question, but there is little to go on. You might try installing htop or have top running in a terminal while you watch a flash video, to see if another programs starts running and hogging the resources. Or you might launch your browser from a terminal and navigate to a flash site, to see if an error occurs in your browser.

---

### Post by Crafty Kisses on 2008-08-08
> **Rohbart said:**
> Hello, 
my Ubuntu crashes quite often while I'm looking streams for example from cnn.com
The last sound before it crashes is repeated constantly and I cannot 
even move the cursor. The keiybord is neither responding. So I have to break the system manually. Can someone tell me how to fix this problem?

That's weird, post the following output:
```
top
```
Possibly a resource issue.

---

### Post by Rohbart on 2008-08-08
sorry I have had a problem attaching a screenshot
 
I have no disc activity
I waited several minutes and the system didn't turn normal
System is up to date
I'm using Hardy heron

---

### Post by Rohbart on 2008-08-08
hello, today I was again looking a video (via firefox) and my system crashed again. Is here maybe someone who has the same problem?

---

### Post by spiderbatdad on 2008-08-08
personally, I am fond of the seamonkey browser. It can be installed from synaptic package manager by installing the iceape packages. There are customizable themes and a majority of mozilla add-ons available.

Other than that I suggest opening a hidden file in your home directory: .mozilla/firefox/<something>.default
look for the file urlclassifier3.sqlite in the default folder. Delete this file: urlclassifer3.sqlite. Restart firefox.

---

### Post by Rohbart on 2008-08-14
thanks for the advice. Unfortunately I can't find mozilla in my folder. Is there a way of searching for it? I can use it but don't find it.

---

### Post by gerben1 on 2008-08-14
Note that he is talking about _**.**_mozilla, with a dot in front. 

Directories and files that start with a dot are hidden by default, if you go to your home directory and press <Ctrl>h you can toggle showing/hiding hidden files (or select "View->Show hidden files").

---

