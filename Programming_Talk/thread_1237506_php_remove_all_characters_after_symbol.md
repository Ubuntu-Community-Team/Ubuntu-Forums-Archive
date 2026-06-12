---
title: "php remove all characters after symbol"
date: 2009-08-11
forum: Programming Talk
---

### Post by sandyd on 2009-08-11
How can i remove all characters behind the "_" symbo?
for example, i have a variable named $avatarimg.
the contents are
h3498fn3874fb3_fj0943fn.jpg. I want to remove the "_fj0943fn.jpg" part

---

### Post by Mirge on 2009-08-11
> **carlee said:**
> How can i remove all characters behind the "_" symbo?
for example, i have a variable named $avatarimg.
the contents are
h3498fn3874fb3_fj0943fn.jpg. I want to remove the "_fj0943fn.jpg" part

```

<?php

$avatarimg = "somethingbefore_after.jpg";
$new_avatarimg = substr($avatarimg, 0, strpos($avatarimg, "_"));

print $new_avatarimg;

?>

```

Just a quick example...

---

### Post by ghostdog74 on 2009-08-11
the easier way is to explode it and get the first element
```

$s = explode("_",$avatarimg);
print $s[0];

```

---

