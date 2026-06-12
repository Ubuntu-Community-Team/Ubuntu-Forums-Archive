---
title: "html help needed"
date: 2010-10-06
forum: Programming Talk
---

### Post by rcayea on 2010-10-06
Hey everyone,

I am fairly new to the whole html thing. It isn't too difficult to learn.

My question is, how do I make a square box in html? I have looked all over the net and I have found something about div and sand but I don't quite understand how to use those tags. 


I have attached a picture of what I am trying to do...I am trying to make the box on the left so that when someone clicks on the big box they will be taken to the page about linux.

Thanks,
Randy

---

### Post by johnl on 2010-10-06
Hi,

Sounds like what you are after is a 'two-column' approach.  
Take a look at [this site](http://www.456bereastreet.com/lab/developing_with_web_standards/csslayout/2-col/) which walks you through how to do this with (X)HTML and CSS.

---

### Post by Crazedpsyc on 2010-10-06
Divs are very good, or you could use a table

with divs:
```

<div align="left" style="width: 50%; height: 75%;"><img src="tux.png" /></div>
<a href="pucks.html"><div align="right" style="width: 50%; height: 75%;"><h1>pucks</h1></div></a> 
```with table:
```
<table border="1">
<tr>
<td style="width: 50%; height: 75%;"><img src="tux.ong" /></td>
<a href="pucks.html"><td style="width: 50%; height: 75%;"><h1>Pucks</h1></td></a>
</tr>
</table> 
```

---

### Post by rcayea on 2010-10-06
Thank you much! I will study your tips and let you know what I come up with. Thanks for the help!

---

### Post by Crazedpsyc on 2010-10-06
Your welcome, you may want to look at [http://www.w3schools.com/html/](http://www.w3schools.com/html/) for future help (although the forum is a great place too)

---

