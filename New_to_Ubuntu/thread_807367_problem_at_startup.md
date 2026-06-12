---
title: "problem at startup"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by xenocide13 on 2008-05-25
i have been using ubuntu for the past 5 days or so
it has all been working fine i was here on the forms a few minutes ago and my computer froze
no big deal i restarted it but now whenever i try to open 
firefox or an application nothing comes up and it just stays there wont let anything else work
any advice or help?

---

### Post by mikewhatever on 2008-05-25
> **xenocide13 said:**
> i have been using ubuntu for the past 5 days or so
it has all been working fine i was here on the forms a few minutes ago and my computer froze
no big deal i restarted it but now whenever i try to open 
firefox or an application nothing comes up and it just stays there wont let anything else work
any advice or help?

Can you describe exactly what happens at startup and to what stage do you get. Can you see the desktop? Copy and post here any error messages you get.

---

### Post by xenocide13 on 2008-05-25
it compleatly loads, i can see everything, no messages. when i try to open firefox for example it stays highlighted like i still have the mouse over it but it never opens that happens with all aplications

---

### Post by HalPomeranz on 2008-05-25
Any error messages at the end of /var/log/messages or ~/.xsession-errors?  To see the last 20 lines in these files you might do:

```

tail -20 /var/log/messages
tail -20 ~/.xsession-errors

```

---

### Post by xenocide13 on 2008-05-25
cant get into my terminal =/

---

### Post by HalPomeranz on 2008-05-25
> **xenocide13 said:**
> cant get into my terminal =/

<Ctrl>-<Alt>-<F1> will take you to a text-mode console that will allow you to log in.

<Ctrl>-<Alt>-<F7> will take you back to your windowing environment when you're through.

---

### Post by xenocide13 on 2008-05-25
Nope. No error messages


Update, When i try to open firefox then do the ctrl+alt+f1 and then go back to the desktop the menu bar and the pane bars stay gray and blank other then my username network connection and sound
Does that help at all?

---

### Post by xenocide13 on 2008-05-25
Another update
the screensaver seems to be working fine
i can open a folder that is on my desktop but when ever i try to go up a level or anything like that i get an error messaqge saying that the file browser is not responding then it gives me the option of waiting or force quit, if i quit i lose all the icons and on my desktop

---

### Post by HalPomeranz on 2008-05-25
> **xenocide13 said:**
> Nope. No error messages


Update, When i try to open firefox then do the ctrl+alt+f1 and then go back to the desktop the menu bar and the pane bars stay gray and blank other then my username network connection and sound
Does that help at all?

Meh.  It definitely sounds like something in your windowing environment is not starting properly.  I thought of one more place to look for error messages-- trying looking in /var/log/Xorg.0.log.  Without some sort of error message to go on, this is going to be really hard to debug...

The only other thing I can think of is to make sure that the ownerships in your homedir haven't gotten messed up in some way.  Try this:

```

find ~/ | sort >/tmp/allfiles
find ~/ -user ***<yourusername>*** | sort >/tmp/userfiles
diff /tmp/allfiles /tmp/userfiles

```

Replace ***<yourusername>*** in the code above with your user name on your machine.  If you get any output from the diff command, then some files in your home directory are owned by a different user.  That might be the cause of your problem or it might not.

---

### Post by xenocide13 on 2008-05-25
i think that i am typing it in wrong because i have no idea how to put the line that is straight up and down in a command

yea i know its pathetic

I went back and ran
tail -20 ~/.xsession-errors
and the only error i see which wasent there the first time is

"nautilus=share-message: called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare : cannot open usershare directory /var/lib/samba/usershares. error no such file or directory please ask your sytem admin to enable user sharing

---

### Post by HalPomeranz on 2008-05-25
> **xenocide13 said:**
> i think that i am typing it in wrong because i have no idea how to put the line that is straight up and down in a command

On my keyboard the "pipe" character is <Shift>-\ (right under the backspace key on most US keyboards).  On most keyboards it's represented with a little break in the middle of the vertical line, rather than as a solid line as it appears in these forums and on the command line.

> **xenocide13 said:**
> 
I went back and ran
tail -20 ~/.xsession-errors
and the only error i see which wasent there the first time is

