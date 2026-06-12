---
title: "Running .sh problems?"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by armistice90 on 2013-05-28
Hello everyone,

I'm attempting to run a .sh file, but I'm encountering issues. I've already changed its permissions to allow execution, but when I double click the icon, no window asking if I would like to run the script appears. I ran this file just fine on every version of Ubuntu 12 I used. but I'm having issues now that I've switched to Ubuntu 13. Any advice?

---

### Post by prodigy_ on 2013-05-28
> **armistice90 said:**
> I've already changed its permissions to allow execution, but when I double click the icon, no window asking if I would like to run the script appears.
If a file is marked executable, it's executed silently. Why would you need a confirmation dialog anyway?

---

### Post by Locus Kiesselbachi on 2013-05-28
hehe ...hello!

Try through terminal Ctrl+T!

You need to install korn shell program-thingy.
```
sudo apt-get install ksh
```
then open your executable file.
```
*sh "filename"*
```
or
```
sudo sh *"filename"*
```
[I]or
[/I]```
sudo ksh *"filename"*
```

:)

---

### Post by prodigy_ on 2013-05-28
> **Locus Kiesselbachi said:**
> or
More like *not*. ;) A .sh file is very likely a bash script which, depending on what's inside, may be incompatible with sh/ksh.

---

### Post by Locus Kiesselbachi on 2013-05-28
Well, sometimes it helped me trying to get .sh thingy running. ;-)

---

### Post by armistice90 on 2013-05-28
I suppose I didn't clarify too well. I'll click, and it opens with gedit instead of prompting if I want to run the file. I've always recieved a prompt in the past when using 12

---

### Post by deadflowr on 2013-05-28
What's the intended result of the script?

---

### Post by armistice90 on 2013-05-28
It's supposed to run a visual novel.

---

### Post by deadflowr on 2013-05-28
Is it a long script?

Maybe in it's somewhat short, like a page or so, you could post it and we could review what's at fault.

If you choose to, please use the code tags from the reply box toolbar (# symbol)

---

### Post by armistice90 on 2013-06-01
Sure thing. It's rather short, so here it is.

```
#!/bin/sh

# We assume Darwin means Mac OS X. Sorry, Darwin guys.
if [ "x`uname -s`" = "xDarwin" ]; then
    dir=`dirname "$0"`
    dir=`cd "$dir"; pwd`
    base=`basename "$0"`

    export RENPY_LAUNCHER_DIR="$dir"

    if [ -e "$dir/${base%.sh}.app/Contents/MacOS/${base%.sh}" ] ; then
        launcher="$dir/${base%.sh}.app/Contents/MacOS/${base%.sh}"
    else
        launcher="$dir/${base%.sh}.app/Contents/MacOS/Ren'Py Launcher"
    fi

    exec "$launcher" "${0%.sh}.py" "$@"
fi

exec "`dirname \"$0\"`/lib/python" "-OO" "${0%.sh}.py" "$@"
```

---

### Post by HiImTye on 2013-06-01
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
open your file manager (Files or nautilus), then click the gear icon, go to preferences, clivk the Behaviour tab, then choose 'Ask each time' below 'Executable Text Files'

---

### Post by prodigy_ on 2013-06-01
> **armistice90 said:**
> Sure thing. It's rather short, so here it is.

```
#!/bin/sh

# We assume Darwin means Mac OS X. Sorry, Darwin guys.
if [ "x`uname -s`" = "xDarwin" ]; then
    dir=`dirname "$0"`
    dir=`cd "$dir"; pwd`
    base=`basename "$0"`

    export RENPY_LAUNCHER_DIR="$dir"

    if [ -e "$dir/${base%.sh}.app/Contents/MacOS/${base%.sh}" ] ; then
        launcher="$dir/${base%.sh}.app/Contents/MacOS/${base%.sh}"
    else
        launcher="$dir/${base%.sh}.app/Contents/MacOS/Ren'Py Launcher"
    fi

    exec "$launcher" "${0%.sh}.py" "$@"
fi

exec "`dirname \"$0\"`/lib/python" "-OO" "${0%.sh}.py" "$@"
```
Since the whole **if [ "x`uname -s`" = "xDarwin" ] ... fi** block is intended for OS X, essentially you only need the last line. Which looks alright to me but it simply runs another (python) script.

Try running this .sh file from terminal window and see if there are any error messages.

---

### Post by armistice90 on 2013-06-03
Here's where my true beginner shines...

What command do I use to run it from terminal?

---

### Post by MidnightGrey on 2013-06-03
> **armistice90 said:**
> What command do I use to run it from terminal?

to run a script from terminal you just have to call it.
for example if your script is in the folder ~/bin/scripts/MyScript.sh, you can type out this code:

```
$ ~/bin/scripts/MyScript.sh
```
or
```

$ cd ~/bin/scripts
$ ./MyScript.sh
```

However since you say when you double click your script, gedit opens. I suspect your execute permissions may not be set properly.
If the above does not work, try set your permissions using this code:
```

$ chmod +x ~/bin/scripts/MyScript.sh

```
You can also view your file permissions in file explorer by right clicking on the script > Properties > Permissions > is Execute checked?

---

### Post by Dabo Ross on 2013-06-03
Make sure that the option in nautilus/files is to open a dialog. The default may have changed in 13.04.

This is how I would change this option:

Go to Preferences -> Behavior.
Check 'Ask each time' under 'Executable Text Files'.

Was that already set or does it work the way you want it to when it is set to that?

I think the default is 'View executable text files when they are opened' in 13.04, but I am not sure about which the default is.

HiImTye already said this so I am just elaborating.

Here are screenshots of what I do to get to that settings page:
[http://screencloud.net/v/F4lK](http://screencloud.net/v/F4lK)
[http://screencloud.net/v/sSIO](http://screencloud.net/v/sSIO)

---

### Post by armistice90 on 2013-06-06
There we go! Thanks for all the help. It finally worked.

Here's the sequence I had to run:
I tried the chmod command you listed, but I recieved error messages. I then tried the two-part code you mentioned. 
```
cd ~/Scriptfile
./File Name.sh

```
As it turns out, the space in the original file's name would not allow me to run it from terminal. I went and renamed it so it was one word, and renamed the python script it was based on.
```
./FileName.sh
```
It opened and I could read my visual novel after that. 

Thanks again!

---

### Post by steeldriver on 2013-06-06
Just fyi, you can handle filenames with spaces in 2 other ways (aside from renaming them) - 'escaping' the space(s) with a backslash character or quoting the name

```
./File\ Name.sh
```

```
./"File Name.sh"
```

```
"./File Name.sh"
```

```
./"File Name".sh
```

---

