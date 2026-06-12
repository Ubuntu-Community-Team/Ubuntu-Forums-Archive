---
title: "would this be hard to program in bash?"
date: 2009-02-11
forum: Programming Talk
---

### Post by jakupl on 2009-02-11
I have quite a deal of subscriptions on Youtube. It is often pretty clever to download the Youtube clips right away, just in case. I am using a CLI program called youtube-dl for this.

I have one directory for each of my subscriptions in /home/jakup/Videos
like /home/jakup/Videos/fakesagan

Would it be possible (I am really bad at this) to make a script called - say youtube, where I write "youtube" In terminal and it does this.



1. First asks which youtuber the video is from, we can call this $user, and it uses this to determine which directory to put it in, If the user does not match any directory than make a new one (preferably not case sensitive).

2. ask which day of the month the video was uploaded to youtube = $dd

3. ask which month the video was uploaded to youtube = $mm

4. ask which year the video was uploaded to youtube = $yy

5. ask for the name of the video = $vidname

6. ask for the youtube url of the video = $url

Then executes the following command:

```
youtube-dl -o /home/jakup/Videos/$user/$dd$mm$yy$vidname $url
```


So if fakesagan would upload a video today "12 feb 2009" called "hello", I would go to terminal and enter "youtube", and there i would enter:

fakesagan
12
02
09
hello
[http://www.youtube.com/watch?v=FXc_¤%&/(/&%¤&/()(/&%¤%&/(](http://www.youtube.com/watch?v=FXc_¤%&/(/&%¤&/()(/&%¤%&/()

and it would execute the following command
```
youtube-dl -o /home/jakup/Videos/fakesagan/120209hello http://www.youtube.com/watch?v=FXc_¤%&/(/&%¤&/()(/&%¤%&/(
```

and the video would appear in /home/jakup/Videos/fakesagan/120209hello


If you are really bored and feel like doing something, you are more then welcome :)

---

### Post by ghostdog74 on 2009-02-11
for asking user for input, you can use read.

---

### Post by Tek-E on 2009-02-12
A simple shell script could be used to do this....  Like ghostdog74 said. you get input using the read command. If you want Ill right the script for you.  It would be no more than a few lines to do what your asking.

---

### Post by jimi_hendrix on 2009-02-12
this is what bash was bourne for!

*ducks*

but seriously...use bash for this

---

### Post by ghostdog74 on 2009-02-12
> **Tek-E said:**
> . If you want Ill right the script for you.  It would be no more than a few lines to do what your asking.
i could have write it out myself, but i prefer him to try himself. pls hold your urge for a while longer until he encounter genuine problems.

---

### Post by jespdj on 2009-02-12
> **jimi_hendrix said:**
> this is what bash was bourne for!
This is what bash was Bourne Again for! ;)

---

### Post by jakupl on 2009-02-12
> **ghostdog74 said:**
> i could have write it out myself, but i prefer him to try himself. pls hold your urge for a while longer until he encounter genuine problems.

:) yes I like that. Later today, I will spew out some weird code... hopefully :popcorn:

---

### Post by jakupl on 2009-02-12
This is what I've managed to do... don't laugh ;) :

```
#!/bin/bash


echo -n "Name of channel 'name': "
read name
echo "name = $name"

echo -n "Name of video 'video': "
read video
echo "video = $video"

echo -n "url 'url': "
read url
echo "url = $url"


echo

echo -n "Enter the date dd mm yy 'dd', 'mm' and yy "
echo =n "(separated by a space or tab): "
read dd mm yy
echo "dd = $dd      mm = $mm	yy = $yy"

mkdir /home/jakup/Desktop/$name
youtube-dl -o /jakup/Desktop/$name/$dd$mm$yy$video $url


exit 0
```

The only thing that does not work is the youtube-dl part.

---

### Post by ghostdog74 on 2009-02-12
try using curly braces for your variables
```

${dd}${month} 

```

---

### Post by jakupl on 2009-02-12
> **ghostdog74 said:**
> try using curly braces for your variables
```

${dd}${month} 

```

yeah I changed dd to ddd because dd is a program

NAME
       dd - convert and copy a file
but okay I will try.

---

### Post by jakupl on 2009-02-12
Like this? 
```

#!/bin/bash


echo -n "Name of channel 'name': "
read name
echo "name = ${name}"

echo -n "Name of video 'video': "
read video
echo "video = ${video}"

echo -n "url 'url': "
read url
echo "url = ${url}"


echo

echo -n "Enter the date dd mm yy 'ddd', 'mm' and yy "
echo =n "(separated by a space or tab): "
read ddd mm yy
echo "ddd = ${ddd}      mm = ${mm}	yy = ${yy}"

mkdir /home/jakup/Desktop/${name}
youtube-dl -o /jakup/Desktop/${name}/${ddd}${mm}${yy}${video} ${url}


exit 0

```

the mkdir works, but immediately exits, and the youtube-dl is never executed.

---

### Post by jakupl on 2009-02-12
And another thing. The ${name} usually has spaces, so it needs to handle spaces.

---

### Post by ghostdog74 on 2009-02-12
then use double quotes around your variables. this is part of the basics pls read the bash link in my sig for more.

---

