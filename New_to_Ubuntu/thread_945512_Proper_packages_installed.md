---
title: "Proper packages installed?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by RussW210 on 2008-10-12
Hello,

I just wanted to make sure I have the proper packages installed.  I was playing around with my graphics drivers the other day with someones assistance but switched back over to the Envy Driver.  The following was done:

- Instructed to install libstdc++5, which also installed "non-free-codecs" and "w32codecs".  Upon realizing I had libstdc++6 installed, I removed all three packages.

- Removed "linux-headers-2.6.24-19-gener" because I have "linux-headers-2.6.24-19" installed.  This also removed "linux-headers-generic".

Have I done the correct thing?  The reason why I ask is because my Cairo Dock seemed to be having problems responding to my mouse-over on startup.

Thanks

---

### Post by RussW210 on 2008-10-12
"uname -r" returns "2.6.24-19-generic"...

I am just worried that I got rid of something that I will need and I removed "linux-headers-generic-2.6.24-19-gener" and "linux-headers-generic".

But at the same time I don't want to installed two different versions of the same package because that might be what is making my Cairo Dock respond weird on startup.

---

### Post by SunnyRabbiera on 2008-10-12
Yeh i cannot say as I am not an expert on this sort of thing as i dont use a fancy graphics card... just a intel one.
Just be very careful right now, I dont want to see you go into a kernel panic.

---

