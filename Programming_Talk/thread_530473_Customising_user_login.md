---
title: "Customising user login"
date: 2007-08-20
forum: Programming Talk
---

### Post by giles.wheatley on 2007-08-20
Hi

I am not sure if this is the right forum but I guess that what I am wanting to do may require scripting.

I have a machine for my children each with their own login and I want to be able to limit the time they are logged in so that they get a warning and then automatically logged out. I used to be able to script using the c shell and the bourne shell many many years ago and am only now returning to *nix.

Any advice welcome
Many thanks 
Giles

---

### Post by pmasiar on 2007-08-20
IMHO this is as evil as Windows Vista with Genuine Advantage! :-)

Why log off your kids after time interval? IMHO better would be to analyze logs, maybe show them that on login, and teach them to use time responsibly (and face **social** consequences if not). Better than let them relogin, slightly annoyed, after they lost something from last save.

---

### Post by Wybiral on 2007-08-20
Why do you want to limit their computer use?

> Better than let them relogin, slightly annoyed, after they lost something from last save.

I agree, what if they're trying to research and learn things but get consistently cut off? Letting them educate themselves with computers is definitely not bad. If it's games or certain websites you're trying to block, there are other ways.

If they're that bad at obeying a limit given by you in the first place, they will just log back in.

---

### Post by giles.wheatley on 2007-08-20
Woah - I was not really looking for advice on how to bring up my children. I am sure you are all well intentioned but with limited number of computers, limited time, and several children all wanting to logon - and not always for educational research purposes - I want to exercise some level of parental responsibility. 

So if anyone does have any ideas of how I can limit a session and the number of sessions by each user in any one day, I would love to hear from them.

Regards
Giles

---

### Post by Wybiral on 2007-08-20
> **giles.wheatley said:**
> Woah - I was not really looking for advice on how to bring up my children. I am sure you are all well intentioned but with limited number of computers, limited time, and several children all wanting to logon - and not always for educational research purposes - I want to exercise some level of parental responsibility. 

So if anyone does have any ideas of how I can limit a session and the number of sessions by each user in any one day, I would love to hear from them.

Regards
Giles

I didn't mean for it to sound like that, I just figured if the goal was preventing things like games/certain website that there is probably an easier way that would allow for them to still use the computer properly.

I'm not judging your parenting, I was just thinking that there may be a better way then just timing them and automatically logging off such as blocking certain non-education related sites and not allowing for software such as games and the like on the computer.

But I see where you're coming from, I just couldn't understand why someone would limit their child's access to a computer (and I didn't consider the situation of having multiple children competing for their slice of time).

Sorry if it came out wrong.

---

### Post by Mr. C. on 2007-08-20
The pam_tally module of PAM allows maintaining a tally of logins, which can be reset each evening.

[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_tally.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_tally.html)

There currently isn't anything built into GDM to do what you want, but it can easily be scripted.  See:

[http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/](http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/)

MrC

---

### Post by pmasiar on 2007-08-20
> **giles.wheatley said:**
> with limited number of computers, limited time, and several children all wanting to logon - and not always for educational research purposes - I want to exercise some level of parental responsibility. 

My apology if you felt that way. It's hard to relate - we have more PC than people (some obsolete ones not used at all), and since my older son set up our home LAN, I gave up on responsibility :-) oops now you can see I am old :-(

Maybe your family is good candidate for edubuntu, with bunch of dirt cheap stations all connected and running apps not locally, but on server?

---

### Post by CptPicard on 2007-08-20
Just get a bunch of old computers, they're practically junk and be had essentially for free, but will run Linux just beautifully. Then when it's the kids' own time, allowing them to spend it on the computer is far preferable to them spending it at the mall, getting drunk and shagging random other kids.

I have spent the last 15 years on the computer and I turned out just fine. I can do an NP-completeness proof, and I even became a bitter hermit with a burning hatred of humanity!!

---

### Post by Note360 on 2007-08-20
ah the classic burnign hatred of humanity. THat is sucha nice thing to have isnt it.

My suggestion... Convert to buddhism so the burning hatred doenst develop... Just a sly tounge in cheek hermit like suggestion.

---

### Post by pmasiar on 2007-08-20
> **Note360 said:**
> Convert to buddhism so the burning hatred doenst develop....

Nah, you don't get it at all: if he can prove NP-completeness, what more Buddhism can offer him? How humanity can be relevant at all? :-)

---

### Post by giles.wheatley on 2007-08-23
Hi

Apologies accepted - in fact I have 6 children and time is an issue. Regarding unsuitable browsing or game playing, that is where I do trust my children rather than police them.

Quite how this thread turned to comments on hatred and buddhism I am not quite sure and have no idea what NP-competeness is. (Is it really true that the choice is between hours on a computer or drinking and sha__ing; and why random other kids? Cannot they be discerning in their pursuit of pleasure and relaxation?) 

However, many thanks for the suggestions but right now I have a dead computer thanks to my 10 year old switching the PSU from 230V to 110V resulting in a bang that scared the living daylights out of him - lesson enough in itself! This more urgent problem is subject of another thread and if anyone wants to divert that one to philosophy, its in the hardware forum. 
:-)

