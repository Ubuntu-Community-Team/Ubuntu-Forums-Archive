---
title: "Wget and zenity --progress"
date: 2006-11-25
forum: Programming Talk
---

### Post by Mathieu11 on 2006-11-25
Hello,
I'm making a little nautilus script to get a copy of a whole website on my harddisk.
I use the wget function.
I'd like to get a progressbar with zenity to show the advancement of the wget function. 
Anyone know how I could do it ?
This doesn't work : 
wget -r -l$recursion -k -E $adresse | zenity --progress --pulsate --auto-close

PS : I do not wish to use the wget --progress function that I know, as it only shows progress in the terminal.

---

### Post by Twigman on 2006-12-06
wget [http://filename](http://filename) 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading \2/' | zenity --progress --title="Downloading File..."

That will print the download rate and also advance the progress bar.

This will only work if wget is printing the download percentages.. and that will only work if wget knows how far along it is... I've used that successfully when downloading single files..

Hope it helps..

Twigman

---

### Post by Twigman on 2006-12-06
Thought I should just explain what that code actually does ;)

wget .... 2>&1 merges the stderr output into stdout

sed -u '.....' mangles the output from wget so that it appears like this:

1%
# Downloading (bitrate)
2%
# Downloading (bitrate)

the -u parameter means 'don't buffer much'
# means update the text in the dialog for zenity..

and the zenity part is fairly obvious...

---

### Post by goodrench on 2008-03-18
> **Twigman said:**
> Thought I should just explain what that code actually does ;)

wget .... 2>&1 merges the stderr output into stdout

sed -u '.....' mangles the output from wget so that it appears like this:

1%
# Downloading (bitrate)
2%
# Downloading (bitrate)

the -u parameter means 'don't buffer much'
# means update the text in the dialog for zenity..

and the zenity part is fairly obvious...

does this only work with wget?
I have some scripts that I would like to give this feature to but I can't figure out how to do it.
I want to use it with mencoder functions.
Is this possible?

---

### Post by jobsonandrew on 2008-03-27
Hi, thanks for the code example for the progress bar.. but i have a problem with it:
if you cancel the dialog, wget keeps running... and the only way to stop it is to end it with the system monitor or kill it in the terminal

any idea how to fix this?

---

### Post by goodrench on 2008-03-27
> Hi, thanks for the code example for the progress bar.. but i have a problem with it:
if you cancel the dialog, wget keeps running... and the only way to stop it is to end it with the system monitor or kill it in the terminal

any idea how to fix this?

add

```

--auto-kill
```

to the zenity options

---

### Post by jobsonandrew on 2008-03-27
yeah I tried using --auto-kill but it doesnt work.. I think it actually kills sed.. as that is whats feeding the progress box..?

because of this it doesnt kill wget

---

### Post by bodhi.zazen on 2008-06-14
This is an old thread, but I found it as I was having a similar problem.

There is a bug report here :

[https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/220656](https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/220656)

The "problem" is --auto-kill , I think, refers to killing the zenity progress dialog at 100 %.

In this case, wget keeps running ....

I do not have a solution, just a work around ...

_Note_: Thanks Twigman for the awesome sed expression ...

To contine with the wget / zenity expression used by Twigman :

```

# Start wget | zenity
# **Note the & at the end of the pipe, this allows the script to continue with wget running in the background**
wget [http://filename]("http://filename/") 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading \2/' | zenity --progress --title="Downloading File..." **[COLOR=red]&[/COLOR]**

#Start a loop testing if zenity is running, and if not kill wget
RUNNING=0
while [ $RUNNING -eq 0 ]
do
if [ -z "$(pidof zenity)" ]
then
  pkill wget
  RUNNING=1
fi
done
```This will stop wget if zenity is killed (ie cancel button is hit).
This will leave a partially downloaded file, so you may want to clean up after killing wget.

It is an ugly hack, and there may be a better way, but that is the best I could do.

