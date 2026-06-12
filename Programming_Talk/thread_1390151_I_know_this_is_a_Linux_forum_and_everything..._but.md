---
title: "I know this is a Linux forum and everything... but the Win32 API?"
date: 2010-01-25
forum: Programming Talk
---

### Post by Muffinabus on 2010-01-25
I've been learning C++ for a while and I'm taking more advanced courses at my community college now.  We were assigned to do a project, nothing too fancy, but I thought I would go ahead a bit and try to do more.

My aim is to create a graphical Tic Tac Toe game.  The logic behind the game itself is really simple, just I've never programmed with graphics in C++ before.  I began learning the win32 API for my graphics needs - The class primarily works in Windows using Visual Studio C++ 2008.

Right now what I've got is a Window and some code so that an action can be performed when the user clicks under certain coordinates inside the window.  I'm stuck right now as I have literally no idea how to create and display images on the window.  Looking at some functions in MSDN I see some for writing bitmaps, but I don't know how to implement them or if they're even what I require.  Right now I'm looking at the DrawState function, would this be close to something that I need?

I think my needs are pretty simple, an image of an X to be displayed if user1 clicks somewhere, and an O to be displayed if user2 does so, with the appropriate flags marked in the code to register and do win checking.  I don't think I need to use a graphics API for this, do I?  Would it be wise to go and use opengl for something this simple?

The hardest part about this is that I don't know what's available to me or how to use it entirely properly.  Any help would be appreciated to point me in the right direction, even if it's just telling me to go to a different forum that is more dedicated to Windows programming or programming in general, this is the only one that I frequently visit.  I just thought that maybe I'd catch someone who's knowledgeable about win32.

Thanks!

---

### Post by Hellkeepa on 2010-01-25
HELLo!

Go for Qt instead, works on both Windows and Linux. As a bonus you'll get Mac OS support as well.

Happy codin'!

---

### Post by Garratt on 2010-01-25
or you could try, [www.cplusplus.com](www.cplusplus.com) [http://tinyurl.com/y9wmrt9]("http://tinyurl.com/y9wmrt9")

---

### Post by hessiess on 2010-01-25
Use SDL, the windows API is a complete mess and is much more manageable with two or three extra layers of abstraction;).

And to be honest, X11 is the same, if not worse.

---

