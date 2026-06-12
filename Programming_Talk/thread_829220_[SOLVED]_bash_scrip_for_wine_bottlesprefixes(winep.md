---
title: "[SOLVED] bash scrip for wine bottles/prefixes(/wineprefixes)"
date: 2008-06-14
forum: Programming Talk
---

### Post by soxs on 2008-06-14
I made a script to compile wine with prefixes so I can use multiple ones at the same time without having to mess around with installing reinstalling and all that mess. in combination with several wine prefixes (do wineprefixcreate this is very handy).

Some time ago I ran straight into a nasty problem. Old wine versions won't even compile on hardy 8.04 (64bit, yes I know about the link stuff required). With the great help from some persons around here (BIG thx to happyhamster) I got it finally to compile. Today i centerd my effort on making all that things dynamically availiable, instead of sticking to one single old version (0.9.45, well, I still like to play wc3tft, which is not possible atm due to the lack of a complete accept ex implementation in wine and some other problems with the 1.0 RCs)

In order to make wine 0.9.45 compile, it is require to edit parse.c in the folder ./dlls/wldap32 and replace/remove 3 lines.
> **happyhamster said:**
> Ok, I tried something ugly and it compiled.

In a clean source folder, open the file parse.c (in the /dlls/wldap32 folder), and search for line 339 and 420 respectively.

line 339:

line 420 (this one is spread out over 2 lines):


change both into: 

- Then continue with the howto (creating symlinks, etc). When done compiling, you can create a .deb file using checkinstall:

sudo apt-get install checkinstall

sudo checkinstall --fstrans=no

- On first sight, it appears to work fine (it runs Tomb Raider Legend for example).
Quoted from: [http://ubuntuforums.org/showthread.php?t=799701&page=2](http://ubuntuforums.org/showthread.php?t=799701&page=2)
Note: Some additional packages are required.


What I am going to is parsing parse.c for these 2 statements and replacing them with the pendning one-liner. The bad thing is that I happen to get millions of running garbage chars instead of a usefull output.
So anyone around there how is willing to giv it it a shot? Thx a lot.

Attached parse.c, so you do not need to dl the whole wine-0.9.45 package
Attached the wine0.9.45.build.log, so anyone can follow "the unformated howto" from happyhamster.



```
#! /bin/bash

p="$HOME/Desktop/parse.c"
if ! [[ -f $p ]] ; then
	echo "There is no parse.c!"
	exit 77
fi
ii="`cat $p`"
####
## $ii is code, so always (ALWAYS!!) use ""!!(otherwise I get a bunch of errors/garbage chars)
####
#echo "$ii"
#echo "$p"
#exit 0
#sudo chmod 755 -vf $p 2&> /dev/null

x=`cat "$ii" | grep -n "ldap_parse_sort_control( ld, controlU, &res, &attrU );" | cut -f1 -d ":"`

#if [ $x = "" ]; then
#	echo "Replacement allready done."
#	exit 3
#fi
#
y=`cat "$ii" |grep -n "ret = ldap_parse_vlv_control( ld, controlU, &pos, &count," | cut -f1 -d ":"`
#if [ $y = "" ] || [ $y -n ] ; then
#	echo "Replacement allready done."
#	exit 4
#fi

sleep 5
replace="ret = LDAP_SUCCESS;"

total=`wc -l $p|cut -f1 -d " "`
echo "Total: $total"

#x<y, anyways anydays, anytime
L1=`expr "$x-1"|bc`
echo "L1: $L1" 
partA=`cat $ii | head -n $L1`
clear
echo "$partA"
sleep 10

## cut from [$lx+1] to [$ly-1]
L2=`expr "$y-1"|bc`
L3=`expr "$y-1-$x"|bc`
echo "L2: $L2" 
echo "L3: $L3" 
partB=`cat "$ii" | head -n $L2 | head -n $L3`

## a 2 liner, keep that in mind
L4=`expr "$total-$y-2"|bc`
echo "L4: $L4" 
partC=`cat "$ii" | tail -n $L4`

##replace old parse.c
## for debug, so $p must not be recreated manulally ervey time
p="$p.new"
echo $partA > $p ##overwrite the old one (maybe from a prior try) and required for the final version..
echo $replace >> $p
echo $partB >> $p
echo $replace >> $p
echo $partC >> $p

exit 0
```

---

### Post by soxs on 2008-06-14
lol, the answer has  3 letters.. sed and it simplyfies the task to searching wihch chars need to be escaped.

So I am going fine with the following code:

```
#! /bin/bash

p="$HOME/Desktop/parse.c"
if ! [[ -f $p ]] ; then
	echo "There is no parse.c!"
	exit 77
fi
sudo chmod 755 -vf $p 2&> /dev/null
sed -i 's/ret\ =\ ldap_parse_sort_control(\ ld,\ controlU,\ &res,\ &attrU\ );/ret\ =\ LDAP_SUCCESS/' $p
sed -i 's/ret\ =\ ldap_parse_vlv_control(\ ld,\ controlU,\ &pos,\ &count,/ret\ =\ LDAP_SUCCESS/' $p
sed -i 's/(struct\ berval\ \*\*)context,\ errcode\ );/\ /' $p

exit 0
```
Note: Too bad I can#t thank myself :-P

---

