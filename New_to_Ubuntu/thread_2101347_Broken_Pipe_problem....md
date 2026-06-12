---
title: "Broken Pipe problem..."
date: 2013-01-04
forum: New to Ubuntu
---

### Post by adamthomas on 2013-01-04
I have just installed linux on my computer. Whenever I try to install or remove something, it tells me that the software package failed to install/remove.In the details, it says that it "cannot allocate memory", and that there is a "broken pipe". Can someone tell me what this means and how to fix it? Please help.

---

### Post by Impavidus on 2013-01-04
"Broken pipe" means that two programs were cooperating to do something. Program A was doing something and sending data into a so-called pipe, program B was reading this data from the other end of the pipe and processing it. For some reason, program B stopped or crashed, leaving a broken pipe. When program A tried to continue writing to this broken pipe it recieved a signal, left an error message and terminated.

"Cannot allocate memory" means that a program couldn't get the (RAM) memory it wanted. Unable to complete its task, it gave an error message and terminated. Probably this was the program B from the previous paragraph.

It's unlikely to run low on RAM by just installing some packages. How much RAM and swap do you have and how much are you using? Keep the system monitor open whilst using the software centre. What ubuntu version is this?

There could be a problem in the software centre. Have you tried installing via the command line?

---

### Post by adamthomas on 2013-01-05
Thanks for replying. I have tried using the command line as per your advice. Whenever I do, it says there is an error "processing initramfs-tools(--configure)". My RAM is mostly full because I have installed linux on  my memory stick, not on my hard drive. Searching free -m on the command line produces this:
             total       used       free     shared    buffers     cached
Mem:           991        765        225          0         61        424
-/+ buffers/cache:        279        711
Swap:            0          0          0

When I used system monitor while using the software centre, it said that RAM usage was at about 440MiB, or 45%, and swap was not available. The version of ubuntu I am using is 12.04.1 LTS.

---

