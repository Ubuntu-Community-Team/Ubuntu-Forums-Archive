---
title: "Simple mySQL Query works in Windows, not Ubuntu"
date: 2010-08-14
forum: Programming Talk
---

### Post by ohmysql on 2010-08-14
When I'm using mySQL Query Browser in Windows and Ubuntu, I entered the following text:

select 2+2;
select 1+1;

In Linux, here's what happens:

If I execute this query, I get error 1064, asking me to check my syntax around "select 1+1;

This query doesn't run because the parser isn't stopping at the first semi-colon.

In Windows here's what happens.

If I put the text cursor over "select 2+2;", that line will be light, and the second line will be shaded dark gray. The shading happens at the semi-colon. If I delete the semi-colon, both lines will be normal, nothing will be shaded. So by adding the first semi-colon after select 2+2, the parser shades the second line (select 1+1).

If I execute the query, I get the answer is 4. If I move the text cursor to the second line, I get the answer is 2.

Is there something wrong in Ubuntu?

---

### Post by r-senior on 2010-08-14
Are you using a query tab in both cases, or a script tab on windows and a query tab on Ubuntu?

You can tell by the black & white icon on the left of the tab. A query tab is a lightning flash, a script tab is a multiple-line document.

---

### Post by ohmysql on 2010-08-14
> **r-senior said:**
> Are you using a query tab in both cases, or a script tab on windows and a query tab on Ubuntu?

You can tell by the black & white icon on the left of the tab. A query tab is a lightning flash, a script tab is a multiple-line document.

Thanks for the clarifying question.

I'm using a query tab in both cases. The script runs fine in both Windows and Ubuntu.

I hope that helps.

---

### Post by r-senior on 2010-08-14
I don't think there's anything to worry about with MySQL on Ubuntu. The MySQL Query Browser may be a different code base, or perhaps a different version. Either way, the query browser query tab is really designed for running one SQL statement at a time. It may be different on Windows, but that doesn't mean either is wrong because both do the job correctly for single queries.

Certainly I've used MySQL and the GUI tools extensively on Ubuntu and not had any problems - regularly moving MySQL-based web applications freely between Ubuntu and Windows.

---

### Post by ohmysql on 2010-08-14
Thanks for the reply.

Here are a couple of questions I have for you or anyone else.

1.) Is the same thing happening to you in both Windows and Ubuntu?
2.) I understand that the query window is meant for executing one query at a time. You'll note that in my example above, I only execute one query at a time in Windows. That said, I have to say I find it annoying that I can only *write* one query at a time in the entire window. In Windows, I'm able to have more than one query in a window, even if I run just one at a time.

So I'm wondering if there's a different delimiter in Ubuntu than is Windows (maybe it's not a semi-colon, maybe it's some other character)? I'd like to figure out how to have 1+1; and 2+2; in the same window without both trying to execute. Any ideas?

Maybe it doesn't matter to you, but I find it inconvenient.

---

### Post by r-senior on 2010-08-14
I get the same behaviour as you do on Ubuntu. I don't have any Windows machines to check. 

Flicking through some MySQL forum posts, it sounds like the capability to select from multiple queries in the query tab, as opposed to the script tab, was a feature added following requests from users. I guess it's possible that it's not in the Linux version, for whatever reason.

Did you check your version numbers on Ubuntu and Windows? I suspect Windows is a higher revision.

In searching I also note that Query Browser and Administrator have reached end-of-line and bug fixes have not been accepted since December 2009.

