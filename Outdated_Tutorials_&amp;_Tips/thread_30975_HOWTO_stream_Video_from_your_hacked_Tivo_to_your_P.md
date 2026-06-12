---
title: "HOWTO: stream Video from your hacked Tivo to your PC."
date: 2005-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by gunnyman on 2005-05-01
Hacking Tivo is another hobby of mine and the fine folks who reside at dealdatabase.com have come up  with a way to stream Tivo'ed shows to your LINUX box.  This  is a long time coming since streaming to windows has been around for a long time.
Got you tivo owners attention? Good!

First you need to have a hacked Tivo (duh).
That hacked Tivo needs to be running Vserver and  if your tivo has been hacked, it likely already has that installed.
Second  Install VLC from Ubuntu's repositories.
3rd head over to 

[Sourceforge](http://sourceforge.net/project/showfiles.php?group_id=134740&package_id=149348) 
and get two files:
[http://prdownloads.sourceforge.net/tivo-vlc/vlc-ty-i686-linux-r42.tar.bz2?download](http://prdownloads.sourceforge.net/tivo-vlc/vlc-ty-i686-linux-r42.tar.bz2?download)
[http://prdownloads.sourceforge.net/tivo-vlc/vlc-vstream-i686linux-r37.tar.bz2?download](http://prdownloads.sourceforge.net/tivo-vlc/vlc-vstream-i686linux-r37.tar.bz2?download)
unzip these to /usr/lib/vlc/demux you will need to sudo to access this directory.

now for the fun part
start vlc
file-open-network stream
in the box type:
tivo://tivoipaddress/plist

this generates a playlist of all the shows on the Tivo.
go to view playlist to see it
double click on a show.
Enjoy.
This works great over wireless connections too!

---

### Post by Dromio on 2005-05-02
I gave it a shot, but VLC doesn't seem to be connecting to my tivo's vserver.  Tytools under wine does, but not VLC.  vserver just sits there, waiting for a connection.

---

### Post by gunnyman on 2005-05-02
don't know what to tell you Dromio, works flawlessly for me.
Tytools uses tserver though not vserver.
Make sure vserver is running.

---

### Post by Dromio on 2005-05-02
[QUOTE=gunnyman]don't know what to tell you Dromio, works flawlessly for me.
Tytools uses tserver though not vserver.
Make sure vserver is running.[/QUOTE]
 It looks to me like both of the files you linked unzip to make libty_plugin.so, just different revisions.  Maybe there's a different link for one of the files?

---

### Post by gunnyman on 2005-05-02
oh man you're right
[http://prdownloads.sourceforge.net/tivo-vlc/vlc-vstream-i686linux-r37.tar.bz2?download](http://prdownloads.sourceforge.net/tivo-vlc/vlc-vstream-i686linux-r37.tar.bz2?download)
gets you the vstreamer module for VLC
so sorry about that.
I fixed it in my original post

---

### Post by Dromio on 2005-05-02
[QUOTE=gunnyman]oh man you're right
[http://prdownloads.sourceforge.net/tivo-vlc/vlc-vstream-i686linux-r37.tar.bz2?download](http://prdownloads.sourceforge.net/tivo-vlc/vlc-vstream-i686linux-r37.tar.bz2?download)
gets you the vstreamer module for VLC
so sorry about that.
I fixed it in my original post[/QUOTE]
 Much better.  I can get the plist now :)  I can't test it for real until I get home though.

Thanks.  I'd tried to do this once before some time ago, but couldn't figure out where to put the vlc libraries.

---

### Post by gunnyman on 2005-05-02
yeah me too, the new vstreamer module is very sweet too, the old one would segfault vlc 10 minutes into a show.

---

### Post by Dromio on 2005-05-02
Well, it's unwatchable with my AirNET (802.11b) tivo.  Just not enough bandwidth to support the stream.  Then again, I record everything in best quality-- that may have something to do with it.

Oh well, it's a very nice hack.  Makes me wish I'd worked harder and wired it with ethernet instead of taking the easy way out.

---

### Post by gunnyman on 2005-05-02
works great with my Directivo :) 
I guess since the stream is compressed  more on one of those I don't have any hiccups.

---

### Post by wmcbrine on 2005-05-04
There's also a patch for MPlayer to support this. (The streaming, that is -- the demuxing of Tivo streams has already made it into mainstream MPlayer.)

[http://tivo-mplayer.sourceforge.net/](http://tivo-mplayer.sourceforge.net/)

I'm not certain if it works with the latest versions of MPlayer. (I just keep a separate "mplayer-tivo" binary around.)

---

### Post by gunnyman on 2005-05-04
Yeah I compiled Tivo Mplayer as well, but it was always so choppy ( probably due to my wireless and the fact that the asx wrapper is there.  This method is raw ty file decoded by vlc.
Me likey.

---

### Post by shawnT on 2005-05-11
In the first post, you say to install vlc from the repositories. When they are select it refers you to  wxvlc. Can I use either one or do I need the vlc.

Thanks Shawn

---

### Post by gunnyman on 2005-05-11
I didn't have that problem.
I am using the universe, multiverse, and marrilat repositories though.

---

### Post by shawnT on 2005-05-11
[QUOTE=gunnyman]I didn't have that problem.
I am using the universe, multiverse, and marrilat repositories though.[/QUOTE]
 my bad. I didn't scroll down enough on the package manager screen.

Thanks for the quick reply.
Shawn

---

### Post by momo66 on 2005-05-27
[QUOTE=gunnyman]!

First you need to have a hacked Tivo (duh).
That hacked Tivo needs to be running Vserver and  if your tivo has been hacked, it likely already has that installed.
Second  Install VLC from Ubuntu's repositories.
3rd head over to 

[Sourceforge](http://sourceforge.net/project/showfiles.php?group_id=134740&package_id=149348) 
and get two files:
[http://prdownloads.sourceforge.net/tivo-vlc/vlc-ty-i686-linux-r42.tar.bz2?download](http://prdownloads.sourceforge.net/tivo-vlc/vlc-ty-i686-linux-r42.tar.bz2?download)
[http://prdownloads.sourceforge.net/tivo-vlc/vlc-vstream-i686linux-r37.tar.bz2?download](http://prdownloads.sourceforge.net/tivo-vlc/vlc-vstream-i686linux-r37.tar.bz2?download)
unzip these to /usr/lib/vlc/demux you will need to sudo to access this directory.

[/QUOTE]

This might be a dumb question but do I install these files on the Tivo or my Ubuntu box?

Mike

---

### Post by iitywygms on 2005-10-25
I am sure I have installed the plugins correctly but when I try to connect with vlc I get a message "no suitable module found"

any ideas.

---

### Post by iitywygms on 2005-10-29
bump

---

### Post by blkno1 on 2005-11-30
Hmmm since I upgraded to breezy vlc no longer opens my playlist.  vserver is up and running on the tivo box ok.  Any ideas.  

-bk

---

### Post by artships on 2005-12-03
The tivo modules are for VLC 0.8.1 and won't work with Breezy's VLC 0.8.4.  According to the tivo vlc site, you'll need to install all the vlc source, the tivo modules source, then recompile the modules.  Lemme know when you do so I can beg the modules off of you.

Edit:  0.8.4 binaries posted in Dealdatabase:
[http://dealdatabase.com/forum/showthread.php?p=242585#post242585](http://dealdatabase.com/forum/showthread.php?p=242585#post242585)

Alas, they don't work for me.  Try'em?

---

### Post by plewisfdx on 2005-12-17
[QUOTE=iitywygms]I am sure I have installed the plugins correctly but when I try to connect with vlc I get a message "no suitable module found"

any ideas.[/QUOTE]


I got this same message.  I googled it, and although I didn't find the answer I saw several references to typing <tivoaddress>/llist (instead of plist).  I tried this, and it worked flawlessly.  The output of this was a list with shows and numbers.  I replaced the "llist" with the number and it streamed the show.

---

### Post by plewisfdx on 2005-12-17
[QUOTE=momo66]This might be a dumb question but do I install these files on the Tivo or my Ubuntu box?

Mike[/QUOTE]


These files are codecs for your linux vlc (client) to read the stream from the tivo.  The only program on the tivo that is required is vserver.  So, to answer your question, you would install these on Ubuntu, not the tivo.

---

### Post by morphx on 2007-06-29
In case anyone is interested, here's a link to a version of mplayer with included support to play streams directly off your Tivo. This binary was compiled from the latest CVS sources under Ubuntu 7.04

[http://software.xfx.net/ftp/mplayer_dev-SVN-r23694-4.1.2.tar.gz]("http://software.xfx.net/ftp/mplayer_dev-SVN-r23694-4.1.2.tar.gz")

---

### Post by wusl.au on 2008-05-27
Hi,  what's the chance that there's a version of Mplayer available for Hardy (8.04) with tivo streaming support?  

The one that's packaged with Mythbuntu 8.04 does not do this.

If I can get that going I'll be one step closer to having Tivo support from within Mythbuntu :)

TIA
Wusl.au

---

