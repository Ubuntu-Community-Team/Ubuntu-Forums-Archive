---
title: "Fixing Filezilla Help"
date: 2011-05-10
forum: Packaging and Compiling Programs
---

### Post by Syndacate on 2011-05-10
Hey,

I modify files via SFTP quite frequently.  It is important, because of this, that I have an SFTP client that can upload upon save.  gFTP cannot manage this because it seems to listen for the editor close in order to upload the file.

So I turn to filezilla.

The only problem, this developer here [http://trac.filezilla-project.org/ticket/4694](http://trac.filezilla-project.org/ticket/4694) (codesquid) refuses to implement the feature of uploading upon save for reasons nobody quite understands.  I believe he is trying to make it so that if an upload is corrupted due to two concurrent uploads, it is not filezilla's fault, rather the user because they clicked "ok" to upload.

NOBODY WANTS THE STUPID DIALOG, but it's there, none-the-less, and you can't get rid of it.  This is extremely pathetic when you need rapid dev/compiling modules.

Anyway, that's his problem, fine, but I cannot live like this.  Every other SFTP client supports it, CuteFTP supports it, if you're on a Mac, both main SFTP clients (Cyberduck & Transmit) support this functionality, and the main SFTP client for Windows (WinSCP) implements this perfectly.

I'll make the change myself, I don't really care.  I'm concerned with the re-packaging of it since I'd like to make it remain as a package registered by the package manager.

So I'm wondering on what I have to do for this so it's legitly installed.

I'm guessing I have to uninstall the existing package, then download the source via synaptic, install all the dev libs required, make the changes, re-compile, then install the deb (simply by double clicking)...and that should register it with the package manager, correct?

I'd love a program that I can just save and have it upload to a server..and I just can't keep clicking OK in this stupid dialog anymore, especially when I'm in a time critical situation.

Thanks for your time, guys.  Sorry about the post being long.

Note:
codesquid, if you read this, you are acting miserable in terms of being a developer for a FOSS project.  It is a common feature that all other mainstream editors (both free and paid) support.  Nobody is on your side yet you continue to argue with many unhappy users in the community.  The least you could do is provide the option, if users would like to use it.

---

