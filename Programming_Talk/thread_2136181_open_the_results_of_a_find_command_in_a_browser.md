---
title: "open the results of a find command in a browser"
date: 2013-04-16
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-04-16
Hi Guys,

OK - that is a pretty bad title for a post.
I don't really have the proper vocabulary to explain what I mean, but here it goes.

I have all of the man files on my system converted to html files in a directory in my home.

If I run:
```
#!/bin/bash
read -p "Searching for: " search_string; find /home/grouchygaijin/man-pages-html -iname "$search_string" 2>/dev/null
```

It works.
The script brings up the path to the html file(s) that matches the search.
Now, I *could* just be happy and copy the path to the file then paste it into the browser, but I thought it would be much cooler to be able to have the browser open up the file when I click on it.

The question is:
How can I tell the script to let me choose to open the search results (path to the file found) in a browser.

I really appreciate the help!

---

### Post by Vaphell on 2013-04-16
xdg-open "$file" to open with program associated with the file type or simply browser_name "$file"

```
#!/bin/bash

dir="$HOME/man-pages-html"
read -p "Searching for: " search_string
readarray -t results < <( find "${dir}" -iname "*${search_string}*.html" )

if (( ${#results[@]} == 1 ))
then 
  xdg-open "${results[@]}"   # open the only result immediately
elif (( ${#results[@]} > 1 ))
then
  select s in "${results[@]/#$dir\//}"; do break; done   # allow user to select file from the list of results
  xdg-open "$dir/$s"
else
  echo "no files found, sorry"
fi
```

---

### Post by GrouchyGaijin on 2013-04-17
Wow!
THANK YOU!
Now I need to figure out what you did.

---

### Post by Vaphell on 2013-04-17
*readarray* line captures the output of *find* and stores it in the *results* array, each line is a separate element, ${results[0]} - 1st element of the array, ${results[1]} = 2nd, etc.
${array[@]} = all elements. 
if you want to see the contents of the array you can use something like this:
```
printf "'%s'\n" "${results[@]}"
```

if the array length ( **${[COLOR="#0000CD"]#[/COLOR]results[@]}** ) is 1 then simply run *xdg-open* <results>

if it's greater than one: create menu populated with elements of *results[]* using *select*. It's a potentially infinite loop in case one wants to put repetitive tasks in it, so *break* is needed to jump out right after the choice. Whatever you have chosen is opened with *xdg-open*.
Array elements store full paths but in menu i trimmed them a bit for aestetic purposes: ${results[@]/#$dir\//} = elements of *results[]* with $dir path removed. $dir is glued back with selected value in the next line.

to illustrate:
```
$ prefix=ABC
$ x=ABCsomething
$ echo $x:${x/#$prefix/}
ABCsomething:something
$ array=( "ABC111" "ABC222" "ABC333" )
$ echo ${#array[@]}
3
$ printf "'%s'\n" "${array[@]}"
'ABC111'
'ABC222'
'ABC333'
$ printf "'%s'\n" "${array[@]/#$prefix/}"
'111'
'222'
'333'
$ select s in "A" "B" "C"; do echo "you selected '$s'"; break; done
1) A
2) B
3) C
#? 3
you selected 'C'
$ select s in "${array[@]/#$prefix/}"; do echo "you selected '$s'"; break; done
1) 111
2) 222
3) 333
#? 2
you selected '222'

```

---

### Post by schragge on 2013-04-17
@OP
Just wondering why using [http://manpages.ubuntu.com](http://manpages.ubuntu.com) or [http://manpages.debian.net](http://manpages.debian.net) is not an option?

---

### Post by GrouchyGaijin on 2013-04-17
> **schragge said:**
> @OP
Just wondering why using [http://manpages.ubuntu.com](http://manpages.ubuntu.com) or [http://manpages.debian.net](http://manpages.debian.net) is not an option?

Well, I suppose they are options.  They sound like better options actually, I just didn't think of it.
(I was thinking to myself that I'd probably need to update my directory of man pages if I install a new program.)
How can I modify this script to use the manpages.ubuntu.com link instead of my local directory.

---

### Post by schragge on 2013-04-17
The fourth link under **Navigating the Repository** on manpages.ubuntu.com is *[Download the 'dman' shell script]("http://manpages.ubuntu.com/dman") to run on a command line*. The link before that is *Install the search engine plugin for your browser*.

The manpages on manpages.ubuntu.com are just static HTML files, so e.g. [dpkg(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html") in English for *precise* is
```
http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html
```

---

### Post by GrouchyGaijin on 2013-04-17
Cool - thanks man!

---

