---
title: "ubuntu was ruining my computer"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by apple freak ubunt uuser on 2012-02-03
when first installing ubuntu using wubi, it didn't load and the screen didn't get any signal, so i did hold the start button for 5 seconds:mad:. when starting up again i booted windows and it did cost windows startup repair an hour to repair the damage:eek:. trying again.

(:-$sorry for my bad english, but i'm just a 13 year old student starting to hate windows and wanting to be a litle nerdy.)

---

### Post by bcbc on 2012-02-03
It's never a good idea to hard power off a computer. What was likely happening was that - even though it appeared hung up because the screen was off - there was background disk access going on. When you cut off power at this time, file corruption may occur - and this is regardless of what OS you are running (if you have a disk activity light on the computer, you can probably see if something is happening in the background)

In general with Linux, whenever you need to hard reset you should first attempt: [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot")

I recommend posting your computer brand/model and particularly your graphics card. Usually when you have this sort of issue it's because of the graphics card e.g. nvidia, some radeons. You can usually get around it with the 'nomodeset' kernel boot option (for more info [see here]("http://ubuntuforums.org/showthread.php?t=1613132") and note Wubi-specific instructions in post #8 )

---

