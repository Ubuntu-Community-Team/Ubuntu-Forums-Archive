---
title: "Browsers and CSS"
date: 2011-12-20
forum: Programming Talk
---

### Post by CoffeeRain on 2011-12-20
Hi! I have a problem with browsers and CSS. When I used CSS to put something on the top left corner, I used
```

{float:left; clear:both; margin:0; padding:0;}
```
to put it there. In Firefox, it is a few lines down, but in someone's Safari that I checked it with, it is where it should be. Is this because of one of the attributes I used, or because I used the <p> tag? Thanks.

---

### Post by kamaji792 on 2011-12-21
Think we need to see a little bit more of your code.

I tried the following, with Firefox 8.0 on Ubuntu 10.04 and the text appeared top left:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
<title>XHTML Transitional 1.0</title>
<style type="text/css">
   p {float:left; clear:both; margin:0; padding:0;}
</style>
</head>

<body>

   <p>Some text</p>

</body>

</html>
```

Can I also recommend Firebug for CSS testing and development.  It allows you to edit/add CSS and see what it does to a web page.

atb k

---

### Post by CoffeeRain on 2011-12-21
I fixed it by putting it in a div and clearing the div. Thanks for the suggestion, I'll get that. :)

---

### Post by amingv on 2011-12-21
Although you already solved your problem, it is worth mentioning that different browsers may come with different default margins/paddings/borders for elements. For this reason it is sometimes useful to specify a

```

* {
    margin: 0px;
    padding: 0px;
    border: 0px;
}
```

rule so that you can individually specify margins, etc. across browsers in an uniform fashion.
If you don't want to use a wildcard you can replace * with the name of the offending tag(s) (in your case I assume it's <body>).

---

