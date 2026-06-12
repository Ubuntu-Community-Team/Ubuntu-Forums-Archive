---
title: "progress  bar for dvdbackup"
date: 2009-02-24
forum: Programming Talk
---

### Post by einnar on 2009-02-24
Hello!

I have a launcher on my bar that runs the following script :
```

dvdbackup -M -i/dev/dvd -o/home/einnar/Videos/temp; eject /media/cdrom0
```

It launches with a simple :

```
/home/einnar/Videos/copydvd
```

Is there an easy way to add a progress bar to this? Currently, it launches, copies, and ejects the disk with no window popping up, and no indication that it's working other than the DVD spinning. Works great, but I'd like to put a progress bar on it if at all possible.

Thanks much!

Einnar

---

### Post by einnar on 2009-02-24
bump :popcorn:

---

### Post by einnar on 2009-02-25
No-one has any ideas? :(

---

### Post by Ferrat on 2009-02-25
Not really a progress bar but run it in a terminal and use a while loop that prints something every say 1min, or so? or write % of done, not the real one but 
size of img / how much your writer can write every say minute and draw % from that?

EDIT: in bash ofc, should be easy

---

### Post by geirha on 2009-02-25
zenity is commonly used to get a progress bar for scripts, but it either requires the command to provide some output while it works, or that the command outputs a percentage of how far it has gotten.

dvdbackup is a difficult case since it does not provide any continous output. I've made you a script that feeds zenity a . every ¼ second so the bar will at least pulsate. dvdbackup with the -I option will show how big the files from the dvd will be. If you add some code to parse that, you can check it against a stat of the files it creates and be able to print a percentage once in a while, instead of just a '.'. Might be that someone else here will take on the challenge and expand the script to do just that. 

Anyway, here's the script.
```

#!/bin/bash
dvdbackup -M -o /home/einnar/Videos/temp &                     
pid=$!
trap "
    [ -e /proc/$pid ] && kill $pid
    eject /dev/dvd
" EXIT

while [ -e /proc/$pid ]; do
    sleep 0.25
    echo -n .
done | zenity --progress --pulsate --auto-kill

```

Check the man-page of zenity. You can add --title and --text to change the title and text of the progress-bar window. Hitting the cancel button should kill dvdbackup and eject the cd, but I haven't tested that. (I don't have a cd/dvd-player on the laptop I'm on atm).

---

### Post by einnar on 2009-02-26
Thanks geirha, I think we're on the right track. What you gave me pops up a box, but I just have a blue square moving back and forth like a cylon eye.

I'm open to any other process that copies the DVD onto the hard drive. I'm not married to dvdbackup.

I used to have a script in 6.10 that would copy the DVD contents to the hard drive automatically upon insertion of the DVD. With the new way that detection is handled, I haven't figured out how to do that yet, as I can't figure out how to launch scripts upon DVD detection like in 6.10. (I miss having the actions under "removable media".) The script ran it through libdvdcss in the process.

I'm just looking for a way to copy my dvds to my HD, so they don't take up so much room. I travel a lot, and being able to watch movies while gone is a great thing. My prior method was to copy them to the drive with a script, and when I saw it eject one DVD, I'd just put another in. After about 3-5 of them, I'd set up a script with acid-rip to make avi's out of them, and I'd watch them while gone that week. With the changes in gnome since 6.10, it's a lot harder for me as I'm still a novice to scripting.

---

### Post by geirha on 2009-02-27
> **einnar said:**
> 
I used to have a script in 6.10 that would copy the DVD contents to the hard drive automatically upon insertion of the DVD. With the new way that detection is handled, I haven't figured out how to do that yet, as I can't figure out how to launch scripts upon DVD detection like in 6.10. (I miss having the actions under "removable media".) The script ran it through libdvdcss in the process.


It appears that ability is just hidden away from the GUI. Hit Alt+F2 and run "gconf-editor"

Then browse to /desktop/gnome/volume_manager and look at the autoplay_dvd* keys.

---

### Post by einnar on 2009-02-27
Sweet..

You rock! Any idea how to make the progress bar progress now, instead of just back and forth? :)

---

### Post by geirha on 2009-02-27
What did your Edgy script run? Does it provide more output?

---

### Post by einnar on 2009-02-28
Here's the code. I downloaded it from another forum a few years back. It doesn't work for some reason in 8.04, and I'm not smart enough about bash to figure out why.


