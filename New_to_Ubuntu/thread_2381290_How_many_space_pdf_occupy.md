---
title: "How many space pdf occupy"
date: 2017-12-29
forum: New to Ubuntu
---

### Post by sed_faster on 2017-12-29
HEllo,

I am trying this:
```

ls -r * | grep "pdf" | du -h

```
Also I tried this code:
```

du -ch -d 5 *.pdf

```
But I can't quantify all pdf I have on subdirectories.
My purpose is count all pdf I have on directory and see how many space they occupy.
Thanks

---

### Post by vasa1 on 2017-12-29
This may not be what you want but try```
find . -iname "*.pdf" -type f -exec du {} \; | nl
```

You could redirect the output to a file and then open that in LibreOffice Calc to total the sizes. There maybe a more elegant way. For that you'll need to wait for the experts :)

```
find . -iname "*.pdf" -type f -exec du {} \; | nl > edgar.txt
``` will give you a file named edgar.txt with all the files and their sizes and the line numbering tells you how many files there are. The output is tab-delimited and opens nicely in Calc. You can use the sum function.

If you don't want to use Calc, follow up with```
find . -iname "*.pdf" -type f -exec du {} \; | nl | awk '{sum+=$2} END {print sum}'
```you'll just get the total of all the sizes which matches what I get in Calc. You won't see the file names, etc.

I got the awk bit from [https://unix.stackexchange.com/questions/242946/using-awk-to-sum-the-values-of-a-column-based-on-the-values-of-another-column](https://unix.stackexchange.com/questions/242946/using-awk-to-sum-the-values-of-a-column-based-on-the-values-of-another-column)

---

### Post by Holger_Gehrke on 2017-12-29
```

find . -iname '*.pdf' -print0| du -c --files0-from=-

```
should do it ...

Holger

---

### Post by vasa1 on 2017-12-29
> **Holger_Gehrke said:**
> ```

find . -iname '*.pdf' -print0| du -c --files0-from=-

```
should do it ...

Holger

Thanks :D

---

### Post by sed_faster on 2017-12-29
Thanks to yours help. 
@[**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("https://ubuntuforums.org/member.php?u=1961578") I was study your command and I can understood.

@[**[COLOR=#C61919][B]vasa1**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=449866") I was study your code and I try apply this logic on this post: [https://ubuntuforums.org/showthread.php?t=2381100](https://ubuntuforums.org/showthread.php?t=2381100)
I intend use fdupes only to pdf files. For this I try this:
```

find Desktop/teste_repeat/ -iname '*.pdf' -exec fdupes -rnA -m {} \;
fdupes: could not chdir to Desktop/teste_repeat/FR_2017-615_teste.pdf
fdupes: could not chdir to Desktop/teste_repeat/FR_2017-615sdfadasd.pdf

```
On my logic the find will search only pdf files and after this will execute fdupes to output the command find. Am I think well?
Before I think about this I try this:
```

$ find Desktop/teste_repeat2/ -iname '*.pdf' -print0 | fdupes -rnAm --files0-from
fdupes: unrecognized option '--files0-from'
Try `fdupes --help' for more information.

```
Only after I read output error I remember the parameter --files0-from correspond an output du program

thanks

---

### Post by Holger_Gehrke on 2017-12-30
You might want to take another look at the [manual page for fdupes]("http://manpages.ubuntu.com/manpages/precise/man1/fdupes.1.html"). You can't pass filenames as arguments to this program, only directories.

Holger

---

### Post by sed_faster on 2017-12-30
Ok, after think more about isse I understand. I don't use fdupws to over files but over directories. To know if determine file is duplicate I need another algorithm. Thanks

---

### Post by sed_faster on 2017-12-30
For example, I use this script to identify all files duplicate from a specific type:
```

find test/ -type f -exec sha256sum '{}' ';' | sort | uniq --all-repeated=none -w 65

```
After this I am thinking create a routine where count how many times determine hash with 65 characters is duplicate more than  two times and rm all at least one of them. For example, this script report this:
> 
af4b4122fa5922fa33fc79cedsfdsfdsfgsdgdsf435454552348704b146f77e6395  tes/truby2.pdf
af4fdgfdgfgfdggsddfsdfnkljskjfsdjfjdskjfkjshdkhjkdshkgfd48704b146f77e6395  test/rubydsf.pdf
a866d465465164641644654654165fd6514g6fs546s14d65g416fdg6s514g6f95  test/ruby.pdf

The next step are remove second and third occurrence and let say first occurrence (always the first occurrence). 
Do you any another idea about this routine/purpose or do you think is it a good way to solve my issue?
Thanks

---

