---
title: "Anchor text?"
date: 2015-06-13
forum: Programming Talk
---

### Post by satimis on 2015-06-13
Hi all,

Anchor text?  I don't know the exact term which I'm looking.

I expect providing an exact URL to reader so that on clicking it he/she will immediately browse the topic on a web page instead of reading from the top of that page to find the topic.

For example on;
[http://bakery.satimis.com/diabetes-friendly-bread/](http://bakery.satimis.com/diabetes-friendly-bread/)

there are several recipes.  What will be the URL for 3) Bread, Whole Wheat Bread?

Thanks

Regards
satimis

---

### Post by ofnuts on 2015-06-13
The target page must have an anchor tag with a name:
```

<a name="some_name"> 

```
And you provide a URL with that name in the page that refers to it:
```

<a href="http://somewhere/some/page.html#some_name">

```

---

### Post by satimis on 2015-06-13
> **ofnuts said:**
> The target page must have an anchor tag with a name:
```

<a name="some_name"> 

```
And you provide a URL with that name in the page that refers to it:
```

<a href="http://somewhere/some/page.html#some_name">

```
Hi,

Thanks for your advice.

Where to put the anchor tag?
```

....
....
<span style="color: #ff0000;"><strong>3)</strong></span>
<span style="color: #ff0000;"><strong>Bread, Whole Wheat Bread</strong></span>
Number of Servings: 14 (1-1/2 lbs)
....
....

```

Regards
satimis

---

