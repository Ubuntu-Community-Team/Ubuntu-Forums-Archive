---
title: "Adjust script to autoclose Firefox"
date: 2012-06-21
forum: Programming Talk
---

### Post by zoomy942 on 2012-06-21
Afternoon!

Here at The Community Library, we use Ubuntu machines as appliances for patrons to search the Public Access Catalog (PAC).  

I have a small script I'll place below that will auto open Firefox if a patron closes it but we are looking at extending it's functionality.  If a patron walks away from a machine, their search is left up and I was wondering if I could adjust my little script to still function as it does but also auto close firefox after a short time?

I tried some ideas but all they did was prevent Firefox opening completely or not auto closing at all.  It was different placement of this...


sleep 45
pkill firefox-bin


Thanks everyone.  

PZ


```
#!/bin/bash
while true; do firefox; sleep 1s; done



```

---

### Post by dwhitney67 on 2012-06-21
I use a script at home to govern the amount of time my daughters can spend browsing the internet.  If they exceed a prescribed time period, I kill firefox using shell statements similar to:
```

APP_PID=`ps -fu $USER | grep firefox | grep -v grep | awk -F " " '{print $2}'`

kill $APP_PID

```

---

### Post by epicoder on 2012-06-22
If you run a command in the background using &, the variable $! is assigned its pid. So you could do something like this to restart Firefox every 5 minutes:

```
while true
do firefox &
sleep 5m
kill -5 $!
done
```

It would only take a few more lines to restart FF immediately if it closes.

---

### Post by zoomy942 on 2012-07-23
> **sh228 said:**
> If you run a command in the background using &, the variable $! is assigned its pid. So you could do something like this to restart Firefox every 5 minutes:

```
while true
do firefox &
sleep 5m
kill -5 $!
done
```

It would only take a few more lines to restart FF immediately if it closes.

That's fantastic!  As a small adjustment, can it be made to auto shut FF after a period of idle time?

---

### Post by Pinoy Tux on 2012-07-24
> **zoomy942 said:**
> can it be made to auto shut FF after a period of idle time?
Here is an alternative you might want to look into.  Instead of using idle time as metric in auto-restarting Firefox, use idle bandwidth.

(1) Find out how much bandwidth is being consumed during a preset period. You can use nstat.

```
nstat -z | grep "IpExtInOctets" | tr -s ' ' | cut -d ' ' -f2
```will return (in bits) the amount of bandwidth consumed since it was last called and then resets the counter to 0.

(2) If the amount of bandwidth consumed in (1) falls below a certain threshold, pop-up a timed dialog box that warns the user that it detected possible inactivity and waits for action.  Zenity should be able to handle this.

```
zenity --warning --timeout=5 --text="You have 5 seconds to click the OK or (X) button."
echo $?
```will return the exit code that corresponds to the (in)action that has taken place.

(3) If there was no action taken, it's assumed there's no user infront of the computer and the script can kill Firefox.

-=-=-=-=-

You will use two scripts.  One will function to do only one thing: start Firefox in a loop and make sure Firefox gets restarted if the user forcibly exits it.  The other script monitors bandwidth activity.

In pseudo-code form, the Firefox looper should look like the following:

```
while [ true ]
do
  if [ pidof firefox = blank ]
  then
    firefox
  fi
  sleep 1
done
```The companion bandwidth activity checker will look like the following:

```
PERIOD=Waiting time to allow nstat to accumulate the needed data
THRESHOLD=Below this value (in bits) it's possible there's inactivity

while [ true ]
do
  sleep $PERIOD
  CONSUMED=nstat...
  if [ $CONSUMED < $THRESHOLD ]
  then
    zenity...
    if [ $? = no button clicked ]
    then
      kill `pidof firefox`
    fi
  fi
done
```-=-=-=-=-

You will have to do some trial-and-error to find the sweet spot for the THRESHOLD value.  What you can do is run nstat twice: the first time is to reset the counter to zero.  Then wait for a PERIOD and run nstat a second time to get a new reading.  Of course you have to make sure there's minimal or no network activity while you're waiting.  The value you get should give you a rough estimate of what your THRESHOLD value should be.  Adjust this value to your preference.

There are at least three pitfalls to be wary of:


