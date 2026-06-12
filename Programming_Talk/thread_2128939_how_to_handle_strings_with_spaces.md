---
title: "how to handle strings with spaces"
date: 2013-03-24
forum: Programming Talk
---

### Post by AmbiguousOutlier on 2013-03-24
Hello, I'm attempting my first script. I'm trying to do a loop that picks up all text files in a directory including all it's subdirectories. However whenever there is a space in the one of the directories the "for in" statement treats this as two separate file names. Is there any way of treating them the same?

```
for i in $(find . -name *.txt); do #i think I need to put quotes around something??
	echo $i
done
```


alternatively I was thinking I could 

```
count=$(find . -name *.txt | wc -l);
for i = 1 to $count; do
	echo find . -name *.txt | wc -l #obviously I need to somehow only select one at a time
done
```

Any thoughts?

---

### Post by steeldriver on 2013-03-24
Try

```

for i in **[COLOR=#0000ff]"[/COLOR]**$(find . -name **[COLOR=#0000ff]'[/COLOR]***.txt**[COLOR=#0000ff]'[/COLOR]**)**[COLOR=#0000ff]"[/COLOR]**; do 
    echo **[COLOR=#0000ff]"[/COLOR]**$i**[COLOR=#0000ff]"[/COLOR]**
done
```

or maybe better 

```

while read -r -d $'\0' i; do 
    echo "$i"; 
done < <(find . -name '*.txt' -print0)
```

---

### Post by LeDieu on 2013-03-24
You can do the same without the find command:
```

#!/bin/bash

for file in *.txt
do
        echo $file
done

```

Hope this is what you where looking for.

---

### Post by schragge on 2013-03-24
> **LeDieu said:**
> You can do the same without the find command: Nope. > **RhysGM said:**
> I'm trying to do a loop that picks up all text files in a directory [COLOR=red]including all it's subdirectories[/COLOR]. In bash, you can make shell glob recurse through subdirectories, see [post=12572394]the next post[/post] by **steeldriver** below.

Still, the *while* loop with *read* suggested by **steeldriver** is the most general solution. Quoting the *find* output inside *for* loop's *in* list won't work as it will turn the whole output of *find* into one argument. If the loop body only consists of one command then using *find*'s action *-exec* may also be a viable alternative:
```
find -name \*.txt -exec [COLOR=#0000ff]command[/COLOR] {} \;
``` And even if there are more than one command, sometimes *-exec* may be convenient:
```
find -name \*.txt -exec sh -c '[COLOR=#0000ff]command1[/COLOR] "$0"; [COLOR=#0000ff]command2[/COLOR] "$0"' {} \;
```

---

### Post by steeldriver on 2013-03-24
... LeDieu's approach might work for subdirs if you enable the bash 'globstar' option

> **LeDieu said:**
> You can do the same without the find command:
```

#!/bin/bash

[COLOR=#0000ff]shopt -s globstar
shopt -s nullglob
[/COLOR]
for file in [COLOR=#0000ff]****/**[/COLOR]*.txt
do
        echo [COLOR=#0000ff]**"**[/COLOR]$file[COLOR=#0000ff]**"**[/COLOR]
done

```

Hope this is what you where looking for.

but the 'while loop' is how I'd do it, I think

---

### Post by AmbiguousOutlier on 2013-03-25
I could potentially be handling hundreds of files so if I understand the -exec command, this wouldn't work. 

However I can't get the while loop working. 

> **steeldriver said:**
> Try
```

while read -r -d $'\0' i; do 
    echo "$i"; 
done < <(find . -name '*.txt' -print0)
```

The above produces a redirection error.


```

while read -r -d $'\0' i; do 
    echo "$i"; 
done < $(find . -name '*.txt' -print0)
```

This still concatenates the filenames together. And looks like it's trying to execute the file. 

I don't really understand what the above is doing so if I simplify it down, I get the below which still doesn't work;

```
while read i; do 
	echo $i; 
done < $(find . -name '*.jpg')
```

```
rhys@Orange:~/Documents/Scripts$ ./exists
./exists: 3: ./exists: cannot open ./flac_music/Evanescence/folder.jpg
./flac_music/Evanescence/fanart.jpg
./flac_music/Evanescence/Fallen/folder.jpg: No such file
```

But it got me thinking, I could output the result of the find into a text file and then read the text file in one by one. 

```
find . -name '*.jpg' -print > ./file.txt

while read i
do           
	echo $i           
	echo "file processed"
done <file.txt
```

This has also given me the idea of producing a log file. What fun lies ahead. :) 

I'm still interested to know what I'm doing wrong on the loops though.

---

### Post by Vaphell on 2013-03-25
I could potentially be handling hundreds of files so if I understand the -exec command, this wouldn't work.

