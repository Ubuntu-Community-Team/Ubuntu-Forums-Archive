---
title: "PHP Help"
date: 2008-10-14
forum: Programming Talk
---

### Post by Mbengi Bongi on 2008-10-14
Hi guys,

What I'm trying to achieve here is a web page that will query a csv file and display data from that file. From what I've seen the way forward is using PHP.

After having trawled through Google I'm still unsure, I'm a newbie when it comes to php.

Basically I want to enter the first entry of a row from the csv file (which will be a 3 letter code) into a text box, click a 'submit' button (or press <enter> ) and then I want the web page to display the data from that row in a table or something.

Any help would be appreciated

---

### Post by mike_g on 2008-10-14
> What I'm trying to achieve here is a web page that will query a csv file and display data from that file. From what I've seen the way forward is using PHP.
You can use the split function to separate your values into an array: [http://uk.php.net/split](http://uk.php.net/split)

Then go over the array echoing the contents to your table cells.

Edit:
> Basically I want to enter the first entry of a row from the csv file (which will be a 3 letter code) into a text box, click a 'submit' button (or press <enter> ) and then I want the web page to display the data from that row in a table or something.
For this you could split the csv file string and check the first column of each row to see if it matches the code. If so, output the content of the row.

---

### Post by drubin on 2008-10-14
[http://www.php.net/fgetcsv](http://www.php.net/fgetcsv) This link might help you.

---