### Post by jakupl on 2009-02-12
> **ghostdog74 said:**
> then use double quotes around your variables. this is part of the basics pls read the bash link in my sig for more.

Yes I tested it with the mkdir command and it works now.
But the actual script does not get to the youtube-dl execution.

```
#!/bin/bash


echo -n "Name of channel 'name': "
read name
echo "name = ${name}"

echo -n "Name of video 'video': "
read video
echo "video = ${video}"

echo -n "url 'url': "
read url
echo "url = ${url}"


echo

echo -n "Enter the date dd mm yy 'ddd', 'mm' and yy "
echo =n "(separated by a space or tab): "
read ddd mm yy
echo "ddd = ${ddd}      mm = ${mm}	yy = ${yy}"

mkdir /home/jakup/Desktop/${name}
youtube-dl -o /jakup/Desktop/${name}/${ddd}${mm}${yy}"${video}" ${url}


exit 0
```

EDIT: it kinda starts the youtube-dl but then just exits

---

### Post by geirha on 2009-02-12
If ${name} may contain spaces, put it in quotes as well. Just put that whole argument inside one set of double quotes.

Btw, read can also print a prompt. ```
read -p "Type something: " var
```
Should make it a little bit shorter and neater.

---

### Post by jakupl on 2009-02-12
But why does it not finish the youtube-dl command?

---

### Post by geirha on 2009-02-12
> **jakupl said:**
> But why does it not finish the youtube-dl command?

Never used youtube-dl, but I'm guessing it just fails when you give it an invalid url...

---

### Post by jakupl on 2009-02-12
> **geirha said:**
> Never used youtube-dl, but I'm guessing it just fails when you give it an invalid url...

so you are saying that youtube-dl probably can't manage variables?

---

### Post by geirha on 2009-02-12
The commands have no knowledge about variables; bash handles those. Let's take an example. Let's say the variables contain this:
```

name="Some Channel"
ddd=12
mm=02
yy=09
video="Cool stuff"
url="http://youtube.com/some/url/we/pretend/is/valid"

```

Now what happens when bash comes to the youtube-dl line is that it first replaces all variables with their values
```

youtube-dl -o /jakup/Desktop/${name}/${ddd}${mm}${yy}"${video}" ${url}
# becomes
youtube-dl -o /jakup/Desktop/Some Channel/120209Cool\ Stuff http://youtube.com/some/url/we/pretend/is/valid
```
The command is called with 4 arguments (you wanted to give it 3):
Argument 1: -o
Argument 2: /jakup/Desktop/Some
Argument 3: Channel/120209Cool\ Stuff
Argument 4: [http://youtube.com/some/url/we/pretend/is/valid](http://youtube.com/some/url/we/pretend/is/valid)

I'm guessing it fails to download the url: "Channel/120209Cool Stuff" to "/jakup/Desktop/Some"

The space in the $name is not inside quotes, so it will be treated as an argument delimiter. In general, if a variable contains a path, always quote it with ""

---

### Post by jakupl on 2009-02-12
No I have put it all in double quotes. this is how it looks now.

```
#!/bin/bash


echo -n "Name of channel 'name': "
read name
echo "name = ${name}"

echo -n "Name of video 'video': "
read video
echo "video = ${video}"

echo -n "url 'url': "
read url
echo "url = ${url}"


echo

echo -n "Enter the date dd mm yy 'ddd', 'mm' and yy "
echo =n "(separated by a space or tab): "
read ddd mm yy
echo "ddd = ${ddd}      mm = ${mm}	yy = ${yy}"

mkdir /home/jakup/Desktop/${name}
youtube-dl -o "/jakup/Desktop/${name}/${ddd}${mm}${yy}${video}" ${url}


exit 0
```

But it does not work.

ps. the youtube names never contain spaces.

---

### Post by phrostbyte on 2009-02-13
You might want to change youtube-dl to "echo" to see what is being passed to the command exactly.

---

### Post by jakupl on 2009-02-13
Okay... guys it works now. I was just an idiot. in the last directory path I actually wrote /jakup/Desktop/... and forgot /home

well it works flawlessly. yey


this is the final code:

```
#!/bin/bash


echo -n "Name of channel 'name': "
read name
echo "name = ${name}"

echo -n "Name of video 'video': "
read video
echo "video = ${video}"

echo -n "url 'url': "
read url
echo "url = ${url}"


echo

echo -n "Enter the date dd mm yy 'ddd', 'mm' and yy "
echo =n "(separated by a space or tab): "
read ddd mm yy
echo "ddd = ${ddd}      mm = ${mm}	yy = ${yy}"

mkdir /home/jakup/Desktop/${name}
youtube-dl -o "/home/jakup/Desktop/${name}/${ddd}${mm}${yy}${video}" ${url}


exit 0
```

---

### Post by phrostbyte on 2009-02-13
If you want to make it a little smaller you can replace this

echo -n "url 'url': "
read url
echo "url = ${url}"

with this

read url -p "url 'url': "
echo "url = ${url}"

:)

---

### Post by jakupl on 2009-02-14
> **phrostbyte said:**
> If you want to make it a little smaller you can replace this

echo -n "url 'url': "
read url
echo "url = ${url}"

with this

read url -p "url 'url': "
echo "url = ${url}"

:)

Yeah :) I will. Thank you very much, I will do that.

---

