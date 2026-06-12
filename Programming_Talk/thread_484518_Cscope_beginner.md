---
title: "Cscope: beginner"
date: 2007-06-25
forum: Programming Talk
---

### Post by Rij on 2007-06-25
Hello,
I am new to the Linux and in general, the Unix world. I am learning how to use Cscope to browse the source code. I downloaded the Cscope package from the distribution CD. Then I follow the exact guidelines as provided in the Cscope sourceforge help site
[http://cscope.sourceforge.net/large_projects.html](http://cscope.sourceforge.net/large_projects.html)

The cscope.files look like this:
    LNX=/home/arijit/linux-2.6.17
    cd / 	
    find  $LNX                                                                \
	-path "$LNX/arch/*" ! -path "$LNX/arch/i386*" -prune -o               \
	-path "$LNX/include/asm-*" ! -path "$LNX/include/asm-i386*" -prune -o \
	-path "$LNX/tmp*" -prune -o                                           \
	-path "$LNX/Documentation*" -prune -o                                 \
	-path "$LNX/scripts*" -prune -o                                       \
	-path "$LNX/drivers*" -prune -o                                       \
        -name "*.[chxsS]" -print >/home/arijit/cscope/cscope.files


However, when I run the command: cscope -b -q -k

I get the following error:
cscope: cannot find file LNX=/home/arijit/linux-2.6.17
cscope: cannot find file 6.17
cscope: cannot find file cd
cscope: cannot find file cd
cscope: cannot find file find
cscope: cannot find file find
cscope: cannot find file $LNX
cscope: cannot find file \
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file h
cscope: cannot find file $LNX/arch/*
cscope: cannot find file !
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file $LNX/arch/i386*
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: only -I, -c, -k, -p, and -T options can be in file cscope.files
cscope: cannot find file \
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file h
cscope: cannot find file $LNX/include/asm-*
cscope: cannot find file !
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file $LNX/include/asm-i386*
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: only -I, -c, -k, -p, and -T options can be in file cscope.files
cscope: cannot find file \
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file h
cscope: cannot find file $LNX/tmp*
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: only -I, -c, -k, -p, and -T options can be in file cscope.files
cscope: cannot find file \
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file h
cscope: cannot find file $LNX/Documentation*
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: only -I, -c, -k, -p, and -T options can be in file cscope.files
cscope: cannot find file \
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file h
cscope: cannot find file $LNX/scripts*
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: only -I, -c, -k, -p, and -T options can be in file cscope.files
cscope: cannot find file \
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file h
cscope: cannot find file $LNX/drivers*
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: only -I, -c, -k, -p, and -T options can be in file cscope.files
cscope: cannot find file \
cscope: only -I, -c, -k, -p, and -T options can be in file cscope.files
cscope: only -I, -c, -k, -p, and -T options can be in file cscope.files
cscope: cannot find file *.[chxsS]
cscope: -p option in file cscope.files: missing or invalid numeric value
cscope: cannot find file >/home/arijit/cscope/cscope.files
Cannot open file /
cscope: cannot create inverted index; ignoring -q option
cscope: removed files ncscope.in.out and ncscope.po.out

Any help will be highly appreciated.
Thanks in advance.

---

### Post by geraldm on 2007-06-25
Hello,

when posting with environment variables, mention your shell.
It looked to me that the file you created with the find
command was improper. There should have been no file
name "6.17" or "cd" or "find".  
Try from an empty directory:

# using tsch shell:  (just set the env variable)
setenv LNX /home/pkg/build/linux/linux-2.6.21.1u
# check the env variable:
echo $LNX

#use the env $LNX:  (NOTE this is not in accord with the referenced project.
# it is just this example.  Need to redirect the output into cscope.files)
find $LNX -name "*.c" > cscope.files

# then when issuing the command I get three files: cscope.in.out
# cscope.out cscope.po.out
cscope -b -q -k

Best regards,
Gerald.

---

### Post by Rij on 2007-06-26
Thank you for your help.
I am using bash.
I tried running the same commands from the command line and it worked without any modifications.
Any insight?

---

### Post by geraldm on 2007-06-26
Then you have found out how to create the data base files.
I suggest using the tutorial that is on the cscope.sourceforge.net
site.  It is best not to create the huge files with the commands
in my previous post.  The data files were over 90 Megabytes!.
Pick a small project to learn to use the cscope tool.

best regards,
Gerald

---

