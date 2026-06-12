---
title: "Nautilus Actions Configuration and Bash Script Help"
date: 2011-09-17
forum: Programming Talk
---

### Post by Choonster on 2011-09-17
Note: This is the first time I've posted in these forums, so I wasn't entirely sure where to put this.

I'm having difficulties in writing a bash script to add to the right-click menu via Nautilus-Actions (NA). This script will extract the contents of each of the selected archives to its own folder in the current directory, just like WinRAR's "Extract to archive-name/" right-click command.

The only scripting/programming experience I have is writing Lua scripts for World of Warcraft AddOns, so Bash is new to me. Because of this, I thought I'd try and get the script working using **echo** commands before replacing those with the actual extracting commands.

I'm planning to have NA call the script with three arguments: the directory of the file, the file's base name without the extension and the file's mimetype (in that order).

Here's my current code:```
#!/bin/sh
#!/bin/bash

zip="application/zip"
rar="application/x-rar-compressed"
tar="application/x-tar"

echo $3

if "$3" == $zip
then
	echo "$1 $2 This is a Zip" #echo the directory ($1) and file name ($2) followed by "This is a Zip"
	exit $3

elif $3 == $rar
then
	echo "$1 $2 This is a RAR"
	exit $3

elif $3 == $tar
then
	echo "$1 $2 This is a tar"
	exit $3
else
	echo "Nope"
fi

exit 0
```

When I run this via the terminal like so (as if NAC ran it on a .zip archive named *file name* in the directory *path/to/file*):```
~/Documents/echotest.sh "path/to/file" "file name" "application/zip"
```(*~/Documents/echotest.sh* is the path to the script file)

Ideally, the following would appear in the terminal:```
application/zip
path/to/file filename This is a Zip
```

Instead, this appears:```
application/zip
/home/coon-pc/Documents/echotest.sh: 26: application/zip: not found
/home/coon-pc/Documents/echotest.sh: 26: application/zip: not found
/home/coon-pc/Documents/echotest.sh: 26: application/zip: not found
Nope
```

Basically, why is it throwing these errors and what can I do make it work? An explanation in fairly basic terms would be appreciated.

I've spent a bit of time on Google first looking for a pre-made solution and then looking for a way to make this script work, but couldn't find anything.

Thanks for any help.

---

### Post by Smart Viking on 2011-09-17
You have two shebangs, you can only have one.

remove "#!/bin/sh" and make sure "#!/bin/bash" is on the very first line.

There's no "application/zip", that is a problem.

---

### Post by Choonster on 2011-09-17
> **Smart Viking said:**
> You have two shebangs, you can only have one.

remove "#!/bin/sh" and make sure "#!/bin/bash" is on the very first line.
Thanks, didn't know that. Well after removing the *sh* shebang and running it from the terminal as before, it gave me the same errors but with a different line number for each one.

Here's the new code:```
#!/bin/bash

zip="application/zip"
rar="application/x-rar-compressed"
tar="application/x-tar"

echo $3

if "$3" == "$zip"
then
	echo "$1 $2 This is a Zip"
	exit $3

elif $3 == $rar
then
	echo "$1 $2 This is a RAR"
	exit $3

elif $3 == $tar
then
	echo "$1 $2 This is a tar"
	exit $3
else
	echo "Nope"
fi

exit 0
```

The terminal command:```
~/Documents/echotest.sh "path/to/file" "file name" "application/zip"
```

And the output:```
application/zip
/home/coon-pc/Documents/echotest.sh: line 9: application/zip: No such file or directory
/home/coon-pc/Documents/echotest.sh: line 14: application/zip: No such file or directory
/home/coon-pc/Documents/echotest.sh: line 19: application/zip: No such file or directory
Nope
```



> **Smart Viking said:**
> There's no "application/zip", that is a problem.So how would I tell it to check if the third argument ($3) is equal to the literal "application/zip" string rather than a file?

---

### Post by Smart Viking on 2011-09-17
I don't really know a lot of bash.

I made a python script, doing the same thing or something. I have no idea what the purpose of your program is.

```

#!/usr/bin/env python
import sys

zip = "application/zip"
rar = "application/x-rar-compressed"
tar = "application/x-tar"

directory = sys.argv[1]
filename = sys.argv[2]
whatever = sys.argv[3]

print whatever

if whatever == zip:
  print "%s %s This is a Zip" % (directory, filename)

