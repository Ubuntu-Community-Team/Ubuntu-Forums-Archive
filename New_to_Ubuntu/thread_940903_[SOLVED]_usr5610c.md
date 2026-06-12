---
title: "[SOLVED] usr5610c"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by ranch hand on 2008-10-07
I have a Dell XPS 420. Came with Vista Home Premium. This is the last straw for me.

I bought a new 320G WD HDD and installed Hardy Heron. This is great. No modem detection, this is not great.

Got rid of the Connexant d850 and installed a US Robotics 5610c. This is sold by dell and according to the CD and the USR website, compatible with linux kernals 2.3 and above. They say installation should be automatic.

Through terminal and with some help over the phone with my son we can detect an unknown modem at /dev/ttys0.

When I boot up the modem dials out in a rather noisy fashion, which sounds like it does when dialing on the MS HDD.

There is no connection detectable and I do not believe there is one.

I put in a SUSE 10.3 live CD and had no trouble getting the modem detected. It was too late to try configuring the connection then and I could really see no point in it. It was just to test the ability of at least some linux distro seeing this modem.

I sure hope that someone has some idea what to do here because I don't. I really want to be rid of this MS Vista HDD. The reason I went with 2HDDs is that I really don't want MS on here at all.

With the modem straight there would only be one more problem that could be worked out with out MS.

Please help,
ranch hand

---

### Post by phidia on 2008-10-07
Take a look at the Ubuntu wiki on [dial up modem set up]("https://help.ubuntu.com/community/DialupModemHowto").
If you have any problems with that let the thread/forum know where you get stuck.

---

### Post by stephanvaningen on 2008-10-07
Unfortunately that page does not mention US Robotics modems... but starting with the scanning mentioned on that page should get you one step further.
What's the result of the scan?

> **phidia said:**
> Take a look at the Ubuntu wiki on [dial up modem set up]("https://help.ubuntu.com/community/DialupModemHowto").
If you have any problems with that let the thread/forum know where you get stuck.

---

### Post by phidia on 2008-10-07
I should have paid more attention to the modem model thanks for reminding me steph.
That modem is a hardware modem it shouldn't need any driver configuration.
See [this site]("http://linux.wikia.com/wiki/Dial-up") for reference.
I don't know what's going on but you should try to install gnomeppp.
Before you can get your modem fully working you need to open a terminal and enter "sudo pppconfig" You might not need sudo but I think you do-it's been a while since I've used dial up.

---

### Post by ranch hand on 2008-10-07
> **phidia said:**
> Take a look at the Ubuntu wiki on [dial up modem set up]("https://help.ubuntu.com/community/DialupModemHowto").
If you have any problems with that let the thread/forum know where you get stuck.

I have gone through all that for the Winmodem that was in  the box when we bought it.  Just for your entertainment - Scanmodem never worked at all.

cd /dev 
rm modem         this is refused because doesn't see modem
ln -s ttyS0      lists unknown modem
Minicom          gedit = blank page

---

### Post by ranch hand on 2008-10-07
> **stephanvaningen said:**
> Unfortunately that page does not mention US Robotics modems... but starting with the scanning mentioned on that page should get you one step further.
What's the result of the scan?

I don't have time to go through all this right now - on lunch break.  Need to get back to fence fixxing.

Will check later this evening and get back.

---

### Post by ranch hand on 2008-10-07
> **phidia said:**
> I should have paid more attention to the modem model thanks for reminding me steph.
That modem is a hardware modem it shouldn't need any driver configuration.
See [this site]("http://linux.wikia.com/wiki/Dial-up") for reference.
I don't know what's going on but you should try to install gnomeppp.
Before you can get your modem fully working you need to open a terminal and enter "sudo pppconfig" You might not need sudo but I think you do-it's been a while since I've used dial up.

I am just in for lunch from running fence.  We ship soon and it is nice if you can find the buggers.

Will try this stuff and check links this evening.

I believe I may try reinstalling the modem.

---

### Post by ranch hand on 2008-10-07
OK
Started the evening by;
remove modem
fire up ubuntu
can't find modem
shut down ubuntu
install modem
fire up ubuntu
dials on boot up before and during log in
connection icon has red triangular alert with !
cursor over renders "no connection"
/dev: rm modem  renders "rm: cannot remove modem: no such file or directory

I was also informed that minicom was not installed, worked last night.

There are two reasons I am using and internal modem.  1: I am used to them and have enough clutter around the computer.
2: No serial ports on this box at all.

This may be part of the problem.  When I ordered the modem I also got a RS232 card with 2 serial and 1 parallel ports.  I installed this so I could use an old HP Deskjet 712c printer.

This works on the Vista side of the computer but not on the Ubuntu side.  As this is a minor problem I have been ignoring it.  Why?  It is very clear that running any flavor of linux is tough without an internet connection.

I am starting to wonder if I should just save the few files I have on the Ubuntu HDD to CD and reinstall Ubuntu with the modem connected and the serial card in with printer connected.

There is undoubtedly better ways of installing new hardware and this may not work.  I am used to MS though and there, as we all know, reinstall Windows is one of the first, not last, things to try as you will get there anyway.

Speaking of which, Vista in general and IE7 in particular are getting even more unstable.  I'm shocked.
Thanks

---

### Post by ranch hand on 2008-10-07
Oops, I forgot.
I checked all the links.  Nothing seems to help although they might if I ever get the modem to be seen by Ubuntu.

I must have it configured close to right because it does try to connect inspite of claiming there is no modem.

---

### Post by ranch hand on 2008-10-08
Busy hour:
download minicom
burn to CD
shut down
fire Ubuntu
goes thru dial agian same deal
run thru USR CD commands
minicom 2.3 on terminal screen!
says modem at /dev/ttys1!
try AT at promt does not display
try at at promt does not display
try CTRL+A Z for minicom help
nothing I dare try helps

