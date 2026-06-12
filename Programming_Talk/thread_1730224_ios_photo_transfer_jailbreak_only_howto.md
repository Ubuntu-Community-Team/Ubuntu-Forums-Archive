---
title: "ios photo transfer jailbreak only howto"
date: 2011-04-15
forum: Programming Talk
---

### Post by bashologist on 2011-04-15
Trasnsfer photos to your ipod on 4.2.1.

**[COLOR="Red"]Warning: Jailbroken devices only. Only tested on ios 4.2.1 on an iPod Touch 4g. Use at your own risk.[/COLOR]**

Install ifuse and zenity.  This will force the photos app to regenerate the photos database file. Uses zenity for file selection and progress bar.

```
#!/usr/bin/env bash

files=$(zenity --file-selection --multiple | tr "|" "\n")
filecount=$(echo "$files" | wc -l)

test -n "$files" || exit 1
test -d /mnt/ipod || gksudo mkdir /mnt/ipod
test -w /mnt/ipod || gksudo chmod a+w /mnt/ipod
test -d /mnt/ipod/private || ifuse --root /mnt/ipod || exit 1
cd /mnt/ipod/private/var/mobile/Media/DCIM/100APPLE || exit 1

counter=1
echo "$files" | while read file; do
	echo "scale=1; 100 / ($filecount / $counter)" | bc
	cp -n "$file" ./
	((counter++))
done | zenity --progress --auto-close --width 700

counter=1
mkdir temp
for input in *.*; do
	output=$(printf "IMG_%04d.${input##*.}" "$counter")
	mv "$input" "temp/${output^^}"
	((counter++))
done

mv temp/*.* ./
rmdir temp
mv -n ../../PhotoData/Photos.sqlite ../../PhotoData/Photos.sqlite.bak 2> /dev/null
cd
fusermount -u /mnt/ipod

```

After the transfer close and reopen the photos app for the changes to take effect.

---

### Post by LatinaLover93 on 2011-04-17
Hello again. Just stopping by to say that i've found a much easier way to get photos (or any file, for that matter) into your ipod, wirelessly. U just need ifile cydia app and a web browser. Open ifile on your idevice n tap on the wifi bar looking icon. It will start a web server and the last line will be your idevices ip address and a port number. just enter it into your web browser and there you go, upload away. Its cool since u get to do it from any operating system, and no ssh required. Granted it wont replace ssh, since it wont let u edit the files already on the idevice, but good for getting a quick song or two or some photos on there quickly without booting into windows

---

### Post by bashologist on 2011-04-18
I wouldn't say it's easier exactly, it's another way maybe. I havn't tried it but it looks like the difference would mainly be that it's done wirelessly as opposed to a wired transfer. You could modify the above script to mount the filesystem wirelessly too.

Also the above script works with some videos too.

Edit:
Here's another option if you have rsync and ssh installed.

```
# replace 192.168.0.151 with your address
# optionally setup passwordless login
# ssh-keygen
# ssh-copy-id mobile@192.168.0.151

files=(/home/foo/bar.png)
rsync --verbose --recursive --progress "${files[@]}" mobile@192.168.0.151:/private/var/mobile/Media/DCIM/
ssh mobile@192.168.0.151 'cd /private/var/mobile/Media/DCIM/; counter=1; mkdir temp; find * -type f | while read file; do output=$(printf "IMG_%04d.${file##*.}" "$counter"); mv "$file" "temp/${output^^}"; ((counter++)); done; mv temp/* 100APPLE/; rmdir temp; rm -f ../PhotoData/Photos.sqlite; killall MobileSlideShow'
```

Edit 2:
Learning alot more.

If you copy over a mp4 1080p h264 video it will play back which is interesting since safari won't let you play back 1080p video unless it's in a mpeg2 container using a m3u8 playlist.

You don't actually need to jailbreak it seems since the PhotoData directory is available with a normal mount (without --root option).

You can copy photos even to the ipad 2 which doesn't have a jailbreak available yet but the above script won't do that right now.

---

