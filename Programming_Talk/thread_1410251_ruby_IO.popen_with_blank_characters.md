---
title: "ruby IO.popen with blank characters"
date: 2010-02-18
forum: Programming Talk
---

### Post by christoforever on 2010-02-18
basically trying to start a process with io.popen. the directory where the program can start from is user chosen ... so we may have something like c:/program/bin or something like c:/documents and settings/program/bin. Of course the program starts when there is no space but chokes when the path has spaces ... I've tried escaping the spaces and I've tried putting \s in the spaces but nothing. I've also tried putting the argument in quotes but nothing... what should I do?

---

### Post by christoforever on 2010-02-19
I've solved the problem. I put the entire string in quotes like so  
```

IO.popen("\"#{path.to.dir}/bin/exec.exe #{path.to.options}\"")

```

when I should have done this
```

IO.popen("\"#{path.to.dir}/bin/exec.exe\" \"#{path.to.options}\"")

```

it's a noob error for sure ... but it was a busy day and I didn't catch it until the following morning ;) So for anyone coming across this post remember to put any arguments which have spaces in the filepath in quotes. Not the whole string but each argument.

---

