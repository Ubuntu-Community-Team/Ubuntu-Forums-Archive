---
title: "Mono Documentation?"
date: 2006-01-12
forum: Programming Talk
---

### Post by Viro on 2006-01-12
I've spent the last few days playing around with Mono, writing some toy code to explore its features. One thing that I'm really missing is some good documentation! In Monodoc, a lot of entries are just stubs, and contain no useful information. I've searched the net for documentation regarding mono, but there isn't much to go on.

For example, I've Googled a bit, and was looking for ways to interface with system libraries in Mono without manually wrapping all the functions I need via P/Invoke. Turns out there is a Posix/Unix namespace in Mono that according to the description does what I need. However, there isn't any information on what's included/excluded, and more importantly how to use it (compiler flags? runtime flags? I get errors when trying to use classes from there).

What I am looking for is something like the MSDN or the Javadocs which provide all the APIs and language features available on Mono. I know that the information on MSDN applies to a certain extent to Mono, but I'm interested in the Mono stack, not the .NET stack. Does anyone know where I go to find the information I need?

---

### Post by mostwanted on 2006-01-12
[http://www.go-mono.com/docs/index.aspx](http://www.go-mono.com/docs/index.aspx)

---

### Post by public_void on 2006-01-12
Mono has something called MonoDoc, which I think your looking for. But that is like the link suggest and it has many missing entries. It does get update regularly only a couple of days ago I downloaded version 1.1.11, now 1.1.13.

---

### Post by Viro on 2006-01-12
[QUOTE=mostwanted][http://www.go-mono.com/docs/index.aspx](http://www.go-mono.com/docs/index.aspx)[/QUOTE]

I was afraid that would be the best site for information. It's so.... sparse, nothing like the Javadocs or MSDN or even Qt or wxWidgets documentation.

For example the Mono.Unix namespace (and it happens to be the namespace I'm most interested in), which is almost entirely devoid of information and since this isn't part of the standard .NET framework, I can't rely on MSDN or some Microsoft .NET book/website to provide me with the information I need.

---

### Post by David Marrs on 2006-01-12
The only documentation I've seen has been lousy. If you find anything good, please let me know. :)

---

### Post by Jessehk on 2006-01-12
Unfortunately, this is my only "beef" with open-source software of this type. There is no (or very little) documentation!

For example, how can gtkmm compete with Qt when there is hardly any up-to-date documentation on gtkmm and Qt has hundreds of detailed class references, examples, and tutorials?

The same applies to gtk# documentation, documentation for things like the GIMP, and other OSS.

---

### Post by Viro on 2006-01-13
Surely if they want Mono to gain a broader acceptance as a desktop development environment, they should have better documentation. Not necessarily as complete as the MSDN or Javadocs, but even like wxWidgets which at least documents all the classes. Surely with the advent of things like Doxygen, it should be fairly trivial to generate documentation assuming the developers comment their code?

On a related note, seeing as this is open source software, how does one go about finding what classes/methods are in a particular namespace on Mono? If I can do that, perhaps when I am free I could try to help the Mono project update their rather sparse documentation.

---

