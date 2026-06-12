---
title: "for loop through find results in sh script"
date: 2010-04-02
forum: Programming Talk
---

### Post by dirkraft on 2010-04-02
I've spent days on this now trying all kinds of things to get this for loop to work. My script is a bit more involved than this, but all my problems boil down to this.
```

dirkraft@ubuntu:~/Desktop/local$ find test/
test/
test/fileone
test/filetwo
dirkraft@ubuntu:~/Desktop/local$ cat printfiles.sh 
#!/bin/sh

IFS=$'\n'
for x in `find test/`
do
	echo "FILE"
	echo $x
done

dirkraft@ubuntu:~/Desktop/local$ ./printfiles.sh 
FILE
test/
test/fileo
FILE
e
test/filetwo
dirkraft@ubuntu:~/Desktop/local$

```

Output should have been very simple:
```

FILE
test/
FILE
test/fileone
FILE
test/filetwo

```

How can I loop over the results of a 'find' command?!

Thanks.

---

### Post by falconindy on 2010-04-02
```
while read line; do
  #do whatever with each line of the results
done < <(find test)
```

---

### Post by gmargo on 2010-04-02
It's apparently to do with the IFS setting.  While the $'\n' seems to work in bash, it does not seem to work in dash (aka sh).  Change IFS to the following and your script works:
```

IFS='\

'

```
Could also do with this way (I've just always used the above):
```

IFS='
'

```

---

### Post by dirkraft on 2010-04-02
Thanks to both for your replies.

I just tried this and can't believe that this is the only way to set IFS to a newline in a script.

Thanks again.

---

### Post by geirha on 2010-04-02
Iterating find output with for is error-prone and bad practice. See [http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020) and [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

In bash4 you can use globstar instead

```

shopt -s globstar
for file in test/**; do 
  echo "FILE: $file"
done

```

---

