---
title: "Help with an AJAX script"
date: 2009-06-29
forum: Programming Talk
---

### Post by ivikas on 2009-06-29
Hello all,

          i'am new to ajax technology.I need a script.The usage is like we have a select<select> box and when user select a value from select box then the content for three entries have to be loaded via ajax.

For eg if we have "employee id" as a select field.And if a user select a particular id then the details like "employee name","employee age" and "employee salary" has to be loaded automatically for corresponding id.

Any help or web link will be highly appreciated.

Thanks in advance

With Regards,
Vikas

---

### Post by viljun on 2009-06-29
Start with this
[http://www.xul.fr/en-xml-ajax.html](http://www.xul.fr/en-xml-ajax.html)

Ajax definitive guide from o'reilly is a good buy for you.

---

### Post by loell on 2009-06-29
you can retrieve and update those elements with jquery post.

[http://docs.jquery.com/Ajax/jQuery.post]("http://docs.jquery.com/Ajax/jQuery.post")

you must provide a form wherein if an emplyee id is passed it will retrieve/return those info needed for those elements to be updated.

---

### Post by michaelzap on 2009-06-29
I stopped writing my own Ajax code when I discovered jQuery. With it you can load the contents of or data from another file with one simple line of code, and you an do a whole lot more than that as well. I highly recommend that you give jQuery (or another Ajax Javascript library) a shot before reinventing the wheel.

---