I will return to this thread once I have repaired my computer and looked into the suggestions already made.

Giles

---

### Post by PHuN on 2007-08-23
> **giles.wheatley said:**
> Hi

I have a dead computer thanks to my 10 year old switching the PSU from 230V to 110V resulting in a bang that scared the living daylights out of him - lesson enough in itself! 

Giles

Believe it or not I did something very similar to this when I was about 13, (seeing what a 110v electro-magnet would do to a SVGA display) seemed like a good idea at the time.
Good luck with getting it back up. Kids will be kids.:):(

I have been following this post, I am quite interested in the same principal that giles is, hope to hear more comments on possible solutions, though I guess I could always script it out like said before. Have to think about that.

---

### Post by Note360 on 2007-08-23
> **giles.wheatley said:**
> Hi

Apologies accepted - in fact I have 6 children and time is an issue. Regarding unsuitable browsing or game playing, that is where I do trust my children rather than police them.

Quite how this thread turned to comments on hatred and buddhism I am not quite sure and have no idea what NP-competeness is. (Is it really true that the choice is between hours on a computer or drinking and sha__ing; and why random other kids? Cannot they be discerning in their pursuit of pleasure and relaxation?) 

However, many thanks for the suggestions but right now I have a dead computer thanks to my 10 year old switching the PSU from 230V to 110V resulting in a bang that scared the living daylights out of him - lesson enough in itself! This more urgent problem is subject of another thread and if anyone wants to divert that one to philosophy, its in the hardware forum. 
:-)

I will return to this thread once I have repaired my computer and looked into the suggestions already made.

Giles


The randomness was for comic relief. Sorry mate.

---

### Post by slavik on 2007-08-24
> **CptPicard said:**
> Just get a bunch of old computers, they're practically junk and be had essentially for free, but will run Linux just beautifully. Then when it's the kids' own time, allowing them to spend it on the computer is far preferable to them spending it at the mall, getting drunk and shagging random other kids.

I have spent the last 15 years on the computer and I turned out just fine. I can do an NP-completeness proof, and I even became a bitter hermit with a burning hatred of humanity!!
welcome to the brotherhood. ;) :-P

EDIT: this solution is actually nice in case you have a lab with "express" stations (5minute time limit, just to print something and such). very useful.

---

### Post by giles.wheatley on 2007-09-03
Hi,

New power supply bought and installed and Ubuntu back up and running!!!!

I have looked at the suggestions made so far and they allow me to set times when login is allowed for a given user, logout a user at a given time, and display a warning message before forced logout. Some of this will, I am sure be useful. However, what I want to be able to do is start the clock on login and then give a five minute warning after 30 minutes (to allow saves, goodbyes, etc) and force logout after 35 minutes.

Any ideas?

Giles

---

### Post by Mr. C. on 2007-09-03
The **at** command may be what you want.  Place it in the .login file for the users.

```
man at
```

MrC

---

### Post by giles.wheatley on 2007-09-07
Thanks. I have written the following script and call it from .profile

echo "/usr/bin/zenity --warning --text \"Hello $USERNAME, you have five minutes before logout. Please save your work now.\" --display=:0.0" | at now + 1 minutes
echo "/usr/bin/skill -KILL -u $USERNAME" | at now + 2 minutes

Clearly the times set are for testing!

Now I need to be able to lock out the user for the remainder of the day. I have looked at PAM but am still uncertain how to do this other than search and edit time.conf on the fly which sounds clunky to me.

any suggestions would be welcome. Even locking out a user for a given period would do.

Regards
Giles

---

### Post by giles.wheatley on 2007-09-24
Hi,

I have now cobbled together a couple of scripts that serve my purposes - it provides for a set quota of time and encourages sessions of half an hour. It is not hack proof but seems to work for relatively non-techie children.

It is file based with the following files:
user1.start - stores the current session start time - reset on each quota recalc
user1.quota - stores the current quota
user1.log - provides a trace of the script

all times are in hh:mm format

The first script sets up the quota - (in this fragment for user1):

#!/bin/bash
lp="/etc/gdev/quota/logs"
qh="============New Quota Set: `date`============"

echo "9:00" > $lp/user1.quota
chown user1:giles $lp/user1.quota
echo "0:0" > $lp/user1.start
chown user1:giles $lp/user1.start
echo $qh > $lp/user1.log
chown user1:giles $lp/user1.log

The second script does the monitoring:

#!/bin/bash
qf="/etc/gdev/quota/logs/$1.quota";
sf="/etc/gdev/quota/logs/$1.start";
lf="/etc/gdev/quota/logs/$1.log";
if [ -e "$qf" ]; then
   echo "Quota applies"
else
   #zenity --info --text "No quota applies" --title="Quota for $1" --display=$DISPLAY
   echo "No quota applies"
   exit;
