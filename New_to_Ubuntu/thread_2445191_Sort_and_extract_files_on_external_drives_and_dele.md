---
title: "Sort and extract files on external drives and delete all folders"
date: 2020-06-10
forum: New to Ubuntu
---

### Post by bripoole on 2020-06-10
Hi

I want to find a script that automates a find and move action and sorts files into common file types and moves them to their corresponding folders labelled for example pdf's doc txt image etc etc

Anyone know how you do that?

I stupidly over the years backed up whole drives including system files

Ideally it would be great to be able to search for user created files only, but i have been told that is impossible?

---

### Post by TheFu on 2020-06-10
Yes, it is possible.  But we are here to help you, so post the beginnings of a bash script or python or perl or ruby ... We aren't a homework service.

Bash beginners guide: [https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)
35 'find' examples: [https://www.tecmint.com/35-practical-examples-of-linux-find-command/](https://www.tecmint.com/35-practical-examples-of-linux-find-command/)
Linux Command Explainer: [https://explainshell.com/](https://explainshell.com/)

If the files were in /media/old-disk-1 and I wanted them copied (always copy, don't move!!!!), then I'd do one type (say pdf) of file at a time.  /media/new-disk/PDFs  There are hundreds of assumptions in this line:

```
$ find /media/old-disk-1  -type f -iname \*pdf -exec cp {} /media/new-disk/PDFs \;
```

That will find all files ending in *pdf, case-INsensitive, copy them to /media/new-disk/PDFs/.  If there are any duplicate named files, the last one copied will remain.  If you want to keep the paths, then I'd use rsync.  Assuming no NTFS or FAT-whatever storage involved.  Those can break some find command options.  

I didn't use any permissions or userid options, but those do exist as well with 'find'.

I'd run that example command for each type of file, changing the target and pattern match.  If you never want to clobber existing files (those already copied earlier), it gets more complex and harder and won't be 1 line.

Depending on the old disks/partitions, it might be easiest to delete those directories which don't have anything personal inside.  For example, /media/old-disk-1/usr/ won't have any personal files, so just delete that.  

You'll need to be smarter about other top level directories.  On a former desktop, /media/old-disk-1/var/ probably doesn't have anything, but if it was a web or DB server, then the most critical files are stored under there. Deleting them would be terrible without careful consideration.

But we cannot say what is important to you.  On a desktop Linux storage partition, /home/{userid} is were almost all personal files get placed unless the user went out of their way to do something different.  We don't know what you may or may not have done.  I don't put all that much in /home/thefu. It holds configuration files and a few documents for reference and a few hundred scripts that I've written over the decades.

There are tools that find duplicate files in storage too.  finddup is one.  It looks deeper than just the filename to decide whether a file is "the same" or not.  For fun, about 10 yrs ago, I wrote my own duplicate file finder.  Getting the list of files that were the same wasn't all that hard.  Deciding which 1 to keep ... that was harder and I never solved it in the script.  It was always a manual effort.  It was a huge effort, so I decided to just buy a 4TB disk and selectively move over important files as needed. The $150 for that disk was less costly than my time+effort in my estimation.

Anyways, hope this gets you started.  Post some code. Ask specific questions.

---

