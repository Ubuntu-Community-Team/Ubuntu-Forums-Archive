---
title: "Firefox crash on Flash websites."
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-23
I just tried to access steampowered.com, only to have Firefox crash multiple times trying to access it. It seems that no matter how much I try, Firefox and Flash for Linux are just so inherently flawed and bejumbled that there is no perfect way to achieve any sort of functional zen between them. If anyone has a solution, please help.

Running:
Firefox 3
Flash 10
Gecko media player addon.

I hope for the love of all that is holy that these issues are fixed with 8.10.

---

### Post by mevets on 2008-09-23
In my experience, flash 10 is just crashy on linux. You might want to consider downgrading to flash 9.

Also, you didnt mention anything about audio problems, but since its so common I have to ask whether you think you are having problems with pulseaudio. Maybe you run totem to watch a movie then surf to youtube and get no sound. If so, you might want to tell ubuntu to use ALSA instead of pulseaudio.

---

### Post by NoReflex on 2008-09-23
This has solved it for me : 
```
sudo apt-get install libflashsupport
```

Best wishes,
NoReflex

---

### Post by Joeb454 on 2008-09-23
You aren't running 64 bit Ubuntu by any chance are you?

---

### Post by NoReflex on 2008-09-23
> **Joeb454 said:**
> You aren't running 64 bit Ubuntu by any chance are you?
Ubuntu Hardy 32 bit here...

---

### Post by kansasnoob on 2008-09-23
Look at post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

---

### Post by Joeb454 on 2008-09-23
> **NoReflex said:**
> Ubuntu Hardy 32 bit here...

I was asking the OP mainly :p Flash is more of an issue with 64 bit.

I'm still using Flash 9 on my 32 bit install

---

### Post by Grimhound on 2008-09-23
32 bit. Tried using Flash 9, but Flash 10 was used and has made more work stabley. Still jittery and crashy.

---

### Post by tuxxy on 2008-09-23
I have no problems with Flash on 64-bit, this post is a good example to show its not just a 64-bit issue.

---

### Post by ethyreal on 2009-03-03
> **NoReflex said:**
> This has solved it for me : 
```
sudo apt-get install libflashsupport
```

Best wishes,
NoReflex

that fixed me too!

more specifically this is the new package that replaces libflashsupport, but it still does the trick.

```
sudo apt-get install flashplugin-nonfree-extrasound
```

---

