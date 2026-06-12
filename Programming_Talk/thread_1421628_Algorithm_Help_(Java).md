---
title: "Algorithm Help (Java)"
date: 2010-03-04
forum: Programming Talk
---

### Post by taekwondodogoof on 2010-03-04
Hi. I was wondering if anyone knew of an algorithm that could help me solving this problem. Supposing that you have a list of items with various weights and values (aka an item with a weight of 12 and a value of 15, then an item with a weight of 30 and a value of 60, ...), how would you find the combination of items that would give you the greatest value, while being under a certain weight limit, like 100.

Thanks so much,
Jared

---

### Post by nmccrina on 2010-03-04
Edit: not really helpful :D

---

### Post by howlingmadhowie on 2010-03-04
> **taekwondodogoof said:**
> Hi. I was wondering if anyone knew of an algorithm that could help me solving this problem. Supposing that you have a list of items with various weights and values (aka an item with a weight of 12 and a value of 15, then an item with a weight of 30 and a value of 60, ...), how would you find the combination of items that would give you the greatest value, while being under a certain weight limit, like 100.

Thanks so much,
Jared

that sounds rather like the napsack problem which is as far as i know np-hard.  i think you really just have to do the leg work.

---

### Post by doas777 on 2010-03-04
subtract the diff between value and weight for each element, and store in a sorted list. then pull off the big end of the list until you can't add any more (because the next element would break the weight rule). I think that would do what you want, and save the need to calculate each set seperately and then compare them. 

another option is to just divide value by weight for each element. that value shoudl represent the value per weight unit. your set would logically consist of as many of the high value elements as you can get in under your weight limit.

either way reduces the nested looping.

---

### Post by howlingmadhowie on 2010-03-04
> **doas777 said:**
> subtract the diff between value and weight for each element, and store in a sorted list. then pull off the big end of the list until you can't add any more (because the next element would break the weight rule). I think that would do what you want, and save the need to calculate each set seperately and then compare them. 

another option is to just divide value by weight for each element. that value shoudl represent the value per weight unit. your set would logically consist of as many of the high value elements as you can get in under your weight limit.

either way reduces the nested looping.

it's not a bad method, but it isn't garenteed to work. consider the following items:
item A weighs 90 and has a value of 95
item B weighs 50 and has a value of 50

maximum weight is 100.
2 * B would give a total value of 100, even though their value density is lower than the value density of A.

---

### Post by CptPicard on 2010-03-04
Yeah, it's knapsack... and I suspect this is therefore homework. :) The OP can easily find approximations discussed on the net.

---

