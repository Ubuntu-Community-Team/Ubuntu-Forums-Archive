---
title: "multilevel menu recognition   MMR&#8482;"
date: 2008-06-27
forum: Programming Talk
---

### Post by henchman on 2008-06-27
Hello, 

Iam currently expanding our companies CMS (no, we won't use joomla :) :(( ) and iam sitting in front of a problem:

We have a dynamic menu on the page and while creating this menu on every page impression, the script checks for every element if it equals the currently opened url. 
A Problem occurs if we have a page in the menu like 

index.php?action=foo

and on the page there is a link like to 

index.php?action=foo&page=2

because obviously that's not the same. I thought about comparing each parameter and if all parameters of the menu's element are in the current url, make this the active link. But this would throw up links like

index.php?action=foo

and

index.php?action=foo&subaction=bar

which might not be the same menu element...

Perhaps iam some sort of blind for this problem, dunno. Any help would be greatly appreciated. Thanx :)

---

### Post by LoneWolfJack on 2008-06-27
```

$url = 'index.php?action=foo&subaction=bar'
$url = substr($url,strrpos($url,'&'),strlen($url));

```

... will simply cut off everything not important to your menu activation thingy.

---

### Post by henchman on 2008-06-27
hm.. thanks, you pointed me to the right direction:

the opened page could handle a different string to the menu class, where it, as you said, cuts off the unimportant parts. :)

thank you :)

---

