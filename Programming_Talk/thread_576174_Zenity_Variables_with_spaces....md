---
title: "Zenity: Variables with spaces..."
date: 2007-10-14
forum: Programming Talk
---

### Post by ryanVickers on 2007-10-14
I have been doing some scripting, and come to the conclusion that zenity is incapable of storing a string with spaces in it.

take the following previews as an example:

#1: Simple BASH
```

variable="hello world!"
echo $variable

```
it would echo 'hello world'

now,
```

variable=$(zenity --entry --text "Please enter some text" --entry-text "Hello world!")
echo $variable

```
variable will now equal 'hello'

Any ideas to a solution? (not using underscores - I need this for something else where they will definitly *not* work! ;))

---

### Post by ryanVickers on 2007-10-14
wait, my previews are working, but the script is not... :mad:

---

### Post by ryanVickers on 2007-10-14
I think I've solved it!

If you set the value with a variable, ex:

```

#!/bin/bash
var="Hello World"
variable=$(zenity --entry --text "Please enter some text" --entry-text $var)
echo $variable

```
it returns "hello"

but if you do it like in the first post, with literal quotes (""), then it returns Hello World! :p

---

### Post by cwaldbieser on 2007-10-15
This has to do with how the shell is interpreting your command.  If you don't quote it, the shell sees:
```

variable=$(zenity --entry --text "Please enter some text" --entry-text Hello World)

```
It looks like the --entry-text option has "Hello" as its argument, and "World" is just some extra garbage on the command line.  

I'm not exactly sure why zenity doesn't flag the extra argument as an error or at least a warning.

The "echo" example you give is fine, because echo takes all its arguments, concatentes them with the first IFS field separator, and outputs them.

---

### Post by goodrench on 2008-01-14
I am trying to write a script using zenity and I want to use --file-selection.
If I select a file with spaces in the name it will only see the text before the spaces.


```
input=`zenity --text="Name of file to convert" --file-selection`

```

should I follow this with

```
echo $input
```


???

---

### Post by geirha on 2008-01-16
Just make sure you quote ("") the variable whenever you use it:
```
some-command "$input"
# instead of
some-command $input
```

---

### Post by goodrench on 2008-01-16
I tried the 


```

command "$input"
 
```

but it didn't work.
I think the problem is with the zenity input.
When the command is trying to run it gives an error saying that the file cannot be found.
The file it is refering to only shows the file name until the first space.

I am trying to write a script that other people can use.
For my own use I don't mind renaming the file but 
it would be easier if spaces weren't an issue.

```

Failed to open /media/hdb3/07-08-27.
Cannot open file/device.

```

---

### Post by geirha on 2008-01-16
Could you paste the line where you try to use the $input?

---

### Post by goodrench on 2008-01-16
this is what I am trying to do.


```
mencoder -of mpeg -mpegopts format=dvd:vbitrate=9000 -o tmp/movie.dvd -oac copy -ovc copy "$input" |  zenity --progress --pulsate --title="Creating temp files" --auto-close 

```

---

### Post by geirha on 2008-01-16
Well, that looks correct. If you run "echo $input" on a line before that mencoder-line, does it print the whole file-name or just up to the first space?

You could try quoting the zenity command above too: ```
input=**"**`zenity --text="Name of file to convert" --file-selection`**"**
``` though the original should work ...

---

### Post by goodrench on 2008-01-16
> **geirha said:**
> Well, that looks correct. If you run "echo $input" on a line before that mencoder-line, does it print the whole file-name or just up to the first space?


yes it does echo the entire file name including spaces.

---

### Post by geirha on 2008-01-17
> **goodrench said:**
> yes it does echo the entire file name including spaces.

That's odd. I copy/pasted that line and tried it myself. Worked fine for me with a filename with spaces... I have no idea why it doesn't work for you ...

For reference, here's my little test-script:
```
#!/bin/bash
input=`zenity --file-selection --text="foo"`
echo $input
mencoder -of mpeg -mpegopts format=dvd:vbitrate=9000 -o tmp/movie.dvd -oac copy -ovc copy "$input" |  zenity --progress --pulsate --title="Creating temp files" --auto-close
```

---

### Post by goodrench on 2008-01-17
Ok I will give you everything I've got.
This is driving me nuts.

Here is the script that I am working with.

```

#! /bin/sh

#make temp directory

mkdir -p tmp/vob &&

input=`zenity --file-selection --text="Name of file to convert"` 

echo "$input"

output=`zenity --entry --width 500 --text="What would you like to name the iso file - no extension, no spaces"`

#convert from .ts to dvd compliant stream


mencoder -of mpeg -mpegopts format=dvd:vbitrate=9000 -o tmp/movie.dvd -oac copy -ovc copy $input |  zenity --progress --pulsate --title="Creating temp files" --auto-close &&

#create dvd structure - uncomment (#) the appropriate line to create 5 minute chapters or 10 minute chapters.

#dvdauthor -o tmp/vob -t --chapters="0:00:00,0:10:00,0:20:00,0:30:00,0:40:00,0:50:00,1:00:00,1:10:00,1:20:00,1:30:00,1:40:00,1:50:00,2:00:00,2:10:00,2:20:00,2:30:00,2:40:00,2:50:00,3:00:00,3:10:00,3:20:00,3:30:00,3:40:00,3:50:00,4:00:00" tmp/movie.dvd &&
dvdauthor -o tmp/vob -t --chapters="0:00:00,0:05:00,0:10:00,0:15:00,0:20:00,0:25:00,0:30:00,0:35:00,0:40:00,0:45:00,0:50:00,0:55:00,1:00:00,1:00:00,1:05:00,1:10:00,1:15:00,1:20:00,1:25:00,1:30:00,1:35:00,1:40:00,1:45:00,1:50:00,1:55:00,2:00:00,2:00:00,2:05:00,2:10:00,2:15:00,2:20:00,2:25:00,2:30:00,2:35:00,2:40:00,2:45:00,2:50:00,2:55:00,3:00:00,3:00:00,3:05:00,3:10:00,3:15:00,3:20:00,3:25:00,3:30:00,3:35:00,3:40:00,3:45:00,3:50:00,3:55:00,4:00:00" tmp/movie.dvd | zenity --progress --pulsate --title="Creating DVD" --auto-close &&

dvdauthor -T -o tmp/vob/ | zenity --progress --pulsate --title="Creating dvd structure" --auto-close &&

#create iso file

mkisofs -dvd-video -udf -o $output.iso tmp/vob | zenity --progress --pulsate --title="Making iso file" --auto-close &&

rm -rf tmp/ | zenity --progress --pulsate --title="Removing temp files" --auto-close


```




