---
title: "Merging Data Files"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by ToshibaLaptoplinux on 2008-11-21
I would like to merge, sort, and remove duplicate entries from two data files. They are both CSV files. One is an address book export from Jpilot and the other is an address book export from Thunderbird.Later I would also like to deal with a 3rd file which would be an Outlook 2000 export.

When finished I will import the clean data back into my applications. I have over 5000 entries in each file of which a large percentage are duplicates.

My first concern is that there will be discrepancies in the field names so I guess I would have to sort and match the fields before merging the files?

The second is that the data will contain both Japanese and English character sets.

I have little experience with text editing in Linux at the command line and all the googling I have done quite frankly has me lost.

It seems that I would have to use some combination of Sed/Awk, Sort -u, and Cat? But I am really at a loss about how to do this. Cat to merge the files and then Sed/Awk and Sort -u to sort and remove duplicates?

The most important thing for me is to also be able to see what data is deleted. So I rather it not delete stuff silently in the background but generate and output a record of the deleted data as well as the clean data.Of course I will back everything up before I start. SO my question is where do I start and what commands and what kind of syntax should I use?

Thanks

---

### Post by jpkotta on 2008-11-21
Roughly,
```
cat file1 file2 > with_dups
cat with_dups | sort | uniq > without_dups
diff -u with_dups without_dups
```
You will probably have to replace "sort" and "uniq" with more sophisticated stuff as you said.  Perhaps a good tool to manipulate a CSV file is OO.o Calc or Excel.  But diff will show you precisely what changed.

---

### Post by ToshibaLaptoplinux on 2008-11-21
Thank you. That seems like a good way to start but I am curious. When I cat the two files will it append the second files data into the appropriate fields of the first file. Or does it just append the file kind of like a second page?

---

### Post by ToshibaLaptoplinux on 2008-11-21
OK. I see now that cat doesn't match any fields but just appends the file2. SO I must match the fields between the two files before cat'ing. Does that seem correct?

I would like to try to avoid using OO or excel because I want to learn how to do text manipulation at the command line in Linux but given the data is also important I may resort to it just to get it done.

---

### Post by jpkotta on 2008-11-22
> **ToshibaLaptoplinux said:**
> OK. I see now that cat doesn't match any fields but just appends the file2. SO I must match the fields between the two files before cat'ing. Does that seem correct?
Yes.  You are probably better off importing the two files into Calc, making them look the same, and combining them in there.  Save the combined version, do your merge, and compare combined and merged.

> **ToshibaLaptoplinux said:**
> I would like to try to avoid using OO or excel because I want to learn how to do text manipulation at the command line in Linux but given the data is also important I may resort to it just to get it done.
If you're not doing this 100 times in a row, and Calc is easiest to use if you're just doing this once or twice, there is no reason not to use something like Calc.  Use the right tool for the job.

---

