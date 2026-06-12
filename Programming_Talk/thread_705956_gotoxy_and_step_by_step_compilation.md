---
title: "gotoxy and step by step compilation"
date: 2008-02-23
forum: Programming Talk
---

### Post by phanther on 2008-02-23
1)is this function gotoxy available in ubuntu to program in c.if so please mention the header file also.

2)In turbo c, we use F7 for step by step compilation apart from direct compilation by pressing Alt+F9.i want to know what is the alternative for this F7 function in C

Thanx in advance

---

### Post by slavik on 2008-02-23
1. what is gotoxy?
2. what is step by step compilation?

---

### Post by LaRoza on 2008-02-23
I don't know what gotxy is, but it sounds like something that would be in NCurses.

I don't know what step by step compilation is, do you mean a debugger?

---

### Post by phanther on 2008-02-24
ok i'll make it more clear

1) gotoxy(x,y) is an inbuilt function in C( i am talking about the situation where i am using turbo c in Windows, not in Linux).this function is particularly useful in displaying the output at a specific coordinates on the screen, where x and y are the parameters passed(they r the coordinates).so it basically displayes your output on that portion of the screen.
what i am looking for is a similar code which functions in linux, or if this function is already available then i want the header file.

2)yea basically i was implying upon step by step debugger, sorry i spelled it wron previously.in turbo c we use F7, i want to know the similar version of F7 in linux

---

### Post by LaRoza on 2008-02-24
> **phanther said:**
> ok i'll make it more clear

1) gotoxy(x,y) is an inbuilt function in C( i am talking about the situation where i am using turbo c in Windows, not in Linux).this function is particularly useful in displaying the output at a specific coordinates on the screen, where x and y are the parameters passed(they r the coordinates).so it basically displayes your output on that portion of the screen.
what i am looking for is a similar code which functions in linux, or if this function is already available then i want the header file.

2)yea basically i was implying upon step by step debugger, sorry i spelled it wron previously.in turbo c we use F7, i want to know the similar version of F7 in linux

See NCurses, [http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific)

See: gdb

---

### Post by slavik on 2008-02-24
going to add to laroza's post, for a graphical debugger, there is ddd (it uses gdb as backend).

---

### Post by LaRoza on 2008-02-24
> **slavik said:**
> going to add to laroza's post, for a graphical debugger, there is ddd (it uses gdb as backend).

Thanks, I am not very familiar with gdb.

---

### Post by lnostdal on 2008-02-24
there is also [http://www.kdbg.org/](http://www.kdbg.org/) .. some prefer it even though they use gnome

---

