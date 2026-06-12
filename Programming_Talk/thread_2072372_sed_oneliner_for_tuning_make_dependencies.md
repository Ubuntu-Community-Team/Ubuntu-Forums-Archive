---
title: "sed oneliner for tuning make dependencies"
date: 2012-10-17
forum: Programming Talk
---

### Post by outofsync on 2012-10-17
Hi,

I wish to pipe a dependency file generated with 'gcc -M' through sed, because I'm on a source tree where object files are generated on a build subdirectory.

Basically, I want to change every *.o: occurrence to $(OUTPUT_DIR)/*.o:

For example:

foo.o: foo.c foo.h

should become:

linux64build/foo.o: foo.c foo.h

Note that in this example, linux64build would be the value of the $(OUTPUT_DIR) variable, set somewhere in the Makefile.

I know this must be really simple to do, but I tried to understand the sed tutorial at [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html) and got totally lost... I understand how to replace certain substrings, but didn't find how to achieve the *.o: wildcard behaviour I need...

---

### Post by steeldriver on 2012-10-17
something like this you mean? this only replaces the LHS of rules (because of the :) I'm not sure if that's what you want

```
$ echo "foo.o: foo.c foo.h" | sed  's|[^.]\+\.o:|$(OUTPUT_DIR)/&|'
$(OUTPUT_DIR)/foo.o: foo.c foo.h

```

---

### Post by outofsync on 2012-10-17
The behaviour you describe is what I want, but that oneliner didn't work for me, I suppose it's an issue with backslashes.

After some time of trial and error, I arrived to this solution, which seems to work:

```
sed 's|[^ ]*.o:|$(OUTPUT_DIR)/&|'
```

---

### Post by steeldriver on 2012-10-17
Hmm... OK that's a little bit risky imo - remember *.o doesn't mean the same thing in regex syntax as it does in a shell glob - you have matched zero or more characters excluding literal space, followed by any single character, followed by o: so it's going to replace things like plain foo: moo: and even to:

```
$ echo "to:" | sed 's|[^ ]*.o:|$(OUTPUT_DIR)/&|'
$(OUTPUT_DIR)/to:
```Just as long as you are aware of that - otherwise if you can give an example or two of where my suggestion didn't work we can try to fix that

---

### Post by outofsync on 2012-10-18
> **steeldriver said:**
>  otherwise if you can give an example or two of where my suggestion didn't work we can try to fix that

I'm currently working on both Ubuntu and OSX, but however I only tried it on my OSX box because that's what I've currently on my hands. If I execute your code on the OSX Terminal (with copy and paste), it doesn't modify the original string.

And the same happens if I execute it from a Makefile: It doesn't modify the input.

I tend to believe it's something related to backslashes not being handled well, because I tried to also consider tabs as whitespace (with \t ) and it began to consider the 't' char as a valid input, instead of tabs, so it seems it was ignoring the backslash.

In other words, this is what I get when executing your command from the OSX Terminal:

```
echo "foo.o: foo.c foo.h" | sed  's|[^.]\+\.o:|$(OUTPUT_DIR)/&|'
foo.o: foo.c foo.h
```

---

### Post by steeldriver on 2012-10-18
Ah OK, I don't think your original post mentioned this was on OSX

Likely the OSX version of sed does not support the \+ extension (1 or more occurrences of the preceding pattern) - you could try 

```
sed  's|[^.]\{1,\}\.o:|$(OUTPUT_DIR)/&|'
```which *should* be portable - I think - or try the -E or -r flag to make it GNU-sed compatible and use

```
sed  -r 's|[^.]+\.o:|$(OUTPUT_DIR)/&|'
```(no backslash before the +) or change \+ to * to just match zero or more non-dot characters instead

```
sed  's|[^.]*\.o:|$(OUTPUT_DIR)/&|'
```[http://unix.stackexchange.com/questions/13711/differences-between-sed-on-mac-osx-and-other-standard-sed](http://unix.stackexchange.com/questions/13711/differences-between-sed-on-mac-osx-and-other-standard-sed)

---

### Post by spjackson on 2012-10-18
> **outofsync said:**
> 
I wish to pipe a dependency file generated with 'gcc -M' through sed, because I'm on a source tree where object files are generated on a build subdirectory.

Is there a reason why you want to use sed? Can't you use
```

gcc -M -MT '$(OUTPUT_DIR)/file.o' file.c

```
which appears to be designed for this purpose? (Or -MQ instead of -MT depending on requirements.)

---

### Post by outofsync on 2012-10-22
> **steeldriver said:**
> Likely the OSX version of sed does not support the \+ extension (1 or more occurrences of the preceding pattern)

I think it's not the \+ extension, but there's some issue with the backslash in the shell (if I use \t to specify the tab character, it thinks I'm referring to the 't' character, so it definitely looks like a backslash issue). I'll investigate it.

---

### Post by outofsync on 2012-10-22
> **spjackson said:**
> Is there a reason why you want to use sed? Can't you use
```

gcc -M -MT '$(OUTPUT_DIR)/file.o' file.c

```
which appears to be designed for this purpose? (Or -MQ instead of -MT depending on requirements.)
Although this gcc solution looks smart, however it requires a different dependency file for each source file... this would require huge changes in my source tree, across all makefiles, because I use one dependency file per Makefile, not per source code file.

---

### Post by spjackson on 2012-10-22
> **outofsync said:**
> Although this gcc solution looks smart, however it requires a different dependency file for each source file... this would require huge changes in my source tree, across all makefiles, because I use one dependency file per Makefile, not per source code file.
I don't understand why you say that. This creates one dependency file:
```

#!/bin/bash

for source in *.c
do
    name=$(basename ${source} .c)
    gcc -M -MT "\$(OUTPUT_DIR)/${name}.o" ${source}
    echo # add a blank line to make the dependency file more beautiful
done >> foo.mak

```
Use sed though, if that fits better with your current work flow.

---

### Post by outofsync on 2012-10-22
You're right spjackson, I didn't think of that possibility, it's more reasonable to send all the gcc stdout from all calls to a single output file rather than using sed. 

Well, the only reason for using sed is that I'd like my code to continue being compatible with the SGI cc, and such compiler lacks this GCC extension AFAIK, but I'm using Makefiles which load configurable options, so I can use a different command for building dependencies on Ubuntu and OSX, and on IRIX.

Thanks!

---

### Post by outofsync on 2012-10-27
> **steeldriver said:**
> Ah OK, I don't think your original post mentioned this was on OSX

Likely the OSX version of sed does not support the \+ extension (1 or more occurrences of the preceding pattern) - you could try 

```
sed  's|[^.]\{1,\}\.o:|$(OUTPUT_DIR)/&|'
```which *should* be portable - I think - 
I confirm that this one works on OSX. The origin of the problem was that OSX sed comes from -of course- BSD sed, and BSD sed isn't GNU sed.

So, I need a line that works both on BSD sed and on GNU sed, and yours seems to work. Thanks a lot!

---

