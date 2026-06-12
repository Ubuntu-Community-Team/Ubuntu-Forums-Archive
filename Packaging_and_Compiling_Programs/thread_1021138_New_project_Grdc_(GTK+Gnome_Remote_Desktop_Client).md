---
title: "New project Grdc (GTK+/Gnome Remote Desktop Client) - will it compiles in Ubuntu?"
date: 2008-12-25
forum: Packaging and Compiling Programs
---

### Post by llyzs on 2008-12-25
[Edited on Oct.20] Grdc's next major release is Remmina 0.7! Please read post #54.

---------------------------

Hi Everyone,

Grdc is a remote desktop client designed for GTK+ and Gnome.

I recently started this new project. But I developed it in Debian and do not have an Ubuntu installation to test this. Could someone help to try it in Ubuntu?

All information is available in this site.

[http://grdc.sourceforge.net](http://grdc.sourceforge.net)

Hope you enjoy and thanks in advance!

Vic

---

### Post by bogus_ub on 2009-01-05
Hi llyzs,
thanks for the nice piece of software. The applet compiles but doesn't work. Grdc compiles and runs without any problems (I've checked only rdp, I don't have any vnc to test it, but this options is shown while connecting). It looks and works very nice. And the rd window in fullscreen is what I was waiting for (this drop down at the upper screen edge). I would suggest to add shortcuts for actions when connected and maybe some small banner with ie. host name in this upper menu indicating the current connection.

Hardy, Gnome 2.20

---

### Post by gregh on 2009-01-05
My findings.
On 8:10 (Intrepid)
Gnome: 2.24.1

Compiles fine and runs fine. Panel applet works ok.

This looks like a potential great piece of work, is there any way to save he configurations. I am asking as I use a few TS sessions to different servers every day so could use this a lot if that was possible.

Keep up the good work !

Greg

---

### Post by marmuta on 2009-01-06
This is really nice. I've tried it on 9.04 Jaunty Alpha2, Gnome 2.25.3 and it works well. 

For the applet I've had to create the link from the readme and kill the panel, x-restart is not necessary.
```
ln -s /usr/local/lib/bonobo/servers/Grdc_Applet.server /usr/lib/bonobo/servers/Grdc_Applet.server
killall gnome-panel

```

I like it already better than tsc and vinagre. 
If it had these things I would switch from vncviewer too:

[LIST]
[*]start with a configered server from command line or launcher, to skip the applet,
which is good for many servers, but just takes extra system resources if 
all you need is one or two servers
[*]specify the initial window mode to not be forced to fullscreen
[*]allow to change colors/compression during a session
[*]clipboard support
[/LIST]
gregh, it saved my session, did you use quick connect?

---

### Post by bogus_ub on 2009-01-06
Now the applet works fine for me too:) I must oversee in the add applet window or creating the link helped.
Once more, nice work!

---

### Post by zekopeko on 2009-01-06
this needs to get in jaunty. i'll file a "needs packaging" report on launchpad ASAP.

EDIT: here it is 

[https://bugs.launchpad.net/ubuntu/+bug/314430](https://bugs.launchpad.net/ubuntu/+bug/314430)

---

### Post by gregh on 2009-01-06
> **marmuta said:**
> 
gregh, it saved my session, did you use quick connect?

I thought after to try the "right click" and found the other menu - DOH!

-Greg

---

### Post by cristianfere on 2009-01-07
llyzs, Congratulations for the project, I think it is taking the right path. Would be nice if there was any place to make feature request. I have some suggestions:
automatic adjustment of the window when working in remote mode outside fullscreen; When you close the main window does not kill the sessions active; Resize in the percentage VNC sessions, similar to what is TightVNC; And somehow encrypt the passwords saved ...

---

### Post by llyzs on 2009-01-07
Thanks guys for your comments!

To marmuta:
  o start with a configered server from command line or launcher: this is a supported feature in the current stable release, although it's no documented... try
    $ grdc -c ~/.grdc/foo.grdc
  o specify the initial window mode to not be forced to fullscreen: I am working on a new feature to save the last view mode, this should be what you need.
  o allow to change colors/compression during a session: Not sure if libvncclient support this, will try that later. But I don't think rdesktop can support
  o clipboard support: VNC currently support this feature; I need to take a look at RDP

To cristianfere:
  o automatic adjustment of the window when working in remote mode outside fullscreen: Do you mean scaling of the window?

Thanks for all your suggestions and now I know I still have lots of things to do :)

