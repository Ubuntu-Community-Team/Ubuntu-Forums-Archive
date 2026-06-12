---
title: "Database Normalization in MySQL : )   --- need to confirm my tables"
date: 2008-06-24
forum: Programming Talk
---

### Post by thenetduck on 2008-06-24
Hi
I am new to database normalization and wanted to know if I have form 1 in the database normalization process completed with this table. 

```

USER_ID	Password	email address	
1	hello	test@gmail.com	
			
PROJECT_ID	Name	USER_ID	
1	English Project 101		
			
STACK_ID	Name		
1	dogs are like humans		
			
CARD_ID	Data	STACK_ID	
1	something like this could be on the card'	1	
			
SOURCE_ID	source_type	CARD_ID	SOURCE_INFO_ID
1	book	1	1
SOURCE_INFO_ID	source_information		
1	“McDonalds: Weezz the shizzz”		


```

I need to start making linking tables and don't really know where to begin. With that said, I have yet to find a really good tutorial on database normalization, most that I have found are really confusing. Anyone know of one? What is the next step for this table? 

Thanks 
The Net Duck

OK this is what I have now...

```

email address	Password	
test@gmail.com	hello	
		
PROJECT_ID	Name	
1	English Project 101	
		
STACK_ID	Name	
1	dogs are like humans	
		
CARD_ID	Data	
1	something like this could be on the card'	
		
SOURCE_ID	source_type	
1	book	
SOURCE_INFO_ID	source_information	
1	“McDonalds: Weezz the shizzz”	
		
		
link tables		
		
USER_ID	PROJECT_ID	
		
PROJECT_ID	STACK_ID	
		
STACK_ID	CARD_ID	
		
CARD_ID	SOURCE_ID	
		
SOURCE_ID	SOURCE_INFO_ID	


```

is this better? 

The Net Duck

---

### Post by henchman on 2008-06-25
I think your first database design was okay :) well i actually don't know in which relations your tables are (1:1,1:n,n:m), so can't help you with your second example (just wondering why the 'user table' has no id field anymore, but probably just a mistake).

You just need an extra 'relation table' when you have a n:m relationship. Sometimes it's also good if you are not completely sure if you have such a relationship in the future, cause changing the database design later on sux. 
If you have a 1:1 relationship you can put a foreign key field in one of the tables. If you have a 1:n relationship then you should put it in the n-table.

[http://en.wikipedia.org/wiki/Database_normalization](http://en.wikipedia.org/wiki/Database_normalization) is a good page about normalization. For each of the three forms there are extra pages with good and nice explained examples :)

If you need more help, just ask :>

---

