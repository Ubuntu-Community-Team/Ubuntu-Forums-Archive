---
title: "Trigonometry"
date: 2012-02-09
forum: Programming Talk
---

### Post by leg on 2012-02-09
I am trying to write a simple game and have fallen fairly early with some trigonometry. I am trying to calculate the position of a ball given direction, speed and elapsed time. I think I have this bit fairly close but bouncing it of the edges is giving me a fairly large headache.

Can any of you link me to some resources I can use to solve this problem.

Thanks

---

### Post by muteXe on 2012-02-09
Determine the angle the ball bounces off the wall. The angle of this minus 90 degrees is the angle of incidence from the normal of the wall, meaning (if you assume a 'perfect' reflection, no energy lost) it'll be the same angle for reflection.

---

### Post by Tony Flury on 2012-02-09
When something bounces off a flat wall (assuming it is a perfect bounce) then the angle of return is the same as the angle of collision (strictly speaking the angles are measured from a line perpendicular to the surface).

Put simply - if you know the x and y velocities - then a bounce of a horizontal wall keeps the x direction the same and the y direction is reversed - off a vertical wall the y direction stays the same but the x direction is reversed.  (Assuming x is horizontal movement and y is vertical movement).

If the walls are not perfectly horizontal or vertical - then you will need to calculate an imaginary line which is at 90 degrees to the point of impact, and calculate angles to and from that line.

If the collision is not perfect then that is a (pardon the pun) a whole different ball game - you will have to think about how much energy is lost in the collision - and calculate a new velocity based on the angle of collision and the colision velocity - not for the faint hearted if you are new to trigonometry.

---

### Post by muteXe on 2012-02-09
I'd just get an elastic model working first, before you even begin to worry about inelastic collisions.

---

### Post by Tony Flury on 2012-02-09
> **muteXe said:**
> I'd just get an elastic model working first, before you even begin to worry about inelastic collisions.

Agree - elastic collisions (perfect collisions) against horizontal/vertical surfaces are the best starting points

---

### Post by leg on 2012-02-09
Well thats what I have been doing, or at least thought I was. I am detecting the edges of the screen and negating the appropriate axis variable. It isn't behaving as it should and I don't understand why. Sometimes the gets stuck on the edge and sort of wobbles up and down. Top and bottom detection seems to be ok but left and right is a prob. Oh well thanks for the inpit I shall give it another go tomorrow.

---

### Post by Tony Flury on 2012-02-10
first thing that threw me when i was did a bouncing ball program, was the need to not only detect the edges, but if you ae actually moving towards them.

The position of the ball is not enough, as the ball will not move away from the wall immediately when it "bounces", so make sure you collision test is taking into acount position and direction - it maybe that the wobble is due to not doing this.

---

### Post by leg on 2012-02-11
> **Tony Flury said:**
> first thing that threw me when i was did a bouncing ball program, was the need to not only detect the edges, but if you ae actually moving towards them.

The position of the ball is not enough, as the ball will not move away from the wall immediately when it "bounces", so make sure you collision test is taking into acount position and direction - it maybe that the wobble is due to not doing this.
Yes is it definitely something like that but whats throwing me is that top and bottom bounces are ok. I think the bounce may not be coming far enough away from the wall  and sending it back again.

---

