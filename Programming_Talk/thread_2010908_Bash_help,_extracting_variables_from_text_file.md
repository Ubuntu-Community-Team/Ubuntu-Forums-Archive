---
title: "Bash help, extracting variables from text file"
date: 2012-06-26
forum: Programming Talk
---

### Post by CaptainMark on 2012-06-26
This is probably simple for most here but I'm still learning so please be patient.

I have a script that I've been practising on for a while, which stores some basic settings just in a text file and my script will read the variables from the text to remember them from last time, here it is currently:
```

if [ -e $targets ]; then
    read source destination < $targets
else .....

```
The variable $targets contains the location of the text file so this part takes the first two words from the text file and assigns them as the variables $source and $destination (which are also file paths) my problem is that I want to change it so its the first two lines that get assigned to variables not the first two words, so if the $source and $destination can contain spaces.

I thought this would work
```

if [ -e $targets ]; then
	IFS=$'\n'
	read source destination < $targets
	unset IFS
	fi

```the first variable comes out as expected the complete first line of the text file including spaces, however the second variable does not read the second line but comes out blank.

Could someone help me realise my mistake and point out what I'm missing so I can correct my script,
Thanks
Mark

---

### Post by TheFu on 2012-06-26
I think you are making this harder than it needs to be.  If I understand correctly, that is.

Suppose you have 2 files - 
a) shell script - called "prg"
b) settings - called "settings"

Inside "settings" file:```

source=/some/path/to/a/file/or/directory
target=/some/other/path
```Back inside the "prg" file: 
```
if [ -f "settings" ] ; then
   source "settings"
fi 
```This will set the environment variables for the "settings" file and make them available to the "prg" when running.

Almost anything we could want to accomplish is well explained with examples in the "Advanced Bash Scripting Guide" - [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)   Here's a link for a multi-line read example: [http://tldp.org/LDP/abs/html/internal.html#READR](http://tldp.org/LDP/abs/html/internal.html#READR)

I'm pretty certain there is a way to read specific settings from a file 1 at a time, if you like, but I wouldn't do it the way you are attempting. These are not Windows ini files, after all.  I'd do it by using grep to get the specific line out that I wanted - it would need to be a fairly complex regex to handle comments (#) properly and dump anything after the value.  My initial solution lets the bash interpreter handle that issue for us.

---

### Post by sisco311 on 2012-06-27
+1 for TheFu's idea. 

Save the filenames in a file:
```

cat << EOF > files
source="$source"
dest="$dest"
EOF
```

Then simply source it in your script:
```
. files
```

Otherwise you need two read commands:
```

{
    read -r source
    read -r dest
} < filename

```

But file names may contain newlines in which case your script will fail. You have to use the null character to separate the filenames:
```

printf '%s\0' "$source" "$dest" > files
```

```

{
    IFS= read -r -d '' source
    IFS= read -r -d '' dest
} < files
```

---

### Post by CaptainMark on 2012-06-30
thanks very much, ill study these ideas. i dont have to worry but these variables containing new lines but its about learning so ill be taking this on board, thanks

---

