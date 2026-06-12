---
title: "Programming Challenge 5 Hijack"
date: 2008-03-23
forum: Programming Talk
---

### Post by Fbot1 on 2008-03-23
> **Wybiral said:**
> this is a pretty easy challenge

That's the problem though, Sierpinski's Triangle can't actually be seen.

---

### Post by Wybiral on 2008-03-23
> **Fbot1 said:**
> That's the problem though, Sierpinski's Triangle can't actually be seen.

You mean because it's infinite? Well, yeah... But if you want to look at it like that, nothing can be seen. Have you ever seen the graph of X^2? No, you haven't... Because it's infinite. That mindset would make algebra class quite difficult. Why don't you just try to render an approximate / cut-off view of the triangle?

---

### Post by Fbot1 on 2008-03-23
> **Wybiral said:**
> You mean because it's infinite?

Not exactly, it doesn't take up space (or area rather).

---

### Post by Wybiral on 2008-03-23
> **Fbot1 said:**
> Not exactly, it doesn't take up space (or area rather).

Yes, because it's infinitely precise, like the curve of a sphere (only, inward).

---

### Post by Fbot1 on 2008-03-23
> **Wybiral said:**
> Yes, because it's infinitely precise, like the curve of a sphere (only, inward).

That doesn't fully explain it though. At the very least you need to explain that the structure losses 1/4 each step.

---

### Post by Wybiral on 2008-03-23
> **Fbot1 said:**
> That doesn't fully explain it though. At the very least you need to explain that the structure losses 1/4 each step.

I don't care. My point was that you can render it just as easily as you can render a circle or a sphere. You make it sounds like it's impossible to approximate, which it clearly is not (considering there are tons of images of it online and two submissions to this challenge already). So why don't you just give it a try?

---

### Post by Fbot1 on 2008-03-23
> **Wybiral said:**
> I don't care. My point was that you can render it just as easily as you can render a circle or a sphere. You make it sounds like it's impossible to approximate, which it clearly is not (considering there are tons of images of it online and two submissions to this challenge already). So why don't you just give it a try?

My point is you can't actually see it and the best program would just show nothing which is so easy to do it invalidates the contest.

---

### Post by LaRoza on 2008-03-23
> **Fbot1 said:**
> My point is you can't actually see it and the best program would just show nothing which is so easy to do it invalidates the contest.

It has been said by a great man that computers are modelling tools. They can be used to model things to help humans understand and process data.

The best program would help a human understand the concept as a model, not as "reality".

---

### Post by Wybiral on 2008-03-23
> **Fbot1 said:**
> My point is you can't actually see it and the best program would just show nothing which is so easy to do it invalidates the contest.

Fine, then write one that renders the triangle to a specific depth (maybe four or five iterations). That IS a perfectly doable challenge. Perhaps make it capable of rendering at arbitrary iterations.

---

### Post by Fbot1 on 2008-03-23
> **LaRoza said:**
> The best program would help a human understand the concept as a model, not as "reality".

Not really there a much easier ways to describe it's construction.
> **Wybiral said:**
> Fine, then write one that renders the triangle to a specific depth (maybe four or five iterations). That IS a perfectly doable challenge. Perhaps make it capable of rendering at arbitrary iterations.
That would be okay but that's not the challenge.

---

### Post by Wybiral on 2008-03-23
> **Fbot1 said:**
> Not really there a much easier ways to describe it's construction.

That would be okay but that's not the challenge.

You're being a bit too technical here. If the challenge was to draw a circle, would you give up because it's impossible to draw an infinitely perfect circle? I hope not... I think we all understand that the point is to draw an approximate triangle, not the entire infinite object.

