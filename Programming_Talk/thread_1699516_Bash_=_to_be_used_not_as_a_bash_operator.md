---
title: "Bash = to be used not as a bash operator"
date: 2011-03-03
forum: Programming Talk
---

### Post by highspider on 2011-03-03
Im trying to use the = in bash but not as a bash operator 
I couldn't get an escape sequence or string to work.
the issue i get is with this lines = signs "dd: unrecognized operand"
```

nice -10 dd if=$cd of=$dir/$file

```the full working code thanks to sisco311 and vox754 is here

```
#!/usr/bin/env bash
#
# Quick way to burn iso images of a cdrom disk - from the command.
# used mainly for backing data cd's and Operating system disk to storage drive
#
#edit below isodir line for the dir to save iso to  
#edit below cdrom for your cdrom drive
 
isodir="/media/storage/Software ISO"
cdrom="/dev/sr0"


 if [ ! -d "$isodir" ]; then
   echo "ERROR: ${isodir} does not exist" >&2
   exit 1
 fi
 
 echo -e "\t\t\tScript to write iso images from a cd" 

 #while file name is null-zero length or not .iso ask for a file name
  while [[ $file != *.iso ]]; do
   read -p "  Enter ISO image name example.iso: " file
 done
  
 #if file already exists 
 if [ -f "$isodir/$file" ] ; then
   echo "WARNING file name exists do you want to over write!"
 fi
 
 echo Ripping cd image to "$isodir/$file"
 #double check if location and name or ok
 read -p "       Enter \"y\" for (y)es: " dcheck 
 if [[ $dcheck != [yY] ]]; then
   echo "Aborted!"
   exit 1
 fi
 if mount|grep "$cdrom"; then #check if mounted
     echo "umounting disk"
     umount "$cdrom"
 fi 
 #write iso image with dd
 echo "Ripping"
 nice -10 dd if="$cdrom" of="${isodir}/${file}"  
 #older cds zero out badblocks ~ slower 
 #use below line inplace of above line dd
 #nice -10 dd_rescue -A "$cdrom" "${isodir}/${file}"

```

---

### Post by sisco311 on 2011-03-03
Please check out: [http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target)

