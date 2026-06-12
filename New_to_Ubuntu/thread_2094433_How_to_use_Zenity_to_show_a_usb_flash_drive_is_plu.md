---
title: "How to use Zenity to show a usb flash drive is plugged in"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by mark allyn on 2012-12-13
Hello everyone,

I am trying to figure out how to post a visible notice on the desktop created by zenity that will show the status of a plugged in flash drive.  The following script 1.  writes a file with that info, 2.  writes a log file to the syslog with the info, and 3. finally tries to open up a zenity window with that info on the screen.

```
str1='Flash attached'
echo $str1 > /home/administrator/flashfile
sudo chmod 644 /home/administrator/flashfile
logger "$(whoami) : usb device plugged in" 
export DISPLAY=:0.0
zenity --info --title="USB Flash Status" --text="Plugged In" --width=200

```The following udev rule calls the script.  The script runs step 1 and step 2, but not the zenity step.

```

SUBSYSTEMS=="scsi", ATTRS{vendor}=="SanDisk", ATTRS{model}=="Cruzer", SYMLINK+="markyflash", RUN+="/usr/local/bin/flashscript.sh"

```
I am aware that udev can't write to the console.  But, I thought there  might be a way to work around this by setting the DISPLAY environment  variable.  Apparently, there's more to the problem then what I have come  up with.

Could someone with better expertise suggest a workaround that actually does?

Regards,
Mark Allyn

---

### Post by steeldriver on 2012-12-13
Again, I don't know if this is the 'right' way to do it (I think a few of us thrashed this around a couple of months back - and what I posted then didn't work for that OP) but the problem as I see it is that not even root has xauthority on a display that another user 'owns'

What I did was give root Xauthority on the primary display by extracting the current user's .Xauthority and merging it into root's:

```
#!/bin/bash

export DISPLAY=:0
export XAUTHORITY=/root/.Xauthority

# create a root $XAUTHORITY file if one does not already exist
[ -f $XAUTHORITY ] || > $XAUTHORITY 
# now merge the primary display's current XAUTHORITY so root can display there
xauth -f $XAUTHORITY merge - < <(xauth extract - $DISPLAY)

# now root can send a message to the primary display :0
zenity --notification --text "$(whoami): usb device plugged in"

```I *think* this is safer than simply opening access up via xhosts - but I will standby to be corrected on that

---

### Post by tgalati4 on 2012-12-13
And why is this needed?  Just about every distro will put a mounted device on the desktop.  Right click-->Unmount device gives you a clue that the device is still mounted.

There is a gnome disk-mounter widget.  Does this not show the status of mounted USB flash drives?

---

### Post by mark allyn on 2012-12-14
Good morning Steeldriver and tgalati4,

Steeldriver:  Thanks.  I must study Xauthority--not familiar with it.  I will also try your code.  Hopefully, this morning, but may have to put it off for a day or two.  I will certainly let you know how it works.

Tgalati4:  Well, the answer is:  to see how to do it.  It certainly isn't important or necessary by any measure I can think of,, but like George Leigh Mallory said of  Everest "it is there".  But I guess from your comment that the Gnome guys got there first.  A pity.  I'm just an also-ran.

Cheers to all,

Mark Allyn

---

### Post by mark allyn on 2012-12-14
Good morning, Steeldriver,

I tried your script, but it didn't produce a zenity dialog.  Just to be certain the script ran I wrote to the log file ( as you had previously advised).  The system did indeed detect the plug in and wrote to the syslog.

Have you previously tested this script?

Thanks for helping me on this.

Mark

---

### Post by steeldriver on 2012-12-14
Hi Mark - yes tested and working here, bit puzzled why it's failing for you however as I mentioned I'm not sure that what I'm doing is 'right' so there may be plenty of gotchas I'm not aware of

Does the /root/.Xauthority file get created? if you delete it then plug in the device, does it get re-created?

Is the display you're trying to write to actually :0 (it may not be if you are running over a VNC session for example)?

---

### Post by tgalati4 on 2012-12-14
That sounds fair enough, but realize that mounting a disk requires root privilege and the xserver is writing to your display with (your)user privilege. By using a root Xauthority you could break other things on your desktop, like updating other widgets on your panel.

