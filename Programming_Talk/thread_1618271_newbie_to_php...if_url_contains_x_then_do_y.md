---
title: "newbie to php...if url contains x then do y"
date: 2010-11-10
forum: Programming Talk
---

### Post by caradeporra on 2010-11-10
Ok,

  Wasn't sure where to turn.  I have basically no php experience.  While being a novice I do have a basic understanding of programming - just no experience(meaning if I see the code I can figure out what it does and modify it but don't know enough to write from scratch ;)

  Ok, to the point - I am trying to make my links for my simple html/css site in an include file so I can easily update/add/remove links and change it for all pages.  The problem is I also have classes so that when on one page that tab is all caps and a different color etc.  In an include file though I will need to code it to do that.

  Here is the current include file:
```
<ul>
<li class="normal"><a href="ContactUs.shtml"><img src="images/ContactUs.jpg" /></a></li>
<li class="normal"><a href="Upcoming.shtml">Upcoming Auctions</a></li>
<li class="normal"><a href="Seller.shtml">Seller Benefits</a></li>
</ul>
```

I am looking for something that would say - If current url == "ContactUs.shtml" then class="current"

Basically determine what page is active and make that class the "current" class.

Any help?
Thanks in advance!

Carade

---

### Post by l0rb on 2010-11-11
Are you looking for [HttpMessage::getRequestUrl](http://at.php.net/manual/en/function.httpmessage-getrequesturl.php) ?

---

### Post by caradeporra on 2010-11-11
After some googling this is what I came across:

```
<?php if ($_SERVER['REQUEST_URI']=='/Upcoming' ) {$Upcoming = 'active'} else {}? {echo $Upcoming} ?>
```

I declared the variable in advance to be 'normal'
```
<?php $Upcoming = 'normal' ?>
```
 and the code should change the variable to be 'active' if the url contains '/Upcoming'... I put the echo $Upcoming in there for debugging to see if it is changing that variable. Unfortunately it is changing that variable no matter what the url contains.

I also have not figured out how to take the
```
<li class="active/normal">
```
to insert the variable so that it would be
```
<li class="$Upcoming">
```

Can someone explain how to implement the php variable into that html/css statement?

thanks

---

### Post by Mmmbopdowedop on 2010-11-12
I think the easiest way, or the way I tend to use is like this;

You can declare the value of a variable in a url via ?variable=value

For example;

index.php?page=this

Would be able to be retrieved via php by;
[PHP]<?php

$page = $_GET['page'];

?>[/PHP]

So you'd do something like:

[PHP]<li class="<?php echo $page; ?>">adasdas</li>[/PHP]

It's a bit vague, but hopefully reading this will give you a better idea and something to toy around with.

---

### Post by caradeporra on 2010-11-14
Thank you so much sir!

That is exactly the tip I needed.  Got it all squared away with your get method and set up if statements and it is working like a charm.

5 stars for your answer and a million dollars - well, maybe not a million dollars.

* * * * *  5 STARS * * * *    (now 10!)

---

### Post by Sofia A on 2010-11-14
Hey [caradeporra]("http://ubuntuforums.org/member.php?u=552797") could you share the code you came up with, I'm trying to work a very similar thing, thanks!

---

