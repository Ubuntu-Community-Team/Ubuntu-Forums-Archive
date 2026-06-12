---
title: "ImageColorTransparent not working with GIF"
date: 2010-01-28
forum: Programming Talk
---

### Post by cronick on 2010-01-28
Hello,

I am planning to move a website from my current Cent OS server, to a new VPS with Ubuntu installed. One problem I have noticed is that the PHP GD function ImageColorTransparent does not work successfully when I output the image as GIF. For some reason it works allright when PNG is outputted. 

The weird thing (at least in my opinion) is that it all works great on my current Cent OS server, but on the new Ubuntu driven VPS it simplet wont work no matter what I do.

Has anyone else also experienced this and know what potentially can be done?

---

### Post by CyberJack on 2010-01-28
Can you show some code?

I also had a problem with transeparency with gd on a ubuntu vps. Although I recompiled PHP (the gd problem with 9.04) transparency was not working properly. 

My problem wasn't with the ImageColorTransparent function but with the imagecolorallocatealpha function.

---

### Post by hessiess on 2010-01-28
Just use PNG, GIF's 1 bit transparency looks terrible and most browsers (minus the antique IE6) support PNG fine.

---

### Post by cronick on 2010-01-28
> **CyberJack said:**
> Can you show some code?

I also had a problem with transeparency with gd on a ubuntu vps. Although I recompiled PHP (the gd problem with 9.04) transparency was not working properly. 

My problem wasn't with the ImageColorTransparent function but with the imagecolorallocatealpha function.

The code is completely standard. Regardsless of the use of the function, it simply wont work with GIF. 

I guess I will just go with PNG from now on. I just wanted to hear if there were any solution to this.

---

### Post by korvirlol on 2010-01-28
> **hessiess said:**
> Just use PNG, GIF's 1 bit transparency looks terrible and most browsers (minus the antique IE6) support PNG fine.

there is a markable difference between how IE7 and 8 render PNGs compared to any other half decent browser. 



Otherwise, no reason not to just go with png

---

### Post by cronick on 2010-01-29
After experiencing other weird GD problems I decided to not give up that easy. So I recompiled php with bundled support for GD and that apparently did the trick. 

Now it works just as it should with GIF. I guess there must have been some sort of a bug in the install og PHP I got on my VPS server. 

A plus is that I now have the ability to rotate images with "ImageRotate". For some unreasonable cause it does not come with the un-bundled version.

---

