---
title: "aligning content with div in CSS"
date: 2008-04-28
forum: Programming Talk
---

### Post by anfractuosities on 2008-04-28
I have a small background image that I want all my content to be positioned over.  I have created a div that will be the containing box for all my content, but I cannot seem to get it to center over the bg image.  Here is the relevant html and css.

```


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">

	<head>
		<title>UnSee</title>
		<link href="basic.css" type="text/css" rel="stylesheet" media="all" />
	</head>

	<body>
<div id="alignbox">
content
</div>
</body>
</html>
[/code

[code]
body {
background-color: black; 
background-image : url(bg.jpg); 
background-attachment: fixed;
background-position: center;
background-repeat: no-repeat;
}

#alignbox {
/* size of background image*/
width:700px;
height:525px;

position:fixed;
margin-left:50%;
margin-right:50%;
border: solid 3px red;
}

```

---

### Post by Hyperkill on 2008-04-28
It'd be easier to check for accuracy if you had provided the background image but here's what I got...

```


body {
background-color: black; 
background-image : url(bg.jpg); 
background-attachment: fixed;
background-position: center;
background-repeat: no-repeat;
text-align:center;
}

#alignbox {
/* size of background image*/
width:700px;
height:525px;
text-align:left;
margin:0px auto;
border: solid 3px red;
}

```

Note text-align:center is used to center the div while text-align: left is used to bring the content back to the standard left alignment.  text-align:center is also needed for IE to center the Div.

---

### Post by howlingmadhowie on 2008-04-28
you need:

```

position:absolute;
margin-left:50%;
margin-top:50%;
width:700px;
height:525px;
left:-350px;
top:-262px;

```

---

