---
title: "sed question"
date: 2007-03-28
forum: Programming Talk
---

### Post by jackrobinson on 2007-03-28
Hi I am trying to write a sed one liner which will look for the following line in a file:
> action "record-stream" {
and replace the line following the above line (whatever it might be) with:
> *tab space followed by***command "x-terminal-emulator -e streamripper %q -d /home/jack/ripped -r -q";**
how can I do this?
Thanks in advance.
-Jack

---

### Post by bradleyd on 2007-03-28
this should work,
say there is file call sed.txt, in file is your text from your post.
action "record-stream" { hello
then at propmt type:
cat sed.txt | sed 's/action "record-stream" {/\tcommand "x-terminal-emulator -e streamripper %q -d \/home\/jack\/ripped -r -q";/g'
this produces:
```
       command "x-terminal-emulator -e streamripper %q -d /home/jack/ripped -r -q"; hello

```

---

### Post by jackrobinson on 2007-03-29
> **bradleyd said:**
> this should work,
say there is file call sed.txt, in file is your text from your post.
action "record-stream" { hello
then at propmt type:
cat sed.txt | sed 's/action "record-stream" {/\tcommand "x-terminal-emulator -e streamripper %q -d \/home\/jack\/ripped -r -q";/g'
this produces:
```
       command "x-terminal-emulator -e streamripper %q -d /home/jack/ripped -r -q"; hello

```

Hi thanks for the reply and help.. but this is not exactly what i wanted.
Let's say we have the following two lines in the file (among many other lines):
> action "record-stream" {
        command " ";
what i want sed to do is replace
> command " "; with the string I pasted, when it finds > action "record-stream" {
The operative point here is that > command" "; comes exactly on the next line after > action "record-stream" { and this is where > command " "; needs to be replaced.

With your code, it's replacing  
> action "record-stream" {
and keeping> 
command " ";


Hence it is appearing as follows:
>         command "x-terminal-emulator -e streamripper %q -d /home/jack/ripped -r -q";
        command " ";

---

### Post by WW on 2007-03-29
If you don't mind perl instead of sed:
```

perl -i.save -p -0 -e 's/(action "record-stream" {\n)(.*)\n/$1\t command "x-terminal-emulator -e streamripper \%q -d \/home\/jack\/ripped -r -q";\n/g'  filename

```
This will make the changes in filename.  A copy of the original will be saved in filename.save.

---

### Post by bradleyd on 2007-03-29
if you are still interested in sed this should be what you were looking for(as far as I can understand)
```
 cat sed.txt | sed -e '/action "record-stream" {/ a\  command "x-terminal-emulator -e streamripper %q -d \/home\/jack\/ripped -r -q";/' -e '/command "";/d'

```
not the most elegant but gets the job done. WW perl's one liner works great too.
B

---

