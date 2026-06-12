---
title: "CSS layout; unknown sizes, overflow and proper resizing"
date: 2010-11-13
forum: Programming Talk
---

### Post by worseisworser on 2010-11-13
Take a look at this: [http://static.nostdal.org/~lnostdal/always-here/chat-layout-css-sucks.html](http://static.nostdal.org/~lnostdal/always-here/chat-layout-css-sucks.html). Is it possible to express this using only HTML and CSS; i.e. no JavaScript? Anyone up for the challenge?

Key points are:

[LIST]
[*]The top and bottom areas must not have an explicit size set for them as we do not know how much vertical space the content in them will need; it might even be dynamic (which would require an additional call to our resizer function; that's OK). They must be as small (height) as possible; but not so small that scrollbars appear.
[*]The middle area must overflow properly (auto) using a scrollbar when needed.
[*]..and of course things will need to adjust properly as the user resizes his browser window; the entire window must be made use of.
[/LIST]

Code is pasted below in case the server goes down or something:

```

<!DOCTYPE html
          PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
          "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <title>chat-layout-css-sucks</title>
    <script type="text/javascript"
            src="https://ajax.googleapis.com/ajax/libs/jquery/1.4.3/jquery.min.js">
    </script>

    <style type="text/css">
      /* The W3C can **** off. */
      * {
        -webkit-box-sizing: border-box; /* Safari/Chrome, other WebKit */
        -moz-box-sizing: border-box;    /* Firefox, other Gecko */
        box-sizing: border-box;         /* Opera/IE 8+ */
      }

      html, body {
        width: 100%; height: 100%;
        margin: 0; padding: 0;
        border: 2px solid blue;
      }

      #top, #middle, #bottom {
        border: 1px solid black;
      }
    </style>

    <script type="text/javascript">
      (function(){
        var resizer = function(){
          $("#middle").height($("body").height()
                              - $("#top").outerHeight()
                              - $("#bottom").outerHeight());
        }

        $(document).ready(function() {
          resizer();
        });

        $(window).resize(function() {
          resizer();
        });
      })();
    </script>
  </head>

  <body>
    <div id="top">top; we do not know how much vertical space this content will need</div>
    <div id="middle" style="overflow: auto;">
      blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>
      blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>
      blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>
      blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>
      blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>
      blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>
      blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>
      blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>blah<br/>
    </div>
    <div id="bottom">bottom; we do not know how much vertical space this content will need</div>
  </body>
</html>

```

---

### Post by Jose Catre-Vandis on 2010-11-13
The answer will be here - somewhere

[www.cssplay.co.uk/](www.cssplay.co.uk/)

---

### Post by worseisworser on 2010-11-13
Uhm, the menu just leads to a bunch of .exe file downloads? O_o

edit:
Found something; [http://www.cssplay.co.uk/layouts/bodyfix.html](http://www.cssplay.co.uk/layouts/bodyfix.html) .. but it uses a static header and footer, so no go.

---

### Post by Jose Catre-Vandis on 2010-11-14
or this one?

[http://www.cssplay.co.uk/layouts/flexible-3column.html](http://www.cssplay.co.uk/layouts/flexible-3column.html)

---

### Post by worseisworser on 2010-11-14
> **Jose Catre-Vandis said:**
> or this one?

[http://www.cssplay.co.uk/layouts/flexible-3column.html](http://www.cssplay.co.uk/layouts/flexible-3column.html)

Nope. .. heh .. :)

edit: I've made some small additions to the points above in case they where not clear.

---