---

### Post by Martje_001 on 2008-06-14
bodhi.zazen: Why didn't you add a sleep in the loop..? this consumes way too much CPU.

---

### Post by unrater on 2008-06-14
Twigman, thank you thank you thank you :)

---

### Post by bodhi.zazen on 2008-06-18
> **Martje_001 said:**
> bodhi.zazen: Why didn't you add a sleep in the loop..? this consumes way too much CPU.

Um, err, the dog ate it ?

---

### Post by gigahz on 2008-07-14
wow I like sed more and more but even more the examples helping me understand the manual. 

This was cool

---

### Post by gigahz on 2009-06-13
Hi I used this hack for a while but now in jaunty things seem to be different? Anyway, the second line works for me in jaunty: 
```
wget http://(url) 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading \2/' | zenity --progress --title="Downloading" --auto-close
wget http://(url) 2>&1 | sed -u 's/.* \([0-9]%\)\ \+\([0-9.]\+.\) \(.*\)/\1\n# Downloading at \2\/s, ETA \3/' | zenity --progress --title="Downloading" --auto-close

```
my wget version in jaunty is GNU Wget 1.11.4. To mee it seems spaces are not backslashed anymore (?) :)

---

### Post by gigahz on 2009-06-14
> **gigahz said:**
> 
```
second line:
wget http://(url) 2>&1 | sed -u 's/.* \([0-9]%\)\ \+\([0-9.]\+.\) \(.*\)/\1\n# Downloading at \2\/s, ETA \3/' | zenity --progress --title="Downloading" --auto-close

```


Sorry, I forgot to include more than one percentage digit, see the \+ just before % below:
```
second line:
wget http://(url) 2>&1 | sed -u 's/.* \([0-9]\+%\)\ \+\([0-9.]\+.\) \(.*\)/\1\n# Downloading at \2\/s, ETA \3/' | zenity --progress --title="Downloading" --auto-close

```

Anyway, this version includes Estimated Time of Arrival for the impatient :)

---

### Post by fzerorubigd on 2010-06-19
This is good, but there is still some problems. instead I use named pipes and not anonymous pipes to transfer wget result to zenity . my code is : 
```

DOWNLOAD() {
  rand="$RANDOM `date`"
  pipe="/tmp/pipe.`echo '$rand' | md5sum | tr -d ' -'`"
  mkfifo $pipe
  wget -c $1 2>&1 | while read data;do
    if [ "`echo $data | grep '^Length:'`" ]; then
      total_size=`echo $data | grep "^Length:" | sed 's/.*\((.*)\).*/\1/' |  tr -d '()'` 
    fi
    if [ "`echo $data | grep '[0-9]*%' `" ];then 
      percent=`echo $data | grep -o "[0-9]*%" | tr -d '%'` 
      current=`echo $data | grep "[0-9]*%" | sed 's/\([0-9BKMG.]\+\).*/\1/' ` 
      speed=`echo $data | grep "[0-9]*%" | sed 's/.*\(% [0-9BKMG.]\+\).*/\1/' | tr -d ' %'` 
      remain=`echo $data | grep -o "[0-9A-Za-z]*$" ` 
      echo $percent
      echo "#Downloading $1\n$current of $total_size ($percent%)\nSpeed : $speed/Sec\nEstimated time : $remain"
    fi
  done > $pipe &

  wget_info=`ps ax |grep "wget.*$1" |awk '{print $1"|"$2}'`
  wget_pid=`echo $wget_info|cut -d'|' -f1 `

  zenity --progress --auto-close --text="Connecting to $1\n\n\n" --width="350" --title="Downloading"< $pipe
  if [ "`ps -A |grep "$wget_pid"`" ];then
    kill $wget_pid
  fi
  rm -f $pipe
}

if [ $1 ];then
  DOWNLOAD "$1"
else
  dllink=$(zenity --entry --text "Your download link :" --width="350" --entry-text "" --title="Download url")
  if [ $dllink ];then
    DOWNLOAD "$dllink"
  fi
fi

```I'm still working on regexp and I know there is a lot better regexp than mine in this code but its work .
You can use DOWNLOAD function for your scripts, just take one argument (download link) but I wrote complete example too. 