But that is what makes linux fun.  If you break it you get to keep both pieces.

---

### Post by allynm on 2012-12-15
Hi Steeldriver and Tgalati4,

I've been slow responding to your posts because I'm traveling and I've had a just awful time trying to log in to the forum.  In fact, I've had to change my uname and password in order to get into the forum.

At the moment, I'm using allynm as the uname.  When I get back to my home I'll revert to the previous uname, mark allyn.

Steeldriver--as near as I can tell, the /root/.Xauthority directory was created.  The DISPLAY variable is :0.  as reported by the env command (includes the period/decimal point following the zero).  

tgalati4:  Thanks for your understanding on this business.  As you no doubt have surmised I'm still very new at this linux stuff...so your caution about breaking things is certainly a propos.  Can you suggest an alternative approach that would be less parlous?  

Cheers,

Mark Allyn  aka allynm

---

### Post by allynm on 2012-12-15
Hi Steeldriver and tgalati4,

I forgot to mention to Steeldriver that when I delete the .Xauthority file in /root and reinstall the flash drive, .Xauthority DOES get created in the /root.

Cheers,
Mark

---

### Post by JKyleOKC on 2012-12-15
This may, or may not, be helpful.

I run a script that automagically starts/re-starts a virtual machine when the system boots, by means of /etc/rc.local. However everything concerning the VM is in my home directory, and at boot time I've not yet logged in and the system is running as root. Consequently the VM has to start under my own user ID in order to be accessible when I do log in, or from a LAN connection via RDP.

To make this happen, the script is run via "su" so that root actually uses "su" to switch to my user ID for running the script and putting the VM into the background but owned by me instead of by root.

Perhaps using this "su" trick to make your script run as the user rather than as root might be a solution.

And perhaps, not...

---

### Post by allynm on 2012-12-17
Hello Steeldriver, tgalati4,JKyleOKC,
 
After reading and rereading your responses I realize I need a much better appreciation of this .Authority / auth command stuff.  Since first attempting to use Steeldriver's code and tgalati4's caution I have been trying to get an understanding of what is happening.  Part of the problem comes from my ignorance of Xwindos/Xserver/Xnetworks. There really is nothing comparable in Windows.
 
I have found some stuff on the internet--the best pieces were from IBM (who else?), but there was another tute from someone with a .de file extension.  These were OK, but left me in a dazed and confused condition.  I don't "get" the basic issue or what I'm trying to accomplish when I give "Authority"....
 
Can any of you point me towards a clear explanatory tutorial on what is happening with this .Xauthority business?
 
Thanks,
Mark Allyn aka allynm

---

### Post by JKyleOKC on 2012-12-17
> **allynm said:**
> I have found some stuff on the internet--the best pieces were from IBM (who else?), but there was another tute from someone with a .de file extension.  These were OK, but left me in a dazed and confused condition.  I don't "get" the basic issue or what I'm trying to accomplish when I give "Authority"....
 
Can any of you point me towards a clear explanatory tutorial on what is happening with this .Xauthority business?For any of this to make sense, you have to have at least an overview understanding of the X Window System, which is what most *nix systems currently use to give you a graphic user interface. The wikipedia description at _[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)_ is an excellent starting point. It gets into excessive detail in a hurry, but you can drill down through the embedded links there to get the big picture, and skip over the unnecessary detail.

Your earlier comment that Windows has nothing like it isn't totally correct; it's there, just hidden from most users. Windows called it "gdi.exe" back at version 3.1, when it was still partially visible to curious users. I think it has since been moved inside other DLLs, but it has to be there. Somehow, the information generated by programs has to be converted into a format that the monitor can display. Originally, video cards did it in their hardware and firmware, but only for plain text data. Photos and drawings simply could not be displayed until the Extended Graphic Adapter came along, and even then the display was primitive. The "gdi" (Graphic Device Interface) package of early versions of Windows added the ability to draw lines in any direction, to simulate curves, and to display shading. That made possible the GUIs we now take for granted.

Meanwhile, the *nix community was developing in different directions but faced the same need. The X Window System was the outcome. And since by then, this community was built around the server-client paradigm, X became a server and each user session became a client... The rest all followed from that.

You'll have a great time coming up to speed; it'll be interesting (as in "may you live in interesting times") but I think you'll find it worth the effort...

