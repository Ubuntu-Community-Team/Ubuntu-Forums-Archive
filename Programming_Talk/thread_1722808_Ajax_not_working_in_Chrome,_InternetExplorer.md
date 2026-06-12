---
title: "Ajax not working in Chrome, InternetExplorer"
date: 2011-04-06
forum: Programming Talk
---

### Post by kcode on 2011-04-06
Hi,
I am new to web delevopment. This is the code that gets an XMLHttpRequest object for different browsers.

```

function getHTTPRequestObj()
{
 if(window.XMLHttpRequest()) return new XMLHttpRequest();
 else if(window.ActiveXObject)return new ActiveXObject("Microsoft.XMLHTTP");
}

```

But, this code is not working in IE and Chrome, save Firefox.

Thanks.

---

### Post by deathadder on 2011-04-06
I've never seen AJAX that returns a request object in that way, I've only ever seen / written code that creates the object and makes the request, like so:
```

function doSomeAJAX() {
    var xmlhttp;

    if (window.XMLHttpRequest) {
        // code for IE7+, Firefox, Chrome, Opera, Safari
        xmlhttp=new XMLHttpRequest();
    } else {
        // code for IE6, IE5
        xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
    }

    xmlhttp.onreadystatechange=function() {
        if (xmlhttp.readyState==4 && xmlhttp.status==200) {
            // do something with response
        }
    }

    xmlhttp.open("GET","foo",true);
    xmlhttp.send();
}

```
I would guess that the problem is being caused by IE/Chrome not allowing you to return the object. Does it work if you change how you create the xmlHTTP object?

---

### Post by kcode on 2011-04-06
shall try that.

---

### Post by kcode on 2011-04-06
It does work in Chrome, but not in IE.

---

### Post by deathadder on 2011-04-07
> **kcode said:**
> It does work in Chrome, but not in IE.
Can you post the full code so I can see what you're doing?

---

### Post by jerome bettis on 2011-04-07
> **kcode said:**
> It does work in Chrome, but not in IE.

yes, developing things to be cross browser is about as stressful as it gets

If you can, import the jquery javascript library and learn how to use that.  It is quite nice for a lot of things, ajax being one of them.  All (most..) of the browser quirks and differences are accounted for in there, so it offloads that huge burden from you and you can concentrate on more important things.

I would never use the xmlhttp api directly.  Other people have spent a lot of time hammering through the best practices for you.

[http://sixrevisions.com/javascript/the-power-of-jquery-with-ajax/](http://sixrevisions.com/javascript/the-power-of-jquery-with-ajax/)

---

### Post by kcode on 2011-04-09
This is index.html on the server. 

It allows the customers in a coffee shop to play songs which are preferred by them. That is, there is a global playlist which can be modified by customers.


Regards,
kcode

---

### Post by deathadder on 2011-04-11
IE is throw an "Access is denied" error, due to the lack of sendReloadedPlaylist.php, it's also caused by cross domain request so bear that in mind! But having a look at your code I think (since this is beyond a trivial request) you would benefit from using [jQuery]("http://docs.jquery.com/Tutorials").

---

