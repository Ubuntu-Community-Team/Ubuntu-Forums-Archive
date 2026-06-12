---
title: "Gedit + Java Highlighting"
date: 2009-08-17
forum: Programming Talk
---

### Post by pike168 on 2009-08-17
So im using gEdit to work with java and i really like it but there is one small problem that is really annoying me, gEdit's syntax highlighting for .java files doesnt highlight the type "String" like it does for "int" and "double". So i though by adding this to the java.lang file, it would have then "String" highlighted:

      <keyword>String</keyword>

i add that to the <context id="primitive-types" style-ref="type"> section of the java.lang file and save.

This does not seem to be working however, Is there any way to get "String" highlighted like it does for all the other types ?

---

### Post by pike168 on 2009-08-17
Fixed it.

Added "<style name="def:String".....> to my gEdit .xml styles sheet. Now "String" is highlighted like all the other variable types.

---

### Post by hyperAura on 2009-08-17
cool thnx for the tip, i was always avoiding gedit with Java because of this reason..:)

---

