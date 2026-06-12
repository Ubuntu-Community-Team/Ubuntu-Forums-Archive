---
title: "Create directory with spaces in name using BASH script"
date: 2012-04-21
forum: Programming Talk
---

### Post by nathan.the.sane on 2012-04-21
I'm trying to write a BASH script to rip a cd using cdparanoia, convert it to mp3 using LAME, and then move all the songs into my music directory. However, I've run into a small but immensely frustrating problem which is that I can't seem to create a directory with spaces in the name, for example "~/music/David Bowie - Station to Station". ](*,)

Here is what I have right now:
```
 
echo -n "Enter artist name: "
read -e ARTIST

echo -n "Enter album name: "
read -e ALBUM

DIRECTORY_NAME="\"${ARTIST} - ${ALBUM}\""

mkdir -v ~/tmp/$DIRECTORY_NAME
```I've also tried using read without the -e option, but either way what happens is the shell tries to create separate "David", "Bowie", "-", etc. directories.

The frustrating part is that if I open up an xterm and type mkdir ~/tmp/"David Bowie - Station to Station" I get what I want, but apparently executing that same string from a script doesn't work. :confused:

---

### Post by Habitual on 2012-04-21
```
mkdir -v ~/tmp/"$DIRECTORY_NAME"
```song="Station to Station"
```
artist="David Bowie"
song="Station to Station"
mkdir "$artist $song"

ls -ld David\ Bowie\ Station\ to\ Station/
```or as SeijiSensei suggests quotes
```
"/tmp/$DIRECTORY_NAME"
```I believe either method will work, but one might be more zen than the other. :)

---

### Post by SeijiSensei on 2012-04-21
That's because you enclosed the directory name in quotes when you ran the command from the command line.  Do the same thing in your script:

```
mkdir -v "/tmp/$DIRECTORY_NAME"
```

Make sure to use double quotes; single quotes will treat $DIRECTORY_NAME as a literal and not replace it with its contents.

---

### Post by nathan.the.sane on 2012-04-21
Thanks guys! :popcorn:

It works now (yes!), but out of curiosity (a dangerous thing, I know :p ) my $DIRECTORY_NAME variable did have double quotes around the name, so I'm still confused about why my original approach didn't work.

If it's value was (literally) "David Bowie - Station to Station" (and it was, that's what got output when I did just 'echo $DIRECTORY_NAME') , then I assumed that in my script ~/tmp/$DIRECTORY_NAME would expand to ~/tmp/"David Bowie - Station to Station". It only has quotes around the last part, but as I noted apparently that was enough for it to work when I typed it into the terminal manually, but in the script it created a directory named "David. Why the difference?

---

### Post by SeijiSensei on 2012-04-21
Placing the quotes in the string assigned to an environment variable doesn't matter to bash which doesn't actually look at the contents of the variable at all.  What matters is whether the string that contains the variable(s) is enclosed in quotes since that's what the parser will act upon.

---

