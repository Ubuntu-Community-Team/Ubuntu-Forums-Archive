---
title: "html image problem"
date: 2010-11-14
forum: Programming Talk
---

### Post by rcayea on 2010-11-14
I am trying to figure out why the background image I have set to use on my website is ok, and where I want it in Google Chrome but in Firefox it is gigantic and not at all where I want it. Does anyone have any idea what might be causing this?

If you need some other information, such as code, I would be happy to provide it. 

Thanks,
Randy

---

### Post by Tony Flury on 2010-11-14
Post the following : 
1) the HTML segment where you set the background, 

2) any CSS styles that impact either the entire document or the relevant elements.

In general without seeing what you are doing, it is unlikely that anyone will be able to help.

---

### Post by rcayea on 2010-11-14
Here is the html code:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head><title> Tux and Pucks </title>ery 
<link rel="StyleSheet" type="text/css" href="index.css" />
</head>
<body bgcolor="ffffcc" font-family:sans-serif>
<table border="2" width="100%">
```

Here is my css code for said image:

```
 body {
  background-image: url("/images/banners/tuxandpuckslogo.png");
  background-repeat: no-repeat;
  background-size: 16%;
  background-position:top left;
  background-attachment:fixed;
}

```

I know my very amateur code is probably bad so go easy on me. :)

thanks,
Randy

---

### Post by Tony Flury on 2010-11-14
what size is the png file - and what is the url of the site ?

---

### Post by rcayea on 2010-11-14
my site is: [www.tuxandpucks.com](www.tuxandpucks.com)

the size of the file is 994kb.

---

### Post by epicoder on 2010-11-14
Your problem is a combination of the GIGANTIC proportions of your image (2398x2794) and that Firefox has only some support for CSS3.

"Unknown property 'background-size'.  Declaration dropped."

You could resize your image, or just not support FF.

---

### Post by rcayea on 2010-11-14
ok. thanks. 

Yup, I know my image is huge. I just figured (as I guess a newbie would) that if Chrome was up-to-date with CSS, why wouldn't firefox be.

---

### Post by austinprete on 2010-11-14
Ya, it's reasonable to assume Firefox should be at the same point with CSS3.  But with no official standard out a lot of browsers are holding off with full support, although we'll definitely see more along the way.

---