Besides, the challenges are supposed to be fun. I'm sure the challenge poster will forgive you if it's just an approximation :) But it's no fun at all if you don't submit anything :(

---

### Post by LaRoza on 2008-03-23
This has been split from the challenge thread.

Please do not hijack the challenges with pointless debates about the futility of programs.

If you feel this challenge is "impossible", or pointless, look at the others and you will see that none of them are 100% possible. They are programming exercises.

---

### Post by Fbot1 on 2008-03-23
> **Wybiral said:**
> You're being a bit too technical here. If the challenge was to draw a circle, would you give up because it's impossible to draw an infinitely perfect circle?
Well, that's a little different, the output is limited.

> **Wybiral said:**
> Besides, the challenges are supposed to be fun. I'm sure the challenge poster will forgive you if it's just an approximation :) But it's no fun at all if you don't submit anything :(
I guess, I'll see if can make one tomorrow.

> **LaRoza said:**
> Please do not hijack the challenges with pointless debates about the futility of programs.
It seems perfectly appropriate.

> **LaRoza said:**
> you will see that none of them are 100% possible.
I don't see how.

---

### Post by Wybiral on 2008-03-23
> **Fbot1 said:**
> Well, that's a little different, the output is limited.

The output from the triangle is limited too :)
How is it any different?

---

### Post by LaRoza on 2008-03-23
> **Fbot1 said:**
> 
It seems perfectly appropriate.


I don't see how.

It was not in anyway a contribution to the challenge, and it didn't address any real concerns of the challenge.

You don't see how it is impossible to make an application to write checks in a human form for anyone is possible in a week? You think it is reasonable for a single person to implement BigNums completely on there own in a week?

---

### Post by Fbot1 on 2008-03-23
> **LaRoza said:**
> It was not in anyway a contribution to the challenge, and it didn't address any real concerns of the challenge.

It is a real concern though.

> **LaRoza said:**
> You don't see how it is impossible to make an application to write checks in a human form for anyone is possible in a week? You think it is reasonable for a single person to implement BigNums completely on there own in a week?

possible yes, reasonable no

---

### Post by Lux Perpetua on 2008-03-24
For the record, I don't think it is a pointless debate; actually, I think it's worth bringing up. First let me address those who don't know what this discussion is about: you really don't need to worry about it. The problem brought up here will not diminish the value of any program you might otherwise decide to write. 

To those still interested: the problem is just that if you drew Sierpinski's triangle on your screen (say) by starting with a white screen and coloring pixels containing points of the figure black, and if you were then to do the same at a higher resolution, then your shape would actually get fainter, and if the resolution were high enough to make the pixels microscopic, you wouldn't be able to see anything at all without a microscope. A higher-resolution depiction of an object should be more accurate, so it would seem the most accurate description of this shape at any finite resolution is actually a blank image! So there is apparently a disparity between a "technically accurate" picture and an "intuitively correct" picture.

I could have said "make a bitmap image with a pixel black if it contains points of Sierpinski's triangle and white otherwise," and I could have specified an image size and coordinate system to remove any ambiguity. Since today nobody's pixels are microscopic, this would give a good approximation to Sierpinski's triangle that was still visible to the naked eye. However, I intentionally didn't say that (or anything similar) for reasons that should be clear: to give each entrant the freedom to determine his or her own method of depiction. If you're troubled by the blank picture business, then I'll simply remind you that you have the freedom to find a representation that is faithful to the fractal and doesn't suffer from that problem (and don't say none exist, because they do). > **Fbot1 said:**
> That would be okay but that's not the challenge.On the contrary: it is a perfectly valid interpretation of the challenge. There are other interpretations; I left it vague deliberately. It's not my fault if your interpretation leads to a trivial and uninteresting solution. 

> **Fbot1 said:**
> My point is you can't actually see it and the best program would just show nothing which is so easy to do it invalidates the contest.I can see you've already submitted such a program. Your point doesn't invalidate anything, though, for reasons I've already stated.

I will also point out that your objection applies to all plane curves except plane-filling curves, since they also have zero area. That has never stopped anyone from writing programs that graph functions or draw circles and other nice curves. If you personally want to tell all the authors of such software that their programs are inaccurate and a better program would just output blank pictures, then I encourage you to do so. Be sure to come back and tell us how it went. ;-)

---

### Post by Fbot1 on 2008-03-24
> **Lux Perpetua said:**
> I will also point out that your objection applies to all plane curves except plane-filling curves, since they also have zero area.

