---
title: "Regex help - matching across multiple lines"
date: 2007-08-09
forum: Programming Talk
---

### Post by Cappy on 2007-08-09
Hi, I need to remove all text that starts from <td class="quote"> and continues to </td>
These are from the middle of the html from a phpbb board.
This text usually goes across multiple lines, here is an example:
```

<td class="quote">blah
<br />

<br />
blah</td>


Other text that should not be removed.


<td class="quote">blah

<br />
blah</td>


Other text that should not be removed.

```


```

grep '<td class="quote">.*</td>'
```
won't work since it is across multiple lines

I came across some examples on google such as
[http://www.mail-archive.com/bug-grep@gnu.org/msg00864.html](http://www.mail-archive.com/bug-grep@gnu.org/msg00864.html)
but I didn't find any examples extremely similar to mine. I did find out I would probably need to use **awk** or **perl** to do it but I can't figure out how. This is in a sh shell script.

Thanks

---

### Post by aJayRoo on 2007-08-09
Try this:
```
sed '/<td class=\"quote\">/,/<\/td>/d' input_filename > output_filename
```
I'm pretty sure that does what you need it to!

---

### Post by stylishpants on 2007-08-09
One way is to use sgrep (structured grep).

```
sgrep '"<td " .. "</td>"' file
```

EDIT: oops, never mind, I misread your question.  That's solving the wrong problem.

---

### Post by Mr. C. on 2007-08-09
See if this works for you:

```
#!/usr/bin/perl
#!/usr/bin/perl -i.orig

undef $/;
$_ = <>;

s/<td.*?<\/td>//gs ;

print "$_";
```

Delete the first line to have the input file edited in place.

MrC

---

### Post by ghostdog74 on 2007-08-09
```

#!/usr/bin/python
import re
data=open("file").read()
result=re.compile("""<td class="quote">(.*?)</td>""",re.M|re.DOTALL).findall(data)
for item in result:
    #item=item.replace("\n","")
    print item

```

---

### Post by Cappy on 2007-08-10
Thank you for all the replies!

I ended up needing to detect <table width="90%" cellspacing="1" cellpadding="3" border="0" align="center"> to </table> instead but that was just a matter of substituting it thanks to the great examples!

Here is what I have:
```

sed '/<table width=\"90%\" cellspacing=\"1\" cellpadding=\"3\" border=\"0\" align=\"center\">/,/<\/table>/d'

```

I seem to have one more problem: getting rid of sections of quotes in quotes.
It looks like this:
```

<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">
<tr> 
	  <td><span class="genmed"><b>Someone wrote:</b></span></td>
	</tr>
	<tr>
	  <td class="quote"></span>
<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">
<tr> 
	  <td><span class="genmed"><b>Someone2 wrote:</b></span></td>
	</tr>
	<tr>
	  <td class="quote">
<br />

<br />
Blah
<br />

<br />
Blah</td>
	</tr>
</table>
<span class="postbody">
<br />

<br />
Blah</td>
	</tr>
</table>
<span class="postbody">
<br />
ACTUAL TEXT

</span><span class="gensmall"></span></td>
										</tr>
									</table>

								</td>
							</tr>

```

but the sed returns this:
```

<span class="postbody">
<br />

<br />
Blah</td>
        </tr>
</table>
<span class="postbody">
<br />
ACTUAL TEXT

</span><span class="gensmall"></span></td>
                                                                               </tr>
                                                                        </table>

                                                                </td>
                                                        </tr>

```
and does not get rid of the second quote.

Help in any language will solve the problem, thank you again!

---

### Post by Mr. C. on 2007-08-10
The problem is more complex, because nested elements are allowed.  A regex cannot be used to match this nesting and recursion.  We had all simplified the problem give your initial requirements.

You need a more robust solution to match these nested tables.

There are libraries available in most languages for parsing HTML documents.  I'm sure someone will come up with an example.

MrC

---

### Post by Cappy on 2007-08-11
Okay, I have a working solution! =)

