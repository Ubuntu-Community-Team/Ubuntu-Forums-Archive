---
title: "bash script based on lsb-release"
date: 2017-05-22
forum: Programming Talk
---

### Post by Swiftjay on 2017-05-22
Hey guys,
I'm new to scripting and I'm trying to work on a script that will call out functions based on the version of ubuntu being run

What I have so far:

```

#!/bin/sh
version='lsb_release -sr'
#check for version of ubuntu
$version
if [ $version == '16.04' ]
then
    echo "Version of ubuntu is 16.04 running script"
elif [ $version == '14.04' ]
then
    echo "Version of ubuntu is 14.04 running script"
elif [ $version == '12.04' ]
then
    echo "Version of ubuntu is 12.04 running script"
fi

```

However the bash script just tells me it's too many arguments.  I'm most likely going about this the wrong way but happy for someone that knows better that can provide some tips.

---

### Post by steeldriver on 2017-05-22
```

version='lsb_release -sr'

```

just assigns the string value - if you want the result of the command (aka command substitution) you need

```

version=$(lsb_release -sr)

```

or the older deprecated equivalent using backticks

(as a matter of style, I'd suggest a case statement rather than a sequence of if... then clauses)

---

### Post by Swiftjay on 2017-05-22
steeldriver that case stuff is amazing, looked it up and re-did the script all seems to be working now

```

#!/bin/sh
version=$(lsb_release -sr)

#check for version of ubuntu


case $version in
16.04)
    echo "Version of ubuntu is 16.04 running script"
    ;;
14.04)
    echo "Version of Ubuntu is 14.04 running script"
    ;;
12.04)
    echo "Version of Ubuntu is 12.04 running script"
esac

```

Thanks alot

---

### Post by steeldriver on 2017-05-22
Looks good ;)

You could also add a "catch all" like

```

*)
      echo "Version unrecognized"
      ;;

```

Happy to help

---

