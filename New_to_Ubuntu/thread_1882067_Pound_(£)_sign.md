---
title: "Pound (£) sign"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by john009 on 2011-11-16
As can be seen from the title, I can type the pound sign (shift+3).  However, I cannot get it to display on a web page that I have created and am viewing (locally) on the same machine (127.0.0.1/webpage.php).  What appears instead is this '¬' (without the quotes).  I've tried replacing the pound (£) sign within my code with '&pound' or '£' or £' (without quotes), but the same symbol continues to appear.

I have put the following within the <meta> tag:
http-equiv="Content-Type" content="text/html; charset=UTF-8".

As I understand it, the .htaccess file doesn't come into play unless one is accessing pages from the internet and not when viewing pages locally.  I don't have one on my system (up-to-date 10.10) anyway.

Additionally, when looking at the keyboard set-up, no keyboard option show the pound sign on shift+3 (or anywhere else), only the '¬' symbol.  My wife's laptop, using the same keyboard set-up options (UK Extended - Winkeys and keyboard model of Generic 105-key (Intl) PC) shows the pound sign at the shift+3 position.

I don't think it's charset related, as when I change UTF-8 to something else, the euro (&#8364;) is not printed either.

Any pointers/clues would be appreciated.

Edit: When I typed this, the pound signs that appear in the first paragraph, were entered as '&#onesixthree' and &#onesixthree;' (but digits, not text).

This problem appears in all the browsers I have loaded (Opera, Chrome, Firefox, Epiphany & Dooble).

---

### Post by andrew.46 on 2011-11-16
> **john009 said:**
>  I've tried replacing the pound (£) sign within my code with '&pound' or '£' or £' (without quotes), but the same symbol continues to appear.

Perhaps:

```
&pound**[COLOR="Red"];[/COLOR]**
```

or even:

```

&#163[B][COLOR="Red"];
[/COLOR][/B]
```

---

### Post by SheaMan on 2011-11-16
Wait, right, there it is. You have to make a charset declaration in the header of the html file. 
[http://en.wikipedia.org/wiki/Character_encodings_in_HTML](http://en.wikipedia.org/wiki/Character_encodings_in_HTML)

Which one I am not certain. But if you try a few of them :shrug: I would guess one that is 'British' ??

Whats happening is that while shift 3 produces the hash on an american keyboard and pound on the british the character produced by pressing shift 3 is not 'hash or pound' its a number that is correlated with a map of different characters. Often when a character is not recognized and it came from an american keyboard it is this odd lookin box thing. Apparently with these british boards you get ¬ instead. Note, I wonked this thing to get it to produce that character. There is a key that does not type what the picture is - it types ¬ instead. 

I am not 100% certain, but I am positive that if you change the charset declaration in your header - will work.

---

### Post by john009 on 2011-11-17
Thanks for your replies (andrew.46 & SheaMan).

Andrew, it makes no difference if the semi-colon (;) is present, though it's probably good practice to include it.

SheaMan, having read the Wiki page you referred to, I'm none the wiser.  You said that I "have to make a charset declaration in the header of the html file."  But a the Wiki page says, "For HTML it is possible to include this information inside the head element near the top of the document."  Which is what I have done, as stated in my original post.  My HTML script is as follows:

<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	<title>Metric</title>
<link rel="stylesheet" type="text/css" href="style.css" />
</head>

Or have I missed something there?

As far as I can see (or understand), from reading other related problems, UTF-8 is the correct charset to use.  I still think the problem is more likely to be some basic system setting that I'm missing (or is incorrect), but I'll be damned if I can find it!

---

### Post by andrew.46 on 2011-11-17
All seems a little odd. Here is a bare-bones page I have created using the pound sign correctly:

[http://www.andrews-corner.org/tmp/pound.html](http://www.andrews-corner.org/tmp/pound.html)

Perhaps look at the source and see if it differs from your own?

---

### Post by john009 on 2011-11-19
Thanks Andrew for your reply.

Your script displayed the £ sign on my system, which prompted me to look at where it was and was not being displayed!

All OK within any HTML header tags (H1, H2 etc) & <p></p>.  However, I was trying to display it within a drop-down list (i.e. select a currency).  Also, if I try to type the £ sign within an input field the ¬ symbol was produced.

Anyway, to cut a long story short, I changed the specified font from Califa (which _was_ also my system font) and low & behold the £ sign was displayed wherever required! It appears that the Califa font does not have, or produce the £ sign, whereas virtually every other font does!

I'll mark this this as solved/closed when I find out how!

Thanks again to you both for your time.

---

### Post by BlinkinCat on 2011-11-19
You can mark as solved with the thread tools at top of page.

---

### Post by andrew.46 on 2011-11-19
Good to hear the issue is resolved :). You might consider using a group of fonts in your css rather than a single font btw (using 'font-family') to avoid a few more font issues.

---

