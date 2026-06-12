---
title: "sed - replace string with file path"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by ibizatunes on 2012-12-03
Hello
I have been delivery a application that I need to redirect the logs files and some config file to a share nfs mount
i need to replace in the application config file
{/opt/acc1} to /mnt/acc1
I could do this by hand however i wanted to script it, as i have about 100server to do

```
 sed -i 's/opt/acc1//mnt/acc1//g'
```

however I get error sed -e not valid data set
Ive tried 
```
 sed -i 's/opt/acc1/'/mnt/acc1/'/g'
```
```
 sed -i 's/opt/acc1/"/mnt/acc1/"/g'
```
Please can you help

---

### Post by steeldriver on 2012-12-03
I think you will need to escape the forward slashes in the path - or use a different separator for the sed substitution

```
$ echo "/path/to/file" | sed 's/\/path\/to/\/new\/path/g'
/new/path/file
```or

```
$ echo "/path/to/file" | sed 's#/path/to#/new/path#g'
/new/path/file
```

Option (2) is easier to read imo

---

### Post by Impavidus on 2012-12-03
sed doesn't know which / is part of the search and replace command and which is part of your search string or replace string. Fortunately, you don't have to use the / in sed, it will accept other characters as well:```
sed s:/opt/acc1/:/mnt/acc1/: <input >output
```or whatever I/O way you want.

---

### Post by ibizatunes on 2012-12-03
Knew it was something simply
Cheers

---

