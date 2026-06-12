---
title: "php and encoding characters"
date: 2010-03-16
forum: Programming Talk
---

### Post by korvirlol on 2010-03-16
I am not really sure of the best way to do this, looking for some advice:

I really quite heavily on PHP::serialize for encoding objects and arrays to store in databases (there could be a better way that im not aware of, but this seems to work pretty well), but this raises a few problems.

If i use mysql_real_escape_string on a serilaized array (escapes quotes, and other string elements serialize uses) sometimes it makes the string unable to unserialize, which is an issue. An example of what i mean is:

Before Serilaize:
```

a:3:{s:9:"Operating";a:4:{s:12:"Wage  Expense";s:9:"111745.25";s:4:"rent";s:6:"232.12";s:8:"utilties";s:7:"1212.43";s:1:"a";s:2:"13";}s:8:"Employee";a:1:{s:1:"b";s:2:"43";}s:5:"Other";a:1:{s:1:"c";s:2:"56";}}
```

After serialize, and error message:

```
a:3:{s:9:\"Operating\";a:4:{s:12:\"Wage  Expense\";s:9:\"111745.25\";s:4:\"rent\";s:6:\"232.12\";s:8:\"utilties\";s:7:\"1212.43\";s:1:\"a\";s:2:\"13\";}s:8:\"Employee\";a:1:{s:1:\"b\";s:2:\"43\";}s:5:\"Other\";a:1:{s:1:\"c\";s:2:\"56\";}}

Notice: unserialize(): Error at offset 5 of 237 bytes in  /srv/www/deernet/finances/lib/class.FINANCE_MANAGER.php on line 135 
```


The main reason i am doing this is, in the off chance that an array index has an apostraphe, or some other sneaky character in it, unless i escape the string, the query will break. If i dont escape it, then the array will break. 

There must be a better way to handle soething like this. Any suggestions?

---

### Post by v8YKxgHe on 2010-03-16
Yes, don't store serialized data in the database. You can't do anything with it at the database level apart from select it. What are you storing?

---

### Post by korvirlol on 2010-03-16
Well that was the idea. Basically it is tons of, say, financial or schedule data that needs to get parsed by PHP at a later time. I couldnt really think of a more viable way to store that kind of data (it isnt the same kind of traditional database storage item).

If thats not clear, this is what i mean. For each month there is a ton of raw data that needs to get stored for use in many different places. For example, if i am storing, statistical financial data for 15 people per month, the array stores something like```
 
month-epoch => array(
                     empid1 => array(val1, val2, val3, ..., valn), 
                     empid2 => array(val1, val2, ... valn),
                     .
                     .
)
```It is a really quick and easy way to get the data into a savable format to recall dynamically in different places at a later time.

edit: i dont need to do anyhting at the database level then select it.

---

### Post by v8YKxgHe on 2010-03-16
Use multiple tables, for example one that stores all the people and one that stores the data - the data table having a column that links them to the people one.

You will get far more flexibility out of that, and will be much easier on the database. What if in 6 months you've collected a lot of information, and need to search through it? You're going to have to select all of that data and lug it through MySQL into PHP. If you've got your table structure setup correctly, you would be able to select just the rows and columns you want, with far less overhead.

---

