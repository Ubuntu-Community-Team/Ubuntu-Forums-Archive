---
title: "Bash problems"
date: 2009-05-19
forum: Programming Talk
---

### Post by WUSB11 MY A**E on 2009-05-19
Right, I've been trying to sort something out for me in bash, basically I want to convert all .ogg files tags in all directories in the current directory to have different tags... Anyway, theres absolutely no point in me learning bash completely for just this one use so I've been searching around the internet to try and find a way to do this and have come up with this:

```
#!/bin/bash

for n in *; do
	if [ -d "$n" ]; then
		for o in "$n/*"; do
			echo "$o"
			if [ -d "$n/$o" ]; then
				for p in "$n/$o/*.ogg"; do
    				echo "Extracting comments and COVERART from $n/$o/$p"
    				vorbiscomment -l "$n/$o/$p" | grep -v COMMENT > "$n/$o/$p/-comment.txt"
    				echo "Replacing comments in $n"
    				vorbiscomment -c "$n/$o/$p-comment.txt" -w "$n/$o/$p"
					rm $n/$o/$p-comment.txt
				done
			fi
		done
	fi
done
```

This obviously doesn't do what I want, but its the best I can come up with with my very very limited knowledge of bash. Can anyone help me please?

Thanks in advance :)

---

### Post by weresheep on 2009-05-19
Hello,

From the script you posted, it seems you want to update each OGG file such that the 'COMMENT' tag(s) are removed. Is this correct?

Assuming yes (if no, I need more info), here is an updated version of your script that should accomplish the above task. It will find all OGG files anywhere within the current directory, no matter how deep, so make sure this is what you want before running it.

In fact as I haven't tested this, I would advise you create a test directory with a sample OGG file or two to test on before unleashing it on your main music directory :D

```

#!/bin/bash -
# Remove the 'COMMENT' tags from all OGG files in the CWD tree.

find . -type f -name *.ogg | while read F ; do
  echo "Updating file $F"
  DIR="$(dirname $F)"

  vorbiscomment -l "$F" | grep -v COMMENT > "${DIR}/.comment.txt"
  vorbiscomment -c "${DIR}/.comment.txt" -w "$F"

  rm "${DIR}/.comment.txt"
done

```

-weresheep

---

### Post by k2t0f12d on 2009-05-19
> **WUSB11 MY A**E said:**
> Right, I've been trying to sort something out for me in bash ... theres absolutely no point in me learning bash completely ...Obviously, there is a point. At the very least, if you were to omit that you believe learning is pointless, you will very likely improve your chances of obtaining constructive criticism 100%. Far be it from me to tell you that you should believe otherwise, however; the people that would ordinarily want to help you with this problem do.

Anyway, you don't need to graduate from a technical institute to write useful shell programs. All you need is [this]("http://tldp.org/LDP/abs/html/") book.  I heartily recommend downloading a hard copy to your own local storage and have it open in evince (or equivalent) when attempting to write shell programs.

```
#!/bin/bash

for n in *; do
	if [ -d "$n" ]; then
		for o in "$n/*"; do
			echo "$o"
			if [ -d "$n/$o" ]; then
				for p in "$n/$o/*.ogg"; do
    				echo "Extracting comments and COVERART from $n/$o/$p"
    				vorbiscomment -l "$n/$o/$p" | grep -v COMMENT > "$n/$o/$p/-comment.txt"
    				echo "Replacing comments in $n"
    				vorbiscomment -c "$n/$o/$p-comment.txt" -w "$n/$o/$p"
					rm $n/$o/$p-comment.txt
				done
			fi
		done
	fi
done
```

> **WUSB11 MY A**E said:**
> This obviously doesn't do what I want, but its the best I can come up with with my very very limited knowledge of bash. Can anyone help me please?

Thanks in advance :)

Your primary problem is this```
for n in *; do
```because "*" in this instance is expanded by the interpreter to mean "match any pattern of words or characters in an empty set", thus returning "" (nothing).

even if you corrected that, this```
for o in "$n/*"; do
```has a similar problem in that [COLOR="Blue"]*$n/**[/COLOR] will expand to the name of the directory and nothing more since once again "*" is pattern matching in an empty set.

finally, were that also fixed, this```
for p in "$n/$o/*.ogg"; do
``` would expand to [COLOR="Blue"]*$n/$o/.ogg*[/COLOR] in every iteration because "*" yet again is pattern matching an empty set and inserts nothing in front of [COLOR="Blue"]*.ogg*[/COLOR].

The reason for this is that the bash shell does not automatically assume that any reference to "*" is operating on the names of files in the present working directory. That is bad behavior carried over from cp/m command interpreters which set an equally bad expectation in the user to think that any reference to "*" is going to be applied on filenames. To populate a set to be operated on in a *[COLOR="Blue"]for[/COLOR]* loop, you must create the string of words to operate on.

For example, the usual way you get a list of filenames is to call *[COLOR="Blue"]ls[/COLOR]* followed by an explicit path to the directory whose contents you wish to see (with no path defaulting to the present working directory). To make *[COLOR="Blue"]$n $o[/COLOR]* and *[COLOR="Blue"]$p[/COLOR]* meaningful in the for loop, it could operate in the following way```
for n in $( ls ); do
``` where the dollar-parenthesis statement *[COLOR="Blue"]$( ls )[/COLOR]* invokes a sub-shell which runs the *[COLOR="Blue"]ls[/COLOR]* command and then inserts the output (which is to a list of filenames in your directory) whose contents may assign individually to *[COLOR="Blue"]$n[/COLOR]* during each iteration. *[COLOR="DimGray"]See also, Advanced Shell Scripting, Chapter 20, page 368[/COLOR]*

Having said that, the example I gave you is really terrible, but follows the logic you were employing to search directories for a filename. The main point I wished to convey is why calling "*" is useless because it doesn't imply anything to the interpreter in and of itself. Another problem with that design is that each recursion requires yet another *[COLOR="Blue"]for[/COLOR]* loop indention. Another poster here mentioned the *[COLOR="Blue"]find[/COLOR]* utility which would serve your purpose much better and cleaner and without any need for manual recursion in your program.

---