### Post by Lars Noodén on 2015-06-14
There are two [anchor elements](http://www.w3.org/TR/html4/struct/links.html#edef-A) here:

[list]
[*]<a href="http://somewhere/some/page.html#some_name">
[*]<a name="some_name"></a>
[/list]

The first one, the one with the *href* attribute, goes on the page you want to link **from**

The second one, the one with the *name* attribute, goes on the target page exactly at the point where you want the browser to start displaying.  It's more obvious in a long page.  If you put just the URL in the first anchor (with href attribute) then the browser goes to the top of the page. e.g. [http://groklaw.net/staticpages/index.php?page=ComesExhN05](http://groklaw.net/staticpages/index.php?page=ComesExhN05)
By adding a direction to an anchor with a name attribute, the browser will go straight to where that named anchor is.  e.g. [http://groklaw.net/staticpages/index.php?page=ComesExhN05#E2456](http://groklaw.net/staticpages/index.php?page=ComesExhN05#E2456)

So for your whole wheat bread, if you add something like this:
```

<p>&nbsp;<br />
**<a name="wholewheatbread3"></a>**
<span style="color: #ff0000;"><strong>3)</strong></span><br />
<span style="color: #ff0000;"><strong>Bread, Whole Wheat Bread</strong></span><br />
Number of Servings: 14 (1-1/2 lbs)</p>
<p><span style="color: #3366ff;"><strong>Ingredients</strong></span></p>
<ul>
...

```

Then this link should bring you right to that recipe:
```

http://bakery.satimis.com/diabetes-friendly-bread/#wholewheatbread3

```

A [*name* attribute must start with a letter](http://www.w3.org/TR/html4/types.html#type-name) but can  then include numbers or hyphens, underscores, colons, and periods, but nothing else.

Two side notes: One is that you could use instead of a separate anchor with a name attribute (*<a name=*) you could simply add an [id](http://www.w3.org/TR/html4/struct/global.html#adef-id) attribute to an existing element.  The second is that in the long run, it is a lot easier to do formatting and layout with external [Cascading Style Sheets](http://www.w3.org/TR/REC-CSS1/) (CSS).  This is especially true as the site grows or changes.  With the 1995 style HTML formatting, changes have to be done more or less manually and instance by instance.  With CSS it is enough to change one line and all recipe titles get changed (if it is set up that way) or ingredients lists or anything else for that matter.

---

### Post by satimis on 2015-06-14
Hi Lars,

Lot of thanks for your help with detail explanation.

> **Lars Noodén said:**
> There are two [anchor elements](http://www.w3.org/TR/html4/struct/links.html#edef-A) here:

[list]
[*]<a href="http://somewhere/some/page.html#some_name">
[*]<a name="some_name"></a>
[/list]

The first one, the one with the *href* attribute, goes on the page you want to link **from**

Whether for creating a link on that page?

> 
The second one, the one with the *name* attribute, goes on the target page exactly at the point where you want the browser to start displaying.  It's more obvious in a long page.  If you put just the URL in the first anchor (with href attribute) then the browser goes to the top of the page. e.g. [http://groklaw.net/staticpages/index.php?page=ComesExhN05](http://groklaw.net/staticpages/index.php?page=ComesExhN05)
By adding a direction to an anchor with a name attribute, the browser will go straight to where that named anchor is.  e.g. [http://groklaw.net/staticpages/index.php?page=ComesExhN05#E2456](http://groklaw.net/staticpages/index.php?page=ComesExhN05#E2456)

So for your whole wheat bread, if you add something like this:
```

<p>&nbsp;<br />
**<a name="wholewheatbread3"></a>**
<span style="color: #ff0000;"><strong>3)</strong></span><br />
<span style="color: #ff0000;"><strong>Bread, Whole Wheat Bread</strong></span><br />
Number of Servings: 14 (1-1/2 lbs)</p>
<p><span style="color: #3366ff;"><strong>Ingredients</strong></span></p>
<ul>
...

```

Then this link should bring you right to that recipe:
```

http://bakery.satimis.com/diabetes-friendly-bread/#wholewheatbread3

```

A [*name* attribute must start with a letter](http://www.w3.org/TR/html4/types.html#type-name) but can  then include numbers or hyphens, underscores, colons, and periods, but nothing else.


It works for me skipping to that recipe immediately on the browser.

> 
Two side notes: One is that you could use instead of a separate anchor with a name attribute (*<a name=*) you could simply add an [id](http://www.w3.org/TR/html4/struct/global.html#adef-id) attribute to an existing element.  The second is that in the long run, it is a lot easier to do formatting and layout with external [Cascading Style Sheets](http://www.w3.org/TR/REC-CSS1/) (CSS).  This is especially true as the site grows or changes.  With the 1995 style HTML formatting, changes have to be done more or less manually and instance by instance.  With CSS it is enough to change one line and all recipe titles get changed (if it is set up that way) or ingredients lists or anything else for that matter.
Whether you meant <div id="main"> ?
Before on googling I came across it but I couldn't resolve where I can locate it on that page with Firebug.

I have tried follow;
Start Firebug

Under HTML (on left column)

expand "<body class="page page-id-814 page-template-default logged-in admin-bar custom-background single-author singular two-column right-sidebar customize-support">"

under "<div id="page" class="hfeed">"
I found <div id="main">

But I have no idea whether it that one.  Neither I know how to append that ID to the URL with a hash character in front.

Regards
satimis

---

### Post by Lars Noodén on 2015-06-14
> **satimis said:**
> 
Whether you meant <div id="main"> ?  That's one pre-existing *id* attribute.  There are many others so you would have to add the ones you need.  It's about the same work as adding the anchors:

```

**<div id="wholewheatbread3">**
<span style="color: #ff0000;"><strong>3)</strong></span><br />
<span style="color: #ff0000;"><strong>Bread, Whole Wheat Bread</strong></span><br />
Number of Servings: 14 (1-1/2 lbs)</p>
<p><span style="color: #3366ff;"><strong>Ingredients</strong></span></p>
<ul>
...
<span style="color: #ff00ff;">Total time                    4:28 hrs</span></p>
**</div>**

```

The *<p>&nbsp;</p>* is then not needed.

---

### Post by satimis on 2015-06-14
> **Lars Noodén said:**
> That's one pre-existing *id* attribute.  There are many others so you would have to add the ones you need.  It's about the same work as adding the anchors:

```

**<div id="wholewheatbread3">**
<span style="color: #ff0000;"><strong>3)</strong></span><br />
<span style="color: #ff0000;"><strong>Bread, Whole Wheat Bread</strong></span><br />
Number of Servings: 14 (1-1/2 lbs)</p>
<p><span style="color: #3366ff;"><strong>Ingredients</strong></span></p>
<ul>
...
<span style="color: #ff00ff;">Total time                    4:28 hrs</span></p>
**</div>**

```

The *<p>&nbsp;</p>* is then not needed.
Hi,

Made following change```

<div id="wholewheatbread3">
<span style="color: #ff0000;"><strong>3)</strong></span>
<span style="color: #ff0000;"><strong>Bread, Whole Wheat Bread</strong></span>
Number of Servings: 14 (1-1/2 lbs)

<span style="color: #3366ff;"><strong>Ingredients</strong></span>
<ul>
...

```

[http://bakery.satimis.com/diabetes-friendly-bread/#wholewheatbread3](http://bakery.satimis.com/diabetes-friendly-bread/#wholewheatbread3)
skip to that recipe on browser.

Thanks

Furthermore under <div id="main"> there are many others.  Please refers to photo attached.

How to use them?

satimis

---

### Post by Dimarchi on 2015-06-18
You are referring to the article elements, perhaps? They work just like  all other possible anchors if you want to link to them. That is, since  your document claims to be HTML5 compliant (so says the DOCTYPE), you could, for example,  write it like this...

```

<ul>
<li><a href="#post-814">Diabetes Friendly Bread</a></li>
</ul>

```

That should take you to the article with the id mentioned in that href attribute. Anchors  with name attributes are deprecated in HTML5 - they are still valid in  previous versions. Change href attribute according to your needs.

---

### Post by satimis on 2015-06-18
> **Dimarchi said:**
> You are referring to the article elements, perhaps? They work just like  all other possible anchors if you want to link to them. That is, since  your document claims to be HTML5 compliant (so says the DOCTYPE), you could, for example,  write it like this...

```

<ul>
<li><a href="#post-814">Diabetes Friendly Bread</a></li>
</ul>

```

That should take you to the article with the id mentioned in that href attribute. Anchors  with name attributes are deprecated in HTML5 - they are still valid in  previous versions. Change href attribute according to your needs.
Advice noted.  Thanks

satimis

---

### Post by Lars Noodén on 2015-06-18
> **Dimarchi said:**
> You are referring to the article elements, perhaps? They work just like  all other possible anchors if you want to link to them. That is, since  your document claims to be HTML5 compliant (so says the DOCTYPE), ...

Thanks Dimarchi.  I did not spot the HTML5 declaration when writing the advice above.  I guess HTML5 is  now valid since last October.  However, the [Document Type Declaration for HTML5](dev.w3.org/html5/html-author/#doctype-declaration) is quite strange, probably the MS influence.  Nothing to differentiate it from the upcoming HTML 5.1.  The declaration doesn't say anything about HTML 5 at all only  this, with no link to the authoritative DTD:  :(

```

<!DOCTYPE html>

```

Instead of something like this:

```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

```

or this

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

```

So it turns out the site is using [HTML5](http://www.w3.org/TR/html5/) and not HTML4 / XHTML, so [the *<a name=...* method should be avoided](http://www.w3.org/TR/html5/obsolete.html) and the *... id= ...* method should be used instead.

---

