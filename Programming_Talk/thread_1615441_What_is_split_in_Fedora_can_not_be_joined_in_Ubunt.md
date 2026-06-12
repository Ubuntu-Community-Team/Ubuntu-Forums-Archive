---
title: "What is split in Fedora can not be joined in Ubuntu?"
date: 2010-11-07
forum: Programming Talk
---

### Post by yc2 on 2010-11-07
Hello,

Sorry for putting something here that is not a problem in Ubuntu, however I hope someone here has an idea.

I use GoDaddy Linux web-hosting (I think they use Fedora). I use PHP to produce archives. I am splitting the archive with the PHP/bash command:
```

`split -b 20k  archive.tar.gz   SPLIT`;
```
When I download the parts to Ubuntu they can be joined and the joined file gets the right size by
```
cat SPLIT* > join.tar.gz
```
However, when I try to open the archive it is corrupt.

If I download the unsplit archive it opens OK (even under Windows).
I can also download the whole archive, split and join it in Ubuntu, it opens OK.
It is also possible to split the tar (but not gzip-tar) under Fedora and join under e.g.Windows. The tar-file is too big for practical use, however. I need to have it gzipped which in this case reduces the size by a factor 8.

My only conclusion is that when I split gzipped files in Fedora the parts will not join correctly in Ubuntu. (Same problem if I join under Windows: COPY /B SPLIT* join.tar.gz)

I don't know if it could have to do with blocksize?

It sounds crazy, I hope someone can help. I would like to be able to join the parts under any OS, even Windows.

Thanks.

---

### Post by saulgoode on 2010-11-07
My guess is that the problem lies with the order of the expanded filenames. Try either specifying each name explicitly or something such as*:

```
(cat $(ls SPLIT* | sort)) > join.tar.gz
```


* If you are using BASH, the wildcards should be expanded in alphabetical order. If you are using another shell, they may not be -- but if you are using a different shell then you will need to translate the above code to an appropriate form for that shell.

---

### Post by trent.josephsen on 2010-11-07
IIRC, the order in which wildcard expansions are listed is affected by the LC_COLLATE environment variable.  It's very conceivable, even highly probable, that the LC_* variables are set differently in Fedora and Ubuntu by default.

I could be wrong about that, though.

---

### Post by yc2 on 2010-11-07
Thanks guys, I will try specifying the file-order explicitly. It's time to sleep here. I'll be back with the results as soon as I can try it.

---

### Post by yc2 on 2010-11-07
Thanks a lot, you cracked it.

This joins the files OK in Ubuntu:
(cat $(ls SPLIT* | sort)) > join.tar.gz

This works in Windows:
copy /b SPLITaa+SPLITab+SPLITac+SPLITad join.gz

In Windows it seems the rar program still has problems, it opens all files from all subfolders in the top level folder making the result useless. However, Wnizip opens the joined archive fully OK.

I think I have installed the (un)rar-package in Ubuntu and it takes over opening of the files in Gnome. It will open the joined archive OK. (However, it also makes an archive-icon of the first split file - I assume it includes all split files there, that is how rar works in Windows. However, clicking that icon fails.) 

It seems the cat command do not place files in order? Strange. cat is not a simple command, I think I once used this command and lost the file:

WARNING -  **[COLOR="Red"]You may lose the contents of the file by doing this[/COLOR]** ========
cat tst1 | sed 's/x/x/' > tst1
WARNING -  You may lose the contents of the file by doing this ========

Thanks, thread solved.

---

### Post by v1ad on 2010-11-07
you lost the file because it reads the command & prepares the file so basically it reads command, wipes tst1 and then try's to read from tst1 to tst1 if  you did cat tst1 | sed 's/x/x/' > tst2 if would work properly.

---

### Post by yc2 on 2010-11-07
I am sure cat and pipes are good programs with major bugs removed over the years.

But maybe cat is optimized for speed and efficiency? Looking at the problem in the present thread it seems like cat does not put files in alphabetical order.

