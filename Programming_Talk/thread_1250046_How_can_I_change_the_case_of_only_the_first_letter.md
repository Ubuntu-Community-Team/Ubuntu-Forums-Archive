---
title: "How can I change the case of only the first letter of a word? (for script usage)"
date: 2009-08-26
forum: Programming Talk
---

### Post by KIAaze on 2009-08-26
How can I change the case of only the first letter of a word?
i.e. UeberLisk <-> ueberLisk

It's for use in a bash script, but if necessary I can switch to python too.
awk, sed, tr, perl, C, C++, python, I take whatever works. :)

The idea is to change class names in C++ source files like this:
```
oldClassName->newClassName
OldClassName->NewClassName
oldclassname->newclassname
OLDCLASSNAME->NEWCLASSNAME

```

Here's my current script:
```
#!/bin/bash
set -eu

usage()
{
  echo "USAGE EXAMPLE:"
  echo "`basename $0` DialogLineEdit HoldTheLine"
  echo "This creates a new widget named HoldTheLine based on DialogLineEdit. :)"
  echo "IMPORTANT: For this script to work correctly, the names must be camel case with upper case first letter!!!!!!!"
}

# Check if all parameters are present
# If no, exit
if [ $# -ne 2 ]
then
	usage;
	exit 0;
fi

#Convert the given argument into an all lower case string.
toLower() {
  echo $1 | tr "[:upper:]" "[:lower:]" 
}

#Convert the given argument into an all upper case string.
toUpper() {
  echo $1 | tr "[:lower:]" "[:upper:]" 
}

#Convert the given argument into a capitalized string.
# does not what I want. I only want first letter changed. :(
toCapitalized() {
  echo $1  | python -c "print raw_input().capitalize()"
}

oldcamelname=$1
newcamelname=$2

# create names
oldlowername=$(toLower $oldcamelname)
olduppername=$(toUpper $oldcamelname)
oldcapitalname=$(toCapitalized $oldcamelname)

newlowername=$(toLower $newcamelname)
newuppername=$(toUpper $newcamelname)
newcapitalname=$(toCapitalized $newcamelname)

echo oldlowername=$oldlowername
echo olduppername=$olduppername
echo oldcapitalname=$oldcapitalname
echo newlowername=$newlowername
echo newuppername=$newuppername
echo newcapitalname=$newcapitalname

# echo $oldlowername\plugin.pro
# exit 0

#clean up
cd $oldlowername
qmake test.pro && make distclean
qmake $oldlowername\plugin.pro && make distclean
rm -fv *.orig
cd ..

# copy files
cp -r $oldlowername $newlowername
cd $newlowername

# rename files
rename $oldlowername $newlowername *

# process files
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldlowername/$newlowername/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldcamelname/$newcamelname/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$olduppername/$newuppername/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldcapitalname/$newcapitalname/g" {}

#check for errors
grep -i $oldlowername *
if [ $? -ne 0 ]
then
  echo "ERROR: There are still traces of $oldlowername left."
fi

echo SUCCESS

```

edit:
Found a way to separate words in a camel case string, but I can't figure out how to get a list from it. My python knowledge is still a bit limited.
```
#!/usr/bin/env python
import sys
import re

def usage():
    print "converts \'CamelCase\' to \'Camel Case\'"
    print 'usage: '+sys.argv[0]+' STRING'

def space_out_camel_case(stringAsCamelCase):
    """Adds spaces to a camel case string.  Failure to space out string returns the original string.
    >>> space_out_camel_case('DMLSServicesOtherBSTextLLC')
    'DMLS Services Other BS Text LLC'
    """
    
    if stringAsCamelCase is None:
        return None

    pattern = re.compile('([A-Z][A-Z][a-z])|([a-z][A-Z])')
    print pattern
    return pattern.sub(lambda m: m.group()[:1] + " " + m.group()[1:], stringAsCamelCase)

if len(sys.argv)==1:
	usage()
	sys.exit()

oldname=sys.argv[1]
newname=space_out_camel_case(oldname)
print oldname +' -> '+ newname

```
source: [http://refactormycode.com/codes/675-camelcase-to-camel-case-python-newbie](http://refactormycode.com/codes/675-camelcase-to-camel-case-python-newbie)

---

### Post by KIAaze on 2009-08-26
Solved. :)
It's not self-contained (requires 2 scripts), but it works.
Here it is:

