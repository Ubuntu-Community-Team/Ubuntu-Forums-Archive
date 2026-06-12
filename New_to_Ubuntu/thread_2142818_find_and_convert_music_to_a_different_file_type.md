---
title: "find and convert music to a different file type"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by constellanation on 2013-05-06
I've begun the huge undertaking of organizing my music (and have made a lot of progress) however one of the last things I would like to do is convert all of the various filetypes into mp3 (yes I know, it's not the best, but it plays nice with my car stereo and phone.)  

I ran a line in command that lists the various types of files that are in my music library and they are:
aud
m4a
m4p
mp3
MP3
ogg
wma


almost all of my music is organized in /home/user/Music by /artist/album

Ideally I'd love to run something that finds each instance of a file and converts it, without me having to find each file with in my music folder.

does anyone have any idea what the best way to go about this would be?

---

### Post by Svictor on 2013-05-06
I'd do that with soundconverter. Install it from the software center or :
```
sudo apt-get install soundconverter
``` 
It's pretty intuitive. Folders are added recursively so you could just add /home/user/Music and the rest would follow. Output format and folder can be configured in the preferences. If you want to use that in your car, you probably want the mp3s to be output in a specific folder from which to copy/paste.

---

### Post by constellanation on 2013-05-06
This program is so close to what I want.  I just went through it and the only thing I'm weary of is that I don't have a way to narrow down to only certain file types. For example if I tell it to scan my music folder it brings up all 80+ gb of music, I don't want it to convert every mp3 to mp3 again (and it does I just tested it on one song.) I also tried going to add file, narrow down by file type, but it still added all files with in my music folder. 

I could use this program, I just need a way to pull all non-mp3 files out of the music library.  and preferably put them back into their proper place after they have been converted, instead of having to do it manually (which if worse comes to worse, I could do).

---

### Post by papibe on 2013-05-06
Hi constellanation.

To find your mp3s:
```
find /home/user/Music -iname '*.mp3'
```

To find the files there are not mp3s:
```
find /home/user/Music -regextype posix-awk -iregex '.*\.(aud|m4a|m4p|ogg|wma)'
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by constellanation on 2013-05-06
I've never written or ran a script before, but would it be possible to use the above line 
 
> [COLOR=#000000][FONT=Ubuntu Mono]find /home/user/Music -regextype posix-awk -iregex '.*\.(aud|m4a|m4p|ogg|wma)'[/FONT][/COLOR]

and combine it with the cli for converting music into a script that automates the process?

I'll be honest the idea of pulling that large number of songs and putting them back is frightening, and I saw that it is a lot of songs after running that line.

on a side note, we can remove aud that was only one file and I went ahead and ran it through soundconverter (which appears to strip the metadata.. but there probably isn't a way around that.)

---

### Post by papibe on 2013-05-07
Here's are two versions.

Simple version:
```
find /home/user/Music -regextype posix-awk -iregex '.*\.(aud|m4a|m4p|ogg|wma)' -exec **echo** soundconverter -options '{}' \;
```

Another version:
```
#!/bin/bash
MUSIC="/home/user/Music/"

while IFS= read -d '$'\0' -r file; do
    **echo** soundconverter -options "$file"
done < <(find /home/user/Music -regextype posix-awk -iregex '.*\.(aud|m4a|m4p|ogg|wma)' -print0)

