---
title: "GObject properties &amp; allocation"
date: 2010-04-26
forum: Programming Talk
---

### Post by Masterofpsi on 2010-04-26
Hey, all. I'm teaching myself the Glib object library, and I'm having some trouble with object properties. Say I have a property that gets added like this:

```

enum {
        PROP_0,
        PROP_NAME
};

static void
my_class_init (MyClass *klass) {
        g_object_class_install_property (object_class, PROP_NAME,
                                         g_param_spec_string("name",
                                                             "n",
                                                             "The object's name.",
                                                             "noname",
                                                             G_PARAM_READWRITE | G_PARAM_CONSTRUCT));
}

```

The default value for the "name" property is then "noname." So, if I understand it correctly, if the user does not provide a value for the name property to ```
g_object_new()
```, the constructed object's name value will be "noname". So my question is: can I count on this string being dynamically-allocated so that I can free it in the finalize method and/or in the property's setter?

---