```

echo "${page}" | while read line; do
	tablestart=`echo "$line" | grep '<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">'`
	tableend=`echo "$line" | grep '</table>'`
	if [ -n "$tablestart" ]; then
		deleteatable=`expr "$deleteatable" + 1`
		echo "$deleteatable - one has been added"
	elif [ -n "$tableend" ] && [ "$deleteatable" -gt 0 ]; then
		deleteatable=`expr "$deleteatable" - 1`
		echo "$deleteatable - one has been deleted"
	elif [ "$deleteatable" -eq 0 ]; then
		noquotes="$noquotes
$line"
	fi
	if [ "`echo "$line" | grep '</html>'`" ]; then
		**echo "$noquotes" > "$pagenumber.html"**
	fi
	done
	**noquotes=`cat "$pagenumber.html"`**

```

I have a question about it though. In my code it starts a subshell. How can I get that variable out of the subshell without writing it to a file and reading it back in after the subshell ends? 

Thanks (and thank you for those free online lessons Mr. C.)!


By the way, this is what the output looks like (from one page):
```

1 - one has been added
0 - one has been deleted
1 - one has been added
0 - one has been deleted
1 - one has been added
0 - one has been deleted
1 - one has been added
0 - one has been deleted
1 - one has been added
0 - one has been deleted
1 - one has been added
0 - one has been deleted
1 - one has been added
0 - one has been deleted
1 - one has been added
0 - one has been deleted
1 - one has been added
0 - one has been deleted
1 - one has been added
2 - one has been added
3 - one has been added
2 - one has been deleted
1 - one has been deleted
0 - one has been deleted

```

---

### Post by Mr. C. on 2007-08-11
Output the value on STDOUT and capture the output into a variable.

In your script, you are using a number of "echo | grep" sequences.  Since all you are trying to do is check if the line matches a pattern, use a sequence of if-then-else type clauses to eliminate the grep:

```
if [ "$line" = "</table>" ] ; then
   ...
elsif [ "$line" = "..." ] ; then
   ...
fi

```

MrC

---

### Post by Cappy on 2007-08-12
"Output the value on STDOUT and capture the output into a variable."
Could you show me how? I'm not sure how to do it here.

Wow, you're right about the greps for sure!
The program speed went from 12 seconds a page to only a .4 second =P That's a lot of of time savings!

Now I only have one grep and it doesn't even run until "$deleteatable" is greater than 0.
It seems each of those greps was taking up 4seconds of the parsing each! (I had left the "</html>" grep on and it took 4seconds and something).

What would work even better would be a grep for each of the two terms with it printing out the line numbers. Then, loop through the line numbers generated from the TABLESTART from greatest to smallest. Then, find the closest </table> that is below it. It will do this for each number from the TABLESTART grep. Then, it will compare the numbers; if the start of a deletion is inbetween the range of another area queued for deletion it will remove the nested statement from the deletion queue. Then it will delete each area.

I'm not going to write that because I don't want to deal with an array for this silly project of mine but someone might want to use that if they need a [much] faster method to parse webpages.

---

### Post by Mr. C. on 2007-08-12
> **Cappy said:**
> 
Could you show me how? I'm not sure how to do it here.

Two forms, which do the same thing:
```
var=$(echo good)
echo $var
var=`echo job`
echo $var
```
> **Cappy said:**
> 
Wow, you're right about the greps for sure!
The program speed went from 12 seconds a page to only a .4 second =P That's a lot of of time savings!

Avoiding extra process starts, especially  in loops is always a great savings.
> **Cappy said:**
> 
Now I only have one grep and it doesn't even run until "$deleteatable" is greater than 0. It seems each of those greps was taking up 4seconds of the parsing each! (I had left the "</html>" grep on and it took 4seconds and something).

I'll bet that one can be deleted as well.

You can do your variable assignment without expr as well.  For example:
```


(( var++ ))
(( var = var + 1 ))
```

