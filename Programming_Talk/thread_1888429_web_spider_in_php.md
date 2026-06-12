---
title: "web spider in php"
date: 2011-11-29
forum: Programming Talk
---

### Post by shubham1 on 2011-11-29
hi all,
i am creating a web sphider in php
first i want only that it can extracts a whole website with its links , images and insert into mysql
my question is not how to create
my question is function inside function
this question is related to the dir 
for eg.
[PHP]
function some(perameters)
{
         if(somecondition)
         {
         echo some(permiters);
         }
}
[/PHP]
remeber i have created classes
secondly any other suggestion on web sphider will be greatly apprecitaed if you already created please tell me and give your script if possible
any more idea too
my question is not related to the script of web sphider but function iside function
some the spy code i have not posted right now

---

### Post by shubham1 on 2011-12-04
any one

---

### Post by Sworddragon on 2011-12-04
> **shubham1 said:**
> my question is function inside function

After I saw your example I'm not sure if I have understood you correctly. Do you want to know something about recursions? You should give some more details if you want to get better help.

---

### Post by shubham1 on 2011-12-05
> **Sworddragon said:**
> After I saw your example I'm not sure if I have understood you correctly. Do you want to know something about recursions? You should give some more details if you want to get better help.
look at this example
[PHP]
function a()
{
//using the same function here
echo a();
}
[/PHP]
what is recursions

---

### Post by Sworddragon on 2011-12-05
> **shubham1 said:**
> look at this example
[PHP]
function a()
{
//using the same function here
echo a();
}
[/PHP]

You call the same function in it's definition (this is a recursion). a() will be called infinite times and your script will never end. Recursions are often usefull but have one of the heaviest logics in PHP. Is this what you want to know? If not you should explain your problem better.


Edit:

> **shubham1 said:**
> this question is related to the dir

Want you to make some recursive file operations? If yes give us an example what you want to do exactly.

---

### Post by shubham1 on 2011-12-06
> **Sworddragon said:**
> You call the same function in it's definition (this is a recursion). a() will be called infinite times and your script will never end. Recursions are often usefull but have one of the heaviest logics in PHP. Is this what you want to know? If not you should explain your problem better.


Edit:



Want you to make some recursive file operations? If yes give us an example what you want to do exactly.
this code will explain you every thing yes i want recursive file operations
[PHP]
function subdirs($url)
{
$dir = dir("images");

//List files in images directory
while (($file = $dir->read()) !== false)
{
if(is_dir($file))
{
echo subdirs($file);
}
}
}
[/PHP]
this will get all dirs and their dirs and keep on

---

### Post by Sworddragon on 2011-12-06
> **shubham1 said:**
> this code will explain you every thing yes i want recursive file operations
[PHP]
function subdirs($url)
{
$dir = dir("images");

//List files in images directory
while (($file = $dir->read()) !== false)
{
if(is_dir($file))
{
echo subdirs($file);
}
}
}
[/PHP]
this will get all dirs and their dirs and keep on

Now it is a little clearer to me. You want scan recursive a webserver and search for all it's content like images (do you understand the recursive code or need you just a solution how to do this?). If this is what you want it is a bad idea since you can't go sure to have free access to the directories of a webserver.

It may be the best to scan the html code of the website and get all content from it. Regular expressions could be usefull to do this but it is more difficult than simple recursive functions.

---

### Post by shubham1 on 2011-12-06
> **Sworddragon said:**
> Now it is a little clearer to me. You want scan recursive a webserver and search for all it's content like images (do you understand the recursive code or need you just a solution how to do this?). If this is what you want it is a bad idea since you can't go sure to have free access to the directories of a webserver.

It may be the best to scan the html code of the website and get all content from it. Regular expressions could be usefull to do this but it is more difficult than simple recursive functions.
i want recurive in web sphiders
it was an example look at this example
[PHP]
function crawl($url)
{
$html=file_get_html($url);
$links=$html->find("a");
foreach($links as $link)
{
echo crawl($link->href);
}
}
[/PHP]
remember this is also an example code its not full but recursive is clear

