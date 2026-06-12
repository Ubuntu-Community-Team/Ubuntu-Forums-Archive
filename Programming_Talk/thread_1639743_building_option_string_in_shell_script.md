---
title: "building option string in shell script"
date: 2010-12-07
forum: Programming Talk
---

### Post by RocketRanger on 2010-12-07
Hi

I am trying to build a string of options to pass to rsync as part of a backup script. However when i try to do this:

rsync "$OPTION --delete --dry-run $SOURCE $DEST"

I get an error when running the script. If I echo that string and copy-paste the output it runs fine. If I build the option string beforehand like so:

OPTION="$OPTION --delete --dry-run $SOURCE $DEST";
rsync $OPTION

it also runs fine, so my question is how is this parsed in the script and what is the correct way of doing this?

---

### Post by yeleek on 2010-12-07
I use this in my script

```
PARAMS="-avP --delete --log-file=$LOGDIR$(date +%d-%b-%y).log" # rsync params
```

(LOGDIR obviously being another variable)

and its called via this

```
rsync $PARAMS $SOURCEDIR $TARGETDIR | $ZENITYPARAMS
```

---

### Post by RocketRanger on 2010-12-07
but thats just it. You are building the PARAMS string before you dereference it. That works for me too.

I'm curious about how the shell interprets strings and if it is possible to build it on the same line as the command is called.

---

### Post by yeleek on 2010-12-07
Build it the same time you reference it?  Why would you want to?  Makes for a messy experience the next time you want to update it.

---

### Post by RocketRanger on 2010-12-07
Why? Habit from PHP I guess.

Every time I try to get my hands dirty with shell scripting it strikes me how completely different it is from every other language I have tried but it is just so useful. So now I am really trying to "get it" and string parsing is definitely one of the unfamiliar areas. Also it as an area thats hard to ask google about as it just throws up pages about basic string syntax.

I can make it work and your answer does have merit in clarity, so I have no problem using it. I just got curious about strings.

---

### Post by yeleek on 2010-12-07
I don't think its best for easy to read/modify code, but try messing around with this

```
var="hello mum", echo $var
```

so for example

```
ben@WOPR:~$ OPTION="--delete --dry-run $SOURCE $DEST", echo $OPTION
--delete --dry-run
```

---

