---
title: "Critque my first Python program"
date: 2008-01-06
forum: Programming Talk
---

### Post by DocForbin on 2008-01-06
I hacked together my first Python program last night and would appreciate any feedback so I can improve it, avoid bad habits, etc. I know there is very little error checking, but since it's just for my own use that's not a big concern. This is just a small script to automate copying songs from a rhythmbox playlist to my portable player. It also uses oggenc to convert any FLAC files to Ogg Vorbis. I'm sure this looks pretty dirty, but hey it's working :)

```

#! /usr/bin/env python
# copies songs from playlist (rhythmbox) to OUTPUTDIR, and converts any copied FLAC files to Ogg Vorbis

OUTPUTDIR='/home/adam/Desktop/playlist/'
OGGENC_ARGS='-q 7'

import sys, os, urllib, shutil

def process_song(line):
    lineArray = line.split('=')
    song = '/' + lineArray[1].lstrip('file:/')
    song = urllib.unquote(song.rstrip())
    if os.path.exists(song):
        print 'copying ' + song + '...'
        shutil.copy(song,OUTPUTDIR)
    else:
        print song, 'not found...'
    return

def flac_to_ogg():
    print '\n', 'checking for FLAC files...'
    for f in os.listdir(OUTPUTDIR):
        if is_flac(f):
            print 'converting "' + f + '" to Ogg Vorbis...'
            status = os.system('oggenc ' + OGGENC_ARGS + ' "' + OUTPUTDIR + f + '"')
            print 'status:', status
            if status == 0:
                os.remove(OUTPUTDIR + f)
    return 
            
def is_flac(song):
    if song[-5:].lower() == '.flac':
        return 1
    else:
        return 0

if len(sys.argv) == 1:
    print 'No playlist specified...'
    sys.exit(0)
playlist = sys.argv[1]
if os.path.exists(playlist):
    print 'opening ' + playlist + '...'
    f = open(playlist, 'r')
    i = 0
    for line in f:
        i = i + 1
        if i == 3: #NumberOfEntries
            print line, '\n', 'copying files...'
        else:
            if i > 3:
                process_song(line)
    flac_to_ogg()
else:
    print playlist, 'not found...'


```

---

### Post by Jessehk on 2008-01-06
My only suggestion would be to wrap your main code in a **main()** function and then do something like this:

```

if __name__ == "__main__":
    main()

```

Which will allow you to import the module into the interpretor and play around.

---

### Post by DocForbin on 2008-01-06
Thanks Jesse, that makes sense.

---

### Post by pmasiar on 2008-01-06
Not bad for a first program - looks like you have some Java experience?

Just nitpicking:
- inconsistent naming conventions, mixing var_name and varName styles. Read up PEP008 about preferred Python coding style
- when no args provided, you may print out help, including suggested usage
- I personally dislike 1-letter variable names (hard to find and replace later), I would use ff (or filename) instead of f
- is_flac() can be simplified: 
[php]
def is_flac(song):
    return song[-5:].lower() == '.flac':
[/php]

---

### Post by DocForbin on 2008-01-06
Thanks, this is the kind of feedback what I was hoping for.

> **pmasiar said:**
> 
- inconsistent naming conventions, mixing var_name and varName styles. Read up PEP008 about preferred Python coding style

I usually only use var_name for the "constants" cuz I use all caps. Then underscores for functions. Can you direct me to PEP008, will definitely read it. *edit n/m, found it :)*

> I personally dislike 1-letter variable names (hard to find and replace later), I would use ff (or filename) instead of f

Good point, I agree. I probably just used f because it was used in the examples I found for reading files/directories. I do normally use i for counters though.

> - is_flac() can be simplified: 
[php]
def is_flac(song):
    return song[-5:].lower() == '.flac':
[/php]

Nice, thanks.

No Java experience. A bit of C++, but it's been quite a few years.

Cheers

---

### Post by Quikee on 2008-01-06
Why not instead of 'f' or 'ff' just say 'file' or even better 'playlist' (and rename 'playlist' to 'playlist_filename'). The correct naming of your program much more beautiful and readable (with less need for additional documentation or comments).

[PHP]def is_flac(song):
    return song[-5:].lower() == '.flac':  [/PHP]

Additional comment - don't use 0 for false and 1 for true - use False for false and True for true. 

Also you could use 'mimetypes' module for detection of file type instead of relying on the extension (this is sooo windows like ;) ). 

For example:
[PHP]import mimetypes
import sys

arg = sys.argv[1]

mimetypes.init()
print mimetypes.guess_type(arg)
[/PHP]

---

### Post by Smygis on 2008-01-06
> **pmasiar said:**
> 
- is_flac() can be simplified: 
[php]
def is_flac(song):
    return song[-5:].lower() == '.flac':
[/php]

[php]
def is_flac(song):
    return song.endswith(".flac")
[/php]

Even better :) And its the prefered way of performing tasks like this one.

---

