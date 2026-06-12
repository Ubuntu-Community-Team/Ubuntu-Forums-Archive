---
title: "zenity help"
date: 2011-05-04
forum: Programming Talk
---

### Post by Binary-Synapse on 2011-05-04
Hello.
 
Can someone give me an example of how to modify the text color present in a question window when using **zenity**?
 
 
Something like...
zenity --title "My tytle" --question --text="How are you?"
 
But I wanted the string "**[COLOR=blue]How are you[/COLOR][COLOR=blue]?[/COLOR]**" in blue and bold (for example).
 
 
Thank you

---

### Post by kerry_s on 2011-05-04
it don't do that.

---

### Post by hakermania on 2011-05-04
You can use QtCreator and write simple C++ code in order to achieve this...

---

### Post by Binary-Synapse on 2011-05-04
Hello.
 
>  
You can use QtCreator and write simple C++ code in order to achieve this...

Yes... but I would prefer some simple script language, because the script will be run thousands of times (in Ubuntu machines), by different people and I want to give them the possibility to view / alter the code if necessary.
 
Is there any other command I can use in a BASH script to achieve the same thing?
Preferably without having to install additional pakages. That part is very important.
 
Thank you.

---

### Post by hakermania on 2011-05-04
No....There doesn't seem to exist something so specific like making text bold or changing font size with zenity...

---

### Post by zedixal on 2012-07-23
Hi,

maybe the answers to the OP question refer to a previous version of zenity; in zenity 3.2.0 you can format text using html - the html parser is quite basic, though.

A working example:

```

zenity --info --text \
"<span color=\"blue\"><b>How are you?</b></span>\n \
<span><i>Very</i> <u>well</u>, <s>and</s> <b>you</b>?</span>\n \
<span color=\"red\">Another</span> <span color=\"green\">color</span> <span color=\"blue\">test</span>\n \
<span font-family=\"serif\">Test</span> \
<span font-family=\"sans\">your</span> \
<span font-family=\"mono\">fonts</span>"

```

Credit to: [http://doc.ubuntu-fr.org/zenity](http://doc.ubuntu-fr.org/zenity)

---

### Post by Bachstelze on 2012-07-23
> **zedixal said:**
> 
maybe the answers to the OP question refer to a previous version of zenity;

You do realize this thread is over a year old, right?

---

### Post by zedixal on 2012-07-24
> You do realize this thread is over a year old, right?     Yeah, but HTML support has been there for *more* than a year (look at [this]("http://ubuntuforums.org/showthread.php?t=1250143#5") - 2009 :biggrin:)

However, someone should mark this thread as solved/closed

---

### Post by j3ff on 2012-12-18
> **Bachstelze said:**
> You do realize this thread is over a year old, right?

The age of the thread should never deter someone from replying.  I'm looking at this thread today because I want to alter the styles applied to text in a zenity dialog.  The new information is helpful.

---

### Post by zombifier25 on 2012-12-19
> **j3ff said:**
> The age of the thread should never deter someone from replying.  I'm looking at this thread today because I want to alter the styles applied to text in a zenity dialog.  The new information is helpful.

In most cases it should. Because
1. The OP may no longer be around.
2. Things may have changed a lot in the past years.
(I can probably think of more)
Moreover, the [Code of Conduct](http://ubuntuforums.org/index.php?page=policy) advise against it, so I'm expecting this thread to be locked any time soon.

---

### Post by rusta_tux on 2013-12-11
one year after:

These post was very useful for me, Thank you very much.

---

