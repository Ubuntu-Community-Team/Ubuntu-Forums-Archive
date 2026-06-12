---
title: "BASH script for renaming tracks to prepend disc number"
date: 2010-03-03
forum: Programming Talk
---

### Post by jamesisin on 2010-03-03
I have written a new version of my script for prepending disc numbers to track names (ie: 01 - Track Name.flac becomes 01.01 - Track Name.flac).

You can find the script here:

[http://www.soundunreason.com/InkWell/?p=1415](http://www.soundunreason.com/InkWell/?p=1415)

I would appreciate any constructive criticisms you may have.  I think it could be more secure (I don't like the way I make use of $directory for instance) and I suspect I might be able to write more clean or efficient code.

Thanks for any advice you offer.

---

### Post by falconindy on 2010-03-03
rename will do what you want without the need for a loop.

```
rename 's/^/01./' *.[Ff][Ll][Aa][Cc]
```

[Everybody stand back. I know regular expressions.](http://xkcd.com/208/)

---

### Post by jamesisin on 2010-03-03
Thanks.  You actually made me see a typo in my script.

Now as to your suggestion, will this parse as expected (vis a vis, will it prepend the contents of $REPLY, which ought to be 01-99)?

```
rename 's/^/$REPLY./' *.[Ff][Ll][Aa][Cc]
```

---

### Post by falconindy on 2010-03-03
You'll need double quotes instead of single quotes if you wish to use a variable in the expression.

---

### Post by jamesisin on 2010-03-03
In my mv command I am able to show my work (echo $filename changed).  Is there a simple way I can do that using the rename command?

---

### Post by jamesisin on 2010-03-03
This doesn't work:

```
rename "s/^/$directory./" *.[Ff][Ll][Aa][Cc]
```

I get an error:

```
Bareword found where operator expected at (eval 1) line 1, near "s/^//home"
Search pattern not terminated at (eval 1) line 1.
```

---

### Post by falconindy on 2010-03-03
Huh. Not sure what the specific issue is but there's some malformage of your regex going on. "s/^//home" is definitely not right. I'd double check the contents of your $directory variable for starters.

This is working fine for me:

```
% touch file{01..10}.flac
% ls
file01.flac  file02.flac  file03.flac  file04.flac  file05.flac
file06.flac  file07.flac  file08.flac  file09.flac  file10.flac

% num=01
% rename "s/^/$num/" *.flac
% ls
01.file01.flac  01.file03.flac  01.file05.flac  01.file07.flac  01.file09.flac
01.file02.flac  01.file04.flac  01.file06.flac  01.file08.flac  01.file10.flac
```

---

### Post by jamesisin on 2010-03-03
In my script the user is able to give the path to the folder containing the flac files.  I have been using the /home/... path (and not ~/).  I do print that variable ($directory) and that looks like this:

```
I will prepend 05 to all FLAC files in: /home/username/Desktop/FlacTest

```

So I'm a little confused by a) the additional / and b) the dropping of /username/Desktop/FlacTest.

---

### Post by diesch on 2010-03-03
> **jamesisin said:**
> This doesn't work:

```
rename "s/^/$directory./" *.[Ff][Ll][Aa][Cc]
```I get an error:

```
Bareword found where operator expected at (eval 1) line 1, near "s/^//home"
Search pattern not terminated at (eval 1) line 1.
```

It doesn't work if $directory contains a */*. You can use
```
rename "s|^|$directory.|" *.[Ff][Ll][Aa][Cc]
```
instead (if  $directory doesn't contain a *|*)

---

### Post by jamesisin on 2010-03-03
Or, I'm an idiot.

I was using the wrong variable.  I have updated my post with the corrected version (using remove).

Thanks.  Let me know if you decide it could be further improved.

(I would still like to show my work, if that is possible using rename.)

---

### Post by jamesisin on 2010-03-03
Hi, diesch.  Thanks for the tip.

---

