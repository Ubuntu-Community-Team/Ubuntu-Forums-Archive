---
title: "How to get a filepath from dragging a file onto a script?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Rhyok on 2008-05-06
Hello,
I was just wondering if it was possible to get the filepath of a file by dragging said file onto a bash script? Preferably, I would like it to put it into a variable. Is this possible?

Thanks,
Rhyok

---

### Post by terrorsathan on 2008-05-06
If you pull a file into the terminal it'll work. So if you edit a file with f.e. '$ nano *filename*' in the terminal and you pull a file into it, it'll display the path to the pulled file.

regards

---

### Post by Hospadar on 2008-05-06
I assume you want to write something that you can drag files onto and it will operate on those files.

First off, what is it that you want to do?  There are some nautilus addons which already provide a lot of this type of functionality and your feature may already be covered.

Other than that, there are really two ways you could get this done:

First: Use a nautilus script, it's basically a bash script, but with some extra variables which you'll have to research to find out about, but from what I gather it's pretty easy to do.  Basically, you write a script using these special variables that give you stuff like the filename, then put it into some folder in your home directory, then it shows up as an action in a right-click menu of files.

Second, if you really require dragging, you'd either have to write some crazy extension to nautilus (really hard) or maybe use python and pygtk (i.e. gtk for python) to make a program that just opens a little window that you can drag stuff into that will operate on those files.  This is probably way more work than option one, but python is a relatively easy language and I bet it'd be a fun project if you're into that kind of thing.

---

### Post by Rhyok on 2008-05-07
Thanks Hospadar!
I'm really just looking for something which uses the shred (options -vfuz) command instead of the regular delete command. Also, if I made a Nautilis script (or any bash script for that matter), is there any way to automatically open a terminal to run the script?

Reguards,
Rhyok

---

### Post by Rhyok on 2008-05-07
Well,
I've got a context menu script working now. But the script doesn't appear to be recognizing the shred command unless I run it in the terminal.
Here's the code:
```
#!/bin/bash
for arg
do
shred -fuvz $arg
done
```

I based it off of this script:
```
#!/bin/sh
# make_nautilus_script: copies the selected file(s) to ~/Nautilus/scripts
# and makes it executable.  It will overwrite without warning.
for arg 
do

 cp "$arg" ~/.gnome2/nautilus-scripts/
 chmod u+x ~/.gnome2/nautilus-scripts/"$arg"
 
done
```

Is shred not a sh/bash command by itself? If so, is there a command which will provide similar functionality (overwrites a file several times and then zeros the addresses) or run the gnome-terminal?

---

