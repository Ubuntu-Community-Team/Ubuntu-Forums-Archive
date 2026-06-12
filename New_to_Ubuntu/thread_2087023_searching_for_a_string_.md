---
title: "searching for a string_"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by spillage2 on 2012-11-22
Hi,

I have had a look around but couldnt find any info. Can you use the terminal to search all files on my o/s for a string. I have setup ssmtp but am sure there is a .conf file lurking about with the wrong settings in and I need to find it.

I'm sure it would only be in /etc but not sure how to search all files in /etc for "a_word".

Thanks,

Spill.

---

### Post by spillage2 on 2012-11-22
should it just be ```
grep -R  name_of_string /directory
``` ????

spill.

---

### Post by Pletched on 2012-11-22
```
ls -a
```Shows all files and folders in the current directory.

```
ls -a | grep STRING
```Passes the output of ls to grep to search the current directory listing for STRING.

---

### Post by steeldriver on 2012-11-22
> **spillage2 said:**
> should it just be ```
grep -R  name_of_string /directory
``` ????

Should work fine - you might want to :

[LIST]
[*]do it with 'sudo' if you think the string may be in a file that is read-protected
[*]add '-I' to ignore binary files
[*]add -i to make the match case insensitive
[/LIST]
```
$ sudo grep -RIi name_of_string /etc
```If you don't want to / can't use 'sudo' you can send all the error messages to null to keep the output readable

 ```
$ grep -RIi name_of_string /etc 2>/dev/null
```

---

### Post by spillage2 on 2012-11-22
cheers but will this only look for file names and not a string within a document?

spill.

---

### Post by steeldriver on 2012-11-22
no, it will grep within each file recursively and highlight all the matches e.g.

```
$ grep -IRi WORKGROUP /etc 2>/dev/null
/etc/samba/smb.conf:# Change this to the workgroup/NT-domain name your Samba server will part of
/etc/samba/smb.conf:   workgroup = WORKGROUP
/etc/bash_completion.d/samba:        -W|--workgroup)
/etc/bash_completion.d/samba:            --log-basename --workgroup' -- "$cur" ) )
/etc/bash_completion.d/samba:            --username -p --password -w --workgroup -n --nonprompt -d \
```

---

### Post by spillage2 on 2012-11-22
thanks steeldriver you must of posted just as i uploaded my last post..

just tried and worked a treat...well it did but i'm still none the wiser..php(mail) I aint.

Spill.

---

### Post by Resistent on 2012-11-22
Very helpful. Thank you a lot!!
I have many txt files and I often don't know where to search.

---

