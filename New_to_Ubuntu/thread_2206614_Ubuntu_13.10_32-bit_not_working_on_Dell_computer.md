---
title: "Ubuntu 13.10 32-bit not working on Dell computer"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by amber4 on 2014-02-19
After successfully installing Ubuntu 13.10 (64-bit) to dual-boot on my Gateway with Windows 8, I attempted to install the 32-bit version on my old Dell computer and it would not load Unity past login. I ended up rolling back to [s]12.10 [/s] 12.04 which is working fine, but I'd prefer running the latest version. Unfortunately, I didn't get any screenshots of the terminal when I ran 'unity,' but I do remember a fatal error involving OpenGL and something to do with the display. I know it's vague, but any suggestions as to why this happened? (By the way, the Dell is extremely old and we've had it for years. It currently dual boots Windows XP and Ubuntu [s]12.10[/s] 12.04 LTS. )
'

---

### Post by squakie on 2014-02-19
Might be a video driver or GPU support issue.  Please post back the output of:

lspci | grep VGA

---

### Post by amber4 on 2014-02-19
This is really unfortunate... but I can't do that since I did a fresh install of [s]12.10[/s] 12.04 over 13.10. Should I run it from live USB, and would that give me the same input as if it was actually installed on the computer?

---

### Post by deadflowr on 2014-02-19
> **amber4 said:**
> This is really unfortunate... but I can't do that since I did a fresh install of 12.10 over 13.10. Should I run it from live USB, and would that give me the same input as if it was actually installed on the computer?

That info should be the same whether running a live session, 12.10, or 13.10.
Since it'll be the same hardware.

---

### Post by amber4 on 2014-02-19
Ok, I'll burn the .iso back to the usb I used and do that. (as soon as siblings log off the other computer. :P )

---

### Post by amber4 on 2014-02-19
Argh. Now Startup Disk Creator isn't recognizing my USB drive, even though I can store files on it. I was able to create a bootable USB from it before, but now I'm not able to for some reason.

---

### Post by claracc on 2014-02-20
> **amber4 said:**
> This is really unfortunate... but I can't do that since I did a fresh install of 12.10 over 13.10. Should I run it from live USB, and would that give me the same input as if it was actually installed on the computer?

You don't need to use a live usb session. As you have reinstalled ubuntu 12.10 in the computer, simply open a xterm:
```
CTRL+ALT+T
```

and there run the propossed command:

```
lspci | grep VGA
```

Then you can post here, the output obtained.

---

### Post by amber4 on 2014-02-20
Oh, okay. Here's the output:

```
 family@family-Dimension-3000:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) 
```

---

### Post by deadflowr on 2014-02-20
I don't think that card will work well with Ubuntu
(Not really sure)
Ubuntu uses a more graphically heavy desktop.

But [Xubuntu]("http://xubuntu.org/getxubuntu/") would probably fly on it.
It uses a more traditional style over the newer one Ubuntu uses, but a lot of users with extensive knowledge use it now, so support for problems is quite good. At least here in these forums.
It also shares many of Ubuntu base features, and shares the same repository system, so any app you can install from Ubuntu software center should be installable on Xubuntu.

Personally, I use Ubuntu, but I have used Xubuntu, and find it quite easy to use.
(That ends my sales pitch, thank you);)

---

### Post by amber4 on 2014-02-20
Ok, thanks for the suggestion. :) Since I'm navigating my family away from Windows as it has been running extremely slow on both old and new computers, I might have to stick with Ubuntu on both of them as long as they're running okay, and frankly, even the old Dell dinosaur is performing better with Ubuntu than it ever did with Windows. :P But once they get over the learning curve with Ubuntu, I'll see what they'd like to do (since it's not my computer... haha) and finish fixing everything up before I go off to college. I have been looking into Xubuntu though, since it's supposed to perform better on older computers... or something. It looks like something I'll have to continue looking into. :)

Again, thanks. :)

---

