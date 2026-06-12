---
title: "Find a shell script's location within the script?"
date: 2008-04-12
forum: Programming Talk
---

### Post by maybeway36 on 2008-04-12
Is there a way from inside a shell script to find out where the script is located (which folder it is in?)

---

### Post by chewearn on 2008-04-12
```
pwd
```

---

### Post by LaRoza on 2008-04-12
> **AstalaVista said:**
> ```
pwd
```

That will print the working directory, not the scripts location.

---

### Post by ghostdog74 on 2008-04-12
> **maybeway36 said:**
> Is there a way from inside a shell script to find out where the script is located (which folder it is in?)
you can try $0
eg
```

#!/bin/bash
scriptpath=$0
case $scriptpath in 
 ./*)  echo `pwd` ;;
  * )  dirname $scriptpath
esac

```

---

### Post by stroyan on 2008-04-12
Bash reports paths to the files it is running from in the BASH_SOURCE array.
You may want to use readlink to find the real path through symbolic links.
```

script_dir="$(dirname "$(readlink -f ${BASH_SOURCE[0]})")"

```

---

### Post by bennit on 2009-01-25
cd `dirname`; pwd

---

### Post by mangup on 2009-08-31
This one also works, though it's a bit lengthy:

# Function returns the full path to the current script.
# Example:
#   tmp=`currentscriptpath`
#   echo "path to current script is: "$tmp
currentscriptpath()
{
  local fullpath=`echo "$(readlink -f $0)"`
  local fullpath_length=`echo ${#fullpath}`
  local scriptname="$(basename $0)"
  local scriptname_length=`echo ${#scriptname}`
  local result_length=`echo $fullpath_length - $scriptname_length - 1 | bc`
  local result=`echo $fullpath | head -c $result_length`
  echo $result
}

---