If you would like to stand on the edge be sure to check the ChangeLog file in SVN.

---

### Post by cristianfere on 2009-01-08
Yes, I remember that when using VMWare Center at my old job, had a button called auto-fit which was useful to make automatic adjustment in the size of the window. To those who use the remote desktop in a lower resolution, it would be very useful.

---

### Post by llyzs on 2009-01-16
Guys! I just put a new release 0.3.0 on-line! Most of the requested features should be there, but there are still some are left for future work, for example, scaling... this is not easy one but should be possible, probably I will need some time to get it done.

But anyway, hope you enjoy the new version! Any feedback is appreciate.

---

### Post by marmuta on 2009-01-19
Very Cool, I have 0.3.0 running and I'm still amazed how fast it is. You can almost watch video with it over LAN.

> **llyzs said:**
> Thanks guys for your comments!

  o start with a configered server from command line or launcher: this is a supported feature in the current stable release, although it's no documented... try
    $ grdc -c ~/.grdc/foo.grdc
Worked, thank you. I've found that the profiles in ~/.grdc can be renamed too to make them easier recognizable.
 
>  o specify the initial window mode to not be forced to fullscreen: I am working on a new feature to save the last view mode, this should be what you need.
Yes, works great. Only one thing, when switching back from fullscreen to scrolled window mode the window state isn't fully restored, it's always maximized.

>   o allow to change colors/compression during a session: Not sure if libvncclient support this, will try that later. 
Works very well. I couldn't try it over a low bandwith connection yet though. The lowest setting with what looks like 256 colors may still be too high. I used to go down to 16 colors at times which looks ugly but not having to wait for screen refreshes outweighs that by far.
> But I don't think rdesktop can support
rdesktop may not even need this, it's already plenty fast over low bandwith connection.

One more:
The menu entry is hard to distinguish from vinagres "Remote Desktop Viewer" and I prefer to have the menus sorted by application name. What do think about changing it to "Grdc Remote Desktop Client"? Is that too redundant?

I'm going to use it already, at least for the times when I don't need the clipboard too badly.

---

### Post by r57 on 2009-01-20
Hi!

I wish I could test&use Grdc, it looks very promising, but I'm having some difficulties: 

I compiled it successfully, but there wasn't VNC support. So I compiled libvncserver also, then recompiled Grdc and viola, VNC is in the connection combo box. So it is a OK now.

Yesterday I tested VNC and then I runned into another problem, I cannot see the other desktop. VNC looks connected, I can see cursor moving at servers display, but in Grdc, I see only blank window background. Some issue with libvnc maybe? Any ideas, please?

---

### Post by bogus_ub on 2009-01-20
For me all new features work correctly.
But I encountered a bug (possibly, but I don't think it's on my side). Sometime when I enter the active connection window and try to type something in the 'guest' system it doesn't type anything, or when I click on a folder to open it, it opens the properties window (while connecting to Windows XP). It looks like the ALT or CTRL key is pressed all the time. I must hit them a few times to turn it off. But on my local desktop this keys don't seem to be pressed.

---

### Post by druellan on 2009-01-20
Congrats for the project. I also use terminal server quite frequently and some the annoyances you complain are really there and they are... well, annoying :P
Ubuntu Team surely might take a look here to improve usability.

---

### Post by llyzs on 2009-01-22
> **marmuta said:**
> Yes, works great. Only one thing, when switching back from fullscreen to scrolled window mode the window state isn't fully restored, it's always maximized.

Yes I actually have the same problem with you and I will put in an enhancement for it later.
 