> **Cappy said:**
> 
What would work even better would be a grep for each of the two terms with it printing out the line numbers. Then, loop through the line numbers generated from the TABLESTART from greatest to smallest. Then, find the closest </table> that is below it. It will do this for each number from the TABLESTART grep. Then, it will compare the numbers; if the start of a deletion is inbetween the range of another area queued for deletion it will remove the nested statement from the deletion queue. Then it will delete each area.
The ideal and natural solution here is to use recursion, as this solves the nesting problem.  You essentially start your process loop until you see either a new opening element, in which case you call your self again, or a closing element, in which case you return.
> **Cappy said:**
> 
I'm not going to write that because I don't want to deal with an array for this silly project of mine but someone might want to use that if they need a [much] faster method to parse webpages.
Understood.  There are already, for example, perl packages that do all of this. But your're learning the shell, so thats a good enough reason to continue.

Show your new code so other's can learn too.

MrC

---

### Post by Cappy on 2007-08-12
> **Mr. C. said:**
> Two forms, which do the same thing:
```
var=$(echo good)
echo $var
var=`echo job`
echo $var
I am still not sure how I can use this in my code to retieve the variable $noquotes out of the huge sub shell.


I have a problem with my code:
It is running this paragraph as though it was as one line (even though it isn't)
[CODE]
<td colspan="2" class="postbody"><span class="postbody"></span>
<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">
<tr> 
	  <td><span class="genmed"><b>Cappy wrote:</b></span></td>
	</tr>
	<tr>
	  <td class="quote"></span>
<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">
<tr> 
	  <td><span class="genmed"><b>xander wrote:</b></span></td>
	</tr>
	<tr>
	  <td class="quote"><span style="font-weight: bold">daset</span>

```

So a grep for the table finds it in there. The biggest problem is that there are TWO tables in there.
Simple right?
```

grep -c '<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">'

```
The output is "1".

So I don't get this: It is counting a whole paragraph as a "line" and then when I try to use grep to count the number of tables it only says the pattern is only on one line? Why is it counting this whole paragraph as one line?

A example of the page I am parsing is here:
[http://forums.introversion.co.uk/defcon/introversion/viewtopic.php?t=886&postdays=0&postorder=asc&start=266](http://forums.introversion.co.uk/defcon/introversion/viewtopic.php?t=886&postdays=0&postorder=asc&start=266)
The top post is the one that is having this problem (as are most posts with quotes inside quotes). I thought the "$line" = tablestartingtags was working but it doesn't so disregard that.

Also, if I try to print that long paragraph that is detected as a $line into the terminal using "echo $line"
it only displays this on a line:
```

<tr> e w  <td class="quote"><span style="font-weight: bold">daset</span>ter">

```

This is weird!

---

### Post by Mr. C. on 2007-08-12
I can't help show you what to do regarding your "huge sub shell" unless you show your code.

Remove the idea of "paragraphs" from your thinking.  There is no such concept in plain ASCII files.  Only new lines are recognized.  And grep is a line oriented utility - it too has no notion of paragraphs.

Look at the file with the **od** utility:

```
od -bc somefile
```

and see what actual characters are in the file.  It will look like this:

```
$ cat x
line 1
line 2
$ od -bc x
0000000 154 151 156 145 040 061 012 154 151 156 145 040 062 012
          l   i   n   e       1  \n   l   i   n   e       2  \n
0000016
```

The \n chararcters are the newlines.  This should help clarify things for you.

MrC

---

### Post by Cappy on 2007-08-13
ah "od", I was looking for that earlier. I knew you used it in one of the lessons.

I found out it was a \r at the end of each line
```

page=`echo "$page" | tr '\r' '\n'`
```
fixed the problem =) unix2dos only converts "\r\n" to "\n" so that wasn't an option.

As for the subshell problem it is this whole block of code:
```

echo "${page}" | while read line; do
	if [ "$line" = '<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">' ]; then
		deleteatable=`expr "$deleteatable" + 1`
		echo "$deleteatable - one has been added"
	elif [ "$deleteatable" -gt 0 ] && [ "`echo "$line" | grep '</table>'`" ]; then
		deleteatable=`expr "$deleteatable" - 1`
		echo "$deleteatable - one has been deleted"
	elif [ "$deleteatable" -eq 0 ]; then
		noquotes="$noquotes
$line"
	fi
	if [ "$line" = '</html>' ]; then
		**echo "$noquotes" > "$pagenumber.html"**
	fi
done
**noquotes=`cat "$pagenumber.html"`**

```
I bolded my workaround which is to write $noquotes to a file and read it back in after the subshell.


