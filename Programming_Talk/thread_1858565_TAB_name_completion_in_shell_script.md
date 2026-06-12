---
title: "TAB name completion in shell script"
date: 2011-10-12
forum: Programming Talk
---

### Post by Ranko Kohime on 2011-10-12
I'm writing a shell script with a menu for my commonly used commands, and I've run into two snags on how to handle a particular setup, and my Google-fu hasn't dredged up anything useful.

The first snag is that the script is always started from $HOME, but there are some operations that will need to run in arbitrary folders.  I'd like to have the option of setting the working directory based upon a pre-defined sub-directory (e.g., ~/mount/Workspaces), with BASH TAB-completion for the name of the arbitrary folder.

The second snag is setting up a command line for a program to process a data file with certain commands, with the same TAB name completion.  I know how to do this when passing the file name as an argument to a non-interactive script, but for a menu, I'm a little lost.  :confused:

Any help would be appreciated.

---

### Post by Bachstelze on 2011-10-12
Instead of

```
cd /foo/bar/ba<TAB>
```

do

```
cd /foo/bar/ba*
```

If it is unambiguous (i.e. there is only one folder that matches), it will work as expected.

---

### Post by Ranko Kohime on 2011-10-13
> **Bachstelze said:**
> Instead of

```
cd /foo/bar/ba<TAB>
```

do

```
cd /foo/bar/ba*
```

If it is unambiguous (i.e. there is only one folder that matches), it will work as expected.
Erm, to clarify, /foo/bar would contain multiple directories, and only one of which I would want to work on.  Which directory that is would change frequently, with no predictable prefix, so the closest analogue would be
```
cd /foo/bar/*
```
which of course would get me nothing.

Sorry if my post was a little vague on that point.  ;)

---

### Post by Bachstelze on 2011-10-13
How is the script supposed to know which directory you want to cd to, then? Tab wouldn't work either....

---

### Post by Ranko Kohime on 2011-10-13
> **Bachstelze said:**
> How is the script supposed to know which directory you want to cd to, then? Tab wouldn't work either....
Yeah, that made it less confusing, didn't it?  :)

