---
title: "How to run commands with parameters in Java with gksudo?"
date: 2010-04-25
forum: Programming Talk
---

### Post by Tommy599 on 2010-04-25
Hi,

I want to run the gksudo lshw -short command from Java.

```
gksudo lshw
``` works fine, but I don't need that much information. 

I've tried
```
gksudo lshw\\ -short
gksudo 'lshw -short'
gksudo \"lshw -short\"
```
as Java Strings but none of them work. 


They all work fine from the command line.
I know I can parse the result of lshw but I don't want to if there is a way to run gksudo lshw -short from Java.

Anyone know how/if it can be done?

Thanks!

---

### Post by geirha on 2010-04-25
try
```
gksudo -- lshw -short
```

---

### Post by slavik on 2010-04-25
how are you running them from Java?

---

### Post by Tommy599 on 2010-04-25
> **geirha said:**
> try
```
gksudo -- lshw -short
```

Wow it works! 

Thank you very much! 

Can I also ask why it works? What does the -- do?

---

### Post by slavik on 2010-04-25
generally -- means 'stop processing command line options'

---

### Post by Tommy599 on 2010-04-25
> **slavik said:**
> how are you running them from Java?

I have the commands in an array of Strings and pass them to 
```
runtime.exec(commands[i]);
```

---

### Post by slavik on 2010-04-25
that invokes the shell, I bet. Look into spawning a separate process.

---

### Post by geirha on 2010-04-25
Unfortunately the gksudo man-page does not document the special -- option, though it is fairly common for commands to accept it. As slavik mentioned, it tells the app to stop reading options. Without it, gksudo will treat any argument starting with a - as an option to gksudo. When it encounters --, all arguments following will no longer be treated as options to gksudo, and just passed on to the child process.

If you ask me, this behavior is absurd; the sudo command does not behave this way, but, at least there's a way to work around it.

Oh and according to the javadoc, Runtime.exec does not run the commands in a shell, which would explain why the  attempts of quoting did not work.

---

### Post by Tommy599 on 2010-04-25
> **slavik said:**
> that invokes the shell, I bet. Look into spawning a separate process.

I can get the output I want from it, why change it? 

And what do you mean by separate process? Like a background process or a new Java thread?

---

### Post by slavik on 2010-04-25
> **Tommy599 said:**
> I can get the output I want from it, why change it? 

And what do you mean by separate process? Like a background process or a new Java thread?
I mean fork/exec.

as for --, man getopt ;)

---

