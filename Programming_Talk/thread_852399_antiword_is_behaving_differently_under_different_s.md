---
title: "antiword is behaving differently under different situations"
date: 2008-07-07
forum: Programming Talk
---

### Post by skelooth on 2008-07-07
Hello all, I know that antiword is a small obscure command line utility but I'm hoping I can find someone that can help me solve this issue. The problem is as follows: When I run antiword off of the command line using ```
antiword -w 1000 myfile.doc
``` it works fine. However, when I try to run it on an uploaded file via backticks antiword surrounds bold words with asterisks and replaces all bullets with ordinary periods.

Does anyone have any idea? I just need to automate some simple word document processing which normally works but for whatever reason I'm getting this weird behavior now. Here are the relevant code snippets.

```
<?php
$command="perl doc2html.pl {$_FILES['file']['tmp_name']}  {$_FILES['file']['name']} ";
`$command`;
header( 'Location: index.php' ) ;
?>
```

then inside doc2html....

```
$_= `antiword -w 1000 $input`;
```

---

### Post by odyniec on 2008-07-07
> **skelooth said:**
> then inside doc2html....

```
$_= `antiword -w 1000 $input`;
```
What is $input? Can you post the whole doc2html.pl file?

---

### Post by skelooth on 2008-07-08
$input is just the file name, ie: myfile.doc

doc2html.pl is just a bunch of regular expressions to extract and process the file into what I need. The regular expressions worked properly. The problems didn't begin until I tried calling it via subshell from a php script.

---

### Post by ghostdog74 on 2008-07-08
well, since you are on php, why not do everything in php. PHP has regular expressions too. Also you can call antiword from PHP too.

---

### Post by skelooth on 2008-07-08
That's not the point :) I prefer perl, and the code to do what I needed was much smaller and cleaner in perl.

The script obviously works now, because I changed the regular expressions, but it would be good to know why that happened being that I rely on antiword for a number of inshop utilities. I don't understand what about calling it from a subshell caused that behavior. the -f switch also has no effect on it.

When it first started turning my bullets into periods I thought I was just losing my mind.

---

### Post by prasadnaidu on 2009-04-14
> **ghostdog74 said:**
> well, since you are on php, why not do everything in php. PHP has regular expressions too. Also you can call antiword from PHP too.

i have installed antiword in /home/myusername/bin and i was able to execute this thru command prompt.
but when i tried to run thru php i was not able to get the result. .i get empty array.

1. initially by default when i said make install the following commands executed.
mkdir -p /root/bin
cp -pf antiword kantiword /root/bin
mkdir -p /root/.antiword
cp -pf Resources/* /root/.antiword

THEN I CHANGED TO THE FOLLOWING : I EXECUTED BELOW CODE AS MY location is so.

mkdir -p /home/myusername/bin
cp -pf antiword kantiword /home/myusername/bin
mkdir -p /home/myusername/.antiword
cp -pf Resources/* /home/myusername/.antiword


i changed all the files related to antiword to chown apache:apache
i have given all the chmod function to chmod -R 777

but still when i execute the following i am getting empty array.
<?php
exec('/home/myusername/bin/antiword -t /home/myusername/public_html/word/test/test.doc', $output);
var_dump($output);
?>

my site is hosted in /home/myusername/public_html is my document root

here is my env variables
PATH=/usr/kerberos/sbin:/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/home/myusername/bin
my etc/passwd file has following entry
apache:x:NN:NN:apache:/home/ramakanth:/bin/bash

where NN:NN is port number

i have sent u what ever the details i know....

Please help me in this regard. I am really pissed off with this issue.... and please please help me....
Its has been over 3 days that i am working on this.

Thanks in Advance.
Prasad

---

### Post by Arndt on 2009-04-14
> **skelooth said:**
> Hello all, I know that antiword is a small obscure command line utility but I'm hoping I can find someone that can help me solve this issue. The problem is as follows: When I run antiword off of the command line using ```
antiword -w 1000 myfile.doc
``` it works fine. However, when I try to run it on an uploaded file via backticks antiword surrounds bold words with asterisks and replaces all bullets with ordinary periods.

Does anyone have any idea? I just need to automate some simple word document processing which normally works but for whatever reason I'm getting this weird behavior now. Here are the relevant code snippets.

```
<?php
$command="perl doc2html.pl {$_FILES['file']['tmp_name']}  {$_FILES['file']['name']} ";
`$command`;
header( 'Location: index.php' ) ;
?>
```

then inside doc2html....

```
$_= `antiword -w 1000 $input`;
```

I don't know what antiword is, so this is just a loose guess: could the differing behaviour have to with the fact that in one case, you have a terminal as output, and in the other, you don't? Maybe there is a command option to antiword to force the one or other behaviour.

For 'ls', for example, there is: it lists one column if the output is a file or pipe, and several columns if it's a terminal.

---

### Post by ghostdog74 on 2009-04-14
try this
```

$output = shell_exec("antiword -t test.doc");
print $output;

```

---