---

### Post by allynm on 2012-12-18
Good evening, JKyleOKC,
 
Thank you for your reply.  I'll read the Wikipedia stuff at the link you sent.  Your commentary on the history of this problem was very interesting.  
 
What I have found vexatious was my inability to parse the code that Steeldriver was kind enough to send along.   It was "commented" nicely but the comments assumed a level of sophistication that was not present in my mind.  Not Steeldriver's fault, mind you.  
 
Cheers,
Mark aka Mark Allyn

---

### Post by JKyleOKC on 2012-12-18
> **allynm said:**
> What I have found vexatious was my inability to parse the code that Steeldriver was kind enough to send along.   It was "commented" nicely but the comments assumed a level of sophistication that was not present in my mind.  Not Steeldriver's fault, mind you.That's a rather elegant (in the mathematical sense of minimalistic) bit of "bash scripting" but it definitely doesn't lend itself to easy parsing, especially by anyone who's not intimately familiar with the syntax of the Bourne Again SHell (bash). It really wouldn't help a lot to go through and explain the meaning of each token in the non-comment lines, either. The top-level description is that it first checks to be certain that all the bits and pieces it will need actually exist, then merges the "authority" information that the X server requires together so that said server can contact the logged-in user.

As to just what information that is, the details will be found buried somewhere in that wikipedia entry or something that it references, but for now you can think of them simply as "magic cookies" -- that's how I describe them to myself, and so long as things work, I don't ask how any more because that involves so very many levels of abstraction!

---

### Post by steeldriver on 2012-12-18
Hi Mark (and Jim)

I don't really know any more about the X authority mechanism than what's above (just enough to be dangerous haha)

Basically the way I understand it, when a user initiates an X session on a particular display, the X server generates a 'a magic cookie' which gets saved in the user's .Xauthority file. After that, only clients that have the cookie are allowed to write to that display. Obviously any clients run by the originating user can do that because they can read it from the ~/.Xauthority file.

To allow for non originating users (or more usually, to allow remote clients - via ssh for example) to access the display, various mechanisms exist to extract / merge / manage these cookies. In the script above,

```
xauth extract - $DISPLAY
```simply extracts the cookie belonging to $DISPLAY (whoever owns it - because we are root and root owns the X server we can do that) and outputs it to standard output (indicated by the '-' parameter). Then

```
xauth -f $XAUTHORITY merge - 
```takes the cookie from standard input and puts it into the file defined by $XAUTHORITY, which we previously defined to be /root/.Xauthority - we also export $XAUTHORITY so that it's the appropriate authority file when we invoke zenity. (There's no particular reason we have to use /root/.Xauthority afaik - but that seems as good a place as any.)

The  

```
[ -f $XAUTHORITY ] || > $XAUTHORITY
```line just says "if regular file $XAUTHORITY doesn't exist,  create it" - a less bashistic way would be something like

```
if ! test -f $XAUTHORITY
then 
  touch $XAUTHORITY
fi
```Hope this helps - btw 'man xauth' is not a bad reference

---

### Post by tgalati4 on 2012-12-18
And of course, the X-Windows system got its name because it was one better than the W-Windows system--i.e. Microsoft Windows.

Try to run a command from a remote machine and display the results on a third machine in Windows.  Oh, and be able for one user to remotely display results on hundreds of different remote screens.  Although, I think the modern xserver has 10 displays compiled in as default.  But you can change it.

---

### Post by JKyleOKC on 2012-12-19
I don't think the "W" that came before the first X Window System was from Microsoft Windows. It came from the "V" operating system at Stanford University, according to the wikipedia article... And there were many others, dating back into the mid-70s, before Microsoft. Apple's "Lisa" was apparently Microsoft's inspiration to create a GUI (at least, according to the unauthorized biography of Bill Gates that I read many years ago).

---

### Post by allynm on 2012-12-19
oGood afternoon, Steeldriver, tgalati, and JKyleOKC:

Steeldriver--the parsing for me was very helpful.  You did exactly what I needed to have you do.  There were two questions I had about syntax--namely, what does " - " do...I'm such a novice with linux that I didn't know what to make of that token.  Second was the double " || " token.  I didn't recognize it either.  