"nautilus=share-message: called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare : cannot open usershare directory /var/lib/samba/usershares. error no such file or directory please ask your sytem admin to enable user sharing

I'm fairly certain that message is not related to your problem, but thanks for double-checking.  Were you able to check /var/log/Xorg.0.log?

---

### Post by xenocide13 on 2008-05-25
acpi error (psparse-0355): namespace lookup failure AE_Not_found

ACPI Exception (evgpe-0576: ae_not_found while evaluating gpe method

that came up in the tail 20 log

and hitting shift does nothing for me in the command bar

---

### Post by xenocide13 on 2008-05-25
another thing that i dont get is
before i log in i can shutdown restart
hibernate and all that through options
but once i log in then i try to go to the 
power button or anything like that it locksup

---

### Post by xenocide13 on 2008-05-25
Well i still have not gotten it working i have messed with recovory mode and done all that was listed here 
i went back to the 
tali -20 ~/.xsession-errors

and it gave me
(gnome-panel:6123): gtk- warning ** gtk_widget_size_allocate(): attempt to allocate widget with width -12 and hights 24
I/O warning : failed to load external entity "/home/Username/.compiz/session/default0

if that means anything to anyone
help is really apriciated i am extreamly frustrated

---

### Post by HalPomeranz on 2008-05-25
> **xenocide13 said:**
> another thing that i dont get is
before i log in i can shutdown restart
hibernate and all that through options
but once i log in then i try to go to the 
power button or anything like that it locksup

The above behavior makes sense if something in your personal window environment is hosed up.  But I'm not sure what it could be.

One thing worth trying:

1) Log into your windows and try to start Firefox
2) Switch over to the text console and log in
3) Run the command "ps -ef | grep firefox"

I'm curious if Firefox is actually being started or if things lock up before that.  That might help us narrow down what the problem is.

Also, if you haven't had a chance to do so yet, try out that sequence of find and diff commands I gave you earlier.

---

### Post by xenocide13 on 2008-05-26
firefox command

Username 6112 6082 0 22:57 tty1    00:00:00 grep firefox

as for the diff i get no such file or directory on the alst one

---

### Post by HalPomeranz on 2008-05-26
> firefox command

Username 6112 6082 0 22:57 tty1    00:00:00 grep firefox

OK, that means that Firefox isn't actually starting.  So the next question is gnome-panel running?  gnome-panel is the thing that actually makes the Firefox launch button work.  Try the command "ps -ef | grep gnome-panel". 

> as for the diff i get no such file or directory on the alst one

Probably a typo in a command someplace.  The sequence of commands works for me.

> (gnome-panel:6123): gtk- warning ** gtk_widget_size_allocate(): attempt to allocate widget with width -12 and hights 24

This kind of error shouldn't lock up your windows, though.

> I/O warning : failed to load external entity "/home/Username/.compiz/session/default0

This error is pretty typical when you haven't saved a default windowing session to resume.  I don't think it's anything to worry about.

---

### Post by xenocide13 on 2008-05-26
00:00:01 gnome-panel --sm-clientid default1
0 23:33 tty1 00:00:00 grep gnome-panel

i am guessing that it is not running

ill mess with the diff see if i can get it to wokr

---

### Post by HalPomeranz on 2008-05-26
> **xenocide13 said:**
> 00:00:01 gnome-panel --sm-clientid default1
0 23:33 tty1 00:00:00 grep gnome-panel

i am guessing that it is not running

No, it looks like it's running from the output you give above.  The next thing I'd try is doing a system call trace of what happens in the gnome-panel when you click the Firefox button.  This is complicated, and you're going to end up with a big file full of the system call trace output which will then have to be attached to this thread so that I can take a look at it.  

Would you be able to move the data off of the broken machine onto the machine you're using to post to this thread?  If so, I can walk you through the process of setting up the trace and running the test.

> ill mess with the diff see if i can get it to wokr

OK.

---

### Post by xenocide13 on 2008-05-26
no i dont have anyway of transfering it other then the monitor is right next to my laptop atm so i could just type it all out more accuratly then just what looks important haha

and as for the diff i typed in the first to commands it gives no response then i typed in the diff command and still no response from it either 

