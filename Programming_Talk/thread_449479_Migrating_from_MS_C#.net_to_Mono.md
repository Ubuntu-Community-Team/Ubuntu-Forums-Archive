---
title: "Migrating from MS C#.net to Mono"
date: 2007-05-20
forum: Programming Talk
---

### Post by SoggyCornflake on 2007-05-20
Has anybody written a general tutorial on how to move an application from Microsoft's .net to mono?

I guess my main concern is how easily one could replace winform calls to gtk calls.  Is it even possible?

I know that mono has made some strides, but how big of a gap is there between mono and .net?

---

### Post by HolyJoe on 2007-05-20
I'm very interest at this problem the same.  And one the other hand, I had another problem 
> How to debug Mono C# code?

---

### Post by luisromangz on 2007-05-20
I have used Mono for years now, and from my experience, you should do new development using Gtk#, but if your existing applications already use WindowsForms, you may try to run them without changing the toolkit. In the latests releases of Mono, WindowsForms is almost complete but for the most obscure parts.

And for development, my advice is to use monodevelop from svn, not the standard 0.13 version, as it has much improvements. For gtk# development, don't use the stetic gui designer bundled with it, because is buggy, but use Glade.

I hope you'll manage to develop very nice Mono apps!

---

### Post by SoggyCornflake on 2007-05-20
> **luisromangz said:**
> I
And for development, my advice is to use monodevelop from svn, not the standard 0.13 version, as it has much improvements. For gtk# development, don't use the stetic gui designer bundled with it, because is buggy, but use Glade.

I hope you'll manage to develop very nice Mono apps!

Thanks for the advice and encouragement.  I have the standard version, 0.13, and yes - buggy is a good word for it.

---

### Post by lukew on 2007-05-31
> **SoggyCornflake said:**
> Thanks for the advice and encouragement.  I have the standard version, 0.13, and yes - buggy is a good word for it.

Not to change the conversation but i brought a book on mono development from oreily (blue cover).The book is very good and absolutely ideal for Java programmers and other existing programmers etc. The book has  a couple very good chapters / very useful examples of GTK# development (without the drag and drop). 

I find the drag and drop layout poor in monodevelop; the space is not well used and the layout is very unintuitive. however i do like the actual development environment and code completion / inline api browsing.

Luke

---

