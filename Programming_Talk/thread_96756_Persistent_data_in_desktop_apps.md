---
title: "Persistent data in desktop apps"
date: 2005-11-29
forum: Programming Talk
---

### Post by kook44 on 2005-11-29
Hi-
My professional experience centers around client and server side web development, as well as some procedural command-line type stuff.  I am considering taking on a side project to build a desktop app.  My question is: how do you store, retrieve, and manipulate data within a desktop app (as a rule of thumb)?  I would prefer to have some kind of binary format over a straight text file.  The app will contain a lot of relational data.  For the sake of example - lets assume your typical textbook human resources application (employees that have salaries and addresses, that are in departments, etc...).  There would be a GUI for data entry as well as some type of analysis and reporting.  Is there a way to "embed" some type of sql in your application?  Is it as simple as serializing objects and then using collections methods to parse them in java?  what about other languages, like C++?

Desktop world is completely new to me.  Any advice would be greatly appreciated!

THX!

---

### Post by nemik on 2005-11-29
java i know for sure has mysql drivers and wrappers so having a local SQL DB to store the info on is the best if it is relation, IMO.
C++ must have something like it as well, it is too popular not to.

people also keep going on about python, especially in the ubuntu community. it has a great app for making GUI's and seems to be a very nice language though i have yet to get serious with it. but i know for sure it has SQL wrappers as well.

good luck, i also come from a web dvelopment background and it is how i got into programming (php/mysql) but want to give desktop dev a shot when i find some time.

---

### Post by kook44 on 2005-11-29
> java i know for sure has mysql drivers and wrappers so having a local SQL DB to store the info on is the best if it is relation, IMO.
C++ must have something like it as well, it is too popular not to.

I should've been more specific.  I want to make the app as lightweight and autonomous as possible.  The data used in the app will only be used on that machine, no data needs to be shared, so I wouldn't want to have to install a database server on each desktop.  I was just saying that the way the data will be reported on an queried, SQL would be a good language to use - if you were to be able to somehow "embed" a database within the runtime memory of your app.

---

### Post by Yolteotl on 2005-11-29
Maybe you should look into [SQLite]("http://www.sqlite.org/"). It's a small cross-platform library for C/C++ that implements a embeded SQL database manager. It also has bindings for other languages.

---

### Post by kook44 on 2005-11-29
[QUOTE=Yolteotl]Maybe you should look into [SQLite]("http://www.sqlite.org/"). It's a small cross-platform library for C/C++ that implements a embeded SQL database manager. It also has bindings for other languages.[/QUOTE]

hmmm....
This looks like a good start.  Thanks!  Only C++ libraries, tho.

I'm still wondering, though - what is the proven, typical way to do this?

---

