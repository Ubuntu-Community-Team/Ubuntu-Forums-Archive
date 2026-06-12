---
title: "Ideas for C programming safety?"
date: 2012-05-25
forum: Programming Talk
---

### Post by vancinas on 2012-05-25
I'm going to be teaching myself C programming and I was wondering what would be a good way to guard against messing up my machine while I'm at it. Right now I'm just planning to set up a virtual machine and do all my programming inside that. Is there a better way to protect me from myself? Thanks!

---

### Post by Bachstelze on 2012-05-25
It depends what you mean by "messing up".

---

### Post by jon zendatta on 2012-05-25
my sister got intoxicated & her laptop fell to floor. no C code or firewall could save her:KS

---

### Post by codemaniac on 2012-05-25
> **vancinas said:**
> I'm going to be teaching myself C programming and I was wondering what would be a good way to guard against messing up my machine while I'm at it. Right now I'm just planning to set up a virtual machine and do all my programming inside that. Is there a better way to protect me from myself? Thanks!

When you could write up C codes that breaks your system , means you have really achieved something . ;)

---

### Post by lisati on 2012-05-25
> **codemaniac said:**
> When you could write up C codes that breaks your system , means you have really achieved something . ;)

Mmmmmmmmmmmmmm, rogue pointers! :)

Being alert to possible problems is at least half the battle.

---

### Post by Tony Flury on 2012-05-25
> **vancinas said:**
> I'm going to be teaching myself C programming and I was wondering what would be a good way to guard against messing up my machine while I'm at it. Right now I'm just planning to set up a virtual machine and do all my programming inside that. Is there a better way to protect me from myself? Thanks!

Unless you are modifying the kernel modules, I can't see that you would do much which would "mess up" your system. You might get seg-faults etc but that would only impact your programme, and not others. And even if you do manage to get something so spectactular wrong that you damage another process - you can always get out with a system restart.

Your programme might modify system files, but that would only be possible if you are running your programme using sudo or similar, and I would recommend that you don't use your programme on system files until you are absolutely certain it works (i.e. test files) - and of course - keep backups :-).

---

### Post by zombifier25 on 2012-05-25
> **codemaniac said:**
> when you could write up c codes that breaks your system , means you have really achieved something . ;)

+1

---

### Post by Some Penguin on 2012-05-25
ulimit might be useful if you think you might somehow accidentally write a fork bomb or something going to consume all your file handles.

---

### Post by trent.josephsen on 2012-05-25
Don't run it as root and you should be fine. There's not much you can do in software that will actually damage your computer, and you'd have to be really really dedicated to do it in user space.

If you're concerned about losing data, there's only one defense against that, and you should be doing it anyway: backups.

---

### Post by vancinas on 2012-05-25
Okay. I just wasn't sure if there was a credible chance of breaking my computer. I've heard in the past that C is a language you should be careful with. Thanks for all of your help!

---

### Post by samitharansara on 2012-05-25
> **vancinas said:**
> Okay. I just wasn't sure if there was a credible chance of breaking my computer. I've heard in the past that C is a language you should be careful with. Thanks for all of your help!

Don't worry, don't try some fancy stuff, if you don't know what you are doing :)

Good luck

---

### Post by WitchCraft on 2012-05-26
> **Tony Flury said:**
> Unless you are modifying the kernel modules, I can't see that you would do much which would "mess up" your system. You might get seg-faults etc but that would only impact your programme, and not others. And even if you do manage to get something so spectactular wrong that you damage another process - you can always get out with a system restart.
 
Your programme might modify system files, but that would only be possible if you are running your programme using sudo or similar, and I would recommend that you don't use your programme on system files until you are absolutely certain it works (i.e. test files) - and of course - keep backups :-).
 
Very wrong. 
However, I think the main danger comes from writing makefiles, not from the programs written by beginners.
For example, you can write a makefile and in there write
```
 
clean:
rm -r * .o instead of rm -r *.o

```
 
which will subsequently delete everything, since * matches .. as well :)
Bad luck if you run everything as root, as I do :)
But the good thing about it is, you will never write a clean directive again without double and tripple checking it...

---

### Post by zombifier25 on 2012-05-26
> **vancinas said:**
> Okay. I just wasn't sure if there was a credible chance of breaking my computer. I've heard in the past that C is a language you should be careful with. Thanks for all of your help!

*Every programming language is dangerous.* It doesn't take me very long to write a C, C++, Python, etc. code that could erase the entire hard drive :P

---

### Post by CptPicard on 2012-05-26
> **WitchCraft said:**
> Very wrong. 

Hmm. IMO the post was correct. What was wrong about it?

> 
Bad luck if you run everything as root, as I do :)


Why do you do that?

---

### Post by TheFu on 2012-05-26
> **vancinas said:**
> Okay. I just wasn't sure if there was a credible chance of breaking my computer. I've heard in the past that C is a language you should be careful with. Thanks for all of your help!

Running as a non-root user, there isn't much damage you can cause. 

* You can corrupt memory - a reboot will fix that. Rough pointers can't really harm all that much.
* You can write to files - it can be garbage or overwrite important data, but *nix file permissions will protect you from harming important files.  When you open() a file, you'll know exactly which file it is.

Pointer safety seems to be out of vogue the last decade. A few simple rules make your code much safer.
* Always initialize your pointers to "NULL".
* Always verify that malloc() commands returned a non-NULL address.
* Always free() your allocated memory when you are done with it
* **Most important,** immediately after the free() call, set the pointer address back to NULL. Doing this will make other users of the pointer crash while you are developing, not 6 months later when a user has the program.

The first and last rules are often ignored by code-cowboys who believe they are smarter than everyone else. They aren't usually. Pointer errors are hard to track down if you don't do these things. If you do, your ptr code will protect itself.

---

### Post by trent.josephsen on 2012-05-26
WitchCraft, are you trolling? Nothing Tony said was factually incorrect. * doesn't match dotfiles. Running everything as root is... what? Why? *confused Jackie Chan face*

---

### Post by WitchCraft on 2012-07-14
> **trent.josephsen said:**
> WitchCraft, are you trolling? Nothing Tony said was factually incorrect. * doesn't match dotfiles. 
Not on Ubuntu, yes. Why do you think this is so ? :)


> **trent.josephsen said:**
> 
Running everything as root is... what? Why? *confused Jackie Chan face*
Hehe, well, you know, that way your just faster, because permissions don't ever get in the way. 

Not that it couldn't be done otherwise.
But it's just that annoying.
It's a convenience thing.
Convenience at the price of security to be exactly.

---

### Post by ofnuts on 2012-07-14
> **WitchCraft said:**
> Not on Ubuntu, yes. Why do you think this is so ? :)
It is not a matter of Ubuntu...  This is standar bash behavior, see [http://www.gnu.org/software/bash/manual/bashref.html#Filename-Expansion](http://www.gnu.org/software/bash/manual/bashref.html#Filename-Expansion) . So it may be a matter of bash vs other shells, assuming these other shells have this dangerous behavior, but ksh & dash don't... 

> **WitchCraft said:**
> 
Hehe, well, you know, that way your just faster, because permissions don't ever get in the way.
Not that it couldn't be done otherwise.
But it's just that annoying.
It's a convenience thing.
Convenience at the price of security to be exactly.You are actually a Windows user... On Linux, running as non-root is convenient. On windows it's a very different matter.

---

### Post by SirWhy on 2012-07-14
So the message of the day (and every day) is 'Don't run things as root unless you absolutely need to'. I learnt that the hard way.... well not really, it was a virtual maachine

---

