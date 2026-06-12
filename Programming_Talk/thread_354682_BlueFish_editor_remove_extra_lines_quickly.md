---
title: "BlueFish editor remove extra lines quickly?"
date: 2007-02-06
forum: Programming Talk
---

### Post by shane2peru on 2007-02-06
Hey, I started using BlueFish for my html editing.  Really nice, I'm really impressed with it as an all around editor even for other documents.  Very nice.  Anyway, I really need to clean up some html coding and wondered if someone here could help me.  I want to remove a bunch of empty lines in my html document.  It looks like this ```
<td>



</td>







blah blah







blaah blaah



```  ok you get the idea.  There is a lot of that.  Is there a way to quickly search and replace and two lines with just one line, or somehow get rid of all those extra lines?  It is an excessive amount, and I worked for about 30 minutes manually deleting them, and realized I only had about 2% of the page done.  I need specific instructions for BlueFish, or another editor in the repos.  I tried their regular expressions, but I'm not real familiar with reg expressions.  Thanks.

Shane

---

### Post by Ramses de Norre on 2007-02-06
You want to get rid of the whitespace? 
If so following command will do so:
```
sed -i file.html -e '/^$/d'
```
Make a backup of the file in case I missed something but I'm pretty sure it's correct.

---

### Post by shane2peru on 2007-02-06
> **Ramses de Norre said:**
> You want to get rid of the whitespace? 
If so following command will do so:
```
sed -i file.html -e '/^$/d'
```
Make a backup of the file in case I missed something but I'm pretty sure it's correct.
Thanks, but didn't work.  I was going to attach the web page, but it is pretty big.  Instead you can see it [here]("http://www.rices4peru.com/ESBible7.html"), just look at the coding.  I have cleaned up the top part some, but below there are horrible spaces.  It is only in the coding not the page, so you will need to 'view source'  Thanks for the help.

Shane

---

### Post by Ramses de Norre on 2007-02-06
Ok, I see I forgot something. New shot: ```
sed -e 's/[[:blank:]]//g' -e '/^$/d' -i file.html
```

---

### Post by shane2peru on 2007-02-06
> **Ramses de Norre said:**
> Ok, I see I forgot something. New shot: ```
sed -e 's/[[:blank:]]//g' -e '/^$/d' -i file.html
```

:lolflag: that was funny, it did a great job of removing spaces!!!  The page looked very bad though. (don't worry it was a copied file to test on.)  I don't think I want spaces removed, my bad, I think just the blank lines removed.  That is a really slick trick though, really fast!  Where can I find a list of reg expressions to use with that line?  That is what this is right ```
's/[[:blank:]]//g' -e '/^$/d'
```  just a regular expression?  What if I remove the [[:blank:]] tag, would that do the trick?  Thanks for the help.

Shane

---

### Post by Ramses de Norre on 2007-02-06
Ow right, now it removes _all_ whitespaces..
If you remove the [[:blank:]] part you'll end up with the same expression as the first one I gave you, my second line contained two separate regexps, both were indicated by "-e", the second one was the same as my first attempt and it wont work on lines containing whitespace in the beginning (hence the extra part).

Third attempt:
```
sed -e 's/^[ \t]*//' -e '/^$/d' -i file.html
```

(and I feel like my credibility decreases with each attempt.. :p)

---

### Post by shane2peru on 2007-02-06
> **Ramses de Norre said:**
> Ow right, now it removes _all_ whitespaces..
If you remove the [[:blank:]] part you'll end up with the same expression as the first one I gave you, my second line contained two separate regexps, both were indicated by "-e", the second one was the same as my first attempt and it wont work on lines containing whitespace in the beginning (hence the extra part).

Third attempt:
```
sed -e 's/^[ \t]*//' -e '/^$/d' -i file.html
```

(and I feel like my credibility decreases with each attempt.. :p)

No, you definitly were getting better with each attempt, 1st attempt nothing, 2nd attempt every white space was gone, and the 3rd attempt, Hooray!  we got it.  Somewhere, or some how it ate a little bit of coding, because the page doesn't look right, that could be because the css style sheet is not located right there?  I will check.  Thanks for the help.  That is a really efficient trick!  And the page loads much quicker too.  Thanks a bundle!

Shane

---

### Post by Ramses de Norre on 2007-02-06
Yeah sed is an amazingly powerful command, and my last line should first remove all leading tabs and spaces (the first regexp) and then delete all empty lines (the second regexp) I know almost nothing about html so I'm not sure whether one of those actions can change the look of the page..

And I'm glad it worked, my credibility got up again ;)

---

