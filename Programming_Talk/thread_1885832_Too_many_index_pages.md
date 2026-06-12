---
title: "Too many index pages?"
date: 2011-11-23
forum: Programming Talk
---

### Post by Hack.The.Pow. on 2011-11-23
Hello everybody.  I am running a web server that hosts some media files to my friends.  

I am trying to provide a nicer interface for them instead of a simple directory tree.  However in every directory it seems I am creating a index.php file to show the files available for download(ex: mysite.com/Media/Videos/index.php).  It seems like it is bad practice to have this many index pages on one site.  

Would this be a bad thing or no?  I just feel awkward having a index page for every directory root.  Would there be any other way of doing this?

---

### Post by Bachstelze on 2011-11-23
You could have the directory as parameter, like index.php?path=Media/Video and then use PHP to list the files in that directory and create the download links.

Alternatively, just don't put an index page at all and use Apache's built-in indexing. For a simple file server it should be nice enough.

---

### Post by Hack.The.Pow. on 2011-11-24
> **Bachstelze said:**
> You could have the directory as parameter, like index.php?path=Media/Video and then use PHP to list the files in that directory and create the download links.

Alternatively, just don't put an index page at all and use Apache's built-in indexing. For a simple file server it should be nice enough.

By the built in indexing do you mean the default directory viewing?  If so that's what I have now and just for fun wanted to make something more attractive with preview images and such.

---

### Post by Hack.The.Pow. on 2011-11-25
So I have used the path variable in my php script now to reduce the amount of index files.  I have sanitized input so directory traversal attacks would not be possible.  I was just wondering if what i have is enough.

I have made sure that all path entries start with one of the 4 correct directories in my /var/www/Media folder.  I have also checked to see if any ".." is in the path variable.  If there is I deny access.  

What I'm wondering is if this is sufficient.  While this directory is still password protected I want to make sure that it is still as secure as if it were publicly available.

---

### Post by Bachstelze on 2011-11-25
This should be fine. You might also want to make sure all directory path are relative (i.e. don't start with a /). If everything is relative to your /var/www dir and you don't allow .. or have symlinks you should be fine.

---

### Post by Hack.The.Pow. on 2011-11-25
I do have symlinks for all my media folders.  In Media there are 4 symlinks to the various media folders in my home directory.  I don't really see how that would be a problem with my sanitizing of inputs though....

---

