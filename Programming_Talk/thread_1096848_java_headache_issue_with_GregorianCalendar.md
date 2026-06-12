---
title: "java: headache issue with GregorianCalendar"
date: 2009-03-15
forum: Programming Talk
---

### Post by badperson on 2009-03-15
okay, I'm sure this is really basic, but this code: 

```
		while(today.get(Calendar.DAY_OF_WEEK) != Calendar.SATURDAY){
			today.roll(Calendar.DAY_OF_YEAR, true);
			String sqlFormat = "" + today.get(Calendar.YEAR) + "-" + today.get(Calendar.MONTH) + "-" + today.get(Calendar.DAY_OF_MONTH); 
			System.out.println(today.getTime() + " sql format: " + sqlFormat );
		}
```

creates this output: 

```
Today is Sun Mar 15 11:44:22 EDT 2009
Mon Mar 16 11:44:22 EDT 2009 sql format: 2009-2-16
Tue Mar 17 11:44:22 EDT 2009 sql format: 2009-2-17
Wed Mar 18 11:44:22 EDT 2009 sql format: 2009-2-18
Thu Mar 19 11:44:22 EDT 2009 sql format: 2009-2-19
Fri Mar 20 11:44:22 EDT 2009 sql format: 2009-2-20
Sat Mar 21 11:44:22 EDT 2009 sql format: 2009-2-21
```

Why...oh why...does the today.get(Calendar.MONTH) return "2" when the right month displays in today.getTime()???

thanks, 
bp

---

### Post by kjohansen on 2009-03-15
Sounds like Calendar.MONTH is 0 based.  Thus:

Jan   =0
Feb   =1
March =2

etc...

so it is correct.

---

### Post by badperson on 2009-03-15
d'oh....k, that makes sense, thanks...
although I still think it's obnoxious that you have to add one to get a date value that you can actually USE....heh-heh:D
thanks!
bp

---

### Post by drubin on 2009-03-15
Hey it looks like you are trying to format data for sql. It might be easier to use [PreparedStatments]("http://java.sun.com/docs/books/tutorial/jdbc/basics/prepared.html") [http://java.sun.com/j2se/1.5.0/docs/api/java/sql/PreparedStatement.html](http://java.sun.com/j2se/1.5.0/docs/api/java/sql/PreparedStatement.html)

---