[LIST=1]
[*]If nobody is using the computer for an extended period of time, Firefox will regularly get "switched on and off" since bandwidth consumed is always below the threshold value.  (With a little bit of modification in the companion script, this can be addressed.)
[*]If a user starts a big download (e.g. the Ubuntu ISO) and leaves the computer, Firefox won't get restarted until the download is finished.
[*]For those instances where a user is reading a long article, for example, it's likely the warning box will pop up due to idle bandwidth, even though the computer is still being used.
[/LIST]
These pitfalls might be less than ideal, but IMHO this alternative technique is worth considering.

HTH.

---

### Post by zoomy942 on 2012-07-25
> **sh228 said:**
> If you run a command in the background using &, the variable $! is assigned its pid. So you could do something like this to restart Firefox every 5 minutes:

```
while true
do firefox &
sleep 5m
kill -5 $!
done
```

It would only take a few more lines to restart FF immediately if it closes.

Afternoon!  I was using this as it's the simplest, but Im struggling to add lines that will auto open firefox once it's been closed.  I'm not sure how to arrange the lines.  It works great to auto close firefox, but auto opening has stumped me.

---

### Post by Pinoy Tux on 2012-07-25
> **zoomy942 said:**
> ...but Im struggling to add lines that will auto open firefox once it's been closed. I'm not sure how to arrange the lines. It works great to auto close firefox, but auto opening has stumped me. 
Good morning from here.  The reason why it will not auto-open immediately is because of the following line:

```
sleep 5m
```Once the script reaches the above line, it has to wait for the whole 5 minutes to finish before it resumes execution.  So, if the user closes Firefox the moment it opens the first time, it won't auto-open again until 5 minutes have passed.  No matter how you rearrange the lines it still won't cut it due to that single piece of code.  The only way that I can think of (at that moment) is to make sure the script continuously monitors if Firefox is running or not, and re-runs Firefox the moment it doesn't see it running (that's what the pidof command is for).

(Sidenote: the Firefox looper pseudo-script follows the Unix philosophy of writing a program that does one thing, but does it well.  The same goes for the companion bandwidth activity monitoring script.)

That's why I suggested my preceding post.  Just for sh!ts and giggles, I wrote the two scripts and ran them on my machine (Mint 9), and they did the job pretty well.

Edit: Ubuntu 12.04's version of zenity (3.4.0) behaves differently from it's older incarnation (2.30.0 on Mint 9).  The exit codes don't return the same numbers when used on zenity 3.4.0.

---

### Post by zoomy942 on 2012-08-14
Thanks very much!  I'll use the bandwidth method but have run into a spot of trouble.  I have it like this...

```
PERIOD=150s
THRESHOLD=2000

while [ true ]
do
  sleep $PERIOD
  CONSUMED=nstat...
  if [ $CONSUMED < $THRESHOLD ]
  then
    zenity...
    if [ $? = no button clicked ]
    then
      kill `pidof firefox`
    fi
  fi
done

```

I then double click the firefox script and the bandwidth one, run them in terminal as it requests, and I get Firefox opening an unlimited number of times?  Am I missing something?

I'm sure the secret is out than I'm a basic scripter so thank you for your help/patience.

PZ

---

### Post by Pinoy Tux on 2012-08-14
> **zoomy942 said:**
> Thanks very much!  I'll use the bandwidth method but have run into a spot of trouble...run them in terminal as it requests, and I get **Firefox opening an unlimited number of times**?  Am I missing something?
Make sure you run the two scripts in separate terminal windows if you're testing them.  Could you please post the actual scripts you wrote?

---

### Post by zoomy942 on 2012-08-15
> **Pinoy Tux said:**
> Make sure you run the two scripts in separate terminal windows if you're testing them.  Could you please post the actual scripts you wrote?

Morning!  I'll paste it below and yes sir - I double clicked them and chose Open in Terminal... separately 

```
#!/bin/bash
while true
do firefox &
sleep 150s
kill -5 $!
done

```


```
PERIOD=150s
THRESHOLD=2000

while [ true ]
do
  sleep $PERIOD
  CONSUMED=nstat...
  if [ $CONSUMED < $THRESHOLD ]
  then
    zenity...
    if [ $? = no button clicked ]
    then
      kill `pidof firefox`
    fi
  fi
done

```


