---
title: "Protection from accidental deletion in Nautilus"
date: 2009-10-18
forum: Packaging and Compiling Programs
---

### Post by yusdi on 2009-10-18
(Not sure what subforum this thread should be in, sorry if this isn't the right place)

Hello everyone,

Recently I was searching for a way to protect some personal files and folders from accidental deletion (I never like the Trash/Recycle Bin thing, so I always use Shift+Del to delete files). One way is to replace rm with a script that does the filename checking before executing the real rm binary, but this only works for command line and what I need is to prevent deleting the files/folders from the GUI file browser like Nautilus. I also read that you can set an immutable attribute for files, but this only works for Linux file systems (e.g. ext2, ext3), while some of the files and folders that I want to protect is in an NTFS partition (no, I don't have Windows on my PC, it's just that I need my external hard drive to be readable in other people's PCs). Another way is to place the real files and folders in some obscure location, and just make symlinks to them so accidentally deleting the symlinks won't destroy the data. This works, but not exactly what I had in mind (also, will the symlinks still work if the NTFS partition is mounted on Windows?).

And so the solution that I ended up with was to hack Nautilus and add this protection feature. I use a similar concept as the ".hidden" file used to hide files without having to use filenames that start with dot. So in my modified Nautilus, users can create a file named ".protected" in a directory and put the list of files to be protected in there. All files listed in ".protected" can't be deleted or moved to Trash by Nautilus (obviously they can still be deleted by other means such as rm). The format of this ".protected" file is exactly the same as that of ".hidden" -- that is, a newline-separated list of filenames.

Note that ".protected" is read by Nautilus when the directory is opened, so if you create or modify ".protected" from within Nautilus, you need to at least reload the view before the changes can take effect. Also, this protection doesn't prevent a protected file from being deleted when the directory in which the file is stored is deleted (for example, even if /home/ubuntu/dir/file is protected, it will still be deleted if /home/ubuntu/dir is deleted). If you need to also prevent this kind of accident, you'd have to protect the directory as well. It is also a good idea to protect the ".protected" file itself.

My modification is applied to Jaunty's nautilus-2.26.2, the source of which was retrieved using "apt-src install nautilus". I wrote the code for my own purpose and this isn't such a big feature, but maybe someone out there can also benefit, so I share it here for anyone who is interested to try. The compiled debian packages can be downloaded from:

[http://www.mediafire.com/file/nxz2tmzgnzm/nautilus_delete_protection_deb.zip](http://www.mediafire.com/file/nxz2tmzgnzm/nautilus_delete_protection_deb.zip)

I also attach the diff patch here. Please be merciful when criticizing my code; this is my first time playing with a Glib-based application. :)

And oh, although so far my Nautilus has been stable, the usual disclaimer applies: I'm not responsible for anything bad that happens from using this modification; don't blame me if it deletes your porn collection or strangles your cat to death.

---