and i will beleave you on the gnome you know more about it then me 

thanks for all the help

---

### Post by HalPomeranz on 2008-05-26
> **xenocide13 said:**
> no i dont have anyway of transfering it other then the monitor is right next to my laptop atm so i could just type it all out more accuratly then just what looks important haha

Yeah, except that you can expect several thousand lines of output from the trace.  Retyping it into another window just won't work.

> **xenocide13 said:**
> and as for the diff i typed in the first to commands it gives no response then i typed in the diff command and still no response from it either 

Actually, that's good news.  It means that the problem is probably not related to the ownership of files in your homedir.  So one more possible problem eliminated.

But I'm stuck at this point and don't have any other advice to give you.  I'll sleep on it and see if my subconscious comes up with anything.

---

### Post by xenocide13 on 2008-05-26
well i mean i guess i prolly have a flash drive around here somewhere i dont have any idea how that would work if it could at all but thanks for the help and ill keep playing with it see if i can get it to work

---

### Post by xenocide13 on 2008-05-26
Well, i have left it off and unpluged overnight  in hope that it would just somehow fix itself:) but it did not work of course
so i am back to the same issue of nothing working after login
does anyone else have any advice?

---

### Post by xenocide13 on 2008-05-26
Allright so i guess i dont really have that many choices

one idea i had. is there a way to get updates through the ctrl+alt+f1 screen if so i guess i should try that if not
i guess i could always just reinstall ubuntu =/

---

### Post by wootah on 2008-05-26
Have you tried a memory test? Run memtest86 from the grub menu (menu that is displayed at bootup). Perhaps you have bad ram?

You should probably leave this test running for a few hours or so... if you know the memory is 100% good, then I wouldn't bother. However, sometimes memory can go bad--just like that.

Hope that helps!

---

### Post by xenocide13 on 2008-05-26
I dont think it is the ram i had a bad stick but i replaced it but nothing was working when that was bad the computer would randomly restart, stop working, just woldnt co operate 

another reason i dont think it is the ram is it works fine off of a cd 

also i checked already 

=) thanks though

---

### Post by spiderbatdad on 2008-05-26
Read```
dmesg
```

---

### Post by xenocide13 on 2008-05-26
eth0: link up, 100mbps. full-duplex. lpa 0x45e1
bluetooth: core ber 2.11
Net: registered protocol family 31
bluetoth: HCI device and connection manager initialized
bluetooth: HCI socket layer initilized
bluetooth l2cap socet layer initilized
bluetooth: RFCOMMsocket layer initilied
bluetooth: RFCOMM TTY layer initilized
Bluetooth: RFCOMM ver 1.8
[drm] initialized drm 1.1.0 20060810
ACPI PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ16
PCI: Setting latency timer of device 0000:01:00.0 to 64
[drm] initilized radeon 1.28.0 20060524 on minor 0
Net: registered protocol family 17
[drm] setting GART location based on new memory map
[drm] writeback test suceeded in 1 usecd
NET: registred protocol family 10
lo: Disabled Privacy extentions
eth0: no IPv6 routers present

thats what the output of that code is

---

### Post by spiderbatdad on 2008-05-26
That is just the very tail.
Try running it with dmesg | more
or increase the scroll back of your terminal profile so you can see the whole file.

---

### Post by xenocide13 on 2008-05-26
allright how would i increase the scroll back? and could you let me know what your looking for so i dont have to type it all out by any chance?

---

### Post by wootah on 2008-05-26
```
dmesg > ~/dmesg.txt
```
And send the txt file :)

---

### Post by spiderbatdad on 2008-05-26
run this command:
```
dmesg > dmesg.txt
```That will create a text file in your home directory. You are looking for suggestions on how to repair the acpi issues in your boot process. You can right click that file and select create an archive. Upload that archive here with the manage attachment tools if you would like me to look at it.

