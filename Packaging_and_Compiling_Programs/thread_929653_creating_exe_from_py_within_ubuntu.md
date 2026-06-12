---
title: "creating exe from py within ubuntu"
date: 2008-09-25
forum: Packaging and Compiling Programs
---

### Post by soxs on 2008-09-25
Hi,
I successfully package my personal educational package (after about 1h of trying *g*)

Now i stumbled accross another problem: How can I compile a .exe file in order to be able to ship my program to windows users? (I know, I could request them to install pygtk and python, but many windows users are overwhelmed by doing anything else than browsing and (double-)clicking (no offense, but at least 80% of my friends are this type of PC users))

Note: I know this doesn't fit 100% here, but I simply don't know where to ask otherwise.

Q: Would py2exe work in a native linux environment? I didn't find anything on theri website and dl is just source and .exe files.

---

### Post by loell on 2008-09-25
try it in wine? ;)

i wouldn't know if it would work though.

---

### Post by cmay on 2008-09-25
> Now i stumbled accross another problem: How can I compile a .exe file in order to be able to ship my program to windows users? (I know, I could request them to install pygtk and python, but many windows users are overwhelmed by doing anything else than browsing and (double-)clicking (no offense, but at least 80% of my friends are this type of PC users))
if you check out the programming talk forums i think there is a few posts on this subject.if i remember right there is a even post by laroza about this.  however i think there is a tendency to suggest that it is better just to ask the users to install python and the libraries need for the sake of simplicity in the end. i do not use python so i do not know anything about it. i just wanted to point you to the part of the forums where i know the best help can be found .
good luck

---

### Post by randancing on 2008-09-25
Have you thought about simply incorporating the pyGtk and python libraries into your installation program and setting them to install as part of the package? 

Having been a long time 'Windows Invalid', I can tell you that 99% of all windows users will neither know or care that you are installing python on their machine. They will never know it is there.

Windows users are not interested in the beauty and power and control of every byte on every clock cycle of the cpu. That is a 'Linux Guys' thing. Windows users want to use your program in order to 'do' things, not in order to know how they are done.

If there are license agreements to be signed, they will sign them. It doesn't matter as long as the program runs and does want they want to do.

Check compatability before you do something like this because you don't want to screw someones HDD, but it shouldn't be a problem. 

Windows users expect EULA's and addends and plugins with almost everything they install, so make it a part of the program.

---

### Post by soxs on 2008-09-25
> **randancing said:**
> Have you thought about simply incorporating the pyGtk and python libraries into your installation program and setting them to install as part of the package? 

Having been a long time 'Windows Invalid', I can tell you that 99% of all windows users will neither know or care that you are installing python on their machine. They will never know it is there.

Windows users are not interested in the beauty and power and control of every byte on every clock cycle of the cpu. That is a 'Linux Guys' thing. Windows users want to use your program in order to 'do' things, not in order to know how they are done.

If there are license agreements to be signed, they will sign them. It doesn't matter as long as the program runs and does want they want to do.

Check compatability before you do something like this because you don't want to screw someones HDD, but it shouldn't be a problem. 

Windows users expect EULA's and addends and plugins with almost everything they install, so make it a part of the program.
but the n I need to write a install procedure for windows, which I have no clue and even think of vista and bah.. no I am not really keen on doing that though I have no knowledge of C/C++ or any other compileable language, yet..

---

### Post by soxs on 2008-09-25
i had to install python2.5.2.msi via msiexec -i ./balg_blubb.msi before py2exe_foo_bar.exe didn't refuse anymore to install...

I will check now some FAQs and test if it works.. probably tomorrow I'll get back on that topic...

---

### Post by soxs on 2008-09-26
I am back now, and well.. I was able to create a example program in wine hello.exe.. but wine won't execute it.. so I purged the whole fuss again.

Maybe there is another of doing that...

---

