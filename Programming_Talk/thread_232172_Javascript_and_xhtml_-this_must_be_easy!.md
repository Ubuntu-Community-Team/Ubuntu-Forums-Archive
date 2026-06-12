---
title: "Javascript and xhtml -this must be easy!"
date: 2006-08-08
forum: Programming Talk
---

### Post by damianubuntu on 2006-08-08
Hi all
before I go spare banging my head on the wall, I thought I'd ask all you experts here this surely easy question: ;-)

Why does the following code work as html but not as xhtml?

I've taken this code from the examples at the excellent w3schools.com site.  The mouseover image change works fine when the doc is .htm, but the if I save as xhtml and reload in  the browser, the page displays fine, but no mouseover event occurs.

Any suggestions?

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<script type="text/javascript">
function mouseOver()
{
document.b1.src ="images/nanny.jpg"
}
function mouseOut()
{
document.b1.src ="images/qualifications.jpg"
}
</script>
</head>
<title>title</title>
<body>
<a href="http://www.w3schools.com" target="_blank"
onmouseover="mouseOver()"
onmouseout="mouseOut()">
<img border="0" alt="Visit W3Schools!"
src="images/qualifications.jpg" id="b1" />
</a>
</body>
</html>

```

Sorry to post all the code, but I'm so stuck for what must be an obvious thing that I thought it best to include it all.

Thanks for any help......

---

### Post by dabear on 2006-08-08
try to use document.getElementById('the_id_here').src instead

---

### Post by damianubuntu on 2006-08-09
Thanks,
it works!
Shame that all the tutorial sites I visited teach html, javascript and xhtml, but more or less in that order, so that the javascript is suitable for html but not xhtml  ....

thanks again

---

