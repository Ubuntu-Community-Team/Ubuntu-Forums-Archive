---
title: "Ye Olde Advanced CSS Question (rollover mania!)"
date: 2007-03-01
forum: Programming Talk
---

### Post by DirtDawg on 2007-03-01
I'm attempting to make a "toy" website that is written *entirely* in css+html. Nothing else. No Flash, no Javascript.

I would like to include small areas, or buttons, which the user can click to effect other areas on the page. For example, lets suppose there's a button underneath a picture of a smiley face :) . Now suppose when the user presses the button,  the picture changes to a sad face :( . Another click would revert the image back to its original position :) .

I have managed to (mostly) work out a remote rollover system that will allow the button to change the image on either hover or active states. What would really be great is if I could keep the changes permanent after the fact, like an on/off switch. Of course, without Javascript, variables are not possible so this idea might be dead in the water. 

But I have this idea to use the :visited psuedo-class as a primative variable. I think it could work, but the switch would only function one time until the user dumped their cache. Unless there is some way to erase or reverse that specific attribute? 

Is this even possible? Any and all ideas would be greatly appreciated.

Thanks for your opinions.

[color="blue"]UPDATE:[/color] I finished this project months ago and forgot to post it here! Check out my [Spaceship Of Sweetness]("http://www.weeklyhilarity.com/spaceship_of_sweetness/") if you're interested. By the way, as a result of this problem never getting solved, the only way to turn off the coffee pot is to erase that page from your browser history! Not even the future is perfect.

---

### Post by Wybiral on 2007-03-01
Why not use Javascript? Or is this a challenge to not use JS?

---

### Post by DirtDawg on 2007-03-02
> **Wybiral said:**
> Why not use Javascript? Or is this a challenge to not use JS?

Yeah that's the whole point is to push css to the breaking point, which I may have found.

---

### Post by Wybiral on 2007-03-02
> **DirtDawg said:**
> Yeah that's the whole point is to push css to the breaking point, which I may have found.

I admit that I'm not the guy to ask about css, but what I know of it I can't think of any way to make any functional events without the use of Javascript. But... I could be totally wrong.

---

### Post by DirtDawg on 2007-03-02
> **Wybiral said:**
> I admit that I'm not the guy to ask about css, but what I know of it I can't think of any way to make any functional events without the use of Javascript. But... I could be totally wrong.

Well it's been slim pickings on the Net thus far and I know I'm stumped. I may have to change plans to accomodate the limited functionality of the visited, hover, and active pseudo classes. I thought I would try picking brains as a last resort.

That said, I'm still open to suggestions if any one wants to serve one up.

---

