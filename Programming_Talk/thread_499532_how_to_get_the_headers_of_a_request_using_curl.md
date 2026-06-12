---
title: "how to get the headers of a request using curl?"
date: 2007-07-12
forum: Programming Talk
---

### Post by pedrotuga on 2007-07-12
I think this is the most apropriate section, if not mods please move this topic.

I want to get the headers in a comand line so i can see them clearly.

Aparently curl is a bit weird with the way it outputs data

if I...
```
curl -i url > file
``` it doesn't save anything in the file, i wonder why.

anyway, i found this solution:
```
curl -D file url
```
that saves the headers in the file, that's ok, but how do i get them outputed in the command line itself so i can see them imediatly?

EDIT
Ok... i red the man page more carefully

The solution is:
```
curl -I http://ubuntuforums.org
```

---

