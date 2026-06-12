---
title: "A funny way to use g_signal_connect in C++ object"
date: 2010-05-08
forum: Programming Talk
---

### Post by qtgtk on 2010-05-08
[SIZE=2]I'm using gstreamer0.10 these days.[/SIZE]The C++ language binding is still under development,and g_signal_connect can't work with a non-static function.However,I find a way.
Example:
```

class A
{
private:
    void connect_function() {g_signal_connect(...,G_CALLBACK(fack_callback),this);}
    static void fake_callback(...,gpointer data)
    {
     A* instance = (A*)this;
     instance->actual_callback(...,NULL);
     }
    void actual_callback(...,gpointer data);
    
};

```

---

### Post by PaulM1985 on 2010-05-08
I've been doing some work with xine recently I used the same sort of method.  It is the only way I can think of to almost have non-static callbacks.

Paul

---

### Post by dwhitney67 on 2010-05-08
Nothing new here; this approach has been done for more 15 years with C++/motif programming.

---

### Post by nvteighen on 2010-05-08
It's just a proxy callback and I think I've seen this even in Python.

But I know it's encouraging to reach to a solution on your own; ok, it may have been implemented better in the past, but it means that you know how to deal with problems. So don't feel bad and keep working!

---

