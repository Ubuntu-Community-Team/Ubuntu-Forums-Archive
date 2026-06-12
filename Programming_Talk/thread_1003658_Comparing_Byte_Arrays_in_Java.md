---
title: "Comparing Byte Arrays in Java"
date: 2008-12-06
forum: Programming Talk
---

### Post by akshata on 2008-12-06
Hi,
    I need to compare two Byte Arrays in Java and check if one is greater than the other or lesser. Can this be done? I am a novice in Java and need help.

Thannk You

---

### Post by geirha on 2008-12-06
Either loop through the arrays and compare them byte by byte, or wrap them in ByteBuffers and use ByteBuffer's compareTo() method.

[http://java.sun.com/j2se/1.5.0/docs/api/java/nio/ByteBuffer.html](http://java.sun.com/j2se/1.5.0/docs/api/java/nio/ByteBuffer.html)

Look at the wrap() and compareTo() methods.

---

### Post by Unterseeboot_234 on 2008-12-07
The BitArray is the one API class I have noticed that does change on 64-bit or 32-bit computers doing java SDK. On my machine I get 64 placeholders for the bits init to FALSE using the 32-bit JRE. You MUST load a BitArray with values. You can get the Cardinality of the BitArray to speed things up with transversing the Array (iterator).

Having said that statement above, you probably want ByteBuffer so you get Comparator. I have had ByteBuffer compare correctly on 32-bit and 64-bit platforms.

---