> **marmuta said:**
> Works very well. I couldn't try it over a low bandwith connection yet though. The lowest setting with what looks like 256 colors may still be too high. I used to go down to 16 colors at times which looks ugly but not having to wait for screen refreshes outweighs that by far.

Currently it's not really 256 colors, it's actually just picture quality and compress level... I will probably have to take a deeper look into libvncserver later to get more control over color depths.

> **marmuta said:**
> One more:
The menu entry is hard to distinguish from vinagres "Remote Desktop Viewer" and I prefer to have the menus sorted by application name. What do think about changing it to "Grdc Remote Desktop Client"? Is that too redundant?

Actually I would like to change, but I am just not sure if this is the right thing to do, or something the Gnome team wanted... It seems most Gnome apps' menu is just that style.

> **marmuta said:**
> I'm going to use it already, at least for the times when I don't need the clipboard too badly.
In what cases you will have problem using clipboard? I do have problem if I tries to copy/paste string that contains international characters. Are you in the same situation?

---

### Post by bogus_ub on 2009-01-24
> **llyzs said:**
> In what cases you will have problem using clipboard? I do have problem if I tries to copy/paste string that contains international characters. Are you in the same situation?

I'm thinking of being able to copy on local computer and paste on the remote. Or the opposite. That would be really handy.

---

### Post by zekopeko on 2009-01-24
it would be nice to also have a transprent icon for the applet. it has a gray background and it clashes with my panel color.

---

### Post by marmuta on 2009-01-25
> **llyzs said:**
> Actually I would like to change, but I am just not sure if this is the right thing to do, or something the Gnome team wanted... It seems most Gnome apps' menu is just that style.
I'm not sure either. The [Gnome HIG]("http://library.gnome.org/devel/hig-book/stable/desktop-application-menu.html.en#menu-item-names") allow for that though. E.g. The GIMP -> GIMP Image Editor, which is btw. kinda redundant too. I appreciate what gnome is trying to do with things like "Movie Player" but a) this schema breaks if there is more than one Movie Player installed (-> MPlayer Movie Player) and b) I find myself searching the menu for "totem" too many times.


> **llyzs said:**
> In what cases you will have problem using clipboard? I do have problem if I tries to copy/paste string that contains international characters. Are you in the same situation?

My bad, I didn't test that properly. Clipboard does in fact work, yay! Only yes, things like 'ßàáâãäåæç' get mangled. Copying that from server to the client gives '\Uffffffff\Uffffffff\Uffffffff\Uffffffff'.
Doesn't bother me that much personally though since I'm pasting mostly shell commands.

---

### Post by llyzs on 2009-01-25
> **bogus_ub said:**
> For me all new features work correctly.
But I encountered a bug (possibly, but I don't think it's on my side). Sometime when I enter the active connection window and try to type something in the 'guest' system it doesn't type anything, or when I click on a folder to open it, it opens the properties window (while connecting to Windows XP). It looks like the ALT or CTRL key is pressed all the time. I must hit them a few times to turn it off. But on my local desktop this keys don't seem to be pressed.

Well, I believe I fixed this issue today. I can reproduce this issue in the current stable version, by connecting to VNC, then press ctrl-alt-right to switch to the next desktop, then switch back... because when you press ctrl-alt, the key event is sent to the server, but after you press right, focus is lost, then no key release event is going to be sent.

If you don't mind try the latest unstable.
Thanks.

Vic

---

### Post by llyzs on 2009-01-26
> **r57 said:**
> Hi!

I wish I could test&use Grdc, it looks very promising, but I'm having some difficulties: 

I compiled it successfully, but there wasn't VNC support. So I compiled libvncserver also, then recompiled Grdc and viola, VNC is in the connection combo box. So it is a OK now.

Yesterday I tested VNC and then I runned into another problem, I cannot see the other desktop. VNC looks connected, I can see cursor moving at servers display, but in Grdc, I see only blank window background. Some issue with libvnc maybe? Any ideas, please?

