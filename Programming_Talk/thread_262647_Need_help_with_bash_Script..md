---
title: "Need help with bash Script."
date: 2006-09-22
forum: Programming Talk
---

### Post by Freyr Vanir on 2006-09-22
I am making a script to download and save video or audio streams off the net because I hate watching them thru a webbrowser. I got it almost fully working, but I can't get $var1 to change to $var2 then to $var3, etc... when the ***for*** loop loops at the end. 

Also does anybody know a somewhat easy way, I can take a bash script and turn it into a gui app. I tried using dialog, gtkdialog and zenity, but they did not have good docs on how to get started with it, that I could find.


```


n=1
clear 

echo "Welcome to the MPlayer Stream Saver.
";

until [ "$stop" = "y" ]; do
echo "Enter stream $n and press <ENTER>.";
read var$n;
echo ""

echo "Is this the last entry, y/n.";
read stop;

n=`expr $n + 1`
done

echo "
Whats is the extension to the files you are downloading."
read ext

clear

for (( save = 1; save < $n; save++ )); do 
mplayer -dumpstream $var1;
mv stream.dump $save.$ext;
done


```

---

### Post by mssever on 2006-09-22
I'm not a bash expert, but I think that your line ```
read var$n
``` is invalid.

I would do something like:

```
IFS="\n"
file=/tmp/mplayerStreamSaver.`date +%s.%N`
echo "" > $file
#loop start code here
read var
echo "$var" >> $file
#once you're finished with the loop, do
lines=`read -a < $file`
rm $file

```

---

### Post by Freyr Vanir on 2006-09-22
**read var$n** works. I added a extra echo statment so you can see the stream urls are being saved correctly.

```

n=1
clear 

echo "Welcome to the MPlayer Stream Saver.
";

until [ "$stop" = "y" ]; do
echo "Enter stream $n and press <ENTER>.";
read var$n;
echo ""

echo "Is this the last entry, y/n.";
read stop;

n=`expr $n + 1`
done

echo "
Whats is the extension to the files you are downloading."
read ext

clear

echo "Downloading...
$var1
$var2
$var3"

for (( save = 1; save < $n; save++ )); do 
mplayer -dumpstream $var1;
mv stream.dump $save.$ext;
done


```

I'm having problems with this part...
```

for (( save = 1; save < $n; save++ )); do 
mplayer -dumpstream $var1;
mv stream.dump $save.$ext;
done

```
I need var**1** to change to var**2** to var**3** etc. when the *_for loop_* loops.

It will download the first stream I give it but won't get the second or later ones.

---

### Post by mssever on 2006-09-22
Hmmm... dunno how to do that. That's something I'd do in another language (php, ruby, or something).

---

### Post by Freyr Vanir on 2006-09-22
> **mssever said:**
> Hmmm... dunno how to do that. That's something I'd do in another language (php, ruby, or something).

Do you know of any languages I could try, that I could write this code with then just run it with no compiling. I'm using a really old computer so I don't want to mess with compiling everytime I change something, just to see if it works. 

I want to learn to code and I thought the best way to start is to write small things that I need and work my way up.

What i'm tring to do with this in a nut shell is get input from the user and store it, then feed that input one at a time into a program(mplayer in this case). Then rename what mplayer spits out and then have mplayer move on to the next chunk till there is no more left.

---

### Post by Tomosaur on 2006-09-22
On the line inside the for loop which says:
mplayer -dumpstream $var1;

Try changing that to:
mplayer -dumpstream "$var$save"

---

### Post by Freyr Vanir on 2006-09-22
MPlayer spits this out.
```

MPlayer 2:0.99+1.0pre8-0ubuntu5 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) III Mobile CPU       866MHz (Family: 6, Model: 11, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


93 audio & 211 video codecs

Playing var1.
File not found: '1'
Failed to open 1.


Exiting... (End of file)
mv: cannot stat `stream.dump': No such file or directory
MPlayer 2:0.99+1.0pre8-0ubuntu5 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) III Mobile CPU       866MHz (Family: 6, Model: 11, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


93 audio & 211 video codecs

Playing var2.
File not found: '2'
Failed to open 2.


Exiting... (End of file)
mv: cannot stat `stream.dump': No such file or directory


```
**mplayer -dumpstream "$var$save"**
It's skipping **$var** and only does **$save**

**read var$n;**
I think I might be doing some thing odd with the read command that the person who wrote it, did not intend.

---

### Post by Wolki on 2006-09-22
Try it like this:
```
for (( save = 1; save < $n; save++ )); do 
mplayer -dumpstream $(eval echo "\${var${save}}");
mv stream.dump $save.$ext;
done
```

[edit] quick explanation: when you do $var$save, the shell doesn'tknow the order in which you would like to resolve things, and tries ${var}${save}, since you don't have a variable called var this will be empty, so only $save remains. bash soesn't like nested variable thingies like ${var${save}} rhough, so you have to nest it in an eval.

---

### Post by Freyr Vanir on 2006-09-22
> **Wolki said:**
> Try it like this:
```
for (( save = 1; save < $n; save++ )); do 
mplayer -dumpstream $(eval echo "\${var${save}}");
mv stream.dump $save.$ext;
done
```

[edit] quick explanation: when you do $var$save, the shell doesn'tknow the order in which you would like to resolve things, and tries ${var}${save}, since you don't have a variable called var this will be empty, so only $save remains. bash soesn't like nested variable thingies like ${var${save}} rhough, so you have to nest it in an eval.

That worked perfectly and it fixed another part of my script that I was tring to change to make it simpler.

```

n=1

clear

echo "Welcome to the MPlayer Stream Saver.
";

until [ "$stop" = "done" ]; do

	echo "Please input stream #$n, if finished type "done" and press <ENTER>.";
	read var$n

	if [ $(eval echo "\${var${n}}") = "done" ] 
		then stop=done; n=`expr $n - 1`
		else n=`expr $n + 1` 
	fi

	clear
done

echo "What do you want to name the files you are downloading."
read name

echo "What is the extension to the files you are downloading."
read ext

clear

for (( save = 1; save < $n; save++ )); do 
	echo "Downloading Stream $save"
	mplayer -dumpstream $(eval echo "\${var${save}}") > /dev/null;
	mv stream.dump $name$save.$ext > /dev/null;
	echo "Finished Stream $save"
done

```

---

### Post by maaronB on 2006-09-23
Well you seem to have your code fixed.  But to answer your original question.
You can use the ```
shift
``` command.  This shifts all of the commands down.  $2 becomes $1, $3 becomes $2 , etc.

---

