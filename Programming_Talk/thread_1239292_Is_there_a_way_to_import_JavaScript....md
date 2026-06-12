---
title: "Is there a way to import JavaScript..."
date: 2009-08-13
forum: Programming Talk
---

### Post by gjoellee on 2009-08-13
You can use
```
	@import url("css.css");
```
in CSS.

Now is there a way to there a similar function for JavaScript? I am getting pretty tired of managing tons of line like this:
```
<script type="text/javascript" src="js/javascript.js"></script>
```
it is a lot easier just adding one of those files to your index then fifty. (50 is just and example, I don't use that many javascipt files)

---

### Post by jtrulen on 2009-08-13
You could create a single Javascript page with code similar to the following:

```
document.write("<script type='text/javascript' src='file1.js'></script>");
document.write("<script type='text/javascript' src='file2.js'></script>");
```

That way you would only have to call a single *.js page instead of many.

Hope this helps.

---

### Post by Reiger on 2009-08-13
document.write() is unreliable (it may muck up rendering, it may not work, it may cause errors if the order of import matters [because it injects code into the page, which means it may be evaluated before its dependencies have finished loading]), especially in a XML DOM.

If you serve your page using something like PHP, defining a import function might be worthwhile; e.g.:

jsimporter.php;
[php]
<?
  header('Content-type: text/javascript'); /* override server HTTP content type settings, they are nearly always wrong */
  function import($jsfile) {
    /* logic to import jsfile from $jsfile */
    $symbol = dirname(__FILE__) . '/' . $jsfile; // construct path
    $real = realpath($symbol); // path conventions re-mapping
    if(file_exists($real)) {
      readfile($real); // stream the import as part of the loaded JS file
    }
  }
?>
[/php]

Then write your JS code in files like this:

dialog.js.php:
```

<?php require_once('jsimporter.php'); ?>
function customAlert(message) { alert("This is a custom alert message:\n"+message); }

```

test.js.php:
```

<?php require_once('jsimporter.php');
      import('dialog.js.php');
?>
window.onload = function() { customAlert('This is a test'); }

```

In the (X)HTML:
```

<script type="text/javascript" src="dialog.js.php"><!-- all dependencies are imported on the server side --></script>
```

More elaborate logic and error handling etc. can be added of course.

---

### Post by gjoellee on 2009-08-18
Thanks! Sorry for the late reply, but I have been really busy moving from KsHoster.net to StupidReality.org. I will try your code soon, I just have to do some more important things at the moment.

---

