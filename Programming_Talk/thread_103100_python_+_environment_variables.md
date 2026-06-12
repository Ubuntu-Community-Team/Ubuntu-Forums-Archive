---
title: "python + environment variables"
date: 2005-12-13
forum: Programming Talk
---

### Post by Gandalf on 2005-12-13
Hello,

how can i ask environment variables from python? i have somthing like :
import sys
dirs = sys.argv[1:]

i want it to be something like
dirs = ( $NAUTILUS_SCRIPT_SELECTED_URIS )

so how to put the value of NAUTILUS_SCRIPT_SELECTED_URIS to dirs ???

thx

---

### Post by toojays on 2005-12-13
It's something like this:```
import os
dirs = os.environ['NAUTILUS_SCRIPT_SELECTED_URIS']
```

---

### Post by Gandalf on 2005-12-13
[QUOTE=toojays]It's something like this:```
import os
dirs = os.environ['NAUTILUS_SCRIPT_SELECTED_URIS']
```[/QUOTE]
Thanks for your reply it worked this way though i'm still having a problem which i can't figure out how to solve, in fact what im doing is modifying a nautilus script that play selected files (and also recursively into directorie) in XMMS but as you know nautilus will not pass arguments if it is launched from an NFS/SFTP/SMB/etc... mounted directories but the envirement variables will still be here; the original code which i modified it a bit for other issues is
```
#!/usr/bin/python
#
# simple script to recurse a subtree, find all the mp3 and queue them to
# XMMS.
#
# Please modify this script!  My python is rusty at best.
#
# Travis Hume -- travis@usermail.com
# Thu Oct 24 11:06:54 2002
#
# Barak Korren - ifireball@yahoo.com
# Sat Apr 03 2004
#   Some bugfixes, now preserves alphanumerical file-ordering in 
#   sub-directories
#
# Wael Nasreddine - gandal@siemens-mobiles.org
# Tue Dec 13 2005
#   If only one non-supported file is selected program will not hang (endless loop)
#   If nothing to pley display a dialog about it

import sys, glob, os, os.path, dircache

def isAudioFile( f ):
    # to support additional file types just add their appropriate
    # extentions to this list (lower case).
    file_types = ['.mp3','.ogg','.wav','.wma']

    p,ext = os.path.splitext(f)
    try:
        file_types.index(ext.lower())
    except:
        return False

    return True


# change this to something other than None to make the script
# follow symlinks
follow_links = None

def find_mp3s( dirs=None ):
    """ finds all mp3 files rooted at dirs and returns them as a list """
    if not dirs:
        return []

    if os.path.isfile(dirs[0]) and not isAudioFile(dirs[0]):
	return []

    mp3s = []
    while dirs:
        if os.path.isfile(dirs[0]) and isAudioFile(dirs[0]):
            mp3s.append(dirs[0])
            dirs = dirs[1:]
        elif os.path.isdir(dirs[0]):
            found_dirs = []
            for f in dircache.listdir( dirs[0] ):
		p = dirs[0] + "/" + f;
                if os.path.isfile(p) and isAudioFile(p):
                    mp3s.append( p )
                elif os.path.isdir( p ) and not f.endswith( "/proc" ):
                    if not os.path.islink( p ) or follow_links:
                        found_dirs.append( p )

            dirs = found_dirs + dirs[1:]

    return mp3s

dirs = sys.argv[1:]
dirs.reverse()
mp3s = find_mp3s( dirs )
#inf = "";
#for mp3 in mp3s:
#  inf = inf + '"' + mp3 + '"' + "\n"
#os.execvp("zenity", ['zenity','--info','--text=' + inf] )
if len(mp3s) > 0:
	os.execvp("xmms", ['xmms','-p'] + mp3s )
else:
	os.execvp("zenity", ['zenity','--info','--text=Nothing to play'] )
```

can you please guide me or modify it for me? because it's a cool script to play (or to queue into the playlist by replacing -p with -e) files with XMMS too bad it need to modified in order to support NFS,SFTP,etc....

---

### Post by toojays on 2005-12-13
Sorry, but I'm not quite clear about what the problem is.

---

### Post by Gandalf on 2005-12-13
[quote="About Nautilus Scripts"]
All executable files in this folder will appear in the Scripts menu. Choosing a script from the menu will run that script.

When executed from a local folder, scripts will be passed the selected file names. When executed from a remote folder (e.g. a folder showing web or ftp content), scripts will be passed no parameters.

In all cases, the following environment variables will be set by Nautilus, which the scripts may use:

NAUTILUS_SCRIPT_SELECTED_FILE_PATHS: newline-delimited paths for selected files (only if local)

NAUTILUS_SCRIPT_SELECTED_URIS: newline-delimited URIs for selected files

NAUTILUS_SCRIPT_CURRENT_URI: URI for current location

NAUTILUS_SCRIPT_WINDOW_GEOMETRY: position and size of current window
[/quote]

the above quote is from the nautilus scripts folder, i guess you know what i'm talking about now, the above script is made for parameters passed to scripts but since it doesn't pass parameters for NFS folders it must be changed in a way to work with the above envirement variables instead...

---

### Post by toojays on 2005-12-14
I don't mind answering small questions, but I'm not really interested in rewriting this script.

---

### Post by cwaldbieser on 2005-12-14
[QUOTE=Gandalf]the above quote is from the nautilus scripts folder, i guess you know what i'm talking about now, the above script is made for parameters passed to scripts but since it doesn't pass parameters for NFS folders it must be changed in a way to work with the above envirement variables instead...[/QUOTE]
So couldn't you just do something like:
```

dirs = sys.argv[1:]
if len(dirs) < num_required_params: #Not sure how many required params there are...
     dirs = []
     dirs.append(os.environ["VARIABLE_1"])
     #etc.

```

---

