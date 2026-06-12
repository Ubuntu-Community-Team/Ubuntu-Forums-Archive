---
title: "Basic GTKMM Question"
date: 2006-10-06
forum: Programming Talk
---

### Post by fatsheep on 2006-10-06
What terminal command(s) would compile this [simple hello world program]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03s06.html")?

---

### Post by kaamos on 2006-10-06
```
g++ helloworld.cc main.cc -o helloworld `pkg-config gtkmm-2.4 --cflags --libs`
```

The package libgtkmm-2.4-dev is also needed (install with synaptic).

---

### Post by fatsheep on 2006-10-06
Thanks a bunch. :)

---

### Post by Jessehk on 2006-10-06
You'll notice that the answer to your question is in the very tutorial you linked to.

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html#id2515969](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html#id2515969)

---

### Post by fatsheep on 2006-10-06
> **Jessehk said:**
> You'll notice that the answer to your question is in the very tutorial you linked to.

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html#id2515969](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html#id2515969)

That shows how to compile a *single* file, not two.

---