newcustomwidget.sh :
```
#!/bin/bash
set -eu

usage()
{
  echo "USAGE EXAMPLE:"
  echo "`basename $0` DialogLineEdit HoldTheLine"
  echo "This creates a new widget named HoldTheLine based on DialogLineEdit. :)"
  echo "IMPORTANT: For this script to work correctly, the names must be camel case with upper case first letter!!!!!!!"
}

# Check if all parameters are present
# If no, exit
if [ $# -ne 2 ]
then
	usage;
	exit 0;
fi

#Convert the given argument into an all lower case string.
toLower() {
  echo $1 | tr "[:upper:]" "[:lower:]" 
}

#Convert the given argument into an all upper case string.
toUpper() {
  echo $1 | tr "[:lower:]" "[:upper:]" 
}

#Convert the given argument into a capitalized string.
toCapitalized() {
  echo $1  | python -c "print raw_input().capitalize()"
}

toLowerCaseFirstCharacter() {
#   space_out_camel_case.py $1
  LowerCaseFirstCharacter.py $1
}

oldcamelname=$1
newcamelname=$2

# create names
oldlowername=$(toLower $oldcamelname)
olduppername=$(toUpper $oldcamelname)
oldcapitalname=$(toCapitalized $oldcamelname)
oldlowerfirstname=$(toLowerCaseFirstCharacter $oldcamelname)

newlowername=$(toLower $newcamelname)
newuppername=$(toUpper $newcamelname)
newcapitalname=$(toCapitalized $newcamelname)
newlowerfirstname=$(toLowerCaseFirstCharacter $newcamelname)

echo oldlowername=$oldlowername
echo olduppername=$olduppername
echo oldcapitalname=$oldcapitalname
echo oldlowerfirstname=$oldlowerfirstname

echo newlowername=$newlowername
echo newuppername=$newuppername
echo newcapitalname=$newcapitalname
echo newlowerfirstname=$newlowerfirstname

# echo $oldlowername\plugin.pro
# exit 0

#clean up
cd $oldlowername
qmake test.pro && make distclean
qmake $oldlowername\plugin.pro && make distclean
rm -fv *.orig
cd ..

# copy files
mkdir $newlowername
ls -1 $oldlowername | grep -v designer | xargs -n1 -I{} cp -v $oldlowername/{} $newlowername
# cp -r $oldlowername $newlowername
cd $newlowername

# rename files
rename $oldlowername $newlowername *

# process files
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldlowername/$newlowername/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldcamelname/$newcamelname/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$olduppername/$newuppername/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldcapitalname/$newcapitalname/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldlowerfirstname/$newlowerfirstname/g" {}

#check for errors
if grep -i $oldlowername *
then
  echo "ERROR: There are still traces of $oldlowername left."
else
  echo SUCCESS
fi

```

LowerCaseFirstCharacter.py :
```
#!/usr/bin/env python
import sys
import re

def usage():
    print "converts \'CamelCase\' to \'Camel Case\'"
    print 'usage: '+sys.argv[0]+' STRING'

def space_out_camel_case(stringAsCamelCase):
    """Adds spaces to a camel case string.  Failure to space out string returns the original string.
    >>> space_out_camel_case('DMLSServicesOtherBSTextLLC')
    'DMLS Services Other BS Text LLC'
    """
    
    if stringAsCamelCase is None:
        return None

    pattern = re.compile('([A-Z][A-Z][a-z])|([a-z][A-Z])')
    #print pattern
    return pattern.sub(lambda m: m.group()[:1] + " " + m.group()[1:], stringAsCamelCase)

def lowercase_first_letter(stringAsCamelCase):
  index=0
  ret=''
  for ch in stringAsCamelCase:
    if index==0:
      #print ch.lower()
      ret += ch.lower()
    else:
      #print ch
      ret += ch
    index = index + 1
  #print ret
  return ret

def uppercase_first_letter(stringAsCamelCase):
  index=0
  ret=''
  for ch in stringAsCamelCase:
    if index==0:
      #print ch.upper()
      ret += ch.upper()
    else:
      #print ch
      ret += ch
    index = index + 1
  #print ret
  return ret

if len(sys.argv)==1:
	usage()
	sys.exit()

oldname=sys.argv[1]
newname=space_out_camel_case(oldname)
#print oldname +' -> '+ newname
#wordlist = newname.split(' ')
#print wordlist
#print wordlist[0].lower()

#print space_out_camel_case(oldname)
print lowercase_first_letter(oldname)
#print uppercase_first_letter(oldname)

```

