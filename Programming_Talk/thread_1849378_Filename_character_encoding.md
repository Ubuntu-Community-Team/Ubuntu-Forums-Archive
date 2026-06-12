---
title: "Filename character encoding"
date: 2011-09-24
forum: Programming Talk
---

### Post by ingeva on 2011-09-24
I was surprised to discover that the filename encoding in Ubuntu is actually NOT UTF-8.
First I thought that the php function mb_convert_case was buggy, but checking with real UTF-8 string showed that it wasn't.
Most of us (I guess) know about the discrepancy between the infamous NTFS system and Linux' ext-4, and learnt to overcome that (for instance by telling SMB that it's UTF-8!).
But when I convert filenames to lower case some national characters disappear.
"Øvinger" becomes "vinger").

I use the php function mb_convert_case, and the default character set is UTF-8.

Searching the Net I only find that the file system stores the filenames without really caring about the encoding. But I stored the files and specified a filename. UTF-8 is my default character set. Why are the filenames not stored as UTF-8? How can I correct them?

Thanks!

---

### Post by Arndt on 2011-09-24
> **ingeva said:**
> I was surprised to discover that the filename encoding in Ubuntu is actually NOT UTF-8.
First I thought that the php function mb_convert_case was buggy, but checking with real UTF-8 string showed that it wasn't.
Most of us (I guess) know about the discrepancy between the infamous NTFS system and Linux' ext-4, and learnt to overcome that (for instance by telling SMB that it's UTF-8!).
But when I convert filenames to lower case some national characters disappear.
"Øvinger" becomes "vinger").

I use the php function mb_convert_case, and the default character set is UTF-8.

Searching the Net I only find that the file system stores the filenames without really caring about the encoding. But I stored the files and specified a filename. UTF-8 is my default character set. Why are the filenames not stored as UTF-8? How can I correct them?

Thanks!

PHP is not my favourite language, but I have been exposed to it. If you just print the lowercased string to the terminal, is it correct then? Can you take a correct string, with Ø, and create a file with that name?


The file operations as such work fine for me, in bash:

```
$ mkdir test
$ cd test
$ touch Øvinger
$ touch øvinger
$ ls
øvinger  Øvinger
```

---

### Post by ingeva on 2011-09-24
> **Arndt said:**
> PHP is not my favourite language, but I have been exposed to it. If you just print the lowercased string to the terminal, is it correct then? Can you take a correct string, with Ø, and create a file with that name?

I have experimented some more, and found that the problem may be elsewhere. The filename encoding is definitely OK. When I create a filename using UTF-8, the filename is encoded as UTF-8. The problem may be in displaying the filename in terminal, using print_f.

I wrote a php script which created the file "Øvinger.php", and it made a file behaving  exactly the same way.

What I'm doing is this:
A website, on the server side, contains multiple scripts in more than one directory. For simplicity, the names can have any combination of lower/upper characters, but when converted to lower case, two files can not have the same name.
In my script only the lower case names are used, so the first time the site is called (in a session) the script directories are scanned and a table is build that converts "short" to "long" filenames. The short filenames are always in lower case. This means that I can execute any file like this:

include longname ("lower-case-name");
because the function "longname"  returns the complete path of the file to be included.

I actually think that I have been fooled a little here. My strategy will probably work.

Here's my code for creating the "$_SESSION['long'] array:
```

if (!isset ($_SESSION['long']))
{    $_SESSION['long'] = array();
    foreach ($filetypes as $dir)
    {    $files = glob ($dir.DS."*.$dir");
// Save all info for each file. This means that we won't have to
        foreach ($files as $file)        // search any more.
        {    $name = lowercase(name_only ($file));
            $_SESSION['long'][$name] = $file;
        }
    }
}

```DS is the Directory Separator (ususally "/")
$filetypes is the array containing the file types I want to store
name_only is a function to return only the filename
lowercase is the function to return the lower case of a string with the defined encoding

---

### Post by ingeva on 2011-09-24
I think I have found the bug.
I use an UTF-8 lower-case string as the index in an array, and PHP does not allow all characters in index names. Thus the "ø" is stripped off, making this method very inconvenient.
I haven't checked for other characters (yet), but I assume that other quite legal UTF-8 characters are also not allowed (like Æ, Ø, Å, æ, ø, å, Ä, ä, Ö, ö etc).

Edit
I have reported this bug to the php developers.

---

### Post by Arndt on 2011-09-24
> **ingeva said:**
> I think I have found the bug.
I use an UTF-8 lower-case string as the index in an array, and PHP does not allow all characters in index names. Thus the "ø" is stripped off, making this method very inconvenient.
I haven't checked for other characters (yet), but I assume that other quite legal UTF-8 characters are also not allowed (like Æ, Ø, Å, æ, ø, å, Ä, ä, Ö, ö etc).

Edit
I have reported this bug to the php developers.

I'm not sure where that bug is, but this code "works" for me. Does it do something essentially different from yours?

```
<?php

$files = array("øpp", "Øpp");
foreach ($files as $file)
{
  print $file;
  print "\n";
}

?>
```

---

### Post by ingeva on 2011-09-24
> **Arndt said:**
> I'm not sure where that bug is, but this code "works" for me. Does it do something essentially different from yours?

```
<?php

$files = array("øpp", "Øpp");
foreach ($files as $file)
{
  print $file;
  print "\n";
}

?>
```

Certainly.
In your case, the indexes are 0 and 1, and the contents are UTF-8 strings.
In my case, the index was a UTF-8 string, and the 2-byte character was stripped off.

The php developers attempted to reproduce the error but also did it wrong, by not using an assignment but definition, similar to this:

$_SESSION['long'] = array ('øre'=>"php/ØRE.php', 'søke' => 'php/SØKE.php');

which is NOT the same as

$_SESSION['array']['øre'] = 'php/ØRE.php';
$_SESSION['array']['søke'] = 'php/SØKE.php';

I haven't tested this in practice yet but I will as soon as the sun rises .... :)

---

### Post by ingeva on 2011-09-25
I have found the cause of this error. It is not in the array indexes,  but in the function "basename" - which strips off the first character if  it's a two-byte character in the UTF-8 character set.

However,  the error ONLY occurs when the script runs on MY OWN local server  (Apache), and NOT when run either stand-alone locally or from a remote  host.

Therefore I assume that the bug is caused by some kind of relation between my versions of php (5.3.5) and apache (2.0).

---

