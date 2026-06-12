---
title: "pausing BASH script while file open in editor"
date: 2017-04-26
forum: Programming Talk
---

### Post by dwlamb on 2017-04-26
I have literally dozens of xml files to modify so they can be imported to a spreadsheet.  It is important they keep the time stamp as is.  

I am trying to devise a single line command that will: 
[LIST=1]
[*]touch a reference file 
[*]open the xml file in sublime 
[*]pause while the file is edited in sublime 
[*]touch using the reference file to set the time stamp back to the original 
[/LIST]

This is what I have tried
```

touch -r sms-20170102021429.xml sms-20170102021429.xml.REF && \
sublime sms-20170102021429.xml && \
touch -r sms-20170102021429.xml.REF sms-20170102021429.xml

```

However, this command does not pause to wait on exiting sublime before executing the third line.

Is there a simple solution?

---

### Post by Rocket2DMn on 2017-04-26
You could introduce a simple loop after calling sublime wait for the process, e.g.
```

while [ -n "`pgrep subl`" ]; do :; done

```
You could certainly come up with other conditions for the while loop as well, checking for a PID for "subl" is really a hack as it assumes there will only be one match and that it's for the previous command.

---

### Post by Pinoy Tux on 2017-04-28
```
wait
```

---

### Post by Rocket2DMn on 2017-04-28
> **Pinoy Tux said:**
> ```
wait
```

I did of course try to use the wait command, but sublime appeared to fork a new process in a new shell rather than just in the background.  I suspect this is why the OP was having trouble and why I presented a more hacky solution.  However, if he finds that using wait does work, then of course that seems preferable.

When I ran "wait", nothing happend.  If i try something like
```

wait `pgrep subl`

```
I get
> 
bash: wait: pid 17900 is not a child of this shell


---

### Post by dwlamb on 2017-04-28
Thank you Rocket2DMn and Pinoy Tux for your input.

Using wait had  no effect. The commands either as a script or ampersand separated at a  prompt as in the original post to this thread and there was no wait  after sublime was opened.

For efficient use of time to get these  logs in a spreadsheet I mirrored the sub-directory (logs) to another  sub-directory (logs.BK) and ran 
```

for i in sms-*.xml ; do touch -r sms-logs.BK/$i ./$i ; done

```

Running that after any time I edit now or in the future ensures the time stamps will be maintained

---

### Post by Olav on 2017-05-06
> **dwlamb said:**
> Is there a simple solution?
Yes, don't use Sublime (or I guess any GUI text editor). Use vi or nano or another console based editor. Your script should automatically wait until the editor is closed.

If it is always the same edit you must perform, you can probably automate that as well, see: sed, awk etc.

---

