---
title: "PHP - parse CSV file"
date: 2009-12-04
forum: Programming Talk
---

### Post by MN Noob on 2009-12-04
Anyone know of some free code I could take a look at to get an idea of how to do this? I have a lot of it already done, and can parse a simple csv file. But I would like to know how one can use the same script to parse different CSV files. i.e. they don't all look alike or have the data look the same. One may have quotes around the data, or even quotes around some data. (I need to get rid of those quotes for my database) Some files may have data in different columns. (I think I can fix this myself, but wouldn't mind taking a look at other code to see if what I am thinking is a good way of doing it)

Just to cover everything, I am using PHP 5.3.1 on an Apache server. I also am using explode() to get each row and column. (if there is an easier way than using explode, I would be glad to learn)

And I know this isn't specifically a PHP forum, but I have had good luck here in the past with other questions. And you guys are all very nice about it.

Thanks in advance

---

### Post by v8YKxgHe on 2009-12-04
[http://php.net/fgetcsv](http://php.net/fgetcsv)

---

### Post by MN Noob on 2009-12-04
Thanks, not sure how I missed that. I will have to play around with it and some of the examples tonight.

---

### Post by korvirlol on 2009-12-04
fgetcsv is def the way to go.

This little gem will parse each line of the file:
[PHP]
while (($data = fgetcsv($prod)) !== FALSE) {}[/PHP]

where $data is the array containing the elements split on commas, and $prod is the file resource (after upload)

---

