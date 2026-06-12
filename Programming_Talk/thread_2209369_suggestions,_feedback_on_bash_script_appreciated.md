---
title: "suggestions, feedback on bash script appreciated"
date: 2014-03-05
forum: Programming Talk
---

### Post by J_Me on 2014-03-05
Just pieced together a bash script, all it does is strips down the eye candy from a web page and saves the results(a play list) to a .txt file. The script was made up from lots of searches and editing what I found to fit my needs. It's the second script I sort of made up from scratch without following a tutorial so suggestions on feedback, books or exercises would really be appreciated. 
```
#!/bin/sh

# a shell script used to download a specific song list.

# appends variable to the url address.
echo -n "What's the album? "
read var1
b='http://www.foobar/foo/'
c=$b$var1
# confirm address
echo "So you want? $c"

# removes any / within the variable and replaces it with a +
x=$(echo $var1|sed 's/[/]/+/g')
d=_file.txt
e=$x$d

DIR=/home/me/here

# wget output file only temp.
FILE=temp_text.txt

# wget log file, usful info but not needed
LOGFILE=logFileText.log

# web address
URL=$c

cd $DIR
wget $URL -O $FILE -o $LOGFILE

# this sorts the usful bits out from the temp_text.txt file and saves the results to a new file
sed -ne 's/.*album=""><span itemprop="name">\([^<]*\)<.*/\1/p' temp_text.txt > $e

# remove the temp_text.txt file, not needed anymore
rm /home/me/here/temp_text.txt


```

---

### Post by Vaphell on 2014-03-05
1. Switch to bash for convenience features (da)sh doesn't have
2. move configuration bits to the top so everything is in 1 highly visible place, you shouldn't be looking for definitions of your constants like log files 1 page down
3. always quote your variables, especially outside assignments, naked variables are sensitive to whitespace issues for no gain at all
4. don't use all uppercase names for variables because you risk overriding some env variable (all caps by convention). Override PATH for your personal use and see how your script suddenly stops working because it can't find any commands.
5. you can skip the temp file by using
```
wget "$url" -O- | sed ...
```

bash is powerful enough to perform many string transformations on its own, without the overhead of spawning external commands
```
x=$(echo $var1|sed 's/[/]/+/g')
x=${var1//\//+} # parameter expansion in bash
```
[http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)


consider using [http://www.shellcheck.net/](http://www.shellcheck.net/)

---

### Post by J_Me on 2014-03-06
Thanks for the reply, I've tried to rearrange things following your instructions, hope it's clearer. However I didn't write 'wget "$url" -O- | sed ...' into this script just yet, I managed to get it working with the results I needed but it had errors. I'll keep working on it.
```
#!/bin/bash
# a shell script used to download a specific song list.
dir=/home/me/here # the working directory
cd $dir
file=temp_text.txt # wget output file only temp.
logfile=log_file.log # wget log file, usful info but not needed

# appends variable to the url address.
echo -n "What's the album?"
read 'var1'
b='http://www.foobar/foo/'
c=$b$var1
echo "So you want? $c" # confirms address

url=$c # complete web address
wget $url -O $file -o $logfile

x=${var1//\//+} # replaces any '/' with a '+'
d=_file.txt
e=$x$d

# this sorts the useful bits out from the webpage and saves the results to a new file
sed -ne 's/.*album=""><span itemprop="name">\([^<]*\)<.*/\1/p' temp_text.txt > $e

rm /home/me/here/temp_text.txt # remove the temp_text.txt file, not needed anymore


```
Thanks again

---

### Post by Vaphell on 2014-03-06
much better, though i'd drop that cd [COLOR="#0000FF"]"[/COLOR]$dir[COLOR="#0000FF"]"[/COLOR] few lines down to where the script actually begins doing stuff, **with quotes**. Seriously, if you don't know subtle nuances of shell behavior, 'always quote variables' is a good rule of thumb that will save your skin in the long run.

Btw, that cd is somewhat superficial, you can put $dir in all your file definitions if you define them anyway, eg
```
dir=$HOME/here # the working directory

file="$dir/temp_text.txt" # wget output file only temp.
logfile="$dir/log_file.log" # wget log file, usful info but not needed
...
e="$dir/${var1//\//+}_file.txt"
```
this removes the need of navigating by hand.


you have few rather useless variables, eg why have $c if you can name it url right off the bat? Or that e=$x$d, it can be easily compressed to e=${var1//\//+}_file.txt without intermediaries and 2 additional lines.
The names of these variables could use some work too, they are completely uninformative - var1 a b c don't tell you anything of value, their purpose or whatever. Give names some meaning so you don't have to reverse engineer your own script few months down the road.
why not ```
urlbase="http://foo.bar/baz"
url=$urlbase/$album
```
?

echo+read can be replaced by read with prompt
```
echo -n "What's the album?"
read 'var1'

read -p "What's the album? " var1
```

oh, and at the end you don't use $file but hardcoded temp_text.txt

---