Could you tell me what VNC server you are connecting to? I only tested with UltraVNC server, it might be a server compatibility issue.
Thanks.

Vic

---

### Post by bogus_ub on 2009-01-26
> **llyzs said:**
> Well, I believe I fixed this issue today. I can reproduce this issue in the current stable version, by connecting to VNC, then press ctrl-alt-right to switch to the next desktop, then switch back... because when you press ctrl-alt, the key event is sent to the server, but after you press right, focus is lost, then no key release event is going to be sent.

If you don't mind try the latest unstable.
Thanks.

Vic

Still the same. But it looks like you described, with this key events. But I use RDP to a local VirtualBox machine, not VNC. Maybe that the thing that it still doesn't work.

---

### Post by marmuta on 2009-01-26
Vic, that tiny patch below reduces bandwith for the lowest quality setting another little bit. Please have a look. 
I've just seen the new Grdc 0.3.1 and the window gets now restored when switching from fullscreen, thanks a lot!

---

### Post by llyzs on 2009-01-27
> **marmuta said:**
> Vic, that tiny patch below reduces bandwith for the lowest quality setting another little bit. Please have a look. 
I've just seen the new Grdc 0.3.1 and the window gets now restored when switching from fullscreen, thanks a lot!

Yes, the quality actually became even more "poor" and I think this is what Poor quality supposed to be. I committed that change in svn. Thanks.

Vic

---

### Post by edkmho on 2009-02-26
Hey guys,

I am totally newbie to Ubuntu and would like to compile this Grdc. 

First of all, had downloaded the newest version Grdc v0.4.0 and tried to compile and getting some messages :
No package 'glib-2.0' found
No package 'gtk+-2.0' found

What package do i need to install to satisfy above mentioned request.

Please help. 

Thanks.

---

### Post by gregh on 2009-02-26
Welcome to Ubuntu, 

When compiling anything you need to install "dev" packages. For instance to get this to compile you need to install the "glib-2.0-dev" and the "gtk+-2.0-dev"

You may get other messages when you install these, just look for packages ending with "dev" and install them.

Installing "build-essential" will stoip a lot of these messages.

-Greg

---

### Post by edkmho on 2009-02-27
gregh,

Thank you very much for the great advise. I will give it a try. 


Thanks.

---

### Post by cristianfere on 2009-03-01
Hello, for those who want to test Grdc, built packages from last release, 0.4.0. I want to version 8.10, after install is required to login, or restart the X. The packages include the program and applet.
I hope you enjoy!:P:P

---

### Post by Tom_T on 2009-03-08
Thanks for the deb file..

Now it's installed how do I run Grdc ??
Thanks

---

### Post by Tom_T on 2009-03-08
Sorted :)

---

### Post by scaine on 2009-03-08
This is an awesome viewer - full marks so far.  On Jaunty, only version 3 is packaged and there doesn't seem to be a PPA for the latest build, so thanks to cristianfere for the deb.

Without access to version 0.4, the fullscreen only "bug" would have stopped me from using it.  Now, it's a serious contender to replace Vinagre for me.  Couple more tests and I'll be certain.

Thanks to the author and again to cristianfere for the package.

---

### Post by alavarre on 2009-03-17
Vic hi.

Good work, smoothly executing app.

I have started a little project to document it, which I can either post here or send to some email address.

Most of it is pretty self-evident, but I have not yet succeeded in connecting from one SuSE 11.1 machine to another, with either VNC or RDP(oviously the latter, since neither is a windows machine). I DO have vncserver running on the remote machine and *have connected with other clients in the past.

So I may need some hand holding.

Kind regards, Andy

[email]alavarre@gmail.com[/email]

---

### Post by binbash on 2009-03-26
> **cristianfere said:**
> Hello, for those who want to test Grdc, built packages from last release, 0.4.0. I want to version 8.10, after install is required to login, or restart the X. The packages include the program and applet.
I hope you enjoy!:P:P

You have to copy the launcher to /usr/bin to get the applet working :

 sudo cp /opt/grdc/bin/grdc /usr/bin/

