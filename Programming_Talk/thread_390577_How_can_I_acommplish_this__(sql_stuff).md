---
title: "How can I acommplish this ? (sql stuff)"
date: 2007-03-22
forum: Programming Talk
---

### Post by samir85 on 2007-03-22
Hey guys,

I've this SQL script, which contains 3 insert statements. As you can see in the first statement takes data from table MC$TA_F_VVL_KMP_200604. In the 2nd statement it takes data from table MC$TA_F_VVL_KMP_200605 and in the 3rd one from table MC$TA_F_VVL_KMP_200606. So basically it is doing +1, +2 ...
Is there a way I can automatically calculate that in order to automatize the script? SQL scripts doesn't seem to be capable of calculating variables. If that is so, is there some other scripting/programming language available in which I can accomplish this?

I'd be very grateful for any suggestions,
regards Samir

```

insert into SARIKAYA.MC$TA_H_VVL_KAMP_MORPU_200604(DWH_VERTRAG_ID, QUELLTARIF_ID, ZIELTARIF_ID, CCOS_OFFER_FOLDER_ID, BERICHTSMONAT, DATENMONAT, VERTRAGSBEGINN_M, RAHMENVERTRAG, ERLOES_NETTO_EURO, VW_KENN, KKM_KAMPAGNE_ID, KKM_ANTWORTTYP_ID)
SELECT	/*+parallel (T1,4)*/T2.DWH_VERTRAG_ID,
	T2.QUELLTARIF_ID,
	T2.ZIELTARIF_ID,
	T2.CCOS_OFFER_FOLDER_ID,
	to_number(to_char(T2.VVL_STICHTAG, 'YYYYMM')),
	T1.Monats_ID,
	T1.VERTRAGSBEGINN_M,
	T1.RAHMENVERTRAG,
	sum(T1.ERLOES_NETTO_CENT)/100,
	T2.VW_KENN,
	T2.KKM_KAMPAGNE_ID,
	T2.KKM_ANTWORTTYP_ID
FROM DW_HOUSE_SCHEMA.DWH$TA_F_MORPU_VERTRAG T1, 
	[COLOR="Red"]MC$TA_F_VVL_KMP_200604[/COLOR] T2
where T1.DWH_VERTRAG_ID = T2.DWH_VERTRAG_ID
and T1.MONATS_ID = &1
group by T2.DWH_VERTRAG_ID, T2.QUELLTARIF_ID, T2.ZIELTARIF_ID, T2.CCOS_OFFER_FOLDER_ID, to_number(to_char(T2.VVL_STICHTAG, 'YYYYMM')), T1.Monats_ID, T1.VERTRAGSBEGINN_M, T1.VO_KENN, T1.RAHMENVERTRAG, VW_KENN, KKM_KAMPAGNE_ID, KKM_ANTWORTTYP_ID;

commit;

insert into SARIKAYA.MC$TA_H_VVL_KAMP_MORPU_200605(DWH_VERTRAG_ID, QUELLTARIF_ID, ZIELTARIF_ID, CCOS_OFFER_FOLDER_ID, BERICHTSMONAT, DATENMONAT, VERTRAGSBEGINN_M, RAHMENVERTRAG, ERLOES_NETTO_EURO, VW_KENN, KKM_KAMPAGNE_ID, KKM_ANTWORTTYP_ID)
SELECT	/*+parallel (T1,4)*/T2.DWH_VERTRAG_ID,
	T2.QUELLTARIF_ID,
	T2.ZIELTARIF_ID,
	T2.CCOS_OFFER_FOLDER_ID,
	to_number(to_char(T2.VVL_STICHTAG, 'YYYYMM')),
	T1.Monats_ID,
	T1.VERTRAGSBEGINN_M,
	T1.RAHMENVERTRAG,
	sum(T1.ERLOES_NETTO_CENT)/100,
	T2.VW_KENN,
	T2.KKM_KAMPAGNE_ID,
	T2.KKM_ANTWORTTYP_ID
FROM DW_HOUSE_SCHEMA.DWH$TA_F_MORPU_VERTRAG T1, 
	[COLOR="Red"]MC$TA_F_VVL_KMP_200605 [/COLOR]T2
where T1.DWH_VERTRAG_ID = T2.DWH_VERTRAG_ID
and T1.MONATS_ID = &1
group by T2.DWH_VERTRAG_ID, T2.QUELLTARIF_ID, T2.ZIELTARIF_ID, T2.CCOS_OFFER_FOLDER_ID, to_number(to_char(T2.VVL_STICHTAG, 'YYYYMM')), T1.Monats_ID, T1.VERTRAGSBEGINN_M, T1.VO_KENN, T1.RAHMENVERTRAG, VW_KENN, KKM_KAMPAGNE_ID, KKM_ANTWORTTYP_ID;

commit;

insert into SARIKAYA.MC$TA_H_VVL_KAMP_MORPU_200606(DWH_VERTRAG_ID, QUELLTARIF_ID, ZIELTARIF_ID, CCOS_OFFER_FOLDER_ID, BERICHTSMONAT, DATENMONAT, VERTRAGSBEGINN_M, RAHMENVERTRAG, ERLOES_NETTO_EURO, VW_KENN, KKM_KAMPAGNE_ID, KKM_ANTWORTTYP_ID)
SELECT	/*+parallel (T1,4)*/T2.DWH_VERTRAG_ID,
	T2.QUELLTARIF_ID,
	T2.ZIELTARIF_ID,
	T2.CCOS_OFFER_FOLDER_ID,
	to_number(to_char(T2.VVL_STICHTAG, 'YYYYMM')),
	T1.Monats_ID,
	T1.VERTRAGSBEGINN_M,
	T1.RAHMENVERTRAG,
	sum(T1.ERLOES_NETTO_CENT)/100,
	T2.VW_KENN,
	T2.KKM_KAMPAGNE_ID,
	T2.KKM_ANTWORTTYP_ID
FROM DW_HOUSE_SCHEMA.DWH$TA_F_MORPU_VERTRAG T1, 
	[COLOR="red"]MC$TA_F_VVL_KMP_200606[/COLOR] T2
where T1.DWH_VERTRAG_ID = T2.DWH_VERTRAG_ID
and T1.MONATS_ID = &1
group by T2.DWH_VERTRAG_ID, T2.QUELLTARIF_ID, T2.ZIELTARIF_ID, T2.CCOS_OFFER_FOLDER_ID, to_number(to_char(T2.VVL_STICHTAG, 'YYYYMM')), T1.Monats_ID, T1.VERTRAGSBEGINN_M, T1.VO_KENN, T1.RAHMENVERTRAG, VW_KENN, KKM_KAMPAGNE_ID, KKM_ANTWORTTYP_ID;

commit;

```

