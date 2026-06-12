---
title: "[SOLVED] Perl Script written in Windows"
date: 2008-12-12
forum: Programming Talk
---

### Post by Jackp90 on 2008-12-12
This script doesn't work for some reason:

```
#!/usr/bin/perl
use warnings;
use strict;
# Author: Robert
# Date: 20081211
print "Would you like to shutdown your computer? ", '(y/n)';
my $answer;
$answer = <STDIN>;
if ($answer eq "y"){
     print "Do you want a delay? ", '(y/n)', "\n";
     my $y;
     $y = <STDIN>;
     if ($y eq "n"){
          system "shutdown -s -t 120";
          }
     elsif ($y eq "y"){
             print "Time delay in seconds: ";
             my $time;
             $time = <STDIN>;
             system "shutdown -s -t $time";
             }
     else {
           print "Please enter an appropiate value: \n";
           print "Would you like a delay?", '(y/n)',"\n";
           my $y;
           $y = <STDIN>;
           if ($y eq "n"){
                system "shutdown -s -t 120";
                }
           elsif ($y eq "y"){
                   print "Time delay in seconds: ";
                   my $time;
                   $time = <STDIN>;
                   system "shutdown -s -t $time";
                   }
           else {
                 print "Error with Standard Input \n";
                 }
           }
     }
elsif ($answer eq "n"){
        print "Exiting program now \n";
        }
else {
      print "Error with Standard Input \n";
      print "Try running the program again and answer in: 'y' or 'n'", "\n";
      print "Now exiting program \n";
      }
```

this is a school project that i was working on in Windows hence the Dos

the code for disabling a shutdown in dos is 

"shutdown -a"

in case anyone gets it to work . . .

---

### Post by mssever on 2008-12-12
See the Ubuntu Forums policy on homework.

---

### Post by slavik on 2008-12-12
Reopening thread as it has some legitimacy.

Jackp90, please repost your code in [code] tags and tell us exactly what is not working? error messages and such.

---

### Post by Jackp90 on 2008-12-18
Sorry for the long reply I haven't been working on this program in a while:

> **mssever said:**
> See the Ubuntu Forums policy on homework.

I talked to my teacher and he said that it was ok to use the forums to try to get my program to work . . . . 

we are doing a student teaching unit where we chose what to teach the rest of the class I need to know what is wrong with the program that I wrote so that we wont run into this problem

> **slavik said:**
> Reopening thread as it has some legitimacy.

Jackp90, please repost your code in [code] tags and tell us exactly what is not working? error messages and such.

Sorry about [code] tags it won't happen again the only error message that I am getting is the one that I wrote into the program:

> 
Would you like to shutdown your computer? (y/n)y
Error with Standard Input
Try running the program again and answer in: 'y' or 'n'
Now exiting program
Press any key to continue . . .


This leads me to believe that there is a problem with my if then statement.

Any help would be very much appreciated.

---

### Post by ibuclaw on 2008-12-24
1) Use if you are going to read from standard input, use **chomp** to remove the trailing new lines...
```
my $answer;
$answer = <STDIN>;
**chomp $answer;**

```
This will now match both 'y' and 'n' in the if statements.

2) Sometimes pattern matching is better than an "exact" equals expression.
```
if ($answer **=~ /^[Yy]/**) {
```
If you decide to match this way, then chomp is no longer required.

Now go home and try and make us a little less sad, Capiche? :)

Regards
Iain

---

