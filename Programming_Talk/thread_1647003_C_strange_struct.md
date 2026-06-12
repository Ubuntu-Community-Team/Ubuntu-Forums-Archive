---
title: "C strange struct"
date: 2010-12-16
forum: Programming Talk
---

### Post by conehead77 on 2010-12-16
Hi,

i'm quite new to C and i encountered following code snippet:

[PHP]struct prefix_ipv6 *
prefix_ipv6_new (void)
{
  struct prefix_ipv6 *p;

  /* Allocate a full-size struct prefix to avoid problems with structure
     size mismatches. */
  p = (struct prefix_ipv6 *)prefix_new();
  p->family = AF_INET6;
  return p;
}[/PHP]

I only know "normal" structs like this:

[PHP]struct mystruct
   {
       int int_member;
       double double_member;
       char string_member[25];
   } variable;
[/PHP]

What does the first version do? It seems like there is a function inside the struct? But i don't really get it. Also does anybody have a good suggestion for a more advanced C book?

---

### Post by Decatf on 2010-12-16
The function [COLOR=#000000][COLOR=#0000BB]prefix_ipv6_new [/COLOR][/COLOR]returns a pointer to a prefix_ipv6 struct.

The line [COLOR=#000000][COLOR=#0000BB]p [/COLOR][COLOR=#007700]= ([/COLOR][COLOR=#0000BB]struct prefix_ipv6 [/COLOR][COLOR=#007700]*)[/COLOR][COLOR=#0000BB]prefix_new[/COLOR][COLOR=#007700](); [/COLOR][/COLOR] is just calling a function prefix_new() and casting the return value to a prefix_ipv6 pointer.

---

### Post by trent.josephsen on 2010-12-16
That's not a struct definition -- it's a function definition.  The definition of struct prefix_ipv6 should look very like your example.

That beside the point, this is very simple in terms of syntax.  If you couldn't figure that out on your own, I doubt you're ready for anything that could be called "advanced C".  Re-read your copy of K&R2 (you do have one, surely?) and do all the exercises you skipped the first time.

---

### Post by StephenDavison on 2010-12-16
```
struct prefix_ipv6 *
prefix_ipv6_new (void)
{
  struct prefix_ipv6 *p;

  /* Allocate a full-size struct prefix to avoid problems with structure
     size mismatches. */
  p = (struct prefix_ipv6 *)prefix_new();
  p->family = AF_INET6;
  return p;
}
```Let's see, it's been many years since I've looked at C, but here goes...
prefix_ipv6_new() is a function that accepts no parameters and returns a pointer to a prefix_ipv6 structure.  In that function, p points to a dynamically allocated prefix_ipv6 structure.  p->family is the family element in the structure pointed to by p, and it is assigned the value AF_INET6.  So, what you are looking at is a function not a struct.

AFAIAC, if you only buy one book on C make it the the K&R book, The C Programming Language.

Edited to add:  he he, looks like Trent and Decatf got to it while I was typing.  Good to see the K&R book still rules.

---

### Post by conehead77 on 2010-12-16
Ah, thank you all. I guess my brain needs some adjustment to read C code. And thanks for the book suggestion, i'll check it out for sure.

---