Why isn't it the case that
xauth extract - $DISPLAY
does not require "sudo" ?  

I'm still re-reading your in-depth discussion.  Slowly dawning on my brain what is happening.  

The history lessons on "W" and "V" were interesting.  In an odd way, it's just because of the difficulty of doing in Windows what  tgalati4 says that I have never needed to worry about this X-stuff functionality  It was hard enough for me to figure out how to do RPC's in Windows.

As an aside, I spent this morning installing 12.04.1 on an exernal (Seagate) hard drive.  After discovering that I had to change the boot sequence in order to get it to work, it ran (is running now!) beautifully.

Cheers, 
Mark aka mark allyn aka allynm

---

### Post by steeldriver on 2012-12-24
OK as some of you have found out, **THE SCRIPT I POSTED EARLIER DOESN'T WORK**

Looks like I misunderstood how the [FONT=Courier New]xauth extract[/FONT] command works. I thought (hoped?) that it actually queried the X server and (at least for root) could therefore extract the credentials for any display. In fact it seems like it works the same as any other xauth command i.e. **just queries the file defined by the current XAUTHORITY variable** (or by the -f switch if given). So

```
xauth -f $XAUTHORITY merge - < <(xauth extract - $DISPLAY)
```just takes us round in circles. I don't know exactly why it *appeared* to work for me - presumably because I'd been playing with other commands and had managed to create a valid root .Xauthority file.

I still don't know the right way to do this - Mark has suggested elsewhere that it is via dbus. If we are using lightdm, then it seems like we can access the root authority in /var/run/lightdm/root exactly as we would when starting an x11vnc server, and there seems to be an equivalent for gdm in /var/lib though I have not tested it. I don't know what to do for other DMs or indeed if we are running X directly with no DM.

Here is the latest version I'm testing:

```
#!/bin/bash

DISPLAY=:0.0

# we should probably do a nice case..esac based on the display
# manager, with a fall through in case we are not running a DM
# i.e. starting X directly

if [ -f /var/run/lightdm/root/${DISPLAY%.*} ]; then
  # lightdm: attempt to authorize via lightdm root authority
  XAUTHORITY=/var/run/lightdm/root/${DISPLAY%.*}
elif [ -f /var/lib/gdm/${DISPLAY%.*}.Xauth ]; then
  # gdm: attempt to authorize via gdm - NOT TESTED!
  XAUTHORITY=/var/lib/gdm/${DISPLAY%.*}.Xauth
else
  # no DM : attempt to find the user ~/.Xauthority
  XAUTHORITY=
fi
logger "$0: using XAUTHORITY=$XAUTHORITY"

DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY /usr/bin/zenity --notification --text "$(whoami) usb device plugged in"
```PS [FONT=Courier New][ -f $XAUTHORITY ] || > $XAUTHORITY[/FONT] was a Bad Idea (TM) - it creates the file with default mode 664 (should be 600) which is a security no-no. Although that can be fixed with a umask it turns out not to even be necessary to create the file - xauth complains if the file is missing but WILL create it PROVIDED IT GETS A VALID COOKIE.

---

### Post by allynm on 2012-12-24
Good afternoon, Steeldriver,

By Jove, you nailed it!  This is a nice Christmas present, indeed.  The only thing that appeared to not work quite as expected was the "OK"  button.  When pressed it did not close the dialog.  Pressing "Cancel"  did, however.

Your paragraph reading:


[HTML]
I still don't know the right way to do this - Mark has suggested  elsewhere that it is via dbus. If we are using lightdm, then it seems  like we can access the root authority in /var/run/lightdm/root exactly  as we would when starting an x11vnc server, and there seems to be an  equivalent for gdm in /var/lib though I have not tested it. I don't know  what to do for other DMs or indeed if we are running X directly with no  DM.[/HTML]begs a novice like me to ask you to explain what this lightdm and gdm business is/are(?), especially as regards the need for "root".

If you wouldn't mind...

I'll do some research on both,. but if you have a moment, I'd really appreciate some elucidation.

Cheers,

---

### Post by allynm on 2012-12-24
Hi Steeldriver,

