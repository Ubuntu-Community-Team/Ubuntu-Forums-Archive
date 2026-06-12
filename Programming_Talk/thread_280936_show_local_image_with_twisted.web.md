---
title: "show local image with twisted.web"
date: 2006-10-20
forum: Programming Talk
---

### Post by G|N| on 2006-10-20
I want to be able to display an image that is located in my home directory in a twiste.web web page.

for example:
i have a picture in my home dir, like this: /home/me/pic.jpg
but when i use the img tags like this: <img src="/home/me/pic.jpg" /> it can not find the image.

so what path/function/solution do i have to use to show the image?

---

### Post by cwaldbieser on 2006-10-21
> **G|N| said:**
> I want to be able to display an image that is located in my home directory in a twiste.web web page.

for example:
i have a picture in my home dir, like this: /home/me/pic.jpg
but when i use the img tags like this: <img src="/home/me/pic.jpg" /> it can not find the image.

so what path/function/solution do i have to use to show the image?

Could you post the code?  It sounds like you are publishing the HTML to your HTTP server but not the image.

---

### Post by G|N| on 2006-10-21
I think i found a solution.
I create a symbolic link to every image and just store the links in the dir caches_images/ so the html would look like this:
<img src="cached_images/link_to_image" /> and it works very well!

---

