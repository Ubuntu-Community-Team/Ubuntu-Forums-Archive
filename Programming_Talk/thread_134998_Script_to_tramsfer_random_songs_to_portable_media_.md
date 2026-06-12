---
title: "Script to tramsfer random songs to portable media device"
date: 2006-02-23
forum: Programming Talk
---

### Post by junior aspirin on 2006-02-23
hi, i think this is the most approriate forum to ask this.

i have very little knowlage about scripts so i was wondering if some one could help me.

i want to fill my iriver t20 (flashed to ums [http://www.mtp-ums.net/](http://www.mtp-ums.net/)) with random songs from my collection, which has 496 MB of free space

* music stored in /home/paul/music/*album name*/*track*.ogg
* device mounts to /media/usbdisk
* music to be copied to /media/usbdisk/music/
* i have mp3's and ogg's
* can only store 496MB aof music

hope some one can help me, im sure its not hard, i think i could do it myself, its just i dnt know if its posible to make it stop copying files when the player is full.

thanks in advance. :p

---

### Post by purpleturtle on 2006-02-26
The easy way would be to check the return code from the copy (cp) command and as soon as an error occurs stop copying.

---

### Post by purpleturtle on 2006-02-26
Here's a script I've knocked up that should do the trick..

When you run it, it creates an index file with all your music filenames in it (goes to file ~/MusicIndex).  It then randomly picks files from this index of files to copy over. When it has successfully copied the file, it removes the entry from the index.   It should keep doing this until the copy fails.   Then next time you run it, it will reuse the index it originally created to repeat the process, so this time you will not get the same songs included (as they were removed from this list).

Hope this helps :)   I've not tested it much...

If anyone would like to critique my scripting please do.. I'm learing bash scripting at the moment, and thought this seemed like a good challange!

Apologies for the screwed up indentation.. I don't know how you stop the web site removing leading spaces...

> 
#!/bin/bash

# randtracks
# Copy a random collection of songs from source to dest.

# Do not use ~ for these (TODO fix this)
sourced="/home/paul/music"
destd="/media/usbdisk/music"

index=~/MusicIndex
index_done=~/MusicIndexDone

function ErrorExit()
{
  echo "Error: $*" >&2
  exit 1
}

function Dbg
{
  echo "[D] $*" >&2  
}

# Make sure the source and directories exist

if [ ! -d "$sourced" ]; then
  ErrorExit "Could not find source directory $sourced"
fi

if [ ! -d "$destd" ]; then
  ErrorExit "Could not find destination directory $destd"
fi

if [ ! -e $index ]; then
  echo "Creating index $index"
  find "$sourced" -type f -name '*.mp3' -o -name '*.ogg'  > "$index"
fi

track_count=$(wc -l < "$index")

echo "Have $track_count tracks in the collection"

# Now randomly pick tracks to be copied

max_loop=$(($track_count * 2))
for((i=0; i < $max_loop && $track_count > 0; i++))
do
  line_num=$(($RANDOM%$track_count+1))

  # Pick a line at random out of the index
  src_this=$(sed -n "$line_num p" < "$index")

  Dbg "Have chosen line $line_num/$track_count, Src=$src_this"  

  # Format up the destination path
  destf="${destd}${src_this#$sourced}"

  #Dbg "From : $src_this"
  #Dbg "To   : $destf"

  # Try and create the dest directory
  mkdir -p "$(dirname "$destf")"

  if [ -e "$destf" ]; then
    echo "$destf already exists, skipping"
    # Maybe stop processing at this point
  elif cp -v "$src_this" "$destf" ; then

    Dbg "Removing line $line_num from $index"

    # Remove the line from the index
    if ! (sed "$line_num d" < "$index" > "$index.tmp" && mv "$index.tmp" "$index") ; then
      ErrorExit "Removing line $line_num from $index"
    fi

    # Write the line we have randomly picked to another file for reference
    # This is not needed
    echo "$src_this" >> "$index_done"

    # adjust counts
    track_count=$(($track_count - 1))

  else
    Dbg "Failed to copy, exiting"
    break
  fi

done

---

### Post by jerome bettis on 2006-02-26
i've wanted to do this myself for a while.

here's a python script i came up with, it's working great over here.  i hate python but it's good for stuff like this.  i tried using bash but was struggling to do a few things ... i did this in 35 minutes, not bad \\:D/

```
#!/usr/bin/env python

import sys, os, random

src_path = "/home/paul/music"
dev_path = "/media/usbdisk"
dest_path = dev_path + "/music"

# when the player only has 3 megs left, we'll stop trying to copy
# you can lower this to 0 (or anything) so it will try to fit every
# song in your collection, but consider the player might have 2 bytes
# left and you have 800000 songs
player_is_almost_full = 3000000

# returns whether or not dev_path is mounted
def player_is_mounted() : #{
    return (os.popen("mount | awk '{print $3}' | grep " + \
                        dev_path).read().replace("\n", "") == dev_path)
#}

# returns the # of bytes avail on the player
def get_free_space() : #{
    return int(os.popen("df -B 1 | grep `mount | grep " + dev_path + \
                            " | awk '{print $1}'`" + " | awk '{print $4}'") \
                            .read().replace("\n", ""))
#}

# returns the # of bytes of a given file name
def get_file_size(file_name) : #{
    return int(os.popen("ls -l \"" + file_name + "\" | awk '{print  $5}'") \
                            .read().replace("\n", ""))
#}

if __name__ == "__main__" : #{
    if (not player_is_mounted()) : #{
        print "Your mp3 player needs to be mounted on " + dev_path + \
                 " before you can write to it."
        sys.exit()
    #}
    os.popen("mkdir -p " + dest_path)

    # find our entire music collection, if it's very large this could be bad
    # it works ok over here
    file_list = os.popen("find -L \"" + src_path + \
                            "\" -type f -iname \"*.mp3\" -o -iname \"*.ogg\"") \
                            .read().split("\n")[0:-1]

    # loop until there are no more files to copy
    # if the device gets close to full we will stop too
    while (len(file_list) > 0) : #{
        # see how much the player can fit
        free_space = get_free_space()
        if (free_space < player_is_almost_full) : #{
            break       # can't really fit anything else
        #}

        # choose a random file number
        index = random.randint(0, len(file_list) - 1)

         # quotes in the file name will F everything up
        file_list[index].replace("\"", "\\\"")

        # see if it will fit on the player and copy it if so
        if (free_space > get_file_size(file_list[index])) : #{
            os.popen("cp \"" + file_list[index] + "\" " + dest_path)
        #}

        # put the last file in our list where the one we just copied was
        # if it's the last file, we'll just toss it
        if (index != len(file_list) - 1) : #{
            file_list[index] = file_list.pop(len(file_list) - 1)
        #}
        else : #{
            file_list.pop(len(file_list) - 1)
        #}
    #}
#}
``` 
let me know how it works if you try it.

---

### Post by awi on 2006-02-27
I had a similar idea some time ago, but never the time to do it (not yet I hope :)  ). Not only a random selection, but also one that holds your preferences giving more probability to your favorites songs, but still making it less pickable after n1 times, and after n1 times you could be sure of having all of your songs transfered, at least one time. Letting you choose the time period for this event. Kind of cool for an office too, don't you think? Or to have music all the time at home.
Doing a file random choose and running every time you are going to copy it, kills the all random concept. A real random selection, should give you, in average, an uniform selection on all of your tracks, as the number of copies increases.
If you use your script independently, the chances that you get all the songs, shrinks.

