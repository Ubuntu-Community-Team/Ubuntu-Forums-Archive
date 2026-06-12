---
title: "If/then scripting for sequential files"
date: 2007-09-27
forum: Programming Talk
---

### Post by 655 on 2007-09-27
Hi,

I have several numerically-named html files that I would like to convert to human-readable plaintext via the html2text command.  I would like the outputted txt files to inherit the numerical name of the source html files.  

As far as I see it, this requires some usage of the find command in a script, but I don't know how to do it.

In short: the source files are named like "1.html" through "1000.html," and I want to run the command:

html2text -style pretty -nobs -o *.txt *.html;

where *.html is the name of the source html and *.txt inherits this same name.  Unfortunately, I see no functionality in html2text for doing recursive or sequential output, so you can only do one file at a time via a single-line command.  The best I could come up with was to do a find for *.txt within the directory, and then route this to html2text via pipes or -exec, but again, html2text simply takes the first file encountered, outputs it, and then stalls. 

So, what kind of scripting wizardry do I need to employ in order to make it be that: where filename=*.html, execute html2text and output as filename*.txt ?

It's probably easily solved, but I don't know the first thing about shell scripting.  I will take this opportunity, with your assistance, as a chance to learn.

---

### Post by oerd on 2007-09-27
would this work for you?

```

for f in `ls YOUR_DIR`; do
    base=basename $f .html   #strips .html out of the contents of $f
    html2text -style pretty -nobs -o $base.txt $f
done

```

This will execute the html2text command for every file in your collection after basename has been used to strip off the filename ending we don't like ;)

---

### Post by 655 on 2007-09-27
Thanks for your reply.

I may be missing something here, but when I execute the script it prints the following:

```
./script: line 2: 93.html: command not found
./script: line 2: 94.html: command not found
./script: line 2: 95.html: command not found
./script: line 2: 96.html: command not found
./script: line 2: 97.html: command not found
./script: line 2: 98.html: command not found
./script: line 2: 99.html: command not found
./script: line 2: basename.txt: command not found

```This seems like a formatting issue.  Maybe i added a space too many in the script when I created it, or something?

I tried rearranging it a bit but to no avail.:confused:

---

### Post by ghostdog74 on 2007-09-27
> **oerd said:**
> 
```

for f in `ls YOUR_DIR`; do
....

```
;)
use the shell expansion instead
```

for f in YOURDIR/*
....

```

---

### Post by 655 on 2007-09-27
Now it's getting somewhere, but:
```
./script: line 2: syntax error near unexpected token `base=basename'
./script: line 2: `base=basename $f .html '

```
:(

---

### Post by DoktorSeven on 2007-09-27
base=`basename $f .html`

---

### Post by oerd on 2007-09-28
Yeah, I tend to forget the exact bash syntax this late at night. If you apply the suggestions though, there shouldn't be any problems. Right?

---

### Post by 655 on 2007-09-28
The final combination of
```
for f in YOURDIR/*; do
   base=`basename $f .html`   
   html2text -style pretty -nobs -o $base.txt $f
done
```worked.  Thank you oerd, ghostdog74, and DoktorSeven for your combined efforts!

This gave me some insight into the use of variables like this.  And I learned a new command: **basename.  **I'm already putting it to good use.
I should note that at the end it also produced some files named html.txt and basename.txt - which were easily removed, but it left me wondering why.

---

### Post by ghostdog74 on 2007-09-28
> **655 said:**
> 
```
for f in YOURDIR/*; do
   base=`basename $f .html`   
   html2text -style pretty -nobs -o $base.txt $f
done
```worked.  Thank you oerd, ghostdog74, and DoktorSeven for your combined efforts!

take note that if you have lots of files, using basename might be a performance drag because for every looping, the shell calls external process. since you want to get rid of .html, you might as well use bash shell internal functionality
eg
```

# var="test.html"
# echo ${var%%.html}
test
# filename=${var%%.html}
# echo $filename
test

```

---

