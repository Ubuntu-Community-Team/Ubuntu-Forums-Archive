---
title: "[ MySQL - PHP ] Russian characters are represented as ??????."
date: 2009-10-10
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-10
**MySQL field charset:** utf8_unicode_ci ( Unicode, multilingual )
**File encoding:** UTF8 without BOM
**HTML charset:** UTF8

In MySQL, everything seems to be just fine, but PHP fails and I get something like:
```
This is what I get: ???? ??????? :)
This is what I should get: &#1057;&#1072;&#1081;&#1090; &#1079;&#1072;&#1087;&#1091;&#1097;&#1077;&#1085; :)

```

The weirdest part is that my whole website is in Russian - not a single weird character.
Any ideas ? What I need to change to get this thing working ?

---

### Post by januzi on 2009-10-10
You could add:
```

mysql_query( "set names 'utf8'" ) ;

```right after You select database.
Check also 
```

<?php
ini_set('default_charset', 'utf-8');
?>

```And make sure that You sent proper charset in the <head>.

---

### Post by OpenGuard on 2009-10-10
> **januzi said:**
> You could add:
```

mysql_query( "set names 'utf8'" ) ;

```right after You select database.
Check also 
```

<?php
ini_set('default_charset', 'utf-8');
?>

```And make sure that You sent proper charset in the <head>.

Thank you - single-quotes in the first examples finally worked ( already found a similar solution, tough, there were no quotes, which resulted in the same error ).

---

