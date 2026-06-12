---
title: "Perl script returning &quot;Unrecognized character \xC2&quot;"
date: 2013-09-21
forum: Programming Talk
---

### Post by raac on 2013-09-21
Hello guys, I'm wondering why the perl script is returning an error after execution

This is the script
```

#!/usr/bin/perl




@output = split $/, `ls -l | grep '^d'`;
$currentPath = `pwd`;
chomp $currentPath;
    while(scalar(@output))
    {
	$out = shift(@output)
        @directoryName = split(' ', $out);
    }


```

The error is the following:

_***Unrecognized character \xC2; marked by <-- HERE after <-- HERE near column 1 at scripts/rarRecCopy.pl line 8***_

I have no idea why the error happened or what does it even mean? I see no errors in the script itself.
Any ideas?

Thanks.

---

### Post by ofnuts on 2013-09-21
C2 is the uppercase A circumflex, but is also the first byte of some characters encoded on two bytes in UTF-8 (see [http://www.utf8-chartable.de/](http://www.utf8-chartable.de/)). So it could be a case of a script encoded in UTF-8 (and read as such by your editor, si you don't see anything...) but considered as ASCII (ISO-8859-something) by the Perl interpreter. Some interpreters recognize a second line indicating the assumed encoding for the file ("# -*- coding: iso-8859-15 -*-" or '# -*- coding: UTF-8 -*-").

---

### Post by raac on 2013-09-22
Interesting, so you're thinking is a different encoding between the editor and the interpreter. How can I set them to be the same encoding??.
This is the result of the grep command.

drwxrwxr-x 4 tony tony 4096 Sep 17 18:07 eclipse-applications
drwxrwxr-x 2 tony tony 4096 Sep 17 18:24 jarFiles
drwxrwxr-x 2 tony tony 4096 Sep 21 11:58 scripts
drwxrwxr-x 5 tony tony 4096 Sep 20 19:59 shared


For a second I thought that there could be a non-ascii character, but they all are ascii. They're just simple letters and numbers, I'm surprised Perl is acting like this.

---

### Post by ofnuts on 2013-09-22
> **raac said:**
> Interesting, so you're thinking is a different encoding between the editor and the interpreter. How can I set them to be the same encoding??.
See my previous post for the magic string that may make Perl use the right encoding.

Otherwise any decent text editor will let you use a given encoding for a file.

---

### Post by trent.josephsen on 2013-09-22
> **raac said:**
> For a second I thought that there could be a non-ascii character, but they all are ascii. They're just simple letters and numbers, I'm surprised Perl is acting like this.

\xC2 is not in the ASCII character set, so no, they are not all ASCII. You may not be able to see the non-ASCII characters by visual inspection in a text editor, which would seem to be the problem in the first place. Try looking at it in a different editor, or run `xxd rarRecCopy.pl` to see exactly which bytes the file contains.

FWIW, when I copy and paste from your original post, the file contains no non-ASCII characters.

---

