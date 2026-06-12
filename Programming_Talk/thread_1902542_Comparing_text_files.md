---
title: "Comparing text files"
date: 2011-12-31
forum: Programming Talk
---

### Post by MVFORLYFE on 2011-12-31
Hello,

I have two text files. They both contain a list of file names and hashes.
I wish to compare the file names and their respective hashes from file A against file B.
I only want to compare file names with the .jpg extension, so I think I have to use cut to extract the lines with .jpg in them before I can compare them against file b.

The command that was suggested to me was : 

cut -f 1 -d ' ' filea.txt > fileacut.txt
grep -v -f fileacut.txt fileb.txt

I'm guessing that somewhere in the cut command I have to insert the *.jpg extension but I'm not sure where it goes.

Any help is greatly appreciated, thank you.

---

### Post by squenson on 2011-12-31
Hello,

I would first create a file which will only contains the file names *.jpg and sort it by alphabetical order:
grep '.jpg' filea.txt | sort > fileacut.txt
grep '.jpg' fileb.txt | sort > filebcut.txt

Then I would compare the two files with diff:
diff -ac filacut.txt filebcut.txt

---

### Post by ofnuts on 2011-12-31
> **MVFORLYFE said:**
> Hello,

I have two text files. They both contain a list of file names and hashes.
I wish to compare the file names and their respective hashes from file A against file B.
I only want to compare file names with the .jpg extension, so I think I have to use cut to extract the lines with .jpg in them before I can compare them against file b.

The command that was suggested to me was : 

cut -f 1 -d ' ' filea.txt > fileacut.txt
grep -v -f fileacut.txt fileb.txt

I'm guessing that somewhere in the cut command I have to insert the *.jpg extension but I'm not sure where it goes.

Any help is greatly appreciated, thank you.
Typically you run one of the hash files directly against the files you want to check ("md5sum -c")

---

### Post by Lars Noodén on 2011-12-31
> **squenson said:**
> Hello,

I would first create a file which will only contains the file names *.jpg and sort it by alphabetical order:
grep '.jpg' filea.txt | sort > fileacut.txt
grep '.jpg' fileb.txt | sort > filebcut.txt

Then I would compare the two files with diff:
diff -ac filacut.txt filebcut.txt

You could also use [comm](http://manpages.ubuntu.com/manpages/oneiric/en/man1/comm.1.html) for the comparison.  It depends on the results you want to get.

---

