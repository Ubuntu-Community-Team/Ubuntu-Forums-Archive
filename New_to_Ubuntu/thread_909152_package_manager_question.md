---
title: "package manager question"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by biji on 2008-09-03
Hi all,
i have added intrepid to ubuntu source.. but after reload most packages have to be update (must download about 600MB yay.....)
is it possible to *not update* from intrepid but only to ubuntu official but i want to install some packages from intrepid like php5
thanks for help

---

### Post by hyper_ch on 2008-09-03
you don't mix different versions... either stick with the hardy packages or compile php5 from source or use completely intrepid.

Furthermore you should ask yourself: What does PHP5 in intrepid offer that is not offered in PHP5 on hardy? My guess is: Nothing!

---

### Post by biji on 2008-09-03
thanks.. so there is php5 version in hardy already... i will use that

---

### Post by hyper_ch on 2008-09-03
so you say you didn't even check out first whether php5 exists for hardy or if there are other ways to get it? Instead you just opened here a thread and hope that someone just provides the answer?

---

### Post by biji on 2008-09-03
yup, i follow tutorial somewhere to install php5.. it says have to add intrepid

---

### Post by Oldsoldier2003 on 2008-09-03
> **biji said:**
> yup, i follow tutorial somewhere to install php5.. it says have to add intrepid

any tutorial that tells you to add the repos for the alpha version of the next development OS should be avoided like the plague. They are playing with fire, the one that will get burned is you.

Mixing repos is a BAD idea. it can lead to instabilities that may render your system completely unusable. Sure you might get away with it this time, and the next and the next- but it's like playing Russian Roulette- eventually the bullet will come up.

---

