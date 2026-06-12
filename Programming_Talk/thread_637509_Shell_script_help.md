---
title: "Shell script help"
date: 2007-12-11
forum: Programming Talk
---

### Post by SupaSonic on 2007-12-11
I probably should post it here.

I'm trying to migrate a CVSNT repository to a Linux server which runs CVS. However the problem is that all binary files are messed up. I found a script that fixes this issue here:

[http://firefang.net/english/converting-cvsnt-repository-format-to-cvs-repository-format](http://firefang.net/english/converting-cvsnt-repository-format-to-cvs-repository-format)
```

find . -not -name “*,v.bak” -exec grep -q “kopt.*b” \{\} \; -not -exec grep -q “expand.*@b@;” \{\} \; -print0 | xargs -0 -i sh -c “echo conv {};cp \”{}\” \”{}.bak\”;cat \”{}.bak\” | sed 2a\”expand @b@;\” > \”{}\”"
```

the script doesn't seem to work though - if i put it into a separate shell script, I get 

./cvsfix.sh: line 3: unexpected EOF while looking for matching `"'
./cvsfix.sh: line 4: syntax error: unexpected end of file

I honestly have no idea what this script does and how it works, so any help would be appreciated.

---

### Post by SupaSonic on 2007-12-11
Never mind, it seems that if I copy that string to the shell some of the double-quotes and back slashes get removed.

---

