---
title: "For everyone who says ubuntu can't get viruses"
date: 2009-07-29
forum: Recurring Discussions
---

### Post by libihero on 2009-07-29
my computer has been acting up the past couple days... so i decided to do a virus scan using clam and it found two viruses.....
now did it remove them automatically?
and ya i've seen some threads where people were saying using clam is useless and blah blah... so this is for them :P

---

### Post by MelDJ on 2009-07-29
isnt your wine disk the one which is infected?

---

### Post by Sef on 2009-07-29
1) How can you be sure that they are not false positives?

2) Viruses can ride of top of GNU/Linux, but they won't infect it.   For example, if you have a mail server, then you can send viruses to Window computers.

3) Wine runs Windows programs, which are susceptible to malware.   However, your system will not be infected.

4) Oldie, but a goodie [article]("http://www.linux.com/archive/feature/42031") on this subject.

---

### Post by wojox on 2009-07-29
Stay away from WINDOWS

---

### Post by oldsoundguy on 2009-07-29
Following the path, those virus files were in WINE .. where you keep your WINDOWS programs.  Scanning and protection of WINE or a Virtual drive has NOTHING to do with Linux and everything (STILL) to do with Windows.

The virus still can NOT migrate into your Linux operating system!

---

### Post by ibutho on 2009-07-29
Its already well known that Windows viruses will run under WINE. The Windows viruses cannot affect Linux and are restricted to your WINE fake windows directory.

---

### Post by MelDJ on 2009-07-29
> **oldsoundguy said:**
> Following the path, those virus files were in WINE .. where you keep your WINDOWS programs.  Scanning and protection of WINE or a Virtual drive has NOTHING to do with Linux and everything (STILL) to do with Windows.

The virus still can NOT migrate into your Linux operating system!

yeah. ubuntu's not infected. only you wine hard drive:KS

---

### Post by sisco311 on 2009-07-29
> **ibutho said:**
> Its already well known that Windows viruses will run under WINE. The Windows viruses cannot affect Linux and are restricted to your WINE fake windows directory.

+1

OP: please read the *Viruses* section from [thread=510812]Ubuntu Security[/thread]

---

### Post by libihero on 2009-07-29
how do u kno it was in wine?  i think it was the reason my linux has been acting up lately

---

### Post by Mr. Picklesworth on 2009-07-29
I'm impressed that two viruses managed to get that far, given you would have had to run them directly with Wine. Do be careful; if you're running a Windows binary through Wine, it has freedom to do as it pleases, be that malicious or otherwise. While Wine *(I think)* doesn't provide system directories to programs inside it, I believe it *does* provide full access to your home folder by default.

You can restrict that further by going to Applications -> Wine -> Configure Wine. Head to Drives and remove the corresponding ones. Note that any program you run needs to be in a directory accessible to a Wine program, though.

It should be noted that, at best, these only affect Wine and only when a Wine program is running (if that). In fact, as the above article reminds us, chances are they won't work. This is probably because malware relies on fiddly little hacks to function without being noticed. Wine simply doesn't implement all the right functionality for them to work.

---

### Post by MelDJ on 2009-07-29
> **libihero said:**
> how do u kno it was in wine?  i think it was the reason my linux has been acting up lately
  
by reading the scanned folder /home/hamz/wine in your screenshot.:)

---

### Post by Hairy_Palms on 2009-07-29
> how do u kno it was in wine? i think it was the reason my linux has been acting up lately because the two paths in the screenshot are .wine and the second is inside a a windows xp virtual disk image (.vdi)

---

### Post by Mr. Picklesworth on 2009-07-29
> **libihero said:**
> how do u kno it was in wine?  i think it was the reason my linux has been acting up lately

Because ClamAV is designed for Windows viruses :)
Although some people may be erroneously assuming that the viruses are listed in the screenshot (when in fact the listed paths are places yet to be scanned).

Does it give you a list of the viruses somewhere?

What exactly do you mean that "your Linux is acting up"?

---

