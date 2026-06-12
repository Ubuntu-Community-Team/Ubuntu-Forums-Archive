---
title: "Automatic network connection"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by warraagal on 2012-07-22
Is there any way to start a network connection set up in NetworkManager automatically according to a schedule?

The connection should start and stop automatically at a particular time.
Also I would prefer leaving the computer in Suspend state.can scheduled jobs resume the PC from Suspend state??
The reason I wish to do is that my Internet usage from 2am-8am is not billed.

---

### Post by NikTh on 2012-07-22
Hi , and **welcome to Ubuntu Forums ! **

Yes  i am sure there is a way , with **Crontab**. I don't know how to guide you , but i will watch this thread cause i want to see the results. 

Thanks

---

### Post by gordintoronto on 2012-07-22
I'm pretty sure that waking from suspend requires a physical action, such as moving a mouse or pressing a key. The processor is not running, so a program can't do the job.

---

### Post by Cheesehead on 2012-07-22
> **r4rounak said:**
> can scheduled jobs resume the PC from Suspend state??

No. It's suspended. Nothing can run.
However, if it's a desktop you can simply turn off the monitor. If a laptop, change the Power Manager setting so closing the lid will turn off the screen but not suspend.


> **r4rounak said:**
> Is there any way to start a network connection set up in NetworkManager automatically according to a schedule?

Yes. Script the 2:05 a.m. (connect) activities, script the 7:55 a.m. (disconnect) activities, then use cron to trigger the scripts.

The connect script should tell Network Manager to connect, test that you have a good network connection, then launch your (for example) torrent application.

The disconnect script should terminate the application(s), then tell Network Manager to disconnect, test that it really disconnected, plus what to do if the connection fails to terminate (wake you up, shut down the system, etc)

To do it properly, you will need to learn about Network Manager's dBus API ([http://people.redhat.com/dcbw/NetworkManager/NetworkManager%20DBUS%20API.txt](http://people.redhat.com/dcbw/NetworkManager/NetworkManager%20DBUS%20API.txt)), the dbus-send command, your application(s) command line interface (man page), and cron.

*It's not hard*, but it will take some research if you want to do it right.
That's how this community works - all the tools are on your system, and you just need to bolt them together in the right configuration to meet your wishes.

---

### Post by Hadaka on 2012-07-22
Here is a site that explaines some nice uses and gives examples
of commands...how..why and what...
kinda interesting...didnt know this exsisted...thanks for the tip Nikth.

[http://www.pantz.org/software/cron/croninfo.html](http://www.pantz.org/software/cron/croninfo.html)

---

### Post by techvish81 on 2012-07-22
i'm also interested in such automation, is'nt there anything 'macro' type or input recorder utility in linux to automate steps.

---

### Post by Cheesehead on 2012-07-23
> **techvish81 said:**
> is'nt there anything 'macro' type or input recorder utility in linux to automate steps.

Shell scripting and python scripting, despite their seeming steeper learning curve, are much more versatile and flexible than visual macros, and quite stable and predictable.

Oh, and here are the commands to start/stop Network Manager from a script. You can copy-and-paste these into scripts and they should work. Each command is one really long line broken into readable segments by the backslashes (\). This is the equivalent of right-clicking on the NM icon and ticking/unticking "Enable Networking." Much more fine control is possible, but we would need to know lots of details about your settings.

```
# ENABLE NETWORKING
dbus-send --system --print-reply \
          --dest=org.freedesktop.NetworkManager \
          /org/freedesktop/NetworkManager \
          org.freedesktop.DBus.Properties.Set \
          string:"org.freedesktop.NetworkManager" \
          string:"NetworkingEnabled" \
          variant:boolean:true

# DISABLE NETWORKING
dbus-send --system --print-reply \
          --dest=org.freedesktop.NetworkManager \
          /org/freedesktop/NetworkManager \
          org.freedesktop.DBus.Properties.Set \
          string:"org.freedesktop.NetworkManager" \
          string:"NetworkingEnabled" \
          variant:boolean:false
```
Note that both commands are identical except for the boolean true/false in the last line.

---

### Post by warraagal on 2012-08-02
Thanks for the replies. :)

---

### Post by warraagal on 2013-01-17
I found a very simple solution for automating a DSL connection :)
Just use the following commands:
```
nmcli con up id "DSL connection 1"
``` to connect
&
```
nmcli con down id "DSL connection 1"
``` to disconnect

you can replace "DSL connection 1" with ur connection's name
NOTE: 1>The interface your connection will use should be up.In the above case eth0 interface
             2> Dont forget the quotes if the connection name contains space(s)

---

### Post by warraagal on 2013-01-17
> **gordintoronto said:**
> I'm pretty sure that waking from suspend requires a physical action, such as moving a mouse or pressing a key. The processor is not running, so a program can't do the job.

I found the solution to this too :
```
sudo rtcwake -m mem -s 120
```

This will put your system in Suspend-to-RAM state (ACPI S3) (by the -m mem option) and automatically wakeup after 120 seconds :)
You can see the manpage of rtcwake for more options.

---

