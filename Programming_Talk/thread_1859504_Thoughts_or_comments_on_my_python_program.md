---
title: "Thoughts or comments on my python program"
date: 2011-10-13
forum: Programming Talk
---

### Post by mushy365 on 2011-10-13
I am in the process of trying to improve my ubuntu knowledge. So i had installed samba server and apache, so that i can share my media mp3 etc with my family. I gave them the option of downloading the movies from a webpage to their own computers or to stream it from my samba share i set up. 

I realised that having the files in both the /var/www/ and /srv/dropbox (share set up for samba) was doubling the amount of space taken up by my media as it would be on my hard drive twice. 

As samba was the least used, i decided to keep all my media in /var/www and only move files over as and when i need to, it was a bit akward, because sometimes id want to move over about 5 movies to samba and it would take a long time, so i thought it would be a good idea to automate the task, and said it would be a perfect time to try and make something in python and get round to using a .conf file. 

This is what i came up with, it runs in command line and takes arguments, the way i parse the arguments might be stupid, it seems wrong when i was doing it, but im not sure of the proper way to do it. 

basically the program lets me set a source folder "src" amd a destination folder "dst"
Then sync the src folder with the dst folder, with other options of deleting all files or certain file types from the dst folder. 

I wanted to make sure i didnt mess up and lose all the media so the program does not delete from the src folder at all. 

its got options 

./cpy.py -l src   
[lists all files in source folder]
./cpy -c song.mp3 -o songrenamed.mp3
./cpy -d *.mp3 [delete all mp3 files from dst folder]
./cpy -sync   [syncs src and dst folder with same files]
./cpy -sync -v [syncs src and dst folder and lists files in dst folder that are not in src folder]
./cpy -sync -d [syncs src and dst and deletes files in dst folder that are not in src folder]
./cpy -path src [displays current path of src]
./cpy -set src /var/www/ [sets current path of src to /var/www/]


