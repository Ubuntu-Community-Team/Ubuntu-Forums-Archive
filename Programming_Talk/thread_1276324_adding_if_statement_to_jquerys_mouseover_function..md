---
title: "adding if statement to jquerys mouseover function."
date: 2009-09-26
forum: Programming Talk
---

### Post by hockey97 on 2009-09-26
HI, I am using jquery. I am making a fade in and out menu that when the mouse is over the users image a menu fades in and if the mouse is over the menu once the mouse leaves the menu  fades out.


What is currently happening is that I have a menu background and the image links. If you put your mouse over the image links the menu and image links would fade out. 

I want it in a way where the fade out will only occur only if the mouse is not on the menus background nor on the image links.  

what should I do?  I was thinking to try and use a if statement but tried many things and still dosen't work.

---

### Post by korvirlol on 2009-09-27
Sounds like you just need to use selectors:

$(*selector*).mouseover(function(){
    the animation you want
});

$(*selector*).mouseout(function(){
    mouse out animation
});

---