The at business is from USR CD: if minicom comes up type AT at promt and press enter.  If AT displays as you type and OK appears after you press enter install worked.  If not redo install.

Now, another thing comes to mind.  I did install a lib file needed to install free drivers for winmodem as it was a dependancy.  There was another but I never finished it as it needed to be compiled and if I got it compiled from the CD (looked dicey as could not get a clean copy from CD had uneditable aditions from Windows somehow) I would end up with a 14K connection.  If you are familiar with dialup you know that you are lucky to get 10% of your rated speed.  Didn't appeal.

Could that lib file somehow have screwwed with the support that is supposed to be in the kernal?

It is after 10.  I need to eat and sleep.  Another busy day tomorow.  Hopefuly no "ranch adventures".
Thanks again

---

### Post by phidia on 2008-10-08
Did you try "sudo pppconfig" in a terminal? That will create files you need to do dial up. Also wvdial and gnome-pp are useful applets.

---

### Post by ranch hand on 2008-10-08
No I have not.  I have assumed that I needed to have the modem actually show up in a file somewhere.

I did try going thru the config box again and changed the modem setting from ttys0 to ttys1.  This caused the modem to quit responding in any way.  Switching it back to ttys0 caused it to try dialing again.

I will give the comands a try.
Thanks a bunch

---

### Post by ranch hand on 2008-10-08
Tried the pppconfig comand.  Thats neat.  Didn't work, could not find modem.  Tried ttys0, ttyS0, ttys1, ttyS1.  Could not search on its own because "can't probe while pppd is running".

Looks  a lot easier than the gui setup.

Thanks, that was fun.  one of these days I will get this thing running.  I think I might enjoy it.
Well back to the cows.

---

### Post by phidia on 2008-10-08
Could you provide the output of "lspci" entered in a terminal please?

What is the physical connection of your modem-pci slot? 

I think that is what you stated earlier. You may need to move your card if you have a lot of slots. 

I've seen where a pci card slot modem in the last slot of a six slot computer would not set up correctly, but that just a thought/guess. For reference see [this]("https://help.ubuntu.com/community/DialupModemHowto/Setserial?highlight=(minicom)"). This is the important line though: > By default, only ttyS0-ttyS3 (COM1-4 in DOS/Windows terminology) are configured by the kernel, using IRQ 3 and 4.

Also you said you had [mincom]("http://linux.die.net/man/1/minicom") working-am I right? You can get a connection with minicom but it is some work. See provided link.

---

### Post by ranch hand on 2008-10-08
Here is the lspci print.

There are 4 slots.  This one is the first one or bottom one.
Above it I installed the serial card and it, on MS is LPT1, Com5, Com6 now that it is installed.

On Ubuntu the way that we are getting dialling action, if no results is by configuring the gui config to read that the modem is on ttys0.  No others get any responce.

---

### Post by ranch hand on 2008-10-08
Well, I don't know just what to say.

I moved the modem to a different slot.  Did not screw up Vista.  I was shocked.

Fired up THIS HDD.  The Ubuntu or as I like to think of it the real one.  Same old same old.  Ran pppconfig.  Tried dialing.  Sounded good, like a connection.  Icon, right now, says no network connection, but now it lies.

This modem is working even if half of this system does not believe it.

According to System Monitor,  With the same modem, from the same box, on the same connection I am getting about 30 to 50% better speed under Ubuntu than under Vista.

Anyway I owe some thanks to phidia.  I probably could have made it work, but certainly not  before doing a lot of stupid thing and not before next year.

How do we mark this thread solved?

---

### Post by phidia on 2008-10-09
> **ranch hand said:**
> Well, I don't know just what to say.

I moved the modem to a different slot.  Did not screw up Vista.  I was shocked.

Fired up THIS HDD.  The Ubuntu or as I like to think of it the real one.  Same old same old.  Ran pppconfig.  Tried dialing.  Sounded good, like a connection.  Icon, right now, says no network connection, but now it lies.

This modem is working even if half of this system does not believe it.

According to System Monitor,  With the same modem, from the same box, on the same connection I am getting about 30 to 50% better speed under Ubuntu than under Vista.

Anyway I owe some thanks to phidia.  I probably could have made it work, but certainly not  before doing a lot of stupid thing and not before next year.

How do we mark this thread solved?

Devs aren't focused on dial up connections so much as a lot of the world uses broadband, but I'm glad you got it working. I'm guessing an older release might have worked better.

To mark the thread solved as the original poster-I think you just need to edit the Title with the word "Solved" in front of the topic.

---

### Post by ranch hand on 2008-10-09
phidia
There really are a lot of people, particularly in the 3rd world using dial up.  But that is neither here nor there.

This modem works fine even if the desktop icon doesn't know it.  Runs slightoy ahead of its own performance under Vista.  I am getting a very steady whooping 4.4kps.  The best that the winmodem could hold at was about 3.1kps.

That slow is tough, there is a huge speed drop below 3kps in terms of time of download that I don't understand but have watched.  Add that to the fact that a winmodem will not "grab" hold of the connection and you end up spending hours trying to succeed in downloading files.

I have never succeeded in downloading any security updates for Vista.  I didn't care much because  that was one of the things that made LOL and decide to go with a linux OS.  Kind of silly to produce the OS with the most holes and then make the patch files too big for people to get.

I can't seem to edit the title just the body of messages.  Not important, I know it is fixxed or I would be sending this under Vista.

That HDD has been retired for use only in dire emergency.  We didn't run it long enough to hve many files that we really need, besides being worried about the lack of security and obvious instability.

Anyway, thanks again, I'm having fun with this OS which is counter to my experience with MS.

---

