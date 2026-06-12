---
title: "Javascript insert HTML"
date: 2011-05-02
forum: Programming Talk
---

### Post by jdb91 on 2011-05-02
I know this is really on the edge of fitting the forums' description, but I'll try any way.

Right I have two .php files one (for purpose) is called index.php and the other table.php

Table.php populates a table depending on what id you pass it in the URL.

Basically I want index.php to be able to show tables using table.php on demand (these are big tables and take seconds to load).

So I've been looking for a way for javascript to do it, but have only come across HTML's <object> and <iframe> neither of which are very nice and crucially, they don't automatically determine their own size (have also tried to get javascript to so that and it only works for the largest table imported).

What I ideally want is for javascript to insert a <DIV> with the code from table.php.

Any ideas?  I've looked across the net and can't see to find anything like this.

---

### Post by simeon87 on 2011-05-02
Based on how you describe it, why don't you include the output of table.php into a div? So in index.php you'd do:

```
<div>
<?php require_once table.php ?>
</div>
```

---

### Post by jdb91 on 2011-05-02
> **simeon87 said:**
> Based on how you describe it, why don't you include the output of table.php into a div? So in index.php you'd do:

```
<div>
<?php require_once table.php ?>
</div>
```

Thanks kind of it (sorry for poor description) but I only want it rendered on demand or the page will take ages to load.

---

### Post by bashologist on 2011-05-02
For javascript the only thing I can think of personally is to use the responseText from an xmlhttprequest and then use document.write().

Should you maybe be using xml or sql instead of this php option? Sounds like you want a database.

Good luck.

---

### Post by brpylko on 2011-05-02
```

<script type="javscript">
function loadFrame(){
document.getElementByID('phpdiv').innerHTML = "<?php require_once yourfile.php ?>"     //(I actually am not quite sure what should go here)
}
</script>

<div id='phpdiv'>
</div>

```call loadFrame() when you want it loaded.

---

### Post by shadylookin on 2011-05-02
Would doing ajax calls to table.php and appending the result to a div work?

---

### Post by roccivic on 2011-05-03
if you include jQuery ([http://jquery.com/](http://jquery.com/)) in your page, then you can load content through ajax like this:

[HTML]<html>
<body>
<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.5.2/jquery.min.js"></script>
<script type="text/javascript">
// wait until the page is loaded
$(document).ready( function() {
    // attach click event to link
    $('#mylink').click( function() {
        // perform ajax call
        $.get("page.php", { id: "12345" },
           // when the ajax call is finished
           function(data){
             // replace div contents with new content
             $('#mydiv').html(data);
        });
    });
});
</script>
<div id='mydiv'></div>
<a href='#' id='mylink'>load</a>
</body>
</html>
[/HTML]

---

