---
title: "variables in bash scripts - I'm confused"
date: 2013-04-18
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-04-18
:confused:Hi Guys,

I am *attempting* to learn a bit about writing bash scripts.
The test folder I'm using has 20 files named 1.jpg 2.JPG 3.jpg 4.JPG etc.

I was thinking that I'd like to have a script check if any files with the .JPG extension are in a folder and then tell me yes there are or no there are not.

If I run:

```

#!/bin/bash
imagejpg=.JPG
if $imagejpg; then
echo "Files Exist" 
fi

```

I get:
```
line 6: .JPG: command not found

```

If I change the script adding ".JPG" (adding the quotes)
I get the same result.

If I change to imagejpg="*.JPG"
I get :
```
line 6: 10.JPG: command not found
```

I would really appreciate it if someone could tell me what I am doing wrong.

---

### Post by schragge on 2013-04-18
```

imagejpg=.JPG
for file in *$imagejpg
do
  if [[ -f $file ]]
  then
    echo Files exist
    break
  fi
done

```
See [Introduction to if]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html"), [The for loop]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html"), and [File name expansion]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html#sect_03_04_08")

Alternatively, you can do it like this
```

imagejpg=.JPG
stat -c '' *$imagejpg &>/dev/null && echo Files exist

```

See [stat(1)](http://manpages.ubuntu.com/manpages/quantal/en/man1/stat.1.html), [redirection](http://tldp.org/LDP/abs/html/special-chars.html#REDIROUTERROR), and [List Constructs](http://tldp.org/LDP/abs/html/list-cons.html#LISTCONSREF)

---

### Post by GrouchyGaijin on 2013-04-18
Thank you!
I'll check those links.
You make it look so easy, pretty cool.

---

### Post by GrouchyGaijin on 2013-04-18
I'm back to bug the forum again.

OK

The eventual goal is that when the script is run:
The user will see that the script is looking for a specific type of image file.
The user will be told if that file type exists or not.
If the file type exists the user will be told that all files of that type are being resized.

I have this which is incorrect:

```
imagejpg=.jpgread -p "Press the [Enter] key to search for jpegs..."
for file in *$imagejpg
do
  if [[ -f $file ]]
  then
    echo We have jpgs
**[COLOR=#ff0000]else[/COLOR]**
**[COLOR=#ff0000]echo No jpegs[/COLOR]**
fi


if [[ -f $file ]]
then
echo "Resizing jpgs"
break
 fi


for file in *$imagejpg


do gm mogrify -resize 720x720 *.jpg


break
done 
```

This is the output in the terminal when I run the script:
```

Press the [Enter] key to search for jpegs...
/home/john/scripts/test11: line 44: syntax error: unexpected end of file



```

There is no mention that the directory I'm in has [COLOR=#ff0000]no[/COLOR] jpg files.

What am I doing wrong?
I really appreciate the help!!

---

### Post by schragge on 2013-04-18
Why not just
```
gm mogrify -verbose -resize 720x720 *.jpg
```:?:

---

### Post by cortman on 2013-04-18
> **schragge said:**
> Why not just
```
gm mogrify -verbose -resize 720x720 *.jpg
```:?:

Well, this, really. No need for anything else.

> **GrouchyGaijin said:**
> I'm back to bug the forum again.

OK

The eventual goal is that when the script is run:
The user will see that the script is looking for a specific type of image file.
The user will be told if that file type exists or not.
If the file type exists the user will be told that all files of that type are being resized.

I have this which is incorrect:

```
imagejpg=.jpgread -p "Press the [Enter] key to search for jpegs..."
for file in *$imagejpg
do
  if [[ -f $file ]]
  then
    echo We have jpgs
**[COLOR=#ff0000]else[/COLOR]**
**[COLOR=#ff0000]echo No jpegs[/COLOR]**
fi


if [[ -f $file ]]
then
echo "Resizing jpgs"
break
 fi


for file in *$imagejpg


do gm mogrify -resize 720x720 *.jpg


break
done 
```

This is the output in the terminal when I run the script:
```

Press the [Enter] key to search for jpegs...
/home/john/scripts/test11: line 44: syntax error: unexpected end of file



```

There is no mention that the directory I'm in has [COLOR=#ff0000]no[/COLOR] jpg files.

What am I doing wrong?
I really appreciate the help!!

First, your script is full of syntax errors- read the [Bash Beginner's Guide]("http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html") closely- check out each section that deals with a command you use.
As far as how to go about doing this, here's perhaps an improved way (although I'm a scripting beginner myself- someone can feel free to critique this method):

```

echo "Pres Enter to search for JPEGS"
read start
pics=$(find -maxdepth 1 -regex ".*\.jpe?g" -printf "%f\n")
if [ $pics ] ; then
   echo "Pics found!"
   echo "Resizing..."
   for i in $pics ; do
        gm mogrify -resize 720x720 $i
   done
else
    echo "No pics"
fi

```

---

### Post by GrouchyGaijin on 2013-04-18
Thank you for the reply.  I'll read the guide.
I tried the code you wrote:
```
[COLOR=#000000][FONT=Ubuntu Mono]echo "Pres Enter to search for JPEGS"[/FONT][/COLOR]
read startpics=$(find -maxdepth 1 -regex ".*\.jpe?g" -printf "%f\n")if [ $pics ] ; then   echo "Pics found!"   echo "Resizing..."   for i in $pics ; do       do gm mogrify -resize 720x720 $i   doneelse    echo "No pics" [COLOR=#000000][FONT=Ubuntu Mono]fi[/FONT][/COLOR]
```
and got this:
```
line 10: syntax error near unexpected token 
`do' line 10: `       do gm mogrify -resize 720x720 $i'



```

---

### Post by cortman on 2013-04-18
The guide is good; I reference it all the time myself.
The problem with the gm mogrify command is that I copy/pasted your line, and I already had a "do" in my for loop, so just delete the "do" and it should work. My mistake!

---

### Post by GrouchyGaijin on 2013-04-18
and it does - how cool is that!
What is the ? in [COLOR=#000000][FONT=Ubuntu Mono]".*\.jpe?g" for?
How would I change it for images with the extension .JPG or .png?[/FONT][/COLOR]

---

### Post by steeldriver on 2013-04-18
IMO you shouldn't use
```
if [ $pics ]
```

or

```
for i in $pics
```

Both will break if your search finds any filenames with spaces e.g.

```

$ ls *.jpg
[COLOR=#ff0000]** 978-1-234 5678-9.jpg**[/COLOR]  978123456789.jpg
$ pics=$(find . -maxdepth 1 -name '*.jpg' -printf "%f\n")
$ if [ $pics ] ; then echo 'Pics found!'; fi
[COLOR=#ff0000]**-bash: [: 978-1-234: binary operator expected**[/COLOR]
$
$ for pic in $pics; do echo $pic; done
978123456789.jpg
[COLOR=#ff0000][B]978-1-234
5678-9.jpg[/B][/COLOR]

```

A more bullet proof way to do this kind of loop-over-find-results is along the lines of (fill in whatever you want to 'do' instead of echo)

```
$ while read -rd $'\0' pic; do echo "$pic"; done < <(find . -maxdepth 1 -name '*.jpg' -print0)
```

You don't really need to test if there are any matches but if you really must then it's better to (a) quote the variable (make it a habit - ALWAYS!) and (b) test to see if the string is non-empty

```

$ if [ -n "$pics" ] ; then echo 'Pics found!'; fi
Pics found!
$

```

---

### Post by cortman on 2013-04-18
> **steeldriver said:**
> IMO you shouldn't use


You just beat me to that realization. :) Something was nagging in my mind when I re-read that script, so I checked out Greg's wiki. You're absolutely right; here's how I've modified it now- how does this look?

```

#!/bin/bash                                                                     

shopt -s extglob

echo "Press Enter to search for JPEGS"
read start
for i in *.jp?(e)g ; do
    if [ -e "$i" ] ; then
        echo "Pics found."
        echo "Resizing..."
        gm mogrify -resize 720x720 $i
    else
        echo "No pics found."
    fi
done



```

Thanks for pointing that out.

---

### Post by schragge on 2013-04-18
Quote this, too:
```
gm mogrify -resize 720x720 [COLOR=#ff0000]"[/COLOR]$i[COLOR=#ff0000]"[/COLOR]
```
Also note that the code will print "Pics found" for each found JPEG file, so maybe
```

unset found
shopt -s extglob nullglob
for i in *.jp?(e)g; do
  if [[ -f $i ]]; then   
    [[ -v found ]] || echo Pics found.
    : ${found:-set}
    echo Resizing $i
    gm mogrify -resize 720x720 "$i"
  else
    echo Skipping $i: not a regular file
  fi
done
[[ -v found ]] || echo No pics found.

```

---

### Post by GrouchyGaijin on 2013-04-18
WOW - you guys are stars.

What is the ? in ".*\.jpe?g" for?
How would I change it for images with the extension .JPG or .png?

---

### Post by schragge on 2013-04-18
> **GrouchyGaijin said:**
> What is the ? in ".*\.jpe?g" for? [Regular expression](http://manpages.ubuntu.com/manpages/quantal/en/man7/regex.7.html). Similar to [extended pattern matching]("http://ww.gnu.org/software/bash/manual/html_node/Pattern-Matching.html"). It matches either .jpg or .jpeg
> **GrouchyGaijin said:**
> How would I change it for images with the extension .JPG or .png?```
*.@(jp?(e)g|JPG|png)
```

---

### Post by cortman on 2013-04-18
> **GrouchyGaijin said:**
> WOW - you guys are stars.

What is the ? in ".*\.jpe?g" for?
How would I change it for images with the extension .JPG or .png?

The ?(e) is extended globbing, like a regex.

> **schragge said:**
> Quote this, too:
```
gm mogrify -resize 720x720 [COLOR=#ff0000]"[/COLOR]$i[COLOR=#ff0000]"[/COLOR]
```
Also note that the code will print "Pics found" for each found JPEG file, so maybe
```

unset found
shopt -s extglob nullglob
for i in *.jp?(e)g; do
  if [[ -f $i ]]; then   
    [[ -v found ]] || echo Pics found.
    : ${found:-set}
    echo Resizing $i
    gm mogrify -resize 720x720 "$i"
  else
    echo Skipping $i: not a regular file
  fi
done
[[ -v found ]] || echo No pics found.

```

What's the -v option mean? I don't think that's a test operator.
Your addition basically says that if the variable found is unset, echo Pics found, if the variable is set, then don't echo it?

---

### Post by ofnuts on 2013-04-18
> **GrouchyGaijin said:**
> and it does - how cool is that!
What is the ? in [COLOR=#000000][FONT=Ubuntu Mono]".*\.jpe?g" for?
How would I change it for images with the extension .JPG or .png?[/FONT][/COLOR]
1)I don't know because I think that should have been jp?(e)g (to match both "jpg" and "jpeg")

2) replace 
```
for i in *.jp?(e)g;
```
```

shopt -s nullglob
for i in *.jpg *.jpeg *.JPG *.png *.PNG

```

'nullglob' tells the shell to return an empty string for patterns that don't match anything, instead of the pattern itself, so you won't get messages about no file called "*.PNG", for instance.

---

### Post by schragge on 2013-04-18
> **cortman said:**
> What's the -v option mean? Tests if a variable is set. It's bash-specific, see [here]("http://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html").
> **cortman said:**
> Your addition basically says that if the variable found is unset, echo Pics found, if the variable is set, then don't echo it?The variable 'found' is a flag. If it's unset then print 'Pics found' and set it. If it's still unset after the loop ended then print 'No pics found'.

---

### Post by cortman on 2013-04-18
> **schragge said:**
> Tests if a variable is set. It's bash-specific, see [here]("http://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html").
The variable 'found' is a flag. If it's unset then print 'Pics found' and set it. If it's still unset after the loop ended then print 'No pics found'.

Interesting. Thanks for the pointers.

---

### Post by GrouchyGaijin on 2013-04-18
First, thank you guys!
I don't know how in the world you remember, let alone understand all of this.

I *almost* have what I wanted.

There are two things that I'd like to ask about.
When I use this code:
```
#!/bin/bash                                                                     

shopt -s extglob


echo "Press Enter to search for images"
read start
shopt -s nullglob
for i in *.jpg *.jpeg *.JPG *.png *.PNG *GIF *gif; do
    if [ -e "$i" ] ; then
        echo "Pics found."
        echo "Resizing..."
        gm mogrify -resize 720x720 $i
        mv $i ~/Pictures
    else
        echo "No pics found."
    fi
done

```
1. Spaces in the file name do break the script.  How should I fix that?
2. The  else echo "No pics found." doesn't show up.

Again,  I _really_ appreciate the help.

---

### Post by schragge on 2013-04-18
> **GrouchyGaijin said:**
> 1. Spaces in the file name do break the script.  How should I fix that?Quote it: ```
gm mogrify -resize 720x720 [COLOR=#ff0000]"[/COLOR]$i[COLOR=red]"[/COLOR]
```
> **GrouchyGaijin said:**
> 2. The  else echo "No pics found." doesn't show up. You are using *shopt -s nullglob*, so if there's no pics, the loop won't get executed at all. See [post=12608910]my solution above[/post].

---

### Post by GrouchyGaijin on 2013-04-18
> **schragge said:**
> Quote it: ```
gm mogrify -resize 720x720 [COLOR=#ff0000]"[/COLOR]$i[COLOR=red]"[/COLOR]
```
 You are using *shopt -s nullglob*, so if there's no pics, the loop won't get executed at all. See [post=12608910]my solution above[/post].

I can't thank you enough!
I'm marking this as solved and will continue reading the guide.

---

### Post by GrouchyGaijin on 2013-04-20
Hey Guys,

I thought you might like to see the final script:

```
#!/bin/bash 
echo "Unload_camera version 3: This script will remove images and videos from your camera."
echo "Basic script by GrouchyGaijin. [COLOR=#ff0000]**Heavy lifting by schragge. Additional modifications by cortman, steeldriver, and ofnuts**[/COLOR]"
echo "Run this script from the camera"  
now=$(date +"%d-%b-%Y-%T")
mkdir /path/to/where/you want/the/pictures/put/$now 
echo "Making directory to hold the photos."


dir="/path/to/clips/directory"
read -p "Press Enter to check if the clips directory is empty"
if [ "$(ls -A $dir)" ]; then
     echo "Clips is not empty. Did you forget to empty it last time?"
fi 
echo "If files were found type yes to empty the directory"
read x
if [ "$x" = "yes" ]
then
rm -f "$dir"/* 
else
echo "OK, Leaving the directory as is."
fi 
                 
pics_dir="/path/to/$now"
clips_dir="/path/to/clips"


process_image() {
  echo Resizing "$1"
  gm mogrify -resize 720x720 "$1"
  echo Moving "$1" to $pics_dir
  mv "$1" "$pics_dir"
}
process_video() {
  echo Moving "$1" to $clips_dir
  mv "$1" "$clips_dir"
}


process_thumbnail() {
  echo Removing "$1" from the camera
  rm "$1"
}


unload() {
  case $1 in
    image) pattern='*.jpg *.JPG *.png *.PNG *.GIF *.gif';;
    video) pattern='*.MOV *.mov *.mpg *.MPG *.mpeg *.mp4';;
    thumbnail) pattern='*.THM';;
    *) echo Unknown file type, aborting...; exit 1;;
  esac
  echo Press Enter to search for $1 files; read start


  unset found
  for i in $pattern; do
    if [[ -f $i ]]; then
      [[ -v found ]] || echo ${1^}s found.
      : ${found:-set}
      process_$1 "$i"
    else
      echo Skipping $i: not a regular file
    fi
  done
  [[ -v found ]] || echo No or no additional ${1}s found.
}
shopt -s nullglob
unload image
unload video
unload thumbnail
```

---

