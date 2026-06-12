---
title: "scripted rm fears"
date: 2008-07-06
forum: Programming Talk
---

### Post by surfdoc on 2008-07-06
Hi,

I'm wanting to add some automatic file deletion in to a bash script. All the files and directories I want to delete begin with $ or #. I was wondering if its as simple as:

rm -rf $*
rm -rf #*

however I wasn't sure whether these were special characters. I'm afraid I might delete more than I bargained for, so I haven't wanted to try my usual trial and "error" approach (The potential error around a line of script that looks rather like rm -rf * gives me the hebejebies). Can anyone give me some pointers on this?

Ta

---

### Post by CptPicard on 2008-07-06
$* means "all command line parameters" so yeah, that's a huge hole :)

---

### Post by nvteighen on 2008-07-06
> **surfdoc said:**
> 
(...) I'm afraid I might delete more than I bargained for, so I haven't wanted to try my usual trial and "error" approach (The potential error around a line of script that looks rather like rm -rf * gives me the hebejebies). (...)

For your tests, I think you could create a bunch of files inside of a directory **without write permissions**. If the script works, you'll get a "Permission denied" error, if it doesn't find the files, you'll get "File not found" instead. This way, you'll be safe from deleting something wrong... I guess... :p

---

### Post by LinuX-M@n1@k on 2008-07-06
I believe "\$*" and "\#*" would do the trick, but for more safety use nvteighen's advice.

Both $ and # are special characters:
$ - indicates the value the variable holds
# - comment
Correct me if I'm wrong.

[http://tldp.org/LDP/abs/html/special-chars.html](http://tldp.org/LDP/abs/html/special-chars.html)

---

### Post by surfdoc on 2008-07-06
Thanks guys - escaping the characters does seem like the obvious option. Still a little nervous tho. I suppose I could remove the -f and then it would prompt for each file ?

---

### Post by henchman on 2008-07-06
right-o :)

---

### Post by Can+~ on 2008-07-06
Use the [FONT="Courier New"]-i[/FONT] flag so it will prompt for every removal, thus, making sure you're not deleting anything important.

---

