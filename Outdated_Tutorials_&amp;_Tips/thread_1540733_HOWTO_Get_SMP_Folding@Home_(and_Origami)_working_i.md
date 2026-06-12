---
title: "HOWTO: Get SMP Folding@Home (and Origami) working in Ubuntu 10.04"
date: 2010-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by robinl on 2010-07-28
(note: this workaround is from [http://foldingforum.org/viewtopic.php?f=58&t=14782](http://foldingforum.org/viewtopic.php?f=58&t=14782))

As you may or may not know version 6.29 of the Folding@Home SMP client for Linux doesn't work properly due to something wrong with the way the client is linked and doesn't like the Ubuntu libc. Fortunately it's only a minor fix to get it working again.

To those of you that are wondering why use the SMP client, I give you a single word: points. I was running 4 instances of F@H 6.02 in single thread mode and I'd get around 1000 points a day folding most of the day on a Core 2 Quad Q9400 at 3.8Ghz. Now that the SMP version is working my average is around 8000 points a day, more than what I used to get for a week! ([my stats]("http://kakaostats.com/usum.php?u=826656")) The SMP version currently requires at least 4 cores and it should be a relatively fast machine running 64bit Linux, with plenty of RAM and a high uptime as the SMP cores have rather short deadlines. To get the most points you should also get a [passkey]("http://www.stanford.edu/group/pandegroup/folding/FAQ-passkey.html") and put it in below.

So without further ado, here's how to get SMP folding working.

_1. Install F@H using Origami_
(If you don't use Origami you can skip to step 3)
[Origami]("https://help.ubuntu.com/community/FoldingAtHome/origami") is a nice little tool that makes the installation of F@H easier. It sets up the launch scripts and the user for you so that you don't have to worry about it. If you have origami already installed, please erase it to start over again by issuing this command:
```
sudo origami erase
```Use this command to install Origami and tell it we want F@H to be folding for the Ubuntu team in SMP mode:
```
sudo origami install -t 45104 -u USERNAME -p amd64 -k PASSKEY -b big
```Substitute in your user name and passkey and press enter. Note that the -p switch is set to amd64 as there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/origami/+bug/595447") in origami which means it only configures the client to SMP mode if it's set to amd64 (not smp). 

_2. Update the F@H client_
After origami has done its job we need to update the client version. By default it comes with 6.02 which works with Ubuntu out of the box but doesn't support recent SMP cores, which means you won't get any work units. First we need to stop origami:
```
sudo origami stop
```Then download the [latest (6.29) F@H client]("http://www.stanford.edu/group/pandegroup/folding/release/FAH6.29-Linux.tgz") and extract fah6 to your desktop (mpiexec is the same as the one origami downloaded so we don't need it). Then we need to move it to where origami stores the client and overwrite the original client:
```
sudo mv ~/Desktop/fah6 /var/lib/origami/foldingathome/CPU1/fah6
```Also we should change the permissions and owner of the new client to how it was like for the old client, which is done by these 2 commands:
```

sudo chmod 711 /var/lib/origami/foldingathome/CPU1/fah6
sudo chown origami:nogroup /var/lib/origami/foldingathome/CPU1/fah6

```[LEFT][U]3. Make 6.29 client work
[/U]As I said above there's a bug that stops 6.29 from working. Fortunately there's a simple fix to it by installing the package **nscd**:
```
sudo apt-get install nscd
```Then, we need to change a value in its configuration file. First we gotta open the config file:
```
gksudo gedit /etc/nscd.conf
```Then, find the line that says *"enable-cache   hosts  no*". Change that no to a yes, save, and restart nscd by doing:
```
sudo service nscd restar
```Now you can start origami again by issuing
```
sudo origami start
```And hopefully everything will work. The F@H log is at /var/lib/origami/foldingathome/CPU1/FAHlog.txt and you can open it to monitor progress/errors.

[U]Caveats
[/U]
[LIST]
[*]NCSD has a potential security vulnerability if you turn host caching on (see [link]("http://foldingforum.org/viewtopic.php?f=44&t=13064&start=90#p145736") and [link]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=335476")). If you're running a server and/or using Kerberos you should do a bit more reading to see if doing this workaround is a good idea.
[*]The new SMP cores do have a low chance of failing mid way due to a bug in the core or things like that. If you see in the logs that F@H suddenly stopped half way through a WU and then went and fetched a new one don't panic, it might be perfectly normal.
[/LIST]
[/LEFT]

---

### Post by MrRichard on 2010-08-27
Awesome post robinl! But I'm having a bit of trouble running origami when I startup Ubuntu. What command would be needed to paste into System->Preferences->Startup Applications?

P.S. I apologies if my question is vague, as I'm rather new to Ubuntu :)

---

### Post by robinl on 2010-08-28
> **MrRichard said:**
> Awesome post robinl! But I'm having a bit of trouble running origami when I startup Ubuntu. What command would be needed to paste into System->Preferences->Startup Applications?

P.S. I apologies if my question is vague, as I'm rather new to Ubuntu :)

Origami should take care of that - it should start automatically on boot, no configuration needed. If it doesn't seem to work, try doing "origami status".

It should say "Status of FAH client(s): OK" if Origami is running. If it says "Status of FAH client(s): FAILURE" then try manually starting Origami by issuing "sudo origami start". If it still doesn't work feel free to post your F@H logs at /var/lib/origami/foldingathome/CPU1/FAHlog.txt and I'll help you sort it out.

---

### Post by clevertomato on 2010-08-29
Worked here. Thanks! I had all kinds of grief trying to get FAH going until this thread. I like origami and wanted to use it. Now I can.

---

### Post by Nattereri on 2010-09-11
I tried it with 64 bit server LTS and it took 4 tries to get it past the downloading stage. It kept failing with the libc.so.6 error. It's working for now. If it fails I will post here when I have time.

---

### Post by AClark on 2010-09-11
I have two Quad Core 64bit systems (both Lucid) after installing & configuring nscd it is possible to run Folding again.

Unfortunately it takes at least two and as many as four or five tries to connect to the download server each time a new job starts which means a new job won't start unless I am at the machine & remember to check.

I believe this is probably caused by the inherent latency of the satellite internet connection.  Two different locations but both on satellite (no other choice)

Too bad @Folding doesn't seem interested in correcting the underlying problem.

---

### Post by robinl on 2010-09-11
If you're having problems getting it to download a WU can you post your client.cfg (at /var/lib/origami/foldingathome/CPU1/)? I've configured my F@H client to set -advmethods and ask for big WUs and it has been quite consistent at getting WUs immediately.

Adding your passkey to the client might also help, see [URL="http://folding.stanford.edu/English/FAQ-passkey"]http://folding.stanford.edu/English/FAQ-passkey
[/URL]

---

### Post by Nattereri on 2010-09-12
I have just completed a run and can confirm that the relocation error still occurs. It happens when the client trys to connect to the assignment server to get a new WU. When I started it again it connected just fine and downloaded the work unit. I should add that I am no longer using origami and tried the nscd fix on the stanford client. I will be posting on the stanford forums as this seems to be a problem with thier client and not Ubuntu.

---

### Post by motonnerd on 2010-11-14
How do I get Ubuntu to not scale up the processor to work on FAH?  I want it to ignore the idle load, but can't seem to find anything to help me with that.

---

### Post by robinl on 2010-11-14
See [https://help.ubuntu.com/community/FoldingAtHome#Folding%20on%20a%20Notebook](https://help.ubuntu.com/community/FoldingAtHome#Folding%20on%20a%20Notebook)

---

### Post by motonnerd on 2010-11-15
Thanks for the help.
While I had looked at that page, I guess I was  expecting my computer to take processor time away from the FAH core  instead of bringing up the processor when other processes started using  resources, rather than bumping up the clock.  Looking into using  cpulimit to bring the process down to, say, 80% cpu usage so that 20% is  there for other processes without jacking up the clock again.
I  asked this question because I had heard from a few threads (probably  misinterpreted it) that the rc.local route was ineffective, as some  thing or another kept overriding the setting.  So I've added the sysfs  method, but it doesn't seem to be doing that great of a job either --  the best results seem to be with entering 'echo 1 | sudo tee  /sys/devices/system/cpu/cpu*/cpufreq/ondemand/ignore_nice_load' for each  cpu into the terminal.  Which I'll just try shoving into a script which  autoruns at my login.
Beyond that I've now (sorry about the verbage  mismatches, writing as I test) added to that startup script a modified  piece of code which should (and seems to be working well) limit the  usage of the process.  (initial code found at your link).
Summary:
      I'm pretty sure that between the two methods I'm using, the  ignore_nice_load thing is working.  But even so, any load beyond that  seems to jack up the clock, and so the only way to help that is to use  cpulimit.
     I'm using "sudo cpulimit --pid=`ps ax | grep -i fah |  grep -v sh | grep -i .exe | awk '{print $1}'` --limit 80 --lazy" to  control the process because:
          80% utilization seems to be the magic number to my system
          --lazy -- I don't want an orphaned cpulimit process without a target process hanging around my system.
           grep series changed to get what works with my computer.  Your mileage  may vary, I recommend just running ps ax | grep <any combo you  want> until you get the right process.  (-v is the exclude switch)

Criticisms/comments welcome, I know there's got to be a more-efficient way of doing this!

---

### Post by motonnerd on 2010-11-15
I have come to see (after looking at my startup script) that my success so far seems to be attributable more to cpulimit than anything else -- I suppose that if the ignore_nice_load would stick then I could not use cpulimit (or better yet get the behavior I was hoping for earlier).  But Lucid seems to hate that.  If anyone finds a way to get the ignore_nice_load variable to stick let me know -- a night of searching two days ago turned up nothing.
Maybe a different governor entirely?  I hate to move away from what is otherwise a good governor, and no less has an option for exactly what I need...

---

### Post by robinl on 2010-11-16
Hmm seems like the wiki article is wrong. Here's how the Ubuntu equivalent of rc.local actually works [https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)
If you follow that howto and add the ignore nice loads line to that file then it should work as intended.

---

### Post by motonnerd on 2010-11-17
I appreciate your help and owe you an apology -- for some reason I guess I never specified (and shouldn't have posted here anyway) that this thread was for 10.04.
I have started a new thread under 'General Help', and this link should take you to it: [http://ubuntuforums.org/showthread.php?p=10129916#post10129916](http://ubuntuforums.org/showthread.php?p=10129916#post10129916)

Thanks for your help though!

---

### Post by u-slayer on 2010-11-24
Every time I try to install it I get this message:

```
sudo origami install -t 45104 -u BobtheBuilder -b big -p amd64
INSTALLING... PLEASE BE PATIENT
ERROR: STARTUP SCRIPT FAILED TO START
```

I'm running 10.04.1 and I have ia32-libs installed already.

---

### Post by u-slayer on 2010-11-28
anyone?

---

### Post by robinl on 2010-11-30
> **u-slayer said:**
> Every time I try to install it I get this message:

```
sudo origami install -t 45104 -u BobtheBuilder -b big -p amd64
INSTALLING... PLEASE BE PATIENT
ERROR: STARTUP SCRIPT FAILED TO START
```I'm running 10.04.1 and I have ia32-libs installed already.

That is an error with Origami so you'd probably have better luck asking in Origami threads. It seems to be similar to [https://bugs.launchpad.net/ubuntu/+source/origami/+bug/524152](https://bugs.launchpad.net/ubuntu/+source/origami/+bug/524152) but there's no solution on there, and Origami development isn't particularly active (for example the bug mentioned in the HOWTO is still not fixed).

For more information perhaps you can include your F@H log at /var/lib/origami/foldingathome/CPU1/FAHlog.txt if it exists and see what happens if you start Origami manually (ie. with sudo origami start).

---

### Post by AvoidedRider on 2011-01-29
I followed this guide and I have the client using 3 cores of my CPU but not touching my GPU. I tried starting a [thread]("http://ubuntuforums.org/showthread.php?t=1677460") before I found this guide. Any suggestions why nothing would be being done on the GPU?

---