Ya, but that's more of a well established abstraction. I could say "Oh btw all those triangles are really Sierpinski's triangles too but I want to make it visible" but thats really silly.

---

### Post by LaRoza on 2008-03-24
> **Fbot1 said:**
> Ya, but that's more of a well established abstraction. I could say "Oh btw all those triangles are really Sierpinski's triangles too but I want to make it visible" but thats really silly.
Then you don't think this image helps show the fractal?

[img]http://upload.wikimedia.org/wikipedia/en/thumb/7/74/Animated_construction_of_Sierpinski_Triangle.gif/150px-Animated_construction_of_Sierpinski_Triangle.gif[/img]

[http://upload.wikimedia.org/wikipedia/en/thumb/7/74/Animated_construction_of_Sierpinski_Triangle.gif/600px-Animated_construction_of_Sierpinski_Triangle.gif](http://upload.wikimedia.org/wikipedia/en/thumb/7/74/Animated_construction_of_Sierpinski_Triangle.gif/600px-Animated_construction_of_Sierpinski_Triangle.gif)

---

### Post by Wybiral on 2008-03-24
> **Fbot1 said:**
> Ya, but that's more of a well established abstraction. I could say "Oh btw all those triangles are really Sierpinski's triangles too but I want to make it visible" but thats really silly.

Fbot1, it sounds to me like you're just upset because you can't write a Sierpinski renderer :) (and that's going to be my opinion until you can prove otherwise) If you need help, there are plenty of tutorials online (such as the Wolfram page linked in the original challenge post).

---

### Post by LaRoza on 2008-03-24
> **Wybiral said:**
> Fbot1, it sounds to me like you're just upset because you can't write a Sierpinski renderer :) (and that's going to be my opinion until you can prove otherwise) If you need help, there are plenty of tutorials online (such as the Wolfram page linked in the original challenge post).

Probably.

Can I submit the .gif?

---

### Post by Fbot1 on 2008-03-24
> **LaRoza said:**
> Then you don't think this image helps show the fractal?

[img]http://upload.wikimedia.org/wikipedia/en/thumb/7/74/Animated_construction_of_Sierpinski_Triangle.gif/150px-Animated_construction_of_Sierpinski_Triangle.gif[/img]

[http://upload.wikimedia.org/wikipedia/en/thumb/7/74/Animated_construction_of_Sierpinski_Triangle.gif/600px-Animated_construction_of_Sierpinski_Triangle.gif](http://upload.wikimedia.org/wikipedia/en/thumb/7/74/Animated_construction_of_Sierpinski_Triangle.gif/600px-Animated_construction_of_Sierpinski_Triangle.gif)
I'm saying that image needs some explanation for it to be correct.

> **Wybiral said:**
> Fbot1, it sounds to me like you're just upset because you can't write a Sierpinski renderer :) (and that's going to be my opinion until you can prove otherwise) If you need help, there are plenty of tutorials online (such as the Wolfram page linked in the original challenge post).

Oh, its on now! I guess I'll just ask for the number of steps even though that's incorrect.

---

### Post by Wybiral on 2008-03-24
> **Fbot1 said:**
> I'm saying that image needs some explanation for it to be correct.



Oh, its on now! I guess I'll just ask for the number of steps even though that's incorrect.

OK, then don't think about it as the Sierpinski triangle. Just think about it as "how can I divide this triangle using the Sierpinski sieve to the nth iteration?" There's nothing wrong with that.

---

### Post by Lux Perpetua on 2008-03-25
> **Fbot1 said:**
> Ya, but that's more of a well established abstraction. I could say "Oh btw all those triangles are really Sierpinski's triangles too but I want to make it visible" but thats really silly.The fact, however, is that Sierpinski's triangle is itself a continuous plane curve (it's sometimes called "Sierpinski's curve," actually), so if you accept that the usual way of drawing plane curves is valid, then you should also accept that Sierpinski's curve can also be drawn that way. Forget triangles and iterations. You don't have to deal with them if you don't want to. (I will not explain how to interpret it as a plane curve now in case someone wants to submit it as an entry.)

---

