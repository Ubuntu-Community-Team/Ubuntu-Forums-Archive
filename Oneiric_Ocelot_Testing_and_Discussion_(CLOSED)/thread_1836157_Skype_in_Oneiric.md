---
title: "Skype in Oneiric?"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-08-30
Will Skype run in Oneiric? I downloaded the 64-bit .deb directly from Skype, today. It seemed to install with no errors. If I search for it in dash, it gives me the icon, but whan I click on it, absolutely nothing happens. No errors, no warnings, nothing gets added to the syslog.

```
Package: skype                           
New: yes
State: installed
Automatically installed: no
Version: 2.2.0.35-1
Priority: extra
Section: non-free/net
Maintainer: Skype Technologies <info@skype.net>
Uncompressed Size: 29.4 M
Depends: lib32stdc++6 (>= 4.1.1-21), lib32asound2 (> 1.0.14), ia32-libs, libc6-i386 (>= 2.7-1), lib32gcc1 (>=
         1:4.1.1-21+ia32.libs.1.19)
Conflicts: skype
Description: Skype

```Does it work for anyone else in Oneiric AMD64?

Thanks,
Tim

---

### Post by buzzmandt on 2011-08-30
what do you get when running it from terminal, not sure what the command is but you could try just doing
```
skype
```

---

### Post by MadCow108 on 2011-08-30
probably missing libraries, see this bug for a solution:
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/830440](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/830440)

---

### Post by ratcheer on 2011-08-30
Thanks, MadCow108. The instructions in that bug report got it working. But boy, what a mess!

Tim

---

### Post by mspray11 on 2011-09-01
These seem like they will work. I am also reinstalling skype from deb we will see how it goes. Mine is a distro upgrade from natty on a gateway nv53 love the look of Oneiric beta, bugs, yes but good learning. ...........to be continued......

---

### Post by mspray11 on 2011-09-01
Ok the launcher in unity doesn't work for skype, however I can run it fine from terminal.

---

### Post by cariboo on 2011-09-01
You may want to check the launcher in /usr/share/applications, and make sure it is pointing to the right application. I don't bother with a launcher, and just start skype from the dash.

---

### Post by kmsalex on 2011-09-05
I know i had it running and i'm missing a library, so when i lunch it in the terminal i get.

```
alex@alex-HP-G60:~$ skype
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

```

I tried apt-get install libxss.so.1 but it doesn't exsist. how do i get it?

---

### Post by MadCow108 on 2011-09-05
read the thread your posting in.. especially post #3
and another pro tip, open the link in that post and read that page too.

---

### Post by newyorkcityjay on 2011-09-17
I'm running Oneiric Beta and my Skype crashes a lot.

---

### Post by Ipharus on 2011-09-27
This solution (from a page linked earlier in this thread) worked for me :

> echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
sudo apt-get update
sudo apt-get install libxss1:i386 libqtcore4:i386 libqt4-dbus:i386 libqtgui4:i386 

Enjoy!

---

### Post by rbrick49 on 2011-09-27
> **Ipharus said:**
> This solution (from a page linked earlier in this thread) worked for me :



Enjoy!I also did this  echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
and the sudo apt-get update
then reboot then sudo apt-get install skype 
working like a charm

---

### Post by martin-gaspo on 2011-09-28
In order to make it work with Pulse Audio you need to install also x86 librasries for pulse:
```
sudo apt-get install libpulse0:i386
```

I've spent whole day looking for this solution and I coundt find it anywhere. I hope it will help somebody. Enjoy.

---

### Post by inxs44 on 2011-09-28
Martin-gaspo I just wanted to thank you for the time & effort you put into obtaining this pulse audio solution solution for skype 64 bit. I was at my ropes end trying to find a solution for this.

---

### Post by castrojo on 2011-09-28
Guys, don't forget to file a bug so we can fix it in the distro: 

[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/861573](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/861573)