Here is my entire (mostly) finished script:
```

#!/bin/sh
#Author: Cappy of ubuntuforums.org
#Special thanks to: Mr. C.
#
#Purpose: Find out who voted against who in a game of TWG
#
#Go through a phpbb forum, get rid of anything in s,
#pick out the bold words, put the player's name who posted the bold word inside the bold word,
#filter out the GameMaster's posts, and finally print the bold word (with the player's name) to index.html
#
# The name of the game is TWG (The Werewolf Game)
# http://70.85.192.194/~loogsla/twg.shtml
#
#* This program is free software. It comes without any warranty, to
#* the extent permitted by applicable law. You can redistribute it
#* and/or modify it under the terms of the Do What The **** You Want
#* To Public License, Version 2, as published by Sam Hocevar. See
#* http://sam.zoy.org/wtfpl/COPYING for more details.
#
startpage='http://forums.introversion.co.uk/defcon/introversion/viewtopic.php?t=886&postdays=0&postorder=asc&start='
pagenumber=266 ##Page number to start the count at
GM="The GoldFish" ##Name of GM
while true; do
	page=`wget -q -O- "$startpage$pagenumber"` #Download page
	istherenext=`echo "$page" | grep 'Next</a></span>'` #Look to see if there is another page
	page=`echo "$page" | tr '\r' '\n'` #Convert returns to newlines
	deleteatable=0
	noquotes=""
	echo "$pagenumber"
	echo "${page}" | while read line; do
		if [ "$line" = '<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">' ]; then
			deleteatable=`expr "$deleteatable" + 1`
			#echo "LINE2: $line" >> lineproblem.txt
			#echo "$line"
			echo "$deleteatable - one has been added"
		elif [ "$deleteatable" -gt 0 ] && [ "`echo "$line" | grep '</table>'`" ]; then
			deleteatable=`expr "$deleteatable" - 1`
			echo "$deleteatable - one has been deleted"
		elif [ "$deleteatable" -eq 0 ]; then
			noquotes="$noquotes
$line"
		fi
		if [ "$line" = '</html>' ]; then
			echo "$noquotes" > "$pagenumber.html"
		fi
	done
	noquotes=`cat "$pagenumber.html"`
	skip=1
	echo "${noquotes}" | while read line; do
		#Start greps the line before the username
		
		#TEMPLATE SPECIFIC for extra speed - If you use this on another forum
		#you must remove this if statement and set deleteatable=2 for every loop through
		#This is just a line that appears before the name fields, it would be even better to replace this
		#line with a line from your forum's template
		if [ "$line" = '<td class="viewTopicBoxStart">' ]; then
			deleteatable=1
		#Grep for username
		elif [ "$deleteatable" -gt 0 ] && [ -n "`echo "$line" | grep -o '<a name="[^"]*"></a><b>[^<]*</b>'`" ]; then
			tablestart=`echo "$line" | grep -o '<a name="[^"]*"></a><b>[^<]*</b>'`
			deleteatable=2
			lastname="$tablestart"
			#Don't write to variable if it is the GM posting
			if [ "`echo "$lastname" | grep "$GM"`" ]; then
				skip=1
			else
				skip=0
			fi 
		#Grep for bolded words
		elif [ "$deleteatable" -eq 2 ] && [ "`echo "$line" | grep '<span style="font-weight: bold">'`" ]; then
			lastname=`echo "$lastname" | grep -o '<b>[^<]*</b>' | sed 's/<b>//g' | sed 's/<\/b>//g'`
			line=`echo "$line" | sed s/'<\/span>/'" was voted by: $lastname"'<\/span>/g'`
			line="$lastname: $line" 
			deleteatable=0
		#Stop the greps once the user's post is over
		elif [ "$deleteatable" -gt 0 ] && [ "`echo "$line" | grep '</span><span class="gensmall">'`" ]; then
			deleteatable=0
		#Stop greps at the end of the area for all user posts
		#TEMPLATE SPECIFIC for extra speed - can be left alone
		elif [ "$line" = '<td class="catBottom" colspan="2" height="28" align="center">' ]; then
			deleteatable=0
		#Workaround
		elif [ "$line" = '</html>' ]; then
			echo "$noquotesinner" > "$pagenumber.html"
		fi
		if [ "$skip" -eq 0 ]; then
			noquotesinner="$noquotesinner
$line"
		fi
	done
	noquotes=`cat "$pagenumber.html"`
	results=`echo "$noquotes" | grep '<span style="font-weight: bold">'`
	allresults="$allresults
pagenumber: $pagenumber
$results"
	if [ -z "$istherenext" ]; then
		echo '<pre>' > index.html
		echo "$allresults" | grep -o '<span style="font-weight: bold">[^<]*</span>' >> index.html
		echo '</pre>' >> index.html
		exit
	else
		pagenumber=`expr "$pagenumber" + 15`
	fi
done

```
It takes about 5 seconds a page, .5 seconds is for the table removal, 4.5 seconds for the adding of the poster's name into the bolded word.

