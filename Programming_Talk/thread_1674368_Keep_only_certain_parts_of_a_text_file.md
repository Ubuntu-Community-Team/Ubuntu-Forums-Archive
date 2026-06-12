---
title: "Keep only certain parts of a text file"
date: 2011-01-23
forum: Programming Talk
---

### Post by bcooperizcool on 2011-01-23
Ok, you were very helpful with my last question, (I think this ok to post as a new topic...), but how do I keep certain parts of a text file?   Eg.
```

/var/mobile/Applications/324-sfdg/App.app
/var/mobile/Applications/324-sfdg/App.app/blah.extension
/var/mobile/Applications/324-sfdg/App.app/icon.png
/var/mobile/Applications/dsfg-234/OtherApp.app/
/var/mobile/Applications/dsfg-234/OtherApp.app/title.png
/var/mobile/Applications/dsfg-234/OtherApp.app/idk.extension

```
I want to only keep the lines that begin with "/var/mobile/Applications" and end with ".app".   How would I do this?   (this will be inside a bash script)  Also would be nice to remove the extra lines.  

Thanks again for all your help so far!   :D

---

### Post by worksofcraft on 2011-01-23
> **bcooperizcool said:**
> ...
I want to only keep the lines that begin with "/var/mobile/Applications" and end with ".app".   How would I do this?   (this will be inside a bash script)  Also would be nice to remove the extra lines.  

Thanks again for all your help so far!   :D

can you not use grep for this ?
something like:
```
 grep "/var*.app" 
```

---

### Post by bcooperizcool on 2011-01-23
How would I use that for my text file?
```

grep "/var*.app" < file.txt > newfile.txt

```
?
or am I missing something?
Thanks!

---

### Post by worksofcraft on 2011-01-23
> **bcooperizcool said:**
> How would I use that for my text file?
```

grep "/var*.app" < file.txt > newfile.txt

```
?
or am I missing something?
Thanks!

You could do it that way.
You can also use sed.

Actually my regular expression there isn't quite right... you wanted to have the /var at the beginning of line and the .app at the end so it be more like:
```

grep "^/var/mobile/Application.*\.app$" file.txt > newfile.txt

```
^ means beginning of line
$ means end of line
. means anything
* means any number of times
\. means .

hope that helps :)

---

### Post by bcooperizcool on 2011-01-23
Thank you!  :D  (The explanation helped as well).
How can you do that with sed?   I know how to remove, but not keep.

---

### Post by ghostdog74 on 2011-01-23
> **bcooperizcool said:**
> Thank you!  :D  (The explanation helped as well).
How can you do that with sed?   I know how to remove, but not keep.

there are many other ways to do it

awk
```

awk '/^\/var\/mobile\/Application.*\.app$/' file

```

sed
```

sed -n '/^\/var\/mobile\/Application.*\.app$/p' file

```

ruby
```

ruby -ne 'print if /^\/var\/mobile\/Application.*\.app$/' file

```

even just using the bash shell(3.2++)

```

while read -r line
do  
 if [[ $line =~ "^\/var\/mobile\/Application.*\.app$" ]];then   
  echo $line; 
 fi
done < file

```

---

### Post by bcooperizcool on 2011-01-23
Thanks!  I think that covers it for this question!  Until my next question, thanks!

---

### Post by worksofcraft on 2011-01-23
> **bcooperizcool said:**
> Thanks!  I think that covers it for this question!  Until my next question, thanks!

YW :)
but don't forget to use "thread tools" to mark the thread as solved ;)

---

