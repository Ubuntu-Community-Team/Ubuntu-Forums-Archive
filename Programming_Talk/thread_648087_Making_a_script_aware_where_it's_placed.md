---
title: "Making a script aware where it's placed?"
date: 2007-12-23
forum: Programming Talk
---

### Post by Rizado on 2007-12-23
I'd like to make my bashscript launch where it's placed.
If the script is placed in /opt/merryChristmas and run from home (or anywhere else, like "bash /opt/merryChristmas/script") i'd like it to be run in /opt/merryChristmas anyway. I could of course start by "cd /opt/merryChristmas" but I wouldn't be able to move it around :/
I also want it to use /opt/merryChristmas even if I make a symlink of script into /usr/bin

Is this somehow possible?

---

### Post by Bachstelze on 2007-12-23
Hmm, could you explain what you mean by "run it in /opt/merryChristmas" ?

---

### Post by ebash on 2007-12-23
Try doing this at the beginning of your script:
```
cd "$(dirname '$0')"
```

$0 is a special variable that contains the path used to execute the script. By using the command 'dirname' you will obtain the folder where the script is.

---

### Post by winch on 2007-12-23
> **ebash said:**
> $0 is a special variable that contains the path used to execute the script.

The op wants the option of using a symlink in /usr/bin. When running the script via the symlink $0 will contain the path of the symlink.

---

### Post by Rizado on 2007-12-23
> **HymnToLife said:**
> Hmm, could you explain what you mean by "run it in /opt/merryChristmas" ?Well if a script were to echo something to a file like: "echo hello >> file" and I run it from home by /opt/merryChristmas/script it would put "file" in home, I want it in a relative path from the script like "merryChristmas/some/folders/and/output/file"

**ebash** thanks, not sure it's entirely what I'm looking for but I'll look into it after christmas :)

---

### Post by stroyan on 2007-12-23
You can get the directory containing the script file using```
script_dir="$(dirname "$(readlink -f ${BASH_SOURCE[0]})")"
```
The BASH_SOURCE variable is an array of the paths to the source file for each function in the bash function stack.
The "readlink -f" command finds the canonical path to a file, expanding symbolic links.
The "dirname" command removes the file name from the path to get the directory.

---

