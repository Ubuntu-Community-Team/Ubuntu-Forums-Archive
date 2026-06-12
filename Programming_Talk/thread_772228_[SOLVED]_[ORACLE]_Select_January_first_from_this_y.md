---
title: "[SOLVED] [ORACLE] Select January first from this year"
date: 2008-04-28
forum: Programming Talk
---

### Post by Asham on 2008-04-28
How can I do a select from an Oracle database where rows are between now and January first (current year). The table has a column "inserted" which is of the type "DATE".

In MySQL it'd be easy but Oracle is, umm, more of a challenge. :D 
Shouldn't be too difficult for those of you who know Oracle. Unfortunately for me, I have not used Oracle before.

Adam.

---

### Post by JamesUser on 2008-04-28
This should do.

select * from t_table
where column_inserted between '01-JAN-2008' and sysdate;

If you don't want to hard code start date of the **current **year, you can do

select * from t_table
where column_inserted between trunc(sysdate,'year') and sysdate;

---

### Post by Asham on 2008-04-28
For future reference if somebody wants to do the same thing, this is what I did:
```
SELECT ... FROM ... WHERE ... AND TRUNC(inserted) BETWEEN TO_DATE('01-jan-' || TO_CHAR(SYSDATE, 'yyyy'), 'dd-MON-yyyy') AND SYSDATE 
```

Thank you James. :)

---

### Post by JamesUser on 2008-04-28
Hi Asham,

You need not concatenate '01-jan-' and current year of sysdate. trunc(sysdate,'year') does just that.

Try select trunc(sysdate, 'year') from dual; if you want to see what it does. Look at the 10g database reference guide to see what functions are available.

---

### Post by Asham on 2008-04-28
Aha. I didn't know that you see. :)

What I've got is an IP, name of some database, a username+password and portnumber. So when I logon through JDBC, all I have only access to a few views.

---

### Post by JamesUser on 2008-04-28
Well... I don't really understand your first comment. Sorry... :-)

'Dual' is not a view. Its a special table with only one row and one column. Please google for more accurate info.

You don't need special privileges to use trunc(sysdate, 'year') in your query.

---

### Post by Asham on 2008-04-29
What I meant was that I didn't know I could get the reference material for free. I thought you had to pay up to get material.
And since this task is a one-timer, it wouldn't be worth it.  Client will be moving away from Oracle. 

You have been most helpful. Thank you!

---

### Post by JamesUser on 2008-04-29
Glad to be of help... Gotcha... You need not pay for documentation. Various guides are available here.. [http://www.lc.leidenuniv.nl/awcourse/oracle/nav/docindex.htm](http://www.lc.leidenuniv.nl/awcourse/oracle/nav/docindex.htm)

---