Once i run those 2, i double click firefox (because it hadnt opened yet) and it goes on to open an infinite number of them.

PZ

---

### Post by Pinoy Tux on 2012-08-16
> **zoomy942 said:**
> I'm sure the secret is out than I'm a basic scripter...
Okay, I only noticed this now. #-o

Copy the following two scripts and run them in separate Terminal windows.

[COLOR=Red]**the-red-pill.sh**[/COLOR]
```

#!/bin/sh

# http://ubuntuforums.org/showpost.php?p=12126704&postcount=5
# Checks if Firefox is running and starts it if it has been closed

CHECKPOINT=2  # seconds

while [ true ]
do
  echo -n "`date +%r` Firefox is "
  if [ -z "`pidof firefox`" ]
  then
    echo "not running! Starting Firefox now."
    firefox &
  else
    echo "running. Checking in $CHECKPOINT seconds."
  fi
  sleep $CHECKPOINT
done

```[COLOR=Blue][B]
the-blue-pill.sh[/B][/COLOR]
```

#!/bin/sh

# http://ubuntuforums.org/showpost.php?p=12126704&postcount=5
# Kills Firefox if there's minimal network activity

PERIOD=60       # seconds
THRESHOLD=3072  # 3 kbits per 60 second interval based on informal tests
TIMEOUT=30      # timeout for zenity 

MESSAGE="It appears the current session is no longer active.\nClick YES to close the browser and start a new session.\nClick NO if you want to leave the browser open.\n\nIf there is no response in the next $TIMEOUT seconds\nthe browser will close automatically."

while [ true ]
do
  echo "----------\n`date +%r` Accumulating network activity for $PERIOD seconds."
  sleep $PERIOD
  CONSUMED=`nstat -z | grep "IpExtInOctets" | tr -s ' ' | cut -d ' ' -f2`
  echo -n "Bandwidth consumed is $CONSUMED bits "
  if [ $CONSUMED -lt $THRESHOLD ]
  then
    echo -n "and is below the threshold value ($THRESHOLD bits).\nClose the browser? "
    zenity --question --timeout=$TIMEOUT --text="$MESSAGE"
    if [ $? -eq 5 ]  # 5 = YES button has been pressed or timeout event from zenity 3.4.0
    then
      echo "Yes. Closing browser."
      kill `pidof firefox`
    else
      echo "No. Leaving browser open."
    fi
  else
    echo "and is above the threshold value ($THRESHOLD bits)."
  fi
done

```Both scripts should do the job.  The values used in the variables for both scripts are arbitrary, of course and YMMV.  Both scripts run without any issues (so far) for 12.04.

Edit:  If you're getting a "restore session" tab in Firefox, change the Privacy preference to "Never remember history."  This will always start Firefox in Private Browsing mode and will get rid of this minor snag.

---

### Post by zoomy942 on 2012-08-16
Thanks so much for this!

I'll try it in my VM once I get to work.  

I was wondering if my appliances running 10.04 would make the script change?  I could upgrade them to 12.04 if it would help.

---

### Post by Vaphell on 2012-08-16
PinoyTux, you should avoid all caps variables - shell won't complain when you accidentally overwrite some env variable (all caps by convention) in the local scope but things stop working.
yes, i have seen someone using PATH in his script and wondering why no program wants to run.

---

### Post by Pinoy Tux on 2012-08-16
> **zoomy942 said:**
> I was wondering if my appliances running 10.04 would make the script change?  I could upgrade them to 12.04 if it would help.

The only problem I see is with zenity.  As I have mentioned in my previous reply:

> 
Ubuntu 12.04's version of zenity (3.4.0) behaves differently from it's older incarnation (2.30.0 on Mint 9). The exit codes don't return the same numbers when used on zenity 3.4.0.
You can find the version of your 10.04's zenity by:
```

zenity --version

```Adapting it to work with your 10.04 is straightforward.  You only need to change the following line in the-blue-pill.sh to match the appropriate exit code generated with 10.04's zenity:

```

if [ $? -eq 5 ]

```I'll leave it to you as an exercise to find the appropriate exit code and make the changes in the above line.  If you hit a snag,  post back the changes you made to this thread.