(Please mark it affecting you if you've had this problem)

---

### Post by inxs44 on 2011-10-02
I don't believe Oneiric is ready for primetime. Once we had skype working with pulse audio the recent oct 2nd build of Oneiric broke it again. Now when performing a skype test call the recording of one's voice skips then stops suddenly. I pulled up Sound Recorder and any voice recording done on it works properly. Which means it's skype oneiric issue. For the sake of experimenting I turned on Sound Recorder on while I performed Skype test call and skype test call worked and recorded correctly but if I turned off Sound Recorder off Skype test call failed. Any ideas my fellow Ubuntu inmates? Thanks

---

### Post by cariboo on 2011-10-02
Oneiric is going to be released no matter what, keep in mind, that all of the interim releases have had problems on release, but they are usually fixed soon after (for most problems anyway :)). Skype is not a reason to hold back the release, and as Jorge said above, make sure a bug report has been made and add your me too if it has.

---

### Post by rvchari on 2011-10-03
> **ratcheer said:**
> Will Skype run in Oneiric? I downloaded the 64-bit .deb directly from Skype, today. It seemed to install with no errors. If I search for it in dash, it gives me the icon, but whan I click on it, absolutely nothing happens. No errors, no warnings, nothing gets added to the syslog.

```
Package: skype                           
New: yes
State: installed
Automatically installed: no
Version: 2.2.0.35-1
Priority: extra
Section: non-free/net
Maintainer: Skype Technologies <info@skype.net>
Uncompressed Size: 29.4 M
Depends: lib32stdc++6 (>= 4.1.1-21), lib32asound2 (> 1.0.14), ia32-libs, libc6-i386 (>= 2.7-1), lib32gcc1 (>=
         1:4.1.1-21+ia32.libs.1.19)
Conflicts: skype
Description: Skype

```Does it work for anyone else in Oneiric AMD64?

Thanks,
Tim



I had similar problems...

then i completely uninstalled and re-installed from ubuntu-software-center.
it shows skype i 386 and i installed it from there. its working....
(probably it takes the dependencies thats needed on its own, thanks to multi arch structure..)
i am also using 64 bit 11.10 beta as of now and i could do it after all the updates were installed.

---

### Post by peter_altherr on 2011-10-06
i have the same issue as inxs44. my installation is an upgrade of natty amd64 to oneiric amd64. then i uninstalled the natty skype and tried all the workarounds. ended up with the oneiric x86 version (i like the well integrated context menu in the panel) but no correct voice recording. i have applied all workarounds mentionend here in the thread. so now i am going to try the latest one (having audio recorder running while skyping).

i hope the ubuntu team is going to fix that soon as it is a vital skype feature :-)


greetings

peter

---

### Post by cariboo on 2011-10-06
> **peter_altherr said:**
> i have the same issue as inxs44. my installation is an upgrade of natty amd64 to oneiric amd64. then i uninstalled the natty skype and tried all the workarounds. ended up with the oneiric x86 version (i like the well integrated context menu in the panel) but no correct voice recording. i have applied all workarounds mentionend here in the thread. so now i am going to try the latest one (having audio recorder running while skyping).

i hope the ubuntu team is going to fix that soon as it is a vital skype feature :-)


greetings

peter

Your problem is completely different from what this thread is about, I'd suggest you start an new thread.

---

### Post by inxs44 on 2011-10-06
> **peter_altherr said:**
> i have the same issue as inxs44. my installation is an upgrade of natty amd64 to oneiric amd64. then i uninstalled the natty skype and tried all the workarounds. ended up with the oneiric x86 version (i like the well integrated context menu in the panel) but no correct voice recording. i have applied all workarounds mentionend here in the thread. so now i am going to try the latest one (having audio recorder running while skyping).

i hope the ubuntu team is going to fix that soon as it is a vital skype feature :-)


greetings

peter

Peter at this point the only work around I have found is to download Pulseaudio Volume Control manager in order to get skype mic overall functions to work at this time, I sincerely hope Ubuntu team is able to solve this before Oneiric's due release . As  of now Skype does not work properly on Oct 6 rc of Oneiric either.

---

### Post by inxs44 on 2011-10-06
> **cariboo907 said:**
> Your problem is completely different from what this thread is about, I'd suggest you start an new thread.

