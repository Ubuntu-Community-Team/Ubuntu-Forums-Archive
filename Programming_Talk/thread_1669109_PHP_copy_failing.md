---
title: "PHP copy failing"
date: 2011-01-17
forum: Programming Talk
---

### Post by GarySm on 2011-01-17
I'm getting a problem with the PHP copy function. It fails when I use it to copy a 6Gb file.

-rw-r--r-- 1 root       root       4294967296 2011-01-17 10:31 tape-17Jan2011-1025.tap
-rw-r--r-- 1 root       root       6831937996 2011-01-17 10:25 tape.tap

The code:
[PHP]
$backupFilename = 'tape.tap';
$newName = "tape-" . date("dMY-Hi", filemtime($backupFilename));
if(!copy($backupFilename, "$newName.tap"))
{
    die("Error in copy operation");
}
[/PHP]but if i use exec to run 'cp' it works without errors:

-rw-r--r-- 1 root       root       6843004548 2011-01-17 12:25 tape-17Jan2011-1201.tap
-rw-r--r-- 1 root       root       6843004548 2011-01-17 12:01 tape.tap

[PHP]
    exec("cp $backupFilename $newName.tap");
[/PHP]php -v
PHP 5.3.3-1ubuntu9.1 with Suhosin-Patch (cli) (built: Oct 15 2010 14:17:04)
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies

---

