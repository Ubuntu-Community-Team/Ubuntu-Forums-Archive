---
title: "mySQL button counter"
date: 2008-10-26
forum: Programming Talk
---

### Post by Bradosia on 2008-10-26
Hello,

What I am attempting to do is create a button that links a download. A number is displayed next to the button or somewhere else on the page of how many times its been clicked. I want the button when clicked to add the #1 to the MySQL table. So it goes up by 1 everytime it is clicked. There are many downloads on my website so the table will be organized for example:
ID  |   count
1           5
2          40
(ID = the button
count = amount of times its been clicked)

What I am asking you is to help create a script that does this because frankly I have no idea how this is done and all the other download counters dont use mySQL or just have too many features included with them

 for example:
>An admin panel (yuk)
>and also another feature which makes you have to change your download path to something like [www.yourdomain.com/download.php?ID=6](www.yourdomain.com/download.php?ID=6)  (double yuk)

---

### Post by skotos on 2008-10-26
A quick answer:
Every file should have an id: suppose 1 for the first.
The button will have a link to your php script such as this```
<a href="mycounter.php?id=1"><img src="button.png" alt="Filename.ext" /></a>
```Then, in the script you will have to examine the $_GET['id'] value and look for it in the database.```
SELECT * FROM `counter` WHERE `id`=1
```If you find it by the file id (you have to check the returned rows number), you increase the value, otherwise you enter a new record.
Remember when you use the UPDATE command to add at the end LIMIT 1, just in case something goes wrong: in the worst case you will damage a counter per downloaded file and not all!
Then, using the headers functions, you will have to say to the browser the mime type of the file the user is going to receive, then output it.
Look on php.net for the headers functions if your language of choice is php: they provide a few samples on this kind of output!
Another thing: do not use count, but for instance counter, because using reserved words can be misleading and a source of difficult errors to debug

---

