---
title: "[SOLVED] Tomboy not Opening (like a few other apps)"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by mochiko on 2008-07-27
```

chitra@chitra-laptop:~$ tomboy
[DEBUG]: NoteManager created with note path "/home/chitra/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Addins.Database.AddinDatabase.Repair (IProgressStatus monitor, System.String domain) [0x00000] 
  at Mono.Addins.AddinRegistry.Rebuild (IProgressStatus monitor) [0x00000] 
  at Tomboy.AddinManager.InitializeMonoAddins () [0x00000] 
  at Tomboy.AddinManager..ctor (System.String tomboy_conf_dir) [0x00000] 
  at Tomboy.NoteManager.CreateAddinManager () [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 
chitra@chitra-laptop:~$ 


```

i can't open it from the menu bar, and this is what i get when i try from the terminal.. i read somewhere that it could be fixed by deleting the .tomboy file (after backing it up), but i couldn't post on that thread as it didn't allow me. 

any ideas?

---

### Post by braddcadd on 2008-07-27
There is a bug in lauchpad about it:
[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/155399](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/155399)

One of the posts there fixed their problem by typing this in the terminal:
```

export MONO_PATH=/usr/lib/cli/mono-addins-0.2

```

Not sure if that will work for you or not.

---

### Post by mochiko on 2008-07-28
hey thanks, 

i didn't try that because i did something else yesterday, and now it's opening up and working.. but if it happens again i will definitely try that out!

thanks dude.

---

### Post by reemM on 2008-08-26
What exactly did you do? 

Reem

---

