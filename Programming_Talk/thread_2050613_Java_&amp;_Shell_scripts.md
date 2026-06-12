---
title: "Java &amp; Shell scripts"
date: 2012-08-31
forum: Programming Talk
---

### Post by 3v3rgr33n on 2012-08-31
I'm trying to test multiple programs via the terminal. They require user interaction so I want to pipe text to the code on request. Is this possible?

I cannot change the code as I have not written it and I want to test it's correctness. The programming Language is Java. I'm not an expert in shell scripting. Can someone please point me in the right direction.

Regards
Adeeb

---

### Post by Lars Noodén on 2012-08-31
The syntax is simple, you just use a pipe (|) to connect the two programs and the output from the first will become the input for the second.  More than two can be chained together.  AFAIK there is no limit.

```

ls | less
ls | sort | less

```

See material on "pipes and redirects":

[http://www.dsj.net/compedge/shellbasics1.html](http://www.dsj.net/compedge/shellbasics1.html)
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by drmrgd on 2012-08-31
I'm not clear on what you're trying to do here.  Maybe a more clear explanation of what you want your bash script to do, and how it's to interact with the java program(s) would be helpful.  

You can catch user input in Bash and assign it to a variable that you can then pass to the Java program.  The function 'read' might be what you're looking for?  

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html)

---

### Post by steeldriver on 2012-08-31
or maybe you need something like expect (or dejagnu)?

[http://en.wikipedia.org/wiki/Expect](http://en.wikipedia.org/wiki/Expect)

[http://expect.sourceforge.net/](http://expect.sourceforge.net/)

[http://www.gnu.org/software/dejagnu/](http://www.gnu.org/software/dejagnu/)

---

### Post by 3v3rgr33n on 2012-08-31
Hi thanks for the replies. Let me give you an example of what I need. Say you have the following code:
```
 
Scanner input = new Scanner(System.in);
System.out.println("Enter your name");
String name = input.nextLine();
System.out.println("Enter you age");
int age = input.nextInt();

```I want to take take the input from a file. Say I have a file "Test.in". It contains two lines
> 
Adeeb
100
I don't want to physically enter the name and age when the code prompts for it, except I want to write a script that will retrieve it from the file and pass it to the file. I do not want to change the code. I'm just trying to test multiple files of code that  were written by different kinds of people (I was sorta testing them).

---

### Post by steeldriver on 2012-08-31
sounds like 'expect' is exactly what you need (although DISCLAIMER I haven't used it since the days of dialup so there may be better / more modern options that I'm not aware of)

Just googled for some simple examples to get you started - this looks like a good one

[http://www.thegeekstuff.com/2010/10/expect-examples/](http://www.thegeekstuff.com/2010/10/expect-examples/)

---

### Post by 3v3rgr33n on 2012-08-31
Thank you very much. Let me look at it now.

---

