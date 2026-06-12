---
title: "Issue with a bash script on Ubuntu 12.10"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by AlphaBugaboo on 2013-06-24
Hi Everyone,

I have copied pasted a bash script called new_script from   [http://linuxcommand.org/lc3_new_script.php](http://linuxcommand.org/lc3_new_script.php) . I am not sure what I did wrong but whenever I try to run the script I get an error write_function not found. 

```
AlphaBugaboo@Zeus 521$ ./new_script
Enter script output filename: e
Enter purpose of script: e
Include GPL license header [y/n]? > n
Does this script require superuser privileges [y/n]? > n
Does this script support command-line options [y/n]? > n
+ [[ -n e ]]
+ write_script
./new_script: line 360: write_script: command not found
+ chmod +x e
+ set +x

```


I can clearly see the write_script present in the script file. Can anyone please help me figure this out?

I am attaching the file with this post

[ATTACH]244085[/ATTACH]

---

### Post by dshgna on 2013-06-24
A problem with permissions? Have you given the current user execution permissions of new_script?

---

### Post by MidnightGrey on 2013-06-24
Looking at your script file (new_script.sh).
Line 360 is: `write_script >"$script_filename"`
which is part of this if statement
```

if [[ $script_filename ]]; then # Write script to file
        write_script >"$script_filename"
        chmod +x "$script_filename"
else
        write_script # Write script to stdout
fi

```

which appears to be trying to call a function defined in your script here (edit: the //line comments added by me)
```

write_script() { //LINE 167
#############################################################################
# START SCRIPT TEMPLATE
#############################################################################
cat << _EOF_
#! $SCRIPT_SHELL
# ---------------------------------------------------------------------------
# $script_name - $script_purpose

# Copyright $YEAR, $AUTHOR $EMAIL_ADDRESS
$(insert_license)

# Usage: $script_name$usage_message

# Revision history:
# $DATE Created by $PROGNAME ver. $VERSION
# ---------------------------------------------------------------------------
.
.
.
$(insert_root_check)

# Parse command-line
$(insert_parser)

# Main logic

graceful_exit
_EOF_
#############################################################################
# END SCRIPT TEMPLATE
#############################################################################
} //LINE 223


```

Now why the function write_script isnt being called properly i havent figured out yet.

---

### Post by MidnightGrey on 2013-06-24
Okay i found the issue, there is a syntax error at Line 104.
```

        _EOF_

```
needs to be changed to:

```

_EOF_

```

as in you need to remove all preceding spaces before the end of file tag.

---

