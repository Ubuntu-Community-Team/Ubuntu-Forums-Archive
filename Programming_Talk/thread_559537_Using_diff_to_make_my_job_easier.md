---
title: "Using diff to make my job easier"
date: 2007-09-25
forum: Programming Talk
---

### Post by capsid on 2007-09-25
Hello!  I have to run two huge batch files everyday to update enrollments at a college.  Because the browser times-out, I have to first split the files and then upload them one at a time (yes, I know it should be automated, I'm not in charge).   This takes forever because 99% of the entries are redundant, but the system has to check for them anyway.  

I'm hoping I can take today's and yesterday's batch file and run diff, piping to stdout to get my new, slim batch file.  Unfortunately, diff has lots of extra info that I don't need in this case.  I've been reading the man page but I can't figure out how to get just the lines that have been added, with no extra formatting.  

Any suggestions?  This is the first time I've used diff, so bear with me!

---

### Post by gnusci on 2007-09-25
to make a patch file you can run:

```
> diff -ruN old.txt new.txt > patch.diff
```

and to apply the path you can use:

```
> patch -p0 -i patch.diff old.txt
```

---

### Post by capsid on 2007-09-25
Thanks for the quick response.  While I'll definitely be reading up on diff and patch for my programming projects (thx to your example), I'm afraid it wasn't quite what I'm trying to accomplish.  

I'm trying to output only the lines that are present in the new file but not in the old.  In addition, I'm trying to get rid of the diff markup so I'm left with just the content.

Maybe if I run diff and pipe to grep to only grab lines that contain '>' ?  Then I could run some other tool that would strip the '>' character, leaving only the new entries?

If I am doing this in a silly way, please feel free to suggest a different approach.

---

### Post by the_unforgiven on 2007-09-25
> **capsid said:**
> I'm trying to output only the lines that are present in the new file but not in the old.  In addition, I'm trying to get rid of the diff markup so I'm left with just the content.

Maybe if I run diff and pipe to grep to only grab lines that contain '>' ?  Then I could run some other tool that would strip the '>' character, leaving only the new entries?

If I am doing this in a silly way, please feel free to suggest a different approach.
Yes, that's a wrong approach - because even for the lines that were modified, diff reports them as "removed from the old, added to the new".

That said, I don't know if it's even possible to achieve what you want to do :(

---

### Post by capsid on 2007-09-25
> Yes, that's a wrong approach - because even for the lines that were modified, diff reports them as "removed from the old, added to the new".

Could you elaborate a little more?  Are you saying that entries that are present in both files, but at different line numbers, will be marked with '>' in the output of diff?  That would be OK as long as diff doesn't miss any entries that are in the new file but not in the old.  A little redundancy is fine.  For example: running diff on the two files yields a 97kb file.  That is so much more workable than the 3-5MB text files I'm working with now.

Pardon me if I misunderstood.

---

### Post by mssever on 2007-09-25
> **capsid said:**
> Could you elaborate a little more?  Are you saying that entries that are present in both files, but at different line numbers, will be marked with '>' in the output of diff?  That would be OK as long as diff doesn't miss any entries that are in the new file but not in the old.  A little redundancy is fine.  For example: running diff on the two files yields a 97kb file.  That is so much more workable than the 3-5MB text files I'm working with now.

Pardon me if I misunderstood.

This isn't very elegant, but it works: Save the following in a file and make it executable (I called it test.rb). ```
#!/usr/bin/env ruby
while line = gets
   next unless line =~ /^> /
   print line.reverse.chop.chop.reverse
end
```Then, run this command: ```
diff old_file new_file | ./test.rb > result_file
```

---

### Post by capsid on 2007-09-25
Brilliant! Thanks a bunch.  I like the reverse.chop.chop.reverse part a lot :)  I need to learn regexps and spend more time with ruby!!!

I really really really appreciate the help.

---

### Post by stylishpants on 2007-09-25
Some alternate approaches:

```

# this will only work if the sort order is the same in both files
join -v2 file1 file2

# this will work regardless
cat file1 file2 | sort | uniq -u
```

What about the case where a student was in yesterday's file but is not in today's?  What should happen then?  My first approach will not include the dropped name, my second approach will.

---

