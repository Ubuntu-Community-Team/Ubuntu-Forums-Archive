---
title: "What is your favourite (My)SQL command?"
date: 2009-06-16
forum: Programming Talk
---

### Post by theDaveTheRave on 2009-06-16
Hello All.

I'm thinking of starting a new page on the wiki with details of the most helpful (those that aren't obvious) commands in MySQL.

Actually I may spread it out to all SQL servers, so if you are using a different SQL server (sybase, postgres etc), and the syntax is slightly different, please also state the differences.

include  some info on use and problems when using it, if you would like to add one please insert the code and a brief breakdown of the syntax as I have done... then I can get started on the wiki page...

Of course credit will be given.

My personal favourite is
```

load data infile

```

here is the full syntax, and some explanations.....

full syntax
```

load data [COLOR="Red"]infile[/COLOR] '/fullPathTo/myfile.*' [COLOR="Red"]replace[/COLOR] into table 'tablename'
fields terminated by '\t' lines terminated by '\r\n'
([COLOR="Red"]@col1, @col3, @col4, @col5, @col6[/COLOR])
set [COLOR="Red"]1stcolum=@col1[/COLOR], 2ndColumn=@col4, 3rdColumn=@col5...

```

OK a quick breakdown, I've highlighted in [COLOR="Red"]red[/COLOR] those bits that often catch me out

[COLOR="Red"]infile[/COLOR]; you may require to add in the keyword [COLOR="Green"]local[/COLOR] before infile, depending on your server version, and your user permissions to make this command work.

[COLOR="Red"]replace[/COLOR]; may need to be changed to [COLOR="Green"]ignore[/COLOR] if you are importing a file that could have potential errors in it (this prevents the import from aborting part way through..... not good when you have a file with 5 million records!).

[COLOR="Red"]@col1, @col3, @col4, @col5, @col6[/COLOR] I use this syntax to enumerate the colums that are found in the file that I am importing, you can use the true column names if it is easier, and there are only a few!

set [COLOR="Red"]1stcolum=@col1[/COLOR]; again with the above command I am telling the server that the first column in my table (in this instance called 1stcolum should hold the data that is in the @col1 variable I created in the previous line of the command.

thanks for all who add in details.

David

---