```
#!/bin/bash

# set -x

function setTitle () {
    echo -n "]0;$1"
}


umask 022

dvd_device=$1
shift

sub=$1
shift

termTitle="RIP $dvd_device"

if [ "$sub" = "" ] ; then
	if [ "$DISPLAY" = "" ] ; then
		export DISPLAY=:0
	fi
	gnome-terminal -t "$termTitle" -e "$0 $dvd_device sub 2>&1 | tee -a /var/tmp/ripdvdsub.log"
	exit 0
fi

size=`df -h $dvd_device | grep $dvd_device | awk '{print $2}'`
termTitle="$termTitle : $size"
setTitle "$termTitle"
# read x
echo

# exit 0

# backup_dir=/data/staging$dvd_device
backup_dir=/data/movies

title=`dvdbackup -i $dvd_device -I 2>/dev/null | grep 'DVD-Video information of the DVD with title' | sed -e 's/.* title //'`

setTitle "$termTitle : $title"
if [ "$title" = "" -o "$title" = "DVD_VIDEO" -o -d $backup_dir/"$title" ] ; then
	echo 
	read -p "DVD Title '$title' already exists, or is stupid.  Please enter another name, or ENTER to overwrite with the current name " newtitle
	if [ "$newtitle" != "" ] ; then
		title=$newtitle
	fi
fi

setTitle "$termTitle : $title"

status=0
if [ "$title" = "" ] ; then
    echo "The disc name is still invalid.  Exiting."
    status=1
else
    echo "STARTING RIP OF '$title'"

    # Background progress indicator
    while [ true ] ; do
	sleep 30
	setTitle "$termTitle : `du -sh $backup_dir/"$title" | awk '{print $1}'` : $title"
    done &

    time dvdbackup -M -i $dvd_device -o $backup_dir -n "$title"
    chmod -R a+r $backup_dir/"$title"
    find $backup_dir/"$title" -type d -exec chmod a+x {} \;
    echo "DONE RIPPING '$title'"
fi

# Stop the background process indicator
kill %%

eject $dvd_device

setTitle "DONE $termTitle : $title"

echo "$title"
echo "Enter a new name, or just ENTER to quit"
read renameTitle
if [ "$renameTitle" != "" ] ; then
    mv $backup_dir/"$title" $backup_dir/"$renameTitle"
fi

exit $status
```

---

### Post by geirha on 2009-03-02
The gnome-terminal command looks wrong. It might have worked before, but not in newer versions. Anyway, it did have a simple way of tracking progress, namely by first using df to find the size of the DVD, then run du on the destination folder once in a while to see how far it has gotten. It is not exact, so you might end up with the progress bar at 98% when it is done.

Modified my previous script with a little cherry-picking from your old "edgy-script".

```

#!/bin/bash
destination="/home/einnar/Videos/temp"

# Determine dvd-device. If the first argument is the mount-point, find the
# device name from /etc/mtab
dvd_device=${1:-/dev/dvd}
if ! [ -b "$dvd_device" ]; then
    dvd_device=$(grep "$dvd_device" /etc/mtab | awk '{print $1}')
fi

# Gather information on the DVD
dvd_title=$(dvdbackup -I -i $dvd_device | head -1 | awk -F'title ' '{print $2}')
dvd_size=$(df -B1 $dvd_device | tail -1 | awk '{print $3}')

# Check if dvd_title was detected, and check if it already exists at the destination.
if [ -z "$dvd_title" ]; then
    dvd_title="$(zenity --title="dvdbackup" --entry --text="Unable to detect DVD title. Please provide one")"
fi
if [ -e "$destination/$dvd_title" ]; then
    zenity --title="dvdbackup" --question --text="$destination/$dvd_title already exists. Overwrite?" || exit 1
    rm -rf "$destination/$dvd_title"
fi

# Start the dvd-backup
dvdbackup -M -i $dvd_device -n "$dvd_title" -o "$destination" &
pid=$!
trap "
    [ -e /proc/$pid ] && kill $pid
    eject $dvd_device
" EXIT

# Check the size of the destination folder every 10 seconds, and print the percentage
# to zenity.
while [ -e /proc/$pid ]; do
    sleep 10
    size=$(du -bs "$destination/$dvd_title" | awk '{print $1}')
    echo $(( 100 * size / dvd_size ))
done | zenity --progress --title="dvdbackup" --text="Ripping $dvd_title"
retval=$?

# If the progress bar was canceled, ask if the incomplete rip should be removed.
if [ $retval -ne 0 ]; then
    zenity --title="dvdbackup" --question --text="Remove incomplete RIP?" || exit 1
    rm -rf "$destination/$dvd_title"
fi

```

---

### Post by einnar on 2009-03-03
Looks good, but the progress bar went to full right away, then just stayed there until the copy was done. Any thoughts?

Appreciate all the help so far. It feels so close.. ;)

---

### Post by geirha on 2009-03-03
Hm. Might be it is unable to find the correct size of the dvd. After the line that sets dvd_size, add a line that prints those dvd_ variables to a file:
```
echo "$dvd_device,$dvd_title,$dvd_size" >> /tmp/dvdback-output.txt
```

Do their values look correct?

---

### Post by einnar on 2009-03-04
> **geirha said:**
> 
Do their values look correct?

the file says this :

