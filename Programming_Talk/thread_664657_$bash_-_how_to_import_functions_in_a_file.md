---
title: "$bash - how to import functions in a file"
date: 2008-01-11
forum: Programming Talk
---

### Post by kutlu on 2008-01-11
I am preparing some bash scripts.

I want to put all of my functions in one file, and &#305; want to call them from another file. 
How can I import another files' functions?

Up to now, I created all programming parts as separate files. but I am getting bored of a lot of file which include only a few lines.

Second wish: Do you have a link or book which talks about data and function scope in bash?

---

### Post by rrwo on 2008-01-11
Try this:

```

somefunc() {
 ...
}

export -f somefunc()

```

---

### Post by Keith Hedger on 2008-01-11
use: ```

. /path/to/functions

```
at the front of your main script (after the #!/bin/bash)
the dot (in bash) is the same as the include directive in c, you don't have to export the functions as the file will be included in the main script, dont miss the space betwwen the dot and the filename

---

### Post by kutlu on 2008-01-11
> **Keith Hedger said:**
> use: ```

. /path/to/functions

```
at the front of your main script (after the #!/bin/bash)
the dot (in bash) is the same as the include directive in c, you don't have to export the functions as the file will be included in the main script, dont miss the space betwwen the dot and the filename

thanks, it helped a lot.

---

### Post by qglenn on 2009-03-06
This was helpful. Here are a couple of bash custom functions I often use:


```
#usage: consoleLog 'Hello World'
consoleLog()
{
    echo '['$(date +'%a %Y-%m-%d %H:%M:%S %z')']' $1
}

#usage: 
#setValue 'Enter something' 'defaultValue'
#VAR=$NEW_VALUE
setValue()
{
    read -p "$1 ("$2"): " NEW_VALUE
    if [ -z $NEW_VALUE ]; then
        NEW_VALUE=$2
    fi
}
```

---

### Post by pooryorick2 on 2010-03-19
Here's a bash function I wrote to allow me to "import" functions and assign them to pseudo namespaces using prefixes:

[http://www.ynform.org/w/Pub/BashShimport](http://www.ynform.org/w/Pub/BashShimport)

caveat:  this works well for functions, but there is still only one global namespace -- no script-level namespace like Python's

---

### Post by cubeist on 2010-03-19
you can create a file of frequently used variable, functions, etc in a ".cfg" file and then at the top of your script include one of these lines... they all do the same thing!
```
. $HOME/prefs.cfg
```
```
$include $HOME/prefs.cfg
```
```
source $HOME/prefs.cfg
```

I found this solution in the "Bash Cookbook" (Albing, Vossen, & Newham)...every bash scripter should have a copy of this book within each reach!

---

