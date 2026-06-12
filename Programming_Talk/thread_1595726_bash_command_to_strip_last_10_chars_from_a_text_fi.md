---
title: "bash command to strip last 10 chars from a text file"
date: 2010-10-13
forum: Programming Talk
---

### Post by shortridge11 on 2010-10-13
i'm looking for a hint towards what command i could use to remove the last 10 characters from a text file. Any ideas?

---

### Post by saulgoode on 2010-10-13
man head

---

### Post by shortridge11 on 2010-10-13
wait wouldn't i use tail?

---

### Post by spjackson on 2010-10-13
> **shortridge11 said:**
> wait wouldn't i use tail?
No. You would use tail to output the last 10 characters of a file, but not to output all but the last 10 characters. For that you would use head.

---

### Post by shortridge11 on 2010-10-13
you are a genius good sir(s). Thanks

---

### Post by shortridge11 on 2010-10-14
While this worked on my local machine when I went to use it on the remote machine, that version of head doesn't support any extra options. Also each file I do this to will be of a different undetermined length. I also do not have the capability to upgrade or install a newer version of head. Any other ideas?

---

### Post by lloyd_b on 2010-10-14
> **shortridge11 said:**
> While this worked on my local machine when I went to use it on the remote machine, that version of head doesn't support any extra options. Also each file I do this to will be of a different undetermined length. I also do not have the capability to upgrade or install a newer version of head. Any other ideas?

Could you be a little more specific about what you mean by "last 10 characters"?  Is this going to include newlines?  For example, if you have a file that ends like this:```
This is a sample file
Short Line
end
```exactly what should the output look like?

I think I see a way to do this using 'sed', but while it's relatively simple to trim the last 10 characters from the last line of the file, it gets tricky if the last 10 characters spans multiple lines.

Lloyd B.

---

### Post by Diametric on 2010-10-14
Could it be that the remote machine is running a different shell?  That might explain why some of the functionality wasn't there.

---

### Post by saulgoode on 2010-10-14
> **shortridge11 said:**
> While this worked on my local machine when I went to use it on the remote machine, that version of head doesn't support any extra options. Also each file I do this to will be of a different undetermined length. I also do not have the capability to upgrade or install a newer version of head. Any other ideas?

Does your remote machine not offer ANY options to head? 

Does it support the 'stat' command (to find the file size)?

You might try the following:

```
head -c $(($(stat -c %s filename) - 10)) filename
```

where 'filename' is the name of the file.

---

### Post by spjackson on 2010-10-14
> **shortridge11 said:**
> While this worked on my local machine when I went to use it on the remote machine, that version of head doesn't support any extra options. Also each file I do this to will be of a different undetermined length. I also do not have the capability to upgrade or install a newer version of head. Any other ideas?

When you ask how to do something in bash in a Ubuntu forum and you don't specify otherwise, I think that you will find that most people will give you an answer that works in bash on Linux. I would certainly work with that assumption.

As it is to run on some other platform, you really should tell us something about it and what tools are available.

Also, without any conext, it does seem a bit of an odd thing to do, so perhaps you could give a wider picture of what you are trying to achieve so that we can perhaps come up with alternative suggestions.

Do you want to truncate the file in place, or write the output to some other file?

dd will probably do the job if you first find the file size and subtract 10 from the byte count, assuming the system has dd, or perhaps a short Perl script if it has Perl.

---

### Post by conundrumx on 2010-10-14
If you want to do it super kludgey you can do:

```
sed s/"`tail -c 10 [file]`"// [file] > [newfile]
```

But this assumes the last 10 characters are unique, there's probably a better way to do this but I don't really use sed all that often.

---

### Post by lloyd_b on 2010-10-14
> **conundrumx said:**
> If you want to do it super kludgey you can do:

```
sed s/"`tail -c 10 [file]`"// [file] > [newfile]
```

But this assumes the last 10 characters are unique, there's probably a better way to do this but I don't really use sed all that often.

That runs into problems is there are newlines involved - 'sed' only performs the pattern matching on one line at a time, unless you jump through some hoops to get it to do otherwise.

I was thinking of something along the lines of:```
sed "$s/..........$//" file > newfile
```which will strip the last 10 characters from the last line of the file.  But without knowing more about the file, I'm not sure how well it will work, for the same reason - what if those last 10 characters span multiple lines?

We *really* need some idea of what the data is going to look like...

Lloyd B.

---

### Post by ghostdog74 on 2010-10-14
```

data=$(<file)
echo "${data:0:${#data}-10}"

```

---

### Post by spjackson on 2010-10-15
> **ghostdog74 said:**
> ```

data=$(<file)
echo "${data:0:${#data}-10}"

```
Very clever. Congratulations. Of course, it's inefficient for large files and doesn't work for binary files (subject says text, so that's ok), but with those caveats, it may well be an excellent solution.

---

