---
title: "Website help, looks different in IE and FF"
date: 2007-09-12
forum: Programming Talk
---

### Post by mridkash on 2007-09-12
Hi, 
I'm a student and been building a web page for a project. 
I'm using fully open source apps for development and it is great.

The website looks good in Firefox, but when I open it in IE6 (installed on Ubuntu) The whole layout is disturbed. The CSS seems to misbehave in IE6.

This website uses CSS for layout and the design is inspired by the ubuntu forums website, ie resolution independent, easy to use.
It follows a tab style as common buttons appear as tabs on top and the selected tab merges with the background. 


The web page has been built according to w3 standards and also passes validation. 
Please take a look at the code and show me where I'm wrong. 
I'll be very thankful.

also, if possible, open this website in IE on Windows and tell if the problem exists.

archive attached.

Thanks

---

### Post by PaulFr on 2007-09-12
**[http://www.alistapart.com/articles/slidingdoors](http://www.alistapart.com/articles/slidingdoors)** and **[http://www.alistapart.com/articles/slidingdoors2](http://www.alistapart.com/articles/slidingdoors2)** would be a start point to consider.

For differences between IE and Firefox, Google (or insert search engine of choice) is your friend, but you could start with **[http://www.quirksmode.org/css/box.html](http://www.quirksmode.org/css/box.html)** and **[http://www.quirksmode.org/css/contents.html](http://www.quirksmode.org/css/contents.html)**. I have found **[http://www.w3schools.com/](http://www.w3schools.com/)** a good site to start. Hope this helps.

---

### Post by bigboy_pdb on 2007-09-12
I had problems with trying to use XHTML initially when I started creating web pages that were intended for all browsers.

According to XML standards your first line should be the XML declaration (which is the first tag in your file). Internet Explorer expects the first tag to be the DOCTYPE tag. If IE doesn't see the DOCTYPE tag as the first tag it will assume some default format. I'm not certain what its default format is, but it isn't one that matches the XHTML DTD.

I was able to fix the problem and to have strict XHTML that was reported as being valid according to the W3C's validator by using the following code at the top of my HTML files:

```

<!DOCTYPE html 
	PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	...

```

The only thing that you should need to change in your code is the first few lines so that the XML declaration is removed and the html tag is similar to the one that I have (although to be honest I'm not certain if changing the html tag is necessary or not because the only difference is the language settings). The DOCTYPE should be fine as it is and there is no need to add the meta tag because you already have it. Thus, you can try changing the top of your code to:

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

```

I would recommend making a copy of your HTML and Style Sheets in a new folder before making the changes. You might find that you'll need to make other changes to your style sheets as well (but hopefully that won't be necessary).

The W3C's validator can be found here:
[http://validator.w3.org/](http://validator.w3.org/)

---

### Post by Samhain13 on 2007-10-01
I wouldn't go for the "Transitional" DocType though.

If the HTML and CSS validate and show correctly in Firefox while using the Strict DocType, there may arise margin and padding issues once it's changed to Transitional, thus breaking the design in both Firefox and IE again.

If the removal of the XML prolog was enough to solve the problem, don't change the DocType any more. Some professionals actually even recommend not to include the XML prolog if one is serving XHTML as "text/html" rather than "application/xhtml+xml".

Anyway... :D

---

