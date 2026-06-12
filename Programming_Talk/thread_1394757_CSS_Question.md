---
title: "CSS Question"
date: 2010-01-31
forum: Programming Talk
---

### Post by Maheriano on 2010-01-31
I have a website and I'm trying to get 2 images to load side by side at the very top.

So at the top of the index.php page I added:
```
<div id="maxwell"></div>
```
Then in the CSS I added:
```

#maxwell {
width: 200px;

height: 70px;

background-image: url(maxwell.jpg);
margin: 0 0 0 800;

color: #000;
}
```

My 2 questions are:
1. How do I get this image to load aligned with the right side of my page? Basically I have my page set to cover 75% of the page and I want this image to line up with the right side of the layout on all resolutions.
2. How do I get another image to load next to it, lined up with the left side?

You can take a look at [www.xchangerealtygroup.com](www.xchangerealtygroup.com) to get a feel for it but it'll probably change soon as I keep working on it to figure it out. Thanks!

---

### Post by CyberJack on 2010-02-01
My css knowledge is not very good but:

1. You could add a "background-position: top right;" to your css to align the background image to the right top of you div.

2. You cannot get 2 background images in 1 div.
You can use 2 div's with there own background image. If you want 2 div's next to each other you need to know the width of both div's.
As your page width is 75%. I guess this is not an option.
You can also use 2 div's and let one float above the other (see example). 

[HTML]
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" dir="ltr" lang="en">
<head>
  <title>test page</title>
  <style type="text/css">
    #wrapper {
      margin: 0 auto;
      width: 75%;
    }
    #left {
      height: 70px;
      width: 100%;
      background: url('background_image_left.jpg') no-repeat top left;
    }
    #right {
      float: right;
      width: 200px;
      height: 70px;
      background: url('background_image_right.jpg') no-repeat top right;
    }
  </style>
</head>
<body>
  <div id="wrapper">
    <div id="left">
      <div id="right"></div>
    </div>
  </div>
</body>
</html>
[/HTML]

The problem with using page width in percentage is that the user can make the page really small.
When using the example above the right background image will float over the left which can result in a strange looking page when resizing.
I recommend using a fixed page width.

Hope this helps.

---

