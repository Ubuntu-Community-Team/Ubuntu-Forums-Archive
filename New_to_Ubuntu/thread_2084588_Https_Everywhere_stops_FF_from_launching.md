---
title: "Https Everywhere stops FF from launching"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by activedream on 2012-11-15
Hi, i just installed Ubuntu 12.10 in a dual boot and updated, then I started adding addons to Firefox like DownloadHelper and NoScript and RemoveItPermanantly like I have in my Windows 7 firefox installation, only when I installed HTPPS everywhere from the Eff, I could no longer get firefox to launch. I tried to remove and reinstall a couple of times with restarting the computer each time, which is way faster than windows 7, but until I started a Linux recovery option in the bootup screen, and then did something called repair packages or something, I couldn't get firefox to start. When it did start, I went into safe mode - whatever it's called - and removed https everywhere, at which point it worked fine. Has everyone else had success with Https Everywhere but me?  activedream

---

### Post by stinkeye on 2012-11-15
I don't normally use Firefox but I added the Https Everywhere extension
with no problems.
The rest of the extensions are just the default ones so it may be a problem
using Https Everywhere with one of your other added extensions.

Ubuntu 12.10
Firefox 16.0.2
Https Everywhere 3.0.4

---

### Post by activedream on 2012-11-16
Wow, thanks for posting that answer!  I never thought of that, I was worried about Ubuntu, just having installed it. You got it right, it was an add-on conflict. Here's the info, but being a newbie, I don't know exactly what I should have done:  a: I removed firefox and reinstalled it, then restarted the machine. b: after restarting the machine, I did the Ubuntu Recovery option in the dual-boot menu, and did the 'check all file systems' and the 'repair broken packages' option, following all the prompts they threw at me.  thing is, I don't remember if I did a or b first. Anyway, the conflict was between HTTPS Everwhere 3.0.4 from the Electronic Freedom Foundation and the Trackerblock 2.2 add-on for Firefox ummm  16.0.2 I think.(on Ubuntu 12.10) I removed all of the addons, restarted with Https Everywhere, then added all the other addons one at a time, until firefox wouldn't start. (which happened only after installing Trackerblock)  So now I am up and running again, thanks again! You [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by stinkeye on 2012-11-16
> **activedream said:**
> Wow, thanks for posting that answer!  I never thought of that, I was worried about Ubuntu, just having installed it. You got it right, it was an add-on conflict. Here's the info, but being a newbie, I don't know exactly what I should have done:  a: I removed firefox and reinstalled it, then restarted the machine. b: after restarting the machine, I did the Ubuntu Recovery option in the dual-boot menu, and did the 'check all file systems' and the 'repair broken packages' option, following all the prompts they threw at me.  thing is, I don't remember if I did a or b first. Anyway, the conflict was between HTTPS Everwhere 3.0.4 from the Electronic Freedom Foundation and the Trackerblock 2.2 add-on for Firefox ummm  16.0.2 I think.(on Ubuntu 12.10) I removed all of the addons, restarted with Https Everywhere, then added all the other addons one at a time, until firefox wouldn't start. (which happened only after installing Trackerblock)  So now I am up and running again, thanks again! You [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
Hi activedream. Glad you got it fixed.
**FYI:**
Most applications keep preferences or addons to the default config in a
hidden file or folder in your home directory.
eg Firefox keeps your extra addons,history, preferences etc in
the **.mozilla** folder in your home folder.
The preceding dot makes a folder/file hidden.
In the file browser press ctrl+h to show hidden files.

If you were to delete or move the **.mozilla** folder to your desktop,
Firefox would start with clean default settings as if started for the first time in a fresh OS install.

When you uninstall through the software centre it does not remove the hidden
config files in your home folder so will start with the same configs and possibly the same error.

So what I'm saying is, if an application fails to start after you have changed
a preference or added something, you can often fix by moving the config file or folder
and restarting the application.

---

### Post by activedream on 2012-11-17
so I will revisit this page by search if I encounter this problem again, because this info is also good and new to me. repairing the files or packages redid this I guess, or something else I did the long way around. I had to read your reply a few times to get it, and I won't remember it. I love Linux ubuntu though. I feel good using it. I have read other peoples' comments that they felt 'like a kid again', but I didn't really know what they meant at the time. Strange that some OS's have the effect of changing the way you feel?  And thanks again

---

