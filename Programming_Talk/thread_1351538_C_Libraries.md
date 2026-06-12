---
title: "C Libraries"
date: 2009-12-10
forum: Programming Talk
---

### Post by slumbergod on 2009-12-10
Just a simple question I hope more experienced C programmers might be willing to offer their thoughts on.

It's been ages since I played around with C (especially given how much faster and easier I can do things in Python). But I'd like to go back and play around with making a small GUI app. Obviously, I'll make use of Gtk libraries (if that is the toolkit I decide to use).

What I am curious about is whether there are any other libraries programmers use other than the ones that are standard with C. Whenever I read about C there are always warnings about using some statements because they are risky and so on. Have newer C libraries been released / made available to improve on these riskier activities or do people just write their own and keep their own libraries?

Please, if you are sick of questions like this just ignore my post. If you have a constructive comment I'd be grateful (can you tell I am tired of rude tosser comments?).

---

### Post by dwhitney67 on 2009-12-10
> **slumbergod said:**
> 
What I am curious about is whether there are any other libraries programmers use other than the ones that are standard with C.
What do you mean by this?  Gtk is a library, but it has nothing to do with the C Standard Library.  Think of it as complementing the C library, but not as part of it.  Ditto for any other library you can think of.

If you are interested in developing graphics applications, then I would suggest Gtk++.  In other words, forget C and instead use C++.

I started out learning C (at the university level), and then on the job.  So I am not putting it down; in fact, it is a great language, but I prefer to use C++ because it offers more tools.

---

### Post by nvteighen on 2009-12-11
> **slumbergod said:**
> 
What I am curious about is whether there are any other libraries programmers use other than the ones that are standard with C. Whenever I read about C there are always warnings about using some statements because they are risky and so on. Have newer C libraries been released / made available to improve on these riskier activities or do people just write their own and keep their own libraries?


I guess you're talking about stuff like gets(), which can be really risky. Ok, I'm really annoyed sometimes by the fact of knowing the C Standard Library has such a function whose feature is already present at fgets(), which is safer.

The issue in the C Standard Library is that all implementations have to implement all specification of the ISO C Standard. Due to C limitations, creating a function which retrieves everything from stdin till a '\n' and stores it into the char pointer it was given as argument (this is what gets() does) will always be risky because there's no way to guarrantee the string will have the enough amount of storage to hold the data from stdin. To change that, you'll have to change the standard; the reason why a function like gets() is still around is because of backwards compatibility.

Third party libraries should be designed to be safe. If a library is unsafe, people will notice it (at who knows what costs) and stop using it... if it's a Free Software library, maybe a patch ends it up, but if propietary, it can take ages to even notice there is a problem. That's why ehen choosing a library, one should go for well-established libraries with a large user-base... and if Free Software, much better.

But in this, you are in the same sitiuation like any end-user who's concerned about the security of the program he's going to install in his computer.

---

### Post by slumbergod on 2009-12-11
Thanks. So it seems that most people just make use of the standard libraries and if they need a better implementation of a function they just write their own.

Ummmm I know C++ is popular but in the linux world everything I could possible want to contribute to one day is still in C.

---

