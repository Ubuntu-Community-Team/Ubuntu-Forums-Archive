---
title: "Invalid ROM contents?"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by Futant on 2013-01-03
Hello, I have a Dell XPS L502X, i5 2.40GHz, Nvidia GeForce GT 540 (not sure what is relevant, if you need more info let me know) on which I run Ubuntu 12.04, Fuduntu and Windows 7. Since I installed Fuduntu (which is lovely by the way, and I really want them all to play nicely together :P), when I boot Ubuntu I get all sorts of messages on the boot screen, most of which I don't get chance to read. I can see that they are not always the same though. The message I see every time is 'Invalid ROM contents' with some other things (apologies for lack of detail) and most of the time I have to press 'enter' to get past a black screen with a white terminal style cursor (this usually appears before the 'invalid ROM contents' message). I have not noticed any performance issues once Ubuntu has actually booted (apart from a game stopped working, but I think that is a memory issue...) and there are no problems in either of the other OSs.
This has been going on for while now, and I feel I should at least try to find out what the problem is... any ideas? Just pointing me in the right direction would be a massive help...

---

### Post by sisco311 on 2013-01-03
You can use the `dmesg' command to print the message buffer of the kernel which will most likely contain the exact error message.

In order to save the output of the command in a file in your home directory, start a terminal (press Ctrl+Alt+T) and run:
```
dmesg > ~/dmesg.txt
```

If you need help with interpreting its output, then attach the file to your next reply or upload it to a [uwiki]Pastebin[/uwiki].

---

### Post by Futant on 2013-01-03
Hey, thanks for replying. For some reason when I try that command nothing happens? Copied/pasted so it's not a typo... Searched for the text file but found nothing. Am I missing something? Do I need to be sudo?

Strangely, the problem has disappeared but has been replaced by a much stranger one - I restarted my computer a few hours ago and found that Fuduntu has disappeared completely from Grub. Ubuntu and Windows are still there. The fact that Ubuntu's boot errors have gone makes me fear that somehow Fuduntu had been overwritten or something, but I have no idea how this could have happened. In the time between last using Fuduntu (earlier today) and now I have: been on the net, installed updates for Ubuntu and Fuduntu, done an Ubuntu backup, played Skyrim. That's it. No one has been near my computer and I haven't edited any files. What to do? 

I have posted about this on the Fuduntu forum, but just thought I'd mention it here as it is relevant to my original problem.

---

### Post by sisco311 on 2013-01-04
> **Futant said:**
> Hey, thanks for replying. For some reason when I try that command nothing happens? Copied/pasted so it's not a typo... Searched for the text file but found nothing. Am I missing something? Do I need to be sudo?


It should be in the root of your user's home directory and it's called dmesg.txt. Assuming that your user name is *user*: /home/user/dmesg.txt

If the file is empty, then you have use sudo in from of the command.

> **Futant said:**
> 
Strangely, the problem has disappeared but has been replaced by a much stranger one - I restarted my computer a few hours ago and found that Fuduntu has disappeared completely from Grub. Ubuntu and Windows are still there. The fact that Ubuntu's boot errors have gone makes me fear that somehow Fuduntu had been overwritten or something, but I have no idea how this could have happened. In the time between last using Fuduntu (earlier today) and now I have: been on the net, installed updates for Ubuntu and Fuduntu, done an Ubuntu backup, played Skyrim. That's it. No one has been near my computer and I haven't edited any files. What to do? 

I have posted about this on the Fuduntu forum, but just thought I'd mention it here as it is relevant to my original problem.

Please install Boot-Repair and post your boot info:
[uhelp]community/Boot-Info[/uhelp]

---

### Post by Futant on 2013-01-04
Well I was indeed missing something - there was the file right where you said it would be... oops! I've read through it but computer poetry is still new to me and I can't make much sense of it, would much appreciate your help so [here is my pastebin]("http://paste.ubuntu.com/1497591/").

I will install and use Boot-Repair as soon as I get hold of a blank CD to make the boot CD, will do my best to get one tomorrow.

---

