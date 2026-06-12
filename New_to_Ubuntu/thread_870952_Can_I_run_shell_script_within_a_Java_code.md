---
title: "Can I run shell script within a Java code?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by madu on 2008-07-26
Hello,

I wonder is there is a 'correct' way of doing this.
Is it possible for me to run a shell script through a Java program?

For example;

class ScriptInJava {

String command = "ping www.google.com";

public static void main(String[] args) {

// Here I want to the run the string 'command' as I would run it on  a terminal.

// Do more stuff here.

}
}

Is it possible to anything like this?

Thank you.

---

### Post by eightmillion on 2008-07-26
[This]("http://mindprod.com/jgloss/exec.html") seems to cover what you are talking about

---

### Post by madu on 2008-07-26
WOw... thats seems exactly what I want..
Thanks a million mate.

---

### Post by ghostdog74 on 2008-07-26
you should always use Java classes whenever possible. Starting from Java 5, there is an isReachable() method in the InetAddress class you can use.

---

### Post by madu on 2008-07-27
Thanks mate.
Didn't know about it. Will check that out.

---

