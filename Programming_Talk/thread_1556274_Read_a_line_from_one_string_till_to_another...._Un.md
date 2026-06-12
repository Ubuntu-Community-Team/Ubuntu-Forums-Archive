---
title: "Read a line from one string till to another.... Unix scripting.."
date: 2010-08-19
forum: Programming Talk
---

### Post by hakermania on 2010-08-19
So i have a file which contains paths to JPG images separated by a space.
I have to separate them each path to another file. So, I have to search all strings that start from /home/ and ends with .jpg
Then write each one to another file...

Can you please help me on doing this???

---

### Post by Bachstelze on 2010-08-19
If I understand correctly...

```
firas@tsukino ~ % cat test  
/home/foo/bar/baz.jpg /home/bar/foo.jpg /home/bar/foo.png /var/www/foo.jpg /home/bar/baz/foo.jpg
firas@tsukino ~ % grep -o "/home/[^ ]*\.jpg" test > test2 
firas@tsukino ~ % cat test2
/home/foo/bar/baz.jpg
/home/bar/foo.jpg
/home/bar/baz/foo.jpg

```

---

### Post by hakermania on 2010-08-19
Thanks for your reply. Some Dirs have Spaces between them (e.g. Nice Pictures), then I have a script to correct them and add a \ before every space.
Your solution doesn't work in case the path includes Dirs with Spaces (e.g. /home/alex/Pictures/Nice\ Pictures/pic.jpg)

---

### Post by dwhitney67 on 2010-08-19
> **hakermania said:**
> Thanks for your reply. Some Dirs have Spaces between them (e.g. Nice Pictures), then I have a script to correct them and add a \ before every space.
Your solution doesn't work in case the path includes Dirs with Spaces (e.g. /home/alex/Pictures/Nice\ Pictures/pic.jpg)

Take a step back... why did you create a file that is hard to parse?

Would it not have made more sense to place a separate file path on individual lines?  More importantly, why do you even have a file?  Could you not have used the 'find' command to locate the desired files and then process them?

---

### Post by hakermania on 2010-08-19
[dwhitney67]("http://ubuntuforums.org/member.php?u=322753") Interesting... Problem solved actually by this suggestion......
If you know QtCreator
i used QStringlist::join("\n") instead join(" ")
cool, thank you

---

### Post by geirha on 2010-08-19
Even better would be to use \0 as separator, because \0 is the only character not allowed in pathnames.

To iterate a \0 separated list in bash, you'd do:
```
while IFS= read -r -d '' file; do
  echo "Do stuff with $file"
done < file.list

```

See [http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)

---