Regarding the lost file I am still surprised. I thought the pipe-system (| and >) was executed in the order it appeared on the command line. (I haven't met this problem - lost file - piping other programs than cat, but I may be wrong here.)

But maybe the "lost file pipe" above gains a little efficiency by not storing any intermediary results.

---

### Post by v1ad on 2010-11-07
ye that is the problem, you though they where executed in order. that is a yes and no answer. it reads the command prepares the documents then executes the command in order. but the document you are trying to read is blank because it prepared the file already. it's weird but thats the way it works.

---

### Post by saulgoode on 2010-11-07
> **yc2 said:**
> But maybe cat is optimized for speed and efficiency? Looking at the problem in the present thread it seems like cat does not put files in alphabetical order.

**cat** itself does not handle the ordering of the files; the wildcard filename (SPLIT*) is expanded by the shell and **cat** is supplied with the expanded list. The POSIX standard mandates that the expanded list should in alphabetical order (or more precisely, in the LC_COLLATE order to which trent.josephson alluded).

If "(cat $(ls SPLIT* | sort)) > join.tar.gz" works yet "cat SPLIT* > join.tar.gz" does not, then your shell is not behaving in a POSIX-compliant manner (or you have somehow specified a non-standard LC_COLLATE). You should probably raise the issue with the maintainers of your shell.

> **yc2 said:**
> Regarding the lost file I am still surprised. I thought the pipe-system (| and >) was executed in the order it appeared on the command line. (I haven't met this problem - lost file - piping other programs than cat, but I may be wrong here.)

Piped commands run concurrently. As soon as the source program produces some output, the sink program will start processing it. In your example, the **sed** output will start overwriting *tst1* before **cat** has completed reading it.

---

### Post by yc2 on 2010-11-08
Thanks for a clear explanation including POSIX and LC_COLLATE, I will have to look into how the wildcards are expanded.

- - -

tst1 | sed 's/x/x/' > tst1

I am still a little surprised that the output file can overwrite the input file. If I create a new file that has the same name as another file on the disk I thought it worked like this: The new file was created on empty space of the disk. When all data finally had been written to the file, as the very last thing, the directory file pointer for the file name is changed to point at the new file. (Until this last moment, the old file is still reachable under the same name.)

To me it was as obvious as setting
a = a + 1;
Which is valid in all programming languages I know.

But obviously i have to rethink here.

---

### Post by Arndt on 2010-11-08
> **yc2 said:**
> Thanks for a clear explanation including POSIX and LC_COLLATE, I will have to look into how the wildcards are expanded.

- - -

tst1 | sed 's/x/x/' > tst1

I am still a little surprised that the output file can overwrite the input file. If I create a new file that has the same name as another file on the disk I thought it worked like this: The new file was created on empty space of the disk. When all data finally had been written to the file, as the very last thing, the directory file pointer for the file name is changed to point at the new file. (Until this last moment, the old file is still reachable under the same name.)

To me it was as obvious as setting
a = a + 1;
Which is valid in all programming languages I know. But obviously i have to rethink here.

It's not valid in Prolog or Erlang, actually. Or rather, it's valid, but its result may surprise you.

To return to the subject, some operating systems indeed worked like you describe, but I suppose it was one of the design decisions in Unix, in order to keep it simple. For example, if several processes want to write to the same file, probably only one should be allowed to, so you need file locking.

---

### Post by trent.josephsen on 2010-11-08
The appropriate way to cause sed to overwrite a file in-place is like so:

```
sed -i 's/find_pattern/repl_pattern/' filename
```
If you use -i.bak (for instance), the edited file will be saved under the original filename and the original will be saved as $filename.bak.

This same pattern also works with some other tools, like perl, but it's a feature implemented by the tool's author, and won't work with everything.

---

### Post by yc2 on 2010-11-08
Thanks for many good suggestions in this thread. Sorry for discussing two matters at the same time, but everyone seems to be able to separate them.

It appears that I must apologize. In the middle of the thread I may have given wrong information regarding joining the archives.

I have now run the following commands up and down, downloaded the parts in different order, opened the archives etc
```
(cat $(ls *PART* | sort)) > join1.tar.gz
cat *PART* > join2.tar.gz
cmp -b join1.tar.gz join2.tar.gz
diff join1.tar.gz join2.tar.gz

```
I can no longer verify a difference between the two ways of joining the files.

The only problem I can see is how the archive handler in the graphic environment handles the _parts_. I think my system uses (un)rar package.

(un)rar will show the first part as an archive icon. When I click that icon the archive shows a completely erroneous size (several G instead of K). This archive cannot be opened properly.

However, the _joined_ archives open correctly no matter which of the two methods joining them I have used.

Thanks for getting many clarifying replies in this thread. It has solved my problem.

---

