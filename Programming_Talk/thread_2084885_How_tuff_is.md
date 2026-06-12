---
title: "How tuff is"
date: 2012-11-16
forum: Programming Talk
---

### Post by miguelpires on 2012-11-16
Hello,
This my be a dumb question, but how hard is to port a C sharp (I think this is the language) accounting program, from a  windows base to a linux base?

I don't know how big is th source code, neither what is inside, but for me to understand can someone explain to me?

Best Regard's
Miguel

---

### Post by cgroza on 2012-11-17
It depends on how many windows specific features and libraries that program uses.

---

### Post by Unterseeboot_234 on 2012-11-17
The whole idea about .NET was similar code would drive a variety of technologies be it VB or SQL Server. MONO is the Linux community attempt to utilize the MS .NET libraries. You would need MS Developer Studio and the Mono bridge plug-in to begin discovering the methods within the software you wish to reverse engineer.

Java has a similar Reflection of the software functions and it has been my experience using reverse-engineering tools that you end up with a huge list of unmeaningful names for methods and variables. Like for example

private double method00001( double arg1, boolean arg2 ) {
if (arg2)  return -1.0 * arg1;
return 0.0;
}

and then somewhere else in the code arg1 is var00099;

IMHO, you might be better off designing your own GUI and reverse-code the functionality.

---