Also see: [http://ubuntuforums.org/showthread.php?t=808022](http://ubuntuforums.org/showthread.php?t=808022)
Obviously that post isn't your exact problem, but shows how to edit the necessary file based on any suggestions from dmesg.

---

### Post by xenocide13 on 2008-05-26
how would that work if i am running off of two different computers and the one its on is basicly dead haha

---

### Post by signseeker on 2008-05-26
Do you have any other desktop enviroments/window managers installed? ie XFCE etc?

if so, can you log into that without any issues? 

if not, you should consider installing one from the command prompt.

---

### Post by xenocide13 on 2008-05-26
nope i dont

do you know the command to get and install that?

---

### Post by signseeker on 2008-05-26
> **xenocide13 said:**
> nope i dont

do you know the command to get and install that?

try 

sudo apt-get install xfce4

---

### Post by xenocide13 on 2008-05-26
allright that got and installed it but i dont know what to do with it or where it is

---

### Post by signseeker on 2008-05-26
> **xenocide13 said:**
> allright that got and installed it but i dont know what to do with it or where it is

ok. you need to get back to your login screen - (probably gdm) 

once there, you should now be able select a xfce session from one of the menus. 

try logging into xfce.

---

### Post by xenocide13 on 2008-05-26
allright whenever i log in as that it just gives me a peach colored screen no icons folders menu bars nothing and my mouse is there

---

### Post by signseeker on 2008-05-26
What does right-clicking do?

---

### Post by xenocide13 on 2008-05-26
=/ nothing

---

### Post by signseeker on 2008-05-26
Hmm. Would you consider reinstalling?

---

### Post by xenocide13 on 2008-05-26
yea i think i will most likely have to but what bothers me more then that is i have no idea why it crashed it just stoped working in the middle of a session and now nothing works

---

### Post by signseeker on 2008-05-26
I know. Sometimes it's for stupid reasons. Perhaps a corrupt file or something. 

Good luck.

---

### Post by xenocide13 on 2008-05-26
Thanks for the help

looks like i am rebooting tonight or tomorrow 

all help is still apriciated

---

### Post by signseeker on 2008-05-26
Perhaps a minimal install to start off with - and gradually build your system up. That way you may have a better idea of what went wrong (if it happens again)

---

### Post by HalPomeranz on 2008-05-26
Another thought I had was to take your machine to a local Linux User Group in your area.  There may be somebody who can figure out what's wrong with the machine once they're sitting in front of it.

---

### Post by xenocide13 on 2008-05-26
actually i am in a fairly small town i dont know of any groups around here that are like that

i asked my friend who introduced me into ubuntu and everything but he had no ideas at all either so it looks like i am about to start fresh and reinstall now hope to get everything working tonight

---

### Post by perillux on 2008-05-26
I have a somewhat similar problem.  Maybe it can help you.  I was messing with some settings for compiz and now I can't click anything, when I click OK or cancel buttons the button highlights and looks like it's clicked but it doesn't do anything, I can't click the firefox button same as you, or any other panel items, and I couldn't click in any text entry boxes such as google search or URL bar, couldn't open drop down menus nothing.

So, for me it was simply a compiz problem (which I still have by the way, but only when I enable it) I just use metacity now and everythings fine.

Try the command **metacity --replace** but I think that will only work when the X server has already started.  Maybe someone else can help you make a startup script to enter that command.  You could always try ctrl+alt+f1 and then enter the command, but I'm not sure if that will do the trick.

---

### Post by xenocide13 on 2008-05-26
sounds like exactly what was happening to me but i just hit 100% installation kinda late =/ 

thanks though good thought for future reference

---

### Post by perillux on 2008-05-26
just in case our problems are (were) the same, I will let you know if I find a way to repair my compiz so that if your issue arises again maybe it will work for you too.

---

### Post by xenocide13 on 2008-05-26
allright sounds good. 

just reinstalle got back to desktop 102 updates 0_o

next thing to do is get the video card working then get blender back and start over =/ oh well good way to kill time

thanks for allt he help ill let you know if anything on the updates crash

---

### Post by xenocide13 on 2008-05-26
allright got it back up and running
i have two problems 

one openGL rendering
it wont do it lines flash on the screen the usual problems with ATI cards. what i dont get is i have the drivers all up to date got the conf. right i beleave, and it should be working but its not any advice? 

two. sound
i have no sound at all out of my headset and no speakers to test.
if i type alsamixer in my terminal the headphones volume is on 0 but it wont let me turn it up

---

