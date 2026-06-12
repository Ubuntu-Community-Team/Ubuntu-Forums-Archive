---
title: "Msgbox in script"
date: 2009-10-15
forum: Programming Talk
---

### Post by jamesdcarroll on 2009-10-15
I installed an app (Oracle DB) that has a startup shell script. I only use the DB for development so I start it and stop it whenever I need to. The only thing is there's no indication when they are done. 

I don't know bash (or is it dash?) scripting really, but is there a simple command that I can add to pop up a little "DONE" message box? Something akin to MsgBox "DONE" in VB?

Thanks,

---

### Post by BenAshton24 on 2009-10-15
You could use zenity:

```
zenity --info --text="Hello :)"
```

Hope this helps, Ben :)

---

### Post by jamesdcarroll on 2009-10-24
Works like a charm. One more quick question though: the script takes in two parameters.  How would I put those into message? 

Thanks again

---

### Post by internalkernel on 2009-10-24
> **jamesdcarroll said:**
> Works like a charm. One more quick question though: the script takes in two parameters.  How would I put those into message? 


I'm not sure exactly what you mean by parameters, but for a variable - maybe something like:

```
zenity --info --text="`echo $VAR1`"
```

or if you want the output of a command into the zenity dialog:

```
( mount -t /dev/sdb1 /media/disk-1;
echo "# Disk Successfully mounted" ) | zenity --info 
```

Zenity echoes the text of whatever follows #

---

### Post by jamesdcarroll on 2009-10-24
'Parameters' being defined as information passed into the script. For instance, the script (from the fine folks at Oracle) that I'm mangling takes two parameters: *action* and *target* to tell it what to do. For example:

**emctl start dbconsole** tells it to start up the dbconsole app while
**emctl stop dbconsole** tells it to shut it down. 

I was just looking to capture the parameters passed in for the message. Not that big a deal.

---

### Post by BenAshton24 on 2009-10-24
```
zenity --info --text="$1 $2"
```

$1 = Your First Param
$2 = 2nd

etc.

---

