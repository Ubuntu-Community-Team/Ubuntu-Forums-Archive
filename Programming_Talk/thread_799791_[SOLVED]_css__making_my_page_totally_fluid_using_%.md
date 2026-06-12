---
title: "[SOLVED] css : making my page totally fluid using %s"
date: 2008-05-19
forum: Programming Talk
---

### Post by anfractuosities on 2008-05-19
I am trying to make my page resizable for various screen sizes and resolutions.  It is mostly graphics, arranged using divs.  I have been trying many ways to make it resize.  

this works great, except the images get very distorted when the window is square, or any other shape then what it was originally designed as.

```

#tree{
position:absolute;
bottom:0;
right:45%;
width:8%;
height:35%;
}

#tree img{
width:110%;
height:100%;
}

```

I tried making one of the image dimensions auto, but this causes scroll bars to appear at certain window proportions.  Is this a problem that I have to work out with javascript?  or can I accomplish it in css?

---

### Post by mashcaster on 2008-05-19
Change 1 dimension only, the other should follow.

---

### Post by anfractuosities on 2008-05-19
I did this, but the image ends up protruding from the containing div and causing scroll bars to appear.


K... i figed it out...I need to specify only one dimension for both the containing div and the image.  Thanks

---

### Post by mashcaster on 2008-05-19
Seems to work for me:

[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-Strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
	<head>
		<title></title>
		<meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
	</head>
	
	<body>
	        <div style="width:50%;border:solid 1px black;">
			<img src="http://ubuntuforums.org/images/misc/ubuntulogo.png" style="width:100%;"></img>
            	</div>
	</body>
</html>[/HTML]

---

### Post by mashcaster on 2008-05-19
Ah, I posted to late.  Good to know you sorted it.

---

