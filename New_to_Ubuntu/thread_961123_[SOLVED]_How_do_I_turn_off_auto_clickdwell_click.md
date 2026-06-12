---
title: "[SOLVED] How do I turn off auto click/dwell click"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by partsguy22 on 2008-10-28
I just installed ubuntu 8.04 on my laptop (HP dv6500) 
the problem is if I let the pointer hover over any thing it will open it without clicking it or it will move the cursor to a different location
I can't figure out how to turn off this bloody auto click feature off:mad:


I've looked in system-->preferences-->mouse and the dwell click button is not checked

I've also checked in system-->preferences-->windows and the auto select isn't checked either

I'm a complete Linux noob so please be gentle

thanks

---

### Post by Tamlynmac on 2008-10-28
Check your gconf-editor (I believe it's in your applications/system tools as configuration editor)

Once open left click on the arrow next to desktop - left click the arrow next to gnome - left click the arrow next to accessibility. Then left click on the mouse folder.

On the right side of the window in the list of mouse delay and dwell configuration look for "dwell enabled" if this box is checked - left click on the box once to disable. You may also wish to disable "delay enable".

Do you have a mouse that loaded any special drivers that may also be an issue? Is there a mouse icon listed in your menus (especially  system administration or preferences) or in the panel?

---

### Post by partsguy22 on 2008-10-28
thanks that seems to have worked

---

### Post by Tamlynmac on 2008-10-28
Glad it worked and don't think twice about asking for assistance. I was a noob after installing Ubuntu (FF) and many people assisted in getting me on track. There's a lot of good people on this forum, that truly enjoy helping others.

A very intelligent man once told me that there are no stupid questions - only dumb answers.
:lolflag:
Hope you're enjoying the Ubuntu experience.

---

### Post by partsguy22 on 2008-10-28
Well I thought it was fixed I guess it is not it just changed what it was doing it still opens, closes , minimises folders and menus without clicking on them  and if I type past my curser in a text feild it causes the text to sart over where ever the pionter is

also if I just pass my pointer over a menu it will select anything I pause at

there are no drivers installed for a mouse as far as im aware ,its a synaptics touch pad and it also acts as have clicked something if I tap the pad...i just want to have full control over what my pointer does
if I want to click on some thing I want to have to use the mouse buttons
.... I just want to turn this off....this is driving me nuts

any more help would be greatly appreaced I do like ubuntu so far and its working flawlessly on my desktopand I love it....it just making me think I should have stuck with vista on the laptop


thanks again

---

### Post by Tamlynmac on 2008-10-28
Open system/control center/
left click on Assistive Technologies
If "Enable assistive technologies is enabled (checked) - disable it (uncheck)

---

### Post by partsguy22 on 2008-10-28
ive tried that as well...the settings are the same between my desk top and my laptop and my desk top dosent do it


right now

system-->preferences-->mouse-->dwell click unchecked

system-->preferences-->assistive technologies-->enable assistive technologies unchecked

gconf editor-->desktop-->gnome-->accessibility-->mouse-->
button lqayout-->2
delay enable-->unchecked
delay time-->1.700000476837158
dwell enable-->unchecked
dwell show ctw-->unchecked 
dwell time-->3
threshold-->30
all the rest are at 0


any other ideas?

---

### Post by partsguy22 on 2008-10-28
It was something I did when I edited my screen resolution in xorg.conf

I fixed it now all is fine again


thanks for the help

---

### Post by vivekjustthink on 2012-09-11
Hi,

if still u have problem, follow my post [here]("http://ubuntuforums.org/showthread.php?p=12232127") [[http://ubuntuforums.org/showthread.php?p=12232127]](http://ubuntuforums.org/showthread.php?p=12232127]). :P

---

### Post by abra6 on 2013-04-28
Right, so I have the same problem, and it is quite aggravating. I have been looking through various threads on the subject and the  solutions don't appear to apply to my system. Under mouse and keyboard there is no tick box or mention of any feature called dwell click, and there is no gconfig editor that I can find. I can also not find anything like "assistive technologies". I am running Lubuntu on an old Acer, version 12.04. I am a complete beginner with linux, and do not know how to code. I noticed another thread proposes a solution involving inputting code... I would try this if I was walked through how... it appears to apply to "ubuntu 12.04". Is it safe for me to assume that this would also apply to LUBUNTU 12.04?   Anyhow, thank you very much in advance for the assistance. I have done everything I could to make sure I wasn't asking any redundant questions... I simply cannot find a way to implement the solutions that are already proposed here. Cheers to ya'
-A6-

---

