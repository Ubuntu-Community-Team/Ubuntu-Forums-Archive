---
title: "Bash help needed"
date: 2007-06-21
forum: Programming Talk
---

### Post by Naps on 2007-06-21
Hello,

I'm trying to proccess some tcpdump files using bash script.


I have 500mb files from tcpdump in format : abc and the next one is abc1 , abc2 , abc3 and so goes on.

I've made a simple bash script

But it counts only until abc9.

```

while [ `ls -1|wc -l` != "1" ]; do
  last=`cat $ROOT/lasttcldumpfile.txt`
  current=${last:0:3}`expr ${last:1:3} + 1`
  echo  Current is $current
  echo The counter is $COUNTER
  let COUNTER=COUNTER+1
  gzip -1 $current
  rm $current.gz
  echo $current > $ROOT/lasttcldumpfile.txt
done

```

Can someone help me out?


thx,

Naps

---

### Post by MEW on 2007-06-21
I think it would be much simpler to do something like this:
```

for File in abc*
do
echo $File
gzip -1 $File
rm $File
done

```

---

### Post by yabbadabbadont on 2007-06-21
That would be easier, but he may get an "arg list too long" error if there are enough files present.

---

### Post by MEW on 2007-06-21
What I do in that situation is something like
```
for File in abc1*
```
and then 
```
for File in abc2*
```
and so on, until there are few enough files left that
```
for File in abc*
```
starts working.

---

### Post by yabbadabbadont on 2007-06-21
You could probably use find with xargs to handle it too.

---

### Post by Naps on 2007-06-21
No i want to get them in the right order.

That's why i prefer this method.


btw fixed :)

```


 current=${last:0:3}`expr ${last:3} + 1`


```


but i don't know how to start it if there is no entries at  lasttcldumpfile.txt

---

### Post by yabbadabbadont on 2007-06-21
> **Naps said:**
> No i want to get them in the right order.

That's why the sort command exists...  :D

Anyway, I'm glad you figured it out.

---

### Post by arvevans on 2007-06-21
for filename in abc abc1 abc2 abc3
    do
    [your parsing code here]
    done

---

### Post by Naps on 2007-06-21
> **Naps said:**
> 
but i don't know how to start it if there is no entries at  lasttcldumpfile.txt



And what about this one..


i've tried..


i mean if there is no file.


how can i write a new file and start it..

---

### Post by Mr. C. on 2007-06-21
> **Naps said:**
> 
but i don't know how to start it if there is no entries at  lasttcldumpfile.txt

What is it exactly that you want to do when that file is empty ?

Your code:
```
gzip -1 $current
rm $current.gz
```
Seems like a very expensive equivalent to :

```
rm $current
```

In the future when you do things like this, try to be consistent with your naming patterns to ease processing of the border cases:

abc0
abc1
abc2
...
abc2000

MrC

---

### Post by hasimir44 on 2007-06-22
First off, sorry, but this seems like a job for perl, not bash (because of the *natural* sort). Anyway, I'm assuming that every file starts with abc (otherwise this sort routine will not work..), followed by a number that's not zero padded. the my_sort subroutine is just stripping the numbers off each filename, then zero padding the hell out of them (not sure how many files you have there..) before comparing them. eh, it works. 

also, not sure why you're just compressing and then immediately deleting the files.. but if that's what you want, just uncomment those 2 lines in the foreach loop. 

```
#!/usr/bin/perl

my @files = glob("abc*");
my $count = 0;

sub my_sort {
  $a =~ /(\d+)/;
  $num1 = $1;
  $num1 = 0 . $num1 while length($num1) < 10;
  $b =~ /(\d+)/;
  $num2 = $1;
  $num2 = 0 . $num2 while length($num2) < 10;
  $num1 cmp $num2;
}

@sfiles = sort my_sort @files;

foreach my $file (@sfiles) {
  $count++;
  print "Working with: $file\n";
  #system("gzip -1 $file");
  #unlink("$file.gz");
}

```

example..

```
Working with: abc1
Working with: abc2
Working with: abc3
Working with: abc4
Working with: abc5
Working with: abc6
Working with: abc7
Working with: abc8
Working with: abc9
Working with: abc10
Working with: abc11
Working with: abc12

```

---

### Post by hasimir44 on 2007-06-22
> In the future when you do things like this, try to be consistent with your naming patterns to ease processing of the border cases:

