---
title: "PHP Error message"
date: 2019-07-13
forum: Programming Talk
---

### Post by mike.lussier on 2019-07-13
I have a simple php script that I have been working on. to debugf it I ran it from command line. 
python test2.php
I get this error
```

root@desktop:/var/www/# python test2.php
  File "test2.php", line 1
    <?php
    ^
SyntaxError: invalid syntax

```

here is the code
```

<?php
$command = "cat /var/log/_gateway-syslog.log");
$raw_output = shell_exec($command);
$output = process_output($raw_output):
echo "<pre>$output</pre>";

function  process_output($text)
{
  // do your text processing here instead of using a shell command pipeline in shell_exec()
  cat /var/log/_gateway-syslog.log | grep -a 20.254
 return $processed_text;
}


```

---

### Post by norobro on 2019-07-13
Think about your command line for a minute:```
root@desktop:/var/www/# [COLOR=#ff0000]python[/COLOR] test2.php
```Is this a tutorial or homework? I ask because of the comment line:```
  // do your text processing here instead of using a shell command pipeline in shell_exec()
  cat /var/log/_gateway-syslog.log | grep -a 20.254
```I interpret that to mean that you should use php functions to open and process the file. To use cat and grep, which are shell commands, you will have to use exec() or shell_exec().

---

### Post by SeijiSensei on 2019-07-13
You need to use the php command-line program if you want to test your script. Why would you think python knows anything about PHP?

```
php /path/to/script.php
```

Also there's an extraneous right parenthesis in line two.

---

