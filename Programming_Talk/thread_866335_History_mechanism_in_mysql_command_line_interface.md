---
title: "History mechanism in mysql command line interface?"
date: 2008-07-21
forum: Programming Talk
---

### Post by lenticular on 2008-07-21
I've been working to move some database applications from MS-Access to MySQL so that I won't have to run an XP VM.  One thing that is driving me nuts is the command interpreter in mysql.  Is there anything like bash or ksh that will let me use vi editing commands to search and edit commands I've given in the past?

I've found the .mysql_history file, so I know that all of this is kept, but it is a real drag having to up-arrow through my history to find the command I want to repeat or edit.

Bonus question: I find myself reflexively using ctrl-c to interrupt a mysql command in progress.  That works great in bash, but just terminates the mysql session and drops me back into the shell.  Where can I define this kind of thing for mysql?

Thanks,
  John

---

### Post by LoneWolfJack on 2008-07-21
AFAIK there are no such things. the mysql shell is just a convenience tool intended for quick testing and querying. changing its behavior would mean changing a mysql core file. also, think of maintaining the mod...

as for terminating a mysql command, I don't think that is possible. yet I'm no mysql god so I could be wrong. but just think of a delete command on a table with many rows... you'd end up with only half of the rows deleted and with no control over which ones are going to be deleted first.

for rolling back transactions, there are the more sophisticated mysql table types like innodb.

---

### Post by tinny on 2008-07-21
Can you connect to your DB from a desktop machine?

If so why don't you use MySQL Query Browser?

[http://www.mysql.com/products/tools/query-browser/](http://www.mysql.com/products/tools/query-browser/)

Part of the GUI tools bundle.
[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

Ive used it alot and its solid! It will make your life sooo much easier.

---

### Post by stylishpants on 2008-07-22
The mysql client included with ubuntu is compiled with the readline library, so you have full access to readline within the mysql shell.

Use Ctrl-r, just like in bash, to do a reverse history keyword search.


The built-in readline support also means that you can turn on vi editing mode for the mysql shell.  To enable vim mode just to try it out, enter the mysql shell and hit Ctrl-Meta-j.

To enable vi mode permanently, create or edit your ~/.inputrc file, and add these lines:
```

set keymap vi
set editing-mode vi

```
Note that this will also make vi mode the default for all new bash shells.


Still, I'm not sure that enabling vi mode will do you any good.  It sounds like you're looking for something like the 'fc' command for history editing, and I don't think readline provides that.  Ctrl-r seems to be as powerful as it gets.  A little web searching might turn up something though.

"man readline"  for more information.


As for your bonus question, please read this excerpt from the the mysql man page:

>        As of MySQL 5.0.25, typing Control-C causes mysql to attempt to kill the current statement. If this cannot be done, or Control-C is typed again before the
       statement is killed, mysql exits. Previously, Control-C caused mysql to exit in all cases.


As far as I know, there is no way to interrupt a mysql command before version 5.0.25.


BTW my Hardy system uses the following version of mysql-client from the repos:  
5.0.51a-3ubuntu5.1

---

### Post by ThePerl on 2010-01-11
Yes, John Lenticular.  Of course the equivalent of set -o vi is always with you.  If you can just find it!

I recently got back into MySQL after a couple of years away, and I had a hard time remembering how to do it.  And of course, nothing practical can be found on MySQL's giant mound of documentation pages.

And Google didn't help either, except that I found this thread to really get me ticked off enough to remember.

Enter the closest thing to nothing that you can imagine at the mysql command line prompt.  Sort of like the obelisque in 2001, A Space Odyssey.

$mysql
mysql> <esc><ret>

Now <esc> k will carry you on your journey and one more segment of your life can be a giant Unix vi session.

Brad

---

