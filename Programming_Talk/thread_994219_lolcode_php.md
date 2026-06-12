---
title: "lolcode php"
date: 2008-11-26
forum: Programming Talk
---

### Post by rtoot3 on 2008-11-26
I love finding new programming languages to learn, and i was browsing ubuntu forums and found a thread that was trying to say "hello ubuntu" in every programming language there is. and on page five, somone posted one called lolcode and it looked like this:

```

HAI
CAN HAS STDIO?
I HAS A VAR
VISIBLE "what is yr name?"
GIMMEH VAR
VISIBLE "HAI " N VAR N "! Welcome to Ubuntu
KTHXBYE

```

i love lol cats and i thought this would be a fun programming language to learn. i researched it and found out its a real programming language. i found out how to use it and all that, but ussually i like proggraming stuff for websites, rather than desktop apps. so i looked around on the lolcode website(lolcode.com) and found a php parser! yay! here it is.
[http://www.tetraboy.com/lolcode/index.lol]("http://www.tetraboy.com/lolcode/index.lol")
now here is my problem:
i dont know what a parser is or how to use it
can someone go to that link, and give me as detailed instructions about what files to upload to my site, and where i should upload them please?
also, if i use lol code, can i still use php in my lolcode in case there is some stuff lolcode cant do?

also if you want to see the thread i was on
it here:
[http://ubuntuforums.org/showthread.php?t=497579&highlight=jquery&page=5](http://ubuntuforums.org/showthread.php?t=497579&highlight=jquery&page=5)
its a pretty interesting thread.

EDIT:
heres extra info that i should have posted earlier
> **namegame said:**
> A little self-motivation will get you far.

From the page you linked:



Link to the zip file:
[LOL Code PHP parser ZIP!!]("http://www.tetraboy.com/lolcode/lolcode-0_2.zip")


Link to the source code:

[index.lol source code!!]("http://www.tetraboy.com/lolcode/index.lols")

If you want to be successful in programming, you need to learn to use the resources available to you. People won't always be there to spoonfeed you the information.

EVERYTHING I just gave you is on the page that you linked.

im already aware of all those things, the thing is that i already downloaded the zip file and it wouldnt extract, it just gave me errors. so i ust manually took all the files out and uploaded them to a test folder in my website. but now whenever i try to make a .lol file, it just displays all the code, and i just thought i was doing it wrong(sorry i should have put this info down to start with) anyway, anyone who can get it to work please post how you did it.

---

### Post by lukjad on 2008-11-26
Kewl! I like it.

---

### Post by rtoot3 on 2008-11-26
did you find out how to use it? i still dont know what to do
> **rtoot3 said:**
> 
can someone go to that link, and give me as detailed instructions about what files to upload to my site, and where i should upload them please?
also, if i use lol code, can i still use php in my lolcode in case there is some stuff lolcode cant do?
its a pretty interesting thread.

---

### Post by Reiger on 2008-11-26
From briefly looking at it.

The simple way would be a PHP entry point which loads a LOL code file into a string and feeds the string to the parser (simply call lol_core_parse() with your string as argument).

Then all it has to do is call eval() on the result.
[php]
<?php
require('parser.php');

/*
Somehow obtain the file name of the file to parse; call it $fname.
*/
echo eval(lol_core_parse(file_get_contents($fname)));

?>[/php]

---

### Post by snova on 2008-11-26
I don't think there is a complete implementation. They're still playing around with the idea, deciding on the syntax, and whatnot, from what I gather.

There is a list of implementations on the homepage: [http://lolcode.com/implementations/implementations]("http://lolcode.com/implementations/implementations")

Not all of them are necessarily equal.

Specifications (so far):

[http://lolcode.com/specs?idx=specs]("http://lolcode.com/specs?idx=specs")

---

### Post by rtoot3 on 2008-11-26
> **Reiger said:**
> From briefly looking at it.

The simple way would be a PHP entry point which loads a LOL code file into a string and feeds the string to the parser (simply call lol_core_parse() with your string as argument).

Then all it has to do is call eval() on the result.
[php]
<?php
require('parser.php');

/*
Somehow obtain the file name of the file to parse; call it $fname.
*/
echo eval(lol_core_parse(file_get_contents($fname)));

?>[/php]

im not very good at programming and still not getting it,
do you think you could just atatch all the files i need to make it work

---

### Post by rtoot3 on 2008-11-26
im very sure you can do it because on the website([http://www.tetraboy.com/lolcode/index.lol)he](http://www.tetraboy.com/lolcode/index.lol)he) claims that the website was coded with lolcode, and if you look at the url, the extension is .lol instead of .php or .html

---

### Post by rtoot3 on 2008-11-26
so eager to write in lolcode, yet too stupid to set it up :(

---

### Post by namegame on 2008-11-26
> **rtoot3 said:**
> 
do you think you could just atatch all the files i need to make it work

A little self-motivation will get you far.

From the page you linked:

> This page is actually scripted using LOL code and is using a database. You can see the LOL source of this page, and the PHP parser source linked above. Below is a demo of the parser's features. View the LOL code for usage.There is now a .zip you can use to code website in LOL code!!

Link to the zip file:
[LOL Code PHP parser ZIP!!]("http://www.tetraboy.com/lolcode/lolcode-0_2.zip")


Link to the source code:

[index.lol source code!!]("http://www.tetraboy.com/lolcode/index.lols")

If you want to be successful in programming, you need to learn to use the resources available to you. People won't always be there to spoonfeed you the information.

EVERYTHING I just gave you is on the page that you linked.

---

### Post by rtoot3 on 2008-11-26
> **namegame said:**
> A little self-motivation will get you far.

From the page you linked:



Link to the zip file:
[LOL Code PHP parser ZIP!!]("http://www.tetraboy.com/lolcode/lolcode-0_2.zip")


Link to the source code:

[index.lol source code!!]("http://www.tetraboy.com/lolcode/index.lols")

If you want to be successful in programming, you need to learn to use the resources available to you. People won't always be there to spoonfeed you the information.

EVERYTHING I just gave you is on the page that you linked.

i didnt mean i was that stupid, lol

im already aware of all those things, the thing is that i already downloaded the zip file and it wouldnt extract, it just gave me errors. so i ust manually took all the files out and uploaded them to a test folder in my website. but now whenever i try to make a .lol file, it just displays all the code, and i just thought i was doing it wrong(sorry i should have put this info down to start with) anyway, anyone who can get it to work please post how you did it.

---

### Post by rtoot3 on 2008-11-27
no ones got this to work?

---

### Post by namegame on 2008-11-27
> **rtoot3 said:**
> i didnt mean i was that stupid, lol


Sorry about that. I guess we had a bit of miscommunication.

Anyway, unfortunately, I am unable to help you out about the errors.

I'm on my Windows box for one, which I HATE for programming tasks.

And personally, I have no need for lolcode. I do think it's a great testament to the developers that they have been able to take such an entertaining subject and make it into something that could be "useful." I just don't have the time currently to devote to fun. (YAY school)

---

### Post by rtoot3 on 2008-11-27
thats ok, thanx anyway. i just have to keep tryin.

---

### Post by namegame on 2008-11-27
Now that I think of it, tomorrow is Thanksgiving here in the US, so I might have some time. I'll just host the site locally and see if I can get it running. If not, well, I'll just have to investigate. :)

---

### Post by Tony Flury on 2008-11-27
if your browser is just displaying the code, rather than the code being executed on the server, it suggests that the server has no idea what do with ".lol" files and is serving them 
as something like text/plain.

you said you got errors when you tried to extract the files - what errors did you get ? they might be important as to fguring why it does not work, as i think there is some server configuration that you need to do.

As a general rule it is always easier to post the actual error messages when you ask for help.

---

### Post by wmcbrine on 2008-11-27
> **rtoot3 said:**
> im not very good at programming and still not getting it,Honestly, I wouldn't bother with joke languages until you feel proficient in mainstream languages, no matter how amusing they seem.

---

### Post by rtoot3 on 2008-11-27
> **namegame said:**
> Now that I think of it, tomorrow is Thanksgiving here in the US, so I might have some time. I'll just host the site locally and see if I can get it running. If not, well, I'll just have to investigate. :)

Oh thanks! Happy thanksgiving! Im in the us too.

> **Tony Flury said:**
> if your browser is just displaying the code, rather than the code being executed on the server, it suggests that the server has no idea what do with ".lol" files and is serving them 
as something like text/plain.

you said you got errors when you tried to extract the files - what errors did you get ? they might be important as to fguring why it does not work, as i think there is some server configuration that you need to do.

As a general rule it is always easier to post the actual error messages when you ask for help.

Sorry about that.

```

checkdir error:  /home/ryland/Desktop/lolcode-0_2/lolcode-0_2 exists but is not directory
                 unable to process lolcode-0_2/index.lol.
checkdir error:  /home/ryland/Desktop/lolcode-0_2/lolcode-0_2 exists but is not directory
                 unable to process lolcode-0_2/index.php.
checkdir error:  /home/ryland/Desktop/lolcode-0_2/lolcode-0_2 exists but is not directory
                 unable to process lolcode-0_2/lolz.db.
checkdir error:  /home/ryland/Desktop/lolcode-0_2/lolcode-0_2 exists but is not directory
                 unable to process lolcode-0_2/lol_core.php.
checkdir error:  /home/ryland/Desktop/lolcode-0_2/lolcode-0_2 exists but is not directory
                 unable to process lolcode-0_2/readme.txt.
checkdir error:  /home/ryland/Desktop/lolcode-0_2/lolcode-0_2 exists but is not directory
                 unable to process lolcode-0_2/SQL.php.
checkdir error:  /home/ryland/Desktop/lolcode-0_2/lolcode-0_2 exists but is not directory
                 unable to process lolcode-0_2/STDIO.php.

```

> **wmcbrine said:**
> Honestly, I wouldn't bother with joke languages until you feel proficient in mainstream languages, no matter how amusing they seem.

When I said that I just meant that I've always had trouble setting up new ones. I'm good with php, and I can do a lot with c++(as long as I don't have to make a window), and Ive also done a few things with python, and I was programming with flex for a long time. also i haven't gone into JavaScript very much but i know basic JavaScript. but I'm just not good with setting new ones up.

---

### Post by rtoot3 on 2008-11-27
I'm back from thanksgiving dinner! and sad to see no new replies :(

---

### Post by MicahCarrick on 2008-11-28
> 
checkdir error:  /home/ryland/Desktop/lolcode-0_2/lolcode-0_2 exists but is not directory
unable to process lolcode-0_2/index.lol.

To get around those errors and extract the archive in Ubuntu, open it with the archive manager and click the extract button. Then choose a folder to extract it to and _uncheck the box that says 'Re-create folders'_.

Then you can upload the extracted files to your web server and access .lol scripts (according to the readme) using something like:

[www.some-website.com/index.php?page=news](www.some-website.com/index.php?page=news)

Which would run news.lol and the index.lol is run by default.

---