HTH.

---

### Post by Pinoy Tux on 2012-08-16
> **Vaphell said:**
> avoid all caps variables - shell won't complain when you accidentally overwrite some env variable (all caps by convention) in the local scope but things stop working.
yes, i have seen someone using PATH in his script and wondering why no program wants to run.
Ah!  Good point!  That's another programming pitfall I have to bear in mind.  I've been used to following certain conventions whenever I do coding.

Will have to watch out for that pitfall.  Thanks!

---

### Post by zoomy942 on 2012-08-17
EXCELLENT!

I'll start reading about it now and see if I can unravel the mystery.  

This is great and I thank you.

I will post back later today.

---

### Post by zoomy942 on 2012-08-17
Afternoon!  Well I have good news and bad news...

The good news is, I learned alot about how much you can do with scripting.  Holy smokes.  You can automate copying files, say for a backup of something and you can control power functions.  And in this case, you can control applications and the more I looked, the deeper the rabbit hole got.

However, I tried lots of different adjustments to the line, which I'll paste below, but nothing seemed to create the reaction I was hoping for.  The trouble I found was anything I looked at online didn't specify what version of zenity they were using.  So here are some I tried...

```
if [ "$?" -eq 5 ]
```

```
if [ "$?" "-eq 5" ]
```

```
if [ $? ==eq 5 ]
```

```
if [ $? -eq '5' ]
```

```
if [ "$?" = "eq 5" ]
```

```
if [ "$?" == "eq 5" ]
```

In all honesty, after looking online at some other example scripts, I thought the first one would do the trick since it reminded me of a file path - you have to use quotes to be specific otherwise the computer doesn't see it as a single line of information/location.  

So at this point, I like this practice so I'd rather ask for a hint (online resource to read, tip on a next step, etc) instead of a solution.  

I'm not going to learn if you do it for me. :)

PZ


EDIT - Also, I upgraded my VM to version 12.04 just to see if using it was possible with our appliances.  While your script worked perfectly (I knew it would) there are other parts of 12.04 that make it unusable as out catalog search OS for the patrons.  That unity thing was very different from 10.04 and the hardware requirements are more taxing on our lowly HP PAC (public access catalog) machines.

---

### Post by Pinoy Tux on 2012-08-17
> 
...anything I looked at online didn't specify what version of zenity they were using.
Rather than looking online, open a Terminal window at one of the computers where you're going to put the scripts in, and enter the following in order to find the version of zenity that is installed on that computer:

```
zenity --version
```I'm guessing here, but since one of my workstations is still on Mint 9 (which in turn is based on 10.04, which incidentally is the same version you use in your appliances), the version of my zenity should match yours -- 2.30.0.  12.04's zenity doesn't exhibit the same behavior as 10.04's zenity, so only a slight modification of that line is needed.

> However, I tried lots of different adjustments to the line, which I'll paste below, but nothing seemed to create the reaction I was hoping for... So here are some I tried... <snipped for brevity> So at this point, I like this practice so I'd rather ask for a hint (online resource to read, tip on a next step, etc) instead of a solution.Don't jump immediately into modifying the code without analyzing first what needs to be done.  Remember what I said previously:

> Adapting it to work with your 10.04 is straightforward. You only need to change the following line in the-blue-pill.sh **to match the appropriate exit code generated with 10.04's zenity**That's your hint.  Find out first what exit codes 10.04's zenity returns.  Using the example I wrote in the-blue-pill.sh, there will be five possible scenarios, clicking:

[LIST]
[*]Yes will return an exit code of :-#
[*]No will return an exit code of :-#
[*]The (x) button will return the same exit code as if you clicked :-#
[*]Pressing the ESC key behaves in the same manner
[*]Ignoring the dialog box and allowing it to time out will return an exit code of :-#
[/LIST]
You *did* ask for hints instead of a solution :twisted: which is good, IMO.

So, you have five scenarios that gives three possible values to pick from (assuming we're talking about zenity 2.30.0).  Of those three, you only need one.  And that is all it takes to make the whole thing work in 10.04.

Once you find that eureka moment and get it working in your appliances, I'll give you a :KS

---

