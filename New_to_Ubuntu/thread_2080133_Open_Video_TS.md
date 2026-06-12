---
title: "Open Video_TS"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by Davethehedgehog on 2012-11-03
Just upgraded to Ubuntu 12.10 and I find I can't open Video_TS folders.
In 12.04 I simply had to double click.
Any ideas?

---

### Post by newb85 on 2012-11-03
When you say you "upgraded" do you mean you used the upgrade tool in Update Manager, or did you do a fresh install?

---

### Post by NikTh on 2012-11-03
> **Davethehedgehog said:**
>  I find I can't open Video_TS folders.
In 12.04 I simply had to double click.
Any ideas?

Video Ts folders refers to DVD/Restricted formats. 

Take a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

because if you upgraded through update-manager maybe some packages removed. 

Thanks

---

### Post by Davethehedgehog on 2012-11-03
> **NikTh said:**
> Video Ts folders refers to DVD/Restricted formats. 

Take a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

because if you upgraded through update-manager maybe some packages removed. 

Thanks
Thanks for the responses. 
I used upgrade manager to do the upgrade.
I checked the link suggested by NikTh, but, according to Synaptic I've got the required packages installed.

---

### Post by newb85 on 2012-11-03
Shot in the dark:
Have you tried re-running this?
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Davethehedgehog on 2012-11-04
> **newb85 said:**
> Shot in the dark:
Have you tried re-running this?
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Thanks for the shot in the dark, newb85.
Unfortunately, it didn't find the target.
Any more thoughts would be appreciated.

---

### Post by Davethehedgehog on 2012-11-06
I have solved the problem in the sense that I have re-installed 12.04 on my desktop and videos are no problem.

With reference to newb85's original response, I did a fresh install of 12.10 on my laptop.  Unfortunately, this hasn't solved the video problem.

---

