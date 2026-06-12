---
title: "Perl script to do some renaming?"
date: 2005-11-01
forum: Programming Talk
---

### Post by Stormx on 2005-11-01
Is it possible for a perl script to capitalize the first letter of words of directories within a directory. e.g. web site backup to Web Site Backup. It doesn't have to be recursive, so no sub-dirs.

I'm pretty sure it could be done with regex, but I've never really touched in perl before, so ;-)

Thanks in advance

---

### Post by 23meg on 2005-11-01
[chcase]("http://www.blemished.net/chcase.html") is your thing.

---

### Post by Stormx on 2005-11-01
Handy, but it seems to not rename directories, even when I pass it -d

USAGE:
chcase [-terdlouCcqn] [-x '<perl exp>'] FILE...

       -t       : Test mode (don't actually rename any files)
       -e       : Print examples
       -r       : Rename recursively
       -d       : Also rename directories
       -l       : Rename & follow symbolic links (default is not to)
       -o       : Overwrite if file exists
       -u       : Change to uppercase (default is lower)
       -C       : Capitalize each word
       -c       : Capitalize first character only
       -q       : Quiet mode (no output)
       -n       : No escape characters (for bold/inverse output)
-x '<perl exp>' : Perl expression to operate on filename
                  like s/// or tr///  (you need the quotes)
                  case of filename not changed when this option used

At the moment, I have it set up like
/music/some band - some album/various files here.mp3
It renames the files, but not the directories, when I pass it:

chcase -dCor /media/space/music/

---

### Post by Stormx on 2005-11-01
Hey. I used this one-liner to do the renaming!

find . -type d | sort -r | while read dir; do old=$(basename "$dir"); dir=$(dirname "$dir"); new=$(echo "$old" | perl -pe 's/((?:^|\W)\w)/\U$1/g'); if [[ $new != $old ]]; then echo "$dir/$old ==> $dir/$new"; mv "$dir/$old" "$dir/lolkuber"; mv "$dir/lolkuber" "$dir/$new"; fi; done

What it does: Finds directories, sorts. Then loops through them. It makes a variable called new that uppercases the directory name. Then it checks whether this is different to the real name.

If it is, it renames the directory to "lolkuber", then to the uppercase equivilent. Why do this? Because FAT sees the uppercase and lowercase names as the same, and doesn't rename!

**I didn't write this, and I forget the name of the person who did (reply and i'll put your name here)**

Very very small :) works :)

---