I substituted your zenity call with a call to a tiny GTK+-3.0 app I wrote.  When I plug the flash drive in, it does indeed run the app and a window with a custom window and frame with label appears--just as it should.  However, when I attempt to close the window by hitting the "x" button, on the first attempt, nothing happens--the window stays open.  On the second attempt, the window closes and the flash drive window opens on the desktop.  Moreover, the GTK+-3.0 icon app remains on the side bar and only closes completely if I manually right-click on the iccon and select the correct option.

In short, something seems amiss with the "destroy" signal from the window.

Hmm.  Something to ponder.

I did a bit of reading on lightdm and dimly grasp what it's about.  What does /lightdm/root have to do with the $DISPLAY?

Cheers,
Mark aka allynm

---

### Post by allynm on 2013-01-01
An update on this thread--

I have been taking a crash course (self-taught, highly inefficient) in how to use XAUTHORITY permissions.  Steeldriver was the cause of this, as you may have surmised.  I've learned a good deal, but there is still more to learn.

At any rate... the following script runs when I plug a usb stick into a port.  UDEV calls the script.  The script runs, but produces an anomalous result.  Instead of a single ZENITY window being opened on the terminal, four get opened.  Each has to be closed individually, and then the Desktop looks normal with a window showing the contents of the USB drive.  This happens whether or not the script runs in the FG or in the BG.  

> #!/bin/bash
if  [ "${ACTION}" == remove ]; then
         echo "${ACTION}" > /home/mark/Desktop/USB_OFF
         rm -rf /home/mark/Desktop/USB_ON
elif [ "${ACTION}" == add ]; then
        echo "${ACTION}" > /home/mark/Desktop/USB_ON
        rm -rf /home/mark/Desktop/USB_OFF

        export DISPLAY=:0
    
         xhost +local:
    
         echo "XXXX\n" | sudo -S -u dave /usr/bin/zenity --notification --timeout=3      --text="Plugged in, Man" &
    
         xhost -local:
fi
#
exit 0Can someone suggest why this is happening?

Regards to all and Happy New Year!

Mark Allyn AKA allynm

---

### Post by JKyleOKC on 2013-01-01
My best guess is that UDEV is calling the script more than once. You can add a line to the script, right before the existing "echo", something like this:```
echo date " script called" >> /home/dave/script_debug
```I've not tested this but the idea is to write one line to the "script_debug" file each time the script is called, with a timestamp so you can tell when it happened.

If the USB device happens to be a "universal card reader" like the one I use to copy camera SD cards into my system, UDEV will be called once for each different kind of card supported! I discovered this the confusing way the first time I used the gadget.

---

### Post by allynm on 2013-01-01
Hello JKyleOKC,

You're right.  It's getting called four times.  Do you have any idea how to stop this?

Thanks for the snippet and suggestion.

Regards,

Mark AKA allynm

---

### Post by JKyleOKC on 2013-01-01
While I hate to sound like "RTFM" folk, in this case the best suggestion I can offer is to study "man 7 udev" to find out about all the possible environment variables available to your script.

I think that I would add an echo of some of those to the "debug" line I suggested, to see if any of them provide a unique indication you could use to exit from the script right at the beginning after the first call.

Another possibility would be to make the script create some sort of "semaphore" file or environment variable the first time it's run, that would cause the script to exit without doing anything on the second, third, and fourth calls. You might be able to make an environment variable into a counter so that on the fourth call it erases itself just before the exit. I've not tried to work out all the details of doing this, though, and I can tell you from experience that all sorts of "race conditions" can come into play here. I just spent two full days debugging a simple "awk" program, only to find out that absence of two commas was the total cause of my problem!

---

### Post by allynm on 2013-01-01
Good afternoon, JKyleOKC,

Yes, I take your point about the FM and it is good advice.  I have been hunting around on the Web to see if there might be a workaround.  Several threads on StackOverflow have pointed to the use "lock files"  (flock command) as possibly a viable solution.  

One such snippet is this 