---

### Post by Arndt on 2009-08-26
> **KIAaze said:**
> Solved. :)
It's not self-contained (requires 2 scripts), but it works.
Here it is:

newcustomwidget.sh :
```
#!/bin/bash
set -eu

usage()
{
  echo "USAGE EXAMPLE:"
  echo "`basename $0` DialogLineEdit HoldTheLine"
  echo "This creates a new widget named HoldTheLine based on DialogLineEdit. :)"
  echo "IMPORTANT: For this script to work correctly, the names must be camel case with upper case first letter!!!!!!!"
}

# Check if all parameters are present
# If no, exit
if [ $# -ne 2 ]
then
	usage;
	exit 0;
fi

#Convert the given argument into an all lower case string.
toLower() {
  echo $1 | tr "[:upper:]" "[:lower:]" 
}

#Convert the given argument into an all upper case string.
toUpper() {
  echo $1 | tr "[:lower:]" "[:upper:]" 
}

#Convert the given argument into a capitalized string.
toCapitalized() {
  echo $1  | python -c "print raw_input().capitalize()"
}

toLowerCaseFirstCharacter() {
#   space_out_camel_case.py $1
  LowerCaseFirstCharacter.py $1
}

oldcamelname=$1
newcamelname=$2

# create names
oldlowername=$(toLower $oldcamelname)
olduppername=$(toUpper $oldcamelname)
oldcapitalname=$(toCapitalized $oldcamelname)
oldlowerfirstname=$(toLowerCaseFirstCharacter $oldcamelname)

newlowername=$(toLower $newcamelname)
newuppername=$(toUpper $newcamelname)
newcapitalname=$(toCapitalized $newcamelname)
newlowerfirstname=$(toLowerCaseFirstCharacter $newcamelname)

echo oldlowername=$oldlowername
echo olduppername=$olduppername
echo oldcapitalname=$oldcapitalname
echo oldlowerfirstname=$oldlowerfirstname

echo newlowername=$newlowername
echo newuppername=$newuppername
echo newcapitalname=$newcapitalname
echo newlowerfirstname=$newlowerfirstname

# echo $oldlowername\plugin.pro
# exit 0

#clean up
cd $oldlowername
qmake test.pro && make distclean
qmake $oldlowername\plugin.pro && make distclean
rm -fv *.orig
cd ..

# copy files
mkdir $newlowername
ls -1 $oldlowername | grep -v designer | xargs -n1 -I{} cp -v $oldlowername/{} $newlowername
# cp -r $oldlowername $newlowername
cd $newlowername

# rename files
rename $oldlowername $newlowername *

# process files
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldlowername/$newlowername/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldcamelname/$newcamelname/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$olduppername/$newuppername/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldcapitalname/$newcapitalname/g" {}
ls -1 | xargs -n1 -I{} sed -i -e "s/$oldlowerfirstname/$newlowerfirstname/g" {}

#check for errors
if grep -i $oldlowername *
then
  echo "ERROR: There are still traces of $oldlowername left."
else
  echo SUCCESS
fi

```

