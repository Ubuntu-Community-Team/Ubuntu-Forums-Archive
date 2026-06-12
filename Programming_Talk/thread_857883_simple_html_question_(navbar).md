---
title: "simple html question (navbar)"
date: 2008-07-12
forum: Programming Talk
---

### Post by shoagun on 2008-07-12
I just started learning how to do basic web development.  I'm trying to solve a problem that I imagine has been solved many times over.  Basically, I want the same navigation bar to appear on every page of a site that I'm building.  However, I don't want to copy and paste the same html into the .html file for each page.  If I want to later edit the navigation bar, it would be slightly annoying.   It is much cleaner to  write the code for the navigation bar once, in a single file and then refer to that file whenever needed.   

So far, every solution I've found to this problem involves either:
1. using PHP
2. using some external website building program

My question is:
Is there any way to do this WITHOUT using PHP or any programs?  

Thanks!

---

### Post by Phristen on 2008-07-13
Yes, you can use frames.

---

### Post by ad_267 on 2008-07-13
> **shoagun said:**
> I just started learning how to do basic web development.  I'm trying to solve a problem that I imagine has been solved many times over.  Basically, I want the same navigation bar to appear on every page of a site that I'm building.  However, I don't want to copy and paste the same html into the .html file for each page.  If I want to later edit the navigation bar, it would be slightly annoying.   It is much cleaner to  write the code for the navigation bar once, in a single file and then refer to that file whenever needed.   

So far, every solution I've found to this problem involves either:
1. using PHP
2. using some external website building program

My question is:
Is there any way to do this WITHOUT using PHP or any programs?  

Thanks!

Well you could use another scripting language other than php. But basically no, you can't do this with only html and css. 