I respectfully submit that this issue does fall under the current thread. The problem is in i386 dependency files that we all had to use in order to get skype to load in the 1st place.2ndly the solution is to be found in correcting the current i386 dependency files on which Skype depends for proper execution of it's program. Kindest regards.

---

### Post by cariboo on 2011-10-06
> **inxs44 said:**
> I respectfully submit that this issue does fall under the current thread. The problem is in i386 dependency files that we all had to use in order to get skype to load in the 1st place.2ndly the solution is to be found in correcting the current i386 dependency files on which Skype depends for proper execution of it's program. Kindest regards.

Is it really about dependencies, or a failure in setup, the original poster of this thread couldn't get skype to work at all because of the change to multiarch, you have got skype working, but audio doesn't work for you, so it seems to be a different problem. What's wrong with starting another thread? You may get better help in a new thread instead tacking on to one that has already been solved for most people.

---

### Post by Sworddragon on 2011-10-06
There is already a fix in the ia32-libs so that 32 bit applications are now working on 64 bit systems. This helped me to get Wine running but Skype gives me still an error:

> skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

libxss1 as 64 bit is installed. A workaround is to enable multiarch support and installing skype:i386 with all the i386 dependencies. Is there a way to get Skype running without enabling multiarch support?

---

### Post by inxs44 on 2011-10-07
It would seem we are getting closer & closer to the Oneiric & Skype promised land. Mind you, I repeat, closer. I reinstalled the oct-06 rc of Oneiric 64 bit edition, performed all the updates, once the updates were installed, I installed skype ran a skype test call and it worked perfectly but then I discovered that it was not running on pulseaudio, Then I installed libpulse0:i386 and now skype works as it should recording wise. I hope this observation helps.

---

### Post by effenberg0x0 on 2011-10-07
Weird. I am on Ubuntu 64. I have just ran sudo apt-get update && sudo apt-get upgrade && sudo apt-get install skype. The thing installed normally. I can access it from the dash as expected. It launches and runs OK. I am using standard repos.Not a problem at all with install.

It sounds like ****, but it is not related directly to Skype: My sound setup is messed up (Alsa support for ALC892 is not good, I've been doing trials with other Alsa/Pulseaudio setups). 

Regards,
Effenberg

---

### Post by sonnet on 2011-10-07
> **effenberg0x0 said:**
> Weird. I am on Ubuntu 64. I have just ran sudo apt-get update && sudo apt-get upgrade && sudo apt-get install skype. The thing installed normally. I can access it from the dash as expected. It launches and runs OK. I am using standard repos.Not a problem at all with install.

It sounds like ****, but it is not related directly to Skype: My sound setup is messed up (Alsa support for ALC892 is not good, I've been doing trials with other Alsa/Pulseaudio setups). 

Regards,
Effenberg

That's what I'm wondering about. The people who had problem with Skype did install the application from the repos or did they downloaded the .deb package from skype website and installed it manually?
I'm asking because I want to install it, but if there are problems I'd wait they are fixed.

---

### Post by effenberg0x0 on 2011-10-07
I had no problems using the repos, usinsg the command I posted somewhere above. I guess you could give a try. If it doesn't work, all you have to do is uninstall it with sudo apt-get remove --purge skype. Then you can try other install methods.

Regards,
Effenberg

---

### Post by cariboo on 2011-10-07
Skype is in the partner repositories, so it is the package provided by Skype.

---

### Post by sonnet on 2011-10-07
Strange thing is that aptitude (I use aptitude as I read somewhere it resolve dependencies in a better way than apt-get) won't let me install skype as I get this message:

*Couldn't find package "skype".  However, the following....*


Apt-get on the other hand, doesn't have this problem.
But I read that I should mix the 2 of them.


Also aptitude notify me problems also when trying to install other 32 bit application like acroread and wine, with unresolved dependencies:

[I]Leave the following dependencies unresolved:                                                    
89)     ia32-libs recommends ia32-libs-multiarch                                                      
90)     libqt4-sql recommends libqt4-sql-mysql | libqt4-sql-odbc | libqt4-sql-psql | libqt4-sql-sqlite
[/I]

---

