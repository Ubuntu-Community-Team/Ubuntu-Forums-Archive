---
title: "HTML Images and tables"
date: 2012-12-15
forum: Programming Talk
---

### Post by checoimg on 2012-12-15
Hi I know this is not a programming language but I can't figure out another place for this question. I have a html file and it is displaying a image before a table and the table is typed before the image in the source.

Here is the source:


```
<!DOCTYPE html>
<html>
<head>
<title>W3C Schools test file</title>
<meta http-equiv="refresh" content="5">
<meta name="autor" content="checoimg@gmail.com">
<style type="text/css">
body {background-color:white;}
p {color:blue;}
</style>
</head>
<body>

<table border="1">
<tr>
<td text-aling="center"><h1 style="text-align:center;color:red"> This is a red centered heading</h1></td></tr>
<tr><td><h6>This is a heading</h6></td>
<td><p><em>This is a paragraph emphasized <del>deleted text<del></em></p></td>
<tr><td><p><b>This is paragraph in bold</b><p></td>
<td><p><code>#include "stdio.h"<br>
int main ()<br>
{<br>
printf("Hello everyone\n");<br>
return 0;<br>
}<br>
</code></p></td></tr>
<tr><td><p><abbr>ProMeATe</abbr></p></td>
<td><a href="https://www.plus.google.com"> Google + </a></td>
<br><img src="A.jpg" width="640" height="640">
</body>
</html>
```

---

### Post by Majorix on 2012-12-15
You should think about indenting your code. I have difficulty working out what you are trying to do. Also you should keep indenting your code no matter which language you use.

---

### Post by AstroLlama on 2012-12-15
you have to add a closing tag to end the table. so right before your image you should add

```
</table>
```

+1 on indenting code

---

### Post by trent.josephsen on 2012-12-15
True, but that's not the only mistake by a long shot.

