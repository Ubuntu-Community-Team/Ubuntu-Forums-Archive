---
title: "Eclipse doesn't find the libraries"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by Galpini on 2013-10-25
I used to develop on Unix &" years ago. since then I have been working on Microsoft environment.
I have now installed UBUNTU 12.04 LTS and I have installed Eclipse 3.7.2

I have been through the tutorials for C++ development (Hello World), and I could test the proposed programs.

Now I am trying to write the program proposed in "[SIZE=2]Developing applications using the Eclipse C/C++ Development Toolkit[/SIZE]"
(The program "Lottery.h)

When I build the project, I keep on having errors 'Function 'scanf' could not be resoved (same error for "times", ....)
It does look like that Eclipse doesn't find them in the libraries.

I saw that Eclipse has created an 'includes' folder in my project. There I can see a lot of link to directories. But none of them points to the one containing "times.h", or "stdio.h", ...

1. Why it doesn't include these directories
2. How can I force Eclipse to include these directories in my "includes" directory
3. How can I force Eclipse to include others folders ?

Thank you

---

### Post by Mautobu on 2013-10-25
I would suggest asking at the Eclipse forums, as this problem seems to be application specific.

[http://www.eclipse.org/forums/](http://www.eclipse.org/forums/)

Good luck! And may the odds be ever in your favor.

---

### Post by Galpini on 2013-10-25
Ahhhh,
I found it.

In the project - propertie - C/C++ general / Path and symbols. -- Includes
I need to add a new path.

But hell, why do we need to go through that ? I see there are zillion posts about "scanf".

I'll ask my next question to the eclipse Forum. 
Thanks for your quick reply.

---

