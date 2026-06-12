---
title: "a few WINE questions"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by TechDragon on 2008-11-24
Ok, I am trying to get a program (perfect world int) that I used to use on windows working in Ubuntu 810 with wine. It works but I get no mouse cursor, the gentooians state that it works fine with gentoo and the reason is that they compile wine from source. I have also heard that if you dump the innards of an actual Windows install into the wine directory that wine works better.

1. Does wine work better if compiled from source? How would I go about compiling wine from source in Ubuntu 810?

2. Does wine work better if I drop the innards of an actual windows install into its directory? what specific innards do I need to dump into it?

3. Would it work best of all if I compiled it from source then dumped the windows innards into it?

4. Does WINE work better x86 or x64

---

### Post by echo314 on 2008-11-24
About your first question, newer versions of programs can often be found by using source code instead of the repositories, which can take a while to get the new version. Check which version the repo has, and which the Wine site is offering. You can look at the change log to see if any of the features affect what you wanted.

Good luck!

---

### Post by LowSky on 2008-11-24
> **TechDragon said:**
> 
1. Does wine work better if compiled from source? How would I go about compiling wine from source in Ubuntu 810?

2. Does wine work better if I drop the innards of an actual windows install into its directory? what specific innards do I need to dump into it?

3. Would it work best of all if I compiled it from source then dumped the windows innards into it?

4. Does WINE work better x86 or x64


1. you dont have to compile it from source it works about the same, but if you want the newest version, use WINEHQ repo, over the Ubuntu version.

2. this is a taboo. Way back before version1.0 this was a thing that sometimes worked. You used to have to add fonts like Tahoma to get things to work correctly.

3. No bad idea

4. Now I might get flak for this, but best answer is use x86,. if you need optimum progrma support. Most things run great on 64 bit but when in doubt run 32 bit(x86). BTW it not called x64, its AMD64 -- x86 is an intel chip design name ie, 286, 386, 486, 586, etc...

---

### Post by kostkon on 2008-11-25
> **TechDragon said:**
> Ok, I am trying to get a program (perfect world int) that I used to use on windows working in Ubuntu 810 with wine. It works but I get no mouse cursor, the gentooians state that it works fine with gentoo and the reason is that they compile wine from source. I have also heard that if you dump the innards of an actual Windows install into the wine directory that wine works better.
I don't think it works for them because they have compiled it themselves but because they use a different version of Wine. What version do you have?
> **TechDragon said:**
> 1. Does wine work better if compiled from source? How would I go about compiling wine from source in Ubuntu 810?
Don't think so.
> **TechDragon said:**
> 2. Does wine work better if I drop the innards of an actual windows install into its directory? what specific innards do I need to dump into it?
You could replace some DLLs (or other system files) only if needed. You can do that, if you want.
> **TechDragon said:**
> 4. Does WINE work better x86 or x64
No clue.

But, what the [* Wine AppDB*]("http://appdb.winehq.org/") page for your application says?

---

