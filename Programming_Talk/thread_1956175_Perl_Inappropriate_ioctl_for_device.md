---
title: "Perl Inappropriate ioctl for device"
date: 2012-04-10
forum: Programming Talk
---

### Post by hailholyghost on 2012-04-10
Hello,

I am trying to write errors from a simulation into a text file named "score.error.lna.99X".  The program is 1025 lines long so I won't paste it in entirety here.

I've read this error on other postings but it doesn't appear to apply to this case (i.e. "ioctl" can mean many different things).

However, the file comes out with the name "score.error.lna.99X\:\ Inappropriate\ ioctl\ for\ device" (escapes are not literal).

The output should be very long, about 290 spaces/line on 19,800 lines.

```
print ERRORFILE "$time B2$badb2 B3$badb3 B4$badb4 $bad02_name$bad02 $bad03_name$bad03 $bad04_name$bad04 $bad05_name$bad05 $bad06_name$bad06 $bad07_name$bad07 $bad08_name$bad08 $bad09_name$bad09 $bad10_name$bad10 $bad11_name$bad11 $bad12_name$bad12 $bad13_name$bad13 $bad14_name$bad14 $bad15_name$bad15 $bad16_name$bad16 $bad17_name$bad17 $bad18_name$bad18 $bad19_name$bad19 $bad20_name$bad20 $bad21_name$bad21 $bad22_name$bad22 $bad23_name$bad23 $bad24_name$bad24 $bad25_name$bad25 $bad26_name$bad26 $bad27_name$bad27 $bad28_name$bad28\n";
```

I've tried to get this line as short as I can get it but I can't do that any further than I already have without compromising the data.

Why does the file keep on getting renamed?  Is it because of the number of columns?

Thanks for your time,
-Dave

---

### Post by Some Penguin on 2012-04-11
What you write into a file handle would have no impact on what the file would be named.  You should post the code used to create that file handle and associated file name, instead.

---

### Post by hailholyghost on 2012-04-11
> What you write into a file handle would have no impact on what the file would be named. You should post the code used to create that file handle and associated file name, instead. 

Hi some penguin,

the original input was

```
open ERRORFILE, ">score.error.lna.99X: $!"
   or die "cannot open score.error.lna.99X: $!";
```

the problem was that I had put the "$!" in the first line.  My goof... but in more than 1000 lines of code little things like that are hard to find :p

---

