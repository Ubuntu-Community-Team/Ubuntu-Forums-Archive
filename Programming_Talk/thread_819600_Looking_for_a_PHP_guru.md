---
title: "Looking for a PHP guru"
date: 2008-06-05
forum: Programming Talk
---

### Post by ejpyle on 2008-06-05
I am trying to accomplish what I think is the impossible so here goes...


I have a guestbook written in PHP. When the user posts a comment after clicking "SEND" they are automatically returned to the main index page though what I want it to do is refer back to "mysite/subdirectory/index.php" vs "mysite.com/index.php"

Here is the code which executes after the user clicks "SEND". What do I need to edit below to accomplish this?

```
<?php



}



else {



    // Adds the new entry to the database

    $query = "INSERT INTO guests SET message='$message', name='$name', date=NOW()";

    $result = mysql_query($query);



    // Takes us back to the entries

    $ref = $_SERVER['HTTP_REFERER'];

    header ("Location: $SELF");
}
?> 
```

My understanding is that section under //Takes us back to the entries// would have to be changed to something else.... correct?

---

### Post by Lau_of_DK on 2008-06-05
Couldn't you just do something like

[php]
$newurl = "http://www.google.com"

$script=<<<ES
<script type="text/javascript">
  document.location = $newurl;
</script>
ES;

echo $script

[/php]

Its just off the top of my head, but that would fire a js that moves you to $newurl.

/Lau

---

### Post by jsmiith on 2008-06-05
Replace $SELF with the url that you wish to go to. For some reason I am thinking that you will need to use an absolute url, but that may not be the case.

>>EDIT<< I didn't read the post clearly, anyone else have an idea?

---

