---
title: "[SOLVED] Java: convert a unicode value into a char"
date: 2008-03-11
forum: Programming Talk
---

### Post by NovaAesa on 2008-03-11
Say I have an integer value and want to convert it into a char, what's the best way of doing this? I have looked through the javadocs for the Character class but couldn't come up with anything.

Could someone point me in the right direction?

---

### Post by amingv on 2008-03-12
You mean something like this?

[PHP]
class Main {
    public static void main (String[] args) {
        int foo = (int)'A';
        char bar = (char)65;
        System.out.println (foo);
        System.out.println (bar);
    }
}
[/PHP]

---

### Post by NovaAesa on 2008-03-12
Thank you! That was exactly what I was looking for.

---