LowerCaseFirstCharacter.py :
```
#!/usr/bin/env python
import sys
import re

def usage():
    print "converts \'CamelCase\' to \'Camel Case\'"
    print 'usage: '+sys.argv[0]+' STRING'

def space_out_camel_case(stringAsCamelCase):
    """Adds spaces to a camel case string.  Failure to space out string returns the original string.
    >>> space_out_camel_case('DMLSServicesOtherBSTextLLC')
    'DMLS Services Other BS Text LLC'
    """
    
    if stringAsCamelCase is None:
        return None

    pattern = re.compile('([A-Z][A-Z][a-z])|([a-z][A-Z])')
    #print pattern
    return pattern.sub(lambda m: m.group()[:1] + " " + m.group()[1:], stringAsCamelCase)

def lowercase_first_letter(stringAsCamelCase):
  index=0
  ret=''
  for ch in stringAsCamelCase:
    if index==0:
      #print ch.lower()
      ret += ch.lower()
    else:
      #print ch
      ret += ch
    index = index + 1
  #print ret
  return ret

def uppercase_first_letter(stringAsCamelCase):
  index=0
  ret=''
  for ch in stringAsCamelCase:
    if index==0:
      #print ch.upper()
      ret += ch.upper()
    else:
      #print ch
      ret += ch
    index = index + 1
  #print ret
  return ret

if len(sys.argv)==1:
	usage()
	sys.exit()

oldname=sys.argv[1]
newname=space_out_camel_case(oldname)
#print oldname +' -> '+ newname
#wordlist = newname.split(' ')
#print wordlist
#print wordlist[0].lower()

#print space_out_camel_case(oldname)
print lowercase_first_letter(oldname)
#print uppercase_first_letter(oldname)

```

I don't know if this is more elegant, but it's a lot shorter:

```
name=$1

n2=`echo $name | tr a-zA-Z A-Za-z`

python -c 'import sys;print sys.argv[2][0]+sys.argv[1][1:]' $name $n2
```

---

### Post by DaithiF on 2009-08-26
sorry if i haven't read all the detail and missed some nuances here, but for the original question:
> How can I change the case of only the first letter of a word?
i.e. UeberLisk <-> ueberLisk```
echo "Uberlisk" | sed 's/^./\l&/'
uberlisk
```where \l& means convert whatever was matched (which is ^., ie. the first character) to lowercase

---

### Post by Arndt on 2009-08-26
> **DaithiF said:**
> sorry if i haven't read all the detail and missed some nuances here, but for the original question:
```
echo "Uberlisk" | sed 's/^./\l&/'
uberlisk
```where \l& means convert whatever was matched (which is ^., ie. the first character) to lowercase

I didn't even know 'sed' could do that. Maybe it doesn't in all Unix platforms.

---

### Post by DaithiF on 2009-08-26
> Maybe it doesn't in all Unix platforms
Its standard in GNU sed at least:
[http://www.gnu.org/software/sed/manual/html_node/The-_0022s_0022-Command.html](http://www.gnu.org/software/sed/manual/html_node/The-_0022s_0022-Command.html)

---

### Post by wmcbrine on 2009-08-26
> **Arndt said:**
> I don't know if this is more elegant, but it's a lot shorter:

```
name=$1

n2=`echo $name | tr a-zA-Z A-Za-z`

python -c 'import sys;print sys.argv[2][0]+sys.argv[1][1:]' $name $n2
```
Still way too long...

```
def lowercase_first_letter(oldstr):
    return oldstr[0].lower() + oldstr[1:]
```

or

```
import sys;print sys.argv[1][0].lower() + sys.argv[1][1:]
```

---

### Post by Arndt on 2009-08-26
> **wmcbrine said:**
> Still way too long...

```
def lowercase_first_letter(oldstr):
    return oldstr[0].lower() + oldstr[1:]
```

or

```
import sys;print sys.argv[1][0].lower() + sys.argv[1][1:]
```

Yes, but the OP said "change the case", not "make lower case".

---

### Post by wmcbrine on 2009-08-26
Well, that's not what his code does. But OK...

```
def toggle(str):
    ch = str[0]
    return (ch.upper() if ch.islower() else ch.lower()) + str[1:]
```

---

### Post by KIAaze on 2009-08-26
> **Arndt said:**
> Yes, but the OP said "change the case", not "make lower case".

That's correct. But I said that because it didn't matter to me if it changed the first character to lower or upper or if it toggled it. (would just change the way the arguments are given)
But toggling is nice to have.

Thanks to all of you. Now I learned a few more python and sed tricks. :)

As for my code being long, well I obviously didn't clean it up and left in a lot of unused functions. ;)
The winner for shortest code is DaithiF with sed. =D>

---

