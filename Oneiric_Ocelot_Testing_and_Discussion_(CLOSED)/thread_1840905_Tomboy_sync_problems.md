---
title: "Tomboy sync problems"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by D10 on 2011-09-08
I am having an issue with Tomboy not syncing with Ubuntu One. I have a fresh install of the Oneiric Beta, and most things are working well. Tomboy will not sync with Ubuntu One and gives the following error in the debug log.

```
9/8/2011 8:01:42 AM [DEBUG]: Sync: 29 updates since rev -1
9/8/2011 8:01:42 AM [DEBUG]: SyncManager: Deleting auto-generated note: New Note Template
9/8/2011 8:01:42 AM [DEBUG]: Removing tag from New Note Template: system:template
9/8/2011 8:01:42 AM [DEBUG]: Watchers.OnTagRemoved popularity count: 0
9/8/2011 8:01:42 AM [DEBUG]: Deleting note 'New Note Template'.
9/8/2011 8:01:42 AM [DEBUG]: Creating Buffer for 'New Note Template'...
9/8/2011 8:01:42 AM [DEBUG]: Tag added to New Note Template: system:template
9/8/2011 8:01:42 AM [DEBUG]: Loading notebooks
9/8/2011 8:01:42 AM [ERROR]: Synchronization failed with the following exception: A note with this title already exists: New Note Template
  at Tomboy.NoteManager.CreateNewNote (System.String title, System.String xml_content, System.String guid) [0x00000] in <filename unknown>:0
  at Tomboy.NoteManager.CreateNoteFromTemplate (System.String title, Tomboy.Note template_note, System.String guid) [0x00000] in <filename unknown>:0
  at Tomboy.NoteManager.CreateNewNote (System.String title, System.String guid) [0x00000] in <filename unknown>:0
  at Tomboy.NoteManager.CreateWithGuid (System.String title, System.String guid) [0x00000] in <filename unknown>:0
  at Tomboy.Sync.SyncManager+<CreateNoteInMainThread>c__AnonStorey11.<>m__3F () [0x00000] in <filename unknown>:0
  at Tomboy.GuiUtils+<GtkInvokeAndWait>c__AnonStoreyC.<>m__2F (System.Object , System.EventArgs ) [0x00000] in <filename unknown>:0
9/8/2011 8:01:46 AM [DEBUG]: Saving 'New Note Template'...
```

I found an old BUG #534488 and replied to that, and tried what one person suggested by deleting the manifest.xml file. I also purged and reinstalled Tomboy, but still gives the error on sync.

I have 3 other machines running either 10.04 or 11.04 that are syncing fine with Ubuntu One

Anyone have any suggestions?

Thanks.

---

### Post by fjgaude on 2011-09-08
Wait and by the time the final release comes out it should be fixed...

---

