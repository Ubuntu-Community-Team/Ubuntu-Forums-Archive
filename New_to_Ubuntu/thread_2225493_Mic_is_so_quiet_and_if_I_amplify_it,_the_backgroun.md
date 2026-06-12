---
title: "Mic is so quiet and if I amplify it, the background noise about overpowers my voice."
date: 2014-05-21
forum: New to Ubuntu
---

### Post by Owner_CJ on 2014-05-21
I just installed Ubuntu 14.04 LTS desktop again yesterday. I attempted to switch to Ubuntu as my main OS about a month ago, but when I tried to talk to friends in Skype, they all told me they can't hear me; so, I mucked around a bit and found the sound settings and amplified my mic, but then they complained that it was too staticy. Now, I'm having the same problem, my mic is way too quiet and when I amplify it, I get too much static. I am not using Skype in Ubuntu, rather I've installed VirtualBox and I am running a Windows 7 Virtual Machine. I've noticed that the mic testing bar that shows you how loud your voice is hardly moves on Ubuntu. The mic testing bar moves approximately 2 bars if I yell into my mic. Here is a picture to clarify what I mean by mic testing bar, where it says "Input level:" :
[IMG]http://i.imgur.com/bvB8WHq.jpg[/IMG]
 
Now, I'm not entirely sure if this picture will mean anything, but here it is:
[IMG]http://i.imgur.com/090G3nS.jpg[/IMG]

It has some information about my sound card, but if it's not enough, please tell me what I need to do.

If anyone can help me fix this problem I'm having with my mic, I'd be extremely grateful.

EDIT: I have installed Skype in Ubuntu and have confirmed that the same problem exists. It is not the VM that is the issue, it is something wrong with the host OS (Ubuntu). My problem is that I have no clue what is wrong.

---

### Post by Alley_Oop on 2014-05-21
I found this:

> [COLOR=#333333][FONT=Ubuntu]...To prevent this, go into the Skype Options menu - Sound Devices - remove the tick at: Allow Skype to automatically adjust my mixer levels. Click Apply. Readjust the sound mixer controls.[/FONT][/COLOR]

Source: [https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

---

### Post by Owner_CJ on 2014-05-21
Sorry I was unclear about how I was installing Skype. I have it installed in a Windows 7 Virtual Machine, I tried doing what you recommended; sadly, it didn't work. My friends still are telling me they can hardly hear what I'm saying. Also, I've achieved the same results when I amplifiy my mic as I did the last time -- it produces a ton of static.

---

### Post by Owner_CJ on 2014-05-22
Bump

---

### Post by Vladlenin5000 on 2014-05-22
Are you bumping for what exactly? Troubleshooting Skype for Windows in a VM is outside the scope of this forum...

---

### Post by Owner_CJ on 2014-05-22
I don't feel that I should move this to a different forum because the VM isn't causing the issue, it's the host OS (Ubuntu).

---

### Post by Vladlenin5000 on 2014-05-22
> **Owner_CJ said:**
> I don't feel that I should move this to a different forum because the VM isn't causing the issue, it's the host OS (Ubuntu).

Oh really? Why is that? Please enlighten us.

And... Not that it matters but... Why have you installed Skype in a VM instead of the native version? Is this some kind of project or what?

---

### Post by Owner_CJ on 2014-05-22
Just tested my mic on Skype on Ubuntu... Each person tells me they can hardly hear me even if they have their speakers turned all the way up to 100%. The reason why I have VMs is because I still use Windows for some stuff, and I want to start using Ubuntu as my main OS.

---

### Post by Vladlenin5000 on 2014-05-22
So you've tested native Sype already and found it to have the same issue? That indeed is a problem pertaining to the host OS. A VM - any VM - can only handle hardware as good as the host OS does, never better (that would require a miracle and there's no such thing as miracles).

Now it's time to troubleshoot the audio in your Ubuntu. First and foremost there's a couple of things you should know:
1. Your sound card/chip is quite common and issues in Linux are seldom (if ever) reported for this Realtek ALC662 and...
2. Drivers are already included and they work fine since... Ever!

So... A few questions:
Have you tested that same hardware - board + external mic - before with a different OS?
And aren't you by any chance using speakers? If so the noise you're experiencing it's feedback, not "static"... Important note: there's only so much sensitivity you can pull from a mic before you get feedback. There are ways around it and you can discuss that later if pertinent.
Do you have another input for the mic? I noticed you used the rear connection. Would you please try the frontal as well if available?
Needless to say the first troubleshooting step should be the hardware itself, both internal (board) and external (mic). If you can test another mic and/or the same mic in another computer or recording device please don't hesitate.

---

### Post by Owner_CJ on 2014-05-22
To answer your questions:
> Have you tested that same hardware - board + external mic - before with a different OS? Answer: Yes, I ran Windows 7 Home Premium 64 bit before I started with Ubuntu, I had no problems with Windows, regarding the mic.
> And aren't you by any chance using speakers? If so the noise you're  experiencing it's feedback, not "static"... Important note: there's only  so much sensitivity you can pull from a mic before you get feedback.  There are ways around it and you can discuss that later if pertinent.  
Answer: No, I'm using earbuds, I don't know if it's worth noting, but I am using a 4 ring jack but I use a splitter to separate the 4 ring jack to two 3 ring jacks (mic and audio). 
> Do you have another input for the mic? I noticed you used the rear  connection. Would you please try the frontal as well if available?
Answer: I plugged my mic jack into the front of my desktop, either 1. the front mic socket is broke, or 2. Ubuntu isn't recognizing it, but I think the first point is more possible.
EDIT: My front mic socket is broke, I unplugged my jack and plugged it back into the rear socket, and Ubuntu automatically detected it. So, Ubuntu is working on detecting if something is plugged in.
> Needless to say the first troubleshooting step should be the hardware  itself, both internal (board) and external (mic). If you can test  another mic and/or the same mic in another computer or recording device  please don't hesitate.
Answer: I've tested this headset (or earbuds) on my laptop running Windows 8, I still use the 4 ring to 3 ring splitter and it works just fine. Sadly, I do not have another mic to test, as this headset is the only mic that I have.
Thanks for your help so far, I appreciate it.

---

