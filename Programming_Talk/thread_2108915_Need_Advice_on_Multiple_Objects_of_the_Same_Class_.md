---
title: "Need Advice on Multiple Objects of the Same Class in Ruby"
date: 2013-01-26
forum: Programming Talk
---

### Post by tdawgf on 2013-01-26
Hello everyone,

Thanks in advance for any advice. I am currently trying to create a breakout clone with rubygame. One thing has me stumped and I am unsure of how to approach it. I need to create multiple bricks for a player to break. I have already create a class for an individual brick, but I was wondering if there was a way to generate a certain number of brick objects so that I wouldn't have to hardcode each individual brick in, and I could use it to give players a random number of bricks to break per level. Any advice is greatly appriciated

---

### Post by satsujinka on 2013-01-26
Depending on how complex your brick class is, couldn't you just make a random length array of bricks? (I assume they contain their coordinates or something, so you can then iterate over the array and make each brick have a random coordinate that isn't already in use.)

---

### Post by tdawgf on 2013-01-26
/facepalm I feel stupid now. Don't know why I didn't think of that, but thank you so much. I am gonna try that out here later.

---

### Post by tdawgf on 2013-01-26
Well, I tried it, but unfortunately for me it is not working. I have an array of unique block class objects. I just have no clue how to call their respective draw methods.

---

### Post by satsujinka on 2013-01-27
> **tdawgf said:**
> Well, I tried it, but unfortunately for me it is not working. I have an array of unique block class objects. I just have no clue how to call their respective draw methods.

Assuming your block class has an init method that sets its location to a random coordinate that isn't already taken and a draw method that draws the block:

```
array.each do |x| 
    x.init(takenCoordinates)
    x.draw
end
```

---