elif whatever == rar:
  print "%s %s This is a RAR" % (directory, filename)

elif whatever == tar:
  print "%s %s This is a tar" % (directory, filename)

else: print "Nope"

```

---

### Post by Choonster on 2011-09-17
> **Smart Viking said:**
> I don't really know a lot of bash.

I made a python script, doing the same thing or something. I have no idea what the purpose of your program is.

```

#!/usr/bin/env python
import sys

zip = "application/zip"
rar = "application/x-rar-compressed"
tar = "application/x-tar"

directory = sys.argv[1]
filename = sys.argv[2]
whatever = sys.argv[3]

print whatever

if whatever == zip:
  print "%s %s This is a Zip" % (directory, filename)

elif whatever == rar:
  print "%s %s This is a RAR" % (directory, filename)

elif whatever == tar:
  print "%s %s This is a tar" % (directory, filename)

else: print "Nope"

```
That script works perfectly, but I don't know any Python so you've inspired me to use a Lua script instead of a bash one.

After a little hiccup with the working directory, I installed LuaFileSystem via LuaRocks. It then took me a while to figure out that I needed to actually "load" the LFS library with **require** (WoW AddOns don't have access to the **io** or **os** libraries and can't use **require**).

The text output works fine and I can create a new directory with the appropriate name, but **tar** seems to have trouble unzipping *.tar.bz2* archives with spaces in their names.

I'm also now calling the script with the complete file path as the first argument, with the directory, file name (without extension) and mimetype as the second, third and fourth arguments respectively.

Here's my code:```
#!/usr/bin/lua

require("lfs") --Load the LFS library

local completefilepath, filedirectory, filename, mimetype = ... --Grab the input from the command line and assign it to the appropriate variables

print(completefilepath, filedirectory, filename, mimetype) --Output the value of the variables (For debugging purposes)

lfs.chdir(filedirectory) --Change the working directory to the directory of the input file
lfs.mkdir(filename:gsub("%%20", " ")) --Make a new directory with the same name as the input file (without the extension), subsitute all occurences of %20 for an actual space
lfs.chdir(filename) --Change to the new directory

if mimetype == "application/zip" then
	print("It's a Zip!", filedirectory, filename)
	os.execute("unzip ".. completefilepath) --Execute "unzip path/to/file.zip" via the OS shell
elseif mimetype == "application/x-rar-compressed" then
	print("It's a RAR!", filedirectory, filename)
	os.execute("unrar x ".. completefilepath)
elseif mimetype == "application/x-compressed-tar" then
	print("It's a Tar!", filedirectory, filename)
	os.execute("tar zxvf ".. completefilepath)
elseif mimetype == "application/x-bzip-compressed-tar" then
	print("It's a Tar BZip!")
	os.execute("tar jxvf ".. completefilepath)
else
	print("Nope")
end
```

When I run this in the terminal:```
~/Documents/echotest.lua "/home/coon-pc/Documents/archtesttwo v200.tar.bz2" "/home/coon-pc/Documents/" "archtesttwo v200.tar" "application/x-bzip-compressed-tar"
```

I get this output:```
/home/coon-pc/Documents/archtesttwo v200.tar.bz2	/home/coon-pc/Documents/archtesttwo v200.tar	application/x-bzip-compressed-tar
It's a Tar BZip!
tar (child): /home/coon-pc/Documents/archtesttwo: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```

I'm not sure how to handle the spaces in the file name, putting the path in "double quotes" with **string.format** doesn't seem to make a difference.

Thanks for the help.

---

### Post by dethorpe on 2011-09-19
In your bash version you need this:
 
```
 
#!/bin/bash
zip="application/zip"
rar="application/x-rar-compressed"
tar="application/x-tar"
echo $3
if [[ "$3" == $zip ]]
then
        echo "$1 $2 This is a Zip" #echo the directory ($1) and file name ($2) followed by "This is a Zip"
        exit 1
elif [[ "$3" == $rar ]]
then
        echo "$1 $2 This is a RAR"
        exit 1
elif  [[ "$3" == $tar ]]
then
        echo "$1 $2 This is a tar"
        exit 1
else
        echo "Nope"
fi
exit 0
 

```
 
Note the brackets in the if statements, and the exit $3 replaced with exit 1, as exit takes a numeric return code as its argument.

---

### Post by Choonster on 2011-09-19
Thanks dethorpe, that's exactly what I needed.

Here's my new bash code:```
#!/bin/bash

