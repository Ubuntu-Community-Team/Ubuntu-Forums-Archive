---
title: "PHP render tables from files"
date: 2008-09-30
forum: Programming Talk
---

### Post by null-cipher on 2008-09-30
Hi there everybody.
I run a hobby server here at home, and I host a website for a local LAN group.
When they were just starting out, I would take down the scores for each game an put them up on the site for public scrutiny.

This was all well and good aside from the fact that I had to write in each table by hand, into the html.
As you can imagine, this grows to be very tedious, especially as the LANs grew more frequent.

So, my question is "Is it possible to have PHP read tables out of say... an ods spreadsheet or something similar, for this intended purpose?"

The other option I have, is to have the tables entered into my MySQL database and read them out of there.
However I feel it would be difficult to implement this, as the tables are of varying height and width.

Assistance with either method would be greatly appreciated. :)

---

### Post by drubin on 2008-09-30
> **null-cipher said:**
> The other option I have, is to have the tables entered into my MySQL database and read them out of there.
However I feel it would be difficult to implement this, as the tables are of varying height and width.

Assistance with either method would be greatly appreciated. :)

Huge ++ for using mysql over text files for your data storage. It will be harder at first but once you get the hang of it it will save you alot of time in maintaining the site. 

as for tutorials? How much do you already know about php/html/sql? Then I could point you to the appropriate tutorials. 

[http://www.w3schools.com/PHP/DEfaULT.asP](http://www.w3schools.com/PHP/DEfaULT.asP) Here is a basic one to get you started on php.(There are also links to basic html/css). Let me know if you would like more in depth ones.

---

### Post by Reiger on 2008-09-30
Learning some kind of SQL never hurts for this kind of job; perceiving "difficulty based on the fact that 'rows/cols are of varying height/width'" shows you would benefit from some basic Data Base optimisation tutorials. Specifically, look up the 3NF (3rd normal form) and BCNF (Boyce-Codd normal form). (Not that it won't work if you implement it with 'blanks'; just that for performance & maintainability reasons it's like butchering a pig in a mosque.)

But as far as a direct solution goes: it would seem you would like to 'condense' the tables as it were in some kind of language (yet to be specified, more precisely: to be specified by you, yourself). You can do that (easily) by using XSLT stylesheets.

---

### Post by Mindzai on 2008-09-30
As above, mysql is the tool for this. Data and presentation should not depend on each other and should be separate so you should not base your storage decision on how you intend to display the data. Again as above, good database design is important too.

---

### Post by null-cipher on 2008-10-01
> **rubinboy said:**
> 
as for tutorials? How much do you already know about php/html/sql? Then I could point you to the appropriate tutorials. 

I'm fairly familiar with php, as I have written a web page for work that is effectively a front end for mysql. Used for storing information about second hand parts, I would link you but it's on our intranet. :)
The site in question is [http://nooblan.kicks-***.net/games.php](http://nooblan.kicks-***.net/games.php)
I know the design is hideous, but it was written over a weekend many moons ago (the weekend I got dumped :P) and I just have not got around to redoing the presentation.

The tables that I am talking about are in the statistics part.
Once again, there are many, many abominations of practice on this page. It was written back when I was still newb at this stuff, and is in dire need for a rewrite.

Thanks.

---

### Post by null-cipher on 2008-10-02
I apologize, as I think I'm not making clear my intentions... my bad! :)
I'm looking to create an html form for the users to submit these tables of scores.

My current plan, is to have a large set of template forms, that the user can request, and can be dynamically resized. (Such as a GET parameter that will control how many columns are made)
Unless somebody has a better idea?

Thanks.

---

### Post by rnodal on 2008-10-02
> **null-cipher said:**
> I apologize, as I think I'm not making clear my intentions... my bad! :)
I'm looking to create an html form for the users to submit these tables of scores.

My current plan, is to have a large set of template forms, that the user can request, and can be dynamically resized. (Such as a GET parameter that will control how many columns are made)
Unless somebody has a better idea?

Thanks.

Since the user has the option to select how many columns, I would recommend using a form and using POST instead of GET that way you have more control of what the options are. With get the user can get a little to creative and if this is a public site you do not want that. :)

-r

---

