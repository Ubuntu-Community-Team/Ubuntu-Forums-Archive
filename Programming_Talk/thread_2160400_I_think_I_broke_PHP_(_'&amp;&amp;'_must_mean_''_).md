---
title: "I think I broke PHP ( '&amp;&amp;' must mean '||' )"
date: 2013-07-06
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2013-07-06
EDIT: needed parenthesis on the fist condition
----------------

here is a screenshot of my issue:
[IMG]http://i.imgur.com/8kH3gzc.png[/IMG]
and here is the source code:
[PHP]<?php
echo "type=".$_GET['type']."\nraw=".(isset($_GET['raw'])?$_GET['raw']:'NOT SET')."\n";

if(isset($_GET['type'])?$_GET['type']:0=='pdf' && !isset($_GET['raw']))
    echo "Condition passed";
else
    echo "Condition failed";
?>

[/PHP]

---

