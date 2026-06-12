---
title: "stupid php issue"
date: 2008-12-30
forum: Programming Talk
---

### Post by lapubell on 2008-12-30
i'm hitting my head against a wall, not sure why php does this, but here it is...

I have a textarea input box that i want to parse.  i'm getting annoyed with a little issue that pops up when I search this string later (it's stored in mysql).  The issue could be solved if php could return the string in a one line statement.

so my question, is there a way to turn a multiline string to a single line string?

i've tried:
```

1. $newString = explode("\n", "", $orgString);
2. $chars = str_split($orgString);
   foreach ($chars as $value) {
      if ($value != "\n") {
         $string .= "$value";
      }
   }
3. others...

```

any help would be awesome...

---

### Post by lapubell on 2008-12-30
not the most elegant solution, but i got it.  doing this:

```

$chars = str_split($string);
foreach ($chars as $value) {
    if ($value != "\n") {
        $string .= trim($value);
    }
}

```

---

### Post by slavik on 2008-12-30
why not join all the strings into one then do a preg_relace to remove all \n ???

EDIT: besides, you're breaking the string(s) into chars and then iterating through them ... php's arrays aren't all that great.

---

### Post by catchmeifyoutry on 2008-12-30
If I get your problem correctly, two solutions come to mind:
[PHP]
<?php
$s = "hello\nworld";
$s = implode('', explode("\n",$s)); // solution 1, see http://nl.php.net/manual/en/function.implode.php
$s = strtr($s, array("\n" => '')); // OR, solution 2, see http://nl3.php.net/manual/en/function.strtr.php
echo $s;
?>
[/PHP]
You could also replace the \n by a single space, if you would want to.

---

### Post by Reiger on 2008-12-31
Why not do a:
```

$str = preg_replace("/[\n\r]/",'',$str);

```

But for the sake of curiosity: what was the original problem/issue?

---

