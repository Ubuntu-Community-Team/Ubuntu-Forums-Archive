---
title: "number help in php"
date: 2009-01-15
forum: Programming Talk
---

### Post by brandon88tube on 2009-01-15
First let me say this, I am extremely tired and have been trying to figure this out for a couple hours, so please bear with me.

I can't seem to figure out what I think should be fairly simple, maybe its the lack of sleep... I have a max number, I want to echo only a certain amount of these numbers based upon a limit. When it gets to the last number, I would like it to start with that number and continue to echo numbers based upon the limit until it reaches the max number.

An example: I have a max number of 35, I set the limit to 10, I want to echo the first 10 numbers > 1 2 3 4 5 6 7 8 9 10, then I want to start at 10 and go up to 19, then start with 19 and go up to 28 and so forth all the way until I can echo 28 29 30 31 32 33 34 35. I think I need a type of loop for this, but I haven't been able to devise one to do everything that I want. If anyone can help and come up with an resource efficient way of doing this please share.

---

### Post by DFord425 on 2009-01-15
Make an outer loop where the limit is your max-number. Then an inner loop where the limit is your limit and max-number. kinda like this:
```

while(count<max_number){
  while(inner_count<limit && count<max_number){
    //print number and increment count and inner_count
  }
}

```

---

### Post by brandon88tube on 2009-01-15
What would inner_count be and would a for loop be better?

---

