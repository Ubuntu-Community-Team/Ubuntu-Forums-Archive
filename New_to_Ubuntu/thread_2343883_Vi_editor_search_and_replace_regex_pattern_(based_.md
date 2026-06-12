---
title: "Vi editor search and replace regex pattern (based on some character in the line)"
date: 2016-11-20
forum: New to Ubuntu
---

### Post by devb1 on 2016-11-20
Hello,
I need a search replace expression to use in vi editor (on any other way) in some files where the condition is as below:
Programmers will understand my need. (It is  fortran to C conversion scenario).

Before replacement: 
 <Some_String1> = <Some_String2>[ <Some_number1> : <Some_number2>]

Eg: 
 array1 = array2[4:10]

After replcaement:

for(i = Some_number1; i<Some_number2; i++)
{
      array1[i] = array2[i]
}

Thanks in advance.

---

### Post by TheFu on 2016-11-20
I wouldn't use vi for this unless writing a macro.  I'd use perl which makes things like this really easy thanks to regex grouping.
Lots and lots of vim macro example to work from. Check github and I'm certain you'll find some.  There's a guy that does vimcasts and speaks about vim macros all the time. He's a fanatic about saving 1 keyboard entry by customizing vim. [http://vimcasts.org/](http://vimcasts.org/)

Sorry, I'm not any more help.  I've never created my own vim macro.

---

