---
title: "Some indicators are now styled differently. Why?"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by vasa1 on 2012-08-15
I installed Xfce 4.10 on Ubuntu 12.04 and am using the Greybird theme modified to my needs. All was well until yesterday but then I noticed that a couple of "indicators" in the top panel appear to be styled differently from what they were previously.

The only thing I can think of is that there was an update of light themes (Ambiance and Radiance). Why this should affect me, I'm not sure.

I'm including a composite image to show drop-down menus when I right-click on items in the top-right of the screen:
clock
battery indicator
network manager indicator
and
system load indicator

The clock and battery indicators are as previous and are the way I want. The line on which the mouse cursor rests is a dark gray.

The network manager and system load indicator seem different. The highlight is now orange and the text color is different. I'm suspecting the update to light themes has something to do with it but I don't know how or why.

I've also included the drop-down of the Applications Menu and of gedit. Those two are the way I set them up.

Does anyone who has accepted the light-themes update see what I'm seeing and, if so, is there any fix that I can apply?

---

### Post by vasa1 on 2012-08-15
I'm seeing that just the same two indicators, network manager applet and System load indicator, are behaving differently with two other themes, Orion and Zukitwo.

When I try Ambiance or Radiance, the two light themes that seem to have been part of the light-themes update, all indicators and other apps behave the same as the two indicators mentioned above.

---

### Post by vasa1 on 2012-08-15
Oops! Looks like I showed the gedit bit twice :(

Anyway, it maybe that somethings need not just a switch of themes but a log out and log in. I 'm not sure. But this morning, on restarting the computer, I don't see the orange selected_bg_color. Some other, minor, differences are still there.

---

### Post by vasa1 on 2012-08-20
It's because I was basing my expectations on ~/.themes. The two indicators that were bothering me load at **start up** and are unaffected by changes in ~/.themes. I need to edit stuff in /usr/share/themes/ and not in ~/.themes.

---

### Post by vasa1 on 2012-08-22
The solution for how to use themes in ~/.themes is [here]("http://ubuntuforums.org/showpost.php?p=12182997&postcount=2"). Making those symbolic links helps :)

---

