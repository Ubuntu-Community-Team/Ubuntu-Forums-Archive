---
title: "Javascript - set .innerHTML"
date: 2009-09-14
forum: Programming Talk
---

### Post by Johnsie on 2009-09-14
I have the following line of code:

[PHP]document.getElementById('weightSpan').innerHTML='<tr><td align="right">Weight:</td><td>
<select name="weight" onchange="setTotal();">
<option value="0-100g">0-100g</option>
<option value="101-250g">101-250g</option>
<option value="251-500g">251-500g</option>
<option value="501-750g">501-750g</option>
<option value="751-1000g">751-1000g</option>
</select></td></tr>';[/PHP]


I think the problem is caused by special characters because when I just use normal a-z text it works fine. I've tried escaping the " signs and the <> signs but not had any luck. Am I doing something wrong here and if so how can I fix it?

---

### Post by myrtle1908 on 2009-09-14
What error do you get?  "unterminated string literal" or similar?  Literal line-feeds in your string perhaps?  This works fine for me.  Tested in Firefox.

[PHP]<script language="javascript">
function go() {
    window.document.getElementById('weightSpan').innerHTML='<tr><td align="right">Weight:</td><td><select name="weight" onchange="setTotal();"><option value="0-100g">0-100g</option><option value="101-250g">101-250g</option><option value="251-500g">251-500g</option><option value="501-750g">501-750g</option><option value="751-1000g">751-1000g</option></select></td></tr>'; 
}
</script> 

<body onload="go();">
<div id='weightSpan'></div>
</body>[/PHP]

---

### Post by Johnsie on 2009-09-14
Thanks, I punched your code in and it worked fine. Must've been the line feeds. BTW how did you get an error message? At the moment I'm  just guessing what the errors are! A dubber of some sorts would be nice.

---

### Post by myrtle1908 on 2009-09-14
> **Johnsie said:**
> Thanks, I punched your code in and it worked fine. Must've been the line feeds. BTW how did you get an error message? At the moment I'm  just guessing what the errors are! A dubber of some sorts would be nice.

With Firefox you can either use the JavaScript/Error console (select "Tools->Error Console" from the Firefox menu) or better still download Firebug @ [http://www.getfirebug.com](http://www.getfirebug.com)

Once you start with Firebug you will never know how you managed without it.

---

### Post by Johnsie on 2009-09-14
Thanks, I'll check that out.

---

### Post by Mirge on 2009-09-14
Agreed with Firebug. Also, check out [jQuery]("http://jquery.com").

---

### Post by bobince on 2009-09-14
```
innerHTML='<tr>...
```

IE doesn't allow you to set the innerHTML of <table>s (or a few other elements which have content models other than normal block or inline). You can set the innerHTML of a wrapper <div> containing the table.

---

### Post by Reiger on 2009-09-14
InnerHTML should only be used for reading that property, or putting #PCDATA. It is unreliable for anything else at best, and plain not-working at worst.

The 'proper' way to do this is via the tedious DOM methods; although some libraries offer convenience methods to take out the tedium and append entire trees like that in one go...

---

### Post by myrtle1908 on 2009-09-14
> **Reiger said:**
> InnerHTML should only be used for reading that property, or putting #PCDATA. It is unreliable for anything else at best, and plain not-working at worst.

The 'proper' way to do this is via the tedious DOM methods; although some libraries offer convenience methods to take out the tedium and append entire trees like that in one go...

+1

This why it's always best to use one of the excellent libraries eg. ExtJS, jQuery etc etc.  Best to have these libs shield the uninitiated.

---

### Post by bobince on 2009-09-15
Yeah, framework fans will tell you Their Favourite Library will magically solve all cross-browser problems... take that with a pinch of salt.

For example setting:

    ```
$('table').html('<tr>...')
```

in jQuery will still fail with exactly the same IE &#8216;Object expected&#8217; error as setting table.innerHTML from plain JavaScript.

Frameworks are a good way to reduce the amount of code you have to write, but if you think it's going to save you from learning JavaScript and testing in different browsers you're mistaken.

---

### Post by Johnsie on 2009-09-15
In the end I only left the <options> in there and put the table stuff in the html. The options were the only part that was really changing.

While I do use jQuery and other such libraries sometimes I like to write my own stuff sometimes to help me learn and I like the flexibility of using my own code.

---

### Post by Mirge on 2009-09-15
> **bobince said:**
> Yeah, framework fans will tell you Their Favourite Library will magically solve all cross-browser problems... take that with a pinch of salt.

For example setting:

    ```
$('table').html('<tr>...')
```in jQuery will still fail with exactly the same IE ‘Object expected’ error as setting table.innerHTML from plain JavaScript.

Frameworks are a good way to reduce the amount of code you have to write, but if you think it's going to save you from learning JavaScript and testing in different browsers you're mistaken.

Latest IE I have installed is only IE7, but the following works fine for me... maybe I mis-read or something?

```

<html>
<head>
<title>Test Page</title>
<script type="text/javascript" src="jquery.pack.js"></script>
<script type="text/javascript">
function ChangeTable()
{
    $('#foobar').html('<tr><td>After</td></tr>');
}
</script>
</head>
<body>
<table id="foobar">
    <tr>
        <td>Before</td>
    </tr>
</table>

<input type="button" id="button" value="Click me" onclick="ChangeTable()"/>
</body>
</html>

```

---

### Post by bigboy_pdb on 2009-09-15
> **Mirge said:**
> ... maybe I mis-read or something?

What he's saying is that you'd need to learn javascript regardless of whether or not you use js libraries and that you might get bugs in certain browsers and not in others so it's important that you don't expect everything to be immediately cross platform with them.

Even if the example that was given happens to work for you, there's other problems that you'll find at some point. For example, I've had problems where some browsers allowed me to inject javascript into the head tag, but others generated errors. In IE6 & IE7, I got an error by removing a flash tag (I can't remember if it was object/embed) and recreating it again (using [flashembed]("http://flowplayer.org/tools/flashembed.html")). Also, I've gotten reports for bugs that can only be generated on a certain browser with a specific OS (ie. Firefox on MAC).

**EDIT:** The problems that I mentioned happened when I used JQuery to dynamically modify websites.

---

### Post by Mirge on 2009-09-15
> **bigboy_pdb said:**
> What he's saying is that you'd need to learn javascript regardless of whether or not you use js libraries and that you might get bugs in certain browsers and not in others so it's important that you don't expect everything to be immediately cross platform with them.

Even if the example that was given happens to work for you, there's other problems that you'll find at some point. For example, I've had problems where some browsers allowed me to inject javascript into the head tag, but others generated errors. In IE6 & IE7, I got an error by removing a flash tag (I can't remember if it was object/embed) and recreating it again (using [flashembed]("http://flowplayer.org/tools/flashembed.html")). Also, I've gotten reports for bugs that can only be generated on a certain browser with a specific OS (ie. Firefox on MAC).

**EDIT:** The problems that I mentioned happened when I used JQuery to dynamically modify websites.

Ehhh... I can agree that learning actual Javascript to **an extent** is useful. You don't need to be a professional Javascript developer using native JS code in order to take advantage of frameworks like jQuery. jQuery takes care of a lot of cross-browser compatibility issues, as well as making writing JS itself much easier, more compact and more fun (IMHO). In other words, you don't need to know how to rebuild an engine before you should learn how to drive a car.

The code I posted was pretty specific to the problem mentioned which said that jQuery would barf in IE with it... and it didn't? Is it a problem specific to a certain platform? I've never run IE on anything but Windows so I wouldn't know.

---