depends how you are going to be processing these files. -exec simply executes the command with found name(s) pasted in. It might be unwieldy due to syntax, but not inherently impossible to do pretty much anything. That said, i do these in simple cases and go while read route for anything remotely complicated.


What do you run your script with? Your hashbang line should point to bash because some of mentioned tricks are bash features.
```
#!/bin/sh
```
vs
```
#!/bin/**bash**
```?

test in terminal
```
$ sh    #switching to sh
$ while read f; do echo "$f"; done < <( find ) 
sh: Syntax error: redirection unexpected
$ bash # back to bash
$ while read f; do echo "$f"; done < <( find )
<plenty of paths>
```

Check if you can work with builtin globs, rock solid out of the bat. If you are forced to use *find*, in case of *while read ; do... ; done < <(cmd)* try to use \0 as often as possible. It's the only char that allows for unambiguous, rock solid solution for file processing.

builtin globs > while read -d $'\0' > lazy hacks

**tl; dr:** stick to #!/bin/bash and \0 as delimiter

---

### Post by AmbiguousOutlier on 2013-03-25
Yeah, I was using sh not bash. I've got it working now so I'll stick with it, what I've got works with both bash and sh. I guess that line means something. ;) 

I'm stuck again though, I have a file called;

/original/folder/subfolder/file.txt

I don't want to copy the file, but I do want to mirror the folder structure like below;

/mirror/folder/subfolder/

I then want to do some processing and move the new file to the new location keeping the original in tact. 

I've used the sed command to substitute the directory however I need to chop off just the file name, so I can easily mkdir the string. But I'm not sure what to google. 

Normally I would find the position of the last "/" then substring to this position. But google keeps falling back to sed. Any other commands I could use?

---

### Post by AmbiguousOutlier on 2013-03-25
```
#!/bin/bash

mypath=/mirror/folder/subfolder/file.txt

mkdir -p $(dirname "$mypath")
```
works :)


```
#!/bin/bash

mypath=/mirror/folder/sub folder/file.txt

mkdir -p $(dirname "$mypath")
```
doesn't work :(

It's these spaces in my file names, I'm struggling to handle them correctly.

---

### Post by schragge on 2013-03-25
Quote file names with spaces:
```

#!/bin/sh
file='[COLOR=#000000][FONT=Ubuntu Mono]/original/folder/sub folder/file.txt[/FONT][/COLOR]'
path=${file%/*}
newpath=/mirror/${path#/*/}
mkdir -p "$newpath"
cp "$file" "$newpath"

```
There are many ways to copy/move whole folders: rsync, cp -a, cpio, tar. See [post=12510349]this post[/post]. It's about moving /home, but techniques described there are aplicable to copying/moving arbitrary directory subtrees.

---

### Post by Vaphell on 2013-03-25
> Yeah, I was using sh not bash. I've got it working now so I'll stick with it, what I've got works with both bash and sh. I guess that line means something.

why would you want to use sh for your own userspace scripts? Do you have a computer from the 20th century that shaving off that 100k of RAM matters? Bash offers tons of nifty stuff that is not accessible in sh (dash)
You are gimping yourself for no reason. If you have cool features within your arms reach, use them, don't reinvent the wheel with hackish workarounds for the sake of it. These features were in fact implemented to alleviate many of such basic problems like this one.

bash **<( cmd )** that means 'capture the cmd output and make a  fake file of it' is incredibly powerful, it works everywhere you would use files as input. *some_command file*? have *some_command <( cmd ) *instead. You don't pollute your hdd with temporary dump files and can cut to the chase.

---

### Post by AmbiguousOutlier on 2013-03-25
> **schragge said:**
> Quote file names with spaces:
```

#!/bin/sh
file='[COLOR=#000000][FONT=Ubuntu Mono]/original/folder/sub folder/file.txt[/FONT][/COLOR]'
path="${file%/*}"
newpath="${path#/*/}"
mkdir -p "$newpath"
cp "$file" "$newpath"

```

> **Vaphell said:**
> why would you want to use sh for your own userspace scripts? Do you have a computer from the 20th century that shaving off that 100k of RAM matters? Bash offers tons of nifty stuff that is not accessible in sh (dash)
You are gimping yourself for no reason. If you have cool features within your arms reach, use them, don't reinvent the wheel with hackish workarounds for the sake of it. These features were in fact implemented to alleviate many of such basic problems like this one.

I finally got my script working, but yes I'm using work arounds. Like creating text files and replacing spaces with underscore. Ok, I'll make it better, I know it's the best way to learn. :)

EDIT: I think I know what I'm doing, so wanted to mark the thread as solved. Can anyone tell me how??

---

### Post by nothingspecial on 2013-03-25
Read this these
 [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

