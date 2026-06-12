---
title: "Where to start? Simple book catalogue."
date: 2009-02-12
forum: Programming Talk
---

### Post by Chokkan on 2009-02-12
I work at a junior high school and we have quite a lot of English textbooks, many of which are samples. I thought it would be cool to write a little app that allowed you to enter details about a textbook (title, author, maybe a picture of the cover), and also to enter information about each unit of the book and the topics it covers. I'd like to be able to type in a topic and then the app would tell me which book has activities on that topic.

The software I have seen with similar functionality offer much more than I need. I just need it to bring up results and then I open my drawer, find the books, and plan my lesson. I need this to be a standalone app with no net connection necessary.

If anyone can give some ideas on where to start with this, I'd appreciate it. I'm willing to learn how to do this I just need to know what might be involved. How would the information be stored? A database? A simple text file?

---

### Post by .Maleficus. on 2009-02-12
Database would be the best way to go.  Python + SQLite would be a pretty nice solution.  Do you need a GUI?  If so, PyQt would be my choice.  Its easy and takes on your OS' look-and-feel (if you aren't using Linux at school).

---

### Post by ssam on 2009-02-12
have you looked through all of these [http://www.gnomefiles.org/subcategory.php?sub_cat_id=140](http://www.gnomefiles.org/subcategory.php?sub_cat_id=140) to see if any of them will fit. It might be easier to modify the closest one, than start anew.

you might be able to get by using a GUI database program, there are a few such as Base in openoffice, or [Glom]("http://www.glom.org/").

---

### Post by Neural oD on 2009-02-12
If you are not wanting to got too in depth - you could look at the db that comes with open office

---

### Post by Chokkan on 2009-02-12
Thanks for such a quick reply, even better that I understood it :P. I use Linux on my machine at school but my co-worker has a Mac, and there are of course machines running Windows. How easy is it to make a cross-platform app? Better to keep it simple for now, or have it in mind from the start and avoid porting it later?

Thanks again. Anyone with other thoughts please chime in.

EDIT: Thanks to others who replied as I was typing. I'll mull your ideas over.

---

### Post by Neural oD on 2009-02-12
if you use the open office db - it should work in linux and windows - mac too i think??

---

### Post by .Maleficus. on 2009-02-12
Python is completely cross platform (assuming you have it installed on the Windows and Mac machines).

I wasn't aware that OOorg had a database application - I'm taking a look at some docs right now and it seems really easy and very interesting... Before hand-coding an app, I'd definitely take a look at it, cool find Neural oD!

---

### Post by .Maleficus. on 2009-02-12
Double post... ignore.

---

### Post by Chokkan on 2009-02-12
I had a look at some existing apps but they seem like overkill. I'd rather have something specific. In that case it seems like you guys suggesting Base or Glom are right. I'll see which one suits me best.

---

### Post by ZuLuuuuuu on 2009-02-12
I am writing a similar application for my movie collection. It is simpler than you would expect though (does not have searching functions yet). You can investigate the code if you like:

[http://code.google.com/p/canols-movie-archiver](http://code.google.com/p/canols-movie-archiver)

It is a single source file named *main.vala*. It is cross-platform (I tried on Windows and Linux, didn't tried on Mac yet). I used Vala language along with GTK for user interface, and I can clearly recommend them.

---

### Post by stevescripts on 2009-02-12
If you want to roll-your-own here, I also recommend SQLite, coupled with your programming language of choice.

The actual DB would be cross-platform.

Steve
(who might be convinced to help...)

---

