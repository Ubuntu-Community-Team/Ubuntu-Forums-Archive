---
title: "GUI Designers for Eclipse"
date: 2013-03-27
forum: Programming Talk
---

### Post by vikkyhacks on 2013-03-27
I am looking for a perfect GUI designer for eclipse. I know this has been discussed before but I just am not able to find the right one.

   1. I don wish to use Google's GUI Designer cos it crashes too frequently and it is an outdated package.
   2. Found jigooo good but it is not COMPLETELY free.

I am looking for a FREE designer which generates a clean code UNLIKE netbeans where the code cannot be ported easily anywhere else, I creates some xml and .form files which makes everything crappy.

Thanks in advance

---

### Post by harx1337 on 2013-03-28
I'm kind of in the same boat. Netbeans builds a very pretty GUI with minimal work and has tons of flexibility, but OMFG is the code a disaster! Also, I'm pretty well tied to Eclipse.

The approach I've developed is to use Netbeans to build the GUI and point all interacactions with an interface. I implement it in a dummy class in Netbeans (with just System.out.println for events) and implement the real class in Eclipse. After an Netbeans edit I drag it (along with the interface if it changed) over into Eclipse and then *never open that file*.

This is clearly not ideal, but it is sustainable and gives me all the GUI design power of Netbeans while still doing the bulk of the work in Eclipse.


Google's tool is nice but far too buggy, I don't know that there is anything better in the open-source domain (at least not for Swing work).

---

### Post by vikkyhacks on 2013-03-29
Hey thanks for replying at least something I was almost losing faith with this forum,


Tried visual swing for eclipse. Its good, it generates very clean code. Just set the layout to null before you start designing your application. It generates very very clean code like some ordinary programmer, :)

---