---

### Post by cristianfere on 2009-03-26
> **binbash said:**
> You have to copy the launcher to /usr/bin to get the applet working :

 sudo cp /opt/grdc/bin/grdc /usr/bin/

	
	
Did you login/logout? I put a script in /etc/profile.d that adds the /opt/grdc/bin to PATH.

---

### Post by lee_connell on 2009-03-26
Awesome job, keep up the good work, this should replace vinagre and tsclient.  Especially since vinagre did not receive the planned RDP support for gnome 2.26.

---

### Post by binbash on 2009-03-26
> **cristianfere said:**
> Did you login/logout? I put a script in /etc/profile.d that adds the /opt/grdc/bin to PATH.

Nope i didn't logout if you add that to profile.d it is ok

---

### Post by scaine on 2009-04-14
I see that Vic has posted a new version of his GRDC client - 0.5 (as of today, it looks like).  I haven't checked the release notes yet, but if someone feels up to the task of wrapping this awesome viewer into a Deb, or a PPA, I'd be much obliged.

If not, this could well be the first program I'm passionate about to actually try installing myself.  ;)

---

### Post by llyzs on 2009-04-15
Hi scaine,

Please check out the Grdc homepage. I put in a direct-download of the two .deb packages.

This is the first time I made .deb package so please help to test it. Hopefully I didn't mess up anything. :)

Vic

---

### Post by Tom_T on 2009-04-15
What's the difference between the 2 version ??

---

### Post by Tom_T on 2009-04-15
Both installers worked fine for me on Jaunty 9.04.
Thanks :)

---

### Post by scaine on 2009-04-15
Ah superb, Vic - I really appreciate this.  GRDC is a cracking piece of work.  I'll check it out tonight.  For future reference, do you want any bugs reported officially and if so, how?

---

### Post by llyzs on 2009-04-15
To Tom_T: It's good to hear the installer works in 9.04!
To scaine: If you want to report bugs, you can just go to the sourceforge.net project page and go to the "Bug Report" tracker.

Vic

---

### Post by scaine on 2009-04-16
Those debs work perfectly here too, Vic.  Thanks again.

Neil.

---

### Post by esofron on 2009-05-18
Hello,

this is an amazing tool.

Is there any deb package for Jaunty amd64 for version 0.5.0 ?

Thanks,

Elias

---

### Post by Neequu on 2009-06-01
> **esofron said:**
> Hello,

this is an amazing tool.

Is there any deb package for Jaunty amd64 for version 0.5.0 ?

Thanks,

Elias

I second this one! amd64 package.

---

### Post by racecarpete on 2009-06-02
I just found this program and love it. Can I make a feature request and if so where do you want it here or the sourceforge page?

---

### Post by llyzs on 2009-06-18
You are welcome to submit feature requests directly in sourceforge. But right now I am in beta testing the next release 0.6. So future requests will be probably consider in the next next release :)

---

### Post by cristianfere on 2009-07-07
New version (0.6.0) now available on sourceforge.net with packages for i386 and amd64.

GRDC is an amazing program!!!

---

### Post by ktp on 2009-07-09
First, GRDC is great...wish/hope it becomes default in Ubuntu and replace tsclient and Vinagre.  GRDC has made be able to use RDP and VNC again...performance is great.  So thanks for the hard work.

Now I just installed the 0.6 in Jaunty and was playing around with multi-screen.  I was trying to move the grdc window onto second screen and maximize but it would always want to goto primary screen.  I don't know if this is a bug or not, but all other apps maximize on the screen the window is.  Minor issue but wondering if anyone else seen this.

---

