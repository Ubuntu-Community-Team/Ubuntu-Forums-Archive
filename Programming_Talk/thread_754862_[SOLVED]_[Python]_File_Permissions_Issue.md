---
title: "[SOLVED] [Python] File Permissions Issue"
date: 2008-04-14
forum: Programming Talk
---

### Post by themusicwave on 2008-04-14
Good morning everyone,

So I have this python program at work that is essentially an installer for another application.  It copies all kinds of files and moves things around, edits config files, build databases and such.

It's also meant to be run on Windows XP ( I know, I know...)

The issue I am running into seems to be with file permissions.  It usually occurs when I try to erase a file.  It will through a Windows Error stating that Access is denied.

I think the issue may be due to the fact that the file I am trying to erase is in a directory above my current one.  I am running as an admin so I have no idea why I can't remove the file.

The file isn't open currently.

I also run into an issue when I put the installer on a CD-ROM.  Basically, I am trying to read a SQL file off the CD-ROM to create a database.  Once again Windows tells me I can;t do that.  If I run the exact same file with the exact same folder structure off of the hard drive it works....weird...

Any ideas would be great.

---

### Post by ghostdog74 on 2008-04-14
you can look at one of the [demo script]("C:\Python24\Lib\site-packages\win32\scripts\killProcName.py") in windows module. or you can just use Window's own del command by giving a call to it through os.system or something.

---

### Post by themusicwave on 2008-04-14
Currently I am using pythons os.remove and shutil.rmtree functions.

What I mainly am confused by is why they don't seem to work.  When I run the program it fails, yet logged in as the same user I can go delete the files manually with no problem.

---

### Post by ghostdog74 on 2008-04-14
while i can't answer you as I don't play with Windows much , here's another [reference.]("http://aspn.activestate.com/ASPN/docs/ActivePython/2.5/pywin32/Windows_NT_Files_.2d.2d_Locking.html")
you can have a look

---

### Post by themusicwave on 2008-04-14
Well through some more testing I noticed that the file is st to Read-Only.  This means my script can't delete it.  C# can;t do it either.  If I turn off  Read-Only I can then erase it....

Now the problem is how do I set all the file permissions to allow writing/deleting.

---

### Post by ghostdog74 on 2008-04-14
In unix, its done like this :os.chmod(file, 666). 
check the Python doc for os.chmod() and see if it says anything about  its usage in windows.

---

### Post by themusicwave on 2008-04-14
I figured it out.  It was the read only flag that was causing the problem.

I knew about chmod on Linux, but I didn't realize read only on windows mad something undeletable.  The incredibly bizarre part is that you can manually delete a read only file, but not programatically.  That threw me for a loop because I figured it should be the same regardless.  I guess Windows does something similar to my solution.  When you delete a read only file they must first set the read only flag to false and then erase it.  Very strange...

I created this handy little function to do a recursive chmod of a directory to make them writable.  It also makes them deletable.  Of course you need permission to change the permissions for it to work.

[PHP]
import os
import stat

def setWritePermission(path):

    #set this folder to writeable
    os.chmod(path,stat.S_IWRITE)
    
    #step through all the files/folders and change permissions
    for file_ in os.listdir(path):

        filePath = os.path.join(path,file_)

        #if it is a directory, doa recursive call
        if os.path.isdir(filePath):
            setWritePermission(filePath)

        #for files merely call chmod    
        else:
            os.chmod(filePath,stat.S_IWRITE)
[/PHP]

Now I simply use that function to change the permissions of the whole tree before I try to call shutil.rmtree.  Works great.  So I learned something about file permissions and got to use some recursion.  Today is off to a good start.

Kids you may think recursion sucks, but look it's useful! :)

---

