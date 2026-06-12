---
title: "Pidgin Sound Problems"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Takeenvy on 2008-07-29
Heya!! Quick question: Whenever I'm on Pidgin messenger the sound works in the beginning but if I open a page that has sound on it Pidgin's sound quits working, even after I leave the page. Is there a way to solve this?? Thank you muchly to anyone in advance!! :p

---

### Post by iaculallad on 2008-07-29
> **Takeenvy said:**
> Heya!! Quick question: Whenever I'm on Pidgin messenger the sound works in the beginning but if I open a page that has sound on it Pidgin's sound quits working, even after I leave the page. Is there a way to solve this?? Thank you muchly to anyone in advance!! :p


Opening a page? Does that mean a webpage with built-in flash files? If that's the case, you probably need to install the sound wrapper for the non-free flash plugin.

```
sudo apt-get install libflashsupport
```

---

### Post by Takeenvy on 2008-07-29
> **iaculallad said:**
> Opening a page? Does that mean a webpage with built-in flash files? If that's the case, you probably need to install the sound wrapper for the non-free flash plugin.

```
sudo apt-get install libflashsupport
```

Huh. I tried but it didn't work. I even made sure to sign off and back on again but it didn't do anything for me. (And thank you for answering me, you answered my question last time as well!! :) )

Any other ideas maybe?? I appreciate it!!

And yes a webpage. Like if I go to someone's myspace page and it plays music or I watch a video on youtube the sound on Pidgin will stop playing.

---

### Post by KWM987 on 2008-07-30
> **iaculallad said:**
> Opening a page? Does that mean a webpage with built-in flash files? If that's the case, you probably need to install the sound wrapper for the non-free flash plugin.

```
sudo apt-get install libflashsupport
```
I'm having the same problem, everytime I view, say a YouTube video, the sound on Pidgin cuts out, after I close the page sound comes back.  

I was wondering about the wrapper though; it says it is a wrapper for Flash to PulseAudio, I have everything configured to ALSA, would this wrapper be counter productive in this case?

---

### Post by adobrakic on 2008-07-30
Did you try going to System > Prefs > Sound

and change the tabs to ALSA?

---

### Post by KWM987 on 2008-07-30
> **adobrakic said:**
> Did you try going to System > Prefs > Sound

and change the tabs to ALSA?
Yes, I have everything there set to ALSA, and sounds in Pidgin set to ALSA

---

### Post by s0l1dsnak3123 on 2008-09-28
I have this problem too, is there a fix in intrepid?

---

### Post by ftmichael on 2008-10-26
I'm having the same issue with Intrepid RC at the moment.  See [http://ubuntuforums.org/showthread.php?t=954447&page=2](http://ubuntuforums.org/showthread.php?t=954447&page=2) for more.

Michael

---

### Post by jeremy on 2008-12-15
This worked for me:

Pidgin, select Preferences from the Tools menu
...Sounds tab
...Method drop down list, select Command
...Sound command text box, enter: aplay %s

---

### Post by citi on 2008-12-31
Whenever I'm using Pidgin, the sound cuts out after I get a certain number of replies, and after another certain number the program closes completely. This happens to me on multiple computers. Anyone know how to fix?

---

### Post by plantatree on 2011-02-15
> **jeremy said:**
> This worked for me:

Pidgin, select Preferences from the Tools menu
...Sounds tab
...Method drop down list, select Command
...Sound command text box, enter: aplay %s

Haha, I also found out that. Strange that ALSA doesn't work in pidgin directly...

---

