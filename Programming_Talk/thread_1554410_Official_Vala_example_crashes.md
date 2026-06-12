---
title: "Official Vala example crashes"
date: 2010-08-16
forum: Programming Talk
---

### Post by kahumba on 2010-08-16
Hi,
I'm trying out the official example from
[http://live.gnome.org/Vala/ReferenceHandling](http://live.gnome.org/Vala/ReferenceHandling)
but it crashes yielding a stack trace when I run it, any ideas why?

```

[Compact]
[CCode (ref_function = "foo_up", unref_function = "foo_down")]
public class Foo {

    public int ref_count = 1;

    public unowned Foo up () {
        ++ref_count;
        return this;
    }

    public void down () {
        if (--ref_count == 0) {
            delete (void*) this;
        }
    }

    public void method () { }
}

void main () {
    Foo foo = new Foo ();    // allocate, ref
    foo.method ();
    Foo bar = foo;           // ref
} // unref, unref => free

```

---

### Post by splicerr on 2010-08-16
IMHO it's best to stay away from compact classes and just use GObject based ones. Having said that you've either encountered a bug in Vala or the example  was doing something that resulted in undefined behavior.

If you compile with --save-temps and look at the generated C code you can see it crashes because of a mismatch between memory allocation and free function. (g_free should be g_slice_free)

```

Foo* foo_new (void) {
    Foo* self;
    self = g_slice_new0 (Foo);
    ...
}

void foo_down (Foo* self) {
   ...
   g_free ((void*) self);
   ...
}

```I suggest you either file a bug at:

[https://bugzilla.gnome.org/browse.cgi?product=vala](https://bugzilla.gnome.org/browse.cgi?product=vala)

 or post to the Vala mailing list:

[http://mail.gnome.org/mailman/listinfo/vala-list](http://mail.gnome.org/mailman/listinfo/vala-list)

---

### Post by kahumba on 2010-08-17
Thanks a lot.

---