> flock -n /var/run/your.lockfile -c  /your/scriptAccording to the author (arnaud576875:

> It will return immediately with a non  0 status if the script is already running.What do you think?

Regards,
Mark Allyn AKA allynm

---

### Post by JKyleOKC on 2013-01-01
I doubt that the script will still be running on the subsequent calls by UDEV, although it might be. I suspect, however, that UDEV makes its calls sequentially, waiting for each to return before launching the next. Proving this one way or another would be difficult without a mechanism for sub-microsecond timing being available to the script; the "date" command only reports to the nearest full second.

I've taken another look at the man pages for udev, and there's a "$number" variable mentioned that just might offer a solution. It's apparently the "1" in "sda1" and might increment on subsequent calls since there's only one actual device involved here. It's possible that udev assigns a single device name to it and passes partition numbers on each call -- and if this is the case there's the counter that would let you get out with no action if its value was greater than 1. Perhaps some testing with the debug echoes can prove or disprove such a solution...

---

### Post by allynm on 2013-01-01
Hello again, JKyleOKC,

I took your advice and looked over the udev man and saw what you saw.  But, I didn't make the connection you made in terms of serially upping the count until all partitions had been dispatched.  I like your idea.  Let's give it a try.

Spent several fruitless hours on a different workaround that had to do with counting repetitions of the bash pid.   Went nowhere good.

Thanks for helping on this thorny liitle problem.

Regards,
Mark AKA allynm

---

### Post by steeldriver on 2013-01-01
Just thinking out loud, but I wonder if it might be possible to restrict your rule so it is only triggered on the raw disk node rather then each of the partitions? I've never tried it but possibly something like

```
KERNEL=="sd?", ATTRS{ }...
```

---

### Post by allynm on 2013-01-01
Hi Steeldriver and JKyleOKC,

Well, you nailed it, JKyleOKC.  I went back to the UDEV rule and added in KERNEL=="sd$1", left the rest of the UDEV script alone.  This I believe is what steeldriver was "driving at", right?   Ran the thing and BINGO, up popped just a single Zenity window.  If I hit the "OK" button, the window showing the file in the USB drive opens and all is well....

The script I used is shown a couple of posts ago.  Note that I am using Xhost, not xauth.  I also used this funny trick of feeding my password in on stdin (plus the -S sudo option) to avoid the problem of entering my password during script execution.  

I want to play a bit with xauth, but I think we can basically consider this particular thread solved.  Thanks very much for all your generous help.  I really learned a lot from trying to solve this problem and I never bricked my box....yet.

Regards,
Mark Allyn aka allynm

---

### Post by JKyleOKC on 2013-01-01
Glad to hear it! There's a huge amount of untapped power in those udev rules. I've modified some of mine to force my three network adapters to always wind up with the same interface names; until I did this, they would scramble themselves at each reboot. This box has to have two since it serves as the router for my home-office LAN, and one of the first I put in became flaky so I added a third. Then the flakiness cleared up so now one of the three stays disabled but is available as a spare if need be...

Incidentally, will your script work if you remove the "-rf" option from the two "rm" commands? That's an extremely dangerous combination, and I wouldn't think you would need to force removal of the flag files, or need recursion in the command either...

---

### Post by ncwalker2010 on 2013-01-02
Hi guys.  My own little project has led me here and I have found myself in much the same spot as Mr. Allyn.  That being getting zenity to run on the active user terminal from a script launched by a udev rule.

**Quick background:  **This is a home system.  I run Linux at home for the kids and I because it is way easier (to me) to maintain than keeping up with the upgrades on Windows.  So we have several users with several computers on somewhat of a Linux network and a PC in the kitchen we use as a server.  When anyone plugs in a USB I am fine with what Linux 12.04 does.  Open up a window to explore it.  But for a specific flash drive, the one that holds my car audio files, I want it to rsync with my music directory on this server automatically.  (Right now, I do this with a script manually.)  Yeah.  It's not like I do this every day.  More like once every 6 mos.  But I have chose to automate this, like Mr. Allyn, to see if I can.  So sorry for the thread jack, but I'm not sure if it is.  Here is my algorithm so far:

1) Plug in the USB
2) udev checks the serial number and if it is my specific USB it fires a launcher script in /usr/local/bin
3) this launcher script fires a working script in MY directory /home/mark/bin.
3a) it does this so the udev script "releases" and doesn't tie up that end
3b) yes, my real life name is also mark, like Mr. Allyn's
4) the working script executes rsync and sychronizes my car audio disk.

What I DON'T like is there is no feedback that this is actually occurring.  I know that it is because I have checked it by testing it, but I don't like that I cannot tell when it is complete so I am also trying to get zenity to pop me up a message.

