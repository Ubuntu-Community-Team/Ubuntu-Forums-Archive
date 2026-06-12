---
title: "Bash question"
date: 2006-06-01
forum: Programming Talk
---

### Post by mdurham on 2006-06-01
Is there a way to stop the terminal window closing after it has run my script?
Thanks, Mike

---

### Post by Jussi Kukkonen on 2006-06-01
Could you describe your situation in more detail? Normally issuing a command in a terminal doesn't close the terminal...

---

### Post by mdurham on 2006-06-01
> Could you describe your situation in more detail? Normally issuing a command in a terminal doesn't close the terminal...

Sorry. I have an executable script that I double click to run. When it finishes, the terminal that it was running in closes. I'd like for it to hang around so that I can see if there were any errors, messages etc. The script is just a few lines of simple commands to rename and copy some files.
Thanks.

---

### Post by ketsugi on 2006-06-01
Maybe it'd be easier to pipe any potential error output into a Zenity info dialog?

---

### Post by Jussi Kukkonen on 2006-06-01
Maybe add 
```
read -p "Press any key..."
```
as the last line of the script?

---

### Post by yaaarrrgg on 2006-06-01
couldn't you add this the end of the script?

```

sleep 10;
echo "exiting"

```

---

### Post by Engnome on 2006-06-01
Open terminal drag the binary into terminal press enter.

---

### Post by mdurham on 2006-06-01
Thanks Jussi Kukkonen, that seems like a good solution. Thanks to the others too.

---

