---
title: "Python - dynamically add text to webpage"
date: 2011-01-18
forum: Programming Talk
---

### Post by TiBaal89 on 2011-01-18
I'd like to have a webpage do the following... the user clicks a button in the browser which launches a Python script whose output is displayed in the browser dynamically (as if it was the terminal).  This isn't just a dump of the output, the Python script will execute for some time and spit out a line every few seconds or so.

I'm able to accomplish what I want as far as adding text to the browser in javascript using the following:

```
<html>

<script>

  function m() {
    document.body.innerHTML += "<div>Hello World</div>";
  }

</script>

<body>
  <p>Click for message.</p>
  <button onclick="m();">Click!</button>
</body>

</html>
```

Try it:  [http://tibaal89.com/files/innerhtml.html](http://tibaal89.com/files/innerhtml.html)

But of course that doesn't answer the question of how to get text from the Python output to the javascript.

Am I on the right track?  Any help is appreciated.

---

### Post by slavik on 2011-01-19
make the python script output to a file and keep refreshing the page that grabs the contents.

HTTP is not a continuous session!

---

### Post by nmaster on 2011-01-19
i may be mistaken, but i think this is where [AJAX]("http://en.wikipedia.org/wiki/Ajax_(programming)") would be helpful 
> With Ajax, web applications can retrieve data from the server asynchronously in the background without interfering with the display and behavior of the existing page. 

---

### Post by TiBaal89 on 2011-01-19
> **nmaster said:**
> i may be mistaken, but i think this is where [AJAX]("http://en.wikipedia.org/wiki/Ajax_(programming)") would be helpful

Yes, thank you - I'm just finding that myself.  Sounds like exactly what I want to do.  Looking into this right now: [http://en.wikipedia.org/wiki/XMLHttpRequest](http://en.wikipedia.org/wiki/XMLHttpRequest)

---