[http://validator.w3.org](http://validator.w3.org)

---

### Post by checoimg on 2012-12-15
Thank you all for your time adding </table> solved the problem. If you guys can explain me what's indenting.

---

### Post by checoimg on 2012-12-15
This is the definition I found:

When referring to text, **indent** or **indentation** is the increase   or decrease of space between the left and right [  margin]("http://www.computerhope.com/jargon/m/margin.htm") of a paragraph. In many programs, an indent for the first line of   text can be created by moving the [cursor]("http://www.computerhope.com/jargon/c/cursor.htm") to the   front of the line and pressing the [tab key]("http://www.computerhope.com/jargon/t/tab.htm") on the   [keyboard]("http://www.computerhope.com/jargon/k/keyboard.htm"). A typical indent is five spaces from the left-hand or right-hand of the page.

 Is this correct to what you guys are telling me about ?

---

### Post by lisati on 2012-12-15
> **checoimg said:**
> Thank you all for your time adding </table> solved the problem. If you guys can explain me what's indenting.

It's about having your code nicely formatted:

No indenting:
[HTML]
<!DOCTYPE html>
<html>
<body>
<h1>My First Heading</h1>
<p>My first paragraph.</p>
</body>
</html>
[/HTML]
With indenting:
[HTML]
<!DOCTYPE html>
<html>
     <body>
          <h1>My First Heading</h1>
          <p>My first paragraph.</p>
     </body>
</html>
[/HTML]
Done well, it helps keep the code readable and easier to maintain, without messing up what the code does.

---

### Post by checoimg on 2012-12-15
I believe this is better.

```
<!DOCTYPE html>
<html>
<head>
<title>W3C Schools test file</title>
<meta http-equiv="refresh" content="5">
<meta name="autor" content="checoimg@gmail.com">
<style type="text/css">
body {background-color:white;}
p {color:blue;}
</style>
</head>
<body>

<table border="1">
<tr>
<td text-aling="center"><h1 style="text-align:center;color:red"> This is a red centered heading</h1></td>
</tr>
<tr>
<td><h6>This is a heading</h6></td>
<td><p><em>This is a paragraph emphasized <del>deleted text<del></em></p></td>
</tr>
<tr>
<td><p><b>This is paragraph in bold</b><p></td>
<td>
<p><code>#include "stdio.h"<br>
int main ()<br>
{<br>
printf("Hello everyone\n");<br>
return 0;<br>
}<br>
</code></p>
</td>
</tr>
<tr>
<td><p><abbr>ProMeATe</abbr></p></td>
<td><a href="https://www.plus.google.com"> Google + </a></td>
</tr>
</table>
<br><img src="A.jpg" width="640" height="640">
</body>
</html>
```

---

### Post by checoimg on 2012-12-15
> **lisati said:**
> It's about having your code nicely formatted:

No indenting:
[HTML]
<!DOCTYPE html>
<html>
<body>
<h1>My First Heading</h1>
<p>My first paragraph.</p>
</body>
</html>
[/HTML]With indenting:
[HTML]
<!DOCTYPE html>
<html>
     <body>
          <h1>My First Heading</h1>
          <p>My first paragraph.</p>
     </body>
</html>
[/HTML]Done well, it helps keep the code readable and easier to maintain, without messing up what the code does.

I like this one

---

### Post by checoimg on 2012-12-15
Now I got it! Thanks to all for the help.
```
<!DOCTYPE html>
<html>
    <head>
    <title>W3C Schools test file</title>
        <meta http-equiv="refresh" content="5">
        <meta name="autor" content="checoimg@gmail.com">
        <style type="text/css">
        body {background-color:white;}
        p {color:blue;}
        </style>
    </head>
    <body>

<table border="1">
    <tr>
        <td text-aling="center"><h1 style="text-align:center;color:red"> This is a red centered heading</h1></td>
    </tr>
    <tr>
        <td><h6>This is a heading</h6></td>
        <td><p><em>This is a paragraph emphasized <del>deleted text<del></em></p></td>
    </tr>
    <tr>
        <td><p><b>This is paragraph in bold</b><p></td>
        <td>
            <p><code>#include "stdio.h"<br>
            int main ()<br>
            {<br>
            printf("Hello everyone\n");<br>
            return 0;<br>
            }<br>
            </code></p>
        </td>
    </tr>
    <tr>
        <td><p><abbr>ProMeATe</abbr></p></td>
        <td><a href="https://www.plus.google.com"> Google + </a></td>
    </tr>
</table>
        <br><img src="A.jpg" width="640" height="640">
    </body>
</html>

```

---

### Post by spjackson on 2012-12-16
> **checoimg said:**
> Now I got it! Thanks to all for the help.


I use the w3 validator as mentioned by trent.josephsen, but during development, I find [HTML Tidy]("http://www.w3.org/People/Raggett/tidy/") invaluable. It's in the Ubuntu repository. Running it on the new version of your code gives:

```

$ tidy -i -wrap 75 new.html > out.html
line 20 column 51 - Warning: <del> is probably intended as </del>
line 14 column 1 - Warning: <table> lacks "summary" attribute
line 16 column 9 - Warning: <td> proprietary attribute "text-aling"
line 39 column 13 - Warning: <img> lacks "alt" attribute
line 23 column 48 - Warning: trimming empty <p>
Info: Document content looks like HTML 4.01 Transitional
Info: No system identifier in emitted doctype
5 warnings, 0 errors were found!

```

---

### Post by checoimg on 2012-12-16
> **spjackson said:**
> I use the w3 validator as mentioned by trent.josephsen, but during development, I find [HTML Tidy]("http://www.w3.org/People/Raggett/tidy/") invaluable. It's in the Ubuntu repository. Running it on the new version of your code gives:

```

$ tidy -i -wrap 75 new.html > out.html
line 20 column 51 - Warning: <del> is probably intended as </del>
line 14 column 1 - Warning: <table> lacks "summary" attribute
line 16 column 9 - Warning: <td> proprietary attribute "text-aling"
line 39 column 13 - Warning: <img> lacks "alt" attribute
line 23 column 48 - Warning: trimming empty <p>
Info: Document content looks like HTML 4.01 Transitional
Info: No system identifier in emitted doctype
5 warnings, 0 errors were found!

```
Thank you I just downloaded Tidy and looking forward on learning to use it.

---

### Post by tturrisi on 2012-12-17
> **AstroLlama said:**
> you have to add a closing tag to end the table. so right before your image you should add

```
</table>
```

+1 on indenting code

add </tr></table>

---

### Post by checoimg on 2012-12-17
> **tturrisi said:**
> add </tr></table>

Got it

---

