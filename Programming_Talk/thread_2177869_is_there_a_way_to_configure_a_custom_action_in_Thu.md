---
title: "is there a way to configure a custom action in Thunar to skip copy?"
date: 2013-09-30
forum: Programming Talk
---

### Post by sam_baker2 on 2013-09-30
hi,
Is there a way to make a custom action in Thunar that will allow one
to skip copy?

For example, I have a music folder with many sub-folders under it that I add 
music files to from time to time. After a period of time I back-up by simply
copying the main folder and pasting it into my back-up hard-drive. I only
want to backup the new files, not copy over all the old files. Nautilus has
a feature that allows one to "apply this to all files" if one choses to not
replace any old file, only copy new files. I don't see anything like this
on Thunar (or have I missed it?).

---

### Post by erind on 2013-10-03
> **sam_baker2 said:**
> hi,
Is there a way to make a custom action in Thunar that will allow one
to skip copy?

[...]

One way to do that is using *rsync*, whose default behavior is to copy only new files from source to destination. The code below will get you close to Nautilus behavior.
Create a file, call it, say **incremental_paste.sh**, place it in your *home* or *~/bin* directory, make it executable, and add its path to Thunar's custom actions, see below:
> 
Name: [COLOR=#0000ff]*              Paste Here (Incremental)*[/COLOR]
Comments:[COLOR=#0000ff]    *Incremental Paste using rsync*[/COLOR]
Command:     [COLOR=#0000ff]*/home/username/bin/incremental_paste.sh %f*[/COLOR]

In "Apperance conditions" select all, and File pattern leave it as is '*'. 
Note the **%f **at the end of command line above. Btw, you can change the naming and path to your liking.
[B]
incremental_paste.sh[/B]

```
#!/bin/bash
#set -x
## incremental_paste.sh, for use in Thunar's custom actions.

[ -d "$1" ] && destination_dir="$1" || destination_dir="${1%/*}"

## First extract source dir path in a variable.
source_dir="$(
 xclip -o -selection clipboard | 
   perl -ne 'use URI::Escape; chomp; $path = uri_unescape($_); $path =~ s#^(file://)|(\r|/)$##g; $path =~ s#/[^/]+$##; printf "%s/", $path; exit '
 )"

## Execute the incremental copying.
 xclip -o -selection clipboard | 
    perl -ne 'use URI::Escape; chomp; $File = uri_unescape($_); $File =~ s#^(file://)|(\r|/)$##g; $File =~ s#/.*/##; printf "%s\0", $File; ' |
       rsync -ar0 --files-from=-  "$source_dir"  "$destination_dir" 

exit 0

```
AFAIK the script's dependencies (*xclip, perl's modules, rsync*) come with the default install. I've tested this code and it works fine for me, and it's also possible to have a simple visual GUI of the script's progress using *Zenity*, (some more code is needed).

---

### Post by sam_baker2 on 2013-10-04
thanks erind,
that seems to work fine.
I noticed a difference between this script and the way nautilus works, although
I imagine it depends upon the way one would want it to work.

Example: copying from folder A to B.
 If A has a textfile sometext.txt = "abcd"
and B has a textfile sometext.txt = "abcdefg"

nautilus will leave sometext.txt on B as "abcdefg" and this script will
copy over sometext.txt on B to "abcd"

again thanks

---

### Post by erind on 2013-10-04
> **sam_baker2 said:**
> thanks erind,
that seems to work fine.
I noticed a difference between this script and the way nautilus works, although
I imagine it depends upon the way one would want it to work.
[...]


Yes, exactly. As I said above, this code will get as close as it can to Nautilus behavior. Nonetheless rsync has many options, if you dig through them, there could be one that might fit your desired behavior. All you have to do is add other options in this line:

    ```
rsync -ar0 [ other_options_here ] --files-from=- "$source_dir" "$destination_dir" 
```

> [...]

Example: copying from folder A to B.
If A has a textfile sometext.txt = "abcd"
and B has a textfile sometext.txt = "abcdefg"

nautilus will leave sometext.txt on B as "abcdefg" and this script will
copy over sometext.txt on B to "abcd"

again thanks

Try it with *--ignore-existing *option:

```
rsync -ar0 --ignore-existing --files-from=- "$source_dir" "$destination_dir" 

```
From the man pages:
> **--ignore-existing**
              This tells rsync to skip updating files that already exist on the destination (this does not ignore existing directories, or  nothing  would get done).  See also --existing.
...
*-b, --backup*                 make backups (see --suffix & --backup-dir)           
    *--suffix=SUFFIX *        backup suffix (default ~ w/o --backup-dir)


Btw this was an interesting problem that I wanted to tackle a long time ago, but somehow I got carried away by other things, and then forgot about it.

--

Just for completeness' sake I'm posting the other version that includes a GUI progress bar using *awk+zenity*. I find it very handy and this is the version that I'm currently using in my Thunar's Custom Actions.

```
#!/bin/bash
#set -x
## incremental_paste.sh, for use in Thunar's custom actions.
## Added a simple GUI progress bar (awk+zenity). 
## NOTE: In some corner cases where the file manager's pane is filled up with *directories* only (no files), and there's no room left where to right-click into,
#+ the workaround is using the file manager's controls to go UP one step into the parent directory and right-clicking from there into the desired directory.

################### START ##################

[ -d "$1" ] && destination_dir="$1" || destination_dir="${1%/*}"

############################################
## First extract source dir path in a variable.
source_dir="$(
 xclip -o -selection clipboard |
   perl -ne 'use URI::Escape; chomp; $path = uri_unescape($_); $path =~ s#^(file://)|(\r|/)$##g; $path =~ s#/[^/]+$##; printf "%s/", $path; exit '
 )"
############################################

## Execute the incremental (rsync) copying.

 xclip -o -selection clipboard |

    perl -ne 'use URI::Escape; chomp; $File = uri_unescape($_); $File =~ s#^(file://)|(\r|/)$##g; $File =~ s#/.*/##; printf "%s\0", $File; '  |

        rsync -arv0 --progress --files-from=-  "$source_dir"  "$destination_dir"  |

    ## Show a GUI progress of rsync using awk+zenity.

        awk '{
                if (index($0, "to-check=") > 0) {
                   split($0, pieces, "to-check=")
                   split(pieces[2], term, ")");
                      split(term[1], division, "/");
                   print (1-(division[1]/division[2]))*100"%"
                }
                else {
                       print "#"$0;
                }
                if (/sent[ \t]+[0-9]+[ \t]+bytes[ \t]+received[ \t]+[0-9]+[ \t]+bytes.+bytes\/sec/) {
                    status="Sent " $2" bytes, Received " $5 " bytes, Speed " $7 " " $8 "."
                }
                if (/total[ \t]+size[ \t]+is[ \t]+[0-9]+[ \t]+/) total=$4
                fflush();
             }
            END { print "#Total size " total " bytes, " status; fflush() }' |

                zenity --progress --title "Copying New Files ..." --percentage=0 --auto-kill

############################################

exit 0

######################### END ##############

```

---