# $1 == Complete file path
# $2 == File directory
# $3 == File name (without extension)
# $4 == Mimetype

if [[ "$4" == "application/zip" ]]
then
	echo "$1 $3 This is a Zip" #echo the directory ($1) and file name ($3) followed by "This is a Zip"
	mkdir "$2/$3"
	cd "$2/$3"
	unzip "$1"
	exit 1
elif [[ "$4" == "application/x-rar-compressed" ]]
then
	echo "$1 $3 This is a RAR"
	mkdir "$2/$3"
	cd "$2/$3"
	unrar x "$1"
	exit 1
elif  [[ "$4" == "application/x-compressed-tar" ]]
then
	echo "$1 $3 This is a tar"
	mkdir "$2/$3"
	tar zxvf "$1" -C "$2/$3"
	exit 1
elif [[ "$4" == "application/x-bzip-compressed-tar" ]]
then
	echo "This is a tar BZip"
	mkdir "$2/$3"
	echo "$2/$3"
	tar jxvf "$1" -C "$2/$3"
	exit 1
else
		echo "Nope"
fi
exit 0
```

Unfortunately it still doesn't work properly.

When I run the script on a file with no spaces in the name, it works perfectly. When I run the script on a file with spaces in the name via the terminal, it also works perfectly. The problem arises when I try to run the script on a file with spaces in the name via the right-click menu (via Nautilus-Actions).

When run via right click on a zip or RAR with spaces, it creates the directory but then doesn't extract anything.

When run via right click on a tarball (bzip2 or gzip) with spaces, it creates the directory but then extracts the files to the same directory as the archive rather than the newly created one.

---

### Post by Vaphell on 2011-09-19
what did you put in command/parameters fields in nautilus actions? investigate what exactly is passed from NA to your script, if spaces are not escaped script sees n separate parameters and the whole thing falls apart.

---

### Post by Choonster on 2011-09-19
> **Vaphell said:**
> what did you put in command/parameters fields in nautilus actions? investigate what exactly is passed from NA to your script, if spaces are not escaped script sees n separate parameters and the whole thing falls apart.
In the Command section, the Path field is this:```
/home/coon-pc/Documents/echotest.lua
```

The Parameters field is this:```
"%f" %d %w %m
```

The Working directory field is empty.

Putting %d and %w in quotes doesn't work.

---

### Post by Vaphell on 2011-09-19
i did a test
parameters: %%d %d %%m %m %%w %w %%f %f **"%f"**
and redirected the output of a script that prints out all its parameters to a file
$ cat na.output 
%d
/home/me
%m
hm mh.txt
%w
%f
hm mh.txt
**'hm mh.txt'**

NA seems to add single quotes to the string when you use "" around the %symbol.
I think you need to drop the quotes, NA will pass a proper value (my bet is that it does single quoting internally already, when you additionally doublequote it, you make single quotes it added to secure whitespaces a part of the string)

---

### Post by Choonster on 2011-09-19
> **Vaphell said:**
> i did a test
parameters: %%d %d %%m %m %%w %w %%f %f **"%f"**
and redirected the output of a script that prints out all its parameters to a file
$ cat na.output 
%d
/home/me
%m
hm mh.txt
%w
%f
hm mh.txt
**'hm mh.txt'**

NA seems to add single quotes to the string when you use "" around the %symbol.
I think you need to drop the quotes, NA will pass a proper value (my bet is that it does single quoting internally already, when you additionally doublequote it, you make single quotes it added to secure whitespaces a part of the string)
Taking out the quotes around %f doesn't work. It makes the directory but doesn't extract any archive.

---

### Post by Vaphell on 2011-09-19
```
#!/bin/bash

fdir=${1%/*}                  # directory
fname=${1##*/}                # archive name
fname=${fname%%.*}            # archive name (no extension)
exdir=${1%%.*}                # destination
mime=$( file -ib "$1" )
mime=${mime/;*/}              # mimetype

echo File: "$1"
echo Mimetype: "$mime"
#echo \""$fdir"\"  \""$fname"\" \""$exdir"\" \"$mime\"

if [[ "$mime" == "application/zip" ]]
then
  echo "This is a Zip file"
  unzip "$1" -d "$exdir"
elif [[ "$mime" == "application/x-rar" ]]
then
  echo "This is a Rar file"
  unrar x -ad "$1" "$fdir"
