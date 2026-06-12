---
title: "problems with OpenGL (glut) and Compiz"
date: 2007-09-22
forum: Programming Talk
---

### Post by ac251404 on 2007-09-22
I just did a fresh install of Xubuntu + Compiz on my laptop and went to do my first project for my computer graphics class and ran into some issues. 

First I just tested compiling with the glxgears.c and glxdemo.c code from [here]("http://www.koders.com/noncode/fid4CE4499E8BFC8B92B30FB36C9CB524012983A051.aspx"). Everything compiles fine, but glxdemo.c does not show they yellow square at all unless i move the window. When moving it the square shows up but as soon as i release the window it goes all black. glxgears.c appears to run fine at first, but if you drag the window it leaves artifacts all over the desktop. Lastly, my own piece of basic code shows up at first but without any borders/title bar and the window disappears as soon as you click outside of it. In my code I have no resize/redraw events, but it was still working fine on my old setup with GNOME/metacity.

So does anyone have any ideas why this conflict between Compiz and OpenGL seems to be occuring?

Thanks
-Alex

---

### Post by weblordpepe on 2007-09-23
No clue, but it sounds like my symptoms. When I turn on compiz, I can't watch any videos which use OpenGL to accellerate the video. 

That is of course unless I drag the window. Coincidence? I think NOT!

---

### Post by slavik on 2007-09-23
what driver do you two have installed?

---

### Post by weblordpepe on 2007-09-24
The default radeon driver which comes with Ubuntu. When I want to fiddle with Compiz, thats what I use.

Normally I use the restricted driver because its way faster.

---

### Post by hod139 on 2007-09-24
Isn't this a known problem with compiz?  In any case a quick search found me this: [http://ubuntuforums.org/showthread.php?t=558473](http://ubuntuforums.org/showthread.php?t=558473)
and I'm sure there are plenty more threads of a similar theme.

---

### Post by tempuser_01981348723 on 2008-11-30
I've solved this problem in a very naive way.
What you have to do is go to System>Preferences>Appearance and disable any visual effect. You can change this back to yeah-cool-effects mode anytime later.
Ciao

---