### Post by DariusZelvys on 2009-07-30
Hi, maybe here i'll find my answers. 
How does RDP copies data? not sure if it's RDP related, but still i'm asking for help


 i'm in desperate need of help. Imagine 2 networks. connected through the vpn connection. 192.168.111.254 and 192.168.110.254. There is one win2003 server on 111.254 network. Every user on those 2 networks connects to that server through RDP and copies data. Now's the problem. If a user with ubuntu desktop from network connects to 111.254 networks and copies more than 200 lines from excel file for example, paste function in OpenOffice fails. If it's 100 lines, then it works like a charm. If the same computer does this operation on 111.254 network, it works flawlessly with any amount of data. Even with 50000 lines. The same computer goes back to 110.254 network and the copy size drops to 200 maximum. I tried to recplicate the same situation with winxp computer, and everything is working good even with very large amount of data. I can copy 50000 lines using winxp on network 110.254 from network 111.254, but can't do the same operation using ubuntu system. Any ideas?

---

### Post by cjnucette on 2009-08-05
I just found out about this app and i think is great, but i have a problem with the local printers, is there an option to be able to see them on the remote windows system?

---

### Post by scaine on 2009-08-07
Citrix (or xenapp or whatever it's called now) has a method which maps local printers to the remote machine, but there's nothing like that for certain in VNC and I'm fairly sure it's beyond RDP too.  I mean, Citrix isn't even anything really like VNC/RDP - Citrix is about mutliple clients logging in for a desktop experience from a remote location, while VNC/RDP is about controlling a server/pc desktop from a remote location.  It sounds similar, sure, but if need to be printing documents on the remote side using a local printer, then you're possibly using the wrong tool.

---

### Post by NTolerance on 2009-08-08
Wow, this program is amazing.  I've been suffering with Vinagre for far too long.  I've also been using Gnome-RDP, which is a fine program, but GRDC puts the best of all worlds together.  The panel applet is a nice touch.  

I appreciate the work going into packaging this program for Ubuntu.  It's a great thing to be able to go to the project homepage, download a deb and install it.  

Thanks to llyzs and all other contributors for all your hard work and good decisions during the design process.  I fully propose that this be the default in all future Ubuntu releases.

---

### Post by llyzs on 2009-10-20
Oh, it's been really long haven't post here :)

I published a beta version of Remmina - the new project name of Grdc, recently. And I also built it in my PPA for Karmic, so if you already upgrade to Karmic you should be able to use it easily.

The program is consider stable already - just need to wait for the final libssh 0.4 release. Anyway I already built it into PPA as well.

New features including sound/printer RDP options, VNC TLS/VeNCrypt/MSLogon extensions, XDMCP protocol, Tabbed interface, new Tango design(Thanks for Martin Lattner!), etc. It should really be a much better release than grdc 0.6.

Please feel free to try and feedback if you find any issue.

[http://remmina.sourceforge.net](http://remmina.sourceforge.net)

Vic

---

### Post by NTolerance on 2009-10-21
> **llyzs said:**
> Oh, it's been really long haven't post here :)

I published a beta version of Remmina - the new project name of Grdc, recently. And I also built it in my PPA for Karmic, so if you already upgrade to Karmic you should be able to use it easily.

The program is consider stable already - just need to wait for the final libssh 0.4 release. Anyway I already built it into PPA as well.

New features including sound/printer RDP options, VNC TLS/VeNCrypt/MSLogon extensions, XDMCP protocol, Tabbed interface, new Tango design(Thanks for Martin Lattner!), etc. It should really be a much better release than grdc 0.6.

Please feel free to try and feedback if you find any issue.

[http://remmina.sourceforge.net](http://remmina.sourceforge.net)

Vic

GRDC 0.6 was an amazing version in its own right, which I might add is in the Karmic default repositories.  I tried out Kubuntu for a little while and this was the app I missed the most when running KDE.  KRDC doesn't even come close.

At any rate, thanks for the new version and I'll surely be using your PPA when I install Karmic.  :)

---

### Post by Joe_Bishop on 2009-10-22
> **llyzs said:**
> Oh, it's been really long haven't post here :)

I published a beta version of Remmina - the new project name of Grdc, recently. And I also built it in my PPA for Karmic, so if you already upgrade to Karmic you should be able to use it easily.

The program is consider stable already - just need to wait for the final libssh 0.4 release. Anyway I already built it into PPA as well.

