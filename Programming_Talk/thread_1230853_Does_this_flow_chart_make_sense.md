---
title: "Does this flow chart make sense?"
date: 2009-08-03
forum: Programming Talk
---

### Post by swoll1980 on 2009-08-03
never mind it won't let me upload the .vsd

---

### Post by slavik on 2009-08-03
I gotta ask, what language was that in?

---

### Post by Arquis on 2009-08-03
Isn't .vsd a visio file? How can you read it on Linux? Ooo?

---

### Post by wojox on 2009-08-03
Must have wine? Microsoft Office right.

---

### Post by swoll1980 on 2009-08-03
> **slavik said:**
> I gotta ask, what language was that in?

pseudo-code. I can't figure out how to use tab on the forums, so there were no indentations.

---

### Post by swoll1980 on 2009-08-03
> **Arquis said:**
> Isn't .vsd a visio file? How can you read it on Linux? Ooo?

> **wojox said:**
> Must have wine? Microsoft Office right.

I just use Windows for Visio, and some other apps. I hate wine with a passion.

Add: After some research; I guess there may be a tool that opens .vsd files in Linux called vsdviewer.

---

### Post by Slim Odds on 2009-08-03
> **swoll1980 said:**
> I hate wine with a passion.

Why? What's wrong with it?

---

### Post by swoll1980 on 2009-08-03
> **Slim Odds said:**
> Why? What's wrong with it?

I don't want to get a whole debate about it going. Lets just say it's a matter of opinion, and "I don't like it" is mine, and leave it at that.

---

### Post by Slim Odds on 2009-08-03
> **swoll1980 said:**
> I don't want to get a whole debate about it going. Lets just say it's a matter of opinion, and "I don't like it" is mine, and leave it at that.

Just askin'

No need to get all defensive......

over and out!

---

### Post by Can+~ on 2009-08-03
How about a screenshot?

---

### Post by swoll1980 on 2009-08-04
> **Can+~ said:**
> How about a screenshot?

How about print to pdf? I should have thought about that earlier. :oops:

---

### Post by swoll1980 on 2009-08-04
> **Slim Odds said:**
> Just askin'

No need to get all defensive......

over and out!

No offense to you. I'm sorry that came off wrong. I just don't want to start some kind of flame war that's all.

---

### Post by Sockerdrickan on 2009-08-04
Does this pie chart make sense?

[img]http://tommcmahon.typepad.com/photos/uncategorized/2007/03/26/pacmanppt.gif[/img]

---

### Post by issih on 2009-08-04
I think it should function...but its not terribly efficient.

You could have one function to calculate the price of all items, and just pass in the name and price, the burg, fries etc methods are all very similar, make them use the same code.

You should use a switch not a load of if/else ifs in the main loop.

The rest is just about style, personally I'd make it so that you add your prices to a total initialised at zero, rather than having separate prices for fries and so on, some of which may be zero, if you are wanting an audit trail (or receipt system) your approach may be useful, but I'd still do it differently.

Hope that helps

N.B. personally I'd do it with objects, but that just cos I like them :)

---

### Post by swoll1980 on 2009-08-04
> **issih said:**
> I think it should function...but its not terribly efficient.

You could have one function to calculate the price of all items, and just pass in the name and price, the burg, fries etc methods are all very similar, make them use the same code.

You should use a switch not a load of if/else ifs in the main loop.



Yeah those are good ideas. I'm still extremely new at this stuff, so often I find inefficient ways to do things. I'm glad you guys are here to help out though. It makes learning this stuff way easier.

---

### Post by Can+~ on 2009-08-04
Could be coded as a closure for example (I'm guessing you're doing python because of the previous posts)

[PHP]new_item = lambda price: lambda quantity: quantity*price

fries = new_item(0.79)
print fries(3)[/PHP]

An object is fine too.

---

### Post by swoll1980 on 2009-08-04
> **Can+~ said:**
> Could be coded as a closure for example (I'm guessing you're doing python because of the previous posts)

[PHP]new_item = lambda price: lambda quantity: quantity*price

fries = new_item(0.79)
print fries(3)[/PHP]

An object is fine too.

I will look into that further to see exactly how that would work. Thanks for the tip.

---