And this is my what I get when run from the terminal.

```

drew@laptop:/media/data/dvd$ ./ts2iso2.sh 
/media/data/dvd/0301 HBO2 East - the sopranos _ college - 23_12_05.ts
File not found: '/media/data/dvd/0301'
Failed to open /media/data/dvd/0301.
Cannot open file/device.
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing tmp/test...
ERR:  Error opening tmp/test: No such file or directory
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating table of contents
ERR:  No .IFO files to process
Setting input-charset to 'UTF-8' from locale.
mkisofs: No such file or directory. Failed to open 'tmp/vob//VIDEO_TS/VIDEO_TS.IFO'.
mkisofs: Can't open VMG info for 'tmp/vob/'.
mkisofs: Unable to parse DVD-Video structures.
mkisofs: Could not find correct 'VIDEO_TS' directory.
mkisofs: Unable to make a DVD-Video image.
drew@laptop:/media/data/dvd$ 

```

---

### Post by DoktorSeven on 2008-01-17
> mencoder -of mpeg -mpegopts format=dvd:vbitrate=9000 -o tmp/movie.dvd -oac copy -ovc copy $input |  zenity --progress --pulsate --title="Creating temp files" --auto-close &&

Need **"$input"** (with quotes around it) in there, as noted above.

> mkisofs -dvd-video -udf -o $output.iso tmp/vob | zenity --progress --pulsate --title="Making iso file" --auto-close &&

Also needs quotes: **"$output.iso"**

> 
#! /bin/sh

Remove the space between ! and /, and I'd also make that /bin/bash; sh is linked to dash (a bash clone) by default and I've had weird issues with running scripts with dash.

---

### Post by goodrench on 2008-01-17
Thank you geirha and doktorseven.
Problem solved.
I can't thank you enough.
This is exactly what I needed.

Is there any links you can give me to learn more about scripting?

Thanks for the help.

---

### Post by geirha on 2008-01-18
[http://tldp.org/guides.html](http://tldp.org/guides.html) First guide there, Advanced bash scripting guide is very handy to have around when scripting. It's got lots of examples. Though you might skim through the beginner's guide further down first :)

---

### Post by goodrench on 2008-01-18
great link geirha.
lots of great stuff on that site to read as well as links to other sites.
That should keep me busy for a while.

Thanks again.

---

### Post by balistardrake on 2010-11-26
I know this thread is quite old, but I was also having some problems with my zenity script. My script is as follows:


```
var=False "John Doe" "JD"

Course=$(zenity --list --text "Please Make a Selection" --radiolist --column "Choice" --column "Name" --column "Code" $var)
```

This is giving me a weird looking list because of the space in "John Doe." I can't do "$var" because then the whole like will be put into the first column of the list and I don't want that. Does anyone have any suggestions?

---

### Post by geirha on 2010-11-26
Use an array instead.

```

arr=( False "John Doe" JD 
      False "Jane Doe" JD2
)
course=$(zenity --list --text "Please Make a Selection" --radiolist --column "Choice" --column "Name" --column "Code" "${arr[@]}")

```

Trying to put syntactical quotes into a string will always fail. This explains why: [http://mywiki.wooledge.org/BashFAQ/050](http://mywiki.wooledge.org/BashFAQ/050)

Also, I've learned a lot more about bash since last I commented in this thread and I now recommend to **NOT** read the bash guides at [http://tldp.org/guides.html](http://tldp.org/guides.html). The only good guide out there (that I know of) is [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide).

---

### Post by balistardrake on 2010-11-26
> **geirha said:**
> Use an array instead.

```

arr=( False "John Doe" JD 
      False "Jane Doe" JD2
)
course=$(zenity --list --text "Please Make a Selection" --radiolist --column "Choice" --column "Name" --column "Code" "${arr[@]}")

```

Trying to put syntactical quotes into a string will always fail. This explains why: [http://mywiki.wooledge.org/BashFAQ/050](http://mywiki.wooledge.org/BashFAQ/050)

Also, I've learned a lot more about bash since last I commented in this thread and I now recommend to **NOT** read the bash guides at [http://tldp.org/guides.html](http://tldp.org/guides.html). The only good guide out there (that I know of) is [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide).

Wow. Thanks so much for the quick reply. You bash source also helped a lot. I wasn't able to fix my problem using your solution because the contents of arr were actually an output of a command. I found the solution on the site you suggested though. Thanks again

---

