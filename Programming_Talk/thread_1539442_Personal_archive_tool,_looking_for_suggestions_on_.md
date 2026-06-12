---
title: "Personal archive tool, looking for suggestions on improving the code"
date: 2010-07-26
forum: Programming Talk
---

### Post by mo.reina on 2010-07-26
i've written a tool in python where you enter a title, content, then tags, and the entry is then saved in a pickle file.  it was mainly designed for copy-paste functionality (you spot a piece of code you like on the net, copy it, and paste it into the program), not really for handwritten content, though it does that with no problem.

i mainly did it because i'm always scanning through my pdf files, books, or the net for some coding example of solution that i'd already seen before, and it just seemed logical to have something where you could just put the content in, give it a title and tags, and just look it up whenever you needed to.

i realize there are sites online that handle this ex. [http://snippets.dzone.com]("http://snippets.dzone.com"), but i'm not always online when i code.  i also admit that i didn't really look to see if anyone had written a desktop app, the project seemed like a fun thing to do so here i am.

it wasn't designed with millions of entries in mind, so i just use a pickle file to serialize the data instead of one of the database APIs.  the query is also very basic, only title and tags and no ranking based on the query.

there is an issue that i can't figure out, when you are at the list of entries there's a try, except clause where it tries to catch a valid index (integer).  if you enter an inavlid integer, it will ask you to enter a valid one, but it doesn't seem to be able to assign it to the variable.  if you enter a valid integer straightaway, there are no problems and the entry will display.


anyway let me know what you guys think.  this is coded for python3.

---

