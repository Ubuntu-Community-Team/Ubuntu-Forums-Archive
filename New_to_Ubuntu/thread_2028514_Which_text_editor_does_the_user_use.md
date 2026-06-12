---
title: "Which text editor does the user use?"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by bustard on 2012-07-18
I am writing a script in which the user's editor opens a file for him to edit. So it is a command like this:

gedit <path to file>

The problem is that I do not know if the user has gedit installed. Maybe he uses kwrite or something else.

Is there something the script can check to see what editors are available to the user?

---

### Post by Paqman on 2012-07-18
AFAIK all versions of Ubuntu come with nano, so you could use that.

---

### Post by oldos2er on 2012-07-18
> **bustard said:**
> Is there something the script can check to see what editors are available to the user?

Wouldn't you want to use the default system editor? Whatever $EDITOR is?

---

### Post by Azdour on 2012-07-18
Hi,

It's not perfect but you could try:

```

xdg-open

```

---

### Post by cortman on 2012-07-18
> **oldos2er said:**
> Wouldn't you want to use the default system editor? Whatever $EDITOR is?

AFAIK the $EDITOR variable is only set if the user defines a custom environment, i.e., a .envrc file or the like.
The only editor that is on ALL Linux systems is vi. Vi is about as unwieldy for a beginner as it gets, though. I think I'd use nano.

---

### Post by drmrgd on 2012-07-18
I think the question is, though, if the OP is having the user work from the CLI or is launching this script graphically.  If not using CLI, wouldn't it better to use a graphical editor, in which case the script can query for Kate (default in KDE) or Gedit (default in Ubuntu)?

---

### Post by PaulW2U on 2012-07-18
And then there's Lubuntu and Xubuntu which have their own defaults. Can we be sure from the original post that Ubuntu is being used?

I think the script might have to make multiple checks to ensure all possibilities are catered for.

---

### Post by Cheesemill on 2012-07-18
+1 for xdg-open.

```
xdg-open <filename>
```Should automatically detect the file type and open it in the users preferred application.

```
rob@precise:~$ xdg-open --help
xdg-open - opens a file or URL in the user's preferred application

Synopsis

xdg-open { file | URL }

xdg-open { --help | --manual | --version }

Use 'man xdg-open' or 'xdg-open --manual' for additional info.
```

---

### Post by bustard on 2012-07-18
Thanks for the replies. xdg-open worked nicely when I added it to the script.

---

