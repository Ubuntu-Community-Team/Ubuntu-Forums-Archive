---
title: "Python and PYGTK"
date: 2008-07-05
forum: Programming Talk
---

### Post by mrblue182 on 2008-07-05
Do you use a program like PyQT or wxPython for creating GUI's, or do you design by hand?

---

### Post by Stshow on 2008-07-05
I like draw GUI by hand
I think it feels very good

---

### Post by ad_267 on 2008-07-05
I haven't done much gui programming but I've used pygtk and gtk in combination with glade and found that to work really well and make building a gui simple and fast.

---

### Post by kaivalagi on 2008-07-08
I have learnt python fairly recently and am now starting out with glade and pygtk. If you fancy taking this route then go and find yourself a download of "glade2py". It will generate skeleton code for all the events you define in your glade file.

So I think the steps would be:

[LIST=1]
[*]Create your GUI in Glade3, setting up the required event signals
[*]Save you glade file
[*]Use glade2py to generate a py file
[*]Start adding your handling code in the py file to create a fully fledged app
[/LIST]

I am not sure whether there are any better GUI to code tools out there for this, but this will definitely give you a good headstart.

Anyone know of any good alternatives to glade2py? Ideally something that is clever enough to enable the editing of a glade file, and resyncing it with a previous python script, without losing any handling code that may have been added by me...

---

### Post by days_of_ruin on 2008-07-08
> **kaivalagi said:**
> I have learnt python fairly recently and am now starting out with glade and pygtk. If you fancy taking this route then go and find yourself a download of "glade2py". It will generate skeleton code for all the events you define in your glade file.

So I think the steps would be:

[LIST=1]
[*]Create your GUI in Glade3, setting up the required event signals
[*]Save you glade file
[*]Use glade2py to generate a py file
[*]Start adding your handling code in the py file to create a fully fledged app
[/LIST]

I am not sure whether there are any better GUI to code tools out there for this, but this will definitely give you a good headstart.

Anyone know of any good alternatives to glade2py? Ideally something that is clever enough to enable the editing of a glade file, and resyncing it with a previous python script, without losing any handling code that may have been added by me...

Never heard of doing that way.Read this [tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---

### Post by kaivalagi on 2008-07-08
> **days_of_ruin said:**
> Never heard of doing that way.Read this [tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

Cool, I'll have to look at gtkbuilder. Quite nifty how you create a method with the right name to match an event, and it can associate the UI to it...learn something new everyday :)

No automatic code generation based on the glade xml though right? Maybe someone is writing something that will do the same for gtkbuilder??? You might want to check out the glade2py stuff anyway, it might save quite a bit of time...it worked out of the box as it were for me, I just took a glade file from a UI I like, edited it, and generated the python to use with it...

I've attached the tar.gz I downloaded for glade2py in case you want to give it a bash. Also, check out this article: [http://sane-pygtk.sourceforge.net/glade2py.html](http://sane-pygtk.sourceforge.net/glade2py.html)

What we need is an updated pydev plugin for eclipse that does all this for us!

Cheers

---

### Post by mrblue182 on 2008-07-09
So, from what I gather, most casual programmers use glade to create GUI's. Thanks, and that tutorial is really nice. =]

---

### Post by mssever on 2008-07-09
> **kaivalagi said:**
> No automatic code generation based on the glade xml though right? Maybe someone is writing something that will do the same for gtkbuilder?
You don't really need automatic code generation if you use Glade 3 and gtk.Builder, because there's very little code to generate.

---

### Post by kaivalagi on 2008-07-09
> **mssever said:**
> You don't really need automatic code generation if you use Glade 3 and gtk.Builder, because there's very little code to generate.

I'll have a play, thanks

---

