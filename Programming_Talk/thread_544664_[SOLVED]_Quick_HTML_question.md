---
title: "[SOLVED] Quick HTML question"
date: 2007-09-06
forum: Programming Talk
---

### Post by Bachstelze on 2007-09-06
Here's the deal :

[http://fkraiem.no-ip.org/system.php](http://fkraiem.no-ip.org/system.php)

I've been pulling my hair on this for hours and I just can't manage to make the three boxes at the same width. Here are the sources :

**system.php**

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
        <title>fkraiem.no-ip.org - System infos</title>
        <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
        <link rel="stylesheet" type="text/css" href="home.css" />
</head>
<body>

<h1>fkraiem.no-ip.org - System infos</h1>
<h2>Server</h2>
<div style="width:600px;">
<pre>
<?php echo(htmlentities(shell_exec('uname -a'), ENT_QUOTES)) ?>
</pre>
<h2>Uptime</h2>
<pre>
<?php system("uptime"); ?>
</pre>
</div>
<h2>Disk usage</h2>
<table class="system">
        <thead class="system">
                <tr class="system">
                        <td class="system">Filesystem</td>
                        <td class="system">Total</td>
                        <td class="system">Used</td>
                        <td class="system">Available</td>
                        <td class="system">% Used</td>
                        <td class="system">Mounted on</td>
                </tr>
        </thead>
<?
function toCorrectUnit($koValue)
        {
                $tmp = $koValue / 1024;
                if($tmp < 1024)
                {
                        $tmp = round($tmp * 10) / 10 . ' MiB';
                }
                else
                {
                        $tmp /= 1024;
                        $tmp = round($tmp * 10) / 10 . ' GiB';
                }
                return $tmp;
        }
exec('df -k', $diskSpace);
$i = 0;
foreach($diskSpace as $line)
        {
        $i++;
        $cell1 = trim(substr($line, 0, 11));
        $cell2 = toCorrectUnit(trim(substr($line, 12, 10)));
        $cell3 = toCorrectUnit(trim(substr($line, 22, 9)));
        $cell4 = toCorrectUnit(trim(substr($line, 32, 9)));
        $cell5 = trim(substr($line, 45, 4));
        $cell6 = trim(substr($line, 50));
        if($cell1 == 'devfs' || $cell1 == 'Filesystem') continue;
                echo("
                <tr class=\"system\">
                        <td class=\"system\">$cell1</td>
                        <td class=\"system\">$cell2</td>
                        <td class=\"system\">$cell3</td>
                        <td class=\"system\">$cell4</td>
                        <td class=\"system\">$cell5</td>
                        <td class=\"system\">$cell6</td>
                </tr>");
        }

?>
</table>
<h2>Versions</h2>
<ul>
<li>PHP : <i><? echo phpversion(); ?></i></li>
<li>MySQL : <i>
        <?
        mysql_connect('localhost', 'root', 'xxx');
        echo mysql_get_server_info();
        ?></i></li>
</ul>
<div class="bottom">
<a href="http://www.apache.org/" target="_blank"><img src="images/apache.png" border="0" alt="Apache" /></a>&nbsp;&nbsp;&nbsp;<a href="http://www.mysql.com" target="_blank"><img src="images/MySQL.png" border="0" alt="MySQL" /></a>&nbsp;&nbsp;&nbsp;<a href="http://www.php.net" target="_blank"><img src="images/php.png" border="0" alt="PHP" /></a>&nbsp;&nbsp;&nbsp;<a href="http://www.openbsd.org" target="_blank"><img src="images/openbsd.png" border="0" alt="OpenBSD" /></a><br />
<a href="http://www.amd.com" target="_blank"><img src="images/amd.png" border="0" alt="Advanced Micro Devices" /></a>&nbsp;&nbsp;&nbsp;<a href="http://www.hp.com" target="_blank"><img src="images/hp.png" border="0" alt="Hewlett-Packard" /></a>
  <p style="padding-top:30px;">
    <a href="http://validator.w3.org/check?uri=referer" target="_blank"><img
        src="http://www.w3.org/Icons/valid-xhtml10"
        alt="Valid XHTML 1.0 Transitional" height="31" width="88"
        border="0" /></a>
  </p>
</div>
</body>
</html>

```

**home.css**

```
body {
        background:#BBDDFF;}

html {
        font-family:sans-serif;
        font-size:small;
        color:#000066;}

pre {
        width:600px;
        font-size:medium;
        font-family:monospace;
        border:1px dashed;
        margin:2em;
        padding:10px;}

table.system {
        width:600px;
        border:1px dashed;
        margin:2em;}

thead.system tr.system td.system {
        border-bottom:1px solid;}

thead.system td.system {
        font-weight:bold;}

td.system {
        padding:0.2em 1em;
        margin:0;}

div.bottom {
        text-align:center;
        margin-top:50px;}

```

I'm sure it' ridiculously simple but I've tried every way I could think of and never succeeded. Any ideas ?

---

### Post by Alp82 on 2007-09-06
I just looked into your code and i'd try to put that table (the third box) inside the div-block: "<div style="width: 600px;">". Maybe that will help.

---

### Post by fdhdghdg on 2007-09-06
This is why

pre {
	width:600px;
        font-size:medium;
        font-family:monospace;
        border:1px dashed;
        margin:2em;
        [COLOR="Red"]padding:10px;[/COLOR]}

Simple ugly fix

table.system {
	[COLOR="Red"]width:620px;[/COLOR]
        border:1px dashed;
        margin:2em;}

---

### Post by aks44 on 2007-09-06
> **fdhdghdg said:**
> This is why

pre {
	width:600px;
        font-size:medium;
        font-family:monospace;
        border:1px dashed;
        margin:2em;
        [COLOR="Red"]padding:10px;[/COLOR]}

Simple ugly fix

table.system {
	[COLOR="Red"]width:620px;[/COLOR]
        border:1px dashed;
        margin:2em;}

My HTML/CSS may be a bit rusty, but isn't padding supposed to be *inside* the box (as opposed to margins that are outside)? Unless I'm confusing with IE's quirks mode (long time I didn't bother with that...)?

---

### Post by Bachstelze on 2007-09-06
fdhdghdg, that did the trick, thanks :)

---

