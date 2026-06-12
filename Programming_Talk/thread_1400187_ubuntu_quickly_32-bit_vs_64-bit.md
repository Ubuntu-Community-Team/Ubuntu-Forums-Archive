---
title: "ubuntu quickly 32-bit vs 64-bit"
date: 2010-02-06
forum: Programming Talk
---

### Post by cometdog on 2010-02-06
Hi folks,

I'm not a GUI programmer, but I have learned some Python and thought it might be fun to play around with quickly.  I started a basic project in quickly using the template ubuntu-project.

I'm running one computer with 32-bit Karmic, and another with 64-bit Karmic.  I started this project on the 32-bit computer and wanted to see if it would run on the 64-bit computer, so I shared it between the computers using Ubuntu One.

However, if I try
```
quickly run
```
on the 64-bit computer, it just tells me
```
Can't execute bin/testprogram
ERROR: run command failed
Aborting

```

So in some ways this shouldn't be surprising -- after all stuff needs to be compiled differently to run on a 64-bit system.  On the other hand, what I have is mostly a Python script, I think, which should run on either system.

Clearly there are some fancy details going on under the hood here.  What is the binary that is failing to execute?  Is there any way to share a project between a 32-bit and 64-bit system?  If not can I "compile" it for the other system somehow?

---

### Post by cometdog on 2010-02-15
bump?

Anyone here tried quickly in the first place?

---

### Post by NovaAesa on 2010-02-15
I'm not 100% sure, but I *think* python does something tricky with compiling the source into bytecode as a speed-up method. So you would maybe need to try re running the script directly. Not really sure though, could be something to try.

---

### Post by OgreProgrammer on 2010-02-15
Modify the files and resave. Add a space, save, should do it. It tracks the time stamps/file size to decide if it needs to recompile included stuff. or delete the .pyc files in the project. They will be recreated.

---

