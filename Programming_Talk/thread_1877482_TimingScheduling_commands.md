---
title: "Timing/Scheduling commands ?"
date: 2011-11-07
forum: Programming Talk
---

### Post by suffer1989 on 2011-11-07
I wish to set a command or a script, to capture a screenshot at a particular time. I need to run the screenshot script several hours before leaving my computer, and I need the accuracy to be within 10ms. I cant seem to find any tutorials on this, so any help would be appreciated. Thanks.

Im running ubuntu 10.04, on a Core 2 duo laptop (t5750 @2ghz ), with 3Gbs of ram and a 500GB Hdd.

---

### Post by suffer1989 on 2011-11-07
> **suffer1989 said:**
> I wish to set a command or a script, to capture a screenshot at a particular time. I need to run the screenshot script several hours before leaving my computer, and I need the accuracy to be within 10ms. I cant seem to find any tutorials on this, so any help would be appreciated. Thanks.

Im running ubuntu 10.04, on a Core 2 duo laptop (t5750 @2ghz ), with 3Gbs of ram and a 500GB Hdd.

EDIT
 I found some tips here : 

[http://tips.webdesign10.com/how-to-take-a-screenshot-with-ubuntu-linux]("http://tips.webdesign10.com/how-to-take-a-screenshot-with-ubuntu-linux")

Im curious if there is a way to have a script that will allow this command to be run to within 10ms accuracy : 

```
scrot -q 85 -d 5 screenshot.png && gimp screenshot.png &
```

---

### Post by suffer1989 on 2011-11-07
bump?

---

### Post by carranty on 2011-11-07
Are you looking for a script which counts down from the moment you run it, or for a script that executes at a (very specific) time?

I believe Linux can count to an accuracy of 1ms, though you won't be able to initiate it (i.e. press the return key) with that kind of accuracy, so I'm not sure there'd be any point.

---

### Post by carranty on 2011-11-07
When you say 10ms, you do mean 0.01 seconds right?

---

### Post by suffer1989 on 2011-11-07
I was looking for a script that I can run before the event, but executes the command at the specified time. I cant seem to find any script or command that will run another command at that specified time, to that degree of accuracy (if that accuracy is even possible).

EDIT : As far as being able to hit the enter key within 10, or even 100ms, I doubt im that accurate, My point is I want the script to be run before hand, and only execute itself at that time, within possibly 10ms of accuracy.

---

### Post by suffer1989 on 2011-11-08
Bump ? It cant be that difficult to do...

---

### Post by suffer1989 on 2011-11-08
I have a simple dilemma. I simply want to execute a command to a very precise time, to about 10ms if possible. 

Ive thought of several ways, either I can set a schedule to run a script on the hour, before the event, then set a delay for when to trigger the other script I want to run.

The other option is to run the script then have it run the command at that specified time. Does anybody have any idea how to do that, with as much accuracy as feasible ?

For example, I want to start the script, leave, then later, I want it to run the command at a precise specified time.

---

### Post by ofnuts on 2011-11-08
> **suffer1989 said:**
> I have a simple dilemma. I simply want to execute a command to a very precise time, to about 10ms if possible. 

Ive thought of several ways, either I can set a schedule to run a script on the hour, before the event, then set a delay for when to trigger the other script I want to run.

The other option is to run the script then have it run the command at that specified time. Does anybody have any idea how to do that, with as much accuracy as feasible ?

For example, I want to start the script, leave, then later, I want it to run the command at a precise specified time.First make sure that your computer clock is that accurate...

Using a delay from the hour assumes that 1) your script is actually started right on the hour and 2) that the delay is accurate enough and 3) that nothing else on the system is going to preempt the CPU or disk. I would at least get the current time at the beginning of the script (to ascertain when it was actually started), and then compute the necessary delay. But even if using "date +%s.%N" computing the delay in bash is going to be an interesting exercise :)

---

