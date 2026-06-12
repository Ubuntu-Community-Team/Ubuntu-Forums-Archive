---
title: "To Compiz or not to Compiz, that is the question."
date: 2011-12-11
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-12-11
Hello,

i'm working on a Python project (which is also a learning process b.t.w.).

To put it simply, I am making an interface on my desktop with, among other things, a button triggering an exposition of currently open windows.

I've got two options for that:

1. use Compiz
2. make my own exposition

Option 1 seems the more sensible at first, because I don't have to re-invent the wheel. But then I have two obstacles:

a. The overlay with the scaled windows ("Scale" is what it's called in Compiz), is above my interface window (which has reserved space on the screen thanks to X-lib). How can I control the size of the Compiz overlay?
b. I want to be able to highlight windows, who need attention (because the exposition would replace the task-bar altogether). Can tweak Compiz at all to do that? It seems quite a venture.

Option 2 is more work, but I'd have more control on the application. I haven't seen whether I could get a thumbnail of the window with Python XLib, but I presume it's possible.

I find this a dilemma, it seems pointless to re-do what Compiz does, but on the other hand, it's so hard to integrate Compiz and make it do what I want.

How would you proceed with this?

---

### Post by CoffeeRain on 2011-12-12
I would say do it yourself. Even though it would be reinventing the wheel as you say, you could do further detailed messing around and correcting afterwards.

---