You could have a look at server side includes, a very basic scripting language that is basically designed only for this sort of thing. [http://en.wikipedia.org/wiki/Server_Side_Includes](http://en.wikipedia.org/wiki/Server_Side_Includes)

Edit: Yes you could use frames but that isn't a very simple or accessible solution and I wouldn't recommend it.

---

### Post by LaRoza on 2008-07-13
> **shoagun said:**
> I just started learning how to do basic web development.  I'm trying to solve a problem that I imagine has been solved many times over.  Basically, I want the same navigation bar to appear on every page of a site that I'm building.  However, I don't want to copy and paste the same html into the .html file for each page.  If I want to later edit the navigation bar, it would be slightly annoying.   It is much cleaner to  write the code for the navigation bar once, in a single file and then refer to that file whenever needed.   

So far, every solution I've found to this problem involves either:
1. using PHP
2. using some external website building program

My question is:
Is there any way to do this WITHOUT using PHP or any programs?  

Thanks!

You can use a client side script to add it, however, that won't degrade gracefully (like CSS, ECMAScript should be linked as an external file with nothing in the markup).

Server side includes are the simplest way. Frames are the worse way, don't do that. 

What you want is to add dynamicism (if that is a word, whatever the "state of being dynamic" word is) to a static language. That requires a language of a sort.

XHTML is static.

---

### Post by Phristen on 2008-07-13
Well SSI would qualify as an "externl program", wouldn't it? :)
If we are restricted by XHTML then frames is the only way to go, unless you wanna mess with javascript.

---

### Post by LaRoza on 2008-07-13
> **Phristen said:**
> Well SSI would qualify as an "externl program", wouldn't it? :)
If we are restricted by XHTML then frames is the only way to go, unless you wanna mess with javascript.

Messing with frames is worse than messing with ECMAScript.

Basically, the OP wants to program without programming.

---

### Post by Phristen on 2008-07-13
> Messing with frames is worse than messing with ECMAScript.I know frames are nasty, but I don't see how client side scripting hacks are any better.

---

### Post by LaRoza on 2008-07-13
> **Phristen said:**
> I know frames are nasty, but I don't see how client side scripting hacks are any better.

It will be standard code? Frames have no place in the lastest standards.

I didn't say client side scripts were, in fact, I advised against it. The issue here is server side sripting, which is the only real option that is usable and degrades gracefully.

---

### Post by -grubby on 2008-07-13
Doing this with PHP would be easy, and doing it with frames would be evil. All you would have to do with PHP is include a file with the html template in it. something like :

** file.php **
[php]$html_template = "<!-- Navbar code -->";[/php]

Then to call it later :

[php]
include("file.php");
echo $html_template;
[/php]

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> Doing this with PHP would be easy, and doing it with frames would be evil. All you would have to do with PHP is include a file with the html template in it. something like :


I think it would make more sense for the nav bar to be in the include.

---

### Post by -grubby on 2008-07-13
> **LaRoza said:**
> I think it would make more sense for the nav bar to be in the include.

Oh, so something like :

**file.php**
[php]
$html_template = "<!-- Navbar code -->";  
echo $html_template;
[/php]

Then calling it :
[php]
include("file.php");
[/php]

---

### Post by Phristen on 2008-07-13
> It will be standard code?I take it OP is more concerned about simplicity, than adhering to standards.
That said, SSI/PHP/etc. would be simpler yet, but then --- we can't use external programs :)

P.S.> Then calling it :
[php]
include("file.php");
[/php]<? include("file.php"); ?> would be more like it, if you are inserting it in the middle of html.
Or better yet, just have a plain text file with navigation bar in it, and print it using [php]<?=get_file_contents("file.htm");?>[/php]

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> Oh, so something like :


No...

```

<!--Navigation links in file named "links.inc"-->
<ul>
<li><a href="#" title="Title">Link</a></li>
<li><a href="#" title="Title">Link</a></li>
<li><a href="#" title="Title">Link</a></li>
<li><a href="#" title="Title">Link</a></li>
</lu>

```

Then just include it whenever it is needed.

[php]
<html>
    <head>
        <title>Title</title>
    </head>
    <body>
    <?php require_once("includes/links.inc");?>
    <!--Page here -->
    </body>
</html>
[/php]

> **Phristen said:**
> I take it OP is more concerned about simplicity, than adhering to standards.

Invalid isn't an option, at least, when you are learning. It is a shame browsers are so tolerant. The web would be so much more useful if it were all valid.

> 
That said, SSI/PHP/etc. would be simpler yet, but then --- we can't use external programs :)

External programs? Like a frames aware browser?

---

### Post by shoagun on 2008-07-13
Thanks for the tips!  I think SSI might be the way to go.  I'll look into using frames as well, but I think SSI might be a tad simpler.  

I think it's odd that this basic function was never built into HTML.  I understand why you'd want a scripting language to do dynamic implementations, but for my case, it's actually static in a sense.  The navigation bar doesn't every vary.  If it's possible to href an image or a style sheet, it seems like it should be possible to href another html file somehow.

---

### Post by LaRoza on 2008-07-13
> **shoagun said:**
> 
I think it's odd that this basic function was never built into HTML.  I understand why you'd want a scripting language to do dynamic implementations, but for my case, it's actually static in a sense.  The navigation bar doesn't every vary.  If it's possible to href an image or a style sheet, it seems like it should be possible to href another html file somehow.

Because HTML is based on SGML (XHTML on XML) and such things have no place in static pages.

There is a way, sort of, but it doesn't work.

---

### Post by Phristen on 2008-07-13
> Invalid isn't an optionAhh... Borg always looking for perfection ;)> Because HTML is based on SGML Well, that explains it! ;)

---

### Post by -grubby on 2008-07-13
> **LaRoza said:**
> No...

```

<!--Navigation links in file named "links.inc"-->
<ul>
<li><a href="#" title="Title">Link</a></li>
<li><a href="#" title="Title">Link</a></li>
<li><a href="#" title="Title">Link</a></li>
<li><a href="#" title="Title">Link</a></li>
</lu>

```

Then just include it whenever it is needed.

[php]
<html>
    <head>
        <title>Title</title>
    </head>
    <body>
    <?php require_once("includes/links.inc");?>
    <!--Page here -->
    </body>
</html>
[/php]


Invalid isn't an option, at least, when you are learning. It is a shame browsers are so tolerant. The web would be so much more useful if it were all valid.



External programs? Like a frames aware browser?


You can include html files with php? I thought you could only include php files. Otherwise I'd probably be doing it that way

---

### Post by -grubby on 2008-07-13
> **Phristen said:**
> Ahh... Borg always looking for perfection ;)Well, that explains it! ;)