New features including sound/printer RDP options, VNC TLS/VeNCrypt/MSLogon extensions, XDMCP protocol, Tabbed interface, new Tango design(Thanks for Martin Lattner!), etc. It should really be a much better release than grdc 0.6.

Please feel free to try and feedback if you find any issue.

[http://remmina.sourceforge.net](http://remmina.sourceforge.net)

Vic

1) Any reason of sftp support? I prefer gvfs for this.
2) Hardcoded tango icons look really ugly. GRDC's ones, using current icon theme, look way better.

So, I think your project has come to the end, you better switch to someone else. BTW, I've rolled back to the grdc from remmina, because it has everything I need and looks better.

---

### Post by hugmenot on 2009-10-22
Remmina looks yummy!

Two small things I noticed: It doesn&#8216;t really quit, the process lingers connected to the shell when I close it. Second, it doesn&#8216;t remember the window size.

Now, the whole grail would of course be to add NX protocol support, but I suppose that would be more difficult.

---

### Post by llyzs on 2009-10-22
> **hugmenot said:**
> Remmina looks yummy!

Two small things I noticed: It doesn‘t really quit, the process lingers connected to the shell when I close it. 

Oh actually this is kind-of "feature": it's now a libunique app, so it will use an internal window counter to track if all windows are closed before quiting the process. When the counter becomes zero, it won't quit immediately, but have 10 seconds delay, because a new window could open just after the last window closes.

If you leave it in the shell for 10 seconds after you close all window it should quit. Maybe I should decrease the delay to something like 5 seconds, or less? Anyway this shouldn't be a problem for normal user who will launch it through the menu or applet.

> Second, it doesn‘t remember the window size.

Could you tell me in which case it doesn't remember the window size? Maybe it's quick connect? The main window and saved connections should remember its size. Moreover, if a connection is opened in an existing window as a tab, it will follow existing window size and "forget" its original saved size.

> Now, the whole grail would of course be to add NX protocol support, but I suppose that would be more difficult.

I already did a lot of work trying to add NX support, but unfortunately I still can't figure out a way to embed the NX window (like rdesktop and Xephyr do). Maybe I will have to hack deeper into the NX library but yes, this is more difficult.

Thanks.

Vic

---

### Post by hugmenot on 2009-10-22
> **llyzs said:**
> Oh actually this is kind-of "feature": it's now a libunique app, so it will use an internal window counter to track if all windows are closed before quiting the process. When the counter becomes zero, it won't quit immediately, but have 10 seconds delay, because a new window could open just after the last window closes.

If you leave it in the shell for 10 seconds after you close all window it should quit. Maybe I should decrease the delay to something like 5 seconds, or less? Anyway this shouldn't be a problem for normal user who will launch it through the menu or applet.
No, that&#8217;s cool. I thought only the windows was destroyed and the process would keep running. I wasn&#8217;t aware of libuniques existence.
> Could you tell me in which case it doesn't remember the window size? Maybe it's quick connect? The main window and saved connections should remember its size. Moreover, if a connection is opened in an existing window as a tab, it will follow existing window size and "forget" its original saved size.
I mean the main window.
> I already did a lot of work trying to add NX support, but unfortunately I still can't figure out a way to embed the NX window (like rdesktop and Xephyr do). Maybe I will have to hack deeper into the NX library but yes, this is more difficult.
Before I asked this question I did a bit of googling. Did you look at the older (maybe now abandoned) code in nxcl and nxlaunch?

---

### Post by llyzs on 2009-10-25
> **hugmenot said:**
> I mean the main window.

For me the main window correctly remember the size. I am on Xubuntu karmic and Debian Squeeze. One possibility that it won't remember its size is that, you might kill the process through Ctrl+C in the terminal, rather than clicking the close button "X" of the window. But of course I am not sure if you actually hit another new bug... the program has the codes handling this thing.

> Before I asked this question I did a bit of googling. Did you look at the older (maybe now abandoned) code in nxcl and nxlaunch?

