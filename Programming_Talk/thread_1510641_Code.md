---
title: "Code"
date: 2010-06-15
forum: Programming Talk
---

### Post by cuberts on 2010-06-15
In normal site editors, how do you do the code wrapping thing like this:

```
How do you make it like this so that the code is inside the box
```
THanks

---

### Post by cuberts on 2010-06-15
```
you cant do it with normal code tags
```

---

### Post by trent.josephsen on 2010-06-15
I'm afraid you'll have to clarify a bit.  What do you mean by "normal site editors", and what "wrapping thing" are you referring to?  Neither of your code snippets wrap for me.

---

### Post by schauerlich on 2010-06-15
I think he means "how would you write the HTML for a [noparse][code][/noparse] box?"

---

### Post by trent.josephsen on 2010-06-15
Like putting a border around it?

CSS:
```
.codebox {
    border: 1px inset;
}
```

HTML:
```
<code class="codebox">
    This text will appear in a box with a 1-pixel border of type "inset".
</code>
```

That gives me a close approximation of this forum's code boxes.

---

### Post by cuberts on 2010-06-15
> **trent.josephsen said:**
> Like putting a border around it?

CSS:
```
.codebox {
    border: 1px inset;
}
```HTML:
```
<code class="codebox">
    This text will appear in a box with a 1-pixel border of type "inset".
</code>
```That gives me a close approximation of this forum's code boxes.But that will keep going and you will have to scroll across the page if it is a super long line

---

### Post by Krupski on 2010-06-16
> **cuberts said:**
> Thanks now I will mark this as a solved thread

You should use the <pre> tag (meaning pre-formatted text) and also use this style:

pre {
font-family: monospace;
white-space: pre-wrap;
}

"pre-wrap" will preserve whitespaces (as is necessary to properly display code), but if you have a super long line, it will wrap in your "codebox" rather than creating a giant horizontal scrollbar in the browser.

-- Roger

---

### Post by cuberts on 2010-06-16
> **Krupski said:**
> You should use the <pre> tag (meaning pre-formatted text) and also use this style:

pre {
font-family: monospace;
white-space: pre-wrap;
}

"pre-wrap" will preserve whitespaces (as is necessary to properly display code), but if you have a super long line, it will wrap in your "codebox" rather than creating a giant horizontal scrollbar in the browser.

-- RogerShould the code look something like this:
<html>
<head><title>Code</title></head>
<style type="text/CSS">
pre {
font-family: monospace;
white-space: pre-wrap;
}
</style>
<body>
<pre>This is where the code will go</pre>
</body>
</html>

---

### Post by Krupski on 2010-06-16
> **cuberts said:**
> Should the code look something like this:


To see what I mean (and what the "pre-wrap" thing does), copy-n-paste this HTML into a file, then open it with your browser.

Now, notice how the one comment line is very long. Move your mouse pointer into the box and watch the "pre-wrap" kick in. This should explain all.

```

<html>
<title>Code</title>
<head>
<style type="text/css">
pre {
	border: 1px solid #000000;
	padding: 0.5em;
	width: 50%;
	font-family: monospace;
}
pre:hover {
	white-space: pre-wrap;
}
</style>
</head>

<body>
<pre>
/* this is a sample of code inside pre tags */
	for (i=0; i<10; i++)
	{
		printf("Hello there\n"); /* note the preserved tabs */
	}
/* now we get a really long line of text that the pre tag would try to preserve the whitespaces for, but if it didn't wrap around at the end then it would make the window very wide and create a horizontal scrollbar. But, "pre-wrap" prevents this from happening. Instead the long text gets wrapped at the first appropriate whitespace (which is either a space or a tab) */
</pre>
</body>
</html>

```


Hope this helps...

-- Roger

---

### Post by crush304 on 2010-06-16
if you want to see how something works on an html page, right click on the page and select 'view page source' or 'view source'

---

### Post by cuberts on 2010-06-17
> **crush304 said:**
> if you want to see how something works on an html page, right click on the page and select 'view page source' or 'view source'Yes thanks for all the help that you are giving me, and yes I know that.

---

### Post by cuberts on 2010-06-17
> **Krupski said:**
> To see what I mean (and what the "pre-wrap" thing does), copy-n-paste this HTML into a file, then open it with your browser.

Now, notice how the one comment line is very long. Move your mouse pointer into the box and watch the "pre-wrap" kick in. This should explain all.

```

<html>
<title>Code</title>
<head>
<style type="text/css">
pre {
    border: 1px solid #000000;
    padding: 0.5em;
    width: 50%;
    font-family: monospace;
}
pre:hover {
    white-space: pre-wrap;
}
</style>
</head>

<body>
<pre>
/* this is a sample of code inside pre tags */
    for (i=0; i<10; i++)
    {
        printf("Hello there\n"); /* note the preserved tabs */
    }
/* now we get a really long line of text that the pre tag would try to preserve the whitespaces for, but if it didn't wrap around at the end then it would make the window very wide and create a horizontal scrollbar. But, "pre-wrap" prevents this from happening. Instead the long text gets wrapped at the first appropriate whitespace (which is either a space or a tab) */
</pre>
</body>
</html>

```
Hope this helps...

-- RogerCan you give me the code to do the prewrap thing, without having to take the mouse over the codebox? Because the long line just looks horrible when it is out of the code box.

---