---

### Post by junior aspirin on 2006-02-28
hi, thanks for this, but i cannot seem to get it to get eather to work :-k 

the bash script returns "Have 0 tracks in the collection"
where as the python one, does nothing

could it be to do with simlinks? my music folder is symlinked to "/mnt/media/my music"

also on a posibly related note:
when i unmount a device ie my media player i get this error:```

unmount error
unable to eject media
>eject: unable to eject, last error: Invalid argument
```

any ideas?

---

### Post by jerome bettis on 2006-03-01
lol it does nothing?? 

"by god!  .. do you know what this means??  .... it means that this **damn** thing doesn't work at all!!!"

are you sure the folders are set right?  i can throw in some print statements to show what's going on if those are set right.   it works flawlessly for me over here.  it should just start copying stuff to it and stop when it's full or you run out of tracks, i'm kind of upset it does nothing lol.

the best reason i can come up with for it doing nothing right now, is that the file list has 0 elements.    that would mean that the find command isn't working, which probably means that the dir is set wrong or there's a slight problem somewhere.

---

### Post by junior aspirin on 2006-03-01
ok, i think its to do with the symlink. i pointed it to "/mnt/media/My Music" and it complains about the space ie it looks for "/mnt/media/My" and "music". when i point it to a file with no spaces the treminal outputs:```

Traceback (most recent call last):
  File "/home/paul/random.py", line 58, in ?
    index = random.randint(0, len(file_list) - 1)
AttributeError: 'module' object has no attribute 'randint'

```