**My understanding so far:**
So when the udev rule fires the launcher, it is doing this as root, therefore there is no "terminal" for this to run.  This thread seems to have solved it with "xhost" that I know nothing about, but I am reading.

[B]My question for the masters:
[/B]When I plug in a USB normally, Linux automatically does things like open up Nautilus to explore the flash drive.  Isn't that using a udev rule?  If so, isn't that ALSO executing as root and how does THAT affect the logged in user's terminal?  That seems to me to be functionally the same thing....

---

### Post by ncwalker2010 on 2013-01-02
So I looked at the other udev rules out there.  Why? To see what it was doing with USBs normally.  After all, it DOES launch nautilus from root on the user terminal.

This is in one called 50-udev-default.rules:

```
# 'libusb' device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", IMPORT{builtin}="usb_id"

```So the first line looks like it is reassigning the permissions from the device from the defaut of 660 to 664 giving read permission to everyone. And the next line is sucking in some device properties as variables, though I don't know what or why.

Then in 70-udev-acl.rules, which I believe executes or occurs later, we find:

```
# SCSI and USB scanners
ENV{libsane_matched}=="yes", TAG+="udev-acl"

```Which looks like it is adding some internal tag to USB devices.  The definition says this searches up the hierarchy of the device until it finds the "udev-acl" tag.  Again, I have no idea what is really happening, but I imagine it has investigated the "guts" of the device and now pulling back to the attachment point to do something with it.

But the end of the same file then has:
```
# apply ACL for all locally logged in users
LABEL="acl_apply", TAG=="udev-acl", TEST=="/var/run/ConsoleKit/database", \
  RUN+="udev-acl --action=$env{ACTION} --device=$env{DEVNAME}"

LABEL="acl_end"
```Which then looks like anything tagged with "udev-acl" gets run through some library.  Which I expect is firing off Nautilus, or some such, on the users interface and passing control from root.

Just wish I knew what to do with this.... :-)

---

### Post by steeldriver on 2013-01-02
You're making excellent progress, I think

