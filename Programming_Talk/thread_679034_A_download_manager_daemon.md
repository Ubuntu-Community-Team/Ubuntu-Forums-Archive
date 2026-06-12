---
title: "A download manager daemon"
date: 2008-01-26
forum: Programming Talk
---

### Post by zazuge on 2008-01-26
when I started ubuntu I found that firefox download manager don't handel resuming
I installed other download managers but none was multi-user nor could run off-session
I searched and found 2 php download manager daemons, one didn't work and I couldn't fix it, the other one don't separate between different users files.

So the story goes on, and the bad programmer didn't have a choice but to write his own half cooked script daemon , the perfection of loosy  conception.

the script is based on  Aleskey's wget-list script.

[http://www.linux.com/articles/59457](http://www.linux.com/articles/59457)

here it is, workin but unpredictable :
the /etc/init.d/zdownload file
```
#DAEMON=/home/scripts/wget/wget-list
DAEMON=/usr/local/sbin/wget-list
NAME=wgetd
DESC="WGET Daemon"
test -x $DAEMON || exit 0
set -e

start(){
echo -n "Starting $DESC: $NAME"
(sudo -u user1 bash -c  $DAEMON 2 >&1 1>/dev/null &)&
(sudo -u user2 bash -c  $DAEMON 2 >&1 1>/dev/null &)&
echo "."
#;;
}

stop(){
echo -n "Stoping $DESC: $NAME"
kill -s TERM `ps -fed | grep "wget-list" | grep -v grep | awk '{print $2 }'|head -n1` && echo wget-list end
kill -s TERM `ps -fed | grep " wget " | grep -v grep | awk '{print $2 }'|head -n1` && echo wget end

  reload)
          stop
          start
    ;;
  force-reload|restart)
        stop
        start
        ;;
  *)
    echo "Usage: /etc/init.d/amule-daemon {start|stop|restart|force-reload|reload}"
    exit 1
    ;;
esac
exit 0

```
I've left the commented code, so that everyone know how aweful i'am at programing
the wget-list file
```
#!/bin/bash
function completedownload {
mv -bv *.*  done2/
cd done2
for x in *.*~ ;do
        mv -bv  "$x" "[0]"`ls "$x" |awk -F"~" '{print   $1}'`;
        for ((y=1 ;y<=10; y+=1 )) ;do
                for z in \[?]*~ ;do
                        name=`ls "$z" |awk -F"~" '{print   $1}'`
                        firstpart=`ls "$name" |awk -F"[" '{print $1 "["}'`
                        lastpart=`ls "$name" |awk -F"]" '{print "]" $2}'`
                        copynum=`ls "$name" |awk -F"[" '{print $2}'|awk -F"]" '{print $1}'`
                        mv -bv "$z" "$firstpart"$(($copynum+1))"$lastpart"
                done
        done
done
cd ..
}
function clean_up { 
        exit 0
}

trap clean_up SIGHUP SIGINT SIGTERM

[ ! -d ~/download/done ] && mkdir -p ~/download/done && touch ~/download/.wget-list
cd ~/download/
while [[ 1==1 ]]
do
while [ `find .wget-list -size +0` ]
do
        url=`head -n1 .wget-list`
        if [ -f ".incomplet" ] ;then
                echo -e "resuming\n"
                if wget -c  $url ; then ( sed -si 1d .wget-list ; rm -f .incomplet;completedownload) else echo error ;break ;fi
         else
                echo -e "downloading\n"
                touch  .incomplet
                if wget  $url ; then ( sed -si 1d .wget-list;mv -bv *.*  done2/;completedownload) else echo error;breack ;fi
        fi
done
sleep 60
done
clean_up

```

I've got a long way to go to make it flawless](*,)
-------update---------
from the posts people have put down i preasume that my post isn't clear
the script I've posted here do work I already downloaded 2 Gb of data with them
I'm posting them here to share them with exigent people that want :
1- A download manager daemon
2- A download manager that is multi-users
3- A download manager that run all-time not only where one is loged
4- A download manager that resume files on all situations and not with a proprietary format
and this download manager can be integrated to firefox via flashgot plugin 
and I hope that interrested peolpe will contribute to this to make it better ,because I think I didn't find a single download manager that fill those requirements.

---

### Post by Majorix on 2008-01-26
May I suggest you use a scripting language for your project instead; and not BASH? Ruby/Perl/Python are good candidates for making this kind of programs. I am not saying BASH wouldn't work, but it just wasn't designed for this kind of stuff.

Other than that, I don't know much about BASH, so can't be of any help at this point.

Good luck.

---

### Post by dwblas on 2008-01-28
wget will resume a download so you don't have to reinvent the wheel.  I would guess that lynx ro elinks might also do this.
[http://www.gnu.org/software/wget/manual/wget.html#index-resume-download-32](http://www.gnu.org/software/wget/manual/wget.html#index-resume-download-32)

---

### Post by shad0w_walker on 2008-01-28
The easiest solution to this IMO is just to use wget (With -c option if you need to resume) and screen.

---

### Post by zazuge on 2008-01-28
> **dwblas said:**
> wget will resume a download so you don't have to reinvent the wheel.  I would guess that lynx ro elinks might also do this.
[http://www.gnu.org/software/wget/manual/wget.html#index-resume-download-32](http://www.gnu.org/software/wget/manual/wget.html#index-resume-download-32)

well typical of the people who don't read the posts, if you didn't read the script I'M USING WGET! :mad:

> **shad0w_walker said:**
> The easiest solution to this IMO is just to use wget (With -c option if you need to resume) and screen.

same thing same kind of people who don't bother to read the posts
OF COURSE I'M USING WGET WITH -C OPTION! :mad:

---

### Post by shad0w_walker on 2008-01-28
I was giving the suggestion to combine with with SCREEN SO YOU DON'T NEED THE DAEMON :mad:

POSTS ARE SO MUCH MORE EFFECTIVE WHEN YOU YELL.

Oh and just for the record, I didn't read your script to notice you using wget, I posted too suggest a way that you can do something and not have to spend the time writing and debugging something but I guess I shouldn't put forward my own attempt at help with out written consent from your chosen deity.

---

### Post by zazuge on 2008-01-29
> **shad0w_walker said:**
> I guess I shouldn't put forward my own attempt at help with out written consent from your chosen deity.
I'm not a self centered freaky weirdo:lolflag:
I just understood from your post that you didn't understand what i'm talking about . -_-'

And what's this SCREEN thingy?

the problem is i'm not trying to produce another download manager like gwget or other.... graphical download manager tool.

this project (too big a word to fit) is a work done fo issues like users who don't have the time to let their X sessions open to let some download manager runing , just to name a few. @_@

---

### Post by shad0w_walker on 2008-01-29
Screen is a nifty utility which is a server admins best friend. You open up a terminal and run screen, get a little copyright notice screen blah blah, and then you appear to be back to the terminal. Except you are now in screen, it works just like a normal terminal however it will continue to run even if you quit X, logout, whatever.

It's pretty much a container to run commands in and keep them running when you leave. I'll give you a link to a tutorial and a much better explanation than mine.

[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

---

### Post by zazuge on 2009-04-17
although 1year have passed i want to repost an update for this script
here it is
lots of things  i wanted to add are missing
* PID files locks for daemon
* PID files locks for multiple downloads
* bandwidth slots to manage bandwidth
* better code to manage errors and retries

but perhapses that's asking too much from a bash scripting?

shad0w_walker suggested screen witch i now i'm using
maybe i'll make use of it for the daemon but that's not top priority

any suggestion is welcome ^^

---

