---
title: "web template help"
date: 2007-08-04
forum: Programming Talk
---

### Post by adza on 2007-08-04
Hi there, i am having some trouble with a concept i think.. i was hoping that someone would be able to help :) I have been working on my website as a hobby for a while now, working primarily on the technical design aspects (learning php) before looking at design... Well, it's now time for me to begin wondering about the design and i've started developing a css/template for the site.
I have a question though, i've created a index page that essentially sets up the index page composed of several other pages, with the 'main' page being my old index.php. When i logon now through the login form, how do i get the welcome page to open inside the 'index' page? ie, so it still displays my header and menu bar stuff etc... i'm a little lost.. (but loving it - haha!)

Cheers :P

---

### Post by tturrisi on 2007-08-05
You can use php includes or even javascript.

<?php
include ("../inc/cookie.php");
?>
<html>
<head>
</head>
<body>
<?php
include ("../inc/header.php");
?>
<p><script type="text/javascript" src="../js/hoiriz_menu.js"></script></p>
<p>Hello world.<?p>
<?php
include ("../inc/footer.php");
?>
</body>
</html>

---

### Post by adza on 2007-08-06
cool thanks tturrisi, these included php elements would all then need to be absolute positioned right? i have got my header and nav bar working (using absolute positions), i'm using the <div> tag though and styling the <div> in a css... the include then comes in the <div> element... Is it better to use include() or require() in php?

---

### Post by LaRoza on 2007-08-06
> **adza said:**
> cool thanks tturrisi, these included php elements would all then need to be absolute positioned right? i have got my header and nav bar working (using absolute positions), i'm using the <div> tag though and styling the <div> in a css... the include then comes in the <div> element... Is it better to use include() or require() in php?

It depends, include will issue a warning if not found, and require will issue an error. Also, you can use: require_once(), and include_once().

For just a design, use include(), for important files, e.g. database connections, use require().

---

### Post by tturrisi on 2007-08-07
You don't have to use absolute positioning, but you can.  Put the styles in your separate css file & the html code in the php includes.

---

