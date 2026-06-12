---
title: "Bash greater than - less than or -lt -gt question"
date: 2010-06-22
forum: Programming Talk
---

### Post by VastOne on 2010-06-22
In the following bash script I am working on I am stuck in one area

```
#!/bin/bash

# Define Variables
csvn=`svn co http://guayadeque.svn.sourceforge.net/svnroot/guayadeque/Trunk guayadeque |grep revision |awk '{print $4}'`
tsvn=1097.
gquepath="/guayadeque"


if [ $csvn = $tsvn ]
	then
		echo "Current svn $csvn is the same as the target svn $tsvn no action required"
		exit
	else
		echo "Current svn $csvn is not the same as the target svn $tsvn proceeding with rebuild"
		echo "Update starting at `date`"
		cd guayadeque
		svn update
		./build
		sudo make install
		echo "Update ending at `date`"
fi
```

Where tsvn is the current svn code (today) that users would be checking on as of this moment.

If a person is at SVN 1097, and there is a new SVN update, this is a non issue as the script would execute as it should.

But there are hundreds of users now and in the future who are less than that.

So at the 

if [ $csvn = $tsvn ]

Line, I am trying to determine the best way to have the script go to the then if the SVN is less than the one stated (with -lt -gt or somehting similar)  ...OR,

A variable in place of tsvn=1097 that would make it a moot point.

Be nice, I am new at it and did a fair amount of research first...

---

### Post by VastOne on 2010-06-23
would the following work?
```

if [ $csvn -ne $tsvn ]
```

or

```
if [ $csvn != $tsvn ]
```

as I don't quite know the difference between integer or string...



Thanks

---

### Post by MadCow108 on 2010-06-23
you can look it up in this manpage:
man test

(if [ ... ]; is just a shortcut for if test ...)

integers (= plain unquoted numbers) are compared with -ne -eq -lt etc.
strings are compared with = != -z -n etc.

you could also convert your integer to a string and use the (less versatile) string comparisons by quoting them:
if [ "$int1" = "$int2"] then

but I do not understand the purpopse of your script.
a checkout always gets the newest revision of your branch so you don't need the if clause in the first place

if you need a special revision use the -r flag of svn

---

### Post by VastOne on 2010-06-23
> **MadCow108 said:**
> you can look it up in this manpage:
man test

(if [ ... ]; is just a shortcut for if test ...)

integers (= plain unquoted numbers) are compared with -ne -eq -lt etc.
strings are compared with = != -z -n etc.

you could also convert your integer to a string and use the (less versatile) string comparisons by quoting them:
if [ "$int1" = "$int2"] then

but I do not understand the purpopse of your script.
a checkout always gets the newest revision of your branch so you don't need the if clause in the first place

if you need a special revision use the -r flag of svn

Thank you...I had read many man pages on both bash and svn prior to asking and then found the -ne at a later time

This SVN is used by an active developer who changes svn sometimes 4-5 a day who is encouraging the users of the app to bring bug fixes and suggestions to him.  When he gets them, he makes the changes and we all need to run the "then" part of the script to get the latest rev.

It is pretty standard for most of us but for new users it is cumbersome to say the least (and confusing) and I am just trying to minimize the amount of tasks needed to get the current svn

The "then" portion of the script works perfectly now, it just fills your screen full of unnecessary detail if you are at the current svn

I appreciate the help! 

:popcorn:

---

### Post by VastOne on 2010-06-23
Marked as solved a the -ne parameter is what I was looking for.

Thanks for your help...

:popcorn:

---

### Post by geirha on 2010-06-23
The old [ command should not be used in bash scripts, only in POSIX or bourne compatible scripts. Use (( for arithmetics and arithmetic comparison [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)
```
a=2 b=10
if (( b > a )); then
  echo "$b is greater than $a"
else
  echo "$b is less than or equal to $a"
fi

```
And [[ for strings and files [http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)
```
a=2 b=10
if [[ $b > $a ]]; then
  echo "$b is greater than $a"
else
  echo "$b is less than or equal to $a"
fi

```

---

### Post by MadCow108 on 2010-06-24
I disagree.
If you do not need the features of the "new" less portable syntax, stick with more portable POSIX syntax.
In that case you should also replace the /bin/bash by /bin/sh

You never know what kind of shell your user's are using.
Especially as this script is for unexperienced users it should just work on most systems and not give some hard to read error message just because people are using e.g. dash and not bash.

Also most documentation documents the posix style. So Users wanting to understand the script might get confused by the less common syntax

---

### Post by geirha on 2010-06-24
> **MadCow108 said:**
> I disagree.
If you do not need the features of the "new" less portable syntax, stick with more portable POSIX syntax.
In that case you should also replace the /bin/bash by /bin/sh


Exactly, if you're writing a bash script (the hashbang is #!/bin/bash), use bash's improved features. If you want to write a POSIX script for portability, set the hashbang to #!/bin/sh and use only features defined by POSIX.

If a bash "tutorial" or "guide" tells you to use [ and expr and other silliness, then that "tutorial" or "guide" is junk. Don't read it. That includes the advanced bash-scripting guide.

---

