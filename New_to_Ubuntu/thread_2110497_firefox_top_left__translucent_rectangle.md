---
title: "firefox top left  translucent rectangle"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by gridd on 2013-01-30
When first opening Firefox a small translucent rectangle  approx  3cm x2cm appears in the top left corner
it then immediately disappears 
could this be a tracker?

I have googled to no effect 
disabling  addons then restarting  doesn't work, and i cant find out how to disable hardware accelerator.
I have completely  reinstalled the os I have three on separate partitions
I'm using Ubuntu 11.10 Atm but this happens on all my linux os' I haven't checked windows yet though
any advise would be welcome.

I first noticed this after loading then deleating 12.10 which seemed to play havoc with grubb I could not see one of my os' and lost a large storage partition also

---

### Post by audiomick on 2013-01-30
I've seen this on my netbook, and maybe on the laptop, but not on my desktop. I don't know what causes it, but I have also seen posts about it on another forum. I don't think it is anything malicious or anything you need to worry about.

---

### Post by gridd on 2013-01-30
> **audiomick said:**
> I've seen this on my netbook, and maybe on the laptop, but not on my desktop. I don't know what causes it, but I have also seen posts about it on another forum. I don't think it is anything malicious or anything you need to worry about.

hi 
   It would be nice to know what is causing it though. Do you remember which forum it was by any chance.As this is affecting every install something must be wrong.

---

### Post by audiomick on 2013-01-30
> **gridd said:**
> hi 
   It would be nice to know what is causing it though. Do you remember which forum it was by any chance

I don't remember where it was on the forum in question. I do know for sure that the discussion stopped months ago, and the conclusion was "it happens sometimes". Not really worth the effort of finding it... ;)

I think there is a possible connection with lower spec machines, but I am not sure.

It would indeed be nice to know what is or was causing the effect. To be quite honest, though, I haven't even noticed it for some months. I don't know whether it has stopped happening, or I have just stopped noticing.

---

### Post by gridd on 2013-01-30
> **audiomick said:**
> I don't remember where it was on the forum in question. I do know for sure that the discussion stopped months ago, and the conclusion was "it happens sometimes". Not really worth the effort of finding it... ;)

I think there is a possible connection with lower spec machines, but I am not sure.

It would indeed be nice to know what is or was causing the effect. To be quite honest, though, I haven't even noticed it for some months. I don't know whether it has stopped happening, or I have just stopped noticing.
Thanks very much for your input anyway, at least Im not alone with it.
         PS.How do you stop noticing the oiliphant in the shopping basket? 

I dont think I should put solved on this though.Just in case some genius solves it with the stoke of a key or something.

---

### Post by audiomick on 2013-01-30
Just started the other two machines to have a look. The effect in question is no longer visible. Don't know what fixed it; I certainly didn't do anything other than let the updater do the regular updates. Must have got fixed somewhere along the way... :-k

---

### Post by gridd on 2013-02-04
I still have this problem on three os. on my acer one 200 laptop 

Does enyone else have it? or any clue as to what it is.

---

### Post by Impavidus on 2013-02-05
I think I know what you're talking about, as I see it happening on my laptop too. It looks like a small delay in the graphics pipeline, where not the entire firefox window is mapped over the background at once. Apparently the block in the upper left is mapped over the background only a few frames later. Graphics pipelines are designed to not always be fully synchonised to prevent delays.

---

### Post by -Robert- on 2013-02-06
> **gridd said:**
> 
Does enyone else have it? or any clue as to what it is.

Count me in. I've got the same issue on several PCs/laptops. I don't have a clue what's causing it...

---

