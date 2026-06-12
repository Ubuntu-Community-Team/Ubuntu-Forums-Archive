---
title: "merging html files with wget"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by ubudabi on 2014-01-06
Hi all,

With the command:

```
wget -i list.txt --recursive --convert-links --page-requisites --html-extension --restrict-file-names=windows --no-clobber
```

I am able to get html files for each URL contained in list.txt. But what If want only one big html file for each URL?

I know that with **the option -O file** wget can merge files but how can I do it for each URL separately?

How can I use the **--domains** option in this case?


Thanks in advance.

---

### Post by varunendra on 2014-01-09
Welcome to Ubuntu Forums nickeforos !

By looking at the man page of wget, it seems there is no internal option in it to do what you want, and so you must **loop** the wget command on the URLs individually.

For example, assuming your URL list file contains one URL per line, you can run the following loop -
```
[COLOR="#FF0000"]**count=1**[/COLOR]; while read [COLOR="#800000"]URL[/COLOR]; do wget --recursive --convert-links --page-requisites --html-extension --restrict-file-names=windows --no-clobber -O [COLOR="#FF0000"]**file-$count**[/COLOR] "[COLOR="#800000"]$URL[/COLOR]"; let [COLOR="#FF0000"]**count**[/COLOR]=count+1; done **< [COLOR="#0000CD"]list.txt[/COLOR]**
```

The above code should merge each URL's corresponding data in "file-<the URL's line no. in the list file>", (e.g. file-1, file-2, file-3... etc.). If you need a more meaningful name for each file, a relevant function to do that can be included in the loop (along with a function to make sure no files are overwritten in case of duplicate names).

---

