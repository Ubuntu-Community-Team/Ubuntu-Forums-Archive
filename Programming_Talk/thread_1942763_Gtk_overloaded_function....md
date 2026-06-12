---
title: "Gtk overloaded function..."
date: 2012-03-18
forum: Programming Talk
---

### Post by tuket on 2012-03-18
Hello, I'm making a program in c++ using gtk and I'm getting the following error.

```
error: overloaded function with no contextual type information
```

In this line:
```
g_signal_connect(G_OBJECT(listen), (const gchar*)"clicked", G_CALLBACK(send), &data);
```

I hope you can help me.;)

---

### Post by tuket on 2012-03-18
Ok, guys I have discovered the problem. 
It is that there are two headers with the same function.
Now the question is: It there any way to specify the header I want?

---

### Post by cgroza on 2012-03-18
Could you provide the signature of both functions and the context that line is in?
Maybe you can provide the compiler more context so the overloading mechanisms knows which one to choose.

---

