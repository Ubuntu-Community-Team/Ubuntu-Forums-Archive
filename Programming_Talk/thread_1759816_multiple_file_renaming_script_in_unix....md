---
title: "multiple file renaming script in unix..."
date: 2011-05-16
forum: Programming Talk
---

### Post by Blackbug on 2011-05-16
I have around 2000 files in a folder of filename as below:
 
XOY001.2011-02-20.EBS-DRIVER
XOX201.2011-01-20.FBS-DRIVER
XOQ101.2011-01-20.XYZ-DRIVER
 
I need to rename all these files to only 
XOY001
XOX201
XOQ101
 
I need to trim 2011-02-20.EBS-DRIVER like pattern.
I am able to display the trimmed filename (list of them of screen) but not sure how to use "MV" command with it.
 
I even tried to take two array's each storing original and desired set of names respectively, but still using mv command on each is creating problem
 
I tried rename command but i dont see it working properly or may be I am not using it properly.
 
I once wrote a small script to rename the .keep files of clearcase to its corresponding checkout file
```

arr=`(find . -name "*.keep" | awk -F.keep '{print$1}')`
counter=0
 
for file in ${arr[@]}
do
cp $file.keep $file
if [ "$?" -eq 0 ]
then
 flag=0
 else
 flag=1
 break
 fi
done
 
if [ $flag -eq 1 ]
then
echo "Unsuccessful"
fi

```
 
But, I need something different for this.
Can anyone help me with my problem?
 
Thanks

---

### Post by AbsolutIggy on 2011-05-16
You could try the command-line utility "mass move" (mmv) instead of writing your own script

[http://linux.die.net/man/1/mmv](http://linux.die.net/man/1/mmv)

---

### Post by Blackbug on 2011-05-16
thanks for replyin
 
but, i dont have mmv in my system and i have no rights to install it..
any other way out of this?

---

### Post by DaithiF on 2011-05-16
i would use rename, 

heres an example:
```
$ rename -n 's/\..*$//' X0Y001.2011-02-20.EBS-DRIVER
XOY001.2011-02-20.EBS-DRIVER renamed as XOY001
```

the -n flag to rename is a 'no-action' flag, it just shows what actions rename **would **perform without actually doing it.  Remove the -n once you're happy you're getting the behaviour you expect

As an example the pattern to rename above will remove all characters after the first '.'

You could apply it to all files in the directory, or all files matching a pattern, depending on your needs, e.g.:

```
$ rename -n 's/\..*$//' *DRIVER
XOY001.2011-02-20.EBS-DRIVER renamed as XOY001
etc...
```

---

### Post by vanadium on 2011-05-16
> **Blackbug said:**
> 
I tried rename command but i dont see it working properly or may be I am not using it properly.
 
I guess the latter.

```
 rename -n 's/20..-..-..\.EBS-DRIVER//' *.DRIVER
```
will display how the command would rename the files. If this is to your liking, repeat the command without the "-n" option to effectively carry out the rename operation.

Edit: DaithiF was faster and confirms this.

---

### Post by Blackbug on 2011-05-16
thanks for replyin
 
although i solved the issue by writin a small script with one loop
 
```

 for i in `ls *DRIVER*`
 do
 temp=`echo $i | awk -F.2011 '{print$1}'`
 mv $i  $temp


```
 
But, I want to try rename command as well..
 
and when i am trying to use it at my end, it does nothin
( i tried using the both example listed by vanadium and DaithiF )
 
It neither displays anything nor do.. may be i am doing somethin wrong..
please help..

---

### Post by DaithiF on 2011-05-16
Hi,
Regarding rename, its possible you have another utility by the same name installed rather than the perl-based rename that vanadium and I have been referring to.  Try **prename**
which is the actual name of the perl script that rename is linked to via the /etc/alternatives mechanism.

ie. same commands as before, but using the command prename rather than rename.  If the command isn't found then you haven't got it installed.  Its in the **perl** package, so sudo apt-get install perl should do the trick (though this should be installed anyway by default).

Secondly, regarding your script, good that it works, but there are some flaws that could be fixed:
1. for i in `ls something` is the wrong way to do this.  The shell can do filename expansion itself, theres no need for an external command and reading the results from ls like this will actually give incorrect results for certain filenames, whereas the shell always does the right thing. 
so instead use:
```
for i in *DRIVER*
```

2.  no need to use awk to trim the part you don't want, again the shell can do this itelf just fine:
```
temp=${i%.2011*}
```

3. ```
 mv $i $temp
```
this will break for filenames with spaces.  Always quote variables in cases like this:
```
mv "$i" "$temp"

```

---

### Post by Blackbug on 2011-05-16
Thanks for the suggestion on the script.
Just one point ${$i%.2011*} is not working on my bash..
it is giving following error: ${$i%.2011*}: bad substitution

---

### Post by DaithiF on 2011-05-16
> **Blackbug said:**
> Thanks for the suggestion on the script.
Just one point ${$i%.2011*} is not working on my bash..
it is giving following error: ${$i%.2011*}: bad substitution
can you see the difference between what you tried and what I suggested?

```
temp=${i%.2011*}
```

---

### Post by Blackbug on 2011-05-17
Yes, I saw now, it was a stupid mistake.
thanks for the helpin on this.

---

