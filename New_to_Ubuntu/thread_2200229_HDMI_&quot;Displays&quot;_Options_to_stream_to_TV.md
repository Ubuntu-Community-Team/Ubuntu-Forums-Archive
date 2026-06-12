---
title: "HDMI: &quot;Displays&quot; Options to stream to TV"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by rover775 on 2014-01-18
Hello all ):P

I am new to Ubuntu. I ordered an ASUS X200-CADBOZ Notebook PC from New Egg, and it came pre-loaded with Ubuntu 12.04 LTS.

The ASUS has an HDMI port, which I have connected to a 29" VIZIO TV. The resolution of the VIZIO is 1366X768.

What I want to do is stream video from websites to the TV by way of the PC using the HDMI connection. I will be using a wireless keyboard to navigate, instead of using the ASUS keyboard. So having the ASUS only to display to the TV will be fine.

Under Settings/Displays, there are options that I don't fully understand, like:

 "Mirror Displays"

"Launcher placement"

"Detect Displays" (ie, when exactly do I select this)

"Apply" (Is this the last button I press?)

I won't need to have anything displayed on the ASUS Laptop, IF, what would be on the laptop is instead displayed to the TV.

What I need is a step-by-step outline of what to do set this up.

I have already tried setting this up, but when I have the HDMI cable plugged in to the TV and the Laptop, I get the laptop image on the TV screen, BUT, moving the cursor on the laptop DOES NOT move it on the TV screen ? ? ? ?

I'm so new to Ubuntu that I didn't really know how to get this info by searching, so please forgive me for that. I have had a desktop PC, a Dell with Windows XP since 2003. I recently dropped Cable TV, and kept just the internet, through Time Warner. I have my own modem and router. So, basically, I want to stream as much "Free" content from the Internet as I can, from sites like Hulu, and from official TV show sites, etc.

BTY, since I won't be able to set my profile just yet:

I am a male living in N. Texas. I work Monday-Friday 1pm-9pm, so during the week, I am usually on the Dell computer before noon, and after 10pm.

---

### Post by DuckHook on 2014-01-18
Hi rover777 and welcome to Ubuntu and the forums.

First things first. From notebook, with HDMI plugged into TV, please post output of the following back to this thread:```
lspci -vnnk | grep -iA20 vga
``````
xrandr
```In general, what you want to do is:
1. Make sure that the notebook senses proper resolutions from both your notebook and your TV,
2. Completely turn off the signal to your notebook monitor, and thus...
3. Leave only the signal going to your TV.

Knowing nothing about your notebook specs, the commands above are designed to provide info about what video chipset it uses, which driver is currently loaded, and what Ubuntu is sensing about the resolution capabilities of both your notebook and your TV. Knowing these things, it should be easier to adjust your video output to your desired configuration.

---

### Post by rover775 on 2014-01-18
**[SIZE=4]-----------Issue Solved----------[/SIZE]** :KS :KS

I was able to get all of what was on the Laptop to the 29" Vizio by selecting in the "Displays" settings:
[SIZE=5]
"**Mirror Displays**"[/SIZE]

That did the trick. Then whatever I moused over and clicked on the Laptop, displayed on the both the PC and the TV.



And to get the sound to go through the HDMI to the TV, instead of the sound going to the Laptop, I went to "Settings/Hardware/Sound" and selected:

**[SIZE=5]"Select HDMI/Display Port"[/SIZE]**

---

