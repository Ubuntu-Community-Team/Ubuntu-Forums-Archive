---
title: "rsync Usage Question"
date: 2011-05-02
forum: Programming Talk
---

### Post by jamesisin on 2011-05-02
I am using rsync to move files from my main machine where I run my torrents to my server where I store the files.  I make copies of the files, rework them as necessary (tagging files for instance), and drop them into a specific transfer folder.

When I am ready I run rsync on that particular transfer folder to it's twin on the server.  This is the basic rsync I run:

```
rsync -ailS --progress --remove-source-files /local/folder/ server:/path/
```

This removes all the files as they are confirmed on the server, but I was hoping to find a way to then remove any empty folder.  I have read the rsync man page but didn't see anything obvious (like --remove-empty-folders).  Basically, I'm trying to get rsync to act like mv in this scenario.

Possible?

---

### Post by bashologist on 2011-05-02
Ssh maybe? rmdir woud not remove regular files and woudn't remove non-empty directories, so you could use it on all your files I would think.
```
ssh address rmdir "/location/*"
```
The command might need to be quoted don't know. I've never heard of that option for rsync tho.

---

### Post by jamesisin on 2011-05-02
Yeah, I could run rmdir over ssh.  I was hoping to find a way to get rsync to perform the action itself.  The command above actually runs rsync over an ssh connection (after entering that command you would get a password prompt from the server); when the command finishes the ssh connection closes with it.

However, I am trying to remove the folders which rsync has emptied on the local machine.  So again, I could issue the rmdir command locally, but I'd rather just get rsync to clean up after itself.  I managed to find a way to remove the *files* as they are transferred/confirmed.

---

### Post by mdurham on 2011-05-02
I don't use --remove-source-files, I use --delete-during which seems to do what you want.

---

### Post by jamesisin on 2011-05-02
> **mdurham said:**
> I don't use --remove-source-files, I use --delete-during which seems to do what you want.

I'm afraid you do not understand what I am trying to accomplish.  The argument --delete-during controls when the file-deletions occur on the *receiving* location while --remove-source-files deletes files as they are moved *from* the *source* folder.

If you look closely at the arguments I am using in the rsync command above you will note that I am not doing *any* deleting on the destination hierarchy.  I am moving files *to* there.  I don't want to delete *anything* over there.

I just want to remove the folder/files from the source hierarchy after they are copied and confirmed at that receiving location.  Think of using rsync like mv rather than using it like cp.

---

### Post by jamesisin on 2011-05-08
Anybody else have any ideas?

---