Speaking of imperfection, I've started to slack off lately on valid xhtml 1.1 code..

---

### Post by LaRoza on 2008-07-13
> **Phristen said:**
> Ahh... Borg always looking for perfection ;)
No. You don't see C programmers writing invalid code. You don't see Python programmers writing invalid code. You don't see invalid XML (try it, with a modern browser you'll get an error). Browsers tolerate way too much. That is bad. It reduces the quality of code and makes the majority of browser code designed to handle ambigious code. It is a mess.

An no, Borg don't look for perfection, I just move the definition of perfection up. The Borg is Perfection.

> 
Well, that explains it! ;)

SGML and XML are meta-languages, which means they are rules that other language uses. SGML is just a way of having a format. It would be like critising Ascii for not including Devanagari.

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> Speaking of imperfection, I've started to slack off lately on valid xhtml 1.1 code..

"Failed validation, 7 Errors"

Get with it!

---

### Post by -grubby on 2008-07-13
> **LaRoza said:**
> "Failed validation, 7 Errors"

Get with it!

I'm so ashamed, I actually changed the Doctype so it would have less errors.

With XHTML 1.1 set I get 18 errors!!

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> I'm so ashamed, I actually changed the Doctype so it would have less errors.

With XHTML 1.1 set I get 18 errors!!

You have silly mistakes in there...

Speaking of web sites, I updated mine. Check it out :-)

This is new! (Not validated, I had enough trouble with the unicode and actually programmed my own editor just to make that form) [http://laroza.freehostia.com/home/apps/hindi/index.php?p=first](http://laroza.freehostia.com/home/apps/hindi/index.php?p=first)

---

### Post by -grubby on 2008-07-13
Wow, almost every error is due to the search box. And, nice. Too bad I don't have any use for it. Also, My site is undergoing an upgrade (as I seem to do every month). Could you check this [Drop down menu](http://grubbn.com/test) out please? 

Also, I think we've highjacked this thread

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> Wow, almost every error is due to the search box. And, nice. Too bad I don't have any use for it. Also, My site is undergoing an upgrade (as I seem to do every month). Could you check this [Drop down menu](http://grubbn.com/test) out please? 

Also, I think we've highjacked this thread

You can't even do valid BBCode :-(

It is some sloppy and invalid code. You should fix it so that all the script is not in the markup.

---

### Post by ad_267 on 2008-07-13
> **nathangrubb said:**
> You can include html files with php? I thought you could only include php files. Otherwise I'd probably be doing it that way

It is a php file. Just one without any "<?php" or "?>" in it!

---

### Post by -grubby on 2008-07-13
> **LaRoza said:**
> You can't even do valid BBCode :-(

It is some sloppy and invalid code. You should fix it so that all the script is not in the markup.

Yeah, but I didn't even make the script. Should I learn EMCAscript?

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> Yeah, but I didn't even make the script. Should I learn EMCAscript?

Yes, or not use it ;)

You don't want to be a code monkey, copying and pasting.

[img]http://hackles.org/strips/cartoon37.png[/img]

> **nathangrubb said:**
> You can include html files with php? I thought you could only include php files. Otherwise I'd probably be doing it that way

You can include anything. It just dumps what is there into the file, and then all of that is parsed as one.

---

### Post by -grubby on 2008-07-13
> **LaRoza said:**
> Yes, or not use it ;)

You don't want to be a code monkey, copying and pasting.

You can include anything. It just dumps what is there into the file, and then all of that is parsed as one.

But copying and pasting sounds like a fun game! That is, until I'm expected to do anything coherent with it

---

### Post by shoagun on 2008-07-13
On second thought, I think I might just hack this.... For some reason, I feel inclined to keep everything entirely in HTML.  I think I'll write a "template.html" file with the basic format for each page (navbar, etc), and then just write a perl script to "update" all other .html files based on the template.  That way if I want to edit the format, I can just edit the template and then use my script to apply the edits to all the other pages.

---

### Post by LaRoza on 2008-07-13
> **shoagun said:**
> On second thought, I think I might just hack this.... For some reason, I feel inclined to keep everything entirely in HTML.  I think I'll write a "template.html" file with the basic format for each page (navbar, etc), and then just write a perl script to "update" all other .html files based on the template.  That way if I want to edit the format, I can just edit the template and then use my script to apply the edits to all the other pages.