### Post by regala on 2009-07-29
> **libihero said:**
> how do u kno it was in wine?  i think it was the reason my linux has been acting up lately

it has to be in Wine or in your vdi image. Clam cannot recognize what it doesn't know anything about. And it knows only about Viruses which are Windows executables, and which can only run under Wine or in your VM.

---

### Post by coldReactive on 2009-07-29
> **sisco311 said:**
> +1

OP: please read the *Viruses* section from [thread=510812]Ubuntu Security[/thread]

"Antivirus" link is dead,

"ClamAV" link is dead,

F-PROT says it's free at the bottom of its page, but you have to buy it through the order page, go figure.

the centralcommand whatever software is not free *shrug*

---

### Post by oldsoundguy on 2009-07-29
> **libihero said:**
> how do u kno it was in wine?  i think it was the reason my linux has been acting up lately

The thumbnail posted has the path to the WINE file(s).

---

### Post by libihero on 2009-07-29
my RAM would go haywire and fill up randomly, freezing just about everything on the screen.  clicking and dragging anything randomly doesnt work.

and like mr. picklesworth said, the fact my screenshot showed the pathway to wine is only because that was what was scanned first.  i could have scrolled down and it would have shown files that had nothing to do with wine or my virtual system

and i dunno how to see where the viruses r :(

---

### Post by oldsoundguy on 2009-07-29
> **libihero said:**
> and i dunno how to see where the viruses r :(

There ARE NO VIRUS PROGRAMS in the wild that attack Linux.  Forget what your Windows friends tell you .. NOT HAPPENING.

NO current AV program that you install in Linux even LOOKS for the stuff except in Windows partitions and on servers (since there ARE virus files that attach TO a server .. but they attack WINDOWS computers USING the the server.

As to your ram problem?  You sure you aren't running something in WINE that is sucking the ram up?

---

### Post by libihero on 2009-07-29
nope im not running anything at all
it could be something besides the virus
it just happens randomly
clicking and dragging, trying to exit windows, opening files, all of them start causing my comp to freeze up

---

### Post by bodhi.zazen on 2009-07-29
> **coldReactive said:**
> "Antivirus" link is dead,

"ClamAV" link is dead,

F-PROT says it's free at the bottom of its page, but you have to buy it through the order page, go figure.

the centralcommand whatever software is not free *shrug*

I fixed the dead links.

When you find such things please PM the OP of the post / thread / how to.

If you do not get a response, PM the staff or report the thread. When PM staff a link to a replacement is always appreciated.

As far as the other links, it is not stated that they are "free".

I add links as suggested by the community, so if you have suggestions send me a PM.

Last, nobody said there are no Linux viruses. All known Linux viruses have been patched long ago, so assuming your system is up to date you are not vulnerable.

Virus scanners can not protect you from zero day exploits, so, for the next virus, it is likely a security update will be available before or soon after a virus definition, so you many Linux users do not feel they need antivirus.

---

### Post by lisati on 2009-07-29
On the rare occasions I've had reason to install and use Wine, the default setup enabled access to the file system via / - thus I know not to be too hasty accepting any assertions that malware run in Wine **can't** hurt Ubuntu as something that is set in stone. The simple solution is to disable Wine's ability to go anywhere it pleases in the filesystem, and limit its access privileges to its own folders.

---

### Post by coldReactive on 2009-07-29
> **lisati said:**
> The simple solution is to disable Wine's ability to go anywhere it pleases in the filesystem, and limit its access privileges to its own folders.

step-by-step please?

---

### Post by lisati on 2009-07-29
> **coldReactive said:**
> step-by-step please?
I just reinstalled Wine from "add/remove" so I could double-check. Here goes:
[LIST=1]
[*]Select applications->Wine->Configure wine from the menu
[*]Select the "Drives" tab
[*]Highlight the entry for "/" (on my machine it shows as "Z:")
[*]click "remove"
[*]Click  "apply"
[*]If all goes well, click "OK"
[/LIST]
This won't prevent all problems, but can help.

---

### Post by libihero on 2009-07-30
the files that were viruses are as shown......
if i just delete them will it fix the problem?

---

### Post by oldsoundguy on 2009-07-30
Those are Windows files! (do you want to delete WINE?)

---

### Post by libihero on 2009-07-30
i already uninstalled and purged wine

---

### Post by Chronon on 2009-07-30
Just so you know, there probably was no virus to begin with.  Broken executables are often false positives.  I get them all the time in a build directory containing binaries built from known good source.

If you have already purged WINE then you should remove those files anyway, virus or not.  They serve no purpose to you now.

---

### Post by oldsoundguy on 2009-07-30
libihero, sorry to say you are exhibiting the standard paranoia of a recently converted Windows user.
Virus files in your Windows partition simply will NOT migrate into and have any effect on your Linux based system.  It just does NOT happen, no matter the FUD you have read on the Windows centric sites.

Sit back and enjoy your virtually bullet proof system and kiss most of the Windows programs goodbye .. there ARE Linux programs to take their place (not games .. but programs you use to accomplish WORK!)
Some are better than the Windows programs, some are equal to the programs and, of course, some are not as good.
TRY THEM!
If you find you can't learn them or that they are not to your liking, simply REMOVE them using Synaptic and try something else. (ALL ARE FREE) 
Unlike Windows, it won't "mess up your registry" since there IS NO REGISTRY!

---

### Post by Mr. Picklesworth on 2009-07-30
Did you use the migration tool when you installed? Thumbs.db is just a non-executable database file created by Windows XP. It gets placed inside picture directories, and it would have been copied over when your pictures were copied over in bulk. Nothing to worry about with those since your Ubuntu system won't understand them, and it's probably a false positive anyway. They are useless files, though, so I suggest you open up your file manager, search (hit Ctrl+f), type "Thumbs.db" and delete all the Thumbs.db files that show up, just to get them out of the way.

Oh, and they had nothing to do with Wine, so don't worry too much about that one. (The .cab files from MS Office are a bit funny, though).

---

### Post by libihero on 2009-07-30
lol ya im bein paranoid cuz my ubuntu just randomly started gettin all jacked up.  i think im jus gonna save my files and reinstall...... i cant figure out why its being all messed up.

---

### Post by lisati on 2009-07-30
> **libihero said:**
> lol ya im bein paranoid cuz my ubuntu just randomly started gettin all jacked up.  i think im jus gonna save my files and reinstall...... i cant figure out why its being all messed up.

Have you been playing with a lot of programs with a view to checking them out?

---

### Post by libihero on 2009-07-30
im not sure what you mean, but no i dont think i have.

---

### Post by lswb on 2009-07-30
> **libihero said:**
> my RAM would go haywire and fill up randomly, freezing just about everything on the screen.  clicking and dragging anything randomly doesnt work.


That just sounds like a normal ubuntu problem, it doesn't have anything to do with viruses.

---

### Post by bodhi.zazen on 2009-07-30
> **lswb said:**
> That just sounds like a normal ubuntu problem, it doesn't have anything to do with viruses.

What ? That is not normal behavior for Ubuntu.

Starting with the RAM, Linux uses RAM very different from Windows.

To see your ram use, start with :

```
free -m
```

As far as locking up , sounds like a problem with X, usually such things come from ATI or Nvidia drivers. We need to know what hardware you are using and I would start a separate thread for these questions as they are almost certainly not a "virus".

It is sad that some OS have problems with viruses such that every time there is a problem the reflex is to think you have a virus on Ubuntu.

---

### Post by libihero on 2009-07-30
i had another thread here:
[http://ubuntuforums.org/showthread.php?t=1225337](http://ubuntuforums.org/showthread.php?t=1225337)
any help appreciated :)

---

### Post by lswb on 2009-07-30
> **bodhi.zazen said:**
> What ? That is not normal behavior for Ubuntu.


I didn't say it was normal behaviour, I just said it is a normal *problem*, the kind of problem many other people post to these forums!
:)

---

### Post by bodhi.zazen on 2009-07-30
Ah, that makes sense now, :lolflag:

---

