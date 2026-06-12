---
title: "gnokii and php help"
date: 2007-02-08
forum: Programming Talk
---

### Post by michie86 on 2007-02-08
Hello..

Can anyone please tell me how I can use gnokii using php commands? The exec() perhaps? If so, how? syntax please?

Thanks :)

---

### Post by rune_kg on 2008-08-02
Just do this:

```
<?
echo `gnokii --blah`;
?>
```

[http://dk.php.net/manual/en/language.operators.execution.php](http://dk.php.net/manual/en/language.operators.execution.php)

---

### Post by drubin on 2008-08-02
`` back tick operators run as system commands. (what ever is inside of them)
sell_exec();
system();


Just a few others take a look at the php.net manual for full examples.

---

