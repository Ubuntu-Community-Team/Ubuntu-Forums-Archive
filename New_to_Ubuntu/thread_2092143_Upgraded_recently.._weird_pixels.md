---
title: "Upgraded recently.. weird pixels"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by schaumie2222 on 2012-12-06
I just upgraded recently to quantal and all of a sudden I get these lines of pixels all throughout my open windows. I am absolute beginner to ubuntu, I use it just for internet and downloading so dont know many commands and such. I didnt like the home screen how all the icons were lined up on the left so I did search and found something to change it back to the oneiric way where I logoff and switch to "gnome" or something like that so im not sure if this is what caused it but attached in a picture of it

---

### Post by Impavidus on 2012-12-07
Your problem is difficult to see on the screenshots (partially because jpeg format always produces weird pixels, use png next time), but most of the time it's caused by buggy graphics drivers. It's not caused by your desktop environment. I had similar problems after upgrading to 11.04, 11.10 and 12.04, which were solved after some regular updates. That's the reason why I'm planning to stay with 12.04 LTS for a while.

Depending on your graphics card (can you post the model you use?), other drivers may be available. Search for non-free drivers (that's non-free as in no freedom of speech, still free of charge). Otherwise, wait a few weeks for bug fixes. People are probably already working on it.

If you just use your machine for internet and downloading it would have been better to stay with 12.04. It will be supported until 2017.

---

### Post by audiomick on 2012-12-07
> **Impavidus said:**
> Your problem is difficult to see on the screenshots...most of the time it's caused by buggy graphics drivers....

In fact, if the problem is the graphic drivers, it will not be visible when viewing the screenshot on another machine. The screenshot is a picture of the signal that is being sent to the graphic drivers. If it is the  drivers that are playing up, one can assume that the signal that is being sent to them is still ok, and therefore that no problem will be visible when viewing the screenshot on a healthy machine.

I am on a netbook with a rather small screen, so I can't be sure, but I can't see anything in those screenshots that I couldn't attribute to .jpg artefacts. Therefore, I think the suggestion that the graphics drivers are at fault is probably a good one.

Do post the model name of your graphics card.  If you don't know exactly, open a terminal and do
```
sudo lshw -C video
```
you will be asked for your password. Type it in and hit enter. You wont see what you are typing, but it is being accepted. The command lshw generates a listing of your hardware. Using "-C video" to modify it tells it to just list the video stuff.

---

### Post by schaumie2222 on 2012-12-07
geforce 8600 gts... I am not a big fan of this version for other reason, what is the easiest way to rollback ... i am also dual booting windows and have a lot of documents I cannot lose

---

### Post by audiomick on 2012-12-07
That is nVidia, isn't it? Are you using the nVidia proprietary driver?

There is no easy way to roll back the version of Ubuntu. You have to fresh install the older version.

---

