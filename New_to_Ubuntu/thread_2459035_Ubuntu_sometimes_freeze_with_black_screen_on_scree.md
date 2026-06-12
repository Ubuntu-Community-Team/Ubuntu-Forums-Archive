---
title: "Ubuntu sometimes freeze with black screen on screen lock"
date: 2021-03-09
forum: New to Ubuntu
---

### Post by dreaddune on 2021-03-09
Hello there guys

As documented many times on the internet, some computers may have problems with freezing when using Ubuntu, and even though I've found many different posts about this particular problem, I've not been able to solve it.

My problem is quite simple; sometimes my laptop (Ubuntu 20.04 LTS) freezes with a black screen when it locks the screen. If sound is playing at the time, the computer will play the last about half a second of the sound repeatably. Trying to change TTY with Ctrl+Alt+F# does nothing. Pressing Caps Lock, the light on the keyboard does not turn on.
The freeze might be worse at larger loads, but  am not entirely sure about that.
The only solution to the freeze is a hard shutdown by holding the power button.

I'm using a Dell Latitude 7490 laptop, which includes a Intel(R) Core(TM) i7-8650U and Intel UHD Graphics 620. Most of the time I am also using an external monitor for work.

I've tried many possible solutions to no avail. Some of these include:
[LIST]
[*]Increase Swap size to 8Gb (8 chunks of 1Gb) 
[*]Install another version of Ubuntu (20.10 to 20.04 LTS) 
[*]Disabled secure boot 
[*]Using ```
intel_idle.max_cstate=1 i195.enable_dc=0 
``` in the grub configuration according to [https://linuxreviews.org/Intel_graphics](https://linuxreviews.org/Intel_graphics) because of the Kaby Lake Refresh CPU 
[*](A couple more which I've forgotten :( ) 
[/LIST]

Setting ```
nomodeset
``` seems to make the problem go away (not entirely sure) but is not feasible as a long-term solution.

I hope anyone have any ideas to a solution :)

---

### Post by Regexaurus on 2021-03-09
Reseat memory modules, and if the problem persists, memtest? [https://www.dell.com/community/Latitude/Anyone-else-having-freezing-issues-with-Dell-Latitude-7490-s/td-p/7307897](https://www.dell.com/community/Latitude/Anyone-else-having-freezing-issues-with-Dell-Latitude-7490-s/td-p/7307897)
[COLOR=#4D5156][FONT=Roboto]&#128556;[/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-03-09
> **nomencl8ure said:**
> Reseat memory modules, and if the problem persists, memtest? [https://www.dell.com/community/Latitude/Anyone-else-having-freezing-issues-with-Dell-Latitude-7490-s/td-p/7307897](https://www.dell.com/community/Latitude/Anyone-else-having-freezing-issues-with-Dell-Latitude-7490-s/td-p/7307897)
[COLOR=#4D5156][FONT=Roboto]&#128556;[/FONT][/COLOR]

Great find. It's definitely hardware.

Do NOT use 'nomodeset'.

---

### Post by dreaddune on 2021-03-10
> **nomencl8ure said:**
> Reseat memory modules, and if the problem persists, memtest? [https://www.dell.com/community/Latitude/Anyone-else-having-freezing-issues-with-Dell-Latitude-7490-s/td-p/7307897](https://www.dell.com/community/Latitude/Anyone-else-having-freezing-issues-with-Dell-Latitude-7490-s/td-p/7307897)
[COLOR=#4D5156][FONT=Roboto]&#128556;[/FONT][/COLOR]

How would I go about resetting the memory modules?
Also, the problem described in the post doesn't really match my problem. His is most definitely a hardware problem since it has something to to with the side where you grab the laptop from, while this is a problem with waking up from sleep/screen lock?

> **CelticWarrior said:**
> Great find. It's definitely hardware.

Do NOT use 'nomodeset'.

Why are you so aggressive against using nomodeset? Since "Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded", it doesn't seem do anything major, except for removing some capabilities of the video-side of the kernel. Which was also why I said that it isn't a long-term solution, but it does seem to remove the problem.

---

### Post by CelticWarrior on 2021-03-10
> **dreaddune said:**
> How would I go about resetting the memory modules?
Also, the problem described in the post doesn't really match my problem. His is most definitely a hardware problem since it has something to to with the side where you grab the laptop from, while this is a problem with waking up from sleep/screen lock?



Why are you so aggressive against using nomodeset? Since "Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded", it doesn't seem do anything major, except for removing some capabilities of the video-side of the kernel. Which was also why I said that it isn't a long-term solution, but it does seem to remove the problem.

How do you go about resetting the memory modules is you access them, remove them and put them back firmly. It's basic hardware troubleshooting.
'nomodeset' is as you describe and that's exactly the problem. It doesn't "remove the problem", it masks it by not using the full hardware capabilities that it should be using. And knowing that it has no dedicated video RAM, the fact that the problem seems to no occur or occur less frequently with 'nomodeset' points again to the memory being at fault.

---

### Post by dreaddune on 2021-03-10
> **CelticWarrior said:**
> How do you go about resetting the memory modules is you access them, remove them and put them back firmly. It's basic hardware troubleshooting.
'nomodeset' is as you describe and that's exactly the problem. It doesn't "remove the problem", it masks it by not using the full hardware capabilities that it should be using. And knowing that it has no dedicated video RAM, the fact that the problem seems to no occur or occur less frequently with 'nomodeset' points again to the memory being at fault.


Ah, I didn't think he meant the old-fashioned way ;)
I'm not that comfortable with doing this as it is a work computer, but if there are no alternatives I can give it a try

---

### Post by dreaddune on 2021-03-15
After having run a clean memtest86 (not memtest86+ as this is an UEFI-based system), I am not quite sure that a reset of the memory modules would do any difference. Should I still try it?

---

### Post by dreaddune on 2021-03-19
> **dreaddune said:**
> After having run a clean memtest86 (not memtest86+ as this is an UEFI-based system), I am not quite sure that a reset of the memory modules would do any difference. Should I still try it?

So I did a memory module reset (pulled the cards out and put them back in again) about a week ago with much success, but I just experienced a freeze again.
This time I put the laptop to sleep while not being plugged into power (working on the train) and when I woke it up after I plugged in both power and an external monitor over HDMI, it froze again. I'm not sure whether the freeze happened/happens when I put it to sleep or wake it up again, but I'm pretty sure that external monitors worsen the problem..

Does anyone have any suggestions? Logs? Tests?

---

