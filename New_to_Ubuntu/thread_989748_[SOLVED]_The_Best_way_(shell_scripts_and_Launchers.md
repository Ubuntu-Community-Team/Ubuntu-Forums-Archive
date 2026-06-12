---
title: "[SOLVED] The Best way (shell scripts and Launchers)"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Wisp558 on 2008-11-21
So. I'm running ePSXe through wine (no end of trouble with the native Linux version... *sigh*... 

I've found that it will see plugins ONLY if I cd to the directory first. 

So, instead of a launcher, I've jury-rigged a sh script that reads

cd /[Directory of ePSXe]
wine ./ePSXe.exe

which is great. (It's in my XP partition)

what I want to know, is, how can I get rid of the annoying "Do you want to display or execute?" Window? is it a special kind of launcher? can I add multiple commands to a launcher? 

Thanks much, wisp558

---

### Post by kerry_s on 2008-11-21
```
exec wine ./ePSXe.exe
```

---

### Post by Wisp558 on 2008-11-21
I feel stupid now. I didn't use your method... I just had the launcher run the script.

D'OH!

---

