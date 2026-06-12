---
title: "[PHP] &quot;Unexpected T_WHILE&quot; error..."
date: 2008-10-12
forum: Programming Talk
---

### Post by fiddler616 on 2008-10-12
Hello,
This weekend (which happens to be four days for me), I'm trying to absorb as much PHP as possible to make my webpages a bit nicer.
I've already figured out (through a combination of common sense and Google) how to operate variable assignment, if statements and printing, but when I tried a while statement, I got:
> 
Parse error: syntax error, unexpected T_WHILE in /mnt/local/home/timmymacdonald/experimental.tmac.andrewmin.com/phptest.php on line 20
So I reread the tutorial, tried the alternate syntax, and still got the error.
So I copied and pasted the tutorial's example (from php.net, no less), which is this:[PHP]

while ($i <= 10) {
    echo $i++;  /* the printed value would be
                    $i before the increment
                    (post-increment) */
} [/PHP]
($i is already defined as 1)
And get the error. You can look at it for yourself [here]("http://experimental.tmac.andrewmin.com/phptest.php"), and I'm attaching my complete source (all .5KB of it) in case you find it useful. (Update: it's a .txt, since I'm not allowed to upload .php's, and am definitely not zipping it)(So just rename).
Thanks you.

---

### Post by cmay on 2008-10-12
i tested the test.txt on me and my brothers old site and it works after putting two } the right places. and a ; on line 19 and twenty. i cant copy and paste andything into this forums editor for some reason but maybe you can  let you see it here [http://brothersofmai.frac.dk/viewpage.php?page_id=4](http://brothersofmai.frac.dk/viewpage.php?page_id=4)

i have the file on the page so i can maybe upload it later when i find out why the forums editor do not work for me. i have a post in the forums feed back help about this subjekt. 
hope some one else can help you better.

---

### Post by cmay on 2008-10-12
[PHP]http://brothersofmai.frac.dk/viewpage.php?page_id=4

<HTML>
<HEAD>
<TITLE>
PHP Fun
</TITLE>
</HEAD>
<BODY>
<?php

$x = 1;
$i = 1;
if($x==1)
{
print("Yo, x is one!");
}
$x++;
if($x!=1){
	print("<BR> x is no longer one");
}
while ($i <= 10) {
    echo $i++;  /* the printed value would be
                    $i before the increment
                    (post-increment) */
}
/*Welcome Ubuntu forum reader. The following are lines of code I made up which wouldn't work, so I decided it was my mistake, and commented them out for future review. The above is copied from the tutorial.
*/
//
//I have no idea why the following doesn't work:
/*while($x<19) {
	x++;
	print("<BR>")
	print($x)
}
*/
//I have no idea why this doesn't work either:
/*
print "Hello World!"
*/
?>



</BODY>
</HTML>
[/PHP]
aha !!
there is a button where you can switch things on and off on the editor in this forums. 
hope it helps i am far from being a expert in anything and that goes for php too.

---

### Post by fiddler616 on 2008-10-12
> **cmay said:**
> i tested the test.txt on me and my brothers old site and it works after putting two } the right places. and a ; on line 19 and twenty. i cant copy and paste andything into this forums editor for some reason but maybe you can  let you see it here [http://brothersofmai.frac.dk/viewpage.php?page_id=4](http://brothersofmai.frac.dk/viewpage.php?page_id=4)

i have the file on the page so i can maybe upload it later when i find out why the forums editor do not work for me. i have a post in the forums feed back help about this subjekt. 
hope some one else can help you better.
That's no fun about the Forum not cooperating.
When I go to your URL, I get redirected to maintenance.php, not the right page :(
According to gedit, lines 19 and 20 are:
	[PHP]print("<BR> x is no longer one")

[/PHP]
(blank line after the print statement.)
And I'm not sure where to put the }s--I'm pretty sure that every { is matched with its own }, though I've definitely been known to be wrong.

---

### Post by cmay on 2008-10-12
sorry. but i did post the working version i just tested .
i am only admin at the site so i do not know why the forums do not cooperate. 
i was only tryin to be helpfull..

---

### Post by fiddler616 on 2008-10-12
> **cmay said:**
> 
aha !!
there is a button where you can switch things on and off on the editor in this forums. 
hope it helps i am far from being a expert in anything and that goes for php too.
Aha is right! It works beautifully, thank you!
I guess the moral to the story is to always use {}s for control flow, and the other moral is that sometimes errors are cause by something before the cited line. (In this case the un-bracketed if statement)(I think)

---

### Post by fiddler616 on 2008-10-12
> **cmay said:**
> sorry. but i did post the working version i just tested .
i am only admin at the site so i do not know why the forums do not cooperate. 
i was only tryin to be helpfull..
We seem to keep missing each other--posting while the other is writing.
But I will *always* appreciate somebody who's trying to help me on teh forums, and that person should never feel guilty about trying to help.
But it's all a moot point as it's solved--Yay!

---

### Post by cmay on 2008-10-12
great.
i spotted it on geany right away. it highligsts brackets and its great little editor for testing. so i was hopin i could let you see the results on the web but that missed a bit. i do not have full powers at the site so maybe thats why i could not let that happen. 
anyway happy to help and good luck.

---

### Post by howlingmadhowie on 2008-10-12
the problem is the missing semi-colon at the end of line 18.

---

### Post by fiddler616 on 2008-10-12
> **howlingmadhowie said:**
> the problem is the missing semi-colon at the end of line 18.
Good call. Python habits die hard. Especially when I want to keep them for my Python-ing :)
You wouldn't happen to have anything to say about the two different control flow-structures, one being:
[PHP]condition {
instructions
}[/PHP]
and the other being:
[PHP]condition:
    instructions
Not part of the condition[/PHP]
Would you? Is it purely stylistic?

---

### Post by howlingmadhowie on 2008-10-12
in general i prefer python's style in that it encourages good readable code. 
basically, if we use code formatting to help us work out what the code means, then a code parser can too. c-style languages (when formatted to be readable) contain redundant information.

however, the python language developers screwed up bigtime when they allowed tabs and spaces for white space at the beginning of a line. consider the case when someone sets their tab width to 6 and you have tab width on 8. suddenly code looks very odd and can even change its behaviour. the obvious solution is to allow spaces only as white space at the start of a line. this really ought to be mandated by the language, however.

---