[http://dev.mysql.com/support/eol-notice.html]("http://dev.mysql.com/support/eol-notice.html")

*Scroll down about half-way.*

MySQL Workbench being the replacement. Perhaps you'd find the functionality you need in the Linux version there? I wonder if MySQL workbench is going to be in Maverick? I'll check when I get time.

[http://dev.mysql.com/downloads/workbench/5.2.html#downloads]("http://dev.mysql.com/downloads/workbench/5.2.html#downloads")

No time this evening but I might try it myself tomorrow. :D

---

### Post by ohmysql on 2010-08-14
> **r-senior said:**
> I get the same behaviour as you do on Ubuntu. I don't have any Windows machines to check.

Thanks for letting me know. Glad it's not just me!

> Flicking through some MySQL forum posts, it sounds like the capability to select from multiple queries in the query tab, as opposed to the script tab, was a feature added following requests from users. I guess it's possible that it's not in the Linux version, for whatever reason.Ahh! That's interesting!

> Did you check your version numbers on Ubuntu and Windows? I suspect Windows is a higher revision. I didn't. I'm not at my Windows machine but I'll look into it. I know that Linux automatically updates stuff. I'm not sure what version I installed on Windows. On Ubuntu I've got 1.2.12.

> In searching I also note that Query Browser and Administrator have reached end-of-line and bug fixes have not been accepted since December 2009.

[http://dev.mysql.com/support/eol-notice.html](http://dev.mysql.com/support/eol-notice.html)

*Scroll down about half-way.*

MySQL Workbench being the replacement. Perhaps you'd find the functionality you need in the Linux version there? I wonder if MySQL workbench is going to be in Maverick? I'll check when I get time.

[http://dev.mysql.com/downloads/workbench/5.2.html#downloads](http://dev.mysql.com/downloads/workbench/5.2.html#downloads)

No time this evening but I might try it myself tomorrow. :D

Sad that they're not doing any more development. I just downloaded Workbench - yes it does execute only one query at a time! Sweet!

I didn't understand something: what do you mean "be in Maverick"?

Thanks so much for the insights!

ohmysql!

---

### Post by r-senior on 2010-08-15
Good! :D Sounds like workbench is the way to go. Graphical database design too, by the sound of it?

> **ohmysql said:**
> I know that Linux automatically updates stuff.
It does, but bear in mind the updates are coming from the Ubuntu repositories, not necessarily from the very latest versions of things. This is a good thing IMO, because it provides stability, but versions can lag behind. Netbeans for example is 6.8 in the repositories but 6.9 has released.

> **ohmysql said:**
> I didn't understand something: what do you mean "be in Maverick"?

Thanks so much for the insights!

ohmysql!
Maverick Meerkat is the codename for Ubuntu 10.10, which will be released 10/10, i.e. October 2010. Ubuntu release cycles are 6 months, versioned by release date, so Lucid Lynx is 10.04, released April 2010, previous version was Jaunty Jackalope 9.10 released October 2009 and so on.

So I was wondering what MySQL GUI tools would be packaged for the 10.10 release. I haven't found out yet. I'll ask the question on the Maverick forum.

---

### Post by ohmysql on 2010-08-17
I have some news: I looked on my Windows version of mySQL and... it's version 1.2.17. Aha!! On Linux I had 1.2.12!

But... Linux only goes up to 1.2.12... sad! So, that answers that question.

I have a question for you:

Graphical interface - what? Workbench does seem good, but I don't know what you're talking about.

I imagine there's some process for notifying the Ubuntu repository people of updates?

And thanks, I didn't know the next of the next version of Ubuntu. That's exciting that it's coming out soon!

I hope they include workbench on 10.10 - I'd be curious what you find out.

Thanks for all the help. I'm not that much of a n00b with mySQL but Linux I sure am.

OH-MY-SQL!!

---

### Post by r-senior on 2010-08-17
> Graphical interface - what? Workbench does seem good, but I don't know what you're talking about.
It's OK, neither do I. ;) ... I read something about SQL workbench having a graphical database design tool. You know the sort of thing - draw tables, add columns, drag foreign key relationships and so on.

But I still haven't got round to installing it, so I don't know. Did you find one?

> I hope they include workbench on 10.10 - I'd be curious what you find out.
Here's the thread. No answer as yet.

[http://ubuntuforums.org/showthread.php?t=1553452]("http://ubuntuforums.org/showthread.php?t=1553452")

---

### Post by ohmysql on 2010-08-17
Hmm, not yet!

---

### Post by r-senior on 2010-08-18
Installed it. Nice. \\:D/

I don't understand how you've not found the data modelling part. It's right in the middle of the home screen between the query and admin tools (see attached).

---

### Post by ohmysql on 2010-08-18
Looks awesome. I looked into workbench for about 2 seconds and totally missed all that stuff. I'm planning a more comprehensive look at it this weekend. Sounds exciting!

---

