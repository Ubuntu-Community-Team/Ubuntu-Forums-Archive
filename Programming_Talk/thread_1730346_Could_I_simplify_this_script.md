---
title: "Could I simplify this script"
date: 2011-04-15
forum: Programming Talk
---

### Post by towheedm on 2011-04-15
I'm not much a scripter, so I'd appreciate any help in simplifying this part of my script:
```
# Ask user if they would like to set the theme as their new theme.
# FIXME Could this be simplified?
echo -n "Would you like to set this as your new theme? (yes/no) "
read RESPONSE
if [ "${RESPONSE}" = "yes" ] ; then
    MKCONFIG_FILE=`echo ${GRUB_DIR} | sed -e s,^/boot,, -e s,^/,,`-mkconfig
    echo "GRUB_MKCONFIG: ${MKCONFIG_FILE}"
    if [ -f ${GRUB_FILE} ] ; then
        if grep -q ^#GRUB_THEME= ${GRUB_FILE} ; then
            sed s,^#GRUB_THEME=.*,${THEME_DIR}/${THEME_DEFINITION_FILE}, <${GRUB_FILE} >${GRUB_FILE}.~
            mv ${GRUB_FILE}.~ ${GRUB_FILE}
        elif grep -q ^GRUB_THEME= ${GRUB_FILE} ; then
            sed s,^GRUB_THEME=.*,${THEME_DIR}/${THEME_DEFINITION_FILE}, <${GRUB_FILE} >${GRUB_FILE}.~
            mv ${GRUB_FILE}.~ ${GRUB_FILE}
        else
            echo -e "\nGRUB_THEME=${THEME_DIR}/${THEME_DEFINITION_FILE}" >>${GRUB_FILE}
        fi
    else
        echo "${GRUB_FILE} was not found!"
        exit
    fi

    # Generate grub.cfg
    if [ -f `which ${MKCONFIG_FILE}` ] ; then
        `which ${MKCONFIG_FILE} -o ${GRUB_DIR}/grub.cfg
    else
        echo "Could not find GRUB's mkconfig script file."
        exit
    fi
fi
```The following vars are defined elsewhere in the script:
GRUB_DIR can be one of 3 values: /grub , /boot/grub or /boot/grub2
THEME_DIR=${GRUB_DIR}/themes
THEME_DEFINITION_FILE=theme.txt
GRUB_FILE=/etc/default/grub

Thanks.

---

### Post by Crusty Old Fart on 2011-04-16
> **towheedm said:**
> I'm not much a scripter, so I'd appreciate any help in simplifying this part of my script:

The only part that looked like it could be simplified to me was if you used parameter expansion to parse what you want to be held in the MKCONFIG_FILE variable instead of using the echo | sed pipeline as follows:
```

***[COLOR=Red]~~~ Change the following line: ~~~[/COLOR]***
MKCONFIG_FILE=`echo ${GRUB_DIR} | sed -e s,^/boot,, -e s,^/,,`-mkconfig

