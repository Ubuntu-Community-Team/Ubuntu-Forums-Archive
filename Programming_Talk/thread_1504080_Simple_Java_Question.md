---
title: "Simple Java Question"
date: 2010-06-07
forum: Programming Talk
---

### Post by telosin on 2010-06-07
Hello,
My brain is dead and I just can't figure this out. It's a pretty simple question, I think. I set up a custom class with a default constructor with 3 parameters. Those parameters are "String columnName", "String columnType", and "int columnNumber". The class is called ObjectLayout. Here is my statement to create an array from this class:

ObjectLayout [ ] ol = new ObjectLayout [colNum + 1];

with colNum having already been defined. When I try to work with this array, I get a NullPointerException and I know the next thing I have to do is fill this array with values but I remember for the life of me how to do that. I've tried lots of things including this which I figured would work:

ol [0] = new ol ("blah","blah",5);

but it didn't work for me. I know that there's a fill command for arrays but it didn't work for me when I tried to follow the Object [] syntax.

Can anyone help me out?

Thanks for your time.

---

### Post by PaulM1985 on 2010-06-07
You should be doing:

ol [0] = new ObjectLayout("blah","blah",5);

not

ol [0] = new ol("blah","blah",5);

Can you post more of your code?

Paul

---

### Post by telosin on 2010-06-07
Wow, that was it. Thank you so much. I can't believe I missed that...
If you want me to post more of my code, I can, but that solved the problem.

Thanks again Paul.

---

### Post by PaulM1985 on 2010-06-07
I only meant for you to post the code if that didn't fix it.  I wasn't sure if what you had posted was in your actual code or something that you mistyped in describing your problem.

Glad your up and running.

Paul

---