/dev/dvd,DVD_MOVIE,57344

---

### Post by geirha on 2009-03-04
Appears df was not as good a tool to use as I thought then ... I doubt the dvd is only 57.3kB ... :/

---

### Post by einnar on 2009-03-04
I agree, it appears a bit light. ;)
Any thoughts? Like I say, I am completely open minded on choice of tool for this.

---

### Post by einnar on 2009-03-06
bump?  :popcorn:

---

### Post by einnar on 2009-03-08
Anyone?

---

### Post by geirha on 2009-03-08
This awk parses the output of dvdbackup -I. It only consider the lines starting from the one matching "VIDEO_TS" until the next line matching "^$" (empty line), then it sums up the second field (which should be the size of each file), and at the end, prints the sum. 
```

dvdbackup -I -i /dev/dvd | awk '/VIDEO_TS/,/^$/ {sum+=$2}END{print sum}'

```

I don't know if there may be an equivalent AUDIO_TS section on some dvds. On the two I've tested with so far, there's only a VIDEO_TS section in the output of "dvdbackup -I". If you find one that differs, post the output.

If it seems to show the correct result, change the dvd_size=-line in the script to
```

dvd_size=$(dvdbackup -I -i $dvd_device | awk '/VIDEO_TS/,/^$/ {sum+=$2}END{print sum}')

```

---

### Post by einnar on 2009-03-09
I think it's closer now, but not quite.. The progress bar goes all the way to "full" after about 5 seconds, then stays there.

It also doesn't eject when done.

Here's the code with my substitutions, in case I did something wrong.

```

#!/bin/bash
destination="/home/einnar/Videos/temp"

# Determine dvd-device. If the first argument is the mount-point, find the
# device name from /etc/mtab
dvd_device=${1:-/dev/dvd}
if ! [ -b "$dvd_device" ]; then
    dvd_device=$(grep "$dvd_device" /etc/mtab | awk '{print $1}')
fi

# Gather information on the DVD
dvd_title=$(dvdbackup -I -i $dvd_device | head -1 | awk -F'title ' '{print $2}')
dvd_size=$(dvdbackup -I -i $dvd_device | awk '/VIDEO_TS/,/^$/ {sum+=$2}END{print sum}')

# Check if dvd_title was detected, and check if it already exists at the destination.
if [ -z "$dvd_title" ]; then
    dvd_title="$(zenity --title="dvdbackup" --entry --text="Unable to detect DVD title. Please provide one")"
fi
if [ -e "$destination/$dvd_title" ]; then
    zenity --title="dvdbackup" --question --text="$destination/$dvd_title already exists. Overwrite?" || exit 1
    rm -rf "$destination/$dvd_title"
fi

# Start the dvd-backup
dvdbackup -M -i $dvd_device -n "$dvd_title" -o "$destination" &
pid=$!
trap "
    [ -e /proc/$pid ] && kill $pid
    eject $dvd_device
" EXIT

# Check the size of the destination folder every 10 seconds, and print the percentage
# to zenity.
while [ -e /proc/$pid ]; do
    sleep 10
    size=$(du -bs "$destination/$dvd_title" | awk '{print $1}')
    echo $(( 100 * size / dvd_size ))
done | zenity --progress --title="dvdbackup" --text="Ripping $dvd_title"
retval=$?

# If the progress bar was canceled, ask if the incomplete rip should be removed.
if [ $retval -ne 0 ]; then
    zenity --title="dvdbackup" --question --text="Remove incomplete RIP?" || exit 1
    rm -rf "$destination/$dvd_title"
fi

```

---

### Post by einnar on 2009-03-10
Bump?

---

### Post by cubeist on 2009-03-10
> **geirha said:**
> 
Anyway, here's the script.
```

#!/bin/bash
dvdbackup -M -o /home/einnar/Videos/temp &                     
pid=$!
trap "
    [ -e /proc/$pid ] && kill $pid
    eject /dev/dvd
" EXIT

while [ -e /proc/$pid ]; do
    sleep 0.25
    echo -n .
done | zenity --progress [COLOR="Red"]--pulsate[/COLOR] --auto-kill

```


sorry, I am too lazy to read all the posts...but if the above script works for you, which geirha posted on page 1, then to get it to progress, instead of pulsate... just delete the pulsate option...

sorry if this is an off-base comment...

---

### Post by einnar on 2009-03-28
While I'd love to say that this worked, I can't access my DVD drive since the last updates. See attached file for reference.

When I put a DVD in, commercial or otherwise, movie or data, I see this in the places menu. (screenshot.png).

If I click it, I see (screenshot-1.png).

I cannot browse to it, mount it, or in any way shape or form read it that I've tried.

Any thoughts?

Thanks much.

---

### Post by einnar on 2009-03-29
bump!:popcorn:

---

### Post by einnar on 2009-04-02
Anyone?

---

