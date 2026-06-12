---
title: "simple bash script mediaplayer"
date: 2008-04-20
forum: Programming Talk
---

### Post by moc on 2008-04-20
Hi,

I've created a small script for playing out my mp3 files randomly.
It generates a random number and then plays out the associated mp3 in a background process using play. By polling the play process, it detects when the play is ended and the next number is played.

[COLOR="Blue"]
#!/bin/bash
#
# Play music from misc dir

misc_path="/home/moc/Music/Misc"

cd $misc_path

num_music=`find . | grep mp3 | wc -l`
echo "number of MP3's : $num_music"


while true
do
 	number=$RANDOM
 	let "number %= $num_music"
 	let "number += 1" 
 	current_num=`find . | grep mp3 | head -$number | sed '$!d'`
 	play "$current_num" &>/dev/null &
	echo "playing $current_num" 	
		
	while [ `ps -ef | grep "$current_num" | wc -l` -gt 0 ];		
	do
 		sleep 1
	done      
	echo "ending $current_num" 	
done

exit 0 
[/COLOR]

My problem is the  `ps -ef | grep "$current_num" | wc -l`
As i understand grep, it will print out the the matching process and the grep itself.  e.g if the process is found, the above will return 2.. if not 1. 
example (playing is ruinning):
$ps -ef | grep "./mymusic.mp3"
moc       2886  2876 12 00:12 pts/0    00:00:06 play ./mymusic.mp3
moc       3388  2984  0 00:13 pts/1    00:00:00 grep ./mymusic.mp3
   
However.. when running my script, it seems that sometimes, the last output line is omitted, so that grep doesn't output itself ?? 
That's why I check for greater than zero rather than one in my script.  
Else my script will sometimes start the next number before the current is ended. On the other hand... with 0, I get an unpredictable delay between numbers.  

can anyone explain this ??  Is a shell bug??

Besides this... my script seems to work. Feel free to use it with your modifications 

regards
/moc

---

### Post by stroyan on 2008-04-20
There is a race between ps gathering a list of processes and the grep process being started.  Sometimes ps finishes before grep is there to report.

You could use the pgrep command to check for a running process.
Pgrep can look at a full command line with the -f option.
```
pgrep -f $current_num
```

Or you could look for the exact process id of the play command using $! and kill.
```
sleep 7 & PID=$! ; while (kill -s 0 $PID);do echo there;sleep 1;done;echo not there
```

Or you could just put your ```
 echo "playing $current_num" 
``` line before the play command and not need to put play in the background.

---

### Post by moc on 2008-04-20
Hi Stroyan,

Thanks for your answer.

Your explanation sounds reasonable. I've read that  ps -ef | grep is common used practice. I understand now it must be used with care.

I use pgrep instead. Haven't heard about that one before,
It seems to work fine.

I'm not sure, I fully understand your second suggestion which uses kill. I'll have to study that later. I'll leave that out for now for the readability of my script :), 

The reason for having play as a background process is to later eventually enhance the script with user interaction in the foreground. 

Thanks again

/moc

---

