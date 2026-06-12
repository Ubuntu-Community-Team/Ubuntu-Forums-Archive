---
title: "Include inside a variable?? (PHP)"
date: 2008-01-06
forum: Programming Talk
---

### Post by saj0577 on 2008-01-06
Hey,

I need to put an include statement inside a variable and it does not seem to be working for me i have spent ages fiddling with it and it will not work.

Here is a cut down version of my code.

[PHP]<?PHP
$abc= "
<table><tr><td>
".include("file.php"); "</td></tr></table>
";


?>[/PHP]


What you will notice if you use this is that rather then making a variable, it actually runs include as if it was not inside a variable.
i.e
[PHP]<?PHP
include("file.php");
?>[/PHP]

i have tried moving around " and . but nothing seems to be working. I would be very greatful if someone could come up with a solution as I can not find anything on google either.


Thanks in advance 
Saj

---

### Post by LaRoza on 2008-01-06
That won't work. include (and require) take a file and plop the contents into the other file.

You you want to store data in another file, store them as variables or functions and include the file at the top of your php files and use the contents.

---

### Post by saj0577 on 2008-01-06
> **LaRoza said:**
> That won't work. include (and require) take a file and plop the contents into the other file.

You you want to store data in another file, store them as variables or functions and include the file at the top of your php files and use the contents.

The slight problem with that is i do not think that would work as. the file i am including is very large (it deals with echo ing xml information into a table.

My whole situation.
I have a file called layout.php which has the basic layout for all my documents
-menu
-log in bit on the side etcc
and on all my other files for example index.php will only contain
[PHP]<?PHP
$content = "hello";
include("layout.php");
?>[/PHP]

and on the layout.php page their is a section that is $content. so when you go to index.php it shows layout.php with "hello" in the area where on the layout page it says $content.

On one of my pages i have i need to include the large file and addition information. I could create a new file with the addition information inside the large file but then every other page that uses the large file will also have the addition content which is not good, and having 2 files would just not be practical at all.

Hope it all makes sense, any questions just ask.

Saj

---

### Post by saj0577 on 2008-01-06
delted

---

### Post by LaRoza on 2008-01-06
I think you need to rethink your design.

You can have plain content in an include.

---

### Post by sas171 on 2008-01-06
There are 2 ways to accomplish this:
[LIST=1]
[*]Use a return statement inside the include file and include it like $var = include(file.php);
[*]Use ob_get and ob_get_clean to capture the output
[/LIST]

But I also think you should restructure your code. Use on of the frameworks and you will be a lot happier ;)

---

### Post by saj0577 on 2008-01-06
Okay so you think use frames? Or is their a better way do you think. When i want to edit te layout of y webpages i only want to ave to edit one file not one per web page as that would be a pain in the ....


Cheers

Saj

---

### Post by LaRoza on 2008-01-06
> **saj0577 said:**
> Okay so you think use frames? Or is their a better way do you think. When i want to edit te layout of y webpages i only want to ave to edit one file not one per web page as that would be a pain in the ....


Cheers

Saj

Frames? Never.

Use external styles sheets for style.

You can use includes, like I do, for the unique content of each page.

---

### Post by saj0577 on 2008-01-06
Yeah that what i have, i think. At the minute i have:
layout.php with position on all content
settings.css with all colour settings text size etc


Is that what you mean?

Saj

---

### Post by saj0577 on 2008-01-06
Would it be possible for you to give me a very basic structure of your website. i.e what files you have and what they do.? IF so i would be very greatful.

So do you define each table (or whatever you use to position your content) in each page for your website.) Because if you do when you want to update your website you have to update every page which is a pain.


Saj

---

### Post by Atp on 2008-03-18
Actually If you guys would bother to read php.net you would find that it is possible to include into a variable by capturing the contents of what include brings into the page

```

ob_start();
include $filename;
$contents = ob_get_contents();
ob_end_clean();

```

---

### Post by LaRoza on 2008-03-18
> **Atp said:**
> Actually If you guys would bother to read php.net you would find that it is possible to include into a variable by capturing the contents of what include brings into the page

```

ob_start();
include $filename;
$contents = ob_get_contents();
ob_end_clean();

```

Post six mentions that.

Please be a bit more respectful when answering, "if you guys would bother to read..." is not really friendly.

You can cite your source, and give the answer, no reason to be insulting.

"If you bothered to read the thread, you would see it was already mentioned...", see?

Also, PHP has a large and confusing standard library with no namespaces and odd naming conventions.

---

### Post by Wybiral on 2008-03-18
> **LaRoza said:**
> Also, PHP has a large and confusing standard library with no namespaces and odd naming conventions.

That's for sure...

---

