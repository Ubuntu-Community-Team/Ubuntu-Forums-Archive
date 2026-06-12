---
title: "Ubuntu 11,10 classic dekstop and compiz"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by Sietse on 2011-12-31
Can anyone tell me how to properly get compiz to work in ubuntu 11.10 with classic gnome?

After i run compiz the window borders dissapear and i dont know how to fix this. 

If anyone could help me with this, thanks in advance.

---

### Post by wildmanne39 on 2011-12-31
Hi, have a look at the second link in my signature for setting up compiz it should help.
Thanks

---

### Post by Sietse on 2011-12-31
Im sorry the link does not help me. The only problem is the window manager crashes on loading compiz. All my window borders and buttons dissapear. I need the solution for that.

In your guide im getting stuck at the part where you must update you repository. Apt complains it cannot find everything.

---

### Post by wildmanne39 on 2011-12-31
Hi, will you please take a screenshot of your desktop and windows so we can see exactly what it looks like? 

If it is what I think it is go down to > Window Decorators & The Commands To Start Themin the guide and restart the window decorations.
Thanks

---

### Post by grahammechanical on 2011-12-31
Excuse me, but what do you mean by "classic gnome?" 

Do you mean the look of the desktop before Unity was made the User Interface? Do you mean Gnome shell or Gnome session fall back?

Compiz is the compositing or window manager for Unity. Gnome shell and Gnome session fall back use Metacity.

It depends on what you mean by "classic gnome. " It may mean that you cannot use Compiz.

Have you seen these links?

[http://ubuntuforums.org/showthread.php?t=1859961]("http://ubuntuforums.org/showthread.php?t=1859961")

[http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html]("http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html")

I am just not sure that Compiz will work with classic gnome.

Regards.

---

### Post by wildmanne39 on 2012-01-01
Hi, here is a link for a video on setting up effects in gnome classic fallback.
[http://www.youtube.com/watch?v=wLTq7J3URSI](http://www.youtube.com/watch?v=wLTq7J3URSI)
I hope this helps.
Thanks

---

### Post by Sietse on 2012-01-01
Wildmanne i followed you guide, and still got the same window border problem. But there is a nice extra session to choose from now. 

Someone said something about a part in the guide about window decorators, it could be me but i am not finding it.

---

### Post by wildmanne39 on 2012-01-01
Hi, in the guide if you look at the right side it has headings that are numbered and you can click on them to take you to that place in the document.

Click on number 20 and it will take you to the window decorator commands, it is not a complete list but the most popular, I did not post one here for you because I do not know which one you need.

Also it is likely that the window decorator plugin in compiz just came unchecked so type window decorator into the filter box in compiz and make sure it has a check by it.
Thanks

---

### Post by Sietse on 2012-01-01
There are other problems as well, when i start compiz i get this in the console:
compiz (core) - Fatal: No composite extension
compiz (composite) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'composite'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Error: InitPlugin 'opengl' failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Fatal: No composite extension
compiz (core) - Fatal: No composite extension

My graphics card is ATI RADEON HD 5700, for creating the xorg.conf file i used aticonfig --initial=dual-head. I assume this is not enough for making compiz run. Which modules should i load, in other words howto change xorg.conf

---