---

### Post by ditsch on 2007-03-22
I can't think of a solution you are searching as you want to calculate a table name for your insert, right? 

I think then, your table layout is bit weird. If the only difference in this tables is the timeframe, why don't you throw the data in one table and add the timeframe as additional columns (as key columns, if you want). With the layout you have, you are creating a table every time a new month starts? That sounds odd in my opinion.

If you can't change the table layout and you have a specific set of tables to insert into, you could trigger the lines from one table to the other by creating triggers in each table to the next table in timeline.

---

### Post by lnostdal on 2007-03-22
Using [Common Lisp]("http://nostdal.org/~lars/writings/about-common-lisp-getting-started-under-ubuntu/common-lisp-getting-started.xhtml") I could do something like that this way:

(i've shortened the strings down, but they illustrate the point)
```

cl-user> (defun mkstr (&rest args)
           (with-output-to-string (s)
             (dolist (a args) (princ a s))))
mkstr
cl-user> (loop :for i :from 1 :upto 9
            :collecting (mkstr "SOME SQL-STUFF HERE 20060" i " MORE SQL; "))
            
("SOME SQL-STUFF HERE 200601 MORE SQL; "
 "SOME SQL-STUFF HERE 200602 MORE SQL; "
 "SOME SQL-STUFF HERE 200603 MORE SQL; "
 "SOME SQL-STUFF HERE 200604 MORE SQL; "
 "SOME SQL-STUFF HERE 200605 MORE SQL; "
 "SOME SQL-STUFF HERE 200606 MORE SQL; "
 "SOME SQL-STUFF HERE 200607 MORE SQL; "
 "SOME SQL-STUFF HERE 200608 MORE SQL; "
 "SOME SQL-STUFF HERE 200609 MORE SQL; ")

```

..this should be very simple to do in almost any language.

---

### Post by pmasiar on 2007-03-22
> **lnostdal said:**
> ..this should be very simple to do in almost any language.

In SQL, table name cannot be varable or even an unbound parameter (provided at execute time), because SQL planner needs to know table name to plan query.

IOW what lnodstal suggests is to write a simple program which will generate strings - SQL statements, and runs them against SQL database server. You need to write a small program which will run your query anyway - it may as well generate the query. :-)

---

### Post by samir85 on 2007-03-22
> I can't think of a solution you are searching as you want to calculate a table name for your insert, right?

Yeah that's right I want to calculate the table name and there lies the problem! 

> I think then, your table layout is bit weird. If the only difference in this tables is the timeframe, why don't you throw the data in one table and add the timeframe as additional columns (as key columns, if you want). With the layout you have, you are creating a table every time a new month starts? That sounds odd in my opinion.

If you can't change the table layout and you have a specific set of tables to insert into, you could trigger the lines from one table to the other by creating triggers in each table to the next table in timeline.

