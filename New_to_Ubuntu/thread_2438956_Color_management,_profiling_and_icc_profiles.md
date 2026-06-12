---
title: "Color management, profiling and icc profiles"
date: 2020-03-20
forum: New to Ubuntu
---

### Post by pkr19792 on 2020-03-20
Hi all,

I was trying to make a new icc profile using Argyll and Im not sure if it was successfull or not:
[ATTACH=CONFIG]285244[/ATTACH]
I dont really understand what that message means?
Nonetheless, the profile was downloaded to the icc folder and I was able to activate it in the color setting.

This brings me to the next question - whenever I start Ubuntu it seems to generate a profile. Is this the case? And what is the purpose? Do I need to activate my calibrated profile every time I turn on the computer?

And my 3 question. I have saved some other profiles there as well (profiles based on IT8 targets for scanning slides). These dont show up in the color settings. Clearly Im not activating these as my monitor profiles, but I run PhotoLine in Wine and it seems like they need to be activated somehow for PhotoLine to use these profiles? How do I do that? The profile I made using Argyll activated by itself.

Cheers
Peter

---

### Post by pkr19792 on 2020-03-21
The solution to the first part (screen shot) was solved by installing Gnome color manager and re-installing the profile.

---

### Post by pkr19792 on 2020-03-21
As for the last issue - the profiles had to be stored in the appropriate folder in Wine.

---

### Post by russellcottrell on 2020-03-23
[FONT=book antiqua]Hello; I put my display profile into the following folder and run this Startup Applications entry:
dispwin /home/username/.local/share/icc/monitor.icc

(dispwin of course is one of the Argyll programs.)

Then in the PhotoLine color management device options, I just set Screen to System.  It seems to work; you can test it by running dispwin using some other profile such as ProPhoto, and everything, including PhotoLine, changes colors.

And, yes, if you want to use other profiles, just put them into the PhotoLine ICCProfiles folder.
[/FONT]

---

### Post by pkr19792 on 2020-03-23
Thanks Russell - appreciate it. You make it easy to switch to Ubuntu.

---

