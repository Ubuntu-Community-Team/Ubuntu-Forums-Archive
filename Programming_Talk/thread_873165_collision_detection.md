---
title: "collision detection"
date: 2008-07-28
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-07-28
hi

so im making a basic pong game in C# without using the many cheating simplified methods i used last time i made it

and im down to collision detection

unfortunetly the only book i have doesnt help me because he tells me to use picture boxs instead of drawing on screen like i want to so the rectangles that im used to using for this are not working

all the articles on google talk about directX which i have no clue how to use (on my windows partition anyway)

other forums have next to no response rate

i know that there arn't that many c# programmers here so anything would be a help

thanks

---

### Post by drubin on 2008-07-28
quick google search for your question...

[http://blogs.msdn.com/coding4fun/archive/2006/11/09/1044454.aspx](http://blogs.msdn.com/coding4fun/archive/2006/11/09/1044454.aspx)
[http://www.codeproject.com/KB/GDI-plus/PolygonCollision.aspx](http://www.codeproject.com/KB/GDI-plus/PolygonCollision.aspx)
[http://www.codeproject.com/KB/GDI-plus/asteroids.aspx](http://www.codeproject.com/KB/GDI-plus/asteroids.aspx)


some of them seem promising.

---

### Post by jimi_hendrix on 2008-07-28
the coding4fun one i tried a long time ago and couldnt get past tutorial 1 because the tutorial was broken (what else would u expect from microsoft) the polygon one was over my head and same with the asteroid one (thus the reason im doing pong)

---

### Post by drubin on 2008-07-28
I did this a WHILE ago but my ones where with cards. (Fixed rectangular shape and size)

**EDIT:** circles can always be enclosed in Squares if it makes things easier :) 

But the principle should be fairly similar.

Create and object/class/interface (Depends on the lang you are coding in)
int x
int y
int width
int height

boolean checkCollision(Shape myShape){
//In here you would check if the bounds of myShape fall in to the bounds of his current implementation.
}

Shape x =new Rectagle(...);//Set height and location
Shape y =new Square(...);//Set height and location

on a change or update of the screen do a 
if(x.checkCollision(y))

Maybe this is obvious but it is very late. This is my last post before bed hope this helps..  :)

---

### Post by jimi_hendrix on 2008-07-28
seems logical

im gong to give it a rest for now and try it later

---

### Post by dribeas on 2008-07-29
> **jimi_hendrix said:**
> so im making a basic pong game in C# without using the many cheating simplified methods i used last time i made it

If pong is the classic one ball + two racquet's game, then general collision algorithms are much harder than what you need. I am assuming rectagles for the racquets and a circle for the ball.

Then the circle ((x,y),r) collides with the rectangle ( (x0,y0),(x1,y1) ) from the left if any of these happens:
[LIST]
[*] Distance from circle's center (x,y) to any one of the corners (x0,y0) or (x0,y1) of the racquet is smaller than circle's radius (r)
[*] Vertical position of the circle's center is in the range [y0,y1] and the horizontal distance between the circle's center (x) and the racquet (x0) is smaller than radius (r)
[/LIST]

That could be extended to upper/lower horizontal sides or even the right side of the racquet (even though it does not seem feasible for the ball to come from the back.

Any complex collision detection algorithm would be overkill as you are working on a simplified scenario.

---

### Post by drubin on 2008-07-29
Agreed @dribeas 
I would be more interested in the angles and impact/forces on the ball :)

else the ball is just going to bounce between the 2 rackets in a straight line.

---

### Post by jimi_hendrix on 2008-07-31
well i resolved the ball in a streight line part wiht a random number determining the incriment to the x and y cords

but the intersect part i still dont know how i solved it...i just retyped something in the if loops that i already had there

i think God knows C#

---