### Post by DocForbin on 2008-01-06
> **Quikee said:**
> Additional comment - don't use 0 for false and 1 for true - use False for false and True for true. 
ya know,  I initially wrote it using true, and when it complained changed to 1. doh  trying to write code without bothering to read documentation, hehe

> Also you could use 'mimetypes' module for detection of file type instead of relying on the extension (this is sooo windows like ;) ). 

For example:
[PHP]import mimetypes
import sys

arg = sys.argv[1]

mimetypes.init()
print mimetypes.guess_type(arg)
[/PHP]
Cool. Although guess_type() does not sound too convincing now does it :)

---

### Post by DocForbin on 2008-01-06
> **Smygis said:**
> [php]
def is_flac(song):
    return song.endswith(".flac")
[/php]

Even better :) And its the prefered way of performing tasks like this one.
Believe it or not, I did switch to this a bit ago after skimming the python style guide.

return song.lower().endswith('.flac')

handy :)

---

### Post by Quikee on 2008-01-06
> **DocForbin said:**
> Cool. Although guess_type() does not sound too convincing now does it :)

More convincing than guessing by file extension ;) I think guessing by file extension is the first guess (and the only guess for flac files) in mimetypes anyway ;)

---

### Post by Acglaphotis on 2008-01-06
[PHP]status = os.system('oggenc ' + OGGENC_ARGS + ' "' + OUTPUTDIR + f + '"')
print 'status:', status
[/PHP]

The for the second statement will always be "0", because, when you assing an os.system("*") to a variable, it will just execute it, but it will not save it's output.

The module subprocess is more adequate as shown here:

[PHP]#! /usr/bin/env python
# copies songs from playlist (rhythmbox) to OUTPUTDIR, and converts any copied FLAC files to Ogg Vorbis

OUTPUTDIR='/home/adam/Desktop/playlist/'
OGGENC_ARGS='-q 7'a

import sys, os, urllib, shutil, subprocess

def process_song(line):
    lineArray = line.split('=')
    song = '/' + lineArray[1].lstrip('file:/')
    song = urllib.unquote(song.rstrip())
    if os.path.exists(song):
        print 'copying ' + song + '...'
        shutil.copy(song,OUTPUTDIR)
    else:
        print song, 'not found...'
    returnf

def flac_to_ogg():
    print '\n', 'checking for FLAC files...'
    for f in os.listdir(OUTPUTDIR):
        if is_flac(f):
            print 'converting "' + f + '" to Ogg Vorbis...'
            process = subprocess.Popen('oggenc ' + OGGENC_ARGS + ' "' + OUTPUTDIR + f + '"', shell=True, stdout=subprocess.PIPE, bufsize=0)
            status = process.stdout
            print 'status:', status.readline()
            if status == 0:
                os.remove(OUTPUTDIR + f)
                return f 
def is_flac(song):
    return song.endswith(".flac")
def main():
        if flen(sys.argv) == 1:
            print 'No playlist specified...'
            sys.exit(0)
        playlist = sys.argv[1]
        if os.path.exists(playlist):
            print 'opening ' + playlist + '...'
            f = open(playlist, 'r')
            i = 0
            for line in f:
                i = i + 1
                if i == 3: #NumberOfEntries
                    print line, '\n', 'copying files...'
                else:
                    if i > 3:
                        process_song(line)
            flac_to_ogg()
        else:
            print playlist, 'not found...'
if __name__ == "__main__":
     main()
[/PHP]

Besides adding the subprocess part, i encapsulated your main part of the program in the function main, so i could test it as a module

---

### Post by DocForbin on 2008-01-06
> **Acglaphotis said:**
> [PHP]status = os.system('oggenc ' + OGGENC_ARGS + ' "' + OUTPUTDIR + f + '"')
print 'status:', status
[/PHP]

The for the second statement will always be "0", because, when you assing an os.system("*") to a variable, it will just execute it, but it will not save it's output.

os.system returns the exit status, doesn't it? I had some flac files that oggenc did not like due to having id3 tags and the status was 253 or something like that.

> The module subprocess is more adequate as shown here:

Thanks! I read a bit on subprocess last night but didn't quite get it.

---

### Post by Acglaphotis on 2008-01-06
> **DocForbin said:**
> os.system returns the exit status, doesn't it? I had some flac files that oggenc did not like due to having id3 tags and the status was 253 or something like that.

I misspoke myself, it *does* return the exit status, but i forgot because successful operations return 0, thus being the most common exit status i see.

---

### Post by DocForbin on 2008-01-06
I incorporated most of the suggestions and changed a few things based on the style guide. I also added some code to skip files if they already exist (including checking for ogg version for flac files), and a system beep on errors converting flac files. And it keeps track of #copied, skipped, etc. now. Looking a bit better, appreciate all the tips :)

[php]
#! /usr/bin/env python
# copies songs from playlist (rhythmbox) to OUTPUTDIR, and converts any copied FLAC files to Ogg Vorbis
# todo: print help info, maybe change os.system to subprocess, maybe error log

