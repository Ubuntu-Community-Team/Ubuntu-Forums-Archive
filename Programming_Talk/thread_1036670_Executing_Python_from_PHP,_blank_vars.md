---
title: "Executing Python from PHP, blank vars"
date: 2009-01-11
forum: Programming Talk
---

### Post by -grubby on 2009-01-11
Alright, so, I have a PHP file that's calling a Python script. I have confirmed this Python script works (in the CLI and in a seperate test PHP script), however it is not working here. The basic jist of this python script is, it accepts arguments and converts them from BBCode to XHTML, using the Postmarkup library.

The PHP code is : 
[php]
$string = shell_exec("python bbcode.py $string");  
[/php]

I have also confirmed the problem is on this line, it works fine when it is commented out (except it's lacking the bbcode conversion). 

The Python script is : 
```
[color=#408080]*#!/usr/bin/env python *[/color]
[color=#008000]**import**[/color] [color=#0000FF]**sys**[/color][color=#666666],[/color] [color=#0000FF]**lib.postmarkup**[/color] [color=#008000]**as**[/color] [color=#0000FF]**bbcode**[/color]

[color=#008000]**def**[/color] [color=#0000FF]main[/color]() :
    string [color=#666666]=[/color] [color=#BA2121]" "[/color][color=#666666].[/color]join(sys[color=#666666].[/color]argv[[color=#666666]1[/color]:])
    [color=#008000]**return**[/color] bbcode[color=#666666].[/color]render_bbcode(string)

[color=#008000]**if**[/color] __name__ [color=#666666]==[/color] [color=#BA2121]"__main__"[/color] : [color=#408080]*# prevent from running if imported*[/color]
	[color=#008000]**print**[/color] main() 

```

When the line is uncommented, $string is just an empty string. If you need more code to help, just ask!

Thanks for any contributations.

---

### Post by -grubby on 2009-01-12
I am bumping this ...

---

### Post by Reiger on 2009-01-12
Just ran a quick test which peforms a mock example:
From a terminal issue the following commands:
[php]
echo '<?php
$str = implode(" ",$_SERVER['argv']);
$py = trim(shell_exec("which python"));
$out = trim(shell_exec("$py \$(pwd)/tst.py $str"));
echo "Test result:
$out
";
?>' > /home/$USER/tst.php[/php]

```

echo '#!/usr/bin/env python
import sys

def main() :
    string = " ".join(sys.argv[1:])
    return "args: "+string

if __name__ == "__main__" : # prevent from running if imported
    print main()' > /home/$USER/tst.py
```

```

chmod +x /home/$USER/tst.php
chmod +x /home/$USER/tst.py
cd ~
php tst.php

```

Test result:
> 
Test result:
args: tst.php


So to summarize the only things I did differently: assume the python script is located at $(pwd) --which is why you have the cd to ~ given the location of the mock up scripts-- and issue a full path to the python executable --the $py bit in the crucial command string. EDIT: Therefore if the content of the $py variable holds no clue (it's not empty) and neither filling in the full path to your script may prove enlightning, then one can only assume it is in the library you import...

---

### Post by -grubby on 2009-01-14
> **Reiger said:**
> then one can only assume it is in the library you import...
[quote=nathangrubb]I have confirmed this Python script works (in the CLI and in a seperate test PHP script)[/quote]

There is nothing wrong with the library or the script.

---

### Post by Reiger on 2009-01-14
Check the content of the $py value; in other words: are you sure that there is a python interpreter available at the command python wherever "here" is?

---

### Post by -grubby on 2009-01-17
... I have Python installed and the interpreter works fine

---

### Post by Canuckelhead on 2009-01-17
try change the permissions on the python script.  make sure that anyone can use it.

I had an issue when I was running PHP - Python...  I think I was running it from apache and seem to remember that it was a permissions issue...  If that works, you'll still wan't to go back and make the restrictions more secure...  I'm at work but I'll check out my solutions more specifically when I get home.  :)

---

### Post by Canuckelhead on 2009-01-17
When apache runs a php script it invokes a subprocess which, I think, is done by :  user: 'www-data', and group 'www-data'...

you didn't say anything about apache but I am assuming that based on my similar problems a while back.

If this is the issue you can also change the apache user in the conf.

---

### Post by -grubby on 2009-01-17
I'll try changing the permissions sometime - right now the script has another bug that I need to fix (Added after the creation of this thread)

---