I don't *know* the answers to your questions - I've been fishing around since Mark first mentioned DBUS and I *think* the way it goes is that udev sits on the kernel side, and dbus sits on the user ('session') side. Somewhere in between there is a handoff between kernel-space and user-space (it used to involve HAL but doesn't since kernel 2.something). Possibly udev 'emits' uevents and dbus monitors them? and then user applications themselves monitor dbus?

There seems to be both a system dbus instance and a session dbus instance - maybe polkit sits between the system bus and session bus and determines what system events a user session is allowed to 'see'?

TBH the documentation that I have been able to find so far is severely lacking / out of date

The bottom line, I am beginning to realize, is that any attempt to display messages in the user-session direct from a udev RUN script is a nasty hack that is probably bypassing the existing IPC mechanism. Perhaps what we should be doing is either tapping in to an existing part of the desktop (possibly even nautilus?) and adding a zenity / popup action there, or creating a separate little user-space daemon that monitors the session dbus for the appropriate uevent?

---

### Post by allynm on 2013-01-02
Good morning JKyleOKC, steeldriver, & welcome NCWalker,

JKyleOKC--yes, it will work if the -rf options are removed.  Not sure exactly why I put them in the command in the first place.  All I wanted to do was put a little "toggle" notice on the desktop that gave the state of the device.  It works fine without the dangerous -rf's.

Mr Walker:  Welcome to the party!  I am a recent arrival the world of MSFT and so matters like authorizations, XServers, logging in as another user (and how to do that) are all quite new and strange.  No doubt MSFT has similar functionality but they are hidden from most of the casual, hobbyists like me.  There is, as far as I know, no Xserver-like entity within Windows--there probably is--but the average joe will not need to deal with it.  Up pop the windows....

Unfortunately, the Xauthority/xauth/xhost stuff is not very well documented.  I have yet to encounter a concise, readable, "big picture" tutorial that puts it all together.  The xauth/xhost man pages are the usual terse descriptions.  The best single piece I have found was written by Ian Shields of IBM.  You can find it at [http://www.ibm.com/developerworks/library/l-basics/section6.html](http://www.ibm.com/developerworks/library/l-basics/section6.html).

I will read your two posts more carefully.  At the moment I must run off to my dentist's office for another of her savage cleanings.

Regards,
Mark Allyn aka allynm

Back later.

---

### Post by ncwalker2010 on 2013-01-02
Mark - I am relatively new to Linux as well.  I mean, I have been using it for a few years, but this is my first foray into modifying it and attempting to make it do what *I* want.

Steeldriver - I am thinking along those lines too... have the root set some flag that the user is monitoring.  And when the user sees it, then do the thing you want to do.  But then what about acknowledging?  So you don't do it again and again.  Won't we run into trouble needing to set the flag back?

I cannot believe this is so hard.  We need the command that says give control over to the user at this point .... or some such.  On a whim I tried:

```
sudo do_what_the_f@ck_i_am_asking_please
```But that didn't work. :-(

I did find this link which looks promising.....  but I have not tried it yet.

[http://ubuntuforums.org/showthread.php?t=994233](http://ubuntuforums.org/showthread.php?t=994233)

and this one...

[http://www.linuxquestions.org/questions/linux-software-2/using-udev-to-automatically-run-a-script-on-optical-disc-mount-792428/](http://www.linuxquestions.org/questions/linux-software-2/using-udev-to-automatically-run-a-script-on-optical-disc-mount-792428/)

Seems to all hinge around EXPORT DISPLAY 0.0

---

### Post by allynm on 2013-01-02
Hello Mr Walker,

Yes, for sure you will need to export DISPLAY=:0  If you are running the script as called from UDEV, in my experience you will also need to get authorization to write to the terminal, either with Xhost (the simple way, but less secure), or with xauth.  Ian Shields' piece on the link I sent shows you how to do it either way.

But, as I read your first post and if I understand what you are trying to do, the udev rule itself will be tricky, I think.  As I read it, you are trying to get a zenity notification after the COMPLETION of a task, not at the instant the device is activated.  

I'll have to look at udev rules more carefully, especialy the ENV{} items....

Regards,
Mark Allyn aka allynm

---

### Post by JKyleOKC on 2013-01-02
Another not-well-known command to explore for this sort of thing is "inotify" (which you will have to install from the repositories, since it's not part of the standard installation). It does quite a bit of what ncwalker wants; I'm using it to sound a notice to me whenever a new file appears in the "incoming" directory of my private ftp server.

The package name is "inotify-tools" and the man pages for the individual tools pretty well describe all the things you can do with them, with a few examples that work well. I simply edited one of the examples to get the action I wanted...

---

### Post by allynm on 2013-01-04
Hi Steeldriver, JKyleOKC, & NCWalker,

I thought this thread was finished...but I was wrong.  Yesterday I tried to use my little xhost script just to be sure it worked...and it didn't.  I still have no idea what went wrong, but spent a very frustrating day doing another work-around.  Finally got the thing to work right.  The call from UDEV worked and the script ran, but wouldn't right to the desktop.

On my system I have created a second user named Dave.  The UDEV script itself has not changed, but what has happened is that I created a magic cookie for Dave to use.  I did this as follows:

```

xauth -f $XAUTHORITY nextract - :0  #prints the cookie to stdout

echo "cookie over multiple lines since it is really really long" |
xauth -f ~dave/temp-xauth nmerge -


```OK.  Now I write the new script for UDEV to call.

```

#!/bin/bash

    export XAUTHORITY=~dave/temp-xauth
    export DISPLAY=:0
    sudo -s -u dave zenity --info --text="Plugged in"  
exit 0


```...And, this code runs.

Now, in post #19 Steeldriver has written code that also runs successfully and doesn't resort to a second user (Dave in this case) to write zenity to the desktop.  The only problem (at the time) with Steeldriver's code was that it called Zenity 4 times, if you remember.  I later discovered -- thanks to JKyleOKC-- that this was a problem with the UDEV script, not Steeldriver's code.  

Two questions arise:
1.  How does Steeldriver's code work--what is this thing about "root" at Lightdm.?
2.  Second question concerns Magic Cookies.  How long do they last?  Forever?  Until I reboot?  

Hoping to hear from all of you.

Thanks for working on this with me.  I've gained a lot of knowledge.

Mark aka allynm

---

