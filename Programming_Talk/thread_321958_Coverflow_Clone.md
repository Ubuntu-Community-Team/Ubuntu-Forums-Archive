---
title: "Coverflow Clone"
date: 2006-12-19
forum: Programming Talk
---

### Post by bieber on 2006-12-19
I'm sure by now most of you have seen or heard of the Coverflow feature in the latest iTunes (if you haven't, just Google it, it'll come right up).  I've gotten kind of annoyed that this is Windows/Mac/proprietary only, so I've decided to go ahead and make a free clone.  Now, it *seems* like this should be something really simple...it is, after all, just a bunch of planes in 3D space with textures applied to them.  The only real problem is that I've never done any sort of 3D programming, or really anything graphical at all; I've been a command line and web dev guy thus far.  So, I reckon I'm gonna go ahead and start working on learning it, do y'all have any suggestions or hints?  I've got this link from another thread: [http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/) and it seems like a really good resource.  Would it maybe be possible to do this without any 3D stuff at all, just skewing the rectangles apropriately to give a 3D look?  Any thoughts and comments are welcome...

---

### Post by Wybiral on 2006-12-19
Sure, the rectangle idea would work... You should look up some tutorials on texture mapping in raycasters... That's how those old games like wolf3d did their texture mapping (they weren't actually 3D, but more along the lines of what you mentioned)...

However... I think the 3d way would be just as easy (if not easier) and could also support much cooler effects like fog and lighting, and the animating would be much simpler in 3d.

I can help some, maybe offer you some example code in OpenGL that might be of use. If you'd like, that is.

---

### Post by bieber on 2006-12-19
If you feel like helping out, I can use any assistance you could provide.  I'm thinking I'll likely set up  a Google projects account for it with SVN, if you want to actually help code.  If you're interested, my email's [email]bieber@bieberworks.net[/email]

---

