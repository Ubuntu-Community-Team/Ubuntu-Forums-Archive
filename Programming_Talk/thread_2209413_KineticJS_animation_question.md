---
title: "KineticJS animation question"
date: 2014-03-05
forum: Programming Talk
---

### Post by mathias-de-gucht on 2014-03-05
Hi everyone,

I was trying to make a spinning wheel for some kind of game.
So I have a circle which is drawed with a variable amount of wedges (chosen by user)
so I have a for-loop which adds every wedge to the layer and if its complete the layer gets added to the stage.

So far so good...

But when I try to let the circle spin (around its center)
I can't get it to work. I can only find tutorials and tips online with things like eg.: rectangle.rotate();
Never stage.rotate();

So I tried layer.rotate() but that resulted in the circle spinning around the top-left corner of the container.
And not much improvement when i add an offset to the layer.

So my question is: Is there a way to let all wedges rotate as a whole circle?

---