---

### Post by Mr. C. on 2007-08-14
You're still using the awfully clumsy and expensive "echo | grep" throughout.  Its entirely unnecessary, slow, and wasteful.  The web page you are accessing is 1339 lines.  That means, you are potentially starting up near that many processes !  This is very slow.  Instead, you want to optimize the program to call as few external programs as possible.

You're doing things in a rather circuitous manner.  Instead of placing the entire page you retrieved via wget into a variable (where variable assignment strips newlines, I might add), just send the output of wget into a pipe, and work on your page line by line. You are creating a simple parser, and you can do what you want line by line.

Here's the idea, rewriting the first part of your script.  You should note how much faster it is, and you should find it much easier to read:

```
#!/bin/bash

pagenumber=266 ##Page number to start the count at
startpage='http://forums.introversion.co.uk/defcon/introversion/viewtopic.php?t=886&postdays=0&postorder=asc&start='
GM="The GoldFish" ##Name of GM

echo "$pagenumber"
echo "$page"

let tablelevel=0

wget -q -O- "$startpage$pagenumber" | 
    tr '\r' '\n' |
    sed -e 's/<table/\n<table/g' -e 's/<\/table/\n<\/table/g' |

    while read line; do
            if [[ "$line" == '<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">'* ]]; then
                    (( tablelevel++ ))
                    1>&2 echo Table level $tablelevel
                    continue
            elif [[ "$line" == '</table>'* ]] && [ $tablelevel -gt 0 ] ; then
                    (( tablelevel-- ))
                    1>&2 echo Table level $tablelevel
                    continue
            fi
            echo $line
    done > ${pagenumber}.html
```

By forcing the table start and end tags to be on a new line, you can strip out entire tables easily, but simply not outputting the line, or any lines, until you see the end of the (first level) table.

Notice I've redirected the entire while loop's output.  While loops act like they are a sub-shell, in that you can redirect their output as a whole.

I placed that output into a file, as you had done, but that is entirely unnecessary as an intermediate step; you can do the remainder of your processing in the same loop.

To allow diagnostic output, I've merged STDIN into STDERR for the echo statements.  This allows output to your terminal (via STDERR) and prevents the diagnostics from being part of the while loop's redirected STDIN.

All you have to do is add similar if-elif lines to match your other patterns.  This essentially creates what is called a state machine.  You will output lines when in a certain state (eg. not in a table), and suppress output when in another state (eg. in a table).

MrC

---

### Post by Cappy on 2007-08-14
Wow, thank you so much Mr. C! =)

I like how you added the \n to the </table> so it doesn't need a grep anymore also.

```
'</table>'*
```
I didn't know the * was possible in this case either.

You answered my questions about the subshell too. I was wondering how exactly that worked. I didn't realize I would  just echoed it and it would go into the file. I will probably end up using this with getlibs to run part of the code with Parallel execution.

