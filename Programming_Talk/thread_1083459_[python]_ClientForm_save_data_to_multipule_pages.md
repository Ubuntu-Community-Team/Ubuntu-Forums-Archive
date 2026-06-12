---
title: "[python] ClientForm save data to multipule pages"
date: 2009-03-01
forum: Programming Talk
---

### Post by Pyro.699 on 2009-03-01
Hello,

So i'm using ClientForm and am opening a webpage with forms on it. When i add the data to the field (with ClientForm) and run **submitted_form = urlopen(form.click()).read() **it displays the proper infomation. But how would i open another page while keeping the same data?

So heres a running example...

_page1.php_
```

<form action="page2.php" method="POST">
<input type="text" name="txt1">
<input type="submit">
</form>

```_page2.php_
```

<form action="page3.php" method="POST">
<input type="text" name="txt2">
<input type="hidden" name="hidden_txt1" value="<?php echo $_POST['txt1']; ?>">
<input type="submit">
</form>

```_page3.php_
```

<?php
echo $_POST['hidden_txt1'];
echo $_POST['txt2'];
?>

```_script.py_
```

from urllib2 import urlopen
from ClientForm import ParseResponse

response = urlopen("page1.php")
forms = ParseResponse(response, backwards_compat=False)
form = forms[0]

form['txt1'] = "text1"

responce2 = urlopen(form.click()).read()
forms2 = ParseResponse(response2, backwards_compat=False)
form = forms2[0]

form['txt2'] = "text2"


print urlopen(form.click()).read()

```[quote=script.py]
text1
text2
[/quote]

That would be how it would work. It carries the data from one page onto the next.

Thanks
~Cody Woolaver

---

### Post by prshah on 2009-03-01
> **Pyro.699 said:**
> [/code]_script.py_
```

...
[color=red]responce2[/color] = urlopen(form.click()).read()
forms2 = ParseResponse(response2, backwards_compat=False)
...

```


I don't have an answer to your problem, but I would like to point out that the variable response2 has a typo...

---

