---
title: "Converting a dynamic PHP page to HTML - print/save as"
date: 2006-05-25
forum: Programming Talk
---

### Post by hagen00 on 2006-05-25
Hi there

My problem is the following. I've got a PHP page on which I do mathematical calculations. I.e. there are a couple of input boxes and a button, that onClick calls a Javascript routine and outputs the results of the calculation in some other text boxes. 

What I want to do now is to be able to firstly print the results by calling javascriptrint(), and also to save the page with the results and also email the page to a friend. 

The easiest way would be if the page was a static HTML page. Then printing, saving and attaching it to an email are easy. So ideally, on the PHP page, I would click a button, that would pop up an HTML page, with the results of the PHP page. And then on that page I would have the option of saving as, printing or emailing.

But how do I convert my PHP page into an HTML page that contains all the dynamically calculated variables?

Does that make sense?

Help much appreciated...

H

---

### Post by tribaal on 2006-05-25
Well you seem to make sense...

I believe the following method should work in pretty much any case, as long as the calculations are made on the server side (i.e. it won't work if the results are calculated with a JavaScript):

(My installation is in French so menu items and labels might differ)

In Firefox right click on the page and choose "Show page sourcecode".
This will open a new window (or tab), with only the HTML source code of the page. 
- Type ctrl-a (so that you select all the text).
- Type ctrl-c (so that you copy everything)
- Now open a text editor like gedit ("Applications" -> "Accessories" -> "Notepad")
- Type ctrl-v (so that you paste your webpage's source in the text editor)

Now save this file as "page.htm". You should now be able to access it with firefox, and it will be static.

Did it work? Is that what you were looking for? 
Let me know!

- trib'

---

### Post by hagen00 on 2006-05-25
Hey, 

Thanks for the reply. I actually came here to say that the problem is resolved. My biggest issue really was the javascript command
```
document.execCommand("SaveAs")
``` I didn't want that to save a php page, but rather an html page. But you can get around that by going 
```
document.execCommand("SaveAs",1,"print.html")
```. So problem solved. I don't need to convert my php page into html after all. 

Cheers

Hagen

---

### Post by tribaal on 2006-05-25
Good! Nice to know your problem is solved!

- trib'

---

### Post by harati on 2009-04-28
document.execCommand is not working in firefox,please give solution

---

### Post by Zugzwang on 2009-04-28
> **harati said:**
> document.execCommand is not working in firefox,please give solution

So what error message do you get in the JavaScript console?

---

### Post by Pratik Parmar on 2012-04-02
> **hagen00 said:**
> Hey, 

Thanks for the reply. I actually came here to say that the problem is resolved. My biggest issue really was the javascript command
```
document.execCommand("SaveAs")
``` I didn't want that to save a php page, but rather an html page. But you can get around that by going 
```
document.execCommand("SaveAs",1,"print.html")
```. So problem solved. I don't need to convert my php page into html after all. 

Cheers

Hagen

Can u plzz mail me dat code..i need it urgently..my email id is [email]pratikp264@gmail.com[/email]

---

