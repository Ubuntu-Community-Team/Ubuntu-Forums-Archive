---
title: "server side script"
date: 2011-01-26
forum: Programming Talk
---

### Post by theflayindutchmn on 2011-01-26
Hi,

There may be a better place to ask this question (please say if so).

I'm a grad student at a university; the departement I'm in hosts websites for gradstudents and faculty if we build a site. 

I'd like to run a (simple) server side script when someone visits my site, perhaps by clicking on a link.

I'll ask my question first, and then state the problem. Is there a way to check what permissions I have (to run scripts), without help from the sysadmin. Is there another way to call a python script (or other, shell commands, etc)?

Problem:

I've tried this with php's ecec and shell_exec commands. They only seem to work for running 'whoami' and 'pwd', but not even for 'ls' or '/bin/ls', let alone running a python (or other) script. These do work if I ssh in and run the php manually (php -f test.php), but when I access my page thought the web, nothing happens. 

To be clear, this is what I'm running:

```
<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
<?php
$output = shell_exec('pwd');
echo $output;
?>
</body>
</html>
```

This snippet works both through the web, and ssh, running php manually. Now if I substitute 

```
$output = shell_exec('ls');
```

then I only get working results via ssh, php manually, not via the web. being able to run 'ls' seems like a necessary condition to running a python script.

I've asked our sysadmin for help (I'm guessing it's a permission issue), but to no avail; I don't think bugging him further is going to get me anywhere.

The site runs on Apache/2.2.3 (CentOS).

I don't know much about web development, so thanks in advance for any help or suggestions.

-nick

---

