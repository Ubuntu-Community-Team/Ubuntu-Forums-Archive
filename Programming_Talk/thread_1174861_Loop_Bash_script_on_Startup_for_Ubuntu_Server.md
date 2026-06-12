---
title: "Loop Bash script on Startup for Ubuntu Server"
date: 2009-05-31
forum: Programming Talk
---

### Post by editorreilly on 2009-05-31
Got a problem, and I'm racking my brain.  

I've got a while/do bash script that has an infinite loop.  I have this running on my desktop version (9.04) using the System/Preferences/Startup Applications running fine.  

But I am trying to run it on 9.04 server edition.  So I can't use the Startup applications.  I tried using the update-rc.d command running the script on runlevel 2, but the loop hangs up the boot process even if when I force the link in rcd.2 to run something like S98myscript.sh

It always hangs up the terminal, and i can't get to the login screen.  Any ideas?  I looked into running it as a daemon, but that seems complicated.

Thanks for any ideas.

-Ryan.

---

### Post by ghostdog74 on 2009-05-31
show your script.!!!

---

### Post by editorreilly on 2009-05-31
Here it is....
> 
#!/bin/bash
# make it loop forever
cd /home/cm02/Desktop/videodrop
while :
do

while sudo lsof /home/cm02/Desktop/videodrop/*.mov; do 
  sleep 5; 
  [ $((count++)) -gt 600 ] && break
done
	files=`ls -al |find *.mov|wc -l`

      echo file count is $files \(should be 0\)
      echo " "
	if [ $files -ne 0 ]; then
		input=$(ls -t *.mov| grep -v '^total' | grep -v '^ *[1-9][0-9]* d' | tail -1)
		output=1_"$(basename "$input" .mov).flv"

ffmpeg -i "$input" -ar 44100 -ab 56 -aspect 4:3 -b 500000 -r 30 -f flv -s 320x240 -ac 1 ~/Desktop/convert/"$output"


yamdi -i /home/cm02/Desktop/convert/"$output" -o /home/cm02/Desktop/ftphold/"$output"
		rm /home/cm02/Desktop/convert/"$output"
		mv -f /home/cm02/Desktop/videodrop/"$input" /home/cm02/Desktop/done1/"$input"
	fi
sleep 2
done


Thanks.

---

### Post by editorreilly on 2009-06-02
Can anyone at least direct me to a link for some help....I'm stuck!

Thanks.

---

### Post by Barriehie on 2009-06-03
I'm not a bash expert but what happens if:

```

#!/bin/bash
gnome-terminal -x myshellscript.sh &
exit 0 

```Might want to echo the PID out somewhere...

Barrie

---

### Post by rippinblaise on 2010-12-15
try:
```
/path/to/myscript.sh&
```

---

