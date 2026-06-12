---
title: "X window system. 2 heads send fire fox from this screen to that screen"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-05-04
hello 
i have 2 monitors running. nvidia. opengl works on both and there setup as 2 seprate x windows 
how can i send a window i have open on one screen to the other

---

### Post by lazyart on 2008-05-04
Drag it?

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-05-04
no didn't work but 
the reason i wanna have 2 heads for x insted of using twin view it it gives you the ability to rotate each cube independntly 
so if any one knows howto enable draging in between 2 x windows or how to make it so that twin view will alow you to just rotate one cube (screen) at a time.
or maybe i coudld right a script or some thing to do this for me
yes i think i could if i knew more about compiz

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-05-05
like i just wanna start a movie on my left screen then  move it to the right rotate the cube on the left screen. and still have the moive on the right screen. and then i could rotate the right screen if i wantied to

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-05-13
bum

---

### Post by wootah on 2008-05-13
Ahh yes I have had this question as well.

I bet there is some black magic command line stuff we could do :P I believe it has something with assigning (moving?) a window to another X session ?

---

### Post by wootah on 2008-05-21
bump?

---

### Post by wootah on 2008-05-26
After much searching:

For ATI: BigDesktop (Proprietary Driver), MergedFB (OpenSource Driver)
For nVidia: TwinView
For Intel: ???
X Specific: Xinerama

When you configure xorg.conf with two sections for device, monitor (screen   0 and 1) and two screens, that sets up dual head with two seperate X sessions. I'm going to add this information to the community docs--it's a little silly how difficult it was to find a clear answer.

Good luck joe!

EDIT: Here is the forum for discussion: [HowTo: Dual Monitors (Xinerama/TwinView/MergedFB/Big-Desktop) http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

---

