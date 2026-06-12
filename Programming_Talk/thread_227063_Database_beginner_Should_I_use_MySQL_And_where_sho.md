---
title: "Database beginner: Should I use MySQL? And where should I learn?)"
date: 2006-08-01
forum: Programming Talk
---

### Post by nmsmith on 2006-08-01
I am a high school maths teacher. I currently keep track of a lot of information at work using a whole bunch of spreadsheets. Originally these were made in Microsoft Excel, but I now use them largely (very slowly) in OpenOffice. I have often wondered whether a database would be a better system than the numerous speadsheets I use for keeping track of things like attendance, homework marks, test results, seating plans, detentions, parents evenings, lateness, letters from home, timetables, telephone conversation records and occasionally producing some standard forms.

My current levels of awareness tell me that MySQL is the most featured and most universal database application, and that I should try to implement something using it. The problem is: is there somewhere I can be pointed to install and learn to use it? Or can anyone recommend a better database application? Or should I be warned off this and recommended to stick to spreadsheets?

---

### Post by Grey on 2006-08-01
Well...  It depends.

A full fledged database offers you a lot more flexibility than a spreadsheet, in that you can write an application around it, to do all sorts of cool stuff, like sorting it however you like, or formatting it to fit your needs.  However, this involves a lot of work, and the end result is usually dependent on how much time you spend on it.

A spreadsheet is for quick and dirty tabulation of a simple amount of data.  From what I gather, this isn't really what you have, and a more robust solution is required.

However, I can't help but think that if you spent all that time writing the perfect front-end to your database, that you would have been better off just dealing with the old spreadsheet.  As a result, I would have to give my personal feeling that a database such as mySQL is simply overkill.  The generic frontends to MySQL feel fairly clunky to me next to a spreadsheet as well (I personally really like PHPMyAdmin, as it's accessible anywhere, but I have a friend who likes MySQLCC).

I might suggest looking into OpenOffice's Base, which might be more of what you are looking for:
[http://www.openoffice.org/product/base.html](http://www.openoffice.org/product/base.html)

It's easy to use and install, and would be quicker and faster than a spreadsheet for simple data.  And it's easy enough to convert to something more exotic should you ever feel the need to get really fancy.

---

### Post by nmsmith on 2006-08-01
Thanks Grey. I see your point, but on my school laptop, with only 192Mb of memory, OpenOffice runs very slowly, which I should have mentioned earlier. I had wondered whether perhaps MySQL would do better. Also I have now been given a windows PC in my classroom, so cross-platform functionality would be a bonus, although it is not a necessity. The other alternative I hadn't mused would be to remove linux from my laptop, reinstate windows, and return to the many-Excel-files solution, which although inelegant did work more fluidly and more quickly than Calc.

---

### Post by LordHunter317 on 2006-08-01
> **nmsmith]My current levels of awareness tell me that MySQL is the most featured and most universal database application,[/quote]It's neither.  It's actually pretty much the least featured, at least among "general purpose" RDBMS.

> Or can anyone recommend a better database application?PostgreSQL.  SQL Server.  Oracle.  DB2.  Anything ! MySQL pretty much.  Access might even fit the bill really well.

> Or should I be warned off this and recommended to stick to spreadsheets?Your data may be better for a spreadsheet, it really depends on how you work with it.

[QUOTE=Grey said:**
> A spreadsheet is for quick and dirty tabulation of a simple amount of data.No, it's for way more than that.  MS doesn't spend all of that time on Excel for "quick and dirty" tasking.

---

