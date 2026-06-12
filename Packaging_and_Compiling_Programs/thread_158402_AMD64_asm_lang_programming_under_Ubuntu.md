---
title: "AMD64 asm lang programming under Ubuntu"
date: 2006-04-11
forum: Packaging and Compiling Programs
---

### Post by Mr. Wizard on 2006-04-11
Hi,

  I have been writing handcrafted, highly optimized .asm code on various platforms for many years.  Since Winblows XP x64 Ed. does such a bad job of supporting "bare metal" programming, I have finally decided to dive into Linux (Ubuntu) in order to write AMD64 code in assember and C/C++.  

  My Unix/Linux skills are rusty at best (I've actually been a Unix sysadmin in a past life) and I have never really done much serious development on a *nix platform.  What is the best way for me to get started writing math intensive code in C/C++ and AMD64 assember under Ubuntu?  I am looking for specific development tool/environment recommendations.   What I am doing would benefit from a great arbitrary precision arithmetic library that works with the integer instructions on whatever platform is it deployed on...no BCD or similar slow alternatives for me!  I want to do all calculations using optimal machine instructions and do whatever BIN2ASC and ASC2BIN  I/O conversion is needed as part of the UI written in C++.

  Given the above is my primary goal, there are a lot of other things I'd like to do, but I can't seem to find a good online reference that will tell me how to accomplish tasks such as  removing unwanted (non-working)  Ubuntu installations, modifying the bootloader options list, etc.  *nix has changed a lot since I learned the basics using a CLI.  I have yet to figure out how to get to a shell in Ubuntu, which is making things more difficult for me.  What is the best self-contained, extremely searchable, organized reference manual and introduction to Ubuntu?  Right now this installation won't even doing anything with the 46 updates it keeps telling me are available...very irritating... I enter the password which it accepts, then it does absolutely nothing.

  As much as I dislike Microsloth, it is very easy to find info on subjects in MSDN (assembly language programming under Winblows being a notable exception -- MSIL is lame.)  For Unbunto, I end up using Google to search the entire Web for info that ought to be in a (planned) documentation site.  The Wiki seems OK, but not as effective at providing answers as MSDN is.  That seems to be a problem with most OpenSource/GPL/PublicDomain/Freeware software projects.  <sigh>

  Have I ranted enough?

---

### Post by DJ_Max on 2006-04-11
All the information you need is available, you just need to read it.
[http://help.ubuntu.com/](http://help.ubuntu.com/) should answer most of your questions.

Since I don't know if you are using KDE or Gnome, I will let you know that in KDE, you should be able to use Kate text editor to edit .asm files.

I have never done Assembly, but when you figure out how to access your package management software(If using KDE, look for Adept, if Gnome, look for Synaptic), search for *asm*, which should give you some Assembly tools.

For the shell, you want an application called *Terminal*, both KDE and Gnome have it in different places. But are hard to miss.
[https://wiki.ubuntu.com/TerminalHowto](https://wiki.ubuntu.com/TerminalHowto)

> That seems to be a problem with most OpenSource/GPL/PublicDomain/Freeware software projects.
You must not use a lot of FOSS software, or aren't used to how it works.

---

