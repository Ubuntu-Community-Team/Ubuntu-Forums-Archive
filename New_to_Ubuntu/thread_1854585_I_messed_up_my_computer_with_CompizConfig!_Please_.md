---
title: "I messed up my computer with CompizConfig! Please help!"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by TigrisAltaica on 2011-10-04
Hi! I tried using compiz config setting manager and started fooling around with it. After activating a few plugins, I can't see the launcher or anything other than my desktop walpaper. Also, all keyboard shortcuts are disabled, I can't open a terminal or anything else to try and load it up again. What can I do?

---

### Post by mike daly on 2011-10-04
That makes 2 of us shooting our feet.  I unchecked UNITY PLUGIN in an effort to revert to the classic desktop.  Running now with live cd on thumb drive.  

Any thought on reversing would be appreciated

---

### Post by garvinrick4 on 2011-10-04
Can give this a go.
```
 unity --reset
```

---

### Post by TigrisAltaica on 2011-10-04
That just results in an error message.

---

### Post by madjr on 2011-10-04
**muahahah more victims !!!**


JK :) try this: 
[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by garvinrick4 on 2011-10-04
> That just results in an error message.
What is error message?

---

### Post by TigrisAltaica on 2011-10-04
I logged into safe mode and changed the settings there but when I logged back into regular ubuntu it was still wrong. However, after doing so I was able to open a terminal and tried the command again. It seems to have worked. THANK YOU.

---

### Post by wildmanne39 on 2011-10-04
Hi, also if you want to setup the cube and effects in 11.04 click on the link in my signature that says setting up the cube and effects it is a step by step guide with pictures, and at the bottom there are directions to reset unity and compiz.
Thank you

---

### Post by garvinrick4 on 2011-10-04
> I logged into safe mode and changed the settings there but when I logged  back into regular ubuntu it was still wrong. However, after doing so I  was able to open a terminal and tried the command again. It seems to  have worked. THANK YOU.Your welcome enjoy your Ubuntu TigrisAltaica.
## EDIT: Can you marked this thread as Solved in upper right in Thread tools, as others with same seem to be prevalent when messing with compiz config.
Might be of help to others with same. Thank You

---

### Post by mike daly on 2011-10-04
Well I got mine working again.  In live cd session I reran compiz config and after I exited out, Unity was back.  Also read about two commands  **GDM RESTART**  and **GDMSETUP** in another post.  

GDMSETUP let me switch to the classic view which is how I got in trouble on the first place.

---

### Post by garvinrick4 on 2011-10-04
>  
Well I got mine working again.
 
Very good mike daily, Welcome to the Forums and happy you fixed your install.

---

