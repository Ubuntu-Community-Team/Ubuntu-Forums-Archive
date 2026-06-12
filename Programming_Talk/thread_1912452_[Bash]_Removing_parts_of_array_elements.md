---
title: "[Bash] Removing parts of array elements"
date: 2012-01-20
forum: Programming Talk
---

### Post by speedkreature on 2012-01-20
I've been at this for a few hours and I seem to be going backwards...

The idea here is to get svn tags and generate an array with them.  This seems to work:
```

Tags=(`svn ls https://root.cern.ch/svn/root/tags`)

```Echoing this displays a list like this
```

cint/
v2-24-05/
v2-25-00/
v2-25-01/
v2-25-02/
v2-25-03/
v2-25-final/
v2-26-00/
v2-26-01/
v2-26-final/
v3-00-01/
v3-00-02/
v3-00-04/
v3-00-05/
v3-00-06/
v3-01-01/
v3-01-02/
v3-01-03/
v3-01-05/
...
v5-24-00/
v5-24-00a/
v5-24-00b/
v5-24-00b-caf/
v5-25-01-alice/
v5-25-02/
v5-25-04/
v5-26-00/
v5-26-00a/
v5-26-00b/
v5-26-00c/
v5-26-00d/
v5-26-00e/
v5-26-00f/
v5-26-00g/
v5-27-02/
v5-27-04/
v5-27-06/
v5-27-06a/
v5-27-06b/
v5-27-06c/
v5-27-06d/
v5-28-00/
v5-28-00a/
v5-28-00b/
v5-28-00c/
v5-28-00d/
v5-28-00e/
v5-28-00f/
v5-28-00g/
v5-28-00h/
v5-29-02/
v5-30-00/
v5-30-00-rc1/
v5-30-00-rc2/
v5-30-01/
v5-30-02/
v5-30-03/
v5-30-04/
v5-30-05/
v5-30-06/
v5-32-00/
v5-32-00-rc1/
v5-32-00-rc2/

```What I'm interested in is the latest stable version.  For that, I think I need to remove the "/" in each entry, then remove all entries that are not 8 characters long.  Finally, it seems the most logical approach would be to take the last element in the array and use that to generate the tag I need so I will always, automatically, copy the latest stable release.
I know it's an awfully complex task for a person who's just getting into bash scripting, and I'm guessing sed will be my friend on this one but I'm not sure exactly how to proceed.  I don't want to spend more hours chasing my tail when someone here can just point me in the right direction.

---

### Post by sisco311 on 2012-01-20
Check out: [http://mywiki.wooledge.org/BashGuide/Arrays](http://mywiki.wooledge.org/BashGuide/Arrays) and BashFAQ 005 (link in my signature) and [http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

So, you could try something like:
```
#!/bin/bash

unset arr i

