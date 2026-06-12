---
title: "[SOLVED] Zenity w/ IF statement to check if selected directory is not EXT3"
date: 2007-12-19
forum: Programming Talk
---

### Post by mdpalow on 2007-12-19
Hi everyone,

I need some help with checking whether or not a directory is EXT3 or not.

```
#!/bin/bash

zenity --directory --file-selection
```

This brings up Zenity where I can click on a drive.

I would like the output (drive/location selected) to be checked to see if it's a file system that is compatible with accepting permissions (EXT3, etc...) If it's not compatible (ex: FAT32 or NTFS) then I want to loop back.

I can't find anything that I can use to put in an IF/WHILE statement for checking file system type, so I can loop if it's FAT32 or NTFS.

Does anyone know how to do this?

thanks.

P.S. One last thought. Is it possible to make the above Zenity code open in a specific folder and not allow me to change it?

thanks again...

---

### Post by geirha on 2007-12-19
Something like this perhaps?

```
dir=$(zenity --file-selection --directory)

while [ $(stat --file-system -c "%T" "$dir") != ext2/ext3 ]; do
  zenity --error --text="Directory must be in an ext2 or ext3 filesystem"
  dir=$(zenity --file-selection --directory)
done

echo "Ok, $dir is fine"
```

And I don't think you can force a directory in zenity like that. I guess the closest thing would be to make the list of legal files and put it in a "zenity --list"

EDIT: Oh, mdpallow, hello again :)

---

### Post by mdpalow on 2007-12-19
lol :)

thank you geirha!

Sorry to take so long to reply, but I was away for a while and then needed to have someone test it for me to see if they got the same problem I did.

Basically, the script works perfectly against my usb flash drive, but when I tested it against my usb hard drive that is ntfs partitioned, I get:

[: too many arguments

in the " while [ $(stat --file-system -c "%T" "$dir") != ext2/ext3 ]; do "

When selecting the NTFS partition (USB Hard Drive), It says it's ok and moves forward. I would think it shouldn't do that.

Can you think of anything? A friend is getting the same error.

Thanks...

---

### Post by mdpalow on 2007-12-19
do you think it allowed because of ntfs-3g , which allows writing to NTFS?

---

### Post by mdpalow on 2007-12-19
seems to be another small problem.

Once you enter the loop (after selecting a fat file system) and then click CANCEL, you get:

stat: cannot read file system information for `': No such file or directory
/home/me/Desktop/new file: line 13: [: !=: unary operator expected
Ok,  is fine

line 13 is the WHILE line...

---

### Post by mdpalow on 2007-12-19
bumpidibump...

Is there anyone else on-line who might be able to help??

---

### Post by geirha on 2007-12-20
The NTFS one probably has spaces in it, so we'll need to enclose that stat command in quotes. And checking if zenity failed is of course a good idea too, so:

```

dir=$(zenity --file-selection --directory)
[COLOR="Navy"]if [ $? != 0 ]; then
  echo "ok, bye bye"
  exit 1
fi[/COLOR]

while [ [COLOR="Navy"]"[/COLOR]$(stat --file-system -c "%T" "$dir")[COLOR="Navy"]"[/COLOR] != [COLOR="Navy"]"[/COLOR]ext2/ext3[COLOR="Navy"]"[/COLOR] ]; do
  zenity --error --text="Directory must be in an ext2 or ext3 filesystem"
  dir=$(zenity --file-selection --directory)
[COLOR="Navy"]  if [ $? != 0 ]; then
    echo "ok, bye bye"
    exit 1
  fi[/COLOR]
done

echo "Ok, $dir is fine"
```

---

### Post by mdpalow on 2007-12-20
Thank you very much Geirha :)

That worked.

---

