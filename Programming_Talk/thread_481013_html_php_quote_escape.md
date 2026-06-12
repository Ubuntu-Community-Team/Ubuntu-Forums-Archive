---
title: "html php quote escape"
date: 2007-06-22
forum: Programming Talk
---

### Post by verbatim210 on 2007-06-22
here is the problem:
$name = 'O\'brian';
[PHP]echo "<td>Leader:</td> <td><input type=text value='$name' name=leader></td><tr>";[/PHP]

Any ideas? Thanks.

So far I have tried:
\ escape symbol before the '
mysql_escape_string()
addslashes()

No success, the output is always Leader: O
everything after the ' will not print.

I was going to post this, but then a friend help me solved the problem so incase anyone is interested here is the modified code that works:

[PHP]echo '<td>Leader:</td> <td><input type=text value="'; echo$name; echo'" name=leader></td><tr>';  [/PHP]

---

### Post by Modred on 2007-06-22
It would probably be simpler to just concatentate the variables together:

[php]
echo '<td>Leader:</td> <td><input type=text value="'.$name.'" name=leader></td><tr>';
[/php]

Code comes out much cleaner (and less to type, too).  Of course, you'll need to ensure $name doesn't contain quote marks, as that will throw off your HTML. You might want to try **htmlentities()** or **htmlspecialchars()** to handle that.

---