Again thanks to original idea of this script, the idea is from the 8th and 3rd post of this thread.

The complete information about this code available on [my blog]("http://cyberrabbits.net/360/bash-gui-wget/") but in Persian (farsi)

---

### Post by cusco on 2010-09-29
> **gigahz said:**
> Sorry, I forgot to include more than one percentage digit, see the \+ just before % below:
```
second line:
wget http://(url) 2>&1 | sed -u 's/.* \([0-9]\+%\)\ \+\([0-9.]\+.\) \(.*\)/\1\n# Downloading at \2\/s, ETA \3/' | zenity --progress --title="Downloading" --auto-close

```

Anyway, this version includes Estimated Time of Arrival for the impatient :)

That was cool.

Thanks it is pretty usefoul. :)

---

### Post by jsevi83 on 2010-12-10
Could you adapt the script to work with axel, instead of wget?

---

### Post by alz3abi on 2011-06-05
hope to see a script for axel please.

i tried but not working :(

```
axel -a http://(url) 2>&1 | sed 's/.* \([0-9]\+%\).* \([0-9]\+.[0-9]\)\(.*\)].*\[\([0-9]\+:[0-9]\+\).*/\1\n#Speed: \2\3 - Estimated time: \4/' | zenity --progress --title="Downloading"
```
:confused:

---

### Post by biffta on 2012-03-15
> **fzerorubigd said:**
> this is good, but there is still some problems. Instead i use named pipes and not anonymous pipes to transfer wget result to zenity . My code is : 
```

download() {
  rand="$random `date`"
  pipe="/tmp/pipe.`echo '$rand' | md5sum | tr -d ' -'`"
  mkfifo $pipe
  wget -c $1 2>&1 | while read data;do
    if [ "`echo $data | grep '^length:'`" ]; then
      total_size=`echo $data | grep "^length:" | sed 's/.*\((.*)\).*/\1/' |  tr -d '()'` 
    fi
    if [ "`echo $data | grep '[0-9]*%' `" ];then 
      percent=`echo $data | grep -o "[0-9]*%" | tr -d '%'` 
      current=`echo $data | grep "[0-9]*%" | sed 's/\([0-9bkmg.]\+\).*/\1/' ` 
      speed=`echo $data | grep "[0-9]*%" | sed 's/.*\(% [0-9bkmg.]\+\).*/\1/' | tr -d ' %'` 
      remain=`echo $data | grep -o "[0-9a-za-z]*$" ` 
      echo $percent
      echo "#downloading $1\n$current of $total_size ($percent%)\nspeed : $speed/sec\nestimated time : $remain"
    fi
  done > $pipe &

  wget_info=`ps ax |grep "wget.*$1" |awk '{print $1"|"$2}'`
  wget_pid=`echo $wget_info|cut -d'|' -f1 `

  zenity --progress --auto-close --text="connecting to $1\n\n\n" --width="350" --title="downloading"< $pipe
  if [ "`ps -a |grep "$wget_pid"`" ];then
    kill $wget_pid
  fi
  rm -f $pipe
}

if [ $1 ];then
  download "$1"
else
  dllink=$(zenity --entry --text "your download link :" --width="350" --entry-text "" --title="download url")
  if [ $dllink ];then
    download "$dllink"
  fi
fi

```i'm still working on regexp and i know there is a lot better regexp than mine in this code but its work .
You can use download function for your scripts, just take one argument (download link) but i wrote complete example too. 

Again thanks to original idea of this script, the idea is from the 8th and 3rd post of this thread.



+1 +1 +1

---

