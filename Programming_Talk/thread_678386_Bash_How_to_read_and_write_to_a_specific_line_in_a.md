---
title: "Bash: How to read and write to a specific line in a file?"
date: 2008-01-25
forum: Programming Talk
---

### Post by Kevuntu on 2008-01-25
How to read and write to a specific line in a file from a bash script?

-Thanks in advance!

---

### Post by ghostdog74 on 2008-01-25
various ways, 
1) while loop + echo/printf
2) awk
3) sed

etc

---

### Post by Kevuntu on 2008-01-25
Could you clarify this a little?
Examples would help a lot.

---

### Post by ghostdog74 on 2008-01-25
first you can help me by showing some examples of what you want to do. show a sample input file, and your expected output what will it look like.
Then after that, you can start reading up some material for scripting. see my sig.

---

### Post by chandra on 2008-01-25
> **Kevuntu said:**
> How to read and write to a specific line in a file from a bash script?

-Thanks in advance!

This is a perl solution, not a bash one.

Let file.txt denote the **line-oriented** file you want to read from and write to. Let us further assume that you want to read line 5 from the file.

You can use perl to do this at the command line using
```
perl -wnl -e 'print if $. == 5;' file.txt
```
Writing to the file is complicated because you could be overwriting the records in the file. Suppose you wanted to substitute whatever is in line 6 with the text

The five boxing wizards jump quickly.

You can do this so:
```
perl -i.bak -wpl -e 's/$_/The five boxing wizards jump quickly./ if $. == 6;' file.txt
```
If you want this text to appear after line 5 but without overwriting what was
originally in line 6, try:
```
perl -i.bak -wpl -e 's/$_/$_\nThe five boxing wizards jump quickly./ if $. == 5;' file.txt
```
The -i.bak switch allows backing up of your original file in each case. Unless you give more details it is not helpful to explain further.

---

### Post by Kevuntu on 2008-01-26
I want to change this:
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection
```
into this:
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	[COLOR="Blue"]#[/COLOR]Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	[COLOR="Blue"]Option		"USB"		"on"[/COLOR]
EndSection
```

---

### Post by ghostdog74 on 2008-01-26
```

awk '/Section/,/EndSection/{
    if ($0 ~ /ForceDevice/ ) {
        print "#"$0
        print "Option        \"USB\"       \"on\""
    }else {
        print 
    }
}
' "file"

```
output:
```

# ./test.sh
Section "InputDevice"
    Driver      "wacom"
    Identifier  "cursor"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"      "cursor"
#    Option      "ForceDevice"   "ISDV4"     # Tablet PC ONLY
 Option        "USB"       "on"
EndSection


```

---

### Post by Apocalipssyss on 2008-01-28
Hi comunity. I have another one. Quit Similiar. How use you  sed or awk for replace, in this case option 3 o the second setting.

```
setting "1" {
     option1="123";
     option2="456";
     option3="789";
}

setting "2" {
     option1="123";
     option2="456";
     option3="789";
}
```

Your help will be apprecieted.

---

### Post by stroyan on 2008-01-28
Your description of the task leaves a lot to be assumed.  I made assumptions. ;-)
It is not clear how the input may vary and what the filter should do about variation.
This example code assumes that any line starting with 'setting' should control whether later lines should be modified.
If it sees a line that starts with 'setting' and has a second field of '"2"' then it will modify later lines containing 'option3'.
If it sees a line that starts with 'setting' and has a different second field then it will not modify later lines containing 'option3'.

The key mechanism here is to set an awk variable when matching a 'setting' line and test that variable when matching an 'option3' line.
The substitution matches the first to second instance of double quotes in a line.
The quotes that are being matched or inserted are quoted with backslashes.

```
awk '/^setting/{M=($2=="\"2\"")}/option3/{if (M) {sub("\"[^\"]*\"","\"new\"")}}{print}'
```

---

### Post by rendon on 2008-01-28
research "head" and/or "tail" at the command line

I'm not on my ubuntu machine at the moment, so I can't try it myself to be sure...

try something like:

head -2 <filename here>

that might print out the first two lines of the file...

I think head and tail would be the easiest to understand and use for the job your doing...

if you want to change:

value="123"

into:
value="234"

you can do something like:
sed -e s/value=\"123\"/value=\"234\"/

maybe :confused: .. again, I'm not at a linux machine at the moment

but anyway, I think you get the general idea, that general format is easy to use, you can play with it, or research it some more.

---

