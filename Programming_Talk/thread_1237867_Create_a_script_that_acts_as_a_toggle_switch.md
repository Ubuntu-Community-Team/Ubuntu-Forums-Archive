---
title: "Create a script that acts as a toggle switch"
date: 2009-08-11
forum: Programming Talk
---

### Post by 4dplane on 2009-08-11
Hi,

I need to wright a script that works as a toggle switch between two different .asoundrc files. Click the toggle button once and one form of the .asoundrc file is written; select the button switch and second form of the .asoundrc file written. I know a bit of C++ and can probably figure it out but any suggestions would be great. Should I use c++?

thanks,
4dplane

---

### Post by unutbu on 2009-08-11
Suppose you have two configs ~/.asoundrc and ~/.asoundrc2
Then whenever this script is run, the contents of the two files will be swapped:

[PHP]#!/bin/bash
mv ~/.asoundrc ~/.asoundrc_tmp
mv ~/.asoundrc2 ~/.asoundrc
mv ~/.asoundrc_tmp ~/.asoundrc2
[/PHP]
You could then make a GNOME launcher to run the script whenever the icon is double-clicked. That would sort of be like a button...

---

### Post by shawnhcorey on 2009-08-11
I would use a symbolic link to link a third name to the file I want to use:
```
ln -sf .asoundrc soundrc
```
or
```
ln -sf .asoundrc2 soundrc
```
See `man ln` for details.

---

### Post by unutbu on 2009-08-11
Yep, that's a better idea.

---

### Post by tgalati4 on 2009-08-11
If you are using asoundconf then your final file must be .asoundrc.  So if you are running a game that requires certain sound setup:

Make a script to run the game:

pseudocode:

#!/bin/bash
# start with a fresh asound resource file
rm .asoundrc
cp myspecialasoundrcfileformygame .asoundrc
asoundconf
runmygame
rm .asoundrc
cp mystandardasoundrcfile .asoundrc
asoundconf
exit

Of course, if your game crashes then you are left with the specialized .asoundrc file configuration.

---

### Post by 4dplane on 2009-08-11
Thanks all, three versions to choose form, what more could I ask for.:P

unutbu I understand you concept and it should work for what I need.

shawnhcorey, how would I use yours exactly? would I still use a script that the button call to flip the ln to the oppisite file?

tgalati4, i almost get it except how does this pseudocode,
rm .asoundrc
How do I know when the program stops?

This script is so I can move from 1/8 inch audio and HDMI audio with the toggle button.

Thanks,
4dplane

---

### Post by shawnhcorey on 2009-08-12
> **4dplane said:**
> shawnhcorey, how would I use yours exactly? would I still use a script that the button call to flip the ln to the oppisite file?


It's been a while since I did any coding in C but below is a shell script that toggles between the files sound1 and sound2.  To do it in C, you need the system calls:

man 2 readlink
man 2 symlink

```
#!/bin/sh
#
# uses POSIX shell
#

# first time there's no .asoundrc
if [ ! -e .asoundrc ]
then
  ln -s sound1 .asoundrc
  exit 0
fi

# in case there's a real file there
if [ ! -h .asoundrc ]
then
  echo ".asoundrc is not a symbolic link" 1>&2
  exit 1
fi

# now toggle them
case `readlink .asoundrc` in
  sound1) ln -sf sound2 .asoundrc ;;
  sound2) ln -sf sound1 .asoundrc ;;
  *) ln -sf sound1 .asoundrc ;;
esac


```

---

### Post by 4dplane on 2009-08-12
Thanks for the info!

---

