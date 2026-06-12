---
title: "How to NOT over-write an existing file"
date: 2014-11-18
forum: Programming Talk
---

### Post by DudeBud on 2014-11-18
Hello peeps, 

I was looking around the intarwebs for some way to neatly organize music files on our family SAMBA share.  I didn't really like my options out there, so i figured I would attempt to create my own.  

In a house of 4 teenagers, everyone is listening to music on some sort of device pretty much all the time.  We have a central Ubuntu media server connected to many great (and not so great) media clients/apps.  We are finding that at times file search and sub-folder navigation can be clumsy or non-existent on some of the devices and prove difficult when we try and play music from sub-folders and/or try to create a playlist with nested files.  Its not always the easiest.... kinda blows actually.

I found this old thread - [ [http://ubuntuforums.org/showthread.php?t=1598528](http://ubuntuforums.org/showthread.php?t=1598528) ]("http://ubuntuforums.org/showthread.php?t=1598528")
and am trying to use the script to uniformly rename all of our music files and place them all in one giant music folder (no more sub-folders).  

I'll attach my modified code.  The problem I have now is that this code will overwrite existing files.  Therefore when we have duplicate mp3's, when I run this script and dump all of our files into one giant folder some of our duplicate files may be overwritten by lesser quality ones. - How do i make sure that when this script is run that the larger mp3 file (or the one with the higher bit rate) remains in this folder and is NOT replaced by a lesser quality version?

PS: Thanks in advance for your help.


[PHP]
#!/bin/bash

# Where should all music be organized to?
music_collection="/media/TheGrid/data/Music"

# SABNZBD usage
# 1) Edit music_collection setting above if your music isn't in the "normal" place
# 2) Set this up as an SABNZBD Post Processing script

# GENERAL usage
# 1) Edit music_collection setting above if your music isn't in the "normal" place
# 2) run in a terminal as: ./mp3organizer /path_to/where_the_new_music_files/are
# Note that the path can't have any spaces.

# NOTES AND ADVANCED USAGE
# File with bad tags are stored to /[Your_music_collection]/unknown
# See the Advanced Options settings if you want to:
# a) Make backup copies
# b) Move instead of copy file from the new music location

# =============================================================================================

# ADVANCED / OPTIONAL SETTINGS
# Want all the files copied somewhere else too?#backup_dir="$HOME/mp3organizer_backups"

# Set to "copy" or "move" to make the script either copy files to your music collection and leave
# the originals where they were or move them to your music collection.
mode="copy"

# If you want the unknown files to be saved somewhere else, or to change where this script
# keeps temporary files, change these:
unknown_dir="/media/TheGrid/data/Music/Unknown_Or_Missing-Data"
working_dir="/media/TheGrid/data/Music/.MusicOrganizer_temporary_files"

# ============================================================================================
# EVERYTHING BELOW HERE IS AS IT SHOULD BE. DONT MESS WITH IT

# Make sure that a folder has been passed to the script
if [ -z "$1" ];then  
echo "Doh!  You have to pass a directory where the music is you want to organize!"
  exit
else
  echo "Working from supplied directory"
  echo "$1"        
          new_music="$1"
fi

# Make sure if a folder has been passed that it actuall exists
if [ ! -d "$new_music" ];then
  echo "Can't find the search directory $new_music"
   echo "For SABNZBD, in the admin go to Settings > Switches and set REPLACE SPACES WITH UNDERSCORSES"
  exit
fi

# Check other folders exist and make them if necessary
if [ ! -d "$working_dir" ];then
  echo "Creating $working_dir"
  mkdir $working_dir
fi

if [ ! -d "$music_collection" ];then
  echo "Creating $music_collection"
  mkdir $music_collection
fi

if [ ! -d "$unknown_dir" ];then
  echo "Creating $unknown_dir"
  mkdir $unknown_dir
fi


###OPTIONAL FEATURE
#if [ ! -d "$backup_dir" ];then
#  echo "Creating $backup_dir"
#  mkdir $backup_dir
#fi

# Copy or Move the new music files to our temporary working area to be processed
if [ "$mode" = 'move' ]; then
  find $new_music -iname "*.mp3" -exec mv {} $working_dir \;
else
  find $new_music -iname "*.mp3" -exec cp {} $working_dir \;
fi

cd $working_dir

# Work on each file one at a time
for F in ./*
do        
     if [ -f "$F" ];then
    # use mediainfo to get the track info    
   # LOTS of stuff going on here. Have to remove leading space, special chars and pad track to 0x etc.    
   # Someone smart could do this a lot more elegantly than this!                
artist=`mediainfo "$F"|grep Performer|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`                
title=`mediainfo "$F"|grep -m 1 "Track name"|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`                
album=`mediainfo "$F"|grep Album|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`                
#I commented out the next line as i did not want track numbers                
#trackno=`mediainfo "$F"|grep Track/ name/Position|awk -F: '{print $2}'|sed 's/^ *//g'| awk '{printf "%02d\n", $1;}'`
          
      echo "============================"
               echo "artist:" $artist
                echo "title:" $title
                echo "album:" $album
                #see above if statement, I removed track number                              
               #echo "trackno:" $trackno
      
# If we have an artist, album and title then we know where to nicely put this file
                        if [  -n "$artist"  ] && [ -n "$album" ] && [  -n "$title"  ];then
          # This is what we are going to call the file
                                filename="$artist ($album) - $title.mp3";
                                mv "$F" "$music_collection"
                                  fi


        #advanced naming features and directory structure building / moving (uncomment to use)
                                #filename="$trackno - $title.mp3";
                                #if [ -n  "$backup_dir" ];then
                                  #cp "$F" "$backup_dir/"
                                  #fi

                                ## If the right directory structure exists - awesome. Move the file.
                                        #if [ -d "$music_collection/$artist/$album" ];then
                                                #mv "$F" "$music_collection/$artist/$album/$filename"
                                        #else
                                          ## If not, build the whole file structure. Won't do any harm to try and create an artist directory that
                                          ## is already there - so not even checking for that.
                                                #mkdir "$music_collection/$artist"
                                                #mkdir "$music_collection/$artist/$album"
                                                #mv "$F" "$music_collection/$artist/$album/$filename"
                                        #fi

                        else
        # Don't know who it's by, what album, or what track, so moving it to UNKNOWN
                        mv "$F" "$unknown_dir/"
                                echo -e "UNKNOWN: $F \n"
                        fi

done 
                                                      [/PHP]

---

### Post by TheFu on 2014-11-18
TL;DR (everything)

>  place them all in one giant music folder 

This is a terrible, terrible, terrible, idea.  If the directory becomes corrupted, EVERY FILE INSIDE will be lost. Directories with more than 500 or so files become really slow to load too. With different OSes involved, the chance of that happening increases.  Please don't do that.

There are many, many, tools that use id3 tags to manage filenames. You can write your own, but if you insist on doing the exercise, just check if the filename already exists before renaming.  The [ABSG]("http%3A%2F%2Ftldp.org%2FLDP%2Fabs%2Fhtml%2F") is full of simple and complex examples to cover almost every scripting need. 

May be worth taking a look at easytag - it is in the repos.  

Checkout the **noclobber** setting for your shell script. **set -o noclobber** [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_06.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_06.html)
You'll need to have a more complex decision about wither to mv files or not - need to check whether the target location already has a file with that name first.

---

### Post by ofnuts on 2014-11-18
> **TheFu said:**
> TL;DR (everything)



This is a terrible, terrible, terrible, idea.  If the directory becomes corrupted, EVERY FILE INSIDE will be lost. Directories with more than 500 or so files become really slow to load too. With different OSes involved, the chance of that happening increases.  Please don't do that.

There are many, many, tools that use id3 tags to manage filenames. You can write your own, but if you insist on doing the exercise, just check if the filename already exists before renaming.  The [ABSG]("http://http%3A%2F%2Ftldp.org%2FLDP%2Fabs%2Fhtml%2F") is full of simple and complex examples to cover almost every scripting need. 

May be worth taking a look at easytag - it is in the repos.

+1 about using not using one single directory for performance reasons (for the rest, there are backups...)

EasyTag is a nice tool, bit it won't move files... 

I would first run a tool to detect potential duplicate files... conflicts maybe best resolved by hand (size isn't always a good criterion, there are good and bad MP3 encoders...). Onece the repository has been scrubbed, any reorg can take place.

---

### Post by DudeBud on 2014-11-18
LoL! Easy there TheFu.

Okay, I can see the performance issue with the massive single folder.  Scratch that... So now I have artist folders inside of the parent directory. (I can live with this)  
This mostly works, except when you pass a directory that contains spaces in the name.  (Example: "Adele - 19")
Any idea how to fix this?

```

dudebud@glad0s:~$ ./MusicOrganizer /media/TheGrid/data/Old_Music/Adele\ -\ 19/
Working from supplied directory
/media/TheGrid/data/Old_Music/Adele - 19/
Creating /media/TheGrid/data/Music
Creating /media/TheGrid/data/Music/Unknown_Or_Missing-Data
Creating /media/TheGrid/data/Music/.music_temporary_files
find: `/media/TheGrid/data/Old_Music/Adele': No such file or directory
find: `-': No such file or directory
find: `19/': No such file or directory
dudebud@glad0s:~$

```




Here is the script I am working with:

[PHP]#!/bin/bash
# Where should all music be organized to?music_collection="/media/TheGrid/data/Music"
# SABNZBD usage# 1) Edit music_collection setting above if your music isn't in the "normal" place# 2) Set this up as an SABNZBD Post Processing script
# GENERAL usage# 1) Edit music_collection setting above if your music isn't in the "normal" place# 2) run in a terminal as: ./mp3organizer /path_to/where_the_new_music_files/are# Note that the path can't have any spaces.
# NOTES AND ADVANCED USAGE# File with bad tags are stored to /[Your_music_collection]/unknown# See the Advanced Options settings if you want to:# a) Make backup copies# b) Move instead of copy file from the new music location
# =============================================================================================
# ADVANCED / OPTIONAL SETTINGS# Want all the files copied somewhere else too?#backup_dir="$HOME/mp3organizer_backups"
# Set to "copy" or "move" to make the script either copy files to your music collection and leave# the originals where they were or move them to your music collection.mode="copy"
# If you want the unknown files to be saved somewhere else, or to change where this script# keeps temporary files, change these:unknown_dir="/media/TheGrid/data/Music/Unknown_Or_Missing-Data"working_dir="/media/TheGrid/data/Music/.music_temporary_files"
# ============================================================================================# EVERYTHING BELOW HERE IS AS IT SHOULD BE. DONT MESS WITH IT
# Make sure that a folder has been passed to the scriptif [ -z "$1" ];thenecho "Doh!  You have to pass a directory with music to organize!"  exitelse  echo "Working from supplied directory"  echo "$1"          new_music="$1"fi
# Make sure if a folder has been passed that it actually existsif [ ! -d "$new_music" ];then  echo "Can't find the search directory $new_music"   echo "For SABNZBD, in the admin go to Settings > Switches and set REPLACE SPACES WITH UNDERSCORSES"  exitfi
# Check other folders exist and make them if necessary
if [ ! -d "$music_collection" ];then  echo "Creating $music_collection"  mkdir $music_collectionfi
if [ ! -d "$unknown_dir" ];then  echo "Creating $unknown_dir"  mkdir $unknown_dirfi
if [ ! -d "$working_dir" ];then  echo "Creating $working_dir"  mkdir $working_dirfi
###OPTIONAL FEATURE - needed if backup enabled#if [ ! -d "$backup_dir" ];then#  echo "Creating $backup_dir"#  mkdir $backup_dir#fi
# Copy or Move the new music files to our temporary working area to be processedif [ "$mode" = 'move' ]; then  find $new_music -iname "*.mp3" -exec mv {} $working_dir \;else  find $new_music -iname "*.mp3" -exec cp {} $working_dir \;fi
cd $working_dir
# Work on each file one at a timefor F in ./*do     if [ -f "$F" ];then    # use mediainfo to get the track info   # LOTS of stuff going on here. Have to remove leading space, special chars and pad track to 0x etc.   # Someone smart could do this a lot more elegantly than this!artist=`mediainfo "$F"|grep Performer|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`title=`mediainfo "$F"|grep -m 1 "Track name"|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`album=`mediainfo "$F"|grep Album|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`#I commented out the next line as i did not want track numbers#trackno=`mediainfo "$F"|grep Track/ name/Position|awk -F: '{print $2}'|sed 's/^ *//g'| awk '{printf "%02d\n", $1;}'`
      echo "============================"               echo "artist:" $artist                echo "title:" $title                echo "album:" $album                #see above if statement, I removed track number               #echo "trackno:" $trackno

# If we have an artist, album and title then we know where to nicely put this file                        if [  -n "$artist"  ] && [ -n "$album" ] && [  -n "$title"  ];then          # This is what we are going to call the file                                filename="$artist ($album) - $title.mp3";                                if [ -n  "$backup_dir" ];then                                  cp "$F" "$backup_dir/"                                  fi                                # If the right directory structure exists - awesome. Move the file.                                        if [ -d "$music_collection/$artist" ];then                                                mv "$F" "$music_collection/$artist/$filename"                                        else                                          # If not, build the whole file structure. Won't do any harm to try and create an artist directory that                                          # is already there - so not even checking for that.                                                mkdir "$music_collection/$artist"                                                #mkdir "$music_collection/$artist/$album"                                                mv "$F" "$music_collection/$artist/$filename"                                        fi                        else        # Don't know who it's by, what album, or what track, so moving it to UNKNOWN                        mv "$F" "$unknown_dir/"                                echo -e "UNKNOWN: $F \n"                        fi        fidone


[/PHP]

           
Almost there!
Thanks for the support!


***WOW!!! the code above DID NOT cut and paste very well. (sorry)  - If you look at my previous example, you can see the directory parameters clearer. They are unchanged in my second post, as I did not touch the intake structure.  - Any help would be great.

---

### Post by DudeBud on 2014-11-18
Also.... 

TheFu, what is ABSG?
I tried to click the link in your post but i think it might be broken.  I entered ABSG into Google and I got "Adult Bible Study Group".

---

### Post by TheFu on 2014-11-18
"advanced bash scripting guide" - it shows how to escape special characters and how to quote filenames. Filenames with spaces are always an issue in scripts.  I remove them, find that easier. Other characters commonly seen in music DBs are issues too.  I use 'rename' for this cleanup```

rename 's/ /_/g' $IN*;
rename 's/_-_/-/g' $IN*;
rename 's/-_/-/g' $IN*
```

are a few examples.

I've solved the same problem you have - wrote a script that places music by genre/artist/album/ - don't have any imaginary property, so we can always re-rip it from the source media.  Don't believe in using those online music long-term rental stores.  If I cannot transfer the asset legally in a will, then it is a rental.  ;)

---