---

### Post by Sworddragon on 2011-12-06
Here is a working example:

[php]<?php
function get_content($url)
{
	preg_match_all('#<img.*? .*?src="([^"]+?)".*?/>#', file_get_contents($url), $matches);
	return $matches[1];
}

$content = get_content('http://ubuntuforums.org/showthread.php?t=1888429');
print_r($content);
?>[/php]

This code will search for images on a webserver (in this example this thread). I found 53 images on this thread but the code is just simple. For example you could maybe use sockets to avoid the need of allow_url_fopen=On and a more complex regular expression (like searching for html images and not only xhtml images, maybe even other html specifications, maybe more whitespaces, images with simple quotes, invalid code (like missing quotes), css images and other content like links). But the code should show you how to do this.

---

### Post by shubham1 on 2011-12-07
> **Sworddragon said:**
> Here is a working example:

[php]<?php
function get_content($url)
{
    preg_match_all('#<img.*? .*?src="([^"]+?)".*?/>#', file_get_contents($url), $matches);
    return $matches[1];
}

$content = get_content('http://ubuntuforums.org/showthread.php?t=1888429');
print_r($content);
?>[/php]This code will search for images on a webserver (in this example this thread). I found 53 images on this thread but the code is just simple. For example you could maybe use sockets to avoid the need of allow_url_fopen=On and a more complex regular expression (like searching for html images and not only xhtml images, maybe even other html specifications, maybe more whitespaces, images with simple quotes, invalid code (like missing quotes), css images and other content like links). But the code should show you how to do this.i dont want script i want recursion i have the scripts

---

### Post by lisati on 2011-12-08
I think we have a terminology problem on top of a language problem here.

Here's a suggestion.

In your script you can scan the "current" directory and keep two lists. The first list has the names of the files you are interested in. The second list keeps a note of ALL the directories you find.

When your script has finished building its lists of files and directories, you can then go through your list of directories and run the script over each of the directories.

Warning: there's a trap for the unwary. It involves the way common file systems refer to the "current" directory and the "parent" directory.

---

### Post by shubham1 on 2011-12-08
> **lisati said:**
> I think we have a terminology problem on top of a language problem here.

Here's a suggestion.

In your script you can scan the "current" directory and keep two lists. The first list has the names of the files you are interested in. The second list keeps a note of ALL the directories you find.

When your script has finished building its lists of files and directories, you can then go through your list of directories and run the script over each of the directories.

Warning: there's a trap for the unwary. It involves the way common file systems refer to the "current" directory and the "parent" directory.
its not what i want see my post

---

### Post by satanselbow on 2011-12-08
It may not be what you want - but without explaining yourself a little better and not mixing your terminology, you are unlikely to get a much better answer...

---

### Post by lisati on 2011-12-08
> **shubham1 said:**
> its not what i want see my post

I have read your posts and the replies given. The method I have described is perfect for what you have described in your first post: scan the web page, build a list of pages to scan, and call the function from within itself to scan the pages you have discovered.

---

### Post by lisati on 2011-12-08
You can find an explanation of recursion here: [http://en.wikipedia.org/wiki/Recursion_%28computer_science%29](http://en.wikipedia.org/wiki/Recursion_%28computer_science%29)

---

### Post by shubham1 on 2011-12-08
yes this is what i am doing

---

### Post by Sworddragon on 2011-12-08
You say that you need recursions and not scripts but this is an unprecise description. You got now even recursions explained. For what need you recursive file operations? My example which scans the content of a website will even look recursive for subpages if extended. On this way you can already completely scan a webpage with all it's subpages. But if this isn't what you want I'm currently out of ideas.

---

### Post by shubham1 on 2011-12-08
thansk man i got it

---

