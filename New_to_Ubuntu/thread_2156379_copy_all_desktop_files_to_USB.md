---
title: "copy all desktop files to USB"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by ub9876 on 2013-06-21
12.04
how do I simply copy all my desktop files to my USB drive???

---

### Post by Uly55es on 2013-06-21
Plug in your USB drive. Open Nautilus (the file manager, it's the home icon in the launcher), and click on "Desktop" on the left bar. Then select all your files and drag them into the USB drive (which will appear in the left bar under the label "devices"). Here you are ;)

---

### Post by monkeybrain2012 on 2013-06-21
What do you mean "desktop files"? Do you mean files on your desktop or .desktop files? Just plug a usb drive in and copy and paste, or if your usb drive shows up as /media/xxxxxxxx
and you want to copy all the files on your desktop, go to terminal and do

cp Desktop/* /media/xxxxxxx

---

### Post by TheFu on 2013-06-21
> **ub9876 said:**
> 12.04
how do I simply copy all my desktop files to my USB drive???

The answer depends on whether you need userid/groupid and other permissions data retained AND what the format of the USB drive file system is.

Sure, you can simply copy and paste using a GUI tool, but that might not leave you with useful data that can be recovered later.

In the most likely scenario where you do care about ownership, groups, permissions and the USB drive is FAT32 or some other non-Linux file system, then I'd use the tar command to create an archive with all that data inside, then use gzip to compress the file - leaving me with a .tgz file that I can move to any file system and it will retain permissions for me.  The downside is that editing the files contained inside the .tgz file can be a hassle.

Hope this helps.

---

### Post by monkeybrain2012 on 2013-06-21
> **TheFu said:**
> The answer depends on whether you need userid/groupid and other permissions data retained AND what the format of the USB drive file system is.

Sure, you can simply copy and paste using a GUI tool, but that might not leave you with useful data that can be recovered later.

In the most likely scenario where you do care about ownership, groups, permissions and the USB drive is FAT32 or some other non-Linux file system, then I'd use the tar command to create an archive with all that data inside, then use gzip to compress the file - leaving me with a .tgz file that I can move to any file system and it will retain permissions for me.  The downside is that editing the files contained inside the .tgz file can be a hassle.

Hope this helps.

If those files are on the desktop chances are they don't need any special permission (seeing that op probably doesn't know how to copy system files there) , as for making an archive you can just use file roller to make a zip file instead of a tar file (OP may want to extract them in a non Linux system), just highlight all the files to be included in the archive, right click and choose "compress" and that's it.

---

### Post by TheFu on 2013-06-21
> **monkeybrain2012 said:**
> If those files are on the desktop chances are they don't need any special permission (seeing that op probably doesn't know how to copy system files there) , as for making an archive you can just use file roller to make a zip file instead of a tar file (OP may want to extract them in a non Linux system), just highlight all the files to be included in the archive, right click and choose "compress" and that's it.

I don't really use GUI tools for this stuff - does "file roller" maintain permission bits correctly inside a ZIP?  If not, that can be an important aspect and a great reason to use TAR even if user and group ownership is not important.  Still, for some files in $HOME, permissions are absolutely critical - ~/.ssh/ and some IM clients store passwords in plain text - I'd hate to have those available to other people on the system after a restore because the permission bits were lost.

OTOH, if these are purely data files, then most likely the permission bits don't matter at all and whatever copy method is used will be just fine.

I just hate over simplifying things when there are significant reasons where that can cause problems.  However, I must admit that prior bosses dinged me on annual reviews for not providing the most likely answer to their question and instead providing 3-5 different options based on different assumptions about their true requirements.

---

### Post by monkeybrain2012 on 2013-06-21
> **TheFu said:**
> I don't really use GUI tools for this stuff - does "file roller" maintain permission bits correctly inside a ZIP?  If not, that can be an important aspect and a great reason to use TAR even if user and group ownership is not important.  Still, for some files in $HOME, permissions are absolutely critical - ~/.ssh/ and some IM clients store passwords in plain text - I'd hate to have those available to other people on the system after a restore because the permission bits were lost..


Well would you scatter files for which "permissions are absolutely critical" all over your desktop? It is possible, but not a very likely scenario. :) I use whatever tools which are most convenient for the job at hand,  why not use the gui if it is easier for the job? There are times where the cli is easier but this is probably not one of them. Many non Linux users are scared off Linux because they have the misconception that you have to use the command line for even the simplest tasks in Linux (so have to memorize gibberish, or look for them somewhere to cut and paste) I try not to feed into that impression. :)


> I just hate over simplifying things when there are significant reasons where that can cause problems.

I would say  it is better to simplify things appropriate for your audience and the question at hand instead of confusing them with irrelevant details. :)

---

### Post by TheFu on 2013-06-22
> **monkeybrain2012 said:**
> Well would you scatter files for which "permissions are absolutely critical" all over your desktop? It is possible, but not a very likely scenario. :) I use whatever tools which are most convenient for the job at hand,  why not use the gui if it is easier for the job? There are times where the cli is easier but this is probably not one of them. Many non Linux users are scared off Linux because they have the misconception that you have to use the command line for even the simplest tasks in Linux (so have to memorize gibberish, or look for them somewhere to cut and paste) I try not to feed into that impression. :)




I would say  it is better to simplify things appropriate for your audience and the question at hand instead of confusing them with irrelevant details. :)

I think we agree to a point. I prefer to use the simplest solution too and to make it the easiest for new-ish users, but I try not to make any assumptions about their need - since I have no idea what "files" she/he is trying to copy. They could be programs or data - I don't know.  
As I'm writing this, I don't remember if the original question was for "desktop" or HOME backups either.  There are many files under $HOME that need correct permissions.  Further, if we teach someone that drag and drop copy for everything on the desktop is how you make a backup, what happens when they want to backup other files where permissions ARE critical?  

Still, I could be completely wrong ... again.  I just noticed this was in the "absolute beginners" area. Should I stay out of here?

Anyway - I apologize if I've scared anyone by suggesting that a tar program be used. I'm fairly certain that a GUI archive manager will create and read tar files on most platforms.  Because I wouldn't assume a specific program was installed, I didn't name one.  Not everyone runs the default desktop, so I don't like to assume that either.

I suppose there is a reason I don't get paid to do end-user support.  I'll try to do better. Promise.

---