fi
case $2 in
   "display" | "logout" | "cron")
      echo "----------adjust quota----------" >> $lf
      quota_hrs=`cut -f 1 -d : $qf`
      quota_mins=`cut -f 2 -d : $qf`
      if [ $quota_hrs -eq 0 -a $quota_mins -eq 0 ]; then
         echo "quota used up" >> $lf
      else
         echo "Old quota: $quota_hrs:$quota_mins" >> $lf
         start_hour=`cut -f 1 -d : $sf`
         start_min=`cut -f 2 -d : $sf`
         echo "    Start: $start_hour:$start_min" >> $lf
         end_hour=`date +%-H`
         end_min=`date +%-M`
         echo "      End: $end_hour:$end_min" >> $lf
         used_hrs=$[end_hour - start_hour]
         used_mins=$[end_min - start_min]
         if [ $used_mins -lt 0 ]; then
            used_mins=$[used_mins + 60]
            used_hrs=$[used_hrs - 1]
         fi
         echo "     Used: $used_hrs:$used_mins" >> $lf
         quota_hrs=$[quota_hrs - used_hrs]
         quota_mins=$[quota_mins - used_mins]
         if [ $quota_mins -lt 0 ]; then
            quota_mins=$[quota_mins + 60]
            quota_hrs=$[quota_hrs - 1]
         fi
         if [ $quota_hrs -lt 0 ]; then
            quota_hrs=0
            quota_mins=0
         fi
         echo "New quota: $quota_hrs:$quota_mins" >> $lf
         echo "$quota_hrs:$quota_mins" > $qf
      fi
      ;;
esac
case $2 in
   "login" | "display" | "cron")
      echo "----------check quota----------" >> $lf
      quota_hrs=`cut -f 1 -d : $qf`
      quota_mins=`cut -f 2 -d : $qf`
      echo "quota: $quota_hrs:$quota_mins" >> $lf
      if [ $quota_hrs -eq 0 -a $quota_mins -eq 0 ]; then
         echo "Quota used up" >> $lf
         zenity --warning --text "You have used up your quota. You will be logged out in 1 minute." --title="Quota for $1" --display=$DISPLAY
         #kill the session
         echo "/usr/bin/skill -KILL -u $1" | at now + 1 minutes
         exit;
      else
         #store current time as start time
         date +%-H:%-M > $sf
         echo "New start time: `date +%-H:%-M`" >> $lf
      fi
      ;;
esac
case $2 in
   "login" | "display")
      echo "----------display quota----------" >> $lf
      hrs=`cut -f 1 -d : $qf`
      mins=`cut -f 2 -d : $qf`
      zenity --info --text "You have $hrs hours and $mins minutes left of your quota this week." --title="Quota for $1" --display=$DISPLAY 
      ;;
esac
case $2 in
   "login" | "cron")
      echo "----------set cron----------" >> $lf
      echo "/etc/gdev/quota/quota $1 \"cron\"" | at now + 5 minutes
      ;;
esac
case $2 in
   "login")
      echo "----------set half hour limit----------" >> $lf
      #display a five minute warning that the session is about to end
      echo "/usr/bin/zenity --warning --text \"Hello $1, you have two minutes before logout. Please save your work now.\" --title=\"Quota for $1\" --display=$DISPLAY" | at now + 28 minutes
      #kill the session
      echo "/usr/bin/skill -KILL -u $1" | at now + 30 minutes
      ;;
esac
case $2 in
   "logout")
      echo "----------atrem----------" >> $lf
      atq >> $lf
      atq | awk '{system("atrm " $1)}'
      atq >> $lf
      echo "==========Session Change==========" >> $lf
      ;;
esac

It is a bit clunky but it seems to work.
Giles

---

### Post by mssever on 2007-09-24
A couple of suggestions:[LIST=1]
[*]From the skill man page: [quote="man skill"]These  tools are probably obsolete and unportable. The command syntax is poorly defined. Consider using the killall,  pkill, and pgrep commands instead.[/quote]
[*]You should only use SIGKILL as a last recourse, because it doesn't allow programs to clean up after themselves. At times, it can even cause damage. The default signal for kill and friends is TERM. You should always send SIGTERM first, and only send SIGKILL to processes that fail to die after being given sufficient time to do so. Remember, if you're killing many processes at once, there might be a bit of a backlog to clear.[/LIST]

---

### Post by L9d on 2007-10-12
I have a bash script that I have used for my 5 boys for a number of years. It begins at startup, watches for tracked login accounts, resets each day, counts down their time when they are logged in, logs when they were on and how much time they used, and kills all processes under their logins when the time runs out.
The effect is that their session suddenly stops and goes back to the login screen.
They have learned to save frequently and I no longer have fights over who's turn it is, how long the other brothers have been on, and whether they have used up their time.

I would be happy to provide the script and instructions on how to install it. 

I'm currently using Kubuntu 7 but this should work on any system (may have to change gawk/awk)

---

### Post by giles.wheatley on 2007-10-25
I would be interested in getting a copy of your script. Mine has developed further since I posted it and there are still some comments on this list that I need to consider.

Many thanks
Giles

---

### Post by bettermentflux on 2007-11-26
I'd also appreciate a copy of the script.

On a related note: I have a shared directory of my Home server that contains videos. I'd love to be able to limit the amount of time each child can spend watching videos.

My preference is to log them off of the samba share once the set time is reached. Anyone know of a way to do that?

---

