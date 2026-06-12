---
title: "Automatically RAR and FTP Upload a Directory, Then Delete"
date: 2010-04-06
forum: Programming Talk
---

### Post by tablebreaker on 2010-04-06
Hey everyone! I'm new to learning scripting, and I'm hoping to find some help. Here's what I want to do:

I would like to archive a directory:
```
rar a "FolderName.rar" -v100m "FolderName"
```

...and that's about as far as I've figured out.

From here, I want to upload FolderName.part* (wildcard depending on how many parts there are) to an ftp server. I'm not sure the command for logging in to an ftp and uploading a file in one go. I've tried using ; to send commands in sequence, but it wasn't working.

After the file transfers are complete, I want the FolderName*.rar files AND the /FolderName/ directory to be deleted. 

Bonus points if this can be automated, and super bonus points if I can be sent an email with the FolderName every time this is successful...

thanks so much for the help!! :D

---