elif [[ "$mime" == "application/x-bzip2" ]]
then
  echo "This is a Tar.Bz2 file"
  mkdir "$exdir" && tar jxvf "$1" -C "$exdir"
else
  echo "I don't know what to do with this file, sorry"
fi
exit 0

```

everything is derived from $1 alone (full file path)
builtin bash functions to strip various parts of the path to get dir, filename, etc, file command to get mime info. I tested 3 cases and all work for me.

---

### Post by Choonster on 2011-09-19
Thanks Vaphell, I realised I was calling the Lua script instead of the Bash one and changed the path to [FONT="Courier New"]/home/coon-pc/Documents/echotest.sh[/FONT] and the parameters to [FONT="Courier New"]%f[/FONT], but it still doesn't quite work

Your script seems to work perfectly on all files when run via the terminal, but doesn't seem to work at all via right click.

I have no idea what's going wrong.

---

### Post by Vaphell on 2011-09-20
my version works with %M (space separated list of full paths though NA entry is set up to work only for single selection), %f is name alone, without the path

```
$ ls ./*
./num a.rar  ./test1.ZIP  ./test 1.zip  ./test 333.tar.bz2

./num a:
num.exe

./test1:
test.txt

./test 1:
test.txt

./test 333:
test.txt
```

all subdirs in this test directory where created with NA in rightclick menu

---

### Post by sisco311 on 2011-09-20
$@ expands to the positional parameters. So "$@" expands to "$1" "$2" ... and so on. If memory serves, in a nautilus script $1 $2 ... are the full path to the selected files. So I would try something like:
```
#!/bin/bash

shopt -s nullglob
for file in "$@"
do
    mime="$(file -b --mime-type "$file")"
    case "$mime" in
        application/zip)
            do something
            ;;
        application/rar)
            do something else
            ;;
         *)
            whatever
            ;;
    esac
done

```

---

### Post by dethorpe on 2011-09-20
Could try to redirect output of script to a log file to see what the parameters are and what happens when you call it via NA. 
 
Might show if the params are not as you expect and if any of the commands are failing.
 
e.g:
 
```
 
...
echo $1,$2,$3,$4 >> na.log
...
if 
 ..
else
        echo "Nope"
fi >> na.log 2>&1
 

```

---

### Post by Choonster on 2011-09-21
Sisco311, I *think* that Nautilus scripts are slightly different to Nautilus Actions scripts. NA scripts are called with the parameters you specify, and these are accessible via $1, $2, etc. This particular script only uses one parameter, so $2 onwards aren't defined.

Vaphell, NA's legend says that %F is the list of full file paths and %M is the list of mimetypes. I'm using [font="Courier New"]%F[/font] as the single parameter. Calling the script on an archive with no spaces in the name works perfectly, but I'm still having trouble with the ones that do have spaces.

Using dethorpe's logging idea, I called the script on a file with no spaces and then a file with spaces.

Here's my current code:```
#!/bin/bash

fdir=${1%/*}		# directory
fname=${1##*/}		# archive name
fname=${fname%%.*}	# archive name (no extension)
exdir=${1%%.*}		# destination
mime=$( file -ib "$1" )
mime=${mime/;*/}	# mimetype

echo "-----------------New File----------------" >> na.log

echo File: "$1" >> na.log
echo Mimetype: "$mime" >> na.log
#echo \""$fdir"\"	\""$fname"\" \""$exdir"\" \""$mime"\" 

if [[ "$mime" == "application/zip" ]]
then
	echo "This is a Zip file"
	unzip "$1" -d "$exdir"
elif [[ "$mime" == "application/x-rar" ]]
then
	echo "This is a Rar file"
	unrar x -ad "$1" "$fdir"
elif [[ "$mime" == "application/x-gzip" ]]
then
	echo "This is a Tar.gz file"
	mkdir "$exdir" && tar zxvf "$1" -C "$exdir"
elif [[ "$mime" == "application/x-bzip2" ]]
then
	echo "This is a Tar.Bz2 file"
	mkdir "$exdir" && tar jxvf "$1" -C "$exdir"
else
	echo "I don't know what to do with this file, sorry"
fi >> na.log 2>&1
exit 0
```

Here's the log for the one without spaces:```
-----------------New File----------------
File: /home/coon-pc/Documents/archtesttwov21.tar.gz
Mimetype: application/x-gzip
This is a Tar.gz file
archtesttwo/new file
archtesttwo/folder/
archtesttwo/a/
archtesttwo/
```

And the same file with a space added:```
-----------------New File----------------
File: /home/coon-pc/Documents/archtesttwo%20v21.tar.gz
Mimetype: ERROR: cannot open `/home/coon-pc/Documents/archtesttwo%20v21.tar.gz' (No such file or directory)
I don't know what to do with this file, sorry
```