[LIST=1]
[*]The script prompts me for a directory
[*]I would enter the first few characters of the directory
[*]Tab complete it, and the script knows to look for folders by that name within /foo/bar.  (we'll assume files that would interfere with completion do not exist in /foo/bar)
[*]When I press enter, it would construct the command as:
[/LIST]
```
cd /foo/bar/$VARIABLE
```
The part I'm trying to get is step 3.

---

### Post by karlson on 2011-10-13
> **Ranko Kohime said:**
> Yeah, that made it less confusing, didn't it?  :)

[LIST=1]
[*]The script prompts me for a directory
[*]I would enter the first few characters of the directory
[*]Tab complete it, and the script knows to look for folders by that name within /foo/bar.  (we'll assume files that would interfere with completion do not exist in /foo/bar)
[*]When I press enter, it would construct the command as:
[/LIST]
```
cd /foo/bar/$VARIABLE
```
The part I'm trying to get is step 3.

Not sure you would be able to do this using shell you can certainly try.  I would suggest getting bash or tcsh source code and reading how it's being done.

The I am not sure how the executable commands tab completion is implemented but the directory/file completion would be intercepting <TAB> then reading contents of the directory and find the names of the contents that match the pattern already entered and if there is more then one entry letting user add more characters until done.  Now as far as shell is concerned I don't think you can do a terminal intercept to make <tab> an end of input character, so it would be <tab>+<enter>, then get an output of `ls ${curval}*` into an array then display the array if it's size > 1 or display an error if size = 0.

And one thing I completely forgot was the ability of removing <tab> from the value of input.

---

### Post by sisco311 on 2011-10-13
In bash:
```
cd /foo/bar || exit 1
read -e dir
echo "$dir"
```

See:```
help read
```

---

### Post by Ranko Kohime on 2011-10-23
> **sisco311 said:**
> In bash:
```
cd /foo/bar || exit 1
read -e dir
echo "$dir"
```

See:```
help read
```
Am I correct in assuming that dir is an arbitrary variable in this context?  (I'm pretty sure it is, but I figured I would ask anyway)  I'm still trying to wrap my mind around the somewhat cryptic help file for "read".

Also, this works great with my script...When I'm accessing single-word-named directories.  Anything with a space, even when escaped, returns:
```
Yukihiro\ Takahashi/
/home/ranko/Media/Workspace/Music to sort
/home/ranko/menus/./menu.sh: line 183: cd: /home/ranko/Media/Workspace/Music to sort/Yukihiro: No such file or directory

```
Any way to get around that?

---

### Post by Ranko Kohime on 2011-11-23
> **Ranko Kohime said:**
> Also, this works great with my script...When I'm accessing single-word-named directories.  Anything with a space, even when escaped, returns:
```
Yukihiro\ Takahashi/
/home/ranko/Media/Workspace/Music to sort
/home/ranko/menus/./menu.sh: line 183: cd: /home/ranko/Media/Workspace/Music to sort/Yukihiro: No such file or directory

```
Any way to get around that?
Bump.  Anyone know a solution to this?

---

### Post by Vaphell on 2011-11-23
could you post the fragment of your code? most likely you didn't put $dir inside double quotes to prevent fragmentation caused by whitespaces

```
startdir=$HOME/test
cd "$startdir" || exit 1
read -e dir
echo "dir: \"$startdir/$dir\""
cd "$dir" && echo -n "ls: " && ls
```

```
$ ./autocomp.sh 
test\ 1/
dir: "/home/me/test/test 1/"
ls: 1.txt  2.txt
```

---

### Post by Ranko Kohime on 2011-11-25
> **Vaphell said:**
> could you post the fragment of your code? most likely you didn't put $dir inside double quotes to prevent fragmentation caused by whitespaces
My current code:

```
flacsplit()
	( clear;
	cd ~/Media/Workspace/Music\ to\ sort || break;
	echo -n "Enter Directory: ";
	read -e "dir";
	pwd
	cd ~/Media/Workspace/Music\ to\ sort/$dir || echo -e "\n\t Error, directory not found, cancelling."; sleep 3; break;
	echo -n "Enter .cue file name: "
	read -e cue;
	echo -e $cue
	echo -n "Enter .flac file name: "
	read -e flac;
	echo -e $flac
	cuebreakpoints $cue | shnsplit -o flac $flac;
	rm $flac;
	cuetag $cue *.flac;
	metaflac --add-replay-gain *.flac;
	echo -e "\n\t Process complete, press Enter to return to menu"
	read enterKey; )

```

---

### Post by Vaphell on 2011-11-25
change
```
cd ~/Media/Workspace/Music\ to\ sort/$dir
```
to
```
cd "$HOME/Media/Workspace/Music to sort/$dir"
```

---

### Post by ofnuts on 2011-11-25
Using text menus is so 1980s.. Did you look into using a regular shell script and an intelligently configured tab completion so that it self-suggest the parameters when used in a command line (subcommand, parameters, directory name, file names, etc...)? See: [http://www.debian-administration.org/tag/command%20completion](http://www.debian-administration.org/tag/command%20completion) and have a look into your /etc/bash_completion.d/ directory.

---

### Post by Ranko Kohime on 2011-12-01
> **Vaphell said:**
> change
```
cd ~/Media/Workspace/Music\ to\ sort/$dir
```
to
```
cd "$HOME/Media/Workspace/Music to sort/$dir"
```
Thank you, that part of my script is working now.  :D

---

### Post by Ranko Kohime on 2011-12-04
> **ofnuts said:**
> Using text menus is so 1980s.. Did you look into using a regular shell script and an intelligently configured tab completion so that it self-suggest the parameters when used in a command line (subcommand, parameters, directory name, file names, etc...)? See: [http://www.debian-administration.org/tag/command%20completion](http://www.debian-administration.org/tag/command%20completion) and have a look into your /etc/bash_completion.d/ directory.
Text menus are awesome.  I can flip to my terminal (Guake), issue two single-number commands, and have any one of a dozen pre-defined commands begin, using just 5 key presses, before my eyes can perceive the screen updates.  :P

Ranting aside, I'm not sure that bash command completion would make what I'm attempting to do simpler.

---

### Post by ofnuts on 2011-12-04
> **Ranko Kohime said:**
> Text menus are awesome.  I can flip to my terminal (Guake), issue two single-number commands, and have any one of a dozen pre-defined commands begin, using just 5 key presses, before my eyes can perceive the screen updates.  :P

Ranting aside, I'm not sure that bash command completion would make what I'm attempting to do simpler.With properly configured tab completion you don't need that many keystrokes either and it works with filenames. 

In the 80s I had to use a big application with a multi-level text menu. One of the "hints" in the User's Manual was that you could enter multi-digit numbers to go directly to menu items deep down, but as someone noted, we ended up remembering arbitrary strings instead of mnemonic names, for instance "8675" instead of "erase".

---

