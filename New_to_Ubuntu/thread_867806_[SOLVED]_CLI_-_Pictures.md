---
title: "[SOLVED] CLI - Pictures"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-23
Hi in the spirit of Learning, I would like to know 2 things:  After having ceedee'd to "Pictures" how do I display one of the images?  I know how to open windows, I'm looking for CLI techniques.  my second question involves files names with blank spaces?  It seems to confuse bash or whoever because the space is interpreted as a break in command or what have I. I'm guessing quotaion marks.  Is this right?

---

### Post by LaRoza on 2008-07-23
Try "fbi" for viewing the images, and yes, use quotes when there are spaces (or better yet, don't use spaces)

(If you want to open an image in a GUI app, you can usually just use the name of the app and the file name, fbi is a framebuffer app)

---

### Post by Joeb454 on 2008-07-23
You can also escape space's with a backslash, i.e. ```
:~$ cd Pictures
:~/Pictures$ fbi ./my\ random\ picture.jpg
```

Though I think quotes may be easier ;)

---

### Post by LaRoza on 2008-07-23
> **Joeb454 said:**
> You can also escape space's with a backslash, i.e. ```
:~$ cd Pictures
:~/Pictures$ fbi ./my\ random\ picture.jpg
```

Though I think quotes may be easier ;)

Note to OP: If you decide to use fbi, read the man page ;)

---

### Post by DGortze380 on 2008-07-23
> **adamogardner said:**
> Hi in the spirit of Learning, I would like to know 2 things:  After having ceedee'd to "Pictures" how do I display one of the images?  I know how to open windows, I'm looking for CLI techniques.  my second question involves files names with blank spaces?  It seems to confuse bash or whoever because the space is interpreted as a break in command or what have I. I'm guessing quotaion marks.  Is this right?

to display pictures (assuming you have gnome installed and are running in an open terminal)

```

gthumb /location/of/file/fileName

```

to handle file names with spaces. Don't use spaces if you can avoid it. (fileName or file_name). Or:

```

<command> file\ name
or
<command> "file name"
or
<command> file<tab>

```

(The tab key will complete command or file name you are typing as long as it has enough unique identifiers. If there are not enough unique identifiers then pressing tab a second time will display a list of files/commands that begin with what you have types. Open a terminal and press <tab> <tab>  ... now type the letter a and press <tab> <tab>

---

### Post by Growbag on 2008-07-23
To overcome the space problem, simply press the TAB key to autocomplete the filename.

IE type your command and any options, then when you get to the part that needs a space, press TAB and it will fill it in for you.

Pressing TAB twice quickly (double-tabbing) will list all possibilities.

Or as laroza suggested, use a single quote in front of the folder/filename that contains a space.

eg:

```
display -l -f '~/Pictures/This filename contains rotten spaces.jpg'
```

Should do it :)

---

### Post by Joeb454 on 2008-07-23
> **LaRoza said:**
> Note to OP: If you decide to use fbi, read the man page ;)

Yeah I've never used fbi so I have no idea, but I needed some sort of command to put at the front ;)

---

### Post by JillSwift on 2008-07-23
Wow. fbi is cool.
Note: It won't work in something like xterm. Use a console.

---

### Post by LaRoza on 2008-07-23
> **Joeb454 said:**
> Yeah I've never used fbi so I have no idea, but I needed some sort of command to put at the front ;)

It wouldn't have worked the way you had it. LOL n00b!

---

### Post by Joeb454 on 2008-07-23
> **LaRoza said:**
> It wouldn't have worked the way you had it. LOL n00b!

Ack...you found out my secret!!!

---

### Post by adamogardner on 2008-07-23
ok  thanks  I'm playing with both fbi and imagemagick.

---

