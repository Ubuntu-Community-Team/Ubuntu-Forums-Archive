---
title: "display external html list item in new page using php?"
date: 2009-10-04
forum: Programming Talk
---

### Post by esteeven on 2009-10-04
I am building a web page and, as is becoming increasingly routine for me, I have bitten off more than I can chew. I am even finding it hard to describe what I want to do

mypage.html needs to display (possibly random) items from a list on another website.

In my confused mind, I imagine the process like this (forgive the fake code : I had real problems displaying code on an earlier post )

externalpage.html

<html>

<li> item one
<li> item two
<li> item three

</html>

mypage.html

<html>
<div>
<php>
I want to display <li> item (possibly random) here
</php>
</div>
</html>

The list item display will be part of a page and not the whole page.

FYI : the person who has asked me to build this site does the following. They log on to externalpage.html and add items to the list (a photograph of a house and a description). mypage.html needs to display list items as examples of what is in the list. The full list is available using an iframe on mypage2.html.

When I agreed to help build the site, I thought it was all going to be html. I know to ask questions now

---

### Post by NoaHall on 2009-10-04
First things first. Php is not declaired using <php> . It's <?php and ?>

What you want to do is 

<?php echo "<li>" . $listitem . "</li>"; ?>

By external, do you mean the webpage on a completely different site?

---

### Post by esteeven on 2009-10-04
Yes. You are right. My php tags were awful.:redface:


<?php echo "<li>"$listitem"</li>"; ?> This is exactly what I want to do, I think.

The list items that I want to display are on another website.

---

### Post by Reiger on 2009-10-04
Aside from the obvious security implications if you cannot trust the source of the content (and by this I mean you can also trust the source itself to be secure from attack); some ideas:

In order of &#8216;robustness&#8217;
[list="1"]
[*]Can you assume that the content can be treated as well-formed XML? In that case the answer is fairly trivial because you can use XSLT to extract relevant data; adapting to the precise structure of the document on the fly.
[*]Can you assume that you know where your data is (that is: can you assume a fixed structure)? In that case you can probably get away with loading the document into a DOMDocument object representation, then use that to extract data. Keep an eye on the necessary entity escape juggling!
[*]Can you assume fairly basic search criteria? In that case you might even be able to get away with a regular expression or similar ad-hoc approach. This is by far the less robust option which should only be used for such basic extraction operations as &#8216;all <li> elements in the document which contain just plain text&#8217;. Anything much more complicated and your regex will cost you not only much more time than full-blown XSLT stylesheets, it will also be far less reliable, certainly far less maintainable, and likely fail you at the first upgrade ...
[/list]

---

### Post by esteeven on 2009-10-04
<?php echo "<li>"$listitem"</li>"; ?>
What I don't understand in the above is how to get the $listitem data.

---

### Post by Reiger on 2009-10-04
Apart from the fact that there are 2 syntax errors in that statement...

... I was talking about an **approach** to extracting the data: not handing out ready-made code. Apart from security precautions; the rest is mostly implementation details anyone can look up on php.net anyways.

---

### Post by esteeven on 2009-10-04
> **Reiger said:**
> 
[*]Can you assume that you know where your data is (that is: can you assume a fixed structure)? In that case you can probably get away with loading the document into a DOMDocument object representation, then use that to extract data. Keep an eye on the necessary entity escape juggling!
[/list]


I think I can assume a fixed structure and I am just about able to follow the "loading into a DOMDocument" but I can only see this as a way of identifying the data location itself. 

My limited knowledge stops me seeing how I can use php to actually extract/get to that data. I take your point about searching php.net and I have been doing this : am I on the right track with file_get_contents ?

edit: nope. I hadn't understood the DOMDocument business but I do now. PHP can load the entire page as a DOMDocument and then I can extract / get to elements that I want to display because I have something I can extract from. Am I doing better??

---

