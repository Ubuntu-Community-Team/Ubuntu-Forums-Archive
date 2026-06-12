---
title: "Tomboy Problems"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Shippou on 2008-10-18
Hello...

I recently got this error:

The panel encountered a problem while loading "OAFIID:TomboyApplet".
Do you want to delete the applet from your configuration?

Also, when I run tomboy in the console,

```

shippou@Shippou ~/Desktop $ tomboy
[DEBUG]: NoteManager created with note path "/home/shippou/.tomboy".
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
shippou@Shippou ~/Desktop $ 

```

Any ideas?

---

### Post by directhex on 2008-10-19
try running "rm -r ~/.tomboy/addin*"

---

### Post by Shippou on 2008-10-20
I've solved the problem by uninstalling tomboy (purge option) then erasing its directory from my home folder. 

Please mark this thread as solved. Thanks a lot. :)

---

