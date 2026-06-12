---
title: "Shell Script Execution Issues"
date: 2009-11-02
forum: Programming Talk
---

### Post by dbsoundman on 2009-11-02
I'm trying to create a shell script that will be a substitute for the normal Amarok launcher on a computer I have which reads its music library from another "server". The server is actually my main desktop computer in my bedroom, which I periodically turn off. The computer that reads my music library on the bedroom computer is in the living room, and is on all the time because it also serves as a print server. What I've been working on is a script that ensures that the remote drive is mounted before starting Amarok, and if it is, constantly monitors that remote drive and kills Amarok if the remote drive disappears. Here's what I have so far:
```
#!/bin/bash
al=`df -v /home/dan | tail -2 | awk '{print $1}'`
a=`echo $al | awk '{print $1}'`
if [ "$a" -a "//192.168.1.100/dan_music" ]
then
#  zenity --info --text="Network drive connected, starting Amarok..."
#  amarok
  amarok | zenity --progress --auto-close --text="Network drive 
connected, starting Amarok..."
  flag="0"
  until [ "$flag" -a "1" ]; do
   al=`df -v /home/dan | tail -2 | awk '{print $1}'`
   a=`echo $al | awk '{print $1}'`
   if [ "$a" -a !["//192.168.1.100/dan_music"] ]
   then
     flag="1"
     killall amarok | zenity --info --text="Network Drive Disconnected!\nAmarok Aborted."
   fi
  done
else
  zenity --warning --text="Network drive not connected.\nAmarok not 
started."
fi
```

The top and bottom parts work fine. I'm having trouble with this part, however:
```
  flag="0"
  until [ "$flag" -a "1" ]; do
   al=`df -v /home/dan | tail -2 | awk '{print $1}'`
   a=`echo $al | awk '{print $1}'`
   if [ "$a" -a !["//192.168.1.100/dan_music"] ]
   then
     flag="1"
     killall amarok | zenity --info --text="Network Drive Disconnected!\nAmarok Aborted."
   fi
  done
```

The UNTIL loop doesn't seem to be changing dynamically; i.e. the value of "flag" never goes to 1, so the script never kills Amarok when it does not detect the network drive. At first I was having issues with an infinite loop, but now it doesn't seem to work at all. There may be a much better way of doing this; if so, I'd LOVE to hear about it. If what I'm doing is unclear please feel free to ask questions, I'd really like your help on this.

PS: I should mention, the reason for having a variable "al" and "a" is because the info returned by the "df" command is too long, so the "al" command comes with some extra info I didn't want. To resolve this, I just repeat the "awk" command to get just the first element of "al" for my argument.

Thanks,
Dan

---

### Post by dbsoundman on 2009-11-02
I figured it out...had to do some poking around, but I had some incorrect operators ( -a instead of == ), typos, and most importantly, I realized that the until statement needed to be on the same line as the program start command. Here's the finished, working product:

```
#!/bin/bash
al=`df -v /remote/blackdiamond/music | tail -2 | awk '{print $1}'`
a=`echo $al | awk '{print $1}'`
b="//192.168.1.100/dan_music"
#echo $a
#echo $b
flag=0
if [ $a == $b ]
then
#  zenity --info --text="Network drive connected, starting Amarok..."
#  amarok
  amarok | zenity --progress --auto-close --text="Network drive connected, starting Amarok..." | until [ $flag -ne 0 ]; do
   cl=`df -v /remote/blackdiamond/music | tail -2 | awk '{print $1}'`
   c=`echo $cl | awk '{print $1}'`
   if [ $c != $a ]
   then
     flag="1"
     killall amarok | zenity --info --text="Network Drive Disconnected!\nAmarok Aborted."
   fi
  done
else
  zenity --warning --text="Network drive not connected.\nAmarok not 
started."
fi
```

Anyone should feel free to use this; just tweak the arguments for df, and adjust the whole al/a and cl/c thing as needed. If anyone wants to use this and has questions, let me know!

-Dan

---

