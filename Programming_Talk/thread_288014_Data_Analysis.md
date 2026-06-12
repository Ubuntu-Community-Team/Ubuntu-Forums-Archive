---
title: "Data Analysis"
date: 2006-10-29
forum: Programming Talk
---

### Post by rwclardy on 2006-10-29
I am looking to do some data analysis, not real complicated stuff, but there is a ton of it.  I have some programming experience and don't mind learning a new language if I have too, but I am much more interested in the results than becoming a full time developer.  

I know enough C++ to get the algorithm, but I am clueless when it comes to reading a database, outputing (especially console stuff), and printing.  Printing isn't that big of deal.

I just want to enter my data, run it and get the results.  

Any ideas?

Thanks rob

---

### Post by DaveBorealis on 2006-10-29
Hello,

What kind of database has your data?  If it's something like MySQL there's a command-line interface that goes with it.  If you're not doing any overly fancy number crunching you could probably do all the data manipulation with the CLI.  However most of the popular scripting languages have APIs to the major databases.  Perl, PHP and (I believe) Python come to mind.

Best regards,
Dave

---

### Post by amo-ej1 on 2006-10-29
perhaps it's better to define your problem set a little bit more, what data are we talking about ? what is the size ? will you need to implement relations on it (as in, will you need a database ?) or ist is a huge array of numbers, will you gather it on the spot or is it offline analysis, what kind of output do you want ? a single number ? graphics ? heck, an opengl rendered rotatable 3d structure ?

---

### Post by DavidBell on 2006-10-29
If you don't want to mess around with database interfaces, see if you database will output data to a csv file then just use scanf() to read the file & fprintf() to print results to file

DB

---

