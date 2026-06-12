---
title: "Quick algebra question"
date: 2013-10-09
forum: Programming Talk
---

### Post by kangaba on 2013-10-09
Hi,
I'm trying to create a **sphere** (previously said circle, sorry) by hand and I'm stuck with a math question: how do I map from [-1.0, 1.0] to [0, 3.14]? For example, if I got 0.0 I should get 1.57, and for 1.0 I should get 3.14.

After googling I didn't find a quick answer except to learn linear algebra from scratch with its vectors matrices etc (I learned it like 2 years ago but totally forgotten by now).

---

### Post by bleutyler on 2013-10-09
Are you asking about transforming a circle with center (-1, 1) to center (0, pi)?

---

### Post by kangaba on 2013-10-09
No, I mentioned the sphere (sorry, I said circle before) as a quick explanation of why I need it, but it's irrelevant to my algebraic question of how to get a corresponding value from (say) set B (0..3.14) based on values from set A(-1, 1), for example for input number -1 I should get zero, and for input number 1 I should get 3.14.

Basically I'm creating the sphere out of vertical stripes, like [this]("http://www.yaldex.com/open-gl/images/18fig01.jpg"), so the Z value must be concave - based on the Y's values from top to bottom (1.0, -1.0), this is achieved by mapping Y's values to 0...PI which when applied to the sine and then put into Z gives a concave stripe.

---

### Post by Vaphell on 2013-10-09
it depends on the transformation but if all you want to do is linear scale+shift, result=pi*(x+1)/2

that said, you should be really worried about your math skills because proportions are done in primary school
set length = 2 scaled to the length of pi => scale factor is pi/2
0*pi/2 becomes pi/2 => required shift is pi/2
= scale*x+shift = pi/2*x + pi/2 = (x+1)*pi/2

---

### Post by kangaba on 2013-10-09
Thanks a lot, I wonder if there is a tutorial that teaches this without having to have strong algebra knowledge, I googled and only found tutorials with too much math abstraction like teaching vectors, matrices and it's unclear if that will contain the info I need to solve this kind of transformations, whatever they're called.

---

