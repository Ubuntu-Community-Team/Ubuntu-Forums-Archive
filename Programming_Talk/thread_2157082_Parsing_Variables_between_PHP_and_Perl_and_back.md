---
title: "Parsing Variables between PHP and Perl and back"
date: 2013-06-24
forum: Programming Talk
---

### Post by RonaldM on 2013-06-24
Hi All

I am an absolute Newbie to Perl. In fact I don't use it, but I am required to just this once get a script to run on the Server instead of by browser. I found some ways by searches and now know how to launch the page from Perl.

However I need help with parsing variables. Simply put. I have a Perl Script that launches a PHP page. That page outputs a Variable. At the bottom of that page I have a Perl Script, which launches another page. This page runs through completes it's task and then at the bottom there is another Perl script which launches another PHP page to perform more tasks.

However where my problem lies is parsing variables between Perl and PHP.

On my first PHP page I have the following code at the bottom: (page1.php)

```
exec("perl /home/scripts/myperl1.pl $the_xml_file");
```

This code then launches the Perl Script(myperl1.pl):

```
#!/bin/sh
$var1 = $ARGV[0];
php /home/scripts/page2.php $var1;

```

Page2.php then has to retrieve the same variable in order to perform it's operations (page2.php)

```
$the_xml_file = $argv[1];
do some processing....

```


I know most of you will find errors in my script already, but please bear in mind I am flying in the dark here and just need to get this to work.

Currently with this script as it is on these pages I am getting the Perl to launch and run the PHP pages, however the variable is not being parsed from one page to another.

Any help will be greatly appreciated.

---

### Post by Lars Noodén on 2013-06-24
Why not run it like this so that the file name and other items can be passed as parameters.

```

exec("/home/scripts/myperl1.pl $the_xml_file");

```

Your perl script should begin with this line, of couse:

```

#!/usr/bin/perl

```

And the XML parser(s) you can load in from CPAN.

---

### Post by SeijiSensei on 2013-06-24
```

#!/bin/sh
$var1 = $ARGV[0];
php /home/scripts/page2.php $var1;

```

While I suggest you follow Lars's suggestion, I wonder if the problem is the trailing semicolon in the php command line.  Bash may be looking for the variable "$var1;" and, not finding it, running the PHP script without the passed parameter.  Semicolons are not necessary to delimit the end of commands in bash.  If you replace "$var1;" with "$var1", does it work?  I'm asking out of curiosity.

In bash you can use the ${variable_name} construct to delimit the variable name when it is concatenated with other text.  From the bash manual page:

 ${parameter}
The value of parameter is substituted.  The braces are required when parameter
is a positional parameter with more than one digit, or when parameter is followed 
by a character which is not to be interpreted as part of its name.

---