yes. and nxcl is in C++ and its implementation is ugly... Actually I did quite a lot research and trial some time ago already. I even already wrote a program in C implemented the NX session protocol, using native libssh (not the annoying nxssh fork!). So I am actually quite close. :)

---

### Post by hugmenot on 2009-10-25
Whether closing the window, or quitting with ^Q, it reverts to the original size. Might be because I use the gnome2-globalmenu applet, which relocates the window menus of GTK windows to the top panel.

I tried editing remmina.pref, no dice (what&#8217;s the difference between main_(width|height) and window_(width|height)?).
And when I removed the config file it didn&#8217;t store anything but secret= upon closing the window.

No clue, but it&#8217;s not that important.

> **llyzs said:**
> So I am actually quite close. :)

Yay! This will become the egg of Columbus in remote desktop clients.

---

### Post by llyzs on 2009-11-01
Hi,

I feel very lucky today! I got EVERYTHING SOLVED in order to implement a clean NX support in Remmina!

1. No nxssh needed. Only libssh + nxproxy (the standard one) + Xephyr.
2. Both encrypted and not-encrypted session are supported by libssh
3. Parent window embedding are supported by Xephyr.

I will post a detailed technical post in Remmina forum soon.

So version 0.8 will guarantee to come with NX support.

Vic

---

### Post by hugmenot on 2009-11-02
Do you develop on sf.net svn, or do you have another repo somewhere? I wanted to have a look at this work, but svn trunk is still at 27th of October.

Exciting news! Do you have a roadmap?

Lastly, I think the three buttons with zoom and window controls on the left of the toolbar are too confusing. They say «Toggle ...» but don&#8217;t toggle, you have to click the right button to go full-screen, and the left button to leave full-screen. And then click the left button again to get rid of scrollbars. And the icons and function change on the left button.

There should be a real full-screen toggle. And the scroll, or fit, or scale behavior should be revisited.

---

### Post by NTolerance on 2009-11-02
Will the new NX support work with Nomachine NX?  I have always used it because it's easy to install.  The last time I tried FreeNX you had to muck around with a lot of XWindows settings that I'd prefer not to touch.

---

### Post by hugmenot on 2009-11-02
On the server side Google&#8217;s neatx project improves upon freenx a lot.

---

### Post by llyzs on 2009-11-03
@hugmenot

I just wrote a test program in my laptop to prove the concept and it's not a ready-to-commit code. But soon I will branch 0.7 and start actually implement this in 0.8 trunk, so just be patient. :) If you are interested you see read this post:

[http://sourceforge.net/apps/phpbb/remmina/viewtopic.php?f=2&t=5](http://sourceforge.net/apps/phpbb/remmina/viewtopic.php?f=2&t=5)

Regarding the buttons, (1)  you are right, they are not really toggle... Remmina has 3 different view modes so they can't be toggle. Probably changing the word to "Switch to ..." is more precise. (2) the left buttons are actually two different buttons - one is Switch to scrolled window mode, the other is "Auto resize window". Maybe I should always show both buttons? But only one of them will be enabled.

@NTolerance

I used NoMachine NX server to test my work, just for the same reason. :) So I probably need someone to test it with FreeNX and neatx later when I commit the NX implementation.

Thanks,

Vic

---

### Post by llyzs on 2009-11-03
> **Joe_Bishop said:**
> 1) Any reason of sftp support? I prefer gvfs for this.
2) Hardcoded tango icons look really ugly. GRDC's ones, using current icon theme, look way better.


1) I know most people won't use it and I actually have plan to support 3party sftp client. But I don't think it will hurt to provide a basic implementation.
2) All remmina icons are theme-able. They are installed as a default fallback theme "hicolor" under /usr/share/remmina/icons, just as the same way with most other packages, for example, /usr/share/gnome-games/icons. If you don't like those icons, you can simply make a theme and override the default ones.

Most people complains about Grdc's icons, so it's more of personal preferences. But I think Remmina's way should be better, it following Tango and freedesktop guidelines, better describe the functionality, and replaceable by themes.

Vic

---

