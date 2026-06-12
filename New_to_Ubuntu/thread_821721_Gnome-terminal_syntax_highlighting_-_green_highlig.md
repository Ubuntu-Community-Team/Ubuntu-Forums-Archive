---
title: "Gnome-terminal syntax highlighting - green highlight?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by 655 on 2008-06-07
Gnome-terminal uses syntax highlighting to display executable files, directories, archives, etc., in different colors, as we know.  

By default the settings include [COLOR=Red]red[/COLOR] for archives, [COLOR=RoyalBlue]light blue[/COLOR] for directories, and [COLOR=Lime]bright green[/COLOR] for executable files.

What does it mean when directories are overlayed in a dark green highlight?
The font is in blue but the "background," or highlight, is green.

I assume this has something to do with file permissions?

---

### Post by cubeist on 2008-06-07
I am not sure, but you could try *ls -l* on the same folder and see what permission settings it has that might be different...

---

### Post by the_doc on 2008-06-07
I think it might indicate the sticky bit permission?

---

### Post by 655 on 2008-06-07
```
lrwxrwxrwx  1 root root     6 2008-05-11 16:35 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-05-11 16:35 cdrom0
[COLOR=DarkRed]drwxrwxrwx  1 root root  8192 2008-06-07 14:33 minerva1[/COLOR]
drwxr-xr-x  7 root root 32768 2008-06-07 14:42 minerva2
drwxr-xr-x 11 root root 49152 1969-12-31 19:00 minerva3
drwxr-xr-x  2 root root  4096 2008-05-27 13:35 multivac1
drwxr-xr-x  2 root root  4096 2008-05-27 13:35 multivac2
drwxr-xr-x  2 root root  4096 2008-05-27 13:35 multivac3
drwxr-xr-x  2 root root  4096 2008-05-27 13:35 multivac4

```

---

### Post by the_doc on 2008-06-07
Weird.  Every directory I find that's highlighted green has the t sticky bit set, and highlighted light blue for T.

---

### Post by 655 on 2008-06-07
[http://ubuntuforums.org/showthread.php?p=4779965](http://ubuntuforums.org/showthread.php?p=4779965)

I should have specified that the directory in question is a remote NTFS share.

There is no change in functionality that I can see, so I guess, as the above post suggests, it is just a poor color choice that can be amended.

---

### Post by 655 on 2008-06-07
Actually a follow-up question:

The disk in question is a drive formatted with NTFS, inherited from a former Windows box, that I haven't backed up and reformatted.  It seems the entire drive and its subcontents have permissions set at 777.

Is this customary for the way Windows handles permissions?

Would it be useful for me to chmod -R that whole disk?  Or could it cause problems?  (PATA drive mounted to /media)

---

### Post by gozo311 on 2010-01-10
I'm sure the highlighting is related to the 777 permissions.  It seems windows files accessed via a mounted device are all rwx permission for all users.  This results in a strange and difficult-to-read green highlight over blue letters for directories in the terminal.  

The highlighting bugs me, and I'm having trouble changing the permissions of these files.  It seems like it shouldn't be that difficult but 

$ sudo chmod 750 -R _filename_ | _directory_

doesn't do a darn thing.

Can someone help?

Alternatively, how to you adjust the colors chosen in the terminal interface?  Is there a configuration file or something?

---

### Post by doobiest on 2010-02-26
I dont know the proper way to fix this issue but this is what I do, and it's easy

```
export LS_COLORS=`echo $LS_COLORS|sed 's/34\;42/0\;46/g'`
```

I'll explain...

Run this to get a list of all dir color options. I'm passing it through sed so it will be more human readable on screen.

```
dircolors| sed 's/\:/\n/g'
```

Find the colour you want to change.  here's a reference (not all are included), [http://linux-sxs.org/housekeeping/lscolors.html]("http://linux-sxs.org/housekeeping/lscolors.html")

To experiement do this:

```
export LS_COLORS=`echo $LS_COLORS|sed 's/34\;42/0\;46/g'`
```

For those unfamiliar with sed, what I am doing is taking the current value and substituting it with the value I want.  So:

sed 's/34\;42/0\;46/g'

means I'm changing the default of 34:42 (blue text, green highlight background) and replacing it with 0:46 (white text, cyan background).

Try it right now if you want, paste this into a terminal and test it. If it does what you like save it to the end of your .bashrc file.

export LS_COLORS=`echo $LS_COLORS|sed 's/34\;42/0\;46/g'`


For those who don't know. go to your home dir, 

```
cd /home/<username>/
```

or just,

```
cd ~
```

edit the file .bashrc, using vi, mcedit, nano, gedit, whatever you like.

Scroll to the end of the file and add that export line.

---

### Post by vidsgr on 2011-10-23
I am not sure how to fix this problem completely... 

But changing LS_COLOR makes life simpler ... Thank u :)

> **doobiest said:**
> I dont know the proper way to fix this issue but this is what I do, and it's easy

```
export LS_COLORS=`echo $LS_COLORS|sed 's/34\;42/0\;46/g'`
```

I'll explain...

Run this to get a list of all dir color options. I'm passing it through sed so it will be more human readable on screen.

```
dircolors| sed 's/\:/\n/g'
```

Find the colour you want to change.  here's a reference (not all are included), [http://linux-sxs.org/housekeeping/lscolors.html]("http://linux-sxs.org/housekeeping/lscolors.html")

To experiement do this:

```
export LS_COLORS=`echo $LS_COLORS|sed 's/34\;42/0\;46/g'`
```

For those unfamiliar with sed, what I am doing is taking the current value and substituting it with the value I want.  So:

sed 's/34\;42/0\;46/g'

means I'm changing the default of 34:42 (blue text, green highlight background) and replacing it with 0:46 (white text, cyan background).

Try it right now if you want, paste this into a terminal and test it. If it does what you like save it to the end of your .bashrc file.

export LS_COLORS=`echo $LS_COLORS|sed 's/34\;42/0\;46/g'`


For those who don't know. go to your home dir, 

```
cd /home/<username>/
```

or just,

```
cd ~
```

edit the file .bashrc, using vi, mcedit, nano, gedit, whatever you like.

Scroll to the end of the file and add that export line.

---

### Post by oldos2er on 2011-10-24
Closed, necromancy. Please don't bump old threads.

---

