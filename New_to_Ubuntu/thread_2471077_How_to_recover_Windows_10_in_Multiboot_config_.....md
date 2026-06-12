---
title: "How to recover Windows 10 in Multiboot config? ...."
date: 2022-01-20
forum: New to Ubuntu
---

### Post by spazum on 2022-01-20
I tried to Pastebin but it does not exist ???? whatever ...... 

[http://pastebin.ubuntu.com/P/svFVm4xkS8/](http://pastebin.ubuntu.com/P/svFVm4xkS8/)

So here is the text instead ...

---

### Post by QIII on 2022-01-20
Pastebin [here]("https://pastebin.ubuntu.com/p/FYdycVj9NC/").

---

### Post by spazum on 2022-01-20
@QIII 
Thanks for finding me a new Pastebin ... I don know why the autogen didnt work the 1st time ...

---

### Post by spazum on 2022-01-20
I was following this thread [https://ubuntuforums.org/showthread.php?t=1769482](https://ubuntuforums.org/showthread.php?t=1769482) as a guide to recovering my Windows 10 partition, when I realized it was [COLOR=#ff0000]**closed**[/COLOR].
But the tool and the walk-thru for outputting relative information about my multiboot environment was/is still usable.
I installed Ubuntu on two partitions (one was a new installed 20.04) and the other was 18 upgraded to 20.04, sharing the same environment with Windows 10.
Then a Microsoft update, right before Thanksgiving trashed this config. I haven't been able to retrieve the Windows 10 partition despite my efforts.

So, now I am looking to ask for advice, help, criticism. You know, crowdsourcing for a solution ... So this link has the results of its analysis.    

[COLOR=#006400][SIZE=3]My Pastebin[/SIZE][/COLOR][SIZE=3]:[/SIZE][http://pastebin.ubuntu.com/P/svFVm4xkS8/](http://pastebin.ubuntu.com/P/svFVm4xkS8/) 

Which one of the threads can I continue my dialog and get support? I used google search, but maybe my query was ineffctive? It just left me even more confused about the solution(s) to solve this problem...

Anyhow
Toss me a bone?

---

### Post by TheFu on 2022-01-20
These forums work different than almost all other forums.  We don't want "me too" addons to an existing thread, because issues are 99% different. In short, start a new thread to get the best support - and ensure the title targets the specific expertise you need.

Each thread is there for 1 person's issue.  If it was the same issue and solved, following what the OP did should have been sufficient.
If you aren't the original poster (the "OP") for that thread, then your issue is likely a little different and needs it's own thread.  

The key to a good thread is having a relevant title, which this thread DOES NOT HAVE. The old post is why I'm here. I know nothing about Win10, so cannot help with that. Sorry.

When posting, the thing that gets the attention of people who might be able to help you is something related to the actual issue.  When I see "Help needed", I don't look at the thread.  I won't look at Win10 boot threads either, since I know nothing about it.  I know there are others here who are expert at boot issues and seem to help with Window/dual boot problems.  But the thread title is what gets them to look.
If I were creating a title, it would be something like "Triple Boot 20.04, 18.04 and Win10; post-Ubuntu update Win boot fails"

Might want to clarify what that link contains.  It isn't working for me.  "The Paste you are looking for does not currently exist. " is the error.
Was it supposed to be boot info or what? Generally, I wouldn't click an external link - definitely never to an image-hosting website.

---

### Post by QIII on 2022-01-20
Threads merged.

---

### Post by oldfred on 2022-01-20
Did you review end of Summary Report?

You have mixed BIOS/MBR & UEFI with gpt partitioning.
BIOS & UEFI are not compatible, but since you have different drives, you can use it, but have to boot from UEFI boot menu.
Some older systems may require you to change UEFI setting from UEFI to BIOS/CSM/Legacy and vice-versa. But newer ones recognize install and will let you boot. 
You will not be able to dual boot from grub as once you start booting you cannot change boot mode.

Since you have UEFI hardware, you really should have UEFI Windows?
Microsoft has required vendors to install in UEFI boot mode since 2012.

---

