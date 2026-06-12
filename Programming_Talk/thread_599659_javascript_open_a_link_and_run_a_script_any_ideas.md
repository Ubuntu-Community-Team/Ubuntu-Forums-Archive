---
title: "javascript open a link and run a script any ideas"
date: 2007-11-01
forum: Programming Talk
---

### Post by zach12 on 2007-11-01
Hello,
I'm trying to make a javascript that will run a js file when you open a like or hit a button.
here my code i have ran it in a debugger (bluefish) and nothing is not working:( 
> <input onclick="src="test" value="test" type="button">
Thanks

---

### Post by LaRoza on 2007-11-01
> **zach12 said:**
> Hello,
I'm trying to make a javascript that will run a js file when you open a like or hit a button.
here my code i have ran it in a debugger (bluefish) and nothing is not working:( 

Thanks

Your code doesn't make sense, could you be more explicit?

You are mixing Script with Markup, that is a bad idea. Keep ALL script in a separate file. 

My site, [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home) is a good example of this. Use FF with the Web Developer Toolbar to really explore the code.

As to what you asked, you cannot run a "file".

Try this:

Make a xhtml document and link a js file to it. In the html file, have this code somewhere:

```

<button id="press">Say Hi</button>

```

In the JS file, have this:

[php]
window.onload = function()
{
    document.getElementById("press").onclick = function()
    {
        alert("Hi");
    }
}
[/php]

---

### Post by zach12 on 2007-11-02
Thanks that works :guitar:

---