OUTPUTDIR='/home/adam/Desktop/playlist/'
OGGENC_ARGS='-q 7'

import sys
import os
import urllib
import shutil

def main():
    if len(sys.argv) == 1:
        print 'No playlist specified...'
        sys.exit(0)

    playlist_filename = sys.argv[1]
    if os.path.exists(playlist_filename):
        results_cnt = {'copied':0, 'skipped':0, 'converted':0, 'errors':0}
        print 'opening ' + playlist_filename + '...'
        playlist = open(playlist_filename, 'r')
        i = 0
        for line in playlist:
            i = i + 1
            if i == 3:  # NumberOfEntries
                print line, '\n', 'copying files...'
            else:
                if i > 3:
                    results_cnt = process_song(line, results_cnt)

        results_cnt = flac_to_ogg(results_cnt)

        print 'done...'
        print '--------------------------------'
        print 'copied:', results_cnt['copied']
        print 'skipped:', results_cnt['skipped']
        print 'converted:', results_cnt['converted']
        print 'errors:', results_cnt['errors']
        print '--------------------------------'
    else:
        print playlist_filename, 'not found...'
    return

def process_song(line, results_cnt):
    line_array = line.split('=')
    song = '/' + line_array[1].lstrip('file:/')
    song = urllib.unquote(song.rstrip())
    if os.path.exists(song):
        song_file = os.path.basename(song)
        if find_song(song_file):
            results_cnt['skipped'] = results_cnt['skipped'] + 1
            print song_file, 'already exists, skipping...'
        else:
            results_cnt['copied'] = results_cnt['copied'] + 1
            print 'copying ' + song_file + '...'
            shutil.copy(song,OUTPUTDIR)
    else:
        results_cnt['errors'] = results_cnt['errors'] + 1
        print song, 'not found...'
    return results_cnt
    
def find_song(song):
    found = False
    if os.path.exists(OUTPUTDIR + song):
        found = True
    elif is_flac(song):  # if flac check for ogg version 
        if os.path.exists(OUTPUTDIR + song[:-4] + 'ogg'):
            found = True
    return found
    
def flac_to_ogg(results_cnt):
    print '\n', 'checking for FLAC files...'
    for filename in os.listdir(OUTPUTDIR):
        if is_flac(filename):
            print 'converting "' + filename + '" to Ogg Vorbis...'
            status = os.system('oggenc ' + OGGENC_ARGS + ' "' + OUTPUTDIR + filename + '"')
            print 'status:', status
            if status == 0:
                results_cnt['converted'] = results_cnt['converted'] + 1
                os.remove(OUTPUTDIR + filename)
            else:
                results_cnt['errors'] = results_cnt['errors'] + 1
                print '\a'  # system beep
    return results_cnt
            
def is_flac(song):
    return song.lower().endswith('.flac')


if __name__ == '__main__':
    main()
[/php]

---

### Post by ghostdog74 on 2008-01-07
> **DocForbin said:**
> 
OUTPUTDIR='/home/adam/Desktop/playlist/'
OGGENC_ARGS='-q 7'

import sys
import os
import urllib
import shutil

Put your imports above..
```

#!/usr/bin/env ................
import sys
import os
import urllib
import shutil
OUTPUTDIR='/home/adam/Desktop/playlist/'
OGGENC_ARGS='-q 7'

```
> 
OUTPUTDIR='/home/adam/Desktop/playlist/'

can be like this, if you want.
```

root="/home"
OUTPUTDIR = os.path.join(root,"adam","Desktop","playlist")

```
makes it easier if you were to use your script in other platforms.

> 
```

    if os.path.exists(playlist_filename):

```

How about checking for if its a file, just in case user keys in a directory.
> 
```

        playlist = open(playlist_filename, 'r')
        i = 0
        for line in playlist:
            i = i + 1
            if i == 3:  # NumberOfEntries
                print line, '\n', 'copying files...'
            else:
                if i > 3:
                    results_cnt = process_song(line, results_cnt)

```

Instead of using a counter...you can use enumerate()
```

for num, line in enumerate(open(playlist_filename)):
    if num == 3: 
      ....
    elif num > 3: 
       ....
   

```
> 
```

        print 'done...'
        print '--------------------------------'
        print 'copied:', results_cnt['copied']
        print 'skipped:', results_cnt['skipped']
        print 'converted:', results_cnt['converted']
        print 'errors:', results_cnt['errors']
        print '--------------------------------'
    else:

```

you can use triple qoutes..don't have to use too many prints
```

print """
   done
   "%s"
   copied : %s
   skipped: %s
   converted: %s
   errors : %s
""" % ( "-" * 100 , results_cnt['copied'] , ........ ) 

```

> 
```

            results_cnt['skipped'] = results_cnt['skipped'] + 1
            .....
            results_cnt['copied'] = results_cnt['copied'] + 1

```

can be shortened to 
```

 results_cnt['skipped'] += 1 #not that it matters
   ..........
 results_cnt['copied'] += 1

```

---