any ideas on how to fix both these?

as a note this is how my music files are organised
```

/mnt/media/My Music/%artist% - %album%/&track Number% - %artist% - %track% - %album%.%mp3 or ogg%

%blah% is a variable
```
dont know if that helps as you can see the My Music folder is left over from windowz xp, as i dual boot, occationaly.

---

### Post by jerome bettis on 2006-03-01
ok i put quotes around the source path in the find command, so that space won't screw it up.  i also turned the option to follow symlinks on, try it now.

not sure why randint doesn't exist, it's a standard python thing, try this first and we'll go from there.

---

### Post by junior aspirin on 2006-03-01
now it just skips to the error.

do you think i need to install something from synaptic? if so what? :-k

---

### Post by jerome bettis on 2006-03-01
hah you named the script random.py didn't you?

rename it and it will work.  :cool:

---

### Post by junior aspirin on 2006-03-02
ooooo groovy, thanks. why does random, not work? or was it the .py on the end?

thanks anyway that is great!

---

### Post by psychicdragon on 2006-03-02
It was trying to import randint from itself instead of the python module random because you named the script random.py.

---

### Post by wsmith on 2009-05-21
Fill my MP3 player one-liner:

find ./ -iname '*.mp3' | sort -R | while read fn ; do if ! cp -v "$fn" /media/disk ; then rm "$fn" && break ; fi ; done


Find all .mp3 files in the current directory
Sort them randomly
Try to copy them to the media
If the copy fails [i.e. disk full], abort.

---

### Post by FatCapybara on 2009-12-10
WSmith - now that's what I call a solution. One simple, not showily obfuscated, statement.

I've got it running now and have saved it for regular use.

Thank you.

---

### Post by ghostdog74 on 2009-12-10
> **jerome bettis said:**
> 
# returns whether or not dev_path is mounted
def player_is_mounted() : #{
    return (os.popen("mount | awk '{print $3}' | grep " + \
                        dev_path).read().replace("\n", "") == dev_path)
#}

# returns the # of bytes avail on the player
def get_free_space() : #{
    return int(os.popen("df -B 1 | grep `mount | grep " + dev_path + \
                            " | awk '{print $1}'`" + " | awk '{print $4}'") \
                            .read().replace("\n", ""))
#}

# returns the # of bytes of a given file name
def get_file_size(file_name) : #{
    return int(os.popen("ls -l \"" + file_name + "\" | awk '{print  $5}'") \
                            .read().replace("\n", ""))
#}

On top of being non portable, if you have no choice to call system commands, call it and manipulate the return results inside Python. Don't pipe processes like that, its ugly and creates extra overheads.
The functionality of awk/grep etc can be done with Python itself

Also, why bother with ls -l, when Python provides these functionalities through the os module??  os.listdir() does just this, along with os.path.isdir, os.path.isfile, etc etc

---

