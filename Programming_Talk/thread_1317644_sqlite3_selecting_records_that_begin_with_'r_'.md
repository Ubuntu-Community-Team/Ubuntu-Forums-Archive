---
title: "sqlite3 selecting records that begin with 'r_'"
date: 2009-11-06
forum: Programming Talk
---

### Post by pozitron969 on 2009-11-06
Hello all,

I am trying to figure out how to select a set of records that I have in a database.  I would like to get the records that begin with 'r_' (sans quotes) in the filename field.

I am using sqlite3 v3.6.16.

Table Name:
files

Schema:
FileID (autoincrement primary key integer)
FullPath (text)
FileName (text)

Sample Data:
502|/media/store/videos/r_5.n_Rome_Season_1.s_1.d_2009-11-06.c_Rome,History,Bloody.a_KevinMcKidd,RayStevenson,PollyWalker.i_nnn.e_.avi|r_5.n_Rome_Season_1.s_1.d_2009-11-06.c_Rome,History,Bloody.a_KevinMcKidd,RayStevenson,PollyWalker.i_nnn.e_avi.avi
503|/media/store/videos/r_5.n_Rome_Season_1.s_2.d_2009-11-06.c_Rome,History,Bloody.a_KevinMcKidd,RayStevenson,PollyWalker.i_nnn.e_.avi|r_5.n_Rome_Season_1.s_2.d_2009-11-06.c_Rome,History,Bloody.a_KevinMcKidd,RayStevenson,PollyWalker.i_nnn.e_avi.avi
504|/media/store/videos/Rome_Season_2x02.avi|Rome_Season_2x02.avi
505|/media/store/videos/Rome_Season_2x03.avi|Rome_Season_2x03.avi


I have tried this query:

[FONT="System"]SELECT * FROM files WHERE filename like 'r_%'[/FONT]

and I still get records #504 and #505 as part of the result.


Any thoughts?  Thank you.

-Andy

---

### Post by Ann.A on 2009-11-06
From the documentation, [http://www.sqlite.org/lang_expr.html](http://www.sqlite.org/lang_expr.html), it says "he LIKE operator does a pattern matching comparison. The operand to the right contains the pattern, the left hand operand contains the string to match against the pattern. A percent symbol ("%") in the pattern matches any sequence of zero or more characters in the string. An underscore ("_") in the pattern matches any single character in the string."

I would suggest experimenting with the GLOB or REGEXP options to see if they will allow matching an underscore without escaping it.

---

