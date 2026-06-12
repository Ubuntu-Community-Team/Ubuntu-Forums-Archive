---
title: "Batch text editing in a shell"
date: 2009-10-01
forum: Programming Talk
---

### Post by drklepto on 2009-10-01
Hi,
I need to perform an operation on a quite big file.
It's organized as this example:

extra-sounds-en.txt
```
conf-enteringno: You are entering conference number
conf-errormenu: Invalid Choice
conf-extended: The conference has been extended.
```

(asterisk voice prompts)

I need to split it in multiple files named with the string preceding ":" and with the last part of the string as content.

conf-enteringno.txt
```
Invalid Choice
```

conf-errormenu.txt
```
This call may be
```

conf-extended.txt
```
The conference has been extended.
```

Anyone knows the mythologic bash-regexp-sed-awk-etc.etc secrets? :D
I'm not that good in that field...

Many thanks for your help!

*kLe*

[SIZE="1"]For anybody curious: I need this to create a full set of asterisk voice prompts on my own language, by using a TTS engine.[/SIZE]

---

### Post by scragar on 2009-10-01
```
#!/bin/bash

mkdir -p "$2" || {
  echo "Unable to create directory and directory doesn't exist."
  exit 1
}

cat $1 | while read line;
do
  echo "${line#*:}" > "$2/${line%:*}.txt"  
done
```
Will need testing.

USAGE:
```
## first make it executable:
chmod +x myscript.sh

## then run it:
./myscript.sh inputfile.txt outputDir
```

---

### Post by drklepto on 2009-10-01
Many thanks for your quick reply!
Unluckily it didn't work. It split file in multiple "sub-files" but it left them empty.

This is the big-file' content:
[http://pastebin.com/m50da4829](http://pastebin.com/m50da4829)

---

### Post by scragar on 2009-10-01
My code wouldn't work with the /'s anyway, even if the code does work. You should have warned me about that first as well.

My error was simply forgetting to change a variable name from my test version to the version I posted here(my test version used "foo", "bar" and "meap" as variable names, not very nice, but efficient for testing :p). I've updated that old post now, but it still won't work with /s as directories, I'll think of a way to handle that and post back in a bit.

---

### Post by scragar on 2009-10-01
```
#!/bin/bash

mkdir -p "$2" || {
  echo "Unable to create directory and directory doesn't exist."
  exit 1
}

cat $1 | while read line;
do
  mkdir -p $(dirname "$2/${line%:*}.txt")
  echo "${line#*:}" > "$2/${line%:*}.txt"  
done
```
Easy edit now that I think about it, just make the directory if we can for every file name we output, not very efficient, but for the file size you've listed it's nothing really.

Attached is the finished output of running:
```
./script.sh input .
```

---

### Post by drklepto on 2009-10-01
I haven't test them yet. But work them or not.. Thank you very much!
You have been very kind to post a possible solution to my own problem!

I'll let you know later! :P

---

### Post by drklepto on 2009-10-01
Worked as a charm!! :)

I made a tiny modification so it stripped away the "space" after ":"

```
#!/bin/bash

mkdir -p "$2" || {
  echo "Unable to create directory and directory doesn't exist."
  exit 1
}

cat $1 | while read line;
do
  mkdir -p $(dirname "$2/${line%:*}.txt")
  echo "${line#*: }" > "$2/${line%:*}.txt"  
done
```

10x a lot!! :guitar:

---

