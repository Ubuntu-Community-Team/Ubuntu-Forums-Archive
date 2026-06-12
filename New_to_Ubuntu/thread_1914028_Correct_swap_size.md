---
title: "Correct swap size"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by brunces on 2012-01-23
Guys,

I've read around the internet that there's no need to use a large swap size, but I have also read that if you use hibernation, you should set the swap memory the same size of your RAM memory amount.

My laptop computer has 4 GB of RAM and I plan to add 4 GB more, making it 8 GB. I use hibernation a lot.

My question is... what is the correct swap size I have to set up? I thought of setting up 8 GB. Am I wrong?

Thanks for your attention.

brunces

---

### Post by sandyd on 2012-01-23
> **brunces said:**
> Guys,

I've read around the internet that there's no need to use a large swap size, but I have also read that if you use hibernation, you should set the swap memory the same size of your RAM memory amount.

My laptop computer has 4 GB of RAM and I plan to add 4 GB more, making it 8 GB. I use hibernation a lot.

My question is... what is the correct swap size I have to set up? I thought of setting up 8 GB. Am I wrong?

Thanks for your attention.

brunces
The thing is, 

[LIST=1]
[*]When you suspend to swap, its compressed (Thanks @Cheesemill), but thats negligible.
[*]The reason why you *should* make swap larger than your RAM is if your using swap already. This is because the swap size is 4GB RAM for hibernation + SWAP already used. You have 4GB Ram, which is pretty much enough. I would probably only make it 5-6GB Swap in total.
[/LIST]

---

### Post by kerry_s on 2012-01-23
if your going to add more ram, you might as well go 8.5gb to cover your hibernation. with that much ram swap won't be used at all.

---

### Post by Double.J on 2012-01-23
You've had some good suggestions - if HDD space isn't a problem then I'd say twice would be plenty - unless you're likely to be maxing your ram gaming and want to hibernate the system?

Personally I don't do anything heavy on the ram, and from using linux on a number of machines I know that my usual computing habbits are between 500M and 1G on the netbook, and 1G and 2G on the desktop. Personally I use the size of my RAM, plus my normal upper limit, plus 10%... so my netbook has 3.1G swap,2G Ram and my desktop 10.2G swap, 8G ram - but then HDD space isn't an issue for me and I like to use hibernate probably more than I should ;)

Just my tuppence!

---

### Post by nipunshakya on 2012-01-23
> **brunces said:**
> Guys,

you should set the swap memory the same size of your RAM memory amount.

My laptop computer has 4 GB of RAM and I plan to add 4 GB more, making it 8 GB. 

you have it right there brunces..go for your allocations for swap. I would suggest you do that.:D

---

### Post by bluexrider on 2012-01-23
Here are the recommendations per UBUNTU 

Suggested reading [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

