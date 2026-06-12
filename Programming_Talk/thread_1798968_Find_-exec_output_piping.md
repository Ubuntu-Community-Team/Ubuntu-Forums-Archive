---
title: "Find -exec output piping"
date: 2011-07-06
forum: Programming Talk
---

### Post by DCM36 on 2011-07-06
I'm trying to do something similar to the following, but haven't quite figured out the correct syntax
```
find . -print -exec python ./pescanner.py {} | tee ./reports/{}.txt \;
```

What I'm wanting to do is:
Use find to find all the files in the current directory
Run the pescanner.py python script against each file, which outputs its findings to the terminal/STDOUT
Output the pescanner.py findings to individual text files in the reports subdirectory

Thanks for any help/suggestions

---

### Post by pafoo on 2011-07-06
for loop is better for that, try this on the command line cd to current directory

```

for item in $(ls .); do /home/pythonscanner.py /home/$item | tee /home/reports/$item; done

```

make sure to use absolute path

also in your python script if you add on the first list #!/usr/bin/python you dont have to use python to run the python script.

---

### Post by DCM36 on 2011-07-06
> **pafoo said:**
> for loop is better for that, try this on the command line cd to current directory

```

for item in $(ls .); do /home/pythonscanner.py /home/$item | tee /home/reports/$item; done

```

make sure to use absolute path

also in your python script if you add on the first list #!/usr/bin/python you dont have to use python to run the python script.

That does work as expected, however is there a way to get things to work recursively? It does run the python script against each file recursively, however the tee report output only ends up in the name of the parent folder.

Example of setup/what happens:

Folder_A
[INDENT]file_a[/INDENT]
[INDENT]file_b[/INDENT]
Folder_B
[INDENT]file_c[/INDENT]
[INDENT]file_d[/INDENT]

Will output to reports with folder_a.txt and folder_b.txt with the results of the python output from file_b and file_d respectively since tee isn't appending

---

### Post by pafoo on 2011-07-06
use tee -a to append. Im not really sure what you mean it puts the text only in the parent directory. Cut and paste what you did.

---

