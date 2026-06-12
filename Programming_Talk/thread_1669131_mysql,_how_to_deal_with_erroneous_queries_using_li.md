---
title: "mysql, how to deal with erroneous queries using like '%find%'"
date: 2011-01-17
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-17
say you are searching a table 
select something from table where field like '%evolution%'

due to the wildcard %, it will return everything in the string that contains 'evolution'
including revolution or devolution, etc... see what I mean?

I though about adding a leading space to it like '% evolution' and that works, BUT BUT BUT, some things wont come bace if the field  data has data like
some words-evolution, or words.evolution. See what I mean? 

I looked at fulltext indexing, but these are not all varchar fields and I heard that fulltext was slow.

If you do a google search for evolution, they dont show results returning revolution.

---

### Post by sdowney717 on 2011-01-17
[http://dev.mysql.com/doc/refman/5.0/en/fulltext-natural-language.html](http://dev.mysql.com/doc/refman/5.0/en/fulltext-natural-language.html)

i did read into this, perhaps it would work ok. 
I wonder how slow it is.
and, how many fields would you fulltext index before it ground down, or will it?

---

### Post by sdowney717 on 2011-01-17
[http://www.petefreitag.com/item/477.cfm](http://www.petefreitag.com/item/477.cfm)

just some more on how to do this,
you can also add by saying something like this

[http://www.mysqlfaqs.net/mysql-faqs/Indexes/Full-Text-Indexes/How-to-create-multi-columns-full-text-index-in-MySQL](http://www.mysqlfaqs.net/mysql-faqs/Indexes/Full-Text-Indexes/How-to-create-multi-columns-full-text-index-in-MySQL)

CREATE FULLTEXT INDEX trialsindex ON bookdata (titles, author, callnumberpre, callnumber, catalogcard, summary)

two words included in search
SELECT * FROM bookdata WHERE MATCH (titles, author, callnumberpre, callnumber, catalogcard, summary) AGAINST ( 'Hurricane katrina');

boolean mode seems to make the most sense to me

SELECT * FROM bookdata WHERE MATCH (titles, author, callnumberpre, callnumber, catalogcard, summary) AGAINST ('+Hurricane -katrina' IN BOOLEAN MODE)

ok, what exactly does the two word search do ? is it either word?

---

### Post by Vaphell on 2011-01-17
[http://dev.mysql.com/doc/refman/5.1/en/string-syntax.html](http://dev.mysql.com/doc/refman/5.1/en/string-syntax.html)

replace **%** with **\%** before running a query

---

### Post by sdowney717 on 2011-01-17
add hurricane but not katrina 

SELECT * FROM bookdata WHERE MATCH (titles, author, callnumberpre, callnumber, catalogcard, summary) AGAINST ('+Hurricane -katrina' IN BOOLEAN MODE)

how would you do this where you wanted the terms hurricane and katrina 

OR

how would you do this where you wanted the terms hurricane or katrina

??

---

### Post by Wtower on 2011-01-17
Yes I believe that you are heading to the right direction. I had to deal with such a situation once when designing a web app and fulltext indexing was my conclusion too. Unfortunately persoanally can't help you with mysql though, as we had to deal with oracle back then.

Another option I guess is to build huge select queries including and excluding possibilities. For smaller web apps a possibility is also to let google do the indexing work with custom search.

---

### Post by Some Penguin on 2011-01-17
Consider Sphinx.  Or Lucene.

---

### Post by sdowney717 on 2011-01-17
I found I can do this type of search, combining match with a like search
The index you create, you have to include those fields in the match search.
And it runs faster than I remember, and now includes text fields.


> SELECT titles, author, callnumberpre, callnumber, catalogcard, summary FROM bookdata where MATCH (titles, author, callnumberpre, callnumber, catalogcard, summary) AGAINST ('glue history' in boolean mode) or MATCH (titles, author, callnumberpre, callnumber, catalogcard, summary) AGAINST ('the') 


> SELECT titles, author, callnumberpre, callnumber, catalogcard, summary FROM bookdata where MATCH (titles, author, callnumberpre, callnumber, catalogcard, summary) AGAINST ('+free -resolve -george' IN BOOLEAN MODE) and (where titles like '%born%')


etc...

---

### Post by sdowney717 on 2011-01-17
how would you do this where you wanted the terms hurricane or katrina?

I think for or it is just 

MATCH (titles, author, callnumberpre, callnumber, catalogcard, summary) 
  AGAINST ('free resolve george')

Use the AGAINST ('+word -word' IN BOOLEAN MODE) for and words and not words

Although I tried just this
> 
MATCH (titles, author, callnumberpre, callnumber, catalogcard, summary) 
  AGAINST ('-free -resolve -george' IN BOOLEAN MODE)



and got no results. I would think using all-words, would return all rows where those words did not exist??

---

