---
title: "o'reilly &amp; smarty are out to kill me :("
date: 2009-10-20
forum: Programming Talk
---

### Post by lunaz on 2009-10-20
i installed smarty on jaunty server with sudo apt-get install smarty.

i'm trying to get smarty working and keep getting these errors. messing around with paths just made different errors. i turned debugging on in Smarty.class.php

> Warning: Smarty error: unable to read resource: "home/luna/public_html/myapp/smarty/templates/index.tpl" in /home/luna/public_html/smarty/Smarty.class.php on line 1092

Fatal error: Smarty error: the $compile_dir '/home/luna/public_html/myapphome/luna/public_html/smarty/templates_c' does not exist, or is not a directory. in /home/luna/public_html/smarty/Smarty.class.php on line 1092

these are the paths to stuff on the server:

```
/home/luna/public_html/myapp/smarty/templates/index.tpl
```

[http://lunaz.homelinux.net/myapp](http://lunaz.homelinux.net/myapp)
[http://lunaz.homelinux.net/myapp/smarty/](http://lunaz.homelinux.net/myapp/smarty/)
[http://lunaz.homelinux.net/smarty/](http://lunaz.homelinux.net/smarty/)

i looked at Smarty.class.php & it said the config_dir was 'configs' so i changed that to configs.

i made sure all file permissions were 644 & dir permissions 755. i tried changing dir permissions to 775 but that didn't help either.

/home/luna/public_html/myapp/smarty.php
```
<?php
// Use the absolute path for Smarty.class.php
require('/home/luna/public_html/smarty/Smarty.class.php');
$base_path = dirname(__FILE__);
$smarty = new Smarty();
$smarty->template_dir = $base_path.'home/luna/public_html/smarty/templates';
$smarty->compile_dir = $base_path.'home/luna/public_html/smarty/templates_c';
$smarty->cache_dir = $base_path.'home/luna/public_html/smarty/cache';
$smarty->config_dir = $base_path.'home/luna/public_html/smarty/configs';
?>
```

/home/luna/public_html/myapp/index.php
```
<?php
require_once("smarty.php");
$smarty->assign('test','123');
$smarty->display('home/luna/public_html/myapp/smarty/templates/index.tpl');
?>
```

/home/luna/public_html/myapp/smarty/templates/index.tpl
```
<html>
<head>
<title>i like smartys. i use to eat them by the packagefull. now i want some, dammit. :(</title>
</head>
<body>
haha {$test}.
</body>
</html>
```

---

### Post by CyberJack on 2009-10-20
The fatal error tells you that the directory where smarty keeps it's compiled templates does not exists.

[CODE]Fatal error: Smarty error: the $compile_dir '/home/luna/public_html/myapphome/luna/public_html/smarty/templates_c' does not exist, or is not a directory. in /home/luna/public_html/smarty/Smarty.class.php on line 1092[CODE]

Have you created the directory (/home/luna/public_html/myapphome/luna/public_html/smarty/templates_c)? and can the apache user write to this directory?

---

### Post by lunaz on 2009-10-20
here's the path to the dir over the net;
[http://lunaz.homelinux.net/myapp/smarty/templates_c/](http://lunaz.homelinux.net/myapp/smarty/templates_c/)

the system path is:
/home/luna/public_html/myapp/smarty/templates_c/

i don't understand where the path
home/luna/public_html/myapphome/luna/public_html/smarty/templates_c
comes from

---

### Post by CyberJack on 2009-10-21
Its defined in /home/luna/public_html/myapp/smarty.php

According to your code, you set the $base_path variable to the directory of the current file. **/home/luna/public_html/myapp/smarty.php** makes your $base_path **/home/luna/public_html/myapp/**

Then you set the template_dir, compile_dir, cache_dir and config_dir. Each of these is using the $base_path variable.
So for example the compile_dir **$base_path.'home/luna/public_html/smarty/templates_c'** will result in **/home/luna/public_html/myapp/home/luna/public_html/smarty/templates_c**.

If you want **/home/luna/public_html/myapp/smarty/templates_c/** as a result, you have to use:
[PHP]
<?php
// Use the absolute path for Smarty.class.php
require('/home/luna/public_html/smarty/Smarty.class.php');
$base_path = dirname(__FILE__);
$smarty = new Smarty();
$smarty->template_dir = $base_path.'smarty/templates';
$smarty->compile_dir = $base_path.'smarty/templates_c';
$smarty->cache_dir = $base_path.'smarty/cache';
$smarty->config_dir = $base_path.'smarty/configs';
?>
[/PHP]

---

### Post by lunaz on 2009-10-25
thanks very much for the help :)

it was that and permission issues. i chmod -R myapp/smarty directory to 777.

---

