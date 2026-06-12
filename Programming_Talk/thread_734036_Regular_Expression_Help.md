---
title: "Regular Expression Help"
date: 2008-03-24
forum: Programming Talk
---

### Post by MicahCarrick on 2008-03-24
I need some help coming up with a regular expression for use in a PHP script. What I need is to search for all occurances of a string ignoring case. Then, I need to insert text before and after the found string without effecting the original string.

For example, if I'm looking for "test", I would match "Test" and "TeSt" and insert text before and after said text without changing it's case.

Can anyone point me in the right direction? My regexp skills are minimal and I'm struggling.

---

### Post by themusicwave on 2008-03-24
Two ideas:

1) just convert the string to lower case before you check.  If case doesn't matter this could work.

Just make a copy of the whole string, convert it to lower and do your check.

2) Build a regular expression

you would need to build a regular expression with every lower and uppercase char in the string in quotes.

Like [TESTtest] that would match test Test TEST tEst...etc.  

Read this for more info:
[http://www.regular-expressions.info/quickstart.html]("http://www.regular-expressions.info/quickstart.html")

---

### Post by LaRoza on 2008-03-24
> **MicahCarrick said:**
> I need some help coming up with a regular expression for use in a PHP script. What I need is to search for all occurances of a string ignoring case. Then, I need to insert text before and after the found string without effecting the original string.

For example, if I'm looking for "test", I would match "Test" and "TeSt" and insert text before and after said text without changing it's case.

Can anyone point me in the right direction? My regexp skills are minimal and I'm struggling.

How are you going to insert text in two places without changing the original string? That is impossible.

---

### Post by themusicwave on 2008-03-24
I assumed he meant he was making a copy first, but I agree with Larozza if you insert something you changed it.

Perhaps you meant without changing the original string?

---

### Post by LaRoza on 2008-03-24
> **themusicwave said:**
> I assumed he meant he was making a copy first, but I agree with Larozza if you insert something you changed it.

Perhaps you meant without changing the original string?

After reading it, it seems like it shouldn't change the case of the text for which it is searching.

It looks like it is inserting hyperlinks into preexisting text, or possibly some other markup.

---

### Post by MicahCarrick on 2008-03-24
Exactly... sorry for the confusion.

I will be inserting a hyperlink around the word and want to ensure that the word inside the tag doesn't loose it's case.

So essentially, I am replacing the word but I'm replacing it with itself plus addition text before and after. I could do it with standard iteration but I figure regex would be much easier--if I knew what I was doing.

---

### Post by LaRoza on 2008-03-24
> **MicahCarrick said:**
> Exactly... sorry for the confusion.

I will be inserting a hyperlink around the word and want to ensure that the word inside the tag doesn't loose it's case.

So essentially, I am replacing the word but I'm replacing it with itself plus addition text before and after. I could do it with standard iteration but I figure regex would be much easier--if I knew what I was doing.

Maybe there is an easier solution: [http://www.php.net/manual/en/function.str-replace.php](http://www.php.net/manual/en/function.str-replace.php)

<edit> This is better for you: [http://www.php.net/manual/en/function.str-ireplace.php](http://www.php.net/manual/en/function.str-ireplace.php)

---

### Post by MicahCarrick on 2008-03-24
The problem with str_ireplace is that I won't be putting the same word back in. It will be case insensitive to FIND the word but I won't be able to put the word back exactly as it was.

Example:

$test = "This is a test";
echo str_ireplace('this', '<a href="#">this</a>', $test);

Now I lost the capital letter "T" in "This".

I'll be parsing a bit of text for which I'm looking for keywords which have definitions and thus will become links to popup windows.

---

### Post by MicahCarrick on 2008-03-24
I think I've got it...

```
$value = 'wolf';
        $replace = "<a class=\"js_popup\" onclick=\"showWordDefinition('$value')\">$1</a>";
        $parsed = preg_replace("/($value)/i", $replace, $text);
```

---

### Post by wrightee on 2008-03-24
That might break something - it doesn't account for text inside of angle brackets, text that's already inside of hyperlinks or partial words.  Your code would replace all the following instances of wolf if limit was set to -1, or just the first if otherwise:

<a href='wolfiwolf.com'>My wolf pictures</a> are wolf good.

.. which probably isn't what you want. Sorry I don't have a better solution just now.

---

### Post by MicahCarrick on 2008-03-24
Well, the good news is that the text is coming from a pure text database without markup. the bad news is that it's finding partial words. I'll later need to find a way to get it to know full words which will have to factor hyphens, whitespace, new lines, parenthesis, and symbols such as TM and copyright.

---

### Post by wrightee on 2008-03-24
Use \b in your regex for word boundary:

/\bwolf\b/ 

will match "my wolf" but not "wolfwolf"

I'm not sure how to accommodate hyphens etc, probably with escaping them.

Remember with a pure text database if you're adding definitions for more than one word, you'll might end up with matches inside of markup that has been added earlier in your loop.  You can avoid with a more complex regex that's outside my brain capacity tonight..  Good luck!

---

### Post by hums07 on 2008-03-25
sorry i messed up... so delete.

---

