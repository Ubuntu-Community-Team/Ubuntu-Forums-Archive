---
title: "parsing command line options in perl help!"
date: 2006-04-06
forum: Programming Talk
---

### Post by garretwp on 2006-04-06
I am slowly learning perl and I am trying to learn how to parse command line options into my script in perl. My problem is that when I try some simple scripts from the web to see how they work, they do not work at all! I need some help here. here is an example: 


#!/usr/bin/perl
########################################################
# Example perl program using Getopt to get command line
# arguments passed to a program.
#
# This example can take 2 parameters
# -h --help
# -v --verbose
#
########################################################
use Getopt::Long;
# initialize the parameter options
$help = '';
$verbose = '';
#call the function passing the param name and variable to assign the value to
GetOptions ('h|help' => $help,
          'v|verbose' => $verbose);

if ($help){
print "The help parameter was supplied to the programn";
}
if ($verbose){
print "The verbose parameter was supplied to the programn";
}
exit(0);

Get anyone help shed light to me on this problem? Again I am new to perl and to any programming lang. and would appreciate any help that you might give me!

Garrett

---

### Post by jrib on 2006-04-07
According to [http://www.unix.org.ua/orelly/perl/prog3/ch32_27.htm](http://www.unix.org.ua/orelly/perl/prog3/ch32_27.htm), it seems that 

```

GetOptions ('h|help' => $help,
'v|verbose' => $verbose);

```

should be: 

```

GetOptions ('h|help' => \$help,
'v|verbose' => \$verbose);

```

This seems to work for me, but I know nothing about perl :)

---

### Post by garretwp on 2006-04-07
_jason,


Thanks for the info! I was just going to post the exact same info that you provided after finding it many hours later! I do not know why that the examples online do not show the \ on the variables! Thank you again for your help! It can be a real pain to learn something and become stuck for hours at time and to find out it was something so simple! That is the way of life! Slowly but surely I will become better in perl. I hope perl was a good choice for learning a first lang.

Garrett

---

### Post by jrib on 2006-04-07
[QUOTE=garretwp]_jason,


Thanks for the info! I was just going to post the exact same info that you provided after finding it many hours later! I do not know why that the examples online do not show the \ on the variables! Thank you again for your help! It can be a real pain to learn something and become stuck for hours at time and to find out it was something so simple! That is the way of life! Slowly but surely I will become better in perl. I hope perl was a good choice for learning a first lang.

Garrett[/QUOTE]

You can view a lot of o'reilly's about perl here: 
[http://www.unix.org.ua/orelly/](http://www.unix.org.ua/orelly/) .  I learned the basics of perl once, but decided not to really get into it.  I'm spending my type learning python, which I really like.  Good luck!

---