and a good bash guide:  [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

You have to quote the variables:
```
nice -10 dd if="$cd" of="${dir}/${file}"
```

If you have any question, please feel free to ask.

---

### Post by highspider on 2011-03-03
thanks that works perfect.

 The biggest problem I have with searching the Internet is that I don't know what the heck to search for since I have no idea what to phrase my problem as.

---

### Post by tgalati4 on 2011-03-03
That is half the challenge--asking the right questions.

---

### Post by sisco311 on 2011-03-03
> **highspider said:**
> thanks that works perfect.

 The biggest problem I have with searching the Internet is that I don't know what the heck to search for since I have no idea what to phrase my problem as.

You're welcome!

Once again, check out the link to the guide I posted. And stay away from the
infamous TLDP guides.

The Internet is full of poorly written and/or inefficient bash script fragments & guides.

Ask your bash related question on freenode's #bash channel (or here).

---

### Post by sisco311 on 2011-03-03
> **tgalati4 said:**
> That is half the challenge--asking the right questions.

+1

@OP:

If you don't mind, I have a few suggestions...

Instead of the shebang you use, you should use `!#/usr/bin/env bash'.

You can replace:
```
if [ "$dcheck" == "y" -o "$dcheck" == "Y" ]; then
```
with:
```
if [[ "$dcheck" == [yY ]]; then
```

redirect the error messages to stderr:
```
echo "ERROR: ${dir} does not exist" >&2
```

Oh, and after:
```
echo "Aborted!"
```
you should quit the script with a non-zero exit status:
```
echo "Aborted!"
exit 1
```

---

### Post by highspider on 2011-03-04
I took your advice but for the life of me I can not get this line to work. I know like with case statements you can use y|Y) with the or and works fine with out being "" string. So i assumed that this should work and is the same. yet it doesn't

```
if [[ "$dcheck" == [yY ]]; then  
```Its always aborted. with Y or y or anykey. It looks way cleaner and want to know more of it and make it work.

I would have responed sooner but I'm playing with Natty Ubuntu. (which should never be upgraded on desktop that uses compiz-fusion) grrr took awhile to get here. metacity --replace & gnome-panel &

---

### Post by Vox754 on 2011-03-04
> **highspider said:**
> I took your advice but for the life of me I can not get this line to work. I know like with case statements you can use y|Y) with the or and works fine with out being "" string. So i assumed that this should work and is the same. yet it doesn't

```
if [[ "$dcheck" == [yY ]]; then  
```



You do realize there is a brace missing?

```

if [[ "$dcheck" == **[yY]** ]]
then
    echo matched
fi

```

Even if the original post was itself wrong, this is the kind of things you need realize by yourself. You can't possible expect to get always correct code.

---

### Post by SeijiSensei on 2011-03-04
> **highspider said:**
> I took your advice but for the life of me I can not get this line to work.

Try using an editor that supports syntax checking.  I use the text-mode editor [jed]("http://packages.ubuntu.com/lucid/jed") in emacs mode, but GUI editors like KDE"s kate have syntax checking as well.  (I suspect gedit does, too, but I haven't used GNOME is a long time now.)  A good syntax checker will use different colors to highlight command words and object strings and will complain if grouping characters like parentheses and braces are not balanced.

---

### Post by highspider on 2011-03-04
> **Vox754 said:**
> You do realize there is a brace missing?

```

if [[ "$dcheck" == **[yY]** ]]
then
    echo matched
fi

```Even if the original post was itself wrong, this is the kind of things you need realize by yourself. You can't possible expect to get always correct code.





  No I didn't know that.  thanks for your help
Sorry new to bash.  I don't get how the [ ] or works.  
 i would think it as 'char' with | binary or
if ( "$dcheck" ==  ( 'y'|'Y' )); then

some how i thought the one brace was meaning a binary or not a typo.  
so is [yY] in braces mean or?



I should have caught that
 My c++ teacher would add errors to code in class.  Because i would joke around with him one day he added an invisible char to my code aka hold alt+numbers
 it would not display the char in visual studio yet wouldn't comply.
  It was the worst error I ever had to debug.

---

### Post by Vox754 on 2011-03-05
> **highspider said:**
> No I didn't know that.  thanks for your help
Sorry new to bash.  I don't get how the [ ] or works.  
 i would think it as 'char' with | binary or
if ( "$dcheck" ==  ( 'y'|'Y' )); then

some how i thought the one brace was meaning a binary or not a typo.  
so is [yY] in braces mean or?

...

That is close to how it works, but it is not just a simple OR.

In general, the right hand side of that comparison uses pattern matching.
```

[[ left_hand == right_hand ]]

```

This means, that in the right hand side you can try to match regular expressions:
```

[AB]   # A or B
[ABC]  # A or B or C
[A-Z]  # Any character from A to Z
[a-zA-Z] # Any character from a to Z, a letter in either lower case or upper case
[AB]C[DE] # A letter A or B, followed by the C, followed by either the letters D or E
          # Possible combinations ACD, ACE, BCD, BCE
Value_[ABC]* # The word "Value_" followed by either A, B, or C,
             # and then followed by any number of characters
             # Combinations Value_A, Value_Ajjj, Value_Bmkl, Value_Crra, Value_Aii,
             # and many more

```

In order to get more info on this, search for "regular expressions", which are vital in many aspects of scripting, and other utilities such as "sed", "grep", "awk", and also appear in other programming languages such as Perl, Python, Java, Tcl.

Another advice.

Make your code readable. Use 4-space indentation, and make sure it is logically aligned.
```

if [ -d "$dir" ]
then
    echo "Ripping cd image to $dir"
    read -p "Enter a file name example.iso: " file
    echo "$dir/$file"
 
    if [ -f "$dir/$file" ] ; then
        echo "WARNING file name exists do you want to over write!"
        read -p "       Enter \"y\" for (y)es: " dcheck

        if [[ "$dcheck" == [yY] ]]
        then
...

```

You could test for the non-existence of the directory, return quickly, and thus save the initial long "if" statement.

```

if [ ! -d "$dir" ]
then
    echo "ERROR: $dir does not exist"
    exit 1
fi

echo "Ripping cd image to $dir"
read -p "Enter a file name example.iso: " file
echo "${dir}/${file}"

# Continue with script

```

Also, "cd" is already a reserved command to "change directory". You are over-writing it with the name of a variable. That's a bad idea.

Also, "dir" is normally an alias for "ls", overriding it too.

Use other variable names.

---

### Post by Vox754 on 2011-03-05
> **sisco311 said:**
> ...
Instead of the shebang you use, you should use `!#/usr/bin/env bash'.
...

Wrong!

It should be #! not !#

I know, it was a simple mistake.

However, talking more serious now. In the case of bash, there is not much use in calling "/usr/bin/env" in the first place.

Bash is a very important part of any Linux system. It's the freaking shell! So chances are that bash is always installed in "/bin/bash".

Most programs in "/bin" or "/sbin" are essential for the system to work, whereas those in "/usr/bin" and "/usr/sbin" are not, and can be installed later, or at the discretion of the system administrator.

Do you see my point? It may be the case that "/usr/bin/env" is not installed, while "/bin/bash" will most probably already be there.

So using the shebang "#!/bin/bash" is perfectly fine.

The shebang "#!/usr/bin/env python" is common with other interpreters, which may exist in different versions, or configured differently for different environments. But for bash, I think that is not needed.

---

### Post by highspider on 2011-03-05
Vox754 thank you very much for "match regular expressions:" 
  This helps a bunch. It must be hided in an advanced guide some where because I could not find it on the Internet.

  The reason I use one or two space.  aka trailing hanger indent.   Is because with large 'NESTED statements or giant classes / object c++". I found that code readably goes down with four spaces due to line breaks.  The indent is still there but rarely do I ever break a line. So I got to habit of using 2 max for a running hanger indent. 
BUT still took your good advice :)  didn't realize all my indents where crappy

  I'm still green to Linux; yet, hate windows.  I've even gone as far as set up my Ubuntu so when I kill it and have only tty mode I have full networking with Links2 to support graphics in tty mode with out needing X. Even a command gpm mouse and learned aptitude for packages. This way I can find the fix on the net and fix it with out ever booting windows.

Thank's again peoples you make learning a lot easer.

In a perfect world college professors would allow homework to be turned as CODE::BLOCK projects.

---

### Post by Vox754 on 2011-03-07
> **highspider said:**
> Vox754 thank you very much for "match regular expressions:" 
  This helps a bunch. It must be hided in an advanced guide some where because I could not find it on the Internet.


It's there in a good guide.

See: [http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

Also, the definite information is the official GNU Bash manual, which is readily available online.

[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

It is heavy, not meant to be read all at once, but to check specifics when you have doubts. 

With any program, always go for the "manual", if it exists, before starting searching random terms over the internet.

> 
  The reason I use one or two space.  aka trailing hanger indent.   Is because with large 'NESTED statements or giant classes / object c++". I found that code readably goes down with four spaces due to line breaks.  The indent is still there but rarely do I ever break a line. So I got to habit of using 2 max for a running hanger indent. 
BUT still took your good advice :)  didn't realize all my indents where crappy
...

I don't care. Use 4 spaces.

If your C++ code looks bad, you are not using it well enough. You should use additional functions, classes, and encapsulation to break your code into smaller pieces.

In the old days, people used to program C using real tabs for indents, and they usually set the tab to expand to 8 spaces on the screen, so the code would look heavily indented, but that was apparently a way to enforce clarity.

People said that if you have more than three levels of indentation, you are screwed anyway and your code needs to be broken up in smaller pieces.

Linus Torvalds, creator of the Linux kernel, said that, by the way. It's one of his famous quotes, and you can search for it if you want. Not everything that comes out of Linus is gold, but he is a competent and experienced programmer.

I recommend 4 spaces, as a more modern approach.

Your code can still be improved.

Again, you can avoid a long "if" statement, if you return quickly. Look at the "else" statement, it does nothing but aborting. Instead of testing for a positive match, test for a negative match, and return quickly if successful.

```

**if [[ "$dcheck" != [yY] ]]**
then
    echo "Aborted!"
    exit 1
fi

if mount|grep $cdrom
then
    echo "umounting disk"
    umount $cdrom
fi 

echo "Ripping"   
nice -10 dd if="$cdrom" of="${isodir}/${file}"  

```

In this case, you sequentially test for a lot of conditions, if all of these are false, it just goes to the bottom code, which does what you want, and it's not buried in various levels of indentation.

Why do you indent the "if" statements if they are at the top level? Keep them aligned, in column 0. Use whitespace, it's your friend.
```

**#!/bin/bash**

isodir="/media/storage/Software ISO"
cdrom="/dev/sr0"

 if [[ ! -d $isodir ]] ; then
   echo "ERROR: $isodir does not exist" >&2
   exit 1
 fi

 echo "Ripping cd image to $isodir"
 read -p "Enter a file name example.iso: " file
 echo "${isodir}/${file}"


if [[ -f ${isodir}/${file} ]] ; then
    echo "WARNING: file name exists"
    echo "Do you want to over write?"
    read -p "       Enter \"y\" for (y)es: " dcheck

    **#**
    **# This logically belongs here.**
    **# If the file does not exist, you don't even need**
    **# to test for [yY]**
    **#**
    if [[ $dcheck != [yY] ]] ; then
        echo "Not over-writing"
        echo "Aborted!"
        exit 1
    fi
fi

**# Quote your variables**
if mount | grep "$cdrom" ; then
    echo "Unmounting disk"
    umount "$cdrom"
fi 

echo "Ripping"   
nice -10 dd if="$cdrom" of="${isodir}/${file}"  

#older cds zero out badblocks ~ slower 
#nice -10 dd_rescue -A "$cdrom" "${isodir}/${file}"

```


Notice that I use "[[" in all instances. This is more powerful than "[". For example, you don't need to quote the variables.

"[[" is a Bash feature, while "[" exist for compatibility with the original Posix shell.

Read the wiki again: [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

---

### Post by highspider on 2011-03-07
[QUOTE=Vox754]
Notice that I use "[[" in all instances. This is more powerful than "[". For example, you don't need to quote the variables.
"[[" is a Bash feature, while "[" exist for compatibility with the original Posix shell.
[/QUOTE]

I read the guild about Korn [[. funny how the korn developers didn't name it something. (aka test2 or something)
it also gave me Idea for 
```
 while [[ $file != *.iso ]]; do
   read -p "  Enter ISO image name example.iso: " file
 done

```I took your advice and made corrections.

The logic behind below code is to double check the user before writing.  Since ripping takes awhile, It gives a the pause needed to verify that user is ok to write that name.iso or overwrite existing name.iso
```
 if [[ $dcheck != [yY] ]]; then 
```

---

