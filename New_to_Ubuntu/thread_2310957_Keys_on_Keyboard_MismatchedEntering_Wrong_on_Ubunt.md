---
title: "Keys on Keyboard Mismatched/Entering Wrong on Ubuntu"
date: 2016-01-23
forum: New to Ubuntu
---

### Post by Gabriel_Saul on 2016-01-23
I noticed an issue with the keys on Ubuntu. FIrst, it was when I was  testing Ubuntu through the LiveCD without installing. Certain keys, when  entered, created the wrong character. Notably, the key for the tilde  and hash comes up as a vertical bar and a backward slash; and the key  for the backward slash and vertical bar comes up as chevrolets. There  are also a few other instances for other keys. It seems to be specific  for symbols. Letters and numbers aren't affected.

Anyway, after installing (3 days ago), and getting to grips with Ubuntu,  the issue seemed to disappear. However, upon logging in today, it is  happening again. Most notably, the hash/tilde key is coming up as a backslash, and Shift-3 is where hash resides. I can't seem to find any shortcut in the system settings that causes a change in layout, nor can I find a way to customise my layout and change it back to default.

How can I fix this? 

Thank you,

GS

---

### Post by Gabriel_Saul on 2016-01-23
Solved the issue itself with the "setxkbmap -layout gb" command in terminal.

I'd still like to know what the possible cause of this may be, however. 

Thank you,

GS

---

### Post by grahammechanical on 2016-01-23
It is all to do with the keyboard language & layout.

During installation we set the default language and the default keyboard layout. In my case I set English (UK) on an extended Winkeys (105 keys) type keyboard. And after installation I get two keyboard layouts - English (US) & English (UK) and I can switch between the two. Personally, I always remove the US layout.

It could be that you are inadvertently triggering the keyboard short cut that switches keyboard layouts. Pressing Super + space will do it. We can add & remove languages in System Settings>Language support and add & remove keyboard layouts in System Settings>Text Entry. 

Regards.

---

### Post by Gabriel_Saul on 2016-01-23
> **grahammechanical said:**
> It is all to do with the keyboard language & layout.

During installation we set the default language and the default keyboard layout. In my case I set English (UK) on an extended Winkeys (105 keys) type keyboard. And after installation I get two keyboard layouts - English (US) & English (UK) and I can switch between the two. Personally, I always remove the US layout.

It could be that you are inadvertently triggering the keyboard short cut that switches keyboard layouts. Pressing Super + space will do it. We can add & remove languages in System Settings>Language support and add & remove keyboard layouts in System Settings>Text Entry. 

Regards.

Thank you very much for clearing that up for me.

I imagine I accidentally trigger the shortcut for switching layouts when I enter my password (which contains a lot of different characters, hence a lot of keys are involved in typing it). I'll remain wary of this. In any case, however, I know exactly how to switch it back, via command line or going into the System Settings.

Thanks again for explaining the cause,

GS

---