I was googling around looking for extra ways to speed up the script and I found this:
[http://www.los-gatos.ca.us/davidbu/faster_sh.html](http://www.los-gatos.ca.us/davidbu/faster_sh.html)
which looks like it could be extremely useful in parsing large files also.

I bet I will have it down to at least a second a page soon (thanks to your help!). I'll post back once I rewrite the script. =)

I wish I had an awesome teacher like you, my programming teachers so far just give it back and give me a 100 =P

---

### Post by Mr. C. on 2007-08-14
You're welcome.

The * at the end of the line is part of pattern matching available in bash (but not sh or ksh).  Search for Pattern in the bash man page for more info.

In the Bourne shell, a while loop was actually executed in a sub-shell.  In Bash, this is merely emulated, and no sub-shell is exec'd.

The link you post is interesting.  The author claims the results are for the Bourne shell.  There are lots of esoteric techniques like those mentioned.  Unless speed is critical, there's no reason convolute otherwise simple code.  In your case, the bulk of the time was spent in starting numerous processes.  Avoiding that is #1 on the list of avoidances.  You'll find you can process the 1300+ lines in no time.  If you really want speed, move to perl or python, or even C.

Please do follow-up.  Its nice to see what people come up with, and other's learn too.

Its a sad state when instructors are nothing more than gold-star-giving babysitters.  I abhor such "instructors".

MrC

---

### Post by Cappy on 2007-08-14
Alright! =)

bash is apparently EXTREMELY slow (maybe that is what that link I gave earlier would do, it would speed up bash up to be as fast as sh?)

Here is your script you posted:
```

$ time bash speedtestbash

real    0m0.926s
user    0m0.832s
sys     0m0.100s

```

Here is my script:
```

$ time sh speedtestsh

real    0m0.551s
user    0m0.392s
sys     0m0.136s

```

Now here is your script turned into sh:
```

#!/bin/sh
startpage='http://forums.introversion.co.uk/defcon/introversion/viewtopic.php?t=900&postdays=0&postorder=asc&start='
pagenumber=36 ##Page number to start the count at
GM="Tripper" ##Name of GM
	#page=`wget -q -O- "$startpage$pagenumber"` #Download page
	noquotes=""
	tablelevel=0

	cat "$pagenumber-saved" | 
    	tr '\r' '\n' |
    	sed -e 's/<table/\n<table/g' -e 's/<\/table/\n<\/table/g' |
   	while read line; do
        	if [ "$line" = '<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">' ]; then
                	#(( tablelevel++ ))
			tablelevel=`expr "$tablelevel" + 1`
                    1>&2 echo "Table level $tablelevel"
                    continue
        	elif [ "$line" = '</table>' ] && [ "$tablelevel" -gt 0 ]; then
                    tablelevel=`expr "$tablelevel" - 1`
                    1>&2 echo "Table level $tablelevel"
                    continue
            	fi
            	echo $line
   	done > ${pagenumber}.html

```
And here is the results from that:
```

$ time sh speedtestbash

real    0m0.191s
user    0m0.052s
sys     0m0.148s

```
(1/3rd of my script!)

Now I redid my script and I have the time down to *drum roll*
```

$ time sh TGFTWG

real    0m0.112s
user    0m0.056s
sys     0m0.072s

```
which makes it 44 times faster than my old script!

I did all these tests by doing a "cat savedpage.html" so that my internet speed wouldn't affect them.

I improved the speed using a lot of tips from your code. For instance:
's/<a name="[^"]*"><\/a><b>**\([^>]*\)**<\/b>/\nNAMEBELOW:\n**\1**\n/g'
Where sed takes the bold word, puts that bold word on its own line, and puts "NAMEBELOW:" on its own line above it. I **bolded** the part where I captured the Bolded word/name and then where I put it on its own line with \1.

One part of my new script's speed is here:
```

#Skip lines before and after posts to improve speed
if [ "$skip" -eq 1 ] && [ "$line" != 'NAMEBELOW:' ]; then
	continue
fi
skip=0

```
which skips lines until the first post, after each post, and after a bolded word (to prevent detecting multiple bolded words in one post). This skips the huge majority of lines with minimal effort.

I've learned a lot from your example =)

