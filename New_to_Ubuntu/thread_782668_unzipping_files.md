---
title: "unzipping files"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by houstonasl on 2008-05-05
i hate to sound so amatuer but i am, while trying to make my transition to ubuntu process easier, i downloaded freeciv, the game for times when i'm not browsing ubuntuforums:wink: well it downloaded it alright and the unzipping program came up needing to know if i wanted to open, extract,add files..... etc. i guess what i'm looking to find out is how do i unzip the file and get to the game? thanx in advance fellas

---

### Post by Joeb454 on 2008-05-05
It's in the repositories - Open Add/Remove or Synaptic Package Manager from the menu's and search for Freeciv.

*Goes to install Freeciv*

I should point out you can also open a terminal and type (or copy) ```
sudo aptitude install freeciv-client-gtk
```

---

### Post by zvacet on 2008-05-05
For extracting rar,zip... go to the applications>accessories<terminal and type

```
sudo apt-get install unrar p7zip p7zip-full
```

after that just right click on file and select **unpack here**

---

### Post by houstonasl on 2008-05-05
thanx a bunch guys....

---

### Post by illu45 on 2008-05-05
> **houstonasl said:**
> i hate to sound so amatuer but i am, while trying to make my transition to ubuntu process easier, i downloaded freeciv, the game for times when i'm not browsing ubuntuforums:wink: well it downloaded it alright and the unzipping program came up needing to know if i wanted to open, extract,add files..... etc. i guess what i'm looking to find out is how do i unzip the file and get to the game? thanx in advance fellas

Extract is the same thing as unzip, only it refers to the general process of extracting files from an archive rather than referring to .zip files specifically.

---

### Post by StaceyRVC on 2008-05-06
> **zvacet said:**
> For extracting rar,zip... go to the applications>accessories<terminal and type

```
sudo apt-get install unrar p7zip p7zip-full
```

after that just right click on file and select **unpack here**

Hi, this is my first post. I am totally new to ubuntu and I have done the above, but when I right click on the rar file I get open with archive manager which doesn't recognize the file. I then go to open with... and I haven't a clue where it installed. Any help on this would be great. Thanks in advance for your help

---

### Post by Monicker on 2008-05-06
> **StaceyRVC said:**
> Hi, this is my first post. I am totally new to ubuntu and I have done the above, but when I right click on the rar file I get open with archive manager which doesn't recognize the file. I then go to open with... and I haven't a clue where it installed. Any help on this would be great. Thanks in advance for your help

You might try extracting it from the command line, to see if there is a more descriptive error message.


Applications -> Accessories -> Terminal


If the file was saved to your Desktop:
```

cd Desktop
unrar x file.rar
```

---

### Post by StaceyRVC on 2008-05-06
> **Monicker said:**
> You might try extracting it from the command line, to see if there is a more descriptive error message.


Applications -> Accessories -> Terminal


If the file was saved to your Desktop:
```

cd Desktop
unrar x file.rar
```

thats the funny thing, i have no idea where it installed to. There is nothing on my desktop, since I like to keep it clean, I am at a total loss on how to extract this "movie"

---

### Post by lazyart on 2008-05-06
Check your home folder.

---

### Post by StaceyRVC on 2008-05-06
I know where the movie went cause i moved to the "video" folder, I just can't get it to extract no matter what i do. Mind you I am VERY VERY new at this (Ubuntu) and I haven't a clue what's going on. I like learning new things but I am starting to give up :(

---

### Post by Monicker on 2008-05-06
What is in Places -> Videos?

Is this a split rar archive, with multiple files?

If the file was downloaded using Firefox, you can go to Tools -> Downloads, and it should be listed there.  If so, right click and select Properties; the path to the file will show up in the dialog box.

---

### Post by HotShotDJ on 2008-05-07
Just a quick, possibly dumb question... have you installed the unrar package (using Synaptic).  Installing the ubuntu-restricted-extras package will also pull unrar in with it along with other ubuntu goodness.

---

### Post by StaceyRVC on 2008-05-07
Thanks guys, I don't know what happened but I rebooted and it actually let me unrar it. I appreciate all the help!

---

### Post by panos1234 on 2008-05-08
Hi!

I have the same problem with Stacey. I note that the zip file needs a password to be extracted. The error message is this:


Usage:     UNRAR <command> -<switch 1> -<switch N> <archive> <files...>
                 <@listfiles...> <path_to_extract\>
           Specify empty listfile name to read names from stdin

<Commands>
  x     Extract with full path        e    Extract to current directory
  t     Test archive files            p    Print file to stdout
  l     List contents of archive      v    Verbosely list contents of archive

<Switches>
  r     Recurse subdirectories        y     Assume Yes on all queries
  o+    Overwrite existing files      o-    Do not overwrite existing files
  f     Freshen files                 u     Update files
  v             List all volumes
  c-            Disable comments show
  x<file>       Exclude specified file
  x@<list>      Exclude files in specified list file
  x@            Read file names to exclude from stdin
  p<password>   Set password
  p-            Do not query password
  kb            Keep broken extracted files
  ierr          Send all messages to stderr
  inul          Disable all messages

---

