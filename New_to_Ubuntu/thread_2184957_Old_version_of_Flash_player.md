---
title: "Old version of Flash player"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by Toni_Vines on 2013-10-31
OK, after much research and hair pulling I've found why I can't get Flash Player to work. I'm running an old AMD Athlone 2800xp machine and apparently Flash does not get on with the cpu. 
I've downloaded Flash Player 9 from the Adobe archive but I really need someone to work me through how to uninstall the current Flash Player and then get this one installed. 
Sorry if I seem a bit thick but I'm very new to this (but really enjoying learning!).
Thanking you,
Toni.

---

### Post by kostkon on 2013-10-31
Sorry, but I would NOT recommend it at all, that version is too old and full of many vulnerabilities, it's totally unsafe to use.

Is it a CPU that doesn't support SSE2?

---

### Post by Toni_Vines on 2013-10-31
> **kostkon said:**
> Sorry, but I would NOT recommend it at all, that version is too old and full of many vulnerabilities, it's totally unsafe to use.

Is it a CPU that doesn't support SSE2?

Yes! Is there any way around this? 
Cheers,
Toni.

---

### Post by kostkon on 2013-10-31
> **Toni_Vines said:**
> Yes! Is there any way around this? 
Cheers,
Toni.
Not really, other than upgrading your CPU or stop using Flash; 2nd option is easier..

---

### Post by Impavidus on 2013-10-31
I think you can just plug in the binary where the automatically installed one is (/usr/something/mozilla/something/plugings/, don't know exactly), but it will be insecure. Keep flash disabled unless you really need it.

---

### Post by merlyn2748 on 2013-10-31
I don't know if you are married to your browser, but you might want to try Google Chrome.  Not Chromium since Pepper flash is not included in the non Google branded version.  That may allow you to still use flash.  You can get a .deb package from going to [www.google.com](www.google.com) and clicking the blue button on the upper right hand corner of the window.  If you are married to using your current browser then you may have to learn to live without flash.

Good Luck,
Justin

---

### Post by deadflowr on 2013-10-31
> **merlyn2748 said:**
> I don't know if you are married to your browser, but you might want to try Google Chrome.  Not Chromium since Pepper flash is not included in the non Google branded version.  That may allow you to still use flash.  You can get a .deb package from going to [www.google.com]("http://www.google.com") and clicking the blue button on the upper right hand corner of the window.  If you are married to using your current browser then you may have to learn to live without flash.

Good Luck,
Justin

It's not a browser problem.
It's a flash needing SSE2 and the PC in question doesn't support it.
Pepperflash won't help.

---