It looks like the spaces are getting "escaped" to [font="Courier New"]%20[/font] but the [font="Courier New"]**file**[/font] command is interpreting them literally.

Thanks for the input everyone, this is tougher than I thought it would be.

---

### Post by Vaphell on 2011-09-21
wtf? o.O
i suspect something has changed in NA and its symbols. In fact i was somewhat dumbfounded earlier with your mimetype parameter as i couldn't find it anywhere in my version.

my NA help window says as follows
%d - dir of the first elem
%f - name of the first elem
%h - hostname of first URI
%m - space-separated list of names
%M - space-separated list of full paths
%p - port number of first URI
%R - space-separated list of URIs
%s - scheme of first URI
%u - first URI
%U - username of first URI

afaik URIs escape characters with %xx notation so your NA probably works with them

create a sample script that will redirect every parameter passed from NA to a file and in NA in parameters put all the symbols you can find in the legend, with/without quotes. Look at output to see if any of them preserves spaces.
if for example dir and name are ok, just glue them together of pass as separate params and tweak the script.

---

### Post by Choonster on 2011-09-21
Vaphell, I'm using NA version 3.0.5. All of the parameters seem to escape spaces. Is there any way to replace every occurrence of %20 with an actual space? It's easily done in Lua, but I don't know very much about Bash.

---

### Post by Choonster on 2011-09-21
I've now got a Lua script that seems to work flawlessly on all four types of archives I'm interested in (Zip, RAR, Tar GZip and Tar BZip2).

It's basically a Lua port of Vaphell's Bash script.

Here's the code (it may not be the cleanest solution, but it gets the job done):```
#!/usr/bin/lua

--os.execute("echo \"--------------New File (Lua)--------------\" >> na.log")

--[[local oldprint = print
print = function(...)
	local str = ""
	for i = 1, select("#", ...) do
		str = str .." ".. select(i, ...)
	end
	os.execute("echo \"".. str .."\" >> na.log")
	oldprint(str)
end]]

local filepath = ... --Grab the input from the command line and assign it to the appropriate variables
filepath = filepath:gsub("%%20", " ") -- Replace escaped spaces with actual ones

print("Path:", filepath)

local filedir, filename = filepath:match("^(.+)/(.+)%..+$")
if filename:sub(-4) == ".tar" then --Remove .tar from the end of the name.
	filename = filename:sub(1, -5)
end
local exdir = (filedir or "") .."/".. (filename or "")
local mime = io.popen("file -ib \"".. filepath .."\""):read()
mime = mime:match("(.+);.+")

print("Directory:", filedir)
print("Name", filename)
print("Exdir", exdir)
print("Mime", mime)


if mime == "application/zip" then
	print("This is a Zip file")
	os.execute("unzip \"".. filepath .."\" -d \"".. exdir .. "\"")
elseif  mime == "application/x-rar" then
	print("This is a Rar file")
	os.execute("unrar x -ad \"".. filepath .."\" \"" .. filedir .."\"")
elseif  mime == "application/x-gzip" then
	print("This is a Tar.gz file")
	os.execute("mkdir \"".. exdir .."\" && tar zxvf \"".. filepath .."\" -C \"".. exdir .."\"")
elseif  mime == "application/x-bzip2"  then
	print("This is a Tar.Bz2 file")
	os.execute("mkdir \"".. exdir .."\" && tar jxvf \"".. filepath .."\" -C \"".. exdir .."\"")
else
	print("I don't know what to do with this file, sorry.")
end
```

I'm calling it with [font="Courier New"]%f[/font] as the parameter. [font="Courier New"]%f[/font] is the single complete file path. Using the singular forces it to run on every file selected rather than run only once. It could (probably) easily be modified to run only once and just iterate over all of the files, but it works as-is.

Thank you all very much for your help.

---

### Post by Vaphell on 2011-09-21
just in case you ever needed to replace %20 with space in bash :)

```
$ echo "$orig"
some%20space%20separated%20stuff
$ echo "${orig//%20/ }"
some space separated stuff
$ echo $orig | sed 's/%20/ /g'
some space separated stuff
```

---

