---
title: "Klean Sweep"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-08-18
Hy all.
I recently installed a program called Klean Sweep.When I started it, it warned me that I should review each file I delete because I could mess up my system.I found 82 000 files, so needless to say I can't check each one up.I have the following categories:
"Empty files" "Empty folders" "Broken Symlinks" "Broken executables" "Backup files" "Orphaned files" "Dead menu entries"  "Obsolete thumbnails" and "Duplicated files".

Which of these can I delete safely? There's over 1 GB of space wasted, so I would want it back.What do you say?Did somebody use this program?

---

### Post by nicedude on 2008-08-18
That program can break your system in the blink of an eye. I tried it once and it wanted to delete all sorts of stuff that was not safe to delete so I don't use it anymore. Be very careful if you do use it. I suggest for one try deb orphan as it will clean out some unwanted stuff as will the following commands.

sudo apt-get clean

sudo apt-get autoremove

those will clear some space, and without breaking anything :-)

---

### Post by Troll_the_Great on 2008-08-18
> **nicedude said:**
> That program can break your system in the blink of an eye. I tried it once and it wanted to delete all sorts of stuff that was not safe to delete so I don't use it anymore. Be very careful if you do use it. I suggest for one try deb orphan as it will clean out some unwanted stuff as will the following commands.

sudo apt-get clean

sudo apt-get autoremove

those will clear some space, and without breaking anything :-)

So you are saying I shouldn't use it?The commands above don't do anything, they don't free space.I don't know if this is relevant, but 90% of the space is taken by "Duplicated files" (924 MB out of 1179 MB).

---

### Post by nicedude on 2008-08-18
The commands I gave you clear out unneeded packages and cached packages which I guess you just have none. I am not trying to tell you what to use in any way, what I am saying is that I almost broke my install with that tool and it finds a ton of stuff that is not safe to remove, If you want your system to boot up and work that is. So unless you absolutely know exactly what you are doing then I would recommend you steer clear of that tool.

What type of duplicate files are we talking about here? And deborphan that I mentioned is in the repositories and only looks for orphaned deb packages that are no longer needed by the system so it might remove something ( if it does though it will be safe )

I just don't want to see you brick your install trying to free a single GB. You said yourself it found 80,000 things and I guarantee you that 80,000 things are in no way safe to delete, that is why I for one don't like that tool and think it should have a big warning label on it.

---

### Post by Troll_the_Great on 2008-08-18
> **nicedude said:**
> The commands I gave you clear out unneeded packages and cached packages which I guess you just have none. I am not trying to tell you what to use in any way, what I am saying is that I almost broke my install with that tool and it finds a ton of stuff that is not safe to remove, If you want your system to boot up and work that is. So unless you absolutely know exactly what you are doing then I would recommend you steer clear of that tool.

What type of duplicate files are we talking about here? And deborphan that I mentioned is in the repositories and only looks for orphaned deb packages that are no longer needed by the system so it might remove something ( if it does though it will be safe )

I just don't want to see you brick your install trying to free a single GB. You said yourself it found 80,000 things and I guarantee you that 80,000 things are in no way safe to delete, that is why I for one don't like that tool and think it should have a big warning label on it.

OK, can you suggest a program that would clean only the unnecessary files, like "Disk cleanup" utility in windows?

---

### Post by brian_p on 2008-08-18
> **Troll_the_Great said:**
> OK, can you suggest a program that would clean only the unnecessary files, like "Disk cleanup" utility in windows?

I'm with nicedude here. His advice is sound. As far as the system is concerned I'd let the package manager handle it because that is whole point of having it. Anything installed which is not a .deb (e.g a compiled program) should either go in $HOME or under /user/local.

I'd be concerned and even suspicious of a program which told me there were 82,000 duplicate files on my machine. Either the program isn't performing as advertised or you are not using it correctly. This is one Linux user's view:

[http://groups.google.co.uk/group/alt.os.linux.mandriva/browse_frm/thread/1356e05eb1751875/bb2d5b25aed3e5ef?hl=en&lnk=st&q=%22kleansweep%22#bb2d5b25aed3e5ef](http://groups.google.co.uk/group/alt.os.linux.mandriva/browse_frm/thread/1356e05eb1751875/bb2d5b25aed3e5ef?hl=en&lnk=st&q=%22kleansweep%22#bb2d5b25aed3e5ef)

---

### Post by afogl001 on 2009-08-17
God bless the Ubuntu forums!  I found KleanSweep in the depositories with three stars so I assumed was safe.  Glad I checked this out first.  I caught on when it would list 5-8 duplicates in the same exact directory.. not sure that's possible with the file system...

---

### Post by KnottyMars on 2010-02-15
Glad I checked here too. I was tempted to install but thought I would do a quick check to see if it worked as it said. I wouldnt mind something that would scan my system to see if there were any space that could be freed up. 

Im on a laptop with a 40GB hard drive so space is at a premium. Ill try nicedudes commands and see if that helps. My problem is mainly a DVD ripping test generated about 4-5GB of files that I promptly deleted but the free space that it shows was the same as when I ripped the DVD. Weird. 

Anyway, thanks for the heads up, Ill poke around some more for something that doesnt potentially kill my system.

---

### Post by fromthehill on 2010-02-15
> **KnottyMars said:**
> My problem is mainly a DVD ripping test generated about 4-5GB of files that I promptly deleted but the free space that it shows was the same as when I ripped the DVD. Weird. 


have you emptied the trash bin?

---

### Post by Norm24 on 2010-02-15
Klean Sweep is DANGEROUS!!!

Ask me how I know.

---

### Post by Redmage913 on 2010-02-15
"How do you know?"

Hey, you asked.

---

### Post by lyall on 2010-02-15
I would use BleachBit and BleachBit(root) before using Klean Sweep

just my two cent worth

good luck and have fun learning

---

### Post by KnottyMars on 2010-02-15
> **fromthehill said:**
> have you emptied the trash bin?

cmon man, I know Im new, but not that new. Yes, trash bin was emptied but still showing the same amount of free space after deleting and empty. 

I didnt note the size of the occupied space, just going off of free space showing in the properties of the file system (right click and click properties). 

And is the built in Computer Janitor safe to use? I noticed a few things in there that it said I could delete, but was a little wary since I got this laptop working exactly the way I want. (just need a bigger HDD)

---

### Post by Dragon_net on 2010-03-10
@KnottyMars: Computer Janitor is completely safe to use. It'll delete any unused software (Components that are no-longer used from uninstalled software) Recommend any software that can be removed and any files that can be optimised.

@Troll_the_Great: Thanks for bringing this up coz I was wondering if there was a program like CCleaner. Shame there isn't but with Ubuntu emptying it's Temp folder when it shuts down, Computer Janitor Cleaning wasted space and Mozilla with it's Browser history eraser. I think my Laptop is gonna be funky quick :P :lolflag:

---

### Post by Joe Awsome on 2010-05-10
I'm really glad I found this too. Don't know what kleansweep might have done to my system. I was installing it and decided to take a look at it, found this thread on google, and boy am I happy I didn't run it. See what research does for you?!

---

