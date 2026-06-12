---
title: "[SOLVED] SQL: Search all Fields"
date: 2008-09-29
forum: Programming Talk
---

### Post by aaaantoine on 2008-09-29
I would like to find all occurrences of 'foo' in every record of every table of my SQL database.  How do I go about doing this?

Usually I search the web for questions like this, but right now I can't think of a clear way to phrase a search query for this.

---

### Post by Mindzai on 2008-09-29
Honestly (and i'm not trying to be an *** here) I would ask myself why I needed to do this as it is very inneficient.

Anyway this should do what you want:

[http://blogs.thesitedoctor.co.uk/tim/2007/11/02/How+To+Search+Every+Table+And+Field+In+A+SQL+Server+Database.aspx](http://blogs.thesitedoctor.co.uk/tim/2007/11/02/How+To+Search+Every+Table+And+Field+In+A+SQL+Server+Database.aspx)

:)

---

### Post by aaaantoine on 2008-09-29
> **Mindzai said:**
> Honestly (and i'm not trying to be an *** here) I would ask myself why I needed to do this as it is very inneficient.

Anyway this should do what you want:

[http://blogs.thesitedoctor.co.uk/tim/2007/11/02/How+To+Search+Every+Table+And+Field+In+A+SQL+Server+Database.aspx](http://blogs.thesitedoctor.co.uk/tim/2007/11/02/How+To+Search+Every+Table+And+Field+In+A+SQL+Server+Database.aspx)

:)

The alternative is to type in all the column names manually and apply the same where clause to each of them.  Is that more efficient?

Thanks for the link.

---

### Post by Mindzai on 2008-09-29
I mean I would be asking myself if I was using the most efficient method of designing my program, such that searching every field of every table is not necessary at all. If the answer to that is 'yes i am' then fine, but this should be a last resort for exeptional circumstances.

---

### Post by aaaantoine on 2008-09-29
> **Mindzai said:**
> I mean I would be asking myself if I was using the most efficient method of designing my program, such that searching every field of every table is not necessary at all. If the answer to that is 'yes i am' then fine, but this should be a last resort for exeptional circumstances.

Well, it's not meant to be part of the software.  I'm running a special query that I may need to run occasionally in the future.

For its purpose, this will prove to be very useful.

---

### Post by drubin on 2008-09-29
create a [full text index]("http://dev.mysql.com/doc/refman/5.0/en/fulltext-search.html").

---

