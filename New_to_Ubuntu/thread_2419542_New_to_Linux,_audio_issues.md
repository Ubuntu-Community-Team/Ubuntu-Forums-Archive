---
title: "New to Linux, audio issues"
date: 2019-05-23
forum: New to Ubuntu
---

### Post by commander-pie on 2019-05-23
Hello,

So I just built my first PC with the goal to use and learn linux along the way. However, I am having real trouble trying to adjust to it. My question right now is how do I make the headphone jack work?

I'm using a b450 tomahawk motherboard and a nzxt h500i case. 

Thanks in advance

---

### Post by Autodave on 2019-05-23
What version of 'buntu did you install?

---

### Post by richard378 on 2019-05-24
Open settings and adjust sound options under input and see if your jack input is there.  Works on Ubuntu 18 and 19.  Which version of Ubuntu are you running?  Does this work.  What problems are you having?  Does it show your sound under Sound in settings or is it totally missing drivers?

---

### Post by MartyBuntu on 2019-05-26
Open a terminal and type in:

**alsamixer**

...then hit the ENTER key.

You'll be presented with some configuration options for any sound card Ubuntu finds. There's headphone output options there.

---

### Post by MartyBuntu on 2019-05-26
Just to make sure, the front panel audio connector was attached to the motherboard when this system was put together, right?

---

