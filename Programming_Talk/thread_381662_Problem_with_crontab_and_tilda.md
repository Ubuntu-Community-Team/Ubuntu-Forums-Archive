---
title: "Problem with crontab and tilda"
date: 2007-03-11
forum: Programming Talk
---

### Post by dayoflayo on 2007-03-11
Hello, so i've got a script that automatically change my wallpaper, and in this script, he launchs an other script that kill tilda and then relaunch it with differents options.
When i launch the script manually, no problem, but when it's crontab, i've got this problem :

after lauchning it manually :
```
dayoflayo@dayoflyo-laptop:~wallpapers$
```

after crontab :
```
$
```

here are my scripts :

```
#!/bin/bash

cd /home/dayoflayo/wallpaper
# nbr=$(find -name \[0-9]* |wc -l)
find . \( -name "*.jpg" -o -name "*.jpeg" -o -name "*.png" \) > list.tmp
sed -e 's/.\///g' list.tmp > list2.tmp
tab=list2.tmp
image=($(cat $tab))
nb=${#image[*]}
toto=$((RANDOM% $nb))
file=${image[$toto]}


sudo mkdir /home/dayoflayo/num_wall
sudo chmod 777 /home/dayoflayo/num_wall
echo $file > /home/dayoflayo/nom_wall



chemin=$PWD/$file
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$chemin"
gconftool-2 --type string --set /desktop/gnome/background/picture_options centered
#echo $chemin

/home/dayoflayo/tilda.sh $file
```

```
#!/bin/bash

PID=`pidof -x tilda`
kill -15 $PID
sleep 5
if (test -n "$1")
then
case $1 in
 0.png)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 1.png)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 2.jpg)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 3.png)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 4.jpg)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 5.jpg)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 6.jpg)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
esac
else
wall=`sed -n 1p /home/dayoflayo/nom_wall`
case $wall in
 0.png)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 1.png)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 2.jpg)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 3.png)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 4.jpg)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 5.jpg)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
 6.jpg)
  sleep 2
  DISPLAY=:0.0 tilda -x 10 -y 700 &
  ;;
esac
fi
```

thx for your help

---

### Post by ssam on 2007-03-11
this is possibly to do with cron not passing your environmental variables to your scripts.

put
```

env > /home/USERNAME/vars_passed_by_cron.txt

```
in you script (insert your USERNAME), and compare the contents of the output file
```
vars_passed_by_cron.txt
```
with the output of the command
```
env
```
in a working terminal


maybe if you put
```

source /etc/environment 
source /home/USERNAME/.bashrc

```
in your script it will get what you need

---

### Post by dayoflayo on 2007-03-11
I don't really understand what you said ( sorry i'm french lol ) so can you please repost my 2 scripts, inserting the command that you said plz ?
thx

---

### Post by Mr. C. on 2007-03-11
In cron, PATH is set to be minimal.  You need to put the directory of your tilda application in $PATH.

eg. PATH=$PATH:/my/path/to/tilda

If this doesn't solve the problem, you will need to show output from your cron job.  Add some debugging print statements.

MrC

---

