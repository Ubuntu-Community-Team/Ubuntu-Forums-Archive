---
title: "LAMP and non-English characters"
date: 2012-06-09
forum: Programming Talk
---

### Post by mörgæs on 2012-06-09
A classic PHP project: A script receives input data using POST from an HTML FORM. 

The problem is to get Icelandic characters shown correctly. 

I have experimented with 

```
meta http-equiv="Content-Type" content="text/html; charset=utf-8"
```

and

```
meta http-equiv="Content-Type" content="text/html; charset=iso-8859-15"
```

but they only solve the problem partly. Either I get the user input or rest of the HTML shown correctly, not both.

Are there any serverside settings which might interfere with the charset?

I know that escaping characters could solve the problem, but I prefer to use configuration as much as possible.

---

### Post by ofnuts on 2012-06-09
> **mörgæs said:**
> A classic PHP project: A script receives input data using POST from an HTML FORM. 

The problem is to get Icelandic characters shown correctly. 

I have experimented with 

```
meta http-equiv="Content-Type" content="text/html; charset=utf-8"
```and

```
meta http-equiv="Content-Type" content="text/html; charset=iso-8859-15"
```but they only solve the problem partly. Either I get the user input or rest of the HTML shown correctly, not both.

Are there any serverside settings which might interfere with the charset?

I know that escaping characters could solve the problem, but I prefer to use configuration as much as possible.The charset in the HTML only indicates to the navigator how to interpret the byte stream (it is normally used only of there is no content-type specified in the HTTP response header).

But that doesn't exempt you from properly encoding the characters in the generated page. 

The characters you received from the client are encoded using the global page encoding (content-type/charset) unless it is overriden by an "accept-charset" attribute in the form.

---

### Post by greenpeace on 2012-06-14
Hi, where are you then displaying the characters?  Do they go through your/a database first?

Where I have this working (for polish characters) i have:

1. This on the pages where I both accept the characters in the form, and where they are later displayed: 
[HTML]<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />[/HTML]

2. This before putting the data into my MySQL table:
[PHP]mysql_set_charset("utf-8");[/PHP]

hope that helps! :)

---

### Post by mörgæs on 2012-06-17
Problem solved.

There is no database involved, only two scripts: Index.php, which calls receiving.php. The latter processes a data (flat) file given a parameter (transferred with POST) and displays the result in an HTML table.

The table heading is hardcoded in the PHP script, but the table contents is built dynamically from the data files. Business as usual.

To begin with, *both PHP files themselves were encoded in UTF-8, as is the default in Gedit*. No matter which charset tags I entered in the two files I couldn't get a) the hardcoded table heading, b) the POST-ed values and c) the dynamically created contents correct, as seen in the first picture.

Finally it struck me that the data files (which were generated on a Windows computer) could have a strange encoding. The command 

```
file -bi <filename>
```

showed that the data files were all encoded with iso-8859-1. 

So, after saving the two PHP scripts in iso-8859-15 (close enough to iso-8859-1), results as seen in the second picture appeared. 

Long story short: Since the data files use the ISO charset, the PHP scripts should also be ISO files and they should state the ISO encoding in 'Content-Type'. If the chain is broken by a UTF-8 charset somewhere, characters are garbled.

This might be common knowledge for experienced PHP developers, but for a semi-green one as I it was news. Hope this helps someone else.

Thanks you both for (indirectly) pointing me in the right direction.


No characters were escaped during the creation of this post.

---

