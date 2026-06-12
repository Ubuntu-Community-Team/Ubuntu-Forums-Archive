---
title: "any idea how to create this?"
date: 2010-05-19
forum: Programming Talk
---

### Post by louis--taylor on 2010-05-19
Hello folks!
I am currently working on a program which requires the user to mark some points on the screen. I would like to create a user interface like this one (note: just the big dot thing):
[IMG]http://dl.dropbox.com/u/3746044/dot-one.png[/IMG]
[IMG]http://dl.dropbox.com/u/3746044/dot-two.png[/IMG]

The only things I need are:
The user has to be able to move these dot things around on the screen.
I can create and destroy the dot things from python.
I can read the screen coordinates of the dot things from python.
They can look like anything, it doesn't matter.

I was thinking of using the python Xlib bindings, any ideas?

---

### Post by raydeen on 2010-05-19
Maybe pygame? I would think that would handle the graphics end and provide the coordinate info and the ability to create/destroy/move the objects.

---

### Post by soltanis on 2010-05-20
I believe that pygame can only detect clicks inside its window, though. I would think Xlib is the way to go, unless you want to do some kind of trickery such as drawing a big transparent window over everything. That may make it easier to render your dots, maybe.

---

### Post by louis--taylor on 2010-05-20
Thank you for your replys! The dots need to be persistent (do not go away until the user closes the program) and the user needs to interact with other programs in the background, so I do not think that drawing a big transparent window over everything would be very practical in this situation, although it is a good idea.

Does anyone have any experience in drawing objects to the screen with Xlib?

---

