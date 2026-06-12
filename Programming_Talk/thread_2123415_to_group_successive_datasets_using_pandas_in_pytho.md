---
title: "to group successive datasets using pandas in python"
date: 2013-03-07
forum: Programming Talk
---

### Post by madhu91 on 2013-03-07
hello. I have a huge GPS datasets of the form (id,timestamp,longitude,latitude). Something like this[TABLE="width: 500"]
[TR]
[TD]id[/TD]
[TD]timestamp[/TD]
[TD]longitude[/TD]
[TD]latitude[/TD]
[/TR]
[TR]
[TD]3[/TD]
[TD]2001-02-02 13:02:01[/TD]
[TD]132.3245[/TD]
[TD]56.2345[/TD]
[/TR]
[TR]
[TD]3[/TD]
[TD]2001-02-02 13:02:06[/TD]
[TD]132.3245[/TD]
[TD]56.2345[/TD]
[/TR]
[TR]
[TD]3[/TD]
[TD].........[/TD]
[TD]same as above[/TD]
[TD]same as above[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]....[/TD]
[TD]....[/TD]
[TD]....[/TD]
[/TR]
[TR]
[TD]3[/TD]
[TD]2001-02-02 13:05:01[/TD]
[TD]132.3245[/TD]
[TD]56.2345[/TD]
[/TR]
[TR]
[TD]3[/TD]
[TD]2001-02-02 13:05:06[/TD]
[TD]132.3246[/TD]
[TD]56.2345[/TD]
[/TR]
[/TABLE]
the above is just an example of how my data is present. I have around 990000 records roughly. now i want something like this
[TABLE="width: 500"]
[TR]
[TD]id[/TD]
[TD]timestamp[/TD]
[TD]longitude[/TD]
[TD]latitude[/TD]
[/TR]
[TR]
[TD]3[/TD]
[TD]2001-02-02 13:02:01 - 2001-02-02 13:05:01[/TD]
[TD]132.3245[/TD]
[TD]56.2345[/TD]
[/TR]
[TR]
[TD]3[/TD]
[TD]2001-02-02 13:05:06[/TD]
[TD]132.3246[/TD]
[TD]56.2345[/TD]
[/TR]
[/TABLE]
i want to merge all the rows of same latitude and longitude values into a single row. I am a beginner in pandas and i cannot use "group by" function where group by groups all the occurances but i want successive occurances to be grouped.

any help would be surely appreciated. :)
thank you very much..

---

### Post by coffeecat on 2013-03-10
*Thread moved to **Programming Talk**,* at request of OP.

---

