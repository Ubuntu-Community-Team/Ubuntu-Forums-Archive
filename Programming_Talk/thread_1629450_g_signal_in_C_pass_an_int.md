---
title: "g_signal in C pass an int"
date: 2010-11-23
forum: Programming Talk
---

### Post by Woody1987 on 2010-11-23
For the life of me I cant get this to work. I have been searching high and low for an example of how to pass an int as a parameter in a g_signal. You would think it would be a very basic example and be listed everywhere but no, I appear to be the only person who needs this done. Anyway heres my code thus far:
```

int a = 1;
g_signal_connect(G_OBJECT(updateEventBox), "button_press_event", G_CALLBACK(myfunc), &a);

void myfunc(int a)
{
    printf("%d\n", a);
}

```

Each time the printf just spews a bunch of incorrect numbers. Whats wrong with it?

---

### Post by dwhitney67 on 2010-11-23
Since you are passing the address of an int, don't you think the parameter within the function should at least be declared as a void*, or whatever gtk uses to identify pointers.

Then, within the function, cast the generic pointer to an int pointer, then dereference the pointer to obtain the int value.

After a little research, maybe something like:
```

void myfunc(GtkWidget* w, gpointer clientData)
{
   int* value = (int*) clientData;

   g_printf("value = %d\n", *value);
}

```

---

### Post by Woody1987 on 2010-11-24
Thanks, its better but not there yet. I used your code, but instead of printing my int, it displays either a 4, 5 or a 6 seemingly at random. For example if I pass a 2 it prints out:

> value = 4
value = 4
value = 5
value = 4
value = 6
value = 4
value = 4
value = 5
value = 4
value = 6
value = 4
value = 4
value = 5
value = 4
value = 6
value = 4
value = 4
value = 5


---

### Post by spjackson on 2010-11-24
> **Woody1987 said:**
> Thanks, its better but not there yet. I used your code, but instead of printing my int, it displays either a 4, 5 or a 6 seemingly at random. For example if I pass a 2 it prints out:
Without code we can only guess. So I'll guess that you pass it the address of a stack variable which is no longer valid when your function is called. If I'm wrong, then please post a small complete example that demonstrates the problem.

---

### Post by Arndt on 2010-11-24
> **Woody1987 said:**
> Thanks, its better but not there yet. I used your code, but instead of printing my int, it displays either a 4, 5 or a 6 seemingly at random. For example if I pass a 2 it prints out:

After also very little research, I find this post:

[http://lists-archives.org/gtk/07188-g_signal_connect-button-press-event-vs-pressed.html](http://lists-archives.org/gtk/07188-g_signal_connect-button-press-event-vs-pressed.html)

---

