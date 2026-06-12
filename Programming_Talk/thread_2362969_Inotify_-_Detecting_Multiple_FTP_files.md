---
title: "Inotify - Detecting Multiple FTP files"
date: 2017-06-04
forum: Programming Talk
---

### Post by theshadow1234 on 2017-06-04
Hello,

I work for a company that uses ftp to transfer multiple .zip files and uploads them to an ftp server. Once thier uploaded we get a notification from the user that thier files were transferred and we manually move them to a different location for storage. We use Ubuntu 14 for our ftp server.

To make this daily task more easier, i've been reading up on inotifywatch and learning some scripts for beginners. Please understand that i am not a programmer so its difficult for me to figure this out so i need some advice if possible. :)

So this is what i've done so far. I've created a script using inotifywatch to watch a dir where these incoming files are being transferred to and then move them  to a different path on the same server. 

The problem i am having is that when it detects an event -e CREATE MOVE in the Watch dir, it sends incomplete or no files files to the target director. I believe this is because the transfer is still in progress. 

So for example.

DIR1 = /Some/Path/To/Watch
DIR2 = /Some/Path/To/Completed

Someone creates a folder from their remote ftp client called NEWFOLDER in DIR1 on our FTP server. Then they start transferring multiple zip files to  /Some/Path/To/Watch/NEWFOLDER/*.zip1, zip2, zip3.etc... My script does not know when the transfer is complete so it can call the command to move the completed NEWFOLDER  to DIR2. 

Is there a trigger or event that INotifywatch can use when files are completed transferring or is there another solution?

An example would help alot.
Thanks for you help.

---

### Post by Rocket2DMn on 2017-06-05
I'm not sure you can determine for certain when a transfer is complete just by observing the file system.  I suspect the closest bet would be to check for the "close_write" event that inotifywatch specifies on its man page for each file separately.  I don't think that FTP guarantees that a file wouldn't be opened and closed more than once during a transfer though, particularly if the server and/or client handle disconnect/resume automatically.  A heuristic approach may be to copy files from DIR1 to DIR2 when you believe a file transfer is completed (like a new file is created or modified, then later closed), but not delete the file from DIR1 until some timer has expired (e.g. the file hasn't been modified for 24 hours).

If you want to detect multiple files in NEWFOLDER being created in a single transfer request, you may need hooks into the FTP server to make a more accurate determination about when a transfer really is complete, assuming the server even has that information (I've never looked at the internals of a FTP server).  Again, the heuristic approach may help you avoid prematurely deleting files, but it still is not a 100% guarantee.  I suspect you would want your users to be aware of your policy as well.

---

### Post by papibe on 2017-06-05
Hi theshadow1234. Welcome to the forum ):P

A few thoughts:

Check inotify's close_write event (as Rocket2DMn mentioned it)

You can use 'fuser' to see if a process has open the file. If the file is being transfer, you'll get a process ID.

If you have the authority to modify the upload procedure, so that the users include a md5 file of the zip files, you'll be able to check when the file has been uploaded completely by checking the sums. For instance:
```
$ ls
file1.zip  file2.zip  file3.zip

$ md5sum *.zip > list.md5

$ ls
file1.zip  file2.zip  file3.zip  list.md5

$ cat list.md5 
60b725f10c9c85c70d97880dfe8191b3  file1.zip
388a137c2f8b8a8920a19544844d7dea  file2.zip
433722f1bb7c70d050e52a3e8107a460  file3.zip

```
Hope it helps. Let us know how it goes.
Regards.

---

