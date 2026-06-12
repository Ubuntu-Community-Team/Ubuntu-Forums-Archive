---
title: "script within a program"
date: 2006-04-21
forum: Programming Talk
---

### Post by krypto_wizard on 2006-04-21
I have to improve on somebody deplhi project.

When user saves a files as *.edf , I have to make a copy of the same file and  name it as FIXED_NAME.edf. This is for eveyr file.

This Project is in Borland Deplhi and on Windows.


I know a little dos script would do that. 

My question is can I embedd this little script in the Borland Delphi project. And if yes how can I do that.

Please help,

---

### Post by jazzmuzik on 2006-04-21
You are asking about Windows programming on a Linux forum. I'm not sure this is the place you want to ask that question unless there's a Delphi for Linux.

In Linux, this will rename a bunch of files:

for i in *.edf; do mv "$i" "FIXED_NAME_$i"; done

The semicolons serve as a newline and that's how you can stack a bunch of commands together on the command line.

If you need to rename just one file:

mv oldfilename newfilename

There is also a 'rename' command, but its syntax is different in Redhat and Debian. Maybe that's not an issue with your program though.

If you need return values after the renaming, that's out of my area of knowledge.

---

### Post by krypto_wizard on 2006-04-21
Thanks for the help. I am a python and Linux user. I just went to a new job. They have given me this work. So I thot posting here can give me some pointers.

all I want to do is add a single line of scripts
```

copy *.edf filename.edf

```

But my question was, inside the delphi program how can one write a DOS command ? 

If anybody has done this kind of job please give me some pointers.

Thanks,

Every help is appreciated,


[QUOTE=jazzmuzik]You are asking about Windows programming on a Linux forum. I'm not sure this is the place you want to ask that question unless there's a Delphi for Linux.

In Linux, this will rename a bunch of files:

for i in *.edf; do mv "$i" "FIXED_NAME_$i"; done

The semicolons serve as a newline and that's how you can stack a bunch of commands together on the command line.

If you need to rename just one file:

mv oldfilename newfilename

There is also a 'rename' command, but its syntax is different in Redhat and Debian. Maybe that's not an issue with your program though.

If you need return values after the renaming, that's out of my area of knowledge.[/QUOTE]

---

### Post by jazzmuzik on 2006-04-21
I think you are asking a good question but in the wrong forum. But I'll give it one last try. Programming languages often have a command called 'system' or something similar which is used to execute an OS command from within a program. In psuedocode it might look like this:

result = system("copy oldfile.edf newfile.edf");

This would run the DOS copy command. Then you'd check the value of 'result' to see if all went well.

Note that 

copy *.edf filename.edf

will not work in DOS because it makes no sense. You are asking to copy a bunch of files to the same filename. Or maybe you are attemping to append a bunch of files into one file.

---

### Post by thumper on 2006-04-22
I'm sure that Delphi wraps the Win32 API.  Using the built in OS functions for dealing with files would be the preferred option here.  Whenever I see a program does a system exec - it makes me shudder.  It is an inelegant solution.

---

### Post by jazzmuzik on 2006-04-22
[QUOTE=thumper]I'm sure that Delphi wraps the Win32 API.  Using the built in OS functions for dealing with files would be the preferred option here.  Whenever I see a program does a system exec - it makes me shudder.  It is an inelegant solution.[/QUOTE]

Excellent point.

---

