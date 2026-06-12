---
title: "[SOLVED] I need help removing the top and bottom of a text file"
date: 2007-10-01
forum: Programming Talk
---

### Post by arsenic23 on 2007-10-01
In an effort to learn bash, I've been trying to come up with something I can do by writing a new bash script every morning.  Today I've been working on translating a .html doc from a forum into a readable plain text document.  I managed to get all of the content I care about formated correctly with a nice long sed command, but I'm left with a fair bit of garbage at the beginning and end of the document that doesn't look like it would be efficiant/possible to remove using any method I know of.

What I need to do is remove everything from the beginning of the file down to a line that matches a certain regex, and then from the end of a file up to a line that is always static.  Any good methods for doing this in bash ?

---

### Post by Cappy on 2007-10-01
I wrote a script to do this for phpBB not too long ago.
Take a look at this:
[http://ubuntuforums.org/showthread.php?t=521711](http://ubuntuforums.org/showthread.php?t=521711)

To answer your original question though you can either loop through using bash like I did in my above script OR
you can write an awk regex to do it. Looking back I should have used awk but I didn't know about its awesome capabilities then.

If you want to see how to do it in awk this post would be a good starting point:
[http://ubuntuforums.org/showpost.php?p=3323614&postcount=4](http://ubuntuforums.org/showpost.php?p=3323614&postcount=4)

---

### Post by stylishpants on 2007-10-01
This is trivial in sed.

```
fhanson@fhanson:/tmp$ cat file
leading garbage
===start===
body
===end===
trailing garbage

fhanson@fhanson:/tmp$ sed -e '1,/===start/d' -e '/===end/,$d' file
body

```

Replace the /===end/ regex with a line number if you prefer.


Of course, learning purposes aside, if you really wanted to convert html to text, you would do "lynx -dump" or "links -dump".

---

### Post by Cappy on 2007-10-01
The only problem with sed is nested statements. In my linked code I was trying to get a copy of all text with no quotes.

Here is an example:
```

**$ cat file**
leading garbage
===start===
body one
===start===
body two
===end===
body one continued
===end===
trailing garbage

**$ sed -e '1,/===start/d' -e '/===end/,$d' file**
body one
===start===
body two

```

If you aren't dealing with anything nested though then sed will work perfectly.

---

### Post by ghostdog74 on 2007-10-01
```

# awk '/start/{f=1};/trail/{f=0};f' file
===start===
body one
===start===
body two
===end===
body one continued
===end===

```

---

### Post by arsenic23 on 2007-10-02
Thanks alot guys, you were all a big help.

Because of the simplicity of what I was doing the sed command worked perfectly.  Truth be told I didn't realize that that was how sed's d command worked, and I even had to go back and reread the man page to perfectly understand why that worked.  Thanks to all your help I was able to get my desired output with only a 10 part sed command.

Thanks again.

edit----------------------
Oh, and BTW, I had no idea that you could -dump with lynx - links - links2.  That's neat.

---

