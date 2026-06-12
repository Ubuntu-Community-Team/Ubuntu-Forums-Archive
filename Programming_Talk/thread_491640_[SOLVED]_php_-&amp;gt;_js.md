---
title: "[SOLVED] php -&amp;gt; js"
date: 2007-07-03
forum: Programming Talk
---

### Post by x1a4 on 2007-07-03
How do I pass value of php array to javascript array?
Thank you.

---

### Post by avik on 2007-07-03
You can loop through the PHP array and echo out the items so they are in the Javascript array notation:

```

echo "js_array = ["
foreach($php_array as $item) { echo "'" . $item . "',"; }
echo "];"

```

Can someone check this for me?  I haven't used PHP in a long time.

---

### Post by Praill on 2007-07-03
> echo "js_array = ["
$phparray=array();
$phparray[0]="something";
$phparray[1]="something2";
for($i=0 ; $i<sizeof($phparray) ; $i++) { echo "'" . $phparray[i] . "',"; }
echo "];"

I think this would be more the way to do it.

---

### Post by avik on 2007-07-03
Actually, foreach works too: [http://us2.php.net/manual/en/control-structures.foreach.php]("http://us2.php.net/manual/en/control-structures.foreach.php").  And I assumed that $php_array was initialized.

Still, both ways are fine.

Hope that answers your question, x1a4.

---

### Post by x1a4 on 2007-07-03
Thank You.

---