### Post by asalapi on 2013-01-18
Although I agree with the above post that os.walk, os.path etc. would do a better --portable-- job --or, otherwise, writing a bash shell script might equally do--, as I am a python novice and a shell ignorant, I just modified the python script taking [http://ubuntuforums.org/showthread.php?t=1183011](http://ubuntuforums.org/showthread.php?t=1183011) and now it has the functionality of:
- searching several extensions (it already was there)
- fixing the maximum total file transfer size, 
- giving list of several source paths with percentage of the total size to be assigned to each one
- recreating the original folder structure

```

#!/usr/bin/env python
# coding: UTF-8
import sys, os, random

#sources of files
src_paths=["/home/asala/TEST/Infantil","/home/normal/Dropbox"]
#total Megabytes to copy
total_MbytesToCopy=100
#percentage of the above MBytes to copy from each folder
src_percent=[10,90];
#destination path
ext_dest_path="/home/asala/TEST/tao"
media_extensions=["mp3","ogg","jpg"]
#set to false if everything should go to the same folder.
recreate_folder_structure = True 
# when the destination has less than 50 megs left, we'll stop trying to copy
player_is_almost_full = 50e6
#set to true for more comments
verbose = False
#end user configuration

#end user should not touch anything below if you don't know what you are doing

file_pattern ="".join([ ' -iname \"*.'+x+'\" -o' for x in media_extensions])
file_pattern=file_pattern[:-2]
total_bytestocopy=total_MbytesToCopy*1048576



from collections import namedtuple

_ntuple_diskusage = namedtuple('usage', 'total used free')

def disk_usage(path):
    """Return disk usage statistics about the given path.

    Returned valus is a named tuple with attributes 'total', 'used' and
    'free', which are the amount of total, used and free space, in bytes.
    """
    st = os.statvfs(path)
    free = st.f_bavail * st.f_frsize
    total = st.f_blocks * st.f_frsize
    used = (st.f_blocks - st.f_bfree) * st.f_frsize
    return _ntuple_diskusage(total, used, free)


# returns the # of bytes of a given file name
def get_file_size(file_name) :
    stat_info = os.stat(file_name)
    return stat_info.st_size

if __name__ == "__main__" :
    if(not(os.path.isdir(ext_dest_path))) :
        print "The target directory must exist " + \
                 ext_dest_path + " before you can write to it."
        sys.exit()


    # find our entire music collection, if it's very large this could be bad
    # it works ok over here

    start_free_space = disk_usage(ext_dest_path).free
    actualbytestocopy_total = min(start_free_space-player_is_almost_full,total_bytestocopy)

    # loop until there are no more files to copy
    # if the device gets close to full we will stop too
    normaliz=sum(src_percent)
    for i in range(len(src_paths)):
        src_path = src_paths[i]
        print "processing "+src_path
        actualbytestocopy = actualbytestocopy_total*src_percent[i]/float(normaliz)
        copied = 0
        file_list = os.popen("find -L \"" + src_path +  "\" -type f "+file_pattern).read().split("\n")[0:-1]
        sll=len(file_list)
        if(sll>0):
            print "Randomly selecting "+str(actualbytestocopy/1024/1024)+" MB among "+str(len(file_list))+" files found."
        else:
            print "No files matched the search pattern."
        randomtrialstofit = 0
        while (len(file_list) > 0) : #{

            # choose a random file number
            index = random.randint(0, len(file_list) - 1)

             # quotes in the file name will F everything up
            file_list[index].replace("\"", "\\\"")
            try:
                filelength = get_file_size(file_list[index])

                if (copied + filelength < actualbytestocopy) :
                   foldername,filename=os.path.split(file_list[index])
                   relative_path = foldername[len(src_path):]
                   if (recreate_folder_structure):
                        ext_full_path = ext_dest_path+relative_path
                        os.popen("mkdir -p \""+ext_full_path+"\" ")
                   else:
                        ext_full_path = ext_dest_path
                   destinationfilename=os.path.join(ext_full_path,filename)
                   if os.path.exists(destinationfilename):
                       if(verbose):
                           print "Skipping "+destinationfilename+" (it exists)"
                   else:
                       if(verbose):
                           print "Copying " + (file_list[index]) #+ " to " + ext_full_path #uncomment for more destination info.
                       os.popen("cp \"" + file_list[index] + "\"  \"" + ext_full_path+"\"")
                       copied = copied + filelength
                       if(verbose):
                           print "Copied " + '%.3f'%((float(copied) / actualbytestocopy) * 100) + "%: "+str(copied/1024/1024.0)+" of "+str(actualbytestocopy/1024/1024.0)+ " Mb"    
                       randomtrialstofit = 0
                else:
                       #print file_list[index]+" too big to fit. Trying another one: "+ str(len(file_list)) + " remaining"
                       randomtrialstofit = randomtrialstofit + 1
                       if (randomtrialstofit > 499 ) :
                             if (verbose):
                                 print "500 failed attempts to find a smaller file: ABORTING "+src_path
                             break
            except (IOError,OSError):
                  print file_list[index]+ "raised an IOError/OSError exception while processing. Check permissions."
            if (index != len(file_list) - 1): #{
               file_list[index] = file_list.pop(len(file_list) - 1)
            else:
               file_list.pop(len(file_list) - 1)
        print src_path+" finished. Processing next folder."
    print "No more folders to process. Exiting."

```

---

