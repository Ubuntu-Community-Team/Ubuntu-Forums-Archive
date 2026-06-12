---
title: "supress error message"
date: 2014-05-28
forum: Programming Talk
---

### Post by peter_brickles on 2014-05-28
Im running a script i have written and the following line give me an error message and im not really sure why can any one help ? 

heres the line in the script that fires the error 

> cat title1 | perl -pi.back -e 'y/+/ /;s/%([\da-f]{2})/pack H2,$1/gie' |sed 's/_/ / g' | sed 's/....$//' > title_formated 



and heres the error 

> -i used with no filenames on the command line, reading from STDIN.



seems to me linke the sed command is the problem although i havnt used the i switch any help would be appreciated 

Pete

---

### Post by spjackson on 2014-05-28
```
[COLOR=#000000]perl -pi.back -e[/COLOR]
```
should just be
```
[COLOR=#000000]perl -e[/COLOR]
```[COLOR=#000000]
The warning message is because of -i.back which doesn't make sense when there are no files on the command line. Also -p doesn't make sense in the pipe context that you are using, but does no harm.

[/COLOR]

---

