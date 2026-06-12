---
title: "css positioning help needed"
date: 2008-04-15
forum: Programming Talk
---

### Post by ELD on 2008-04-15
i have a site here [http://www.prxa.info/test/Untitled-1.html](http://www.prxa.info/test/Untitled-1.html) i need the top bar to be lined up in between the left and right borders, and to have the borders be on top of the top bar, can anyone help, should be simple?

Thanks! :D

---

### Post by mike_g on 2008-04-15
How about something like:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" 

"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Untitled Document</title>
<style type="text/css">
<!--
body 
{
	background-color: #B4A787;
}

div.top
{
	position: relative;
	background-color: #FFFFFF;
	background-image: url(top.jpg);
	background-repeat: repeat-x;
	float:left;
	margin-left: auto;
	margin-right: auto;
	width: 90%;
}

div.left 
{
	background-image: url(border-left.jpg);
	background-repeat: no-repeat;
	background-color: #FFFFFF;
	width: 13px;
	height: 100px;
	float:left;
}

div.right 
{
	background-image: url(border-right.jpg);
	background-repeat: no-repeat;
	background-color: #FFFFFF;
	width: 13px;
	height: 100px;
	float:left;
}
-->
</style></head>

<body>
<div class="left"></div>
<div class="top">dsfdf</div>
<div class="right"></div>
</body>
</html>
```

---

### Post by ELD on 2008-04-15
Thanks it ligns up but i need the top bar to be in line with the tops of the borders if you see what i mean

---

### Post by mike_g on 2008-04-15
Erm, not really. Do you mean setting the top divs height to 100px?

---

### Post by ELD on 2008-04-15
I got it now, i set the margin of the top div to 12px and it has aligned vertically the top to position with the sides, great work dude.

Juse a note, how can i get all 3 divs to stay centered?

Also how can i get the two side divs height to expand along with the top div?

---