I think what he means is - since the files all contain the same alpha characters at the beginning, sorting would be much easier if you zero padded the following numbers so every filename had the same length.. or you can just use perl :)

---

### Post by Mr. C. on 2007-06-22
There's no need to force a language choice, esp when the criteria are equivalent.  The standard sort utility works fine:
```

$ cat x   
abc0
abc
abc23
abc2
abc1
$ sort < x
abc
abc0
abc1
abc2
abc23
```
Padding isn't necessary, and creates an artificial upper limit (eg 001 implies a maximum of 999 before padding is foiled).  My point wasn't about padding, but about keeping the naming structure the same for easy matching: eg. the first 10 are abc0 ... abc9, the next 10 are abc10... abc19, or for pattern patching like abc\d{2}.

MrC

---

### Post by hasimir44 on 2007-06-22
```
The standard sort utility works fine:
```
umm... actually you're wrong. if you test with more files you'd catch that.. 

```
prompt> cat x
abc
abc1
abc2
abc3
abc4
abc5
abc6
abc7
abc8
abc9
abc10
abc11
abc12
abc13
abc14
abc15
abc16
abc17
abc18
abc19
abc20
abc21

```

sort will put abc10 before abc2.

```
prompt> sort x
abc
abc1
abc10
abc11
abc12
abc13
abc14
abc15
abc16
abc17
abc18
abc19
abc2
abc20
abc21
abc3
abc4
abc5
abc6
abc7
abc8
abc9
```

> There's no need to force a language choice, esp when the criteria are equivalent. 

Please, I'm begging you.. post a natural sort routine for bash. This would be very useful, but I'm too lazy to figure it out on my own when perl does it so much easier.

---

### Post by Mr. C. on 2007-06-22
You need to learn to read the man pages and practice using the utilities:

sort -k 1.4n  x

MrC

---

### Post by Naps on 2007-06-22
First of all thx for you help..


Actually i want to get all the files of  the directory instead of the file being proccessed by tcpdump.


I've managed to write this code :

```

#!/bin/bash
cd $ROOTFINAL
COUNTER=0
FLAG=0

while [ `ls -1|wc -l` != "1" ]; do
  last=`cat $ROOT/lasttcldumpfile.txt`
  if [ -e "$last" ]; then
        current=${last:0:3}`expr ${last:3} + 1`
  else
        current=abc

        echo current1 is $current
        sleep 2
  fi

  echo Current is $current
  echo The counter is $COUNTER
  let COUNTER=COUNTER+1
  gzip -1 $current
  rm $current.gz
  echo $current > $ROOT/lasttcldumpfile.txt
done

```

The problem is that tcpdump starts writting the first file : abc and then is going abc1 abc2

I want to get all the files but i'm having to get the first one and proccess to the next one.

But if i  start from abc1 and i get all of them.

---

### Post by Mr. C. on 2007-06-22
I think you are making your job far too difficult and roundabout.

You want to process each file, in order, abc, abc1, abc2, ... abcN.  Consider the following code and output:

```
$ for i in $(/bin/ls -1 abc* | sort -k 1.4n ) ; do
      echo Processing $i ...
done

Processing abc ...
Processing abc1 ...
Processing abc2 ...
Processing abc3 ...
Processing abc4 ...
Processing abc5 ...
Processing abc6 ...
Processing abc7 ...
Processing abc8 ...
Processing abc9 ...
Processing abc10 ...
Processing abc11 ...
Processing abc12 ...
Processing abc13 ...
Processing abc14 ...
Processing abc15 ...
Processing abc16 ...
Processing abc17 ...
Processing abc18 ...
Processing abc19 ...
Processing abc20 ...
Processing abc21 ...
```

What you haven't explained is how and exactly when the file lasttcldumpfile.txt gets created .  It may not be necessary, for example, if you are processing all the dump files after tcpdump has finished.  How many lines are in this file, when is it created, and by what process relative to what you are trying to do here.

MrC

---

### Post by Naps on 2007-06-22
Thx for you help.

At last i've managed to finish it.



thx again.

---

### Post by Mr. C. on 2007-06-22
You're welcome.

Share your final result so that other's can learn too.

MrC

---

### Post by hasimir44 on 2007-06-23
> sort -k 1.4n x

that is awesome! 

> You need to learn to read the man pages and practice using the utilities:

you're absolutely correct :)

---

