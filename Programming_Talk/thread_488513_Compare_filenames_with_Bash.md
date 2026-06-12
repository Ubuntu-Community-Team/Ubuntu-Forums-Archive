---
title: "Compare filenames with Bash"
date: 2007-06-30
forum: Programming Talk
---

### Post by Uuranor on 2007-06-30
Hi all people! :)

I'm having a little problem with a bash script, where I need to compare two filenames.
I want to know which of the two files has got the "smaller" name and I've done this script:

```
#!/bin/bash

test="blab"

for i in `find /home/ -name bla\*` ; do
	file=`basename $i`
	if [ $file < $test ] ; then rm $i
fi
done
```

but ... everytime the for loop reaches the if, console give me the result "blab: no file or directory".
Where do I do the wrong thing?

Thanks all :)

---

### Post by moma on 2007-06-30
Hello.
You must escape-protect the > and < characters. Otherwise shell will eat or misinterpret them.   Try:

if [ "$file" \< "$test" ] ; then rm $i;  fi 

I do not think the bash manual (or even [abs guide...]("http://tldp.org/LDP/abs/html/")) are very clear about this issue
$ man bash

I thought it's similar to the [math on the cli...]("http://home.online.no/~osmoma/RedHat9-apt-get.html#math_on_cli") exercise (some very old notes)

---

### Post by tillo on 2007-06-30
Just use the enchanced test bash version: [[ expression ]]

```

tillo@mctillo:~/uuranor$ cat uuranor.sh 
#!/bin/bash

test="blaII"

for i in $(find test/ -name 'bla*') ; do
        file=$(basename $i)
        echo -n '$i = ';
        echo $i;
        echo -n '$file = ';
        echo $file;
        if [[ "$file" < "$test" ]] ; then echo $i
fi
done
tillo@mctillo:~/uuranor$ ls test
blaI  blaII  blaIII
tillo@mctillo:~/uuranor$ ./uuranor.sh 
$i = test/blaIII
$file = blaIII
$i = test/blaI
$file = blaI
test/blaI
$i = test/blaII
$file = blaII
tillo@mctillo:~/uuranor$

```

---

### Post by robgr85 on 2007-06-30
> **Uuranor said:**
> Hi all people! :)

I'm having a little problem with a bash script, where I need to compare two filenames.
I want to know which of the two files has got the "smaller" name and I've done this script:

```
#!/bin/bash

test="blab"

for i in `find /home/ -name bla\*` ; do
	file=`basename $i`
	if [ $file < $test ] ; then rm $i
fi
done
```

but ... everytime the for loop reaches the if, console give me the result "blab: no file or directory".
Where do I do the wrong thing?

Thanks all :)
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

here You have basic comparison things for bash

Robert

---

### Post by bashologist on 2007-06-30
If by size you meant length then you could use this variable expansion:
```
i="blah"
x="blahblah"
printf "length of i: ${#i}\n"
printf "length of x: ${#x}\n"
```

---

