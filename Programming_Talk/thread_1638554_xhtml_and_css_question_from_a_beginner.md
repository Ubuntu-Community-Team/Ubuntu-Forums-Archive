---
title: "xhtml and css question from a beginner"
date: 2010-12-05
forum: Programming Talk
---

### Post by rcayea on 2010-12-05
Hey everyone,

I am having trouble figuring out my problem. I can't seem to figure out why <h1> won't center on my website. I have attached the corresponding css file which I am trying to use to do the centering with. I am still trying to master the hierarchy of CSS so I suspect that could be the issue. Below is my code. If you get the chance to look over my code, please let me know what I am doing wrong. thanks, randy 


```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
<title> Tux and Pucks: Linux Hockey Music Poetry</title>
<link rel="StyleSheet" type="text/css" href="index.css" />
</head>

<body>
<h1>Linux, Hockey, Music, and Poetry All In One</h1>
<h2>Tux and Pucks<img src="images/banners/tuxandpucks.png>" /h2>
<h3><a href="../../webmail" target="_blank" title="Click To Access Email">Click Here For Email<a/ </h3>

<!--There is more code but i cut it out for this question-->

``````
body 
{
  background-image: url("/images/banners/stripes.png");
  background-repeat: "repeat-x";
  overflow:"hidden";
}

h1
{
text-align:"center";
}
```

---

### Post by Barrucadu on 2010-12-05
It's `text-align:center;`, not `"text-align:"center";`.

---

### Post by rcayea on 2010-12-05
thank you!

---