so here is the code 
**./cpy.py**
```

#!/usr/bin/python
import os, glob, shutil
import sys
import ConfigParser

config = ConfigParser.RawConfigParser()
config.read('cpy.conf')

dropbox_path = config.get('paths','dst')
www_path = config.get('paths','src')

def set_dstpath(path):
    if os.path.isdir(path):
       config.set('paths','dst',path)
       with open ('cpy.conf', 'wb') as configfile:
          config.write(configfile)
       print "[Notice]dst path changed to " + path 
    else:
       print "Invalid folder " + path

def set_srcpath(path):
    if os.path.isdir(path):
       config.set('paths','src',path)
       with open ('cpy.conf', 'wb') as configfile:
          config.write(configfile)
       print "[Notice]src path changed to " + path 
    else:
       print "Invalid folder " + path

def syncfolders(cmds):
    files_to_copy = 0
    files_to_delete = 0
    files_copied = 0
    files_deleted = 0

    os.chdir(www_path)
    ffiles = glob.glob("*.*")
    for f in ffiles:
      if not os.path.exists(dropbox_path + f):
        files_to_copy = files_to_copy + 1
    for f in ffiles:
      if not os.path.exists(dropbox_path + f):
         files_copied = files_copied + 1
         print "**Copying file" + str(files_copied) + " of " + str(files_to_copy) + " : " + f
         shutil.copyfile(www_path + f, dropbox_path + f)

    os.chdir(dropbox_path)
    ffiles = glob.glob("*.*")
    for f in ffiles:
      if not os.path.exists(www_path + f):
        files_to_delete = files_to_delete + 1
        if(cmds == '-v'):
          print "**Excess file: " + f
        
        elif (cmds == '-d'):
          os.remove(dropbox_path + f)
          print "** File Removed :" + f
    if(cmds == "none"):
      print "Sync shows there are " + str(files_to_delete) + " extra files in dropbox !"

if(len(sys.argv) > 1):
  if(sys.argv[1] == '-d'):
     if(len(sys.argv)>2):
        fname = sys.argv[2]
        os.chdir(dropbox_path)
        for f in glob.glob(fname):
           os.remove(dropbox_path + f)
           print "** File Removed :" + f
        
     else:
        print "Usage: cpy.py -d [filename]"

  elif(sys.argv[1] == '-l'):
        if(len(sys.argv)>2):
           if(sys.argv[2] == "src"):
              os.chdir(www_path)
              avi_files = glob.glob("*.*")
           elif(sys.argv[2] == "dst"):
              os.chdir(dropbox_path)
              avi_files = glob.glob("*.*")
           else:
              print "Invalid option " + sys.argv[2]
              print "Usage: cpy.py -l src|dst"
              exit()
           
           for f in avi_files:
               print f
        else:
           print "Usage: cpy.py -l src|dst"
  elif(sys.argv[1] == '-c'):
      #only copys one way, from src to dst
      if(len(sys.argv)>2):
         ftocpy = sys.argv[2]
         if(sys.argv[3] == '-o'):
            #output as different name
            if(len(sys.argv)>4):
              # 4th arg is new output filename
              outputfile = sys.argv[4]
            else:
              outputfile = ftocpy
         if not os.path.exists(dropbox_path + outputfile):
         #does not exist in destination
         #check if it exists in source
            if os.path.exists(www_path + ftocpy): 
               print "Copying file " + ftocpy + " to dropbox ..."
               shutil.copyfile(www_path + ftocpy, dropbox_path + outputfile)
               print "Finished copying file " + ftocpy
            else:
              print "Couldnt find source file"
         else:
           print "File already exists in dropbox"
 
      else:
          print "Usage: cpy.py -c [file to copy to dropbox]"

  elif(sys.argv[1] == '-path'):
      if(len(sys.argv) > 2):
        if(sys.argv[2] == 'src'):
           print "src path = " + www_path
        elif(sys.argv[2] == 'dst'):
           print "dst path = " + dropbox_path
        else:
           print "Invalid path name" + sys.argv[2]
      else:
        print "Usage: ./cpy.py -path src | dst"
  elif(sys.argv[1] == '-set'):
      if(len(sys.argv) > 3):
        if(sys.argv[2] == 'dst'):
           set_dstpath(sys.argv[3])
        elif(sys.argv[2] == 'src'):
           set_srcpath(sys.argv[3])
        else:
           print "Invalid argument: " + sys.argv[2] + " user src or dst"
      else:
        print "Usage: ./cpy.py -set src /var/www/"

  elif(sys.argv[1] == '-sync'):
    if(len(sys.argv) > 2):
      if(sys.argv[2] == '-v'):
         syncfolders("-v")

      elif(sys.argv[2] == '-d'):
          syncfolders("-d")
      else:
         syncfolders("none")
    else:
       syncfolders("none")

```[B]cpy.conf
[/B]```

[paths]
src = /var/www/
dst = /srv/dropbox/

```

---

### Post by endontoddy on 2011-10-16
Why not setup a symbolic link between your media directory and your dropbox/www directories? Then the data only need exist in one place but all of it is accessible in multiple places

---

### Post by mushy365 on 2011-10-16
a symbolic link? How do you set that up

---

### Post by endontoddy on 2011-10-16
using the 'ln' command. So if you had a folder: /var/www/media containing all the files you want to share, you could create a link with:

```
ln -s /var/www/media /srv/dropbox/media
```Now if you look under /srv/dropbox/media you will find everything that is in /var/www/media. There is only one copy of the files but you can access them from two different locations in your file system :)

---

### Post by mushy365 on 2011-10-16
thats awesome, i guess it makes my program obsolete, but its still awesome. The more you use ubuntu the more awesome you find out it is. 

The sad thing is, im learning all this stuff and commands and in two weeks ill be flying off to australia to backpack for a year and ill forget it all by the time i come back.

---

### Post by llanitedave on 2011-10-16
Ummm, backpacking in Australia is not a sad thing.  Anything you've forgotten, you can relearn with a broader perspective than before.

---

