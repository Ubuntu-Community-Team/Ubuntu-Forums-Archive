---
title: "Can someone explain these bash variables"
date: 2009-05-12
forum: Programming Talk
---

### Post by akvino on 2009-05-12
export LC_ALL=C
export LANG=C


What does this do?


And then this - what is $(dirname $0) - ?

. $(dirname $0)/ocf-shellfuncs
. $(dirname $0)/utils/config-utils.sh
. $(dirname $0)/utils/messages.sh
. $(dirname $0)/utils/ra-skelet.sh

---

### Post by myle on 2009-05-12
I guess they are specific to your application.

$( ) is the equivalent of ` ` in a more "modern" way. It is command substitution, which means that the expression which is included, is evaluated and it is replaced by its result. Then, the whole expression (the initial statement, with $() replaced) is finally evaluated.

$0 refers to the name of your application/script

I hope I was helpful.

May google be with you.

---

### Post by lloyd_b on 2009-05-12
> **akvino said:**
> export LC_ALL=C
export LANG=C


What does this do?


And then this - what is $(dirname $0) - ?

. $(dirname $0)/ocf-shellfuncs
. $(dirname $0)/utils/config-utils.sh
. $(dirname $0)/utils/messages.sh
. $(dirname $0)/utils/ra-skelet.sh

The LC_ALL and LANG variables are what are most likely being set so that and scripts called by this script will have them.  For instance, setting LANG=C in this script may hit a test in a later script such as:```
if [ "$LANG" == "C" ]; then
   ...
elif [ "$LANG" = "PYTHON" ]; then
   ...
fi
```

The $(dirname $0) pulls the command that started this script, and extracts the directory name from it.  That way, regardless if you run this as "./script" or "/home/user/bin/script", it knows what directory the script is in, and can then execute the other 4 scripts correctly.

Lloyd B.

---

### Post by Arndt on 2009-05-13
> **lloyd_b said:**
> The LC_ALL and LANG variables are what are most likely being set so that and scripts called by this script will have them.  For instance, setting LANG=C in this script may hit a test in a later script such as:```
if [ "$LANG" == "C" ]; then
   ...
elif [ "$LANG" = "PYTHON" ]; then
   ...
fi
```

The $(dirname $0) pulls the command that started this script, and extracts the directory name from it.  That way, regardless if you run this as "./script" or "/home/user/bin/script", it knows what directory the script is in, and can then execute the other 4 scripts correctly.

Lloyd B.

LANG and LC_ALL have to do with "locales"; i.e. telling the programs how to behave in a particular cultural/language environment. See the man pages locale(5), locale(1) and setlocale(3), for example.

"C" is the value for not specifying any particular language, but instead the environment that predated the locale concept; i.e., ASCII only, American date format, etc. I don't know why they chose "C" for this.

"PYTHON" won't occur.

---

### Post by akvino on 2009-05-13
Thank you all.:)

---

