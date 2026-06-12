---
title: "Simple Database"
date: 2007-03-19
forum: Programming Talk
---

### Post by renzokuken on 2007-03-19
Hi there,

Firstly, i should just mention that i know nothing about programming. I have tried to learn a couple of languages but usually dont get any further than the "Hello World" bit without getting bored. Although i'm slowly picking up Matlab during my PhD (i use it for datat analysis)

Well, the thing is, i now actually have a reason to learn some programming. My supervisor wants me to build a database for all the samples we have made, and the ability to add new samples to it as we make them.

Basically, each sample has a number (in ascending order.....we are up to 3000 now and we currently record the samples on A4, you wouldnt beleive the lever arch files full of paper we have) and about 4 standard variables for each sample (deposition time, constituent elements, temperature, film thickness etc).

He wants me to try and develop a database (he mentioned MS Access but i would rather use something else) with a frontend so we can enter new samples into it as we make them, and call up old samples simply by searching for the sample number or by a constituent element etc.

As a programming newbie, but one who is actually looking forward to learning and trying to do this myself, can anyone give me some basic info on what options are available to me. It has to be able to run on XP. I guess Visual Basic would be an obvious answer.

Thanks

---

### Post by cunawarit on 2007-03-19
Doing a PhD at Southampton? So did I :) What department? I was over at IAM in Computer Science! Small world&#8230;

Anyway, you have a few choices. It really depends how simple you want to go.

If you want to go the ubber basic route, I would suggest avoiding programming altogether. Start an Excel spreadsheet put it in a shared drive and that way you and your supervisor can access it. If you want to be a little cleverer you could version control it with SVN. I don't know if you really need a DB, or just a way of collecting data in a shared area, this is why I suggest a spreadsheet.

Alternatively, you could consider creating a little website. If you are going to host it on your work station, if your machine is anything like mine was over at Computer Science you should be able to see it all over campus. For a database you can either use MySQL or SQL Server, and for language either PHP or ASP.NET, the University should have licenses for Visual Studio, and SQL Server. 

Either way should be simple, PHP might be easier to get the grips with than ASP.NET.

Good luck :) With either PHP or ASP.NET I am sure there will be plenty of people here to help you along.

---

### Post by Mirrorball on 2007-03-19
You don't need to know a programming language to use a database. SQL would be necessary if you really want to learn databases, but you can do what you want with Access. You might try MySQL too, it has a frontend, but I don't know how easy and powerful it is.

---

### Post by cunawarit on 2007-03-19
A good front end for MySQL under XP is Toad. It is pretty nice...

---

### Post by renzokuken on 2007-03-19
thanks for your replies......im over in the Chemistry department cunawarit.

basically, the database needs to be added to and used by probably about 10 people, adding their various samples to it. our research groups has a Fedora powered file server/domain controller that we all log onto.

i could use MySQL on that as the database and create a local PHP webpage that people logged onto the domain can use to update the database. would that work? theres a guy in the group who knows a bit of PHP too.

---

### Post by cunawarit on 2007-03-19
> i could use MySQL on that as the database and create a local PHP webpage that people logged onto the domain can use to update the database. would that work?

I personally don’t know how authentication works outside the Windows/ASP.NET realm. But I am sure there’s a simple way to get your colleagues to authenticate. 

The database part sure will work!

> Theres a guy in the group who knows a bit of PHP too.

Great! :) It should be a simple site, great for learning the basics of Web development.

---

### Post by Mirrorball on 2007-03-19
You could install phpMyAdmin then. Here are the demos, see if it suits you:
[http://www.phpmyadmin.net/home_page/demos.php](http://www.phpmyadmin.net/home_page/demos.php)

---

### Post by Frosty Cold Drink on 2007-03-19
> **renzokuken said:**
> thanks for your replies......im over in the Chemistry department cunawarit.

basically, the database needs to be added to and used by probably about 10 people, adding their various samples to it. our research groups has a Fedora powered file server/domain controller that we all log onto.

i could use MySQL on that as the database and create a local PHP webpage that people logged onto the domain can use to update the database. would that work? theres a guy in the group who knows a bit of PHP too.

This is a good way to go. Authentication is a huge topic. There are various tie-ins you can do to do single sign on with existing domains.

What is nice about using a full RDBMS like MySQL is that you can use a PHP page to manage if you like, use other applications like phpMyAdmin, or connect to the database via ODBC from various spread sheet applications.

---

### Post by renzokuken on 2007-03-20
thanks for all your input people. 

i had a play on phpmyadmin last night and also found this tutorial [http://www.freewebmasterhelp.com/tutorials/phpmysql/1](http://www.freewebmasterhelp.com/tutorials/phpmysql/1) which explains how to do almost exactly what i want.

thanks

my definate plan is to use our central domain/fileserver with PHP and MySQL to access a webpage stored locally on the server (that only people logged into the server can access)

---

### Post by timmie on 2007-03-26
I did do anything of that kind so far.
But there are many scientists around the world.

Maybe there's already a solution?

Try to find something on freshmeat.net or sourceforge.net

I mean there's websolutions for web content publishing or shared bibtex management.
Why not for sample data management?

Please keep us updated.

---

### Post by timmie on 2007-03-26
Hi,
I found

BIKA - A laboratory information management system (LIMS) built on top of Zope and Plone, and coded in Python

via

[https://help.ubuntu.com/community/UbuntuScience](https://help.ubuntu.com/community/UbuntuScience)

Built in cutting edge open source technologies
A combined LIMS, workflow and web content management system
bika (bi:ka Zulu trad) report, from clan to clan, bring news of weddings, births, festivals and funerals 
[http://bika.sourceforge.net/](http://bika.sourceforge.net/)

Maybe you find something similar?

---

### Post by jakev383 on 2007-03-26
Take a peek at this:
[http://anyinventory.sourceforge.net/](http://anyinventory.sourceforge.net/)
I've used it in the past for everything from keeping an inventory of a warehouse to keeping track of address space on a network. Very flexible.

---

