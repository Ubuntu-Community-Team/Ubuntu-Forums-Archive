---
title: "Auto File Rename"
date: 2024-06-08
forum: New to Ubuntu
---

### Post by matthewjackson on 2024-06-08
Hi,

I am hoping someone is able to help me or point me in the right direction, I have tried searching but cant find anything for what i need.

I have a large film collection which i am trying to organise in to the film name and year.

the folder name only had to be the film title and year in brackets, EG film (1990)     currently they are all name with the format, type of file, and such.

As i have so many to rename all manually will take far too long and was wondering if some knows of a script that would be able to run to rename them.

Thanks in advance for any help

Matt

---

### Post by currentshaft on 2024-06-08
Can you provide one or a few examples of rename operations you'd like to automate?

---

### Post by oldfred on 2024-06-08
I have these tools in my notes.
Rename Music using id3 tags
banshee, Picard, Easytag, qmv

But have only renamed photo files with exiftool which extracts photo info for name.
And have written several line bash file to loop thru multiple folders with exiftool, although it can work on sub-folders also.

I only renamed as I ripped DVDs or CDS.
But prefer with Linux to only use underscore (no spaces) and no special characters like ().
 
If in a NTFS partition you have to be careful not to use some characters. Mount with windows_names parameter.
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20)

---

### Post by vanadium on 2024-06-10
I second the comment of Currentshaft. It is impossible to provide any help if yo do not provide information on the current file naming and organisation system. If there is no system in your current naming and organizing scheme, then proceeding manually will be your only option. Oldfred pointed to tagging mediafiles. Some applications then allow to rename/mode media files according to the contents of the tags. Still then, you will need to put order in your tags first, before you can automate.

---

### Post by TheFu on 2024-06-10
Every possible pattern of naming already in use will need to be matched using the RegEx language.  This is one of the few questions where using an A.I. engine to get an answer would be useful.

A question like:
"Using the Linux 'rename' command, take the following input filenames and create a rename command that will generate the following outputs, respectively."  Then pass in 2 columns of directory names - 
old       new

Let the AI engine figure out the patterns.

Of course, AI commonly makes mistakes, so you should test the resulting command(s) in a test area that you are 100% willing to trash.

I go out of my way to 'rename' files/directories so they don't have any spaces or special characters or punctuation. Doing this makes scripting solutions for other needs 1000x easier, since spaces in filenames/directory names are a common delimiter and will break nearly all scripts.  Best to avoid spaces and {}[]()<>~!@#$%^&*=+\|;:'"/? characters completely.

So, if I have this "Some Great Movie: Title (2004)"   ---[then I want]--->    "Some_Great_Movie_Title-2004"

The rename command can use grouping to snag parts of the input names to be put back together for the output name with substitution variables.

You can also use the BASH_REMATCH construct if you want to use bash for this.  For example, I needed to deal with TV show episodes and wanted just 3 parts of the filename.  The episode title, season and episode. Everything else would be dumped.
```
   # Regular expression pattern to match the input format
   pattern="^(.*)[_|[:space:]]+[sS]([0-9]+)[-_[:space:]]?[eE]([0-9]+)(.*)$"

   # Check if the input matches the pattern
   if [[ $1 =~ $pattern ]]; then
      title="${BASH_REMATCH[1]}"
      season="${BASH_REMATCH[2]}"
      episode="${BASH_REMATCH[3]}"
   else
      echo "Invalid input format!"
   fi
```

Of course, it isn't THAT simple. There's other chunking to split the extension off from the other parts of the filename. But in the end, the 'mv' command is used to rename the "old filename" to the "new filename".

If you do this a bunch, like most people with media collections would, you'll want to get the naming exactly like you desire.  My script actually moves files from a download location into the final storage file system, creates the desired directory name with the correct group and g+s permissions, then moves the downloaded files into that directory and renames the files to match my desired limitation.  There are probably renaming tools that would do it better, but I don't trust overly complex scripts from other people. It is a personal flaw.

---

