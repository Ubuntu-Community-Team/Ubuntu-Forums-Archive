---
title: "Recommended Archive Manager for non-tar files?"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by jps2012 on 2012-03-28
I've been able to use archive manager to extract tar files, but not some other kinds of archives I've downloaded. For example, I have an archive named "LATEST-IS-3.2.4" which the archive manager can't extract. 

Are there other archive managers I could use to attempt to extract non-tar files? Any recommendations? 

When tarfiles (or other archived files) are extracted, do I then have to build them via the command line, or does an archive manager do that automatically? 

I'm dreaming that somewhere out there, there's a flowchart that shows what steps to take, depending on what kind of archive/file has been downloaded (when those downloaded files are intended to add to Ubuntu's functionality, and aren't just eyeballers--PDFs, image files, etc.

---

### Post by papibe on 2012-03-28
Hi jps2012.

You can add compress (and uncompress) capabilities to the Archive Manager by installing extra command line tools. For example: zip, tar, 7zip, etc.

However, I wouldn't know what to suggest you at this point since the file doesn't have a well-know extension.

It may be a way though. There is a command called 'file' that reads the first bytes of a file and do a 'educated' guess about what the file is.

Could you post the result of this command?
```
file LATEST-IS-3.2.4
```
Regards.

---

### Post by jps2012 on 2012-03-28
Thanks for the reply, Papibe. Here's what Terminal returns: 

LATEST-IS-3.2.4: xz compressed data

I'm so new to Ubuntu, and to the command line, that even when I see folders and extensions, I'm not always sure what they mean. I know (for example) that tar files arrive compressed in a folder, and (at least in the Nautilus GUI) appear light brown. 

When they're extracted they magically turn orange. I've been waiting for them to ripen further, and start working, but I'm afraid I'm going to have to peel something off (by invoking "install," etc.). What I mean is, I'm fairly sure that uncompressing a folder doesn't automatically make its contents functional. 

But how to tell the difference from a folder whose contents need further processing, and a folder whose contents have been 'activated' (or incorporated into a program, for example) is a mystery to me. 

I apologize for the goofy, fruity joke. I'm trying to cope with my ignorance. It's amazing how much expertise there is in this forum--and amazing how much deciphering I have to do to understand what I'm sure are very basic explanations from the experts here. But I appreciate the effort you are all making to help us.

---

### Post by papibe on 2012-03-28
It looks like you don't need to install anything because xz uncompress tools are installed by default.

There are 2 possibilities: it is either a tar.xz file, or a plain .xz 

Rename the file by adding the trailing extension so it is named either:
```
LATEST-IS-3.2.4.xz
```
or
```
LATEST-IS-3.2.4.tar.xz
```
When you right click on the file, one of the options will be: 'Extract Here'. Which is the same as double click it, and extract in the same directory where the file resides.

Try that and tell us how it goes.
Regards.

---

### Post by jps2012 on 2012-03-29
Thanks, Papibe. I used the following command to rename the file: 

mv LATEST-IS-3.2.4 LATEST-IS-3.2.4.tar.xz

Then I right clicked and chose "extract here." The extraction began, and I saw an orange folder that appeared in my home folder. Then it disappeared, once the extraction completed. 

I've used SearchMonkey and Catfish to see if the uncompressed file landed somewhere else in my system (not that it SHOULD--but I'm trying to be thorough, even if thorough doesn't necessarily mean "logical"). 

I also tried the other option you mentioned, renaming the file this way: 

mv LATEST-IS-3.2.4.tar.xz LATEST-IS-3.2.4.xz

I took the same action, trying to "extract here." Same result as the first attempt: a folder was created temporarily, then disappeared once the extraction completed. 

Still lost. Any recommendations for what to do next?

---

### Post by jps2012 on 2012-03-29
Is it possible that the folder is being renamed after the extraction? I see that I do have two new folders, called 

gtk+-3.2.4 (1)

gtk+-3.2.4 (2)

---

### Post by papibe on 2012-03-29
Yes.

It looks like you extracted it twice and the second time the Archive Manager instead of overwrite it, it change slightly the name.

Do they have the same content?

Regards.

---

### Post by jps2012 on 2012-03-29
Papibe: Yes, the folders all have the same number of files. Now that (it looks like) it's been extracted, _I'm wondering what sequence of commands I should invoke to install the files. _

Do you know of a good website that lists what actions should be taken to compile/install files, based on the type of file being considered? 

Thanks, JPS

---