***[COLOR=Green]~~~ To this: ~~~[/COLOR]***
MKCONFIG_FILE=${GRUB_DIR##*/}-mkconfig

```The rest of it looks okay. I'd have written it a little differently, but my changes wouldn't have amounted to much more than a difference in coding style. Although, I'd be remiss if I didn't point out that it is bad programming practice to make variable names all upper-case. There's a risk of conflicting with built-in system bash variables which are all upper-case. 

> **towheedm said:**
> Thanks.

You're welcome.

---

### Post by towheedm on 2011-04-16
> MKCONFIG_FILE=${GRUB_DIR##*/}-mkconfigCould you explain this?  I can't recall seeing this explained anywhere.

> Although, I'd be remiss if I didn't point out that it is bad programming
 practice to make variable names all upper-case. There's a risk of 
conflicting with built-in system bash variables which are all 
upper-case. Thanks for the advice.  It's an old habit left over from programming VB under Windows.

---

### Post by Crusty Old Fart on 2011-04-16
Howdy towheedm:

> **towheedm said:**
> Could you explain this?  I can't recall seeing this explained anywhere...

Sure. It's called parameter expansion. I used it to strip off the directory path to the grub file. The easiest way to explain it is by examples.
You can see some examples at the following link:
[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

> **towheedm said:**
> 
Thanks for the advice.  It's an old habit left over from programming VB under Windows.
Ugh...VBScript...yuck...another object-oriented POS from Microsuck.

Just notice how upper-case variables can get you into trouble. The grub file is loaded with them and you are modifying the value assigned to GRUB_THEME. So, you're much better off leaving all upper-case variable names to the system.

By the way, I noticed some mistakes and found a way to clean things up a bit by making use of some regex in grep and sed. Also I recoded the script in my own style:

[LIST]
[*]I don't use backticks. They've been superseded by $() command substitution. Those itty-bitty backticks were too hard for my old eyes to see anyway, so I'm glad to see them relegated to the dust bin of obsolete code.
[*]I use the newer [[ keyword for tests.
[*]I don't use all upper-case variable names.
[*]You may notice other differences.
[/LIST]
 
See how this works for you:
```

#!/bin/bash
set -e

# Ask user if they would like to set the theme as their new theme.
# FIXME Could this be simplified?

echo -n "Would you like to set this as your new theme? (yes/no) "
read Response

if [[ $Response == yes ]]; then
  mkConfig_File=${Grub_Dir##*/}-mkconfig
  echo GRUB_MKCONFIG: $mkConfig_File

  if [[ -f $Grub_File ]]; then

    if grep -qe '^#\{0,1\}GRUB_THEME=' $Grub_File; then
      sed "s,^#\{0\,1\}GRUB_THEME=.*,GRUB_THEME=$Theme_Dir/$Theme_Definition_File," <$Grub_File >$Grub_File.~
      mv $Grub_File.~ $Grub_File
    else
      echo -e "\nGRUB_THEME=$Theme_Dir/$Theme_Definition_File" >>$Grub_File
    fi

  else
    echo "$Grub_File was not found!"
    exit 0
  fi  

  # Generate grub.cfg
  if [[ -f $(which $mkConfig_File) ]]; then
    $(which $mkConfig_File) -o $Grub_Dir/grub.cfg
  else
    echo "Could not find GRUB's mkconfig script file."
    exit 0
  fi  
fi

exit 0

```Happy to answer any questions,

Crusty

---

### Post by towheedm on 2011-04-16
> I don't use backticks. They've been superseded by $() command substitution.I saw this in the tutorials but was not sure which was better.  I was following by example from some of GRUB's script files in /etc/grub.d.  Since the back-ticks have been superseded, I will certainly follow your example.

I'm just started learning about regex and eregex and practicing as I go along.  I know I still have quite a bit to learn and I am forever grateful for your recommendations.

I'm trying to finish this script for the 2nd edition of my '[Beginner's Guide to Theming GRUB]("http://ubuntuforums.org/showthread.php?t=1534689")' using the gfxmenu theming engine, so it may not be as elegant as I'd like it to be.

Your code is certainly simpler and more elegant than mine.  I'll go through it later tonight referring back to the tutorial I'm using on regex to better understand it.

I thank you a lot for your help master scripter.

towheedm

---

### Post by Crusty Old Fart on 2011-04-16
Since you're going to have your nose in the books, I'll give you a head start.
Let's look at this line of code:
```

if grep -qe **[COLOR=Blue]'^#\{0,1\}GRUB_THEME='[/COLOR]** $Grub_File; then

```The blue part is the regex. You know that **[B][COLOR=Blue]^#[/COLOR]**[/B] matches a pound sign at the beginning of the line. This: **[COLOR=Blue]{0,1} [/COLOR]**matches the preceding character zero or one time. But grep needs to have the braces {} escaped with backslashes, thus: **[COLOR=Blue]\{0,1\}[/COLOR]** followed with **[COLOR=Blue]GRUB_THEME=[/COLOR]**

So, we are matching: lines beginning with:
**GRUB_THEME=** (zero occurrence of a beginning pound sign)
...or...
**#GRUB_THEME=** (one occurrence of a beginning pound sign)

By matching either of these with regex, we don't need the **elif** section in your original **if** stack.

Similarly with our following sed command:
```

sed "s,**[COLOR=Green]^#\{0\,1\}GRUB_THEME=[/COLOR]**.*,**[COLOR=Red]GRUB_THEME=[/COLOR]**$Theme_Dir/$Theme_Definition_File,"

```Notice the green part. Sed needs the braces {} escaped with backslashes just like grep does. Additionally, the comma between the zero and one needs to be escaped for ***this particular sed command*** because we used commas to delineate between the find field and the replace field in our sed construct.

You'll see the red **[COLOR=Red]GRUB_THEME=[/COLOR]** part that has been added, which wasn't in your original code. I think that was just an oversight on your part. The first part of the sed command removes ***everything*** on a line that begins with either **GRUB_THEME=** ...or...    **#GRUB_THEME=** 
So, we need to put **[COLOR=Red]GRUB_THEME=[/COLOR]** back in so we can assign it the values stored in:
$Theme_Dir/$Theme_Definition_File

Get it?

Have fun,

Crusty

---

### Post by Crusty Old Fart on 2011-04-16
**[COLOR=Blue]New version to handle situations when there is more than one line in the grub file beginning with GRUB_THEME= or #GRUB_THEME=[/COLOR]**
```

**[COLOR=Red]~~~ CRAP CODE REMOVED ~~~[/COLOR]**

```

---

### Post by towheedm on 2011-04-16
Thank you very much for that heads up on the grep command.  Yes, the missing GRUB_THEME= in my original code was a mistake on my part.  Realized it late last night when I tested the script.

As for multiple occurrences of lines beginning with GRUB_THEME=, GRUB will use the theme specified by the last occurrence of a line starting with GRUB_THEME=.  Hmm, did not think about multiple occurrences of GRUB_THEME=.  So now I guess I'll have to clean up the user's grub file by deleting any additional lines starting with GRUB_THEME= or #GRUB_THEME=.

---

### Post by Crusty Old Fart on 2011-04-17
> **towheedm said:**
> Thank you very much for that heads up on the grep command.  Yes, the missing GRUB_THEME= in my original code was a mistake on my part.  Realized it late last night when I tested the script.
You're mighty welcome.

> **towheedm said:**
> 
As for multiple occurrences of lines beginning with GRUB_THEME=, GRUB will use the theme specified by the last occurrence of a line starting with GRUB_THEME=.  Hmm, did not think about multiple occurrences of GRUB_THEME=.  So now I guess I'll have to clean up the user's grub file by deleting any additional lines starting with GRUB_THEME= or #GRUB_THEME=.

There are several ways to handle this problem. The code you had in post #1 would have assigned a new value for GRUB_THEME on the first occurrence of #GRUB_THEME. If it didn't find #GRUB_THEME, it would have assigned a new value for GRUB_THEME on the first occurrence of GRUB_THEME. If it didn't find either #GRUB_THEME or GRUB_THEME, it would have added a line at the end of the grub file to assign a value to GRUB_THEME. 

The simplified code that I put in post #4 worked a little differently. It would have assigned a value to GRUB_THEME on the first occurrence of #GRUB_THEME or GRUB_THEME, whichever came earlier in the grub file. If it didn't find either one, it would have added a line at the end of the grub file to assign a value to GRUB_THEME.

Both of these approaches have the propensity to fail if there are multiple instances of lines beginning with #GRUB_THEME and/or GRUB_THEME.

Even the code I wrote in post #7 was hosed. The way it was written, it would have changed all the lines beginning with either #GRUB_THEME or GRUB_THEME to lines that assign the value we want to GRUB_THEME. And, it would have told us that it was changing more than one line. However, here's how I hosed it: If there was only one line containing either #GRUB_THEME or GRUB_THEME, it would have done nothing to it and it would have added a new line at the bottom of the grub file assigning a value to GRUB_THEME. It wouldn't have resulted in a failure, but it was embarrassingly clunky, so I canned it.

[COLOR=Blue]**I think the best way to handle this is to remove all the lines in the grub file that begin with either #GRUB_THEME or GRUB_THEME and then just add a line at the bottom of the file containing the assignment for GRUB_THEME that we want.**[/COLOR]

Here's the code to do it:
```

#!/bin/bash
set -e

# Ask user if they would like to set the theme as their new theme.
# FIXME Could this be simplified?

echo -n "Would you like to set this as your new theme? (yes/no) "
read Response

if [[ $Response == yes ]]; then
  mkConfig_File=${Grub_Dir##*/}-mkconfig
  echo GRUB_MKCONFIG: $mkConfig_File

  if [[ -f $Grub_File ]]; then
    sed '/^#\?GRUB_THEME=/d' $Grub_File > $Grub_File.~ [COLOR=Blue]**#<--Edit: Hat tip to Vaphell for his suggestions in post #10.**[/COLOR]
    mv $Grub_File.~ $Grub_File
    echo -e "\nGRUB_THEME=$Theme_Dir/$Theme_Definition_File" >> $Grub_File
  else
    echo "$Grub_File was not found!"
    exit 0
  fi  

  # Generate grub.cfg
  if [[ -f $(which $mkConfig_File) ]]; then
    $(which $mkConfig_File) -o $Grub_Dir/grub.cfg
  else
    echo "Could not find GRUB's mkconfig script file."
    exit 0
  fi  
fi

exit 0

```There we go. That's better, simpler and cleaner.

---

### Post by Vaphell on 2011-04-17
not that it makes any difference but:

-r switch allows for clean regular expressions without escaping
```
sed '/^#\{0,1\}GRUB_THEME=/d'
```
is equivalent to
```
sed -r '/^#{0,1}GRUB_THEME=/d'
```

also {0,1} in regex is equivalent to ?
? = 0 or 1
* = 0 or more
+ = 1 or more
```
sed '/^#?GRUB_THEME=/d'
```

---

### Post by Crusty Old Fart on 2011-04-17
> **Vaphell said:**
> not that it makes any difference but:

-r switch allows for clean regular expressions without escaping
```
sed '/^#\{0,1\}GRUB_THEME=/d'
```is equivalent to
```
sed -r '/^#{0,1}GRUB_THEME=/d'
```also {0,1} in regex is equivalent to ?
? = 0 or 1
* = 0 or more
+ = 1 or more
```
sed '/^#?GRUB_THEME=/d'
```

Wow...Just when I think it couldn't get much better, a wizard appears and shares his magic. Thank you, Vaphell.

When I finish this post, I'll edit the code I put in post #9 to incorporate your suggestions.

I didn't know about the -r option for ERE sed. Thanks for educating me on that one. Unfortunately, I've always thought that the regex ? matched one character instead of zero or one. Now I know better, thanks to you.

However, in order for the regex ? to work, it needed to either be escaped or sed's -r option needed to be added. Consider the following:
```

sed '/^#?GRUB_THEME=/d' **[COLOR=Red]#<--This doesn't work.[/COLOR]**
sed -r '/^#{0,1}GRUB_THEME=/d' **[COLOR=Green]#<--This works.[/COLOR]**
sed -r '/^#?GRUB_THEME=/d' **[COLOR=Green]#<--This works.[/COLOR]**
sed '/^#\?GRUB_THEME=/d' **[COLOR=Green][COLOR=Blue]#<--This works and is my preference for brevity reasons.[/COLOR][/COLOR]**

```Like so many others, my knowledge of UNIX has been the result of nibbling away at it over the years whenever I've had the need to do something specific. One of these days, I need to sit down with a good, up-to-date manual and read the damned thing cover to cover.

Thanks again for popping in here and helping out. It's much appreciated.

All the best to you,

Crusty

---

### Post by Vaphell on 2011-04-17
yes, you are right, i should have tested it first :)
i usually run sed with -r, because i want to limit necessary escaping. Some of my regexes would become a mess because of all these \
if i want literal symbols i just put them in [ ], thank you very much :)

> I've always thought that the regex ? matched one character instead of zero or one.
it does in bash globbing (just like * means any sequence) but in regexes * and ? are not standalone symbols that consume chars but mere modifiers to the symbol before them. Besides it wouldn't make any sense, . does '1 of anything' already :)

---

### Post by towheedm on 2011-04-17
WOW!  So much to learn about BASH.  I know I've marked the post as solved, but could I please ask one question?
I've been reading through the link provided by Crusty in post #2, could you tell me which format is acceptable in scripting:

First:
```
[[ some test command ]] && consequent command
```or

Second:
```
if [[ some test command ]]; then
    consequent command
fi

```If I use the first, I'd reduce my script by about 40 lines but I'd like to use to use the one that's acceptable although both does the same thing.

---

### Post by Crusty Old Fart on 2011-04-17
> **towheedm said:**
> WOW!  So much to learn about BASH.  I know I've marked the post as solved, but could I please ask one question?
I've been reading through the link provided by Crusty in post #2, could you tell me which format is acceptable in scripting:

First:
```
[[ some test command ]] && consequent command
```or

Second:
```
if [[ some test command ]]; then
    consequent command
fi

```If I use the first, I'd reduce my script by about 40 lines but I'd like to use to use the one that's acceptable although both does the same thing.

Both are acceptable...and since they both use the [[ keyword for test, they are preferred over the older methods of test.

Your first example is what I like to use whenever I can. It works very well to test a condition and then execute a ***single*** command if the result of the [[ test ]] is true.
The code you have in your second example is needed when you have ***more than one*** command to execute when your [[ test ]] returns true, or have the need of a more complex if stack containing else's or elif's or nested if's etc.

Another trick you might like is:
```

[[ test ]] || command

```In the case above, the command will be excuted only if the [[ test ]] is false.

I also like these:
```

command1 && command2 [COLOR=Green]**#<--command2 will only be executed if the error status of command1 is: true**[/COLOR]

command3 || command4 [COLOR=Green]** #<--command4 will only be executed if the error status of command3 is: false.**[/COLOR]

```Note that the examples in the box above rely on the exit status of single ***commands*** instead of the results of conditional string [[ tests ]] or arithmetic (( tests )).

Just to take this whole bit even further...
This:
```

command1 && command2 || command3

```Is in many cases equivalent to this:
```

if command1; then
  command2
else
  command3
fi

```But in some cases it can get you into trouble. So, unless you know exactly how it's going to be interpreted, you may want to avoid it.
See the following pitfall: [http://mywiki.wooledge.org/BashPitfalls#cmd1_.26.26_cmd2_.7C.7C_cmd3](http://mywiki.wooledge.org/BashPitfalls#cmd1_.26.26_cmd2_.7C.7C_cmd3)

Here's an example of some code that I used recently to mount and unmount a drive and needed the command strings to always return an error status of true whether the drive was mounted or not.
```

sudo mount /media/music || true [COLOR=Green]**#<--will mount the drive if it is not already mounted and always return: true**[/COLOR]
...
... a bunch of code ...
...
sudo umount /media/music || true **[COLOR=Green]#<--will unmount the drive if it is mounted and always return: true [/COLOR]**

```Hope I didn't add too much more confusion to the matter.

---