while read -r element; do
    # remove trailing /
    element=${element%/}
    # if element is 8 character long, add it to the array:
    if (( ${#element} == 8 )); then
        arr[i++]="$element"
    fi
done< <(svn ls https://root.cern.ch/svn/root/tags)

# print last element:
printf '%s\n' "${arr[i-1]}"

# print the array:
#printf '%s\n' "${arr[@]}"

```

---

### Post by ofnuts on 2012-01-20
> **speedkreature said:**
> I've been at this for a few hours and I seem to be going backwards...

The idea here is to get svn tags and generate an array with them.  This seems to work:
```

Tags=(`svn ls https://root.cern.ch/svn/root/tags`)

```Echoing this displays a list like this
What I'm interested in is the latest stable version.  For that, I think I need to remove the "/" in each entry, then remove all entries that are not 8 characters long.  Finally, it seems the most logical approach would be to take the last element in the array and use that to generate the tag I need so I will always, automatically, copy the latest stable release.
I know it's an awfully complex task for a person who's just getting into bash scripting, and I'm guessing sed will be my friend on this one but I'm not sure exactly how to proceed.  I don't want to spend more hours chasing my tail when someone here can just point me in the right direction.
```

tags=$(svn ls https://root.cern.ch/svn/root/tags | grep -e '^v[[:digit:]]-[[:digit:]][[:digit:]]-[[:digit:]][[:digit:]]/$' | sort -r | head -1 | tr -d '/')

```In slow motion:

[LIST=1]
[*]use grep to keep all lines containing exactly:
[LIST]
[*]'v' as the first character
[*]one digit
[*]'-'
[*]two digits
[*]'-'
[*]two more digits
[*]'/' as the last character
[/LIST]
 
[*]sort descending to put the last release first
[*]extract the first line
[*]remove the ending "/"
[/LIST]
If SVN's output is sorted, you can avoid the "sort" and use '"tail -1" instead of "head -1" to keep the last line.

---

### Post by Vaphell on 2012-01-20
alternatively if the initial array doesn't matter at all you can try piping the svn output to sed/grep to filter out unneeded elements, eg.
```
arr=( svn ... | sed 's:/$::' | grep -P '^.{8}$' )
```
last elem would be ${arr[$last]}, where last=$(( ${#arr[@]}-1 ))

@ofnuts, isn't [0-9] more handy than the bloated [[:digit:]]? :-)
also why not use [0-9]{2}?

---

### Post by speedkreature on 2012-01-20
@sisco311: Brilliant!  And thanks for the links!
@ofnuts: I think I see at least two syntax error in there (svn twice, and no closing parentheses).  Even still, my kung-fu isn't strong enough to make it work.  
@Vaphell:  That is vaguely the direction my thought process was originally going.

Thank you, every one for your input!

---

### Post by sisco311 on 2012-01-20
> **Vaphell said:**
> 
@ofnuts, isn't [0-9] more handy than the bloated [[:digit:]]? :-)


In the case of digits, there's not much danger; but in the case of letters of the alphabet, [ASCII ordering cannot be safely assumed]("http://mywiki.wooledge.org/locale"). So, I'd recommend the use of class names.

---

### Post by ofnuts on 2012-01-20
@vaphell: didn't use {2} because it doesn't seem to work in the "simplified" grep regexp syntax, and [[:digit::]] because I started out with '\d' hoping it would work. On the whole since I often have to deal with French, character classes are much safer than [a-z] (not only would I have  to make sure I'm not missing any, but I would also have to insure that the script encoding is adequate).

@speedkreature: fixed the dup "svn" early, also fixed the missing parenthesis.

---

### Post by sisco311 on 2012-01-20
> **ofnuts said:**
> @vaphell: didn't use {2} because it doesn't seem to work in the "simplified" grep regexp syntax

If you want to know why it didn't work, then read the man page of GNU/grep. :evil:
```

man grep | less +/"^ +Basic vs Extended Regular Expressions"

```

In short, you have to escape the curly brackets. :)


You might also want to check out the description of POSIX grep:
[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/grep.html#tag_20_55](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/grep.html#tag_20_55)

And, of course, there is a topic about regular expressions @ Greg's Wiki: [http://mywiki.wooledge.org/RegularExpression](http://mywiki.wooledge.org/RegularExpression) :P

---

### Post by ofnuts on 2012-01-20
> **sisco311 said:**
> If you want to know why it didn't work, then read the man page of GNU/grep. :evil:
```

man grep | less +/"^ +Basic vs Extended Regular Expressions"

```In short, you have to escape the curly brackets. :)


You might also want to check out the description of POSIX grep:
[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/grep.html#tag_20_55](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/grep.html#tag_20_55)

And, of course, there is a topic about regular expressions @ Greg's Wiki: [http://mywiki.wooledge.org/RegularExpression](http://mywiki.wooledge.org/RegularExpression) :P

The best expression would be:
```
 '^v[[:digit]](-[[:digit:]]{2}){2}/$'
```

---

### Post by Vaphell on 2012-01-21
> [quote]didn't use {2} because it doesn't seem to work in the "simplified" grep regexp syntax
In short, you have to escape the curly brackets.
[/quote]

also grep -P gives you perl flavor of regexes
```
$ echo abc12de34f | grep -P '[[:alpha:]]{2,3}'
**abc**12**de**34f
```

edit: -P appears to be bugged though and doesn't account for locale
```
$ echo $'&#261;&#263;&#281;&#322;ó&#347;&#378;&#380;\nabcdef\n123' | grep -P '[[:alpha:]]'
abcdef
$ echo $'&#261;&#263;&#281;&#322;ó&#347;&#378;&#380;\nabcdef\n123' | grep '[[:alpha:]]'
&#261;&#263;&#281;&#322;ó&#347;&#378;&#380;
abcdef
```


no reservations in case of language dependent [[:alpha:]] but [0-9] is simply more convenient and has no drawbacks i can see.

---