Here is my new script:
```

#!/bin/sh
#Author: Cappy of ubuntuforums.org
#Special thanks to: Mr. C.
#
#Purpose: Find out who voted against who in a game of TWG
#
#Go through a phpbb forum, get rid of anything in s,
#pick out the bold words, put the player's name who posted the bold word inside the bold word,
#filter out the GameMaster's posts, and finally print the bold word (with the player's name) to index.html
#
# The name of the game is TWG (The Werewolf Game)
# http://70.85.192.194/~loogsla/twg.shtml
#
#* This program is free software. It comes without any warranty, to
#* the extent permitted by applicable law. You can redistribute it
#* and/or modify it under the terms of the Do What The **** You Want
#* To Public License, Version 2, as published by Sam Hocevar. See
#* http://sam.zoy.org/wtfpl/COPYING for more details.
#
startpage='http://forums.introversion.co.uk/defcon/introversion/viewtopic.php?t=900&postdays=0&postorder=asc&start='
pagenumber=36 ##Page number to start the count at
IgnorePostsFrom="Tripper\|xander" ##Name of GM (case-sensitive) or any other people whos "votes" shouldn't count
while true; do
	page=`wget -q -O- "$startpage$pagenumber"` #Download page
	#page=`cat $pagenumber`
	istherenext=`echo "$page" | grep 'Next</a></span>$'` #Look to see if there is another page
	noquotes=""
	tablelevel=0
	skip=1

	echo "$page" | 
    	tr '\r' '\n' |
    	sed -e 's/<table/\n<table/g' -e 's/<\/table/\n<\/table/g' -e 's/<\/span><span class="gensmall">/\n<\/span><span class="gensmall">\n/g' -e \
	's/NAMEBELOW:/NAME BELOW:/g' -e 's/BOLDBELOW:/BOLD BELOW:/g' -e 's/<a name="[^"]*"><\/a><b>\([^>]*\)<\/b>/\nNAMEBELOW:\n\1\n/g' -e \
	's/<span style="font-weight: bold">\([^<]*\)<\/span>/\nBOLDBELOW:\n\1\n/g' |
   	while read line; do
		#Skip lines before and after posts to improve speed
		if [ "$skip" -eq 1 ] && [ "$line" != 'NAMEBELOW:' ]; then
			continue
		fi
		skip=0

        	if [ "$line" = '<table width="90%" cellspacing="1" cellpadding="3" border="0" align="center">' ]; then
			tablelevel=`expr "$tablelevel" + 1`
                	#1>&2 echo "Table level $tablelevel"
                	continue
        	elif [ "$tablelevel" -gt 0 ] && [ "$line" = '</table>' ]; then
                	tablelevel=`expr "$tablelevel" - 1`
                	#1>&2 echo "Table level $tablelevel"
                	continue
            	elif [ "$tablelevel" -gt 0 ]; then
			continue
		fi
		#Beginning of a user's post get their user name
		if [ "$line" = 'NAMEBELOW:' ]; then
			read line
			postername="$line"
			if [ "`echo "$postername" | grep "$IgnorePostsFrom"`" ]; then
				skip=1
			else
				skip=0
			fi
			continue
		#Grep for bolded words
		elif [ "$line" = 'BOLDBELOW:' ]; then
			read line
			echo "$line was voted by: $postername"
			skip=1
			continue
		#Stop the greps once the user's post is over
		elif [ "$line" = '</span><span class="gensmall">' ]; then
			skip=1
			continue
		fi
	done > ${pagenumber}.html
	page=`cat "$pagenumber.html"`
	echo "page $pagenumber is done."
	allresults="$allresults
$page"
	if [ -z "$istherenext" ]; then
		echo '<pre>' > index.html
		echo "<pre>$allresults</pre>" > index.html
		exit
	else
		pagenumber=`expr "$pagenumber" + 15`
	fi
done

```

<3 Mr. C., I couldn't have made that without you

---

### Post by Mr. C. on 2007-08-15
Nice work Cappy!

Now, let me suggest that you pass in the page number as an argument to your script instead of using the hardcoded pagenumber=36.

See if you can get rid of:

```
	istherenext=`echo "$page" | grep 'Next</a></span>'` #Look to see if there is another page
```

by doing your checks inline.

Keep up the good work.
MrC

---

