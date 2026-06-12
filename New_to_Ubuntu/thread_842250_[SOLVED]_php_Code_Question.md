---
title: "[SOLVED] php Code Question"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by WorldTripping on 2008-06-27
I have a simple chatroom on a site.

It posts and then reads from a .txt flatfile.

Only problem is, when it opens the page and reads the txt file, it reads the whole file (as it should).

Is there any way I can get the php to read only the last 50 lines ?

Here's the code:

```
<?php 
$data = file("log.html");
	foreach ($data as $line) {
	echo $line;
	}
?>
```

Mods: If this is posted in the wrong place, please move accordingly.

Cheers.

---

### Post by hyper_ch on 2008-06-27
[php]
$filename = "/path/to/file.txt";
$handle = fopen ($filename, "r");
$contents = fread ($handle, filesize ($filename));
fclose ($handle);

$contents = explode("\n", $contents);
foreach ($content as $key => $val)
{
    echo "Line $key: $val";
}
[/php]

or


[php]

<?php
$lines = file ('/path/to/file');
foreach ($lines as $key => $val)
{
    echo "Line $key: $val";
}
?>
[/php]

---

### Post by WorldTripping on 2008-06-27
Thanks for that, but it's not quite right.

That code looks at the txt file, and outputs each line with a line number, then the text value, eg;

> Line 1: "Some text"
Line 2: "More text"
Line 3: "Reply text"

What I meant was, if the txt files has 2000 lines in it, I want only the final 50 to be read.

Is that possible ?

Cheers

---

### Post by hyper_ch on 2008-06-27
sure

[php]
<?php
$lines = file ('/path/to/file');
$count = count($lines);
$offset = $count - 50;
foreach ($lines as $key => $val)
{

    if($key >= $offset)
    {
        echo "Line $key: $val";
    }
}
?>
[/php]

---

### Post by wrtpeeps on 2008-06-27
> **WorldTripping said:**
> I have a simple chatroom on a site.

It posts and then reads from a .txt flatfile.

Only problem is, when it opens the page and reads the txt file, it reads the whole file (as it should).

Is there any way I can get the php to read only the last 50 lines ?

Here's the code:

```
<?php 
$data = file("log.html");
	foreach ($data as $line) {
	echo $line;
	}
?>
```

Mods: If this is posted in the wrong place, please move accordingly.

Cheers.

If you are setting something up so that it reads the 50 most recent things, it would make more sense to setup your file so that new things get added at the start.

This would mean you could simply read the first 50 lines and not have to iterate through all of the other ones to get to the last 50.

---

### Post by WorldTripping on 2008-06-27
Brilliant !!

I just took out the;
```
echo "Line $key: $val";
```

And replaced it with;
```
echo "$val";
```

As I don't really need the line numbering in there.

Thanks a million.

---

### Post by WorldTripping on 2008-06-27
> **wrtpeeps said:**
> If you are setting something up so that it reads the 50 most recent things, it would make more sense to setup your file so that new things get added at the start.

This would mean you could simply read the first 50 lines and not have to iterate through all of the other ones to get to the last 50.

I absolutely agree with the concept.

However, it's a chatroom that scrolls downward, so that posters can look up the screen to see the prior posts. Hence when the flatfile is written, later posts get appended to the bottom of the file.

If I were to implement the 'read the top 50 lines' concept, (and reverse how the files was written to), then I would have to read (and output) the top 50 lines one by one, to get the scrolling correct.

This way seemed simpler, and to be honest the txt file doesn't get that long or large before its archived.

Cheers.

---

### Post by manishtech on 2008-06-27
I would like to ask a question. Cant you put the data in the database? 
I this way you dont need to manage the I/O and all the buffering,and sorting and all those things.

I can also understand working with database can lead to a bit overhead,but its affordable.

---

### Post by WorldTripping on 2008-06-27
> **manishtech said:**
> I would like to ask a question. Cant you put the data in the database? 
I this way you dont need to manage the I/O and all the buffering,and sorting and all those things.

I can also understand working with database can lead to a bit overhead,but its affordable.

Yes, I could have put it all into a mySQL database, but to honest the application is not, and does not need to be that complex.

It's a simple one page chatroom, where people post a line at a time. No html, no smilies, nothing fancy. The site does not get that much traffic to warrent an all singing+dancing application. The last chatroom on this site had maybe 2500 lines of chat in 3 years. It does not need to be over-engineered.

This is a straightforward elegant solution to a minor problem (post the last x number of lines, rather that all lines).

Cheers.

---

### Post by manishtech on 2008-06-27
> **WorldTripping said:**
> Yes, I could have put it all into a mySQL database, but to honest the application is not, and does not need to be that complex.

It's a simple one page chatroom, where people post a line at a time. No html, no smilies, nothing fancy. The site does not get that much traffic to warrent an all singing+dancing application. The last chatroom on this site had maybe 2500 lines of chat in 3 years. It does not need to be over-engineered.

This is a straightforward elegant solution to a minor problem (post the last x number of lines, rather that all lines).

Cheers.
I understand! Maybe the stress of your question was more of optimal algorithm for getting the last 50 lines. 
I was stressing more on ease of getting the replies or say in other words managing data using database as I always use to do.

Well, whenever I make anything,I manage all data on database. If the database software is too bulky I start using sqlite to reduce the overhead.

---

### Post by WorldTripping on 2008-06-27
> **manishtech said:**
> Well, whenever I make anything,I manage all data on database. If the database software is too bulky I start using sqlite to reduce the overhead.

I'll have a look at sqlite for future reference.

Cheers.

---

### Post by manishtech on 2008-06-27
> **WorldTripping said:**
> I'll have a look at sqlite for future reference.

Cheers.
Cheers to you too mate!! :)

---

### Post by hyper_ch on 2008-06-27
sqlite is also a databse ;)

eventually you could run a system call with exec....

[php]
$output = exec('tail -n50 /path/to/file');
echo $output;
[/php]

---

### Post by manishtech on 2008-06-27
> **hyper_ch said:**
> sqlite is also a databse ;)

eventually you could run a system call with exec....

[php]
$output = exec('tail -n50 /path/to/file');
echo $output;
[/php]
I meant that since its not client-server modelled,it can put less load on the system and the application too.

---

