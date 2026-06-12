---
title: "nVIDIA somthing or other..."
date: 2008-09-23
forum: New to Ubuntu
---

### Post by MikesGuitar on 2008-09-23
I just installed ubuntu and I keep trying to change the visual effects to normal and it cant do it? Anyone ever get this? I could use the help..

---

### Post by TriSwords on 2008-09-23
Have you enabled restricted drivers if it is an nVidia card?

System > Administration > Hardware Drivers

Enable the nvidia driver (not sure the name it will show up as in the list)

Restart, and if all went well it should let you use desktop effects.

---

### Post by MikesGuitar on 2008-09-23
Yup tried that, it begins to download but a message pops up saying some error. I also have vista on my laptop and there was an option update for the card so i tried that but it didnt work

---

### Post by neverett on 2008-09-23
Mine won't install the driver at all after the recent updates today.

---

### Post by Nepherte on 2008-09-23
If hardware drivers doesn't work, try envy. To install it:
```
sudo apt-get install envyng-gtk
```

With this you can install nvidia/ati drivers. To run it in a terminal:
```
envyng -t
```
or in a gui:
```
envyng
```

I suggest you first choose the option to remove any nvidia driver before installing a new one.

---

### Post by Orange_and_Green on 2008-09-23
> **neverett said:**
> Mine won't install the driver at all after the recent updates today.

I have an nvidia card too and when the update for kernel version 2.6.24-19 came the driver got completely broken. Have you tried loading a previous version of the kernel? (I'm still on 2.6.24-18, I know I should try and see if 2.6.24-19 works by now but I'm just too lazy I guess:lol:)

---

### Post by MikesGuitar on 2008-09-23
> **Nepherte said:**
> If hardware drivers doesn't work, try envy. To install it:
```
sudo apt-get install envyng-gtk
```

With this you can install nvidia/ati drivers. To run it in a terminal:
```
envyng -t
```
or in a gui:
```
envyng
```

I suggest you first choose the option to remove any nvidia driver before installing a new one.

What exactly will I be doing if I do this? I know I have the nVidia becuase I have run updates to it through Vista, and Im pretty sure I dont want remove it....

---

### Post by kpkeerthi on 2008-09-23
envy installs drivers for nvidia cards. It will not remove the driver you already have in Vista.

---

### Post by MikesGuitar on 2008-09-23
Thanks everyone, this forum is a lifesaver, would have NO idea whatsoever if not for this!!

---

### Post by MikesGuitar on 2008-09-23
Hey I tried to do that command in terminal but when it asks for my password i cant type it in? am I doing something wrong? is there some procedure when typing in terminal?

---

### Post by Mornedhel on 2008-09-23
The password you enter when using sudo will not show, even as asterisks.

---

### Post by MikesGuitar on 2008-09-23
Then how do I know if I entered the right one, will it just accept it?

---

### Post by MikesGuitar on 2008-09-23
Nevermind I got it to work but it said some error message did not install anything what to dizzle?

---

### Post by Nepherte on 2008-09-23
And what is the error message exactly?

---

### Post by SarahMarieNC2 on 2008-09-23
> **Nepherte said:**
> And what is the error message exactly?

I'm having this same problem. I copied my error message. Maybe this is the same one he is getting?



W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_amd64.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_amd64.deb)
  404 Not Found

---

### Post by MikesGuitar on 2008-09-23
Thats the exact same message I keep getting!

---

### Post by anotherdisciple on 2008-09-23
You may need to make sure you have the backports repository enabled.

```
sudo gedit /etc/apt/sources.list
```

Find the backports section and remove the pound sign (#) from in front of those 2 lines.

Then do a:

```
sudo aptitude update
```

Let me know if that worked.

---

### Post by MikesGuitar on 2008-09-23
I got a list up but I am not sure what exactly im looking at/for

---

### Post by MikesGuitar on 2008-09-23
I got it! Thanks a lot man

---

### Post by anotherdisciple on 2008-09-24
Cool... did that fix it? I was assuming that is was trying to download software that was in that repo...

---

### Post by SarahMarieNC2 on 2008-09-24
> **anotherdisciple said:**
> Cool... did that fix it? I was assuming that is was trying to download software that was in that repo...

GOsh I hope I did that right. LOL! Yah my back repository wasn't enabled either, had those pound signs in front of them as well. So I hope that fixed it. We'll see in a minute. Thanks!

-----------------------

Edited to Add: Thanks sooo much! This is working. Updating the drivers as I type. Yayyyy! Finally something is going right!

---

