---
title: "Detect --help in a shell scripts"
date: 2010-07-21
forum: Programming Talk
---

### Post by lorderico on 2010-07-21
Hi,

I'm having trouble finding the way to detect --help using getopts in shell script.  Can I get a pointer?

Thanks,
Eric

---

### Post by dwhitney67 on 2010-07-21
Try the following to see if it meets your requirements:
```

#!/bin/bash

set -e

function help()
{
   echo "All good questions deserve a good answer."
}

function usage()
{
   echo "Usage: `basename $0` [-h | --help]"
   exit 1
}


# script body
#
OPTS=`getopt -n $0 -o -h --long help -- $@`

eval set -- "$OPTS"

while true
do
        case "$1" in
                -h|--help)  help; shift ;;
                --)         shift ; break ;;
                *)          usage;  break;;
        esac
done

# continue with script...

```

---