```
Replace -options, for the actual soundconverter's options you need.

Note that both version don't do the conversion, but just echo the command. Remove the word 'echo' when you feel the code is working for you.

Let us know how it goes.
Regards.

---

### Post by constellanation on 2013-05-07
If I'm reading you right, I can run the following (minus echo) and it should start converting any files in my music folder that are aud|m4a|m4p|ogg|wma to mp3 (and if I picked the right options)
> find /home/user/Music -regextype posix-awk -iregex '.*\.(aud|m4a|m4p|ogg|wma)' -exec **echo** soundconverter -b -m audio/mpeg -q -s .mp3 '{}' \;Is that right? Also what happens if I run that line with echo in it?

---

### Post by Vaphell on 2013-05-07
echo only prints out the command that would be executed without it, just so you can see if what will actually happen matches your expectations.
You will get something like
```
soundconverter -b -m audio/mpeg -q -s .mp3 file1.wma
soundconverter -b -m audio/mpeg -q -s .mp3 file2.wma
soundconverter -b -m audio/mpeg -q -s .mp3 file3.wma
soundconverter -b -m audio/mpeg -q -s .mp3 file4.wma
```
one line for each found file

---

### Post by papibe on 2013-05-07
It is safe to run the command as it is right now.

You'll see a bunch of likes like:
```
soundconverter -b -m audio/mpeg -q -s .mp3 Music/file1.m4a
soundconverter -b -m audio/mpeg -q -s .mp3 Music/file2.m4a
soundconverter -b -m audio/mpeg -q -s .mp3 Music/file3.m4a
soundconverter -b -m audio/mpeg -q -s .mp3 Music/file4.m4a
...
```
That is, echoing the commands that would be executed.

Only when you remove the echo, those commands will be actually executed. In that case you may be no output (depending on soundconverter defualt options), and it'd take much, much longer).

Regards.

---

### Post by constellanation on 2013-05-07
so I ran the echo command and it seemed right, so I copied a folder of m4a's out of the music and ran the line on it separate. It works except for one major issue. It adds one song to the gui for soundconverter and requires me to hit the convert button, it then converts the one song, and after I close the gui it reopens the gui with the next song and I have to repeat the process of hitting convert and closing the window for the next song.  Would that be something fixable with the options? I assumed that > **-b**[COLOR=#000000][FONT=arial], [/FONT][/COLOR][B]--batch
[/B][COLOR=#000000][FONT=arial]Convert in batch mode, from command line, without a graphical user interface. You can use this from, say, shell scripts.[/FONT][/COLOR] from the [soundconverter]("http://linux.die.net/man/1/soundconverter") man page would get around that?

---

### Post by Svictor on 2013-05-07
It may be a bug in soundconverter : [https://bugs.launchpad.net/soundconverter/+bug/988256](https://bugs.launchpad.net/soundconverter/+bug/988256) What version do you have?

---

### Post by Svictor on 2013-05-07
You could also use symbolic links as an intermediary step. So assuming you have created a audiotemp folder in your home directory:
```
find /home/user/Music -regextype posix-awk -iregex '.*\.(aud|m4a|m4p|ogg|wma)' -exec ln -s '{}' /home/user/audiotemp \;
```
Then you just feed the resulting files from audiotemp to soundconverter.
If you choose to output at "Same folder as the input file" soundconverter's preferences, all resulting mp3s will be in audiotemp. If you choose to output to a specific folder, you should be able to create subfolders by artist/album. This is if soundconverter finds the appropriate tags in the files.
By the way, if you need to tag many files in automatized ways, [easytag]("https://apps.ubuntu.com/cat/applications/easytag/") works pretty well.

---

### Post by constellanation on 2013-05-07
> **Svictor said:**
> It may be a bug in soundconverter : [https://bugs.launchpad.net/soundconverter/+bug/988256](https://bugs.launchpad.net/soundconverter/+bug/988256) What version do you have?

i have version 2.0.1 I'll get the newer version and try again, thanks for all your help. I'll let you know when I have a few minutes to try it out.

---

### Post by constellanation on 2013-05-07
Thank you all for your help.  After installing the newest version of soundconverter (from tar, no less. A first for me) I was able to run
```
[COLOR=#000000]*find /home/user/Music -regextype posix-awk -iregex '.*\.(aud|m4a|m4p|ogg|wma)' -exec *[/COLOR]**soundconverter -b -m audio/mpeg -q -s .mp3 '{}' \;**
```

and convert the vast majority of my files in a relatively painless manor. It did take a few hours.  And the m4as didn't work because of drm/encryption but they were in the vast minority of files so I can get around that. I ended up keeping the .wmas as well because the mp3 sounded much worse than the original and it was only a few albums worth of music I may do later by hand. 

Originally I was upset that I didn't put in an option to delete after converting to mp3, however after the m4as didn't work successful (yet made mp3s) and the wmas sounded worse I was glad it kept the original.  

Ultimately for deleting the remaining oggs, m4as, and wavs (that I realized I had later) I just searched each file type from nautilus and deleted them in bulk there.  In other words everything worked out perfectly. 

Again thank you all.

---

