---
title: "Unity"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by czgirb on 2012-08-13
Currently I used **Avant dock** in **Unity desktop environment** ... and set the left panel in **AutoHide** mode. But everytime when I minimized an application, it will be minimized in left panel, not in Dock. So, I tried to un-check the **unity plugin** from ccsm ... wow! the top panel is also disappeared. Actually, I love the Unity but I hate the icon's size limitation.

1. Is it possible for us to reduce the icon's size? I wish it was **20** or **25**px.
2. How to make all opened applications are minimized in** Avant**, and not** Unity**?
3. How to **remove the left panel** without **remove the top panel**?

---

### Post by Kopkins on 2012-08-13
I'm not aware of any ways to remove the left panel. You can resize the left panel down to 32 pixels. In 12.04, settings > appearance, and then use the slider at the bottom to change the size of the panel. 

If not using 12.04 I believe you can still use Ubuntu Tweak to change the size of the left panel.
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Kopkins

---

### Post by czgirb on 2012-08-13
> **Kopkins said:**
> I'm not aware of any ways to remove the left panel. You can resize the left panel down to 32 pixels. In 12.04, settings > appearance, and then use the slider at the bottom to change the size of the panel. 

If not using 12.04 I believe you can still use Ubuntu Tweak to change the size of the left panel.
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```Kopkins

Beside** Ubuntu Tweak**, I also installed **MyUnity** and **CCSM**.
But no one can make it **below 32px**.

---

### Post by Kirboosy on 2012-08-13
32 pixels is as small as you can go. You can resize it with Ubuntu-Tweak or you can natively change it under 

Settings-->Appearance-->Look-->Launcher Icon Size


Hope that helps!

---

### Post by czgirb on 2012-08-13
> **Caboose885 said:**
> 32 pixels is as small as you can go. You can resize it with Ubuntu-Tweak or you can natively change it under 
Settings-->Appearance-->Look-->Launcher Icon Size
Hope that helps!

I said ... no one can make it **below 32px**.
I wish it was **20px** or **25px**

---

### Post by vasa1 on 2012-08-13
> **czgirb said:**
> I said ... no one can make it **below 32px**.
I wish it was **20px** or **25px**

Yes we know that. Maybe you should file a feature request @ Launchpad.

---

### Post by Kirboosy on 2012-08-13
> **czgirb said:**
> I said ... no one can make it **below 32px**.
I wish it was **20px** or **25px**

I think we just happened to post at the same exact time because I didn't see your post when I posted a response.

Alas maybe in the future we will be able to customize it a little bit more

---

### Post by NikTh on 2012-08-13
Hi , 
I agree with above posts , you cannot resize below 32px and will be good to fill a future request. 

Also it is not required (at 12.04)  to install ubuntu-tweak or ccsm to change the size of launcher icons . You can do it by 
Dash > Appearance > Launcher icon size. 
Thanks

---

