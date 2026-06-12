---
title: "Why Is MD5sum Not Working?"
date: 2022-01-07
forum: New to Ubuntu
---

### Post by jesus-pieces on 2022-01-07
I am writing this text, as I was told to so by the Ubuntu forum message pop-up. Oh, I am using Ubuntu 20.0.4.

---

### Post by deadflowr on 2022-01-07
Everyone of your commands is wrong.
You can run it with any of these
```
Downloads/file-name-here
~/Downloads/file-name-here
/home/username/Downloads/file-name-here
$HOME/Downloads/file-name-here
```
But there is no such place as /Downloads with just a slash in front like you tried.

---

### Post by howefield on 2022-01-07
Posting images of the terminal is not a good way to share terminal output.

Copy paste the text from the terminal into a post here and post between [noparse]```

```[/noparse] tags. This will make it easier for others to see the text.

---

### Post by The Cog on 2022-01-07
Expanding on deadflowr's post, all these 4 should work (I'm too lazy to type the whole filename - use Tab for filename completion instead of * if you prefer):
```
md5sum Downloads/code_*
md5sum ~/Downloads/code_*
md5sum /home/username/Downloads/code_*
md5sum $HOME/Downloads/code_*
```

---

### Post by jesus-pieces on 2022-01-08
Yeah, it turned out that I needed [sha256sum] , and it worked just fine, like you said it would with [md5sum] -- whoops, and ta-da! Thanks everyone. Uhm, should ta-da be uppercase?

---

### Post by TheFu on 2022-01-08
The way you are showing commands is confusing and odd.  Follow the same method that all the books use.
```
$ command
```
That's for normal users.
```
$ sudo some-admin-command
```
When you need to elevate privileges for 1 command.

Here's a beginning book that is a great place to start learning the basics, in order, so topics are introduced that build and build and build on prior topics.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Looks like the idea of absolute and relative directory paths hasn't been mastered. Learn that ... and tab-completion.

---

### Post by ActionParsnip on 2022-01-09
If the deb isn't found then you need to change directory to where it is (probably in Downloads)

---

