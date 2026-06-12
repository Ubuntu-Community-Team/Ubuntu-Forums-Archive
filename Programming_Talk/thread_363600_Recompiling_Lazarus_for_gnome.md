---
title: "Recompiling Lazarus for gnome"
date: 2007-02-17
forum: Programming Talk
---

### Post by CaptainPanick on 2007-02-17
Hi guys, 

I'm new to both Lazarus and Linux so the learning curve in getting everything to work is quite steep. 

I hope that I'm asking this question in the correct forum section, but here goes: 

I'm currently trying to Rebuild Lazarus (FreePascal IDE) to use gnome instead of gtk as all the text looks large and ugly, both in the IDE and on my custom designed forms. I'm hoping that switching it over to gnome will make it look better. As I understand, I need to switch to gnome in the LCL interface configuration first, and then rebuild the IDE. However, when I perform the build, the following error appears: 
make[2]: *** [../../units/i386-linux/gnome] Error 1 

Perhaps the path is incorrect or something. I tried re-installing the latest debian package for the gnome units but that didn't solve anything. I'm sure I'm just missing something small, or there might be a user restriction on the path. I'm currently using Ubuntu 6.10 Edgy. 

Any help will be greatly appreciated!

PS: I did ask the same question on the Lazarus forums yesterday but still waiting for a response.

---

### Post by runningwithscissors on 2007-02-17
One correction.
You cannot use GNOME _instead of_ GTK. You can compile support for GNOME in, but that does not mean that you should drop GTK.

Having said that, it would be more helpful if you posted more verbose output of the build process. One including the point at which the build broke. (First line saying "error:").

Or, you could wait for someone who uses Ubuntu to help you out as I am not familiar with the process of building software using apt.

---

### Post by CaptainPanick on 2007-02-17
Thx for point that out scissors. :)

With regards to the error messages. That seems to be the only message I get, unless there are a more detailed log of the build somewhere else. The build process basically stops immediately after I've clicked "Build". I then go and look in the Messages log window and that is the only message I get.

---

### Post by mjh007 on 2007-03-29
Hi there

I've just gone through the process of recompiling Lazarus, and the thing that got me stumped for a while was having to start Lazarus using 'sudo' in the terminal:

> sudo startlazarus

This allows for the changes to be made to the lazarus files

Then the next stage is to use gtk2 rather than Gnome - Seemed to work for me nicely. I just went to Tools>Configure "Build Lazarus" and changed the LCL interface to gtk2 and clicked on "Set to Build All". Then I clicked Build and it compiled the whole IDE and everything else for GTK2.

You can then start lazarus normally after that (i.e. without "sudo")

See attached screenshot for gtk2 Lazarus (much better:) )

---