### Post by Lars Noodén on 2011-11-08
You can use the [Time::HiRes](http://search.cpan.org/~zefram/Time-HiRes-1.9724/HiRes.pm) module if you are using Perl for your script.

Make sure your system clock is that accurate.

---

### Post by suffer1989 on 2011-11-08
Im honestly a newbie into linux and commandline ( I just mash about a bit), but is it that hard to have a terminal window saying : 

```
sudo /etc/init.d/ntp restart

  [Insert command specifying time to run the following command] [command that needs to be run]

```
?
I Know what command needs to be run, I dont know how to set it to run at that precise time

---

### Post by Lars Noodén on 2011-11-08
> **suffer1989 said:**
> 
I Know what command needs to be run, I dont know how to set it to run at that precise time

[at](http://manpages.ubuntu.com/manpages/oneiric/en/man1/at.1posix.html) will run programs for you at approximately the time specified.  The resolution is not much though.  You probably need to use "at" to call a script that then waits for the precise moment to run the next script.  For that you can use Time::HiRes from perl.

---

### Post by suffer1989 on 2011-11-08
>  time
              The time can be specified as one, two, or four digits. [B]One-digit
              and two-digit numbers shall be taken  to  be  hours;  four-digit
              numbers  to  be hours and minutes[/B]. The time can alternatively be
              specified  as  two  numbers  separated  by  a   colon,   meaning
              hour:minute.  An  AM/PM  indication  (one of the values from the
              am_pm keywords in the LC_TIME locale category)  can  follow  the
              time;  otherwise,  a  24-hour  clock time shall be understood. A
              timezone name can also follow to further qualify the  time.  The
              acceptable  timezone  names  are  implementation-defined, except
              that they shall  be  case-insensitive  and  the  string  utc  is
              supported to indicate the time is in Coordinated Universal Time.
              In the POSIX locale, the time field  can  also  be  one  of  the
              following tokens:


Is there any way to set it to run on the second ?

---

### Post by Lars Noodén on 2011-11-08
> **suffer1989 said:**
> Is there any way to set it to run on the second ?

Not the way it is currently written.  You could have it call a script that waits until the precise second you need the second script run at.

[sleep](http://manpages.ubuntu.com/manpages/oneiric/en/man1/sleep.1posix.html) will go by the second.  So you could use "at" to call "sleep" if you don't want to write your own timing script.

---

### Post by suffer1989 on 2011-11-08
Im really struggling with the passages. I Dont know scripting, I only dabble in terminal occasionally.

Assuming, I needed to run the command

```
ping 192.168.0.30
```

At the time of 10:32:35 [am], how would I create the command to run that ping event, at the time ?

---

### Post by Lars Noodén on 2011-11-08
```
$ at 10:32
sleep 35
ping 192.168.0.30

```

---

### Post by suffer1989 on 2011-11-08
If the time was pm (its actually AM, but i just want to test it)
I tried 23:16 but ....

```
*********-laptop:~$ at 23:16 sleep 35 ping 192.168.0.30
syntax error. Last token seen: s
Garbled time
```

I pressed enter   before 11:16pm (about 11;15:35)

---

### Post by Lars Noodén on 2011-11-08
"at 10:32" is supposed to be on a line of its own.

---

### Post by suffer1989 on 2011-11-08
> **Lars Noodén said:**
> "at 10:32" is supposed to be on a line of its own.
what did you mean by that ?

---

### Post by Lars Noodén on 2011-11-08
Type **at 10:32** and then press enter before entering the rest.  The other stuff (sleep, ping) goes inside **at**

Another way to do it is like this
```

echo "sleep 35; ping 192.168.0.30" | at 10:32

```

---

### Post by suffer1989 on 2011-11-08
> **Lars Noodén said:**
> Type **at 10:32** and then press enter before entering the rest.  The other stuff (sleep, ping) goes inside **at**

Another way to do it is like this
```

echo "sleep 35; ping 192.168.0.30" | at 10:32

```
Sorry, what does 
```
warning: commands will be executed using /bin/sh
```
imply ? Is it potentially dangerous ?

So, suppose, i want to run this command ```
scrot -q 85 -d 5 screenshot.png && gimp screenshot.png &
```

(this takes a screenshot and opens it in GIMP)

using the string you set up above, I would need to use : 
```
echo "sleep 35; scrot -q 85 -d 5 screenshot.png && gimp screenshot.png &" | at 00:02
``` 
?
(assuming I wanted to run it at 00:02:35am)
[B]
Edit[/B] : I just punched in the command illustrated as above, nothing happened. Normally, when I use 
```
scrot -q 85 -d 5 screenshot.png && gimp screenshot.png &
```
The screenshot opens up with gimp within several seconds.

---

### Post by Lars Noodén on 2011-11-08
> **suffer1989 said:**
> Sorry, what does 
```
warning: commands will be executed using /bin/sh
```
imply ? Is it potentially dangerous ?

It means that your shell script will run using /bin/sh instead of /bin/bash.  That's normal.  bash is bigger and fancier.  If you look (ls -l /bin/sh) you'll see that **sh** is actually [dash](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dash.1.html)

---

### Post by Lars Noodén on 2011-11-08
> **suffer1989 said:**
> 
[B]
Edit[/B] : I just punched in the command illustrated as above, nothing happened. Normally, when I use 
```
scrot -q 85 -d 5 screenshot.png && gimp screenshot.png &
```
The screenshot opens up with gimp within several seconds.

That's because the environment variable DISPLAY is set, so these programs know where to display.  In your shell script you'll probably need to precede everything with 
```

export DISPLAY=:0.0

```

Are you planning on calling graphical programs with **at**?  If not, then it is easier to work with text-based examples.

---

### Post by suffer1989 on 2011-11-08
Honestly, all I want is to get a screenshot using the command :

```
scrot -q 85 -d 5 screenshot.png && gimp screenshot.png &
```

at a certain time, accurate to within a second, and I want it to happen autonomously after I start it. This will only happen once.

**Edit** : I just found that command is really slow when taking screenshots. Is there an easier to have a screenshot taken and automatically saved somewhere ? (Home, maybe ? )

---

### Post by Lars Noodén on 2011-11-08
Something like this?
```

$ at 10:32
export DISPLAY=:0.0;
sleep 35;
scrot -q 85 -d 5 /tmp/screenshot.png && gimp /tmp/screenshot.png &

```

---

### Post by carranty on 2011-11-08
> **suffer1989 said:**
> Bump ? It cant be that difficult to do...

To be honest I don't think its possible.  Scheduling scripts to run at certain times is easy using the Crontab application, but the lowest unit is 1 minute.  Most linux users don't ever need more accuracy than that. Perhaps if you explain exactly why you need this accuracy, someone can suggest a better way of approaching the problem......


EDIT : Lars' example above will do the trick.  I don't see you getting any better accuracy than a few seconds though, on my computer (which is a similar spec to yours) the command
scrot -q 85 -d 5
takes over 5 seconds to run anyway

---

### Post by nothingspecial on 2011-11-08
Threads merged.

---

### Post by suffer1989 on 2011-11-08
> **Lars Noodén said:**
> Something like this?
```

$ at 10:32
export DISPLAY=:0.0;
sleep 35;
scrot -q 85 -d 5 /tmp/screenshot.png && gimp /tmp/screenshot.png &

```

How would I get that into one line ?

---

### Post by Lars Noodén on 2011-11-08
> **suffer1989 said:**
> How would I get that into one line ?

Same as before.  Put a semicolon between commands.

```

echo "export DISPLAY=:0.0; sleep 35; scrot -q 85 -d 5 /tmp/screenshot.png && gimp /tmp/screenshot.png & " | 
at 10:32

```

---

### Post by suffer1989 on 2011-11-08
Awesome, it works :D. However, on my system, it took about 5 seconds, if anybody else reads this thread, test it a few times, to see how long it takes, and compensate for it.


Big thanks to "Lars Noodén" for his time and help. ( I do run Xubuntu on my other PC)

[IMG]http://img849.imageshack.us/img849/9595/screenshotozy.png[/IMG]

---

### Post by Liiiim on 2011-11-08
It takes five seconds because you're telling scrot to delay for five  seconds before taking the screenshot.  Remove the '-d 5' from the scrot  command you won't have that delay.

---

