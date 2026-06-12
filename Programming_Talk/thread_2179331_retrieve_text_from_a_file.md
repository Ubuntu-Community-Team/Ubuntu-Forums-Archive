---
title: "retrieve text from a file"
date: 2013-10-07
forum: Programming Talk
---

### Post by aadil7 on 2013-10-07
Hello everyone

I am trying to read a certain line of text from a certain file and split the text at the delimiter ':'
i keep running into issues and cannot find a resolution!

```

#!/bin/bash
FILE=$1


result=$( grep "/$FILE" /home/storage.txt )
echo "$result"
STORELOCATION=/home/storage.txt


IFS=":" read -r left right << grep $FILE $RESTORELOCATION
echo "[$left][$right]"

```

with this i get the error read: /home/storage.txt: bad variable name

I have also tried

```

#!/bin/bash
FILE=$1


result=$( grep "/$FILE" /home/storage.txt )
echo "$result"


IFS=":" read -r left right << ( grep $FILE /home/storage.txt ) 
echo "[$left][$right]"

```

this returns syntax error "(" unexpected
when i remove the brackets I get an error saying redirection unexpected

how do i resolve this and achieve my desired result?
thanks in advance!

---

### Post by Karlchen on 2013-10-07
Hello, aadil7.

How about approaching the commandline and scripting systematically with the help of this documentation, [Introduction to the Command Line]("http://flossmanuals.net/command-line/"), instead of trying out things wildly? :wink:

Kind regards,
Karl

---

### Post by aadil7 on 2013-10-07
To be truthful ive tried being logical.. Ive used a few different methods & have also done research (im a newbie) and ive just had no luck! Ive spent loads of hours and just want a little guidance so i can be assured

---

### Post by steeldriver on 2013-10-07
I think you are confusing a couple of things - input redirection with **<** and process substitution using **<( command )** . Although when you combine them it looks superficially like a backwards version of the >> output redirection,  you can't mung the << together, they are separate syntactic units  and the second one belongs to the process substitution i.e.

```

$ IFS=":" read -r left right **< <(**echo "left stuff:right stuff"**)**
$ echo "$right"
right stuff

```

EDIT: you should also get in the habit of quoting string variables i.e.

```
IFS=":" read -r left right < <( grep [COLOR=#0000ff]**"**[/COLOR]$FILE[COLOR=#0000ff]**"**[/COLOR] /home/storage.txt )
```

and really you shouldn't use ALLCAPS for your own shell variables - they are (by convention) reserved for system variables

FINAL EDIT: also remember that grep may return more than one match - so depending what you are trying to do you should either add a -m1 switch or loop over the returned results.

---

### Post by aadil7 on 2013-10-08
> **steeldriver said:**
> I think you are confusing a couple of things - input redirection with **<** and process substitution using **<( command )** . Although when you combine them it looks superficially like a backwards version of the >> output redirection,  you can't mung the << together, they are separate syntactic units  and the second one belongs to the process substitution i.e.

```

$ IFS=":" read -r left right **< <(**echo "left stuff:right stuff"**)**
$ echo "$right"
right stuff

```

EDIT: you should also get in the habit of quoting string variables i.e.

```
IFS=":" read -r left right < <( grep [COLOR=#0000ff]**"**[/COLOR]$FILE[COLOR=#0000ff]**"**[/COLOR] /home/storage.txt )
```

and really you shouldn't use ALLCAPS for your own shell variables - they are (by convention) reserved for system variables

FINAL EDIT: also remember that grep may return more than one match - so depending what you are trying to do you should either add a -m1 switch or loop over the returned results.

I had already tested it like

```

IFS=":" read -r left right < <( grep "$FILE" /home/storage.txt ) 
echo "[$left][$right]"

```

but just like before I get a syntax error: redirection unexpected.. I understand your point on caps variable names.. Ill look to change that tonight my main priority is making progress with this as it has been bugging me for far too long!
regards

---

### Post by steeldriver on 2013-10-08
OK let me guess... you are running your script by doing sh ./myscript? That will force it to ignore the #!/bin/bash directive and run it in /bin/sh which won't work i.e.

```

$ IFS=":" read left right < <(echo "left stuff:right stuff")
$ echo $right
right stuff
$ 
$ sh
$ IFS=":" read left right < <(echo "left stuff:right stuff")
sh: 1: Syntax error: redirection unexpected

```

Try it again but just run the script as ./yourscript (no sh!)

---

### Post by aadil7 on 2013-10-08
> **steeldriver said:**
> OK let me guess... you are running your script by doing sh ./myscript? That will force it to ignore the #!/bin/bash directive and run it in /bin/sh which won't work i.e.

```

$ IFS=":" read left right < <(echo "left stuff:right stuff")
$ echo $right
right stuff
$ 
$ sh
$ IFS=":" read left right < <(echo "left stuff:right stuff")
sh: 1: Syntax error: redirection unexpected

```

Try it again but just run the script as ./yourscript (no sh!)

Ow alright.. I didnt know that.. I will try that as soon as i get home.
Thank you!

---

### Post by SeijiSensei on 2013-10-08
If you just want to split the line at ":", use awk:

```

result=$( grep "/$FILE" /home/storage.txt | awk -F: '{print $1}')
echo "$result"

```

That returns all the text up to the colon.  If you replace $1 with $2, it will print the text following the colon.  The default delimiter for awk is the space; -F: tells it to split on the colon instead.

---

