---
title: "Redirect to X11 :0"
date: 2015-01-29
forum: Programming Talk
---

### Post by davemha on 2015-01-29
Hi all,
I'm trying to get the input from a USB barcode scanner to be entered into a webform.

I've tried the softwedge package, which works, but only supports 1D barcodes.  I need to read in 2D barcodes; as soon as I try with softwedge, softwedge crashes.

I wrote a (very) little shell script to spit out the scan:
```
while true; do
    cat /dev/ttyUSB1
done

```

Works great for the shell or any process I run within that tty.  What I really want to do is run my little script but have it put the scan into ANY process that is in focus (like the webform field in Firefox).

If I can't, my next thing would be to try to dig into softwedge and see if I can figure out how to make it work with 2D barcodes.  Problem is, I'm not very good with C, and I know nothing about X programming.

This is on Ubuntu 14.04.

---

### Post by schragge on 2015-01-30
I guess some combination of a command-line X clipboard manipulation tool like [xclip]("http://manpages.ubuntu.com/manpages/trusty/en/man1/xclip.1.html") or [xsel]("http://manpages.ubuntu.com/manpages/trusty/en/man1/xsel.1x.html") with an input automation tool like [xdotool]("http://manpages.ubuntu.com/manpages/trusty/en/man1/xdotool.1.html") or [xmacroplay]("http://xmacro.sourceforge.net/") may do the trick.

---

### Post by davemha on 2015-01-30
xdotool is an awesome find, thanks schragge.  It's kind of slow but, using xdotool I was able to turn my script into a system-wide keypress event generator for my barcode scanner.  Here's my new script, if anyone is interested.

read_ttyUSB1.sh:
```
#!/usr/bin/env bash
stty 57600 sane -echo -echok -icrnl -ixon -icanon -opost -onlcr time 3 min 0 < /dev/ttyUSB1
while true; do
    cat /dev/ttyUSB1 | sed -e 's/\(.\)/\1 /g' |\
               sed s/,/comma/g | \
               sed s/@/at/g |\
               while read LINE; do
        LINE=`echo $LINE Return`
        xdotool key $LINE 2>/dev/null
    done
done
```

Put that in the background with "read_ttyUSB1.sh &" and it just works!

xdotool doesn't parse all keys directly, hence the sed conversions for comma and at.  I may run into other problems like that down the road but should be able to take care of them.

Also, my scanner doesn't have a speaker so I'm planning on adding a beep from the PC speaker.

---

### Post by schragge on 2015-01-30
You can put several sed commands into one sed call:
```
sed 's/./& /g; s/,/comma/g; s/@/at/g; s/$/Return/' /dev/ttyUSB1
```

---

### Post by davemha on 2015-01-30
Nice, didn't know that.  Streamlining is good, I'll update it with that later.  In the meantime, I added a beep feature.  Turns out there isn't a PC speaker on this all-in-one kiosk I'm using, but there are Alsa speakers.  So here's my solution for that (Thanks for the original idea go to Ryne Everett on StackExchange):

```
#!/usr/bin/env bash
_alarm() {
  ( \speaker-test --frequency $1 --test sine )&
  pid=$!
  \sleep 0.${2}s
  \kill -9 $pid
}


stty 57600 sane -echo -echok -icrnl -ixon -icanon -opost -onlcr time 3 min 0 < /dev/ttyUSB1
while true; do
    cat /dev/ttyUSB1 | sed -e 's/\(.\)/\1 /g' |\
               sed s/,/comma/g | \
               sed s/@/at/g |\
               while read LINE; do
        if [ "$LINE" != "" ]; then
            LINE=`echo $LINE Return`
            xdotool key $LINE 2> /dev/null
            if [ "`echo $LINE | grep '^at'`" != "" ]; then
                _alarm 1200 120 &> /dev/null
            fi
        fi
    done 2> /dev/null
done

```

---

