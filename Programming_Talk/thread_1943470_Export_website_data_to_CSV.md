---
title: "Export website data to CSV"
date: 2012-03-19
forum: Programming Talk
---

### Post by scottyf11 on 2012-03-19
Hello,

I have a simple html file saved on my desktop that lists products in this format.

```

<a name="235"/>
<h1>1404</h1>
<div><div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;"><div>10 1/2 INCH GLASS LAMP YELLOW FLOWERS</div><img src="website.data_files/1404.jpg" type="image/jpeg"/></div>
</div>
<hr>

<a name="241"/>
<h1>1403</h1>
<div><div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;"><div>10 IN GLASS LAMP BLUE SHADE</div><img src="website.data_files/1403.jpg" type="image/jpeg"/></div>
</div>
<hr>

```

I would like to figure out a way to have a CSV file exported from this data in the format:

```
1404,10 1/2 INCH GLASS LAMP YELLOW FLOWERS,website.data_files/1404.jpg
1403,10 IN GLASS LAMP BLUE SHADE,website.data_files/1403.jpg

```

Could anyone point me in the right direction??

Thanks!!

Scott

---

### Post by lisati on 2012-03-19
Rather than hard-code the data on the webpage, I'd suggest putting it in a database. That way, you will have some more flexibility when it comes to formatting it for display or preparing it for download as a file.

---

### Post by scottyf11 on 2012-03-19
This website is created by a software program.  I want to extract the data from the website to a CSV so I can upload it my database.

---

### Post by ofnuts on 2012-03-20
> **scottyf11 said:**
> Hello,

I have a simple html file saved on my desktop that lists products in this format.

```

<a name="235"/>
<h1>1404</h1>
<div><div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;"><div>10 1/2 INCH GLASS LAMP YELLOW FLOWERS</div><img src="website.data_files/1404.jpg" type="image/jpeg"/></div>
</div>
<hr>

<a name="241"/>
<h1>1403</h1>
<div><div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;"><div>10 IN GLASS LAMP BLUE SHADE</div><img src="website.data_files/1403.jpg" type="image/jpeg"/></div>
</div>
<hr>

```I would like to figure out a way to have a CSV file exported from this data in the format:

```
1404,10 1/2 INCH GLASS LAMP YELLOW FLOWERS,website.data_files/1404.jpg
1403,10 IN GLASS LAMP BLUE SHADE,website.data_files/1403.jpg

```Could anyone point me in the right direction??

Thanks!!

ScottIf you remove all the line feeds (tr -d) and add them back only before a "<a" then you have one line of data per item and is becomes  a simple matter of removing what you don't want with  a "sed" stage.

---

### Post by SeijiSensei on 2012-03-20
> **scottyf11 said:**
> This website is created by a software program.  I want to extract the data from the website to a CSV so I can upload it my database.

Does the "software program" have the product information in a database?  What kind of database?  If it's an SQL database like MySQL, PostgreSQL, or MSSQL, you can extract the data easily from a computer with Windows and Excel on which the appropriate ODBC connector is installed.

For instance, I have a PostgreSQL database on a virtual host in the cloud.  I can access all the data from a Windows machine in my office with the PG ODBC driver installed.  

Of course, your computer will need to connect over the network to the remote database.  You'd need to coordinate that with the owner of the database.

Otherwise you'll need to be able to write a program or script to massage the HTML file you posted. I don't think it's quite as "simple" as ofnuts would have you believe.  If you know a language like Python or PHP, it shouldn't be too hard.  Editing a file with a bash script using the standard Unix tools like sed, awk, and grep is possible, but arduous, especially for the uninitiated.

---

### Post by The Cog on 2012-03-20
Like this?
```
cat htmlfile | tr -d '\n' | sed 's/<hr>/\n/g' | sed -e  's/<.*<h1>//' -e 's_</h1.*<div>_,_g' -e 's_</div><img src="_,_' -e 's/".*//'
```

---

### Post by ofnuts on 2012-03-20
> **The Cog said:**
> Like this?
```
cat htmlfile | tr -d '\n' | sed 's/<hr>/\n/g' | sed -e  's/<.*<h1>//' -e 's_</h1.*<div>_,_g' -e 's_</div><img src="_,_' -e 's/".*//'
```More or less. I'll trust you for the second sed incantation, but you got the idea. It may be useful to add a grep stage (before the seond sed) somewhere to get rid of the rest of the HTML.

---

### Post by scottyf11 on 2012-03-20
> **The Cog said:**
> Like this?
```
cat htmlfile | tr -d '\n' | sed 's/<hr>/\n/g' | sed -e  's/<.*<h1>//' -e 's_</h1.*<div>_,_g' -e 's_</div><img src="_,_' -e 's/".*//'
```

That works really well thank you!!!  Two questions, the output contains "<br>" tags so how do I remove those?  Also, the text is displayed in the terminal, is there a way to output it to a csv?

Thanks again!!!

---

### Post by scottyf11 on 2012-03-20
To export to a file you just need to add >> and the directory so the resulting code would be

```

cat htmlfile | tr -d '\n' | sed 's/<hr>/\n/g' | sed -e  's/<.*<h1>//' -e 's_</h1.*<div>_,_g' -e 's_</div><img src="_,_' -e 's/".*//' >> /home/user/file.csv

```

All I need now is to remove the <br> tag and maybe any extra spaces at the end of the description div and this thread will be marked solved!

---

### Post by The Cog on 2012-03-22
That's odd. There are no <br> tags in the sample values you posted.

You could try:
```
cat htmlfile | tr -d '\n' | sed 's/<hr>/\n/g' | sed -e  's/<.*<h1>//' -e 's_</h1.*<div>_,_g' -e 's_</div><img src="_,_' -e 's/".*//'  -e 's/<br>//'>> csvfile
```

---

### Post by scottyf11 on 2012-03-22
> **The Cog said:**
> That's odd. There are no <br> tags in the sample values you posted.

You could try:
```
cat htmlfile | tr -d '\n' | sed 's/<hr>/\n/g' | sed -e  's/<.*<h1>//' -e 's_</h1.*<div>_,_g' -e 's_</div><img src="_,_' -e 's/".*//'  -e 's/<br>//'>> csvfile
```

worked perfectly!  you are awesome

---

### Post by scottyf11 on 2012-03-22
Some of the values ended up having the <br> tag.  I didn't realize it either until the output was posted.  Your solution worked perfectly.  Thank you very much.

---

