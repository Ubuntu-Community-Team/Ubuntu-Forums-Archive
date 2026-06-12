---
title: "laptop hibernation problem"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by KingTermite on 2008-05-21
I've noticed that under Ubuntu  my laptop has odd behavior for hibernation sometimes.

I've set the power button to activate hibernate in the power management console and when I hibernate via the button all seems fine.

However, it's also set to hibernate after so long idle (like a few hours or something). Whenever it hibernates that way, it gives me errors coming up saying it did not shut down properly the last time.

Unforunately, I accidentally clicked the "don't show me this again" button one time and now it's not showing me the error, but I know its still happening.

a) how can turn that warning back on
b) any ideas why hibernate is not working properly when it hibernates from idle time?

Laptop: Dell Inspiron 1720, dual boot with Windows XP

---

### Post by KingTermite on 2008-05-21
BUMP

Anybody? <cricket sounds> hello?

---

### Post by nicedude on 2008-05-21
My hibernation did not work as well for my Acer laptop in Hardy so I just disabled the Hibernation mode with the intention of figuring it out once I get the time to read up on it, And also I figure with this release being new a little more time in use and more problems will be found and solved.

That said here is a command to open the power management settings window so paste this in a terminal ( Alt+F2 and check "run in terminal" and paste the command in )

gnome-power-preferences

In that window you can set the slders all the way up to  never put the computer to sleep and it will no longer hibernate and therefore no longer be locking up due to the hibernation issue. At least that will fix your problem until somebody can give you a better solution.

nicedude

---

### Post by perillux on 2008-05-21
your not alone, a lot of laptops have suspend/hibernate issues.  Mine does.
I hibernated successfully once, but then my usb mouse didn't work so I had to restart anyway.

From what I've gathered though, I think it's an ATI problem, probably still happens on some NVidia laptops, but I'm just guessing.

---

### Post by KingTermite on 2008-05-21
> **nicedude said:**
> In that window you can set the slders all the way up to  never put the computer to sleep and it will no longer hibernate and therefore no longer be locking up due to the hibernation issue. At least that will fix your problem until somebody can give you a better solution.

nicedude

Thanks. I guess I could do that. I'd like it to hibernate when idle...but I don't want it to lock up or screw anything up.



> **perillux said:**
> your not alone, a lot of laptops have suspend/hibernate issues.  Mine does.
I hibernated successfully once, but then my usb mouse didn't work so I had to restart anyway.

From what I've gathered though, I think it's an ATI problem, probably still happens on some NVidia laptops, but I'm just guessing.
Mine is a Dell with built in Intel graphics, so not likely anything specific to ATI/NVidia....at least not in my case.

---

### Post by KingTermite on 2008-05-25
May have solved it, not 100% sure.

It seemed (by the lights) that the computer was "waking up" OK, just not the display. I changed power settings to hibernate computer on 1 hour idle time, but to set display to "never" hibernate.

I just came back from an idle hibernate and it seemed to return OK. If it worked consistently a few more times, I'll mark this problem as SOLVED. Though it would be nice to see Ubuntu handle it correctly.

---

### Post by KingTermite on 2008-05-27
> **KingTermite said:**
> May have solved it, not 100% sure.

It seemed (by the lights) that the computer was "waking up" OK, just not the display. I changed power settings to hibernate computer on 1 hour idle time, but to set display to "never" hibernate.

I just came back from an idle hibernate and it seemed to return OK. If it worked consistently a few more times, I'll mark this problem as SOLVED. Though it would be nice to see Ubuntu handle it correctly.

I spoke too quickly. I had a feeling I did when I posted it. It hibernated due to idle activity twice yesterday and failed to reinitialize both times.

This is a bit of a pain in the ****....I don't want to hit the button to hibernate (which works every time) because I don't know if I'll be back in before the 1 hour I have set to hibernate or not. At the same time, I don't want it to  never hibernate because its a laptop and I've learned from previous experience you can give your laptop an early death from leaving it on all the time. Laptops aren't designed to run 24/7 like a desktop is.

---

### Post by Sydius on 2008-05-27
My girlfriend can't hibernate or suspend her Asus laptop, either.  When she comes back, it goes to a tan screen and nothing works.  It's very frustrating to her as well.

---

### Post by KingTermite on 2008-05-27
> **Sydius said:**
> My girlfriend can't hibernate or suspend her Asus laptop, either.  When she comes back, it goes to a tan screen and nothing works.  It's very frustrating to her as well.

Mine hibernates when I force it to hibernate (by button). It's only when it goes to hibernate from idle that it goes fubar. It seems the display does not return. By the lights, I think the computer is waking up ok.

---

### Post by KingTermite on 2008-07-05
Well, this never did get resolved. Never found a solid way to make it not go fubar when it went idle. Even when I tried to set it not to hibernate on idle, it still locks up and forces a reboot.

It's only on rare occasions this is an issue. I can force it to hibernate if I'm not doing anything and won't be back for a while, but its biting me when I'm trying to do a large download and leaving computer alone, so.......

I took matters in to my own hands. I wrote a program to simulate mouse events and keep it alive if I want it to. I even built in a possible timeout, so you can still let it stop and go idle after a while.

See this thread [http://ubuntuforums.org/showthread.php?t=850482](http://ubuntuforums.org/showthread.php?t=850482)

---

