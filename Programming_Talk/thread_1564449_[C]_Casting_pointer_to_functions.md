---
title: "[C] Casting pointer to functions"
date: 2010-08-30
forum: Programming Talk
---

### Post by Odexios on 2010-08-30
What happens if I cast a pointer to a function to a pointer to a function with different signature?

I mean, can I cast a pointer of this type:

[php]void (*first)(int whatever);[/php]to this:

[php]void (*second)(int whatever_1, int whatever_2);[/php] and expect it to work?

I thought this kind of behaviour was illegal (or at least undefined), but I think GTK+ does exactly this...

---

### Post by dwhitney67 on 2010-08-30
Umm, let me guess... It would have killed you to find out the answer to your question on your own.

Gotta love the 21st century... laziness is rampant.

```

void oneArg(int value)
{
}

void twoArg(int value1, int value2)
{
}

int main()
{
   void (*function1)(int) = oneArg;
   void (*function2)(int) = twoArg;   // generates a compiler warning

   (*function1)(1);
   (*function2)(1, 2);   // here too.

   return 0;
}

```

---

### Post by Bachstelze on 2010-08-30
Normally, you'd get a

```
warning: assignment from incompatible pointer type
```

Do you have exmples of how GTK does it?

---

### Post by Odexios on 2010-08-30
Sorry to both of you, I forgot to edit the OP with an example.

In GTK, you can find this:

[php]g_signal_connect_swapped(button,
"clicked", G_CALLBACK(gtk_widget_destroy),
window);
[/php], where button is an instance of a GTK_TYPE_BUTTON class.

The function gtk_widget_destroy has this prototype:

[php]void gtk_widget_destroy(GtkWidget *widget);[/php]while the g_signal_connect_swapped passes to gtk_widget_destroy two arguments: window and button.

Everything works fine without a warning, and this behaviour is typical of the examples I found on the Official GNOME guide.

I tried something like the example you wrote, dwhitney, and I got the warnings; what I don't really understand is why I'm allowed, here, to do something like this. I understand what happens (gtk_widget_destroy takes only the first argument from the stack and completely ignores the other), but I don't see why you can do something like this.

I couldn't find on the standard something which justifies this behaviour, but I doubt GTK gets out of the standard rules, so I'm pretty sure I'm wrong somewhere. But I can't say where...

---

### Post by dwhitney67 on 2010-08-30
From /usr/include/glib-2.0/gobject/gclosure.h:
```

...

/**
 * G_CALLBACK:
 * @f: a function pointer.
 * 
 * Cast a function pointer to a #GCallback.
 */
#define G_CALLBACK(f)                    ((GCallback) (f))

...

/**
 * GCallback:
 * 
 * The type used for callback functions in structure definitions and function 
 * signatures. This doesn't mean that all callback functions must take no 
 * parameters and return void. The required signature of a callback function 
 * is determined by the context in which is used (e.g. the signal to which it 
 * is connected). Use G_CALLBACK() to cast the callback function to a #GCallback. 
 */
typedef void  (*GCallback)              (void);

```

Basically the glib-folks are pulling off some hocus-pocus with casting.

I can do the same trick:
```

void twoArg(int value1, int value2)
{
}

int main()
{
   void (*function1)(int) = (void (*)(int)) twoArg;

   ((void (*)(int, int))(*function1))(1, 2);

   return 0;
}

```

---

### Post by StephenF on 2010-08-30
G_CALLBACK() defined as a macro but translates to a cast does so to a void pointer which strips away checking so avoiding any warnings.

---

### Post by MadCow108 on 2010-08-30
> **Odexios said:**
> I couldn't find on the standard something which justifies this behaviour, but I doubt GTK gets out of the standard rules, so I'm pretty sure I'm wrong somewhere. But I can't say where...

you are right you leave the standard defined area with these kind of tricks.
You generally lose portability e.g. because other architectures handle function argument passing differently:
[http://en.wikipedia.org/wiki/Calling_convention](http://en.wikipedia.org/wiki/Calling_convention)

But the gtk people archive their portability by being very careful and with tons of macros to specialize for different cases.

if you do not know exactly what you're doing, don't do it!

---

