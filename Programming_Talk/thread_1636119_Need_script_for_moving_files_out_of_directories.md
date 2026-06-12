---
title: "Need script for moving files out of directories"
date: 2010-12-02
forum: Programming Talk
---

### Post by taseedorf on 2010-12-02
I need a simple script and have no idea how I would go about coding this.  I can write code, so just a basic idea is all I need.

Need to scan through a large list of directories and remove all files out of the sub folders and place them in the parent directory.  Also, if it's possible, only remove files from folder's with ONLY one file in them...
I have a lot of folders in a directory with e-books and would like them all out of folders... (over 1600) this could get tedious

---

### Post by Vaphell on 2010-12-02
assuming you have these 1600 folders in 1 parent directory

find <parent_dir> -type f -exec mv "{}" <parent_dir> \;
(in dir and its subdirectories find all files and perform 'move' on each of them, {} = name of the found object)
if you skip that -exec part it will simply print out the list of files that matched criteria
this doesn't meet your requirement of moving only single files though. Something more fancy than a single command would be required. Also pray that the names are unique :)

read about find, e.g. find --help and on the internet to see what it can do (and it can a lot)

if you really want to move only single files try something along the lines of
```
#!/bin/sh

IFS='
'

cd "$1"
echo "$PWD"
for dir in `find "$PWD" -type d`
do
  cd "$dir"
  count=$( ls | grep -c ^ )
  if [ $count -eq 1 ]
  then
    find "$PWD" -maxdepth 1 -type f -exec mv "{}" "$1" \;
  fi 
done

``` requires dir as a parameter (. in the parent dir will do), test it on some dummy data first

---

### Post by taseedorf on 2010-12-03
Thanks, I'll try your suggestion and post the finished script if I can get something working....perhaps it will be able to be used by more people. :)

---

### Post by Some Penguin on 2010-12-03
Shouldn't be too bad in Perl, and should be pretty simple in Python as well.  Something to start with:


```

use strict;
use Symbol;
use File::Copy;  # more flexible than built-in rename
use File::Spec;  # more reliable than basename

my @filesToMove = ();

# not recursive, obviously; that could be done with minor modifications
# (basically, create a stack or queue initialized with @ARGV, and add
# -d directories)
for my $dirName (@ARGV) {
  (-d $dirName) || die "'$dirName' is not a directory!";
  my $dirHandle = gensym();
  opendir($dirHandle, $dirName) || die "Failed to opendir '$dirName':  $!";
  my @allFilenamesRelativeToDirName = readdir $dirHandle;
  my @allFilenamesRelativeToHere = map { $_ = "${dirName}/" . $_ }
     @allFilenamesRelativeToDirName;
  # only count normal files, not directories or symlinks
  my @normalFilenames = grep { -f } @allFilenamesRelativeToHere;
  if (scalar(@normalFilenames) == 1) {
     push @filesToMove, $normalFilenames[0];
   }
  closedir($dirHandle);
}

for my $oldFullyQualifiedFile (@filesToMove) {
   my ($volume, $directories, $basefile) = splitpath($oldFullyQualifiedFile);
   if (-e $basefile) {
       print "Not overwriting already-existing $basefile...\n";
   } else {
      move($oldFullyQualifiedFile,".") || die "Move of $oldFullyQualifiedFile failed:  $!";
   }
}

```

It's untested (haven't even bothered running it, this is just fiddling) and fails to deal with certain not implausible cases.  For instance, it should probably track all basenames it sees and complain if any are duplicated, because while the '-e' existence check would reduce the likelihood of clobbering files, it's not really specified which would win the race and therefore it might be useful to not move any of the files and instead warn the user.

---

