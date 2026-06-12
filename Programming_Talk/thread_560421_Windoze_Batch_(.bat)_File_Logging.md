---
title: "Windoze Batch (.bat) File Logging"
date: 2007-09-26
forum: Programming Talk
---

### Post by lamar_air on 2007-09-26
I have a really large batch file that currently doesn't write output to a log file so I need to have it write output to a file.

Is there a way to log the output from a .bat file without putting ">> file.log" at the end of each echo line?

---

### Post by LaRoza on 2007-09-26
You can redirect the individual commands:

```

tree directory /F > log.txt

```

Double click, and it outputs the results into log.txt. You can redirect any command.

If your is more complex, have another bacth file call the other and do the redirection from there.

---

### Post by ghostdog74 on 2007-09-26
> **lamar_air said:**
> I have a really large batch file that currently doesn't write output to a log file so I need to have it write output to a file.

Is there a way to log the output from a .bat file without putting ">> file.log" at the end of each echo line?

say a.bat is your batch file, and inside is this code
```

echo "line1"
echo "line2"
.....
.....
echo "line100"

```

you do not have to put >> after every line in the above because you can simply do :
```

c:\> a.bat > out.txt

```

---

### Post by lamar_air on 2007-09-26
**LaRoza**, Can you explain a bit more what you're saying.  I don't know what exactly you mean??


Ghostdog74, I tried redirecting stdout but this batch file creates a child shell..  the redirection only gets what is outputted from the parent so that doesn't work unfortunately.

---

### Post by LaRoza on 2007-09-26
As I understand, you have a batch file that outputs text and you want that output in a file. If the bat file were using the tree command to list the directory structure, you could put IN the batch file:

```

tree directoryname /F > log.txt

```

(Run the tree command to see what it does, the /F add files to the output)

This would enable the user to double click the file and the log would automatically be filled (this would overwrite it, I think you would want to append, which I think >> does)


If this is not possible, you can write another batch file to call the original and output the results.

I am on Windows now, if you could, post a bit of the file so I can see exactly what you want.

---

