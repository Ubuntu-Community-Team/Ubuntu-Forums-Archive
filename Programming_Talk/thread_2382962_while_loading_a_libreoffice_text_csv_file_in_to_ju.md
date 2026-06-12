---
title: "while loading a libreoffice text csv file in to jupyter notebook got errors"
date: 2018-01-19
forum: Programming Talk
---

### Post by vincent727 on 2018-01-19
while loading a libreoffice text csv file to jupyter notebook using Pandas I got an IOError as below. I am not sure if text csv can be read like an excel csv file? If not, how to solve this problem since excel cannot be used in ubuntu???

Kindly help! thanks!



```
IOError: File root/home/vincent/Documents/ru000-180118.csv does not exist
```

---

### Post by ajgreeny on 2018-01-19
As far as I'm aware a .csv file should be the same wherever it came from.
However I suspect that pathway (where did that come from?) **root/home/vincent/Documents/ru000-180118.csv** is the problem and should be corrected to **/home/vincent/Documents/ru000-180118.csv**.

PS:
What is Pandas and jupyter?  The more detail you give us the more likely you are to get a useful answer.

---

### Post by vincent727 on 2018-01-19
> **ajgreeny said:**
> As far as I'm aware a .csv file should be the same wherever it came from.
However I suspect that pathway (where did that come from?) root/home/vincent/Documents/ru000-180118.csv is the problem and should be corrected to /home/vincent/Documents/ru000-180118.csv.

PS:
What is Pandas and jupyter?  The more detail you give us the more likely you are to get a useful answer.

pandas is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language.

Jupyter Notebook is an open-source web application that allows creating and sharing documents that contain live code, equations, visualizations and narrative text.


In the beginning I tried with /home/vincent/Documents/ru000-180118.csv but did not work.  It showed pathway error. after I changed to root/home/vincent/Documents/ru000-180118.csv the error became IOError as shown in my first post. I will attach a full pic for reference.

---

### Post by vasa1 on 2018-01-19
What does```
locate ru000-180118.csv
```show you?

---

### Post by vincent727 on 2018-01-19
> **vasa1 said:**
> What does```
locate ru000-180118.csv
```show you?


vincent@vincent:~$ locate ru000-180118.csv
/home/vincent/.config/libreoffice/4/user/backup/ru000-180118.csv_0.ods
/home/vincent/.local/share/Trash/files/ru000-180118.csv
/home/vincent/.local/share/Trash/info/ru000-180118.csv.trashinfo
/home/vincent/Documents/.~lock.ru000-180118.csv#
/home/vincent/Documents/ru000-180118.csv
vincent@vincent:~$

---

### Post by SeijiSensei on 2018-01-19
Try removing the lock file: /home/vincent/Documents/.~lock.ru000-180118.csv#

Any better?

Make sure you close all instances of LibreOffice before this.

---

### Post by vasa1 on 2018-01-20
> **SeijiSensei said:**
> Try removing the lock file: /home/vincent/Documents/.~lock.ru000-180118.csv#

Any better?

Make sure you close all instances of LibreOffice before this.
Normally, a lock file is created when a file is opened in LibreOffice. Once LibreOffice is closed, the lock file goes away.

---

### Post by vincent727 on 2018-01-20
> **SeijiSensei said:**
> Try removing the lock file: /home/vincent/Documents/.~lock.ru000-180118.csv#

Any better?

Make sure you close all instances of LibreOffice before this.

How can I find this lock file?
I tried to remove this file in *Documents* directory with code
```
rm .~lock.ru000-180118.csv#
``` but created > rm: cannot remove '.~lock.ru000-180118.csv#': No such file or directory

---

### Post by vincent727 on 2018-01-20
> **vasa1 said:**
> Normally, a lock file is created when a file is opened in LibreOffice. Once LibreOffice is closed, the lock file goes away.


I already closed Libreoffice but don't understand why the lock file still exists.

---

### Post by vasa1 on 2018-01-20
Then, as SeijiSensei suggested, see if deleting it helps with your issue.

---

### Post by SeijiSensei on 2018-01-20
> **vincent727 said:**
> How can I find this lock file?
I tried to remove this file in *Documents* directory with code
```
rm .~lock.ru000-180118.csv#
```

Run 

```
ls -a /home/vincent/Documents
```

Is it still there?  If so, try wrapping the file name in single quotes like this:

```
rm -f '/home/vincent/Documents/.~lock.ru000-180118.csv#'
```

The hash mark at the end has a special meaning in the bash shell; it denotes the beginning of a comment.  Encasing the string in single quotes tells bash to treat the string literally and ignore any special meaning it might otherwise assign to the characters.

---

### Post by vincent727 on 2018-01-20
> **SeijiSensei said:**
> Run 

```
ls -a /home/vincent/Documents
```

Is it still there?  If so, try wrapping the file name in single quotes like this:

```
rm -f '/home/vincent/Documents/.~lock.ru000-180118.csv#'
```

The hash mark at the end has a special meaning in the bash shell; it denotes the beginning of a comment.  Encasing the string in single quotes tells bash to treat the string literally and ignore any special meaning it might otherwise assign to the characters.

After running ```
ls -a /home/vincent/Documents
``` , file **.~lock.ru000-180118.csv# **is no longer there in the directory.  I re-run the ```
locate .ru000-180118.csv
``` and got below outcome. > /home/vincent/Documents/ru000-180118.csv

That is to say, the lock file already disappears.

I tried running the codes again in Jupyter Notebook:
```
import pandas as pd
```
```
ru000 = pd.read_csv("home/vincent/Documents/ru000-180118.csv")
```

I still got the same error: 
> [COLOR=darkred]IOError[/COLOR][COLOR=steelblue]: File home/vincent/Documents/ru000-180118.csv does not exist[/COLOR]

---

### Post by spjackson on 2018-01-21
home/vincent/Documents/ru000-180118.csv is not /home/vincent/Documents/ru000-180118.csv. Try
```

ru000 = pd.read_csv("/home/vincent/Documents/ru000-180118.csv")

```

---

### Post by vincent727 on 2018-01-21
> **spjackson said:**
> home/vincent/Documents/ru000-180118.csv is not /home/vincent/Documents/ru000-180118.csv. Try
```

ru000 = pd.read_csv("/home/vincent/Documents/ru000-180118.csv")

```

It worked!
Thanks you very much, Spjackson! I am still new to ubuntu and sometime it is a little confusing to me for even simple small issue.

BTW, thank all guys who have helped me with this issue.

---

### Post by vincent727 on 2018-01-21
Well, I tried pandas reading other several .csv files into jupyter notebook and got exactly the same error!
Checked again and again and I am sure the path is correct, the files are surely there in the designated folder......

It seems ubuntu is not as friendly in handling .csv spreadsheet with pandas as Windows system. I looked up in the web but could not find a solution for this. Wondering if there is an alternative way to import the .csv spreadsheet with pandas in ubuntu?

---

