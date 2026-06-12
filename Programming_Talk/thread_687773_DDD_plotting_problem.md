---
title: "DDD plotting problem"
date: 2008-02-04
forum: Programming Talk
---

### Post by airvine on 2008-02-04
Hello, I'm trying to debug a program and based on recommendations I've seen decided to use DDD.  The problem I have is that I can't get DDD to plot any arrays.  I searched around for a solution and found that DDD apparently does not work with gnuplot 4.0 or above so I downgraded to gnuplot 3.7 patch 3, but get the error below from the log file:

2008.02.04 16:40:53
<- "(gdb) "
#  Creating display...
#  Creating display...done.
>> "set term xlib\n"
   "set parametric\n"
   "set urange [0:1]\n"
   "set vrange [0:1]\n"
   "set trange [0:1]"
>> "set noborder\n"
   "plot \"/tmp/dddEbxqDx\" title \"T\""
2008.02.04 16:40:53
-> "output &T\n"
#  Display 2: T (enabled, scope main)
2008.02.04 16:40:53
<- "(float (*)[10]) 0xbfcef29c"
2008.02.04 16:40:53
<- "(gdb) "
#  Display 2: T (enabled, scope main, address 0xbfcef29c)
#  Cannot open load file '-bg'
#  Line 0: (No such file or directory)
<= "         Cannot open load file \'-bg\'\n"
   "         line 0: (No such file or directory)\n"
   ""
!  X error
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  10 (X_UnmapWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  17211
  Current serial number in output stream:  17214

The preference in the helpers section is : gnuplot -bg 'grey96' -font '@FONT@' -name '@NAME@' -geometry +5000+5000

Also if I clear the options the program shows the following on the command line: gnuplot -name dddplot1 [6376]: Exit 1
and the error in the log is the same except that it says file '-name' could not be found.

So it looks like for some reason DDD is not passing the plot file on to gnuplot, but I don't know how to remedy this.

I am using Gutsy on a P4 machine and DDD 3.3.11 which I installed using apt-get.  Also I'm fairly new to Linux so I could have easily done something simple wrong.

---

