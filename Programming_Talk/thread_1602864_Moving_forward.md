---
title: "Moving forward"
date: 2010-10-22
forum: Programming Talk
---

### Post by Eragon0605 on 2010-10-22
I have run into a rather hard brick wall in my programming. I want to move forward in my application. I mean, I literally want the view to move forward when I tap a certain key. I have been able to accomplish this pretty easily with the glTranslate function, but there is a problem. I also want to be able to rotate my view, and if I call my glRotate function before I call the glTranslate function, the glTranslate function doesn't work correctly (when I tap a certain key, I translate my objects a certain distance along a certain axis. When I call the glRotate function, that axis is rotated, changing the direction that I am moving). If I call my glTranslate function before my glRotate function, the glRotate function gets messed up (the point the models revolve around is not right below the camera). I have heard of the gluLookAt function, but after about two hours of trial and error, I managed to make no progress. What function or functions is/are best for this? Is there some kind of camera library that would make all my problems go away? I am using C++, SFML, and Ubuntu 10.10. Thank you for your time and effort.

---

### Post by JDShu on 2010-10-22
I myself am a beginner at OpenGL, but are you using glPushMatrix and glPopMatrix?

---

### Post by Eragon0605 on 2010-10-22
What exactly do you mean? I know how to use them, but how would that help anything? If I called glPushMatrix then glTranslate then glPopMatrix, and then called glRotate, for example, my rotate would be fixed but my glTranslate would have no effect at all. The same is true for the opposite. If I called glPushMatrix then glRotate then glPopMatrix, and then called glTranslate, my translate would be fixed but my glRotate would have no effect.

---

### Post by JDShu on 2010-10-23
Sorry that was just my first reaction, because its usually something to do with the sequence of OpenGL calls.

Without any code I couldn't really say for sure what the problem is, but it sounds like your object that you're trying to move (the camera?) is not centered on the origin at all times for some reason.

---

### Post by Eragon0605 on 2010-10-25
I apologize for the long delay. My internet was down. Here is the code I use for camera movement:
[PHP]glMatrixMode(GL_MODELVIEW);
glLoadIdentity();

glRotatef(rotx, 0.f, 1.f, 0.f);

glTranslatef(mvf, 0, 0);
glTranslatef(0, 0, mvs);

//I draw my stuff here...[/PHP]rotx and mvf and mvs are all changed by pressing keys

---

### Post by JDShu on 2010-10-26
hmm wouldn't it be easier to save the matrices instead of calling the identity and then transforming according to some variables?

So you push a key and that calls glRotate or glTranslate depending on what key is pressed. No need to call the identity unless you need to draw something else.

---

### Post by Eragon0605 on 2010-10-26
Oh yeah, didn't think to do that. I'm still fairly new to programming, and I don't always use the thought process needed to solve these problems. Again, thank you for your time and efforts. I really wouldn't have gotten far in programming if not for people like you.

---

