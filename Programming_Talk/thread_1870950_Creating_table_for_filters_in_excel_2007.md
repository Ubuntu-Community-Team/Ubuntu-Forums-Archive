---
title: "Creating table for filters in excel 2007"
date: 2011-10-28
forum: Programming Talk
---

### Post by vjohnny8 on 2011-10-28
Hi all,

Please see the tables below and data:-

create table MST_FILTER(  FL_NO   NUMBER(38) not null,  FL_TYPE VARCHAR2(50),  FL_DESC VARCHAR2(60))alter table MST_FILTER  add primary key (FL_NO) 	1	Text Filters	                Filters [COLOR=navy]**for**[/COLOR] normal text	2	Number Filters	Filters [COLOR=navy]**for**[/COLOR] numerals	3	Date Filters	                Filters on dates	4	Color Filters	                Filters by color   create table MST_FILTER_TYPE(  FL_TYPE_NO     NUMBER(38),  FL_TYPE_NAME   VARCHAR2(50),  FL_TYPE_ACTION VARCHAR2(50))  	1	Equals	                EQ	1	Does Not Equal	NEQ	1	Begins With	BW	1	Ends With	                EW	1	Contains	                C	1	Does Not Contain	NC	2	Equals	                =	2	Does Not Equal		2	Greater Than	>	2	Greater Than Or Equal To	>=	2	Less Than	                                <	2	Less Than Or Equal To	                <=	2	Between	                                BT	2	Top 10	                                T10	2	Above Average	                AAVG	2	Below Average	                BAVG	3	Equals	                                ES	3	Before	                                BF	3	After	                                AF	3	Between	                                BE	3	Tomorrow	                                TM	3	Today	                                TO	3	Yesterday	                                YS	3	Next Week	                                NW	3	This Week	                                TW	3	Last Week	                                LW	3	Next Month	                NM	3	This Month	                                TM	3	Last Month	                                LM	3	Next Quarter	                NQ	3	This Quarter	                TQ	3	Last Quarter	                LQ	3	Next Year	                                NY	3	This Year	                                TY	3	Last Year	                                LY	3	Year to Date	                YD	4	Filter by Cell Color	                FCC	4	Filter by Font Color	                FFC	2	Bottom 10	                                B10

in the above 2 tables, any other change is required i.e any new columns should be added or a new table should be created. any suggestions would be appreciated.

I am creating a table for filters in excel 2007 in oracle 11G

---

