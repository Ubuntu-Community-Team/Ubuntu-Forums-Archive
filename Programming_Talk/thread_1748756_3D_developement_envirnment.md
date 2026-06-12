---
title: "3D developement envirnment"
date: 2011-05-03
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-03
Hey guys,
I'm looking for a 3D envirnment for a game, and I want users to be able to incorperate their own 3D items, like second life. I want them to be able to build and all. What would the best way of going about this be?

---

### Post by jespdj on 2011-05-04
What programming language?

If you're programming in Java, then [jMonkeyEngine](http://jmonkeyengine.com/) is quite nice. Without too much work you can create really nice 3D graphics in Java with it.

---

### Post by jimi_hendrix on 2011-05-04
The best way to have users create their own 3D objects would be to have them model them in another program (like Blender), and then import them into your game.

---

### Post by ubudog on 2011-05-05
> **jespdj said:**
> What programming language?

If you're programming in Java, then [jMonkeyEngine](http://jmonkeyengine.com/) is quite nice. Without too much work you can create really nice 3D graphics in Java with it.

Sweet, I've been looking for something like that, thanks!

---

### Post by ki4jgt on 2011-05-05
> **jimi_hendrix said:**
> The best way to have users create their own 3D objects would be to have them model them in another program (like Blender), and then import them into your game.

I have a save format I want to save them in to save room on the server. The game is going to be free, with free unlimited land. When people don't sign in for a couple of years, I don't want them to lose the land. (it will happen, but with this format it will be next to impossible) The game has it's own format though, That's why I can't import from blender. I'm planning to make it open sourced so hopefully it'll grow. Using this format the server isn't a problem, and it kind of helps with bandwidth too.

---

### Post by ki4jgt on 2011-05-05
> **jespdj said:**
> What programming language?

If you're programming in Java, then [jMonkeyEngine](http://jmonkeyengine.com/) is quite nice. Without too much work you can create really nice 3D graphics in Java with it.

The game server will be in Python. That's all I can program in, I don't know about the game yet, but I need to know how to interpret that server before I start programming the game itself.

---

