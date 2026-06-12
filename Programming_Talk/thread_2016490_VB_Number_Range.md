---
title: "VB Number Range"
date: 2012-07-04
forum: Programming Talk
---

### Post by Kodeine on 2012-07-04
Salutations!

So I'm having to create a game for my College course in visual basic. Of course being a Linux user I'd rather not use VB but unfortunately I have to. So I installed visual studio in a windows eight virtual machine. I know there may be better places to ask this but I generally find that people who program in visual basic have the mental age of a five year old child. So I thought to ask here first instead.

The game is a top-down space game. Where your ship stays in the centre of the form and when you press the arrow keys all planets, stars etc move in the appropriative direction. I'm currently trying to add some functions you can perform such as hailing, beaming down etc. To do this you have to be close enough to a planet.

You can get the X and Y positions of anything via the following command. I haven't got the VM running at the moment so the command may not be fully accurate. Changing the appropriative letter will obviously yield the Y value.

```
Xpos = OBJShip.position.X
```

Since the players ship never moves from it's central location if the planet was near the ship, it will always be in the range of lets say 50-150 on the Y and 300-400 on the X. If it is within this range then your ship is deemed close enough to the planet and you can hail or whatever action you desire. But how do I put that into a IF statement? I can think of one way but it's very much overkill.

```
if XOfShip = 300 or 301 or 302 or 303 or 304 or 305 or... or 400 then
 #your close enough on the X scale.
else
 #your not close enough on the X scale.
```

Needless to say that just doesn't suffice. How can I say if the X of the ship is within the range of 300-400?

---

### Post by Vaphell on 2012-07-04
don't tell me visual basic doesn't support < > <= >= operators
x >= 300 and x <= 400

---

### Post by QIII on 2012-07-04
If I am understanding you correctly, a coarse approach might be

```
If x >= somevalue and x <= somevalue and y >= somevalue and y <= somevalue Then ... 
```Select Case would be more elegant.  I suggest you google Select Case.

And I hope your class is at least in VB.NET and not VB6.

---

### Post by Kodeine on 2012-07-04
Dang I forgot you can specify more than one clause by saying <300 and >200. Thanks for the quick replies!

---