Unfortunately, I'm not responsible for the datebase design. I think they created a new table for every month, because the tables contain a lot of data (around 30 Mio data sets per month).

> Quote:
Originally Posted by lnostdal  
..this should be very simple to do in almost any language. 

In SQL, table name cannot be varable or even an unbound parameter (provided at execute time), because SQL planner needs to know table name to plan query.

IOW what lnodstal suggests is to write a simple program which will generate strings - SQL statements, and runs them against SQL database server. You need to write a small program which will run your query anyway - it may as well generate the query. 

Ok, I got that. So what language do you guys suggest? Someone suggested me doing this in PL/SQL, but I don't like it so much, because it's a propertary language and it's bound to Oracle. So what are the most suitable alternatives?

---

### Post by pmasiar on 2007-03-22
> **samir85 said:**
> Unfortunately, I'm not responsible for the datebase design. I think they created a new table for every month, because the tables contain a lot of data (around 30 Mio data sets per month).

... so it makes perfect sense to *NOT* dump all data into one huge slow table, but separate them by month.

What language? Any language you know and has Oracle database bindings. Scripting languages are popular for those tasks (and for a reason), my choice would be Python, but database bindings might be tricky. Java is another one - Oracle loves java and drivers just work, and task is simple enough that even Java suckiness will not hurt you much. ;-)

I cannot believe I recommend java :-)

---

### Post by samir85 on 2007-03-22
> **pmasiar said:**
> ... so it makes perfect sense to *NOT* dump all data into one huge slow table, but separate them by month.

Exactly!

> What language? Any language you know and has Oracle database bindings. Scripting languages are popular for those tasks (and for a reason), my choice would be Python, but database bindings might be tricky. Java is another one - Oracle loves java and drivers just work, and task is simple enough that even Java suckiness will not hurt you much. ;-)

I cannot believe I recommend java :-)

I'm so glad you recommended Java, because it's the only programming language I ever learned (we use it in college). Anyway, after researching a little I read that for Java I need to install JDBC drivers on the database, is that correct? (I would prefer ODBC ...)

Anyway, I'm so excited that I can finally use a programming language in my job !!! :D

---

### Post by pmasiar on 2007-03-22
> **samir85 said:**
> I'm so glad you recommended Java, because it's the only programming language I ever learned 

OK, but you have to promise me you check Python after you are done with this.:-) here is the link: [http://learnpython.pbwiki.com/](http://learnpython.pbwiki.com/) and you will see that programming can be much simpler than java makes you think it is. 

> for Java I need to install JDBC drivers on the database, is that correct? (I would prefer ODBC ...)

I am no way java expert - just use it bacause I have to. ojdbc14.jar was suggested to me as way to go, maybe someone can tell you and me why. :-) If not obvious, I was victim to [http://en.wikipedia.org/wiki/Cargo_cult_programming](http://en.wikipedia.org/wiki/Cargo_cult_programming) - "just do as i told you, i will explain later" - and later never came. But "it works in my computer" :-)

---

### Post by samir85 on 2007-03-22
> **pmasiar said:**
> OK, but you have to promise me you check Python after you are done with this.:-) here is the link: [http://learnpython.pbwiki.com/](http://learnpython.pbwiki.com/) and you will see that programming can be much simpler than java makes you think it is. 



I am no way java expert - just use it bacause I have to. ojdbc14.jar was suggested to me as way to go, maybe someone can tell you and me why. :-) If not obvious, I was victim to [http://en.wikipedia.org/wiki/Cargo_cult_programming](http://en.wikipedia.org/wiki/Cargo_cult_programming) - "just do as i told you, i will explain later" - and later never came. But "it works in my computer" :-)

I promise you. I was always interested in learning Ruby, unfortunately I don't have much time. Thus, foremost I'm learning the stuff, which I have to learn for college and work and that's imo Java and SQL. :(

---

### Post by pmasiar on 2007-03-22
OK, ruby will do too as a penance for using Java. :-)

Now go and sin no more :-)

PS. Python is as easy and powerfull as Ruby, but code looks cleaner. IMHO, YMMV.

---

### Post by samir85 on 2007-03-22
I'm back!

I spent the last hours learning Java JDBC stuff. Anyway, I figured out, that Java is quite an overkill for those simple scripts I want to make. Do you guys have any other suggestions?

---

### Post by pmasiar on 2007-03-22
> **samir85 said:**
> I spent the last hours learning Java JDBC stuff. Anyway, I figured out, that Java is quite an overkill for those simple scripts I want to make. Do you guys have any other suggestions?

As I said, Python :-) with cx_Oracle library. I installed it on dapper but now on feisty something got wrong :-( Might be that Oracle supports it only on Dapper. I had no time to solve it. 

Best language is the one with all required libraries for the task.

---

