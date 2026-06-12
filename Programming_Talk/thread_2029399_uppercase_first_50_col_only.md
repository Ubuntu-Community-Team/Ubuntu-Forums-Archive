---
title: "uppercase first 50 col only"
date: 2012-07-19
forum: Programming Talk
---

### Post by vbdanl on 2012-07-19
hi,  i have been looking at awk, sed, and tr examples and haven't found one that works for what i am trying to do.  i have a text file that contains 200 bytes records.  i need to uppercase the first 50 bytes of each record, and leave the record the same length as it currently is.
so far my attempts are removing spaces, which i don't want to do.
thanks for your help!

---

### Post by trent.josephsen on 2012-07-19
Are the records separated by newlines? Is there a 1-to-1 correlation between *bytes* and *characters*? If the answer to either question is no, you're going to need to do a little more work.

But this is easy in Perl, untested and probably not the best way. 

```
perl -pe 'substr($_, 0, 50) =~ s/([a-z]*)/\U\1/g' old_file >new_file
```

Alternatively,

```
perl -pe 's/^.{50}/\U$&/'
```

I imagine you might modify the second one to work with sed. I don't know much about sed and even less about awk.

---

### Post by richpri on 2012-07-19
You may want to try using perl.

The @array = split(//, $string);

and the \U string escape may be useful.

---

### Post by steeldriver on 2012-07-19
I'm not much of an awker but (subject to the others' comments about bytes versus characters) I think awk would do it too, something like

```
awk '{ print toupper(substr($1,1,50)) }'
```e.g.

```

$ echo "UUID=5e018f5e-62db-42b8-b551-3107ee125a5b none            swap    sw              0       0" | awk '{ print toupper(substr($1,1,50)) }'
UUID=5E018F5E-62DB-42B8-B551-3107EE125A5B

```

---

### Post by vbdanl on 2012-07-19
this needs to be done on a hpux machine.  I don't know of any perl scripts running on it now, so if possible, i would like to do it with combinations of sed, awk, cut, and tr commands, which i am sure are being used today.

the records are separated by a new line (maybe a CRLF, whichever is unix std).  there is a 1 to 1 char/byte relation. the file was created by a vsam unload utility, and i plan to reload the file using the same vutil utility.

if i can't find a solution using the commands above, i will probably write a cobol program to basically reorg the file.  was just thinking this should be easier than that..

---

### Post by Vaphell on 2012-07-19
> ```
perl -pe 's/^.{50}/\U$&/'
```

I imagine you might modify the second one to work with sed. I don't know much about sed and even less about awk.

```
sed -r 's/^.{50}/\U&/'
sed 's/^.\{50\}/\U&/'
```

---

### Post by vbdanl on 2012-07-19
> **steeldriver said:**
> I'm not much of an awker but (subject to the others' comments about bytes versus characters) I think awk would do it too, something like

```
awk '{ print toupper(substr($1,1,50)) }'
```e.g.

```

$ echo "UUID=5e018f5e-62db-42b8-b551-3107ee125a5b none            swap    sw              0       0" | awk '{ print toupper(substr($1,1,50)) }'
UUID=5E018F5E-62DB-42B8-B551-3107EE125A5B

```

i tried this awk command followed by input-filename > output
it uppercased the first 50 bytes, but the output does not have the rest of the record..like it only has the first 50..

---

### Post by steeldriver on 2012-07-19
my bad, missed that req - how about

```
awk 'BEGIN { OFS="" } { print toupper(substr($0,1,50)),substr($0,51) }'
```

---

### Post by vbdanl on 2012-07-19
> **steeldriver said:**
> my bad, missed that req - how about

```
awk 'BEGIN { OFS="" } { print toupper(substr($0,1,50)),substr($0,51) }'
```

thats funny.. i entered the command like u had at first, and i noticed the output file was 206 bytes longer than other output files, and there are 206 records in my test dataset.. so u are right, i was getting an extra byte per record.
i might have other issues with this.. i didn't know it, but somewhere in my unload file there are 1700 null char.  when i open a copy of the file in vi, it says "1700 null char".  when i was trying the various suggestions everyone sent, i was ending up with a output file 1700 bytes less than my input file.  then this last one had another 206, which is explained..
i am already an hr late getting out of here, so i am going to pursue this in the am.. will try the command above just to see that it gets rid of the extra 206, and may try doing the vutil load on the file to see if it works without the nulls..
i really appreciate all the responses and help from everyone !!

---

### Post by steeldriver on 2012-07-19
OK let us know how it goes

You could look at piping through the 'tr' command to remove the nulls - it's something like 

```
*blah blah* | tr -d '\000'
```should do it I think

---

### Post by vbdanl on 2012-07-20
thanks for all your help.
after looking at it more today, i am going to do it with a program instead of script.  i need to rebuild the entire vsam file starting with an empty file.  since i was going to have to write a pgm to create the empty file anyway, i just as well do it all in there.
i am going to save your examples and would not be surprised if they help me with some task in the future.  thanks again.

---

