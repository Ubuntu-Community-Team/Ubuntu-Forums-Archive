---
title: "Export Mail in Lotus Notes - Script"
date: 2010-03-31
forum: Programming Talk
---

### Post by _francis on 2010-03-31
Hi folks,

I used [this]("http://tech.niques.info/projects/lotus-notes-email-export/")guide to generate a script for mail export in Lotus Notes at work. Everything it's supposed to do works fine, but I'd like the posted date of the mail and its sender also in the file name.

The filename in the script is created like this:
```
OUTFILENAME=expdir$ & "\" & subj & " - " & doc.NoteID & ".eml"
```

Any help on how to extract the posted date and the sender from the mail would be great.

---

