---
title: "structure of PCI ID not clear"
date: 2010-11-02
forum: Programming Talk
---

### Post by jamesbon on 2010-11-02
Hi,
I am learning Kernel Programming these days I came across a structure
```
static DEFINE_PCI_DEVICE_TABLE(rtl8139_pci_tbl) = {
       {0x10ec, 0x8139, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x10ec, 0x8138, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1113, 0x1211, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1500, 0x1360, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x4033, 0x1360, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1186, 0x1300, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
       {0x1186, 0x1340, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
```

Here are two links
[http://lxr.linux.no/#linux+v2.6.36/include/linux/pci.h#L567](http://lxr.linux.no/#linux+v2.6.36/include/linux/pci.h#L567)
[http://lxr.linux.no/#linux+v2.6.36/include/linux/mod_devicetable.h#L17](http://lxr.linux.no/#linux+v2.6.36/include/linux/mod_devicetable.h#L17)

but I could not understand this type of structure definition.

How does one point the following entry
    {0x10ec, 0x8139, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },

1) What is  first field 0x10ec mapped to is it vendor ?
2) What is  second  field 0x8139 mapped to is it device id ?
3) Does PCI_ANY_ID both represent subvendor,subdevice
4) What are these two 0,0 are they class,mask
5) What is RTL8139 is it driver_data

6) I am also not clear with the way the macro was defined.
  In the definition of following macro
#define DEFINE_PCI_DEVICE_TABLE(_table)  const struct pci_device_id _table[] __devinitconst

_table is it an array of structure of type pci_device_id ?

7) What is __devinitconst?

---

### Post by dwhitney67 on 2010-11-02
It is pointless to study the Linux Kernel code if you do not have a strong foundation with the C programming language.  And believe me, from your previous posts, it is blatantly obvious that you need to study the language some more.

As for your questions, I will answer them with some examples...

Initializing a structure is a basic concept.
```

struct Foo
{
   int   val1;
   int   val2;
   char* str;
};

/* initialize a structure consisting of one entry */
const struct Foo one_entry = { 1, 2, "Hello" };


/* initialize an array of structures */
const struct Foo entries[] = { {1,2,"hello"},
                               {3,4,"world"}
                             };

```

As for your other questions, those a merely macros that are being referenced.  They are defined somewhere in the Linux Kernel header files (eg. init.h or compiler.h).

Here's a similar example (that depends on the Foo structure shown above):
```

#define SOME_WHACKED_OUT_MACRO(_table) const struct Foo _table[]

/* this is equivalent to the array of Foo entries shown earlier */
SOME_WHACKED_OUT_MACRO(entries) = { {1,2,"Hello"},
                                    {3,4,"World"}
                                  };

```
As for __devinitconst, I found the declaration of this macro in linux/init.h, however I personally do not understand it's purpose either.  I do know it references the __section macro from linux/compiler.h.

Suffice to say, __devinitconst is a macro that instructs the compiler something "special".

P.S.  One can also initialize a structure as such:
```

const struct Foo entry = { .str="Hello", .val1=1, .val2=2 };

```

---

### Post by jamesbon on 2010-11-02
Thanks for your explanation in both the posts.
How will I access the structure members declared with this method?
> const struct Foo entries[] = { {1,2,"hello"},
                               {3,4,"world"}
                             };

> 
entries[0]->val1
entries[0]->val2
entries[0]->*str

---

