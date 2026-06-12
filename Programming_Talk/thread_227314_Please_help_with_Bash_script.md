---
title: "Please help with Bash script"
date: 2006-08-01
forum: Programming Talk
---

### Post by NobodySpecial on 2006-08-01
I'm trying to write a Bash script to mount a DVD Video iso with fuseiso, play with VLC, then unmount when VLC is closed.  Problem is, it never unmounts when VLC is closed.
```
#!/bin/bash
#
# nautilus-mount-iso

mkdir /media/"$*"
fuseiso "$*" /media/"$*"
gnome-terminal --working-directory=/media/ -e "vlc dvd:///media/"${*%.volume}""
wait %%
fusermount -u /media/"$*" && rmdir /media/"$*"

```
So how can I make the script wait until the "gnome-terminal" line has ended?  Thanks for any help.

---

### Post by apjone on 2006-08-01
so how wud you run this? scipt *iso name*   ???#!/bin/bash
#
# nautilus-mount-iso
iso="$1"
mkdir /media/$iso
fuseiso $iso /media/$iso
vlc dvd:///media/"${iso%.volume}"
fusermount -u /media/$iso
rmdir /media/$iso

run with a -x so you get the debug info

---

### Post by NobodySpecial on 2006-08-04
Thanks for the help!

This script is meant to be saved as a text file such as "mount & play iso" and be placed in ~/.gnome2/nautilus-scripts
With your help to get me started, I have modified it so it will name the mount file without the ".iso":
```
#!/bin/sh

source="$1"
iso=`echo "${1%.*}"`
mkdir /media/$iso
fuseiso $source /media/$iso
vlc dvd:///media/"${iso%.volume}"
fusermount -u /media/$iso
rmdir /media/$iso

```

So right click your DVD iso image and select "mount & play iso" and watch your movie!

Unfortunately, fuseiso seems a bit buggy.  The "mount" command works better, but requires gksudo.

---

