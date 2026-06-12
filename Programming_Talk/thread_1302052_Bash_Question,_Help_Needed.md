---
title: "Bash Question, Help Needed"
date: 2009-10-26
forum: Programming Talk
---

### Post by Xqtftqx on 2009-10-26
Hello, im working on a small bash script project. I need some help on doing the following task:

Say i have this in a file:
```

Name: John
Age: 54

Name: Jamie
Age: 53

Name: Kody
Age: 23

```

I know i can output all the names by doing "grep "Name:" File.txt

But How could i make my program output this:

```

Name: John, 54
Name: Jamie, 53
Name: Kody, 23

```

Any Help would be appreciated thank you

---

### Post by MadCow108 on 2009-10-26
probably very stupid (but working) solution for that specific file format:
is missing error handling completely
```

#!/bin/bash
while read line
do
  name=`echo $line | sed -e "s/Name: \(.*\)/\1/"`
  read line
  age=`echo $line | sed -e "s/Age: \(.*\)/\1/"`
  read line
  echo "Name: $name, $age"
done < file.txt

```

---

### Post by diesch on 2009-10-26
```
echo "Name:" $(grep -A1 'Name: John' your_file.txt | cut -d: -f2)
```

edit: sorry, misread the question. Maybe it's still usefull ;-)

---

### Post by eightmillion on 2009-10-26
I'm not that great with awk, and there's probably a better way to do this, but this gets the job done.
```
awk '/^Name:/{name=$2}/^Age:/{age=$2; printf("Name: %s, %s\n", name,age)}' file.txt
```

---

### Post by ghostdog74 on 2009-10-26
```

awk -vRS="" -vOFS=" " '{$1=$1}1' file

```
output
```

$ ./shell.sh
Name: John Age: 54
Name: Jamie Age: 53
Name: Kody Age: 23


```

---