I do that also; use scripts to write static code for me. It works.

---

### Post by -grubby on 2008-07-13
> **shoagun said:**
> On second thought, I think I might just hack this.... For some reason, I feel inclined to keep everything entirely in HTML.  I think I'll write a "template.html" file with the basic format for each page (navbar, etc), and then just write a perl script to "update" all other .html files based on the template.  That way if I want to edit the format, I can just edit the template and then use my script to apply the edits to all the other pages.

What inclines you to do that? If you did it with PHP you could just edit one file and the every page the navbar was referred from would change. You wouldn't have to write a whole script to update the rest of the files.

---

### Post by shoagun on 2008-07-13
> **nathangrubb said:**
> What inclines you to do that? If you did it with PHP you could just edit one file and the every page the navbar was referred from would change. You wouldn't have to write a whole script to update the rest of the files.

One "practical" motivation is that I'd like to be able to put my site content on a thumb drive and then plug it into any computer and edit it and view it locally.  Using PHP or SSI would require the computer to have Apache installed.  The other motivation is more idealistic.  It's a very simple site with simple content.  I don't see a need to have to include any scripting.  If I ever wanted to hand the site over to someone else to maintain, I'd rather they only had to learn basic HTML and learn basic HTML and basic PHP.

---

### Post by LaRoza on 2008-07-13
> **shoagun said:**
> One "practical" motivation is that I'd like to be able to put my site content on a thumb drive and then plug it into any computer and edit it and view it locally.  Using PHP or SSI would require the computer to have Apache installed.  The other motivation is more idealistic.  It's a very simple site with simple content.  I don't see a need to have to include any scripting.  If I ever wanted to hand the site over to someone else to maintain, I'd rather they only had to learn basic HTML and learn basic HTML and basic PHP.

[http://portableapps.com/apps/development/xampp](http://portableapps.com/apps/development/xampp)

---

### Post by -grubby on 2008-07-13
> **shoagun said:**
> One "practical" motivation is that I'd like to be able to put my site content on a thumb drive and then plug it into any computer and edit it and view it locally.  Using PHP or SSI would require the computer to have Apache installed.  The other motivation is more idealistic.  It's a very simple site with simple content.  I don't see a need to have to include any scripting.  If I ever wanted to hand the site over to someone else to maintain, I'd rather they only had to learn basic HTML and learn basic HTML and basic PHP.

And perl isn't scripting?

EDIT: Or Laroza's link works too

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> And perl isn't scripting?

She said Perl would be used to write the static files, not used on the site.

---

### Post by -grubby on 2008-07-13
> **LaRoza said:**
> She said Perl would be used to write the static files, not used on the site.

ah. I didn't catch that part apparently

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> ah. I didn't catch that part apparently

I do it a lot, for doing longer forms. Check out the IATA quizes on my site, I didn't type all that by hand! I use Python to do it.

The Devanagari one is based on the same code, but unfortunately, Python didn't support Unicode so I had to do some weird things to do all that. In the end, I wrote my own editor...

---

### Post by -grubby on 2008-07-13
> **LaRoza said:**
> I do it a lot, for doing longer forms. Check out the IATA quizes on my site, I didn't type all that by hand! I use Python to do it.

The Devanagari one is based on the same code, but unfortunately, Python didn't support Unicode so I had to do some weird things to do all that. In the end, I wrote my own editor...

How did you use Python to do it? I'm guessing you wrote some sort of script where you entered in the full name of the airline, it took the first letters of each word and used those for prefixes, and also wrote all the form buttons

---

### Post by LaRoza on 2008-07-13
> **nathangrubb said:**
> How did you use Python to do it? I'm guessing you wrote some sort of script where you entered in the full name of the airline, it took the first letters of each word and used those for prefixes, and also wrote all the form buttons

I had a list of the codes/answers and I used the list to make the markup with a simple loop.

---

### Post by -grubby on 2008-07-13
> **LaRoza said:**
> I had a list of the codes/answers and I used the list to make the markup with a simple loop.

ah, that makes sense

EDIT: Now that I think of it.. that would be useful in many cases

---

