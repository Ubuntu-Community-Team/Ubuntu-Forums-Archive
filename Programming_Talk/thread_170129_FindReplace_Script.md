---
title: "Find/Replace Script"
date: 2006-05-04
forum: Programming Talk
---

### Post by musther on 2006-05-04
I need to find/create a script which will find and replace text in a specified file based on statements in a config file, for example:

The text file:
```
Hello world, this is a test
this is a test
this is a test
```

The config file:
```
'is'='was'
'test'='monkey'
```

The command:
```
script example.txt
```

The resulting text file:
```
Hell world, this was a monkey
this was a monkey
this was a monkey
```

The script should be able to match strings consisting of any ASCII characters (including spaces) and replace them with any other string.

Thanks for the help.

---

### Post by LordHunter317 on 2006-05-04
Any reason for this requirement?  As it stands, this can be accomplished with a series of sed one-liners:```
sed -i.bak -e 's/is/was' -e 's/test/monkey/' input 
```And it will generate backup.  It's easy enough to read the input and filter it, but is there a reason for it?

---

### Post by musther on 2006-05-04
I'm visually impaired, I use a device called the bookcourier ([www.bookcourier.com]("http://www.bookcourier.com")) for reading text.  Until recently the tool used to download text has been windows only, but a tool has now been developed for unix/linux/BSD.  The bookcourier has a text to speech engine which is.....  ....not perfect, the best way to make it correctly pronounce words is to search for the correct spelling of words with which it has difficulty and replace them with the phonetic spelling (or one the bookcourier can speak).  We would like to develop a script to do this from a dictionary-type-file, the script would be distributed with the transfer tool (UBT or Unix Book Transfer).

I hope this explains the need.

---

### Post by harisund on 2006-05-04
You might want to add a '/g' at the end of the substitution strings to make sure multiple occurances on the same line are replaced too.

---

### Post by IYY on 2006-05-04
Basically, do what LordHunter317 is saying but add some stuff to parse the config file. I can sketch a little script for reference, but I doubt it'll work just like that since it's late and I will not be testing it:

```
for x in `cat config.txt`
do
        f1=`echo $x | cut -d\' -f2`
        f2=`echo $x | cut -d\' -f4`
        sed -i -e s/$f1/$f2/g input.txt
done
```

Where the input file is input.txt and the config file is config.txt. Note that the result will not be as you expected but:

thwas was a monkey
thwas was a monkey

You never said it has to be a whole word ;)

Edit: hey, what do you know, it actually does work.

---

### Post by musther on 2006-05-05
Yes, it does work, but how do I correct for the fact that it doesn't care about whole words, I tried putting this in the config.txt, but it didn't work.

```
' is '=' was '
' test '=' monkey '
```

Of course that isn't actually good enough because it wouldn't change this:

This is a test it is!

And it'll also have to deal with capitals, so:

IS is Is and iS would all be changed to was.

---

### Post by harisund on 2006-05-05
Don't you agree that is the beauty of open source and programming? You start with something really simply, and before you know it, you get tons of idea, and tons of help, and you have an awesome application in front of you that is capable of doing far more than what the author had originally intended !

---

### Post by musther on 2006-05-06
Well yes, but in this case I'm no programmer, and I just need a simple script, I'd rather it wasn't all that complicated, but I can see how it could be, and how it could do great things.  The help is wonderful, and I really couldn't do this myself, I'm just hoping somebody can tackle the couple of things I said above.

I really do appreciate all the help I get, and for me possibly the greatest thing about open source is the community, both the community which creates it, and that which uses it, these ubuntu forums are a great example.

---

### Post by IYY on 2006-05-06
Here you go, I fixed it:

```
for x in `cat config`
do
        f1=`echo $x | cut -d\' -f2`
        f2=`echo $x | cut -d\' -f4`
        sed -i -e s/\\\<$f1\\\>/$f2/g input.txt
done
```

Now, to deal with capital letters ('This IS a TeSt' would be replaced by 'This was a monkey'):

```
for x in `cat config`
do
        f1=`echo $x | cut -d\' -f2`
        f2=`echo $x | cut -d\' -f4`
        sed -i -e s/\\\<$f1\\\>/$f2/gI input.txt
done
```

---

### Post by musther on 2006-05-06
Thanks so much, that works perfectly!.

I am, (of course) making an attempt to learn to write my own scripts; in a completely unrelated project I am trying to write a nautilus script.  I need to get the filename into a variable.

```
FILENAME="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```

This would store the full path such as '/home/musther/temp/image_54.png' in the variable $FILENAME.  How can I parse this so that I only end up with 'image_54.png' in the variable?

---

### Post by yaaarrrgg on 2006-05-06
have you tried:

```

basename "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

```

that will strip off the directory in bash.

---

### Post by musther on 2006-05-06
But I can't do:

```
FILENAME="basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```

If you do that you end up with 

basename the_string_from_the_nautilus_variable

in $FILENAME

---

### Post by yaaarrrgg on 2006-05-06
you might be able to use a $() or `` around a command like:

```

FILENAME=$( basename "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" )

```

which enables you to nest commands inside one another.  Also for bash scripts, you can do something like:
```

SET FILENAME=$( basename "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" )

```

---

### Post by llonesmiz on 2006-05-06
You could try this:

FILENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

---

### Post by musther on 2006-05-06
Thanks, the nested command approach worked, and that will be quite useful in other areas too.

Cheers

---

### Post by musther on 2006-05-06
Actually, one more question, why wont this work?

```
#!/bin/bash
#
cp $NAUTILUS_SCRIPT_SELECTED_URIS $HOME/.tmp/current.txt
```

I've tried this too:

```
#!/bin/bash
#
cp $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS $HOME/.tmp/current.txt
```

---

### Post by IYY on 2006-05-07
Does the .tmp directory exist?

---

### Post by musther on 2006-05-07
Yes it does.

I've tried it in a shell by doing this.

```
TEST="/home/musther/testing/test.txt"
cp "$TEST" $HOME/.tmp/current.txt
```

And that worked.

---

### Post by yaaarrrgg on 2006-05-07
It's possible those variables don't have the values you expect.  You might try spitting the line out as text rather than actualy executing.  "echo" will print the string:

```

#!/bin/bash
#
echo cp $NAUTILUS_SCRIPT_SELECTED_URIS $HOME/.tmp/current.txt

```

Also, you might want to use the flag "cp -f " in case the file already exists.  That will force it to overwrite.

---

### Post by musther on 2006-05-07
Thanks, I figured out what the problem was, file names with spaces!  This is how I solved it:

```
cp "$(echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)" $HOME/.tmp/current.txt
```

---

### Post by yaaarrrgg on 2006-05-07
in that case, this should work too (a little shorter):

```

cp "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" $HOME/.tmp/current.txt

```

double quotes should not affect the expansion of the variable.

---

### Post by musther on 2006-05-08
I expected that to work too, but it didn't, I'm not sure why.

---

