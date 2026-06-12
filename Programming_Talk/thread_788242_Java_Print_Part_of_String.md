---
title: "Java Print Part of String"
date: 2008-05-09
forum: Programming Talk
---

### Post by dyous87 on 2008-05-09
Hello, I am new to Java and trying to figure out how to do something. If I have a string say:

```
String inputLine = "Click here for more info <a href="http://www.wikipedia.com">Wikipedia</a>"
```How can I get Java to print out just:

> [http://www.wikipedia.com](http://www.wikipedia.com)Any help would be appreciated.

Thanks,
David

---

### Post by LaRoza on 2008-05-09
Does Java has any libraries for handling xhtml, html or xml? 

It would be rather easy using the DOM.

In ECMAScript:

[php]
var linds = document.getElementsByTagName("a"); // Array of <a> elements
var hrefs = new Array(); // A new array (duh)
for (var i = 0; i < linds.length(); i++)
{
    hrefs.push(linds[i].getAttribute("href")); // Append the href attribute value to the href array
}

[/php]

---

### Post by rickh57 on 2008-05-09
That would be a great place to use a regular expression. Regexes excel in parsing text like your example. Just Google for "regular expression" java for more information.

---

### Post by LaRoza on 2008-05-09
> **rickh57 said:**
> That would be a great place to use a regular expression. Regexes excel in parsing text like your example. Just Google for "regular expression" java for more information.

If these strings are already structured, I think it would be best to use a library designed to handle such structured documents, otherwise, re's would be the better bet.

---

### Post by solarwind on 2008-05-09
> **dyous87 said:**
> Hello, I am new to Java and trying to figure out how to do something. If I have a string say:

```
String inputLine = "Click here for more info <a href="http://www.wikipedia.com">Wikipedia</a>"
```How can I get Java to print out just:

Any help would be appreciated.

Thanks,
David

A regular expression would be best. This is what I made when I made my link scraper:

[http://www.paste.metafy.org/view.php?file=vEgusamYhyme.txt&language=java](http://www.paste.metafy.org/view.php?file=vEgusamYhyme.txt&language=java)

You just construct the class with:
```
new Node("String inputLine = \"Click here for more info <a href=\"http://www.wikipedia.com\">Wikipedia</a>\"");
```

Then you call getNodeProperty("href") which will return the string
```
http://www.wikipedia.com
```

Tell me how it goes!

---

### Post by dyous87 on 2008-05-09
Thank you so much to everyone. You have been helpful.

I have been looking up regex and playing around but i can't seem to get it right. Basically as I see it there should be a way to remove everything from my string except what is between a <a href="***urlhere***"> tag

So I have the line:

```
inputLine = inputLine.replaceAll(***something goes***);
```

and I have been messing around by googling and trying different combinations there but i can't get it right. Can someone point me in the right direction. I would really appreciate it.

Thanks
David

---

### Post by solarwind on 2008-05-09
> **dyous87 said:**
> Thank you so much to everyone. You have been helpful.

I have been looking up regex and playing around but i can't seem to get it right. Basically as I see it there should be a way to remove everything from my string except what is between a <a href="***urlhere***"> tag

So I have the line:

```
inputLine = inputLine.replaceAll(***something goes***);
```

and I have been messing around by googling and trying different combinations there but i can't get it right. Can someone point me in the right direction. I would really appreciate it.

Thanks
David

Read my above post! I put this link in there: [http://www.paste.metafy.org/view.php?file=vEgusamYhyme.txt&language=java](http://www.paste.metafy.org/view.php?file=vEgusamYhyme.txt&language=java)

That's the code I wrote that does the job using regex!

---

### Post by dyous87 on 2008-05-09
Ok thanks a lot to all of you i got it!

Now I have another question. Is there a way using a java regular expression to remove everything EXCEPT something in between quotes?

---

### Post by solarwind on 2008-05-09
> **dyous87 said:**
> Ok thanks a lot to all of you i got it!

Now I have another question. Is there a way using a java regular expression to remove everything EXCEPT something in between quotes?

What exactly are you trying to do?

---

### Post by dyous87 on 2008-05-10
```
str = str.replaceAll("\".*\"","");
```

Well I used this line to get rid of everything inside quotation marks and it worked.

But what I wanted to do it get rid of everything outside the quotation marks so i tried

```
str = str.replaceAll("^(\".*\")","");
```

But it doesn't work. What am I doing wrong. I though '^' meant anything but.

David

---

### Post by solarwind on 2008-05-10
> **dyous87 said:**
> ```
str = str.replaceAll("\".*\"","");
```

Well I used this line to get rid of everything inside quotation marks and it worked.

But what I wanted to do it get rid of everything outside the quotation marks so i tried

```
str = str.replaceAll("^(\".*\")","");
```

But it doesn't work. What am I doing wrong. I though '^' meant anything but.

David

My question is, what is your PURPOSE of getting rid of everything outside of the quotation marks? There may be a way of doing it that's 10 times easier.

---

### Post by dyous87 on 2008-05-10
Ok what I am doing is reading from a text file that has a list of a bunch of Names in quotes and then a description next to it like this:

"Joe Doe" Went to Harvard law, graduated in 1999.

"Mary Smith" Traveled to Italy in 2003 where she met her finance.

My program reads the file line by line and then prints each line as a string. 

I was trying to use regex to Get rid of everything outside of the quotations so then I would just be left with a list of names:

Joe Doe
Mary Smith
etc.

Thanks again for your help,
David

---

### Post by solarwind on 2008-05-10
> **dyous87 said:**
> Ok what I am doing is reading from a text file that has a list of a bunch of Names in quotes and then a description next to it like this:

"Joe Doe" Went to Harvard law, graduated in 1999.

"Mary Smith" Traveled to Italy in 2003 where she met her finance.

My program reads the file line by line and then prints each line as a string. 

I was trying to use regex to Get rid of everything outside of the quotations so then I would just be left with a list of names:

Joe Doe
Mary Smith
etc.

Thanks again for your help,
David

I am much better able to help you now.

The following regular expression will return the name only:
```
(?<=")[^"]*(?=")
```

For example, if you provide this text:
```
"Joe Doe" Went to Harvard law, graduated in 1999.
```

It will match this:
```
Joe Doe
```

Remember to run it on each entry. Don't run it on your entire document because it will not work. Run it once for each name/description set.

Hope I helped, tell me how it goes!

---

