---
title: "HOW-TO: De-uglify aMSN."
date: 2005-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by neuschnee on 2005-10-31
First I should give credit to [this guy]("http://gnome-look.org/content/show.php?content=28608") for the icons used in this skin. I didn't make any of them. Some icons/colors/sounds I took from real MSN 7.5, but most I used from the (Gaim) Grystal theme.

With this (poorly written) guide, you can change [this]("http://amsn.sourceforge.net/shots/CVS_amsn_shot.jpg") into [this]("http://img256.imageshack.us/img256/5505/amsngrystal4se.png"). I need aMSN for webcam but I was sick of how ugly it was by default.. so I fixed it with a new skin and anti-aliasing through latest Tcl/Tk.

**1. Install Tcl/Tk 8.5 from CVS.** [Here is a post]("http://www.ubuntuforums.org/showthread.php?t=35358") which describes the process a bit.

**Get everything you need to build Tcl/Tk:**
```
sudo apt-get build-dep tcl8.4 tk8.4
sudo apt-get install libxft-dev
```
**To get CVS Tcl:**
```

cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl login 
<hit enter>
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl co -P tcl
```
**To get CVS Tk:**
```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tktoolkit login 
<hit enter>
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tktoolkit co -P tk
```
**Compile Tcl this way (same way as the tcl8.4 package, but for 8.5):**
```
cd tcl/unix
./configure --prefix=/usr/local --includedir=/usr/local/include/tcl8.5 --enable-shared --enable-threads --enable-64bit --mandir=/usr/local/share/man --enable-man-symlinks --enable-man-compression=gzip && make CFLAGS="-g -O2 -D_REENTRANT"
sudo make install
```
**Compile Tk this way (ditto):**
```
cd tk/unix
./configure --prefix=/usr/local --includedir=/usr/local/include/tcl8.5 --with-tcl=/usr/local/lib --enable-shared --enable-threads --enable-64bit --enable-man-symlinks --enable-man-compression=gzip --enable-xft && make CFLAGS="-g -O2 -D_REENTRANT"
sudo make install
```
**2. Follow this guide to install CVS aMSN***: [http://www.ubuntuforums.org/showthread.php?t=75276](http://www.ubuntuforums.org/showthread.php?t=75276)

*Except, add "--with-tcl=/usr/local/lib --with-tk=/usr/local/lib" to ./configure, like this:

```
./configure --with-tcl=/usr/local/lib --with-tk=/usr/local/lib *(whateverotheroptions)*
```
**3. Load aMSN this way:**
```
/usr/local/bin/wish8.5 /usr/local/share/amsn/amsn
```
I made a one-liner script for this to be lazy, so I can just type "fakeamsn".

```
cat > ~/bin/fakeamsn
#!/bin/sh
/usr/local/bin/wish8.5 /usr/local/share/amsn/amsn
*<Control-D>*
chmod 700 ~/bin/fakeamsn
```
**4. Use my skin.** [Download here]("http://savefile.com/files.php?fid=3456283"). Put in ~/.amsn/skins, select it in aMSN and restart aMSN.

**5. Config aMSN a bit.**
**a)** Set fonts. Tools: Preferences: Appearance tab: Change font button. I use "Bitstream Versa Sans" at size 9. In the Personal tab: My message text, I use "Bitsream Vera Sans Mono".. but it's up to you. (these are the fonts I use in the screenshot)
**b)** I put tabs off (up to you though). Tools: Preferences: Session Tab : My Messaging Interface : Select how to handle multiple message windows: Normal windows without tabs.
**c)** I set some default applications. Go Tools: Preferences: Others tab. And set...
- Browser = "firefox $url" *(could also be "sensible-browser", but this is how I do it)*
- File Manager = "nautilus $location" *(or konqueror $location, I suppose)*
- Open file command: "gnome-open $file"
- Received Files folder: "/home/myname/Desktop" *(or wherever)*
**d)** Now go to the advanced tab.
- Uncheck "Show aMSN's banner"
- Check "Ignore remote users fonts in chats.." *(my preference, up to you)*
- Check "No space between groups"
- Check "Remove empty groups from the contact list"
- Set "Offset the position of the notification pop-up" to x=0 y=26 if you have a 26pixel bottom panel/bar. If you don't, make it 0,0. If it's bigger.. make it bigger (eg. x=0 y=48).

**6. Open a message window to someone and go View: Style: Customized style.**

Set it to:
[color=red]"$tstamp $nick says: $newline   "[/color]
*(without the quotes, and 4 spaces after $newline)*

Click OK.

**7. Done.** :>

This process has a lot of room for error with getting/compiling amsn/tcl/tk, so don't blame me if it doesn't work. I will help where I can, but it won't be a lot. So take this guide as-is, and improve upon it if you'd like. Reading other posts in this thread would probably be a good idea.

---

### Post by bored2k on 2005-10-31
From the other thread:[QUOTE=bored2k]I have made **x86** ubuntu packages for the latest TCL and TK:
[LIST]
[*][http://rapidshare.de/files/6632929/tk8.5a3_8.5a3-1_i386.deb.html](http://rapidshare.de/files/6632929/tk8.5a3_8.5a3-1_i386.deb.html)
[*][http://rapidshare.de/files/6633036/tcl8.5a3_8.5a3-1_i386.deb.html](http://rapidshare.de/files/6633036/tcl8.5a3_8.5a3-1_i386.deb.html)
[/LIST]
[QUOTE=joakim2]Go into your aMSN directory and configure and make it like so: ./configure --with-tcl=/usr/local/tcl/lib --with-tk=/usr/local/tcl/lib && make[/QUOTE][/QUOTE]

---

### Post by Neo40 on 2005-11-01
Thanks for your how-to!! aMSN looks much more beautiful now! :)

---

### Post by neuschnee on 2005-11-01
I also reccomend this:

[http://gnome-look.org/content/show.php?content=27494](http://gnome-look.org/content/show.php?content=27494)

It replaces some of the file dialogues with GNOME/KDE widget dialogues.

---

### Post by steil on 2005-11-01
Nice how-to

---

### Post by Blackie_Chan on 2005-11-01
I've followed all the steps, and still the font in aMSN still looks ugly. My 'Bitsream Vera Sans Mono' size 8 or 9 looks nothing like the font in gedit or other applications. Anyone have suggestions on how I can change my font in aMSN? 

If it'll help, my encoding is set to 'Automatic'. My fonts looks like they have been squished, they are shorter and wider than the normal.

---

### Post by neuschnee on 2005-11-01
[QUOTE=Blackie_Chan]I've followed all the steps, and still the font in aMSN still looks ugly. My 'Bitsream Vera Sans Mono' size 8 or 9 looks nothing like the font in gedit or other applications. Anyone have suggestions on how I can change my font in aMSN? 

If it'll help, my encoding is set to 'Automatic'. My fonts looks like they have been squished, they are shorter and wider than the normal.[/QUOTE]
It sounds like Xft isn't working. You need to compile Tk8.5 with --enable-xft (I'm not sure if the .deb linked here has xft enabled or not).

---

### Post by steil on 2005-11-02
Doing the build-dep does not install libxft-dev. In order to get the anti-aliased fonts use apt-get or synaptic to install libxft-dev before building TK. 

apt-get install libxft-dev

(Please note, if you have already installed AMSN all you have to do is recompile TK)

Also when compiling TK I had to change --with-tcl=/usr/local/lib/tcl8.5 to --with-tcl=/usr/local/lib.

---

### Post by Spider-One on 2005-11-02
Took a few tries with the whole TCL/TK thing. But I had to change the dir to /usr/local/lib when doing ./configure for ~/msn and ./configure in ~/tk/unix

---

### Post by neuschnee on 2005-11-02
Fixed some things (/usr/local/lib and made a mention of installing libxft-dev).

I also have some things to alter in the skin.. maybe I'll get around to it today.

---

### Post by Blackie_Chan on 2005-11-04
Is it just me, or the tk code that you download using cvs broken? 

I need to recompile tk (because I installed libxft-dev, after running going to all the steps), but each time I try run **make CFLAGS="-g -O2 -D_REENTRANT"** I get a whole bunch of errors in *.h and *.c files.

====

I've fixed the problem. Apparently you need to tcl directory inorder to recompile tk.

---

### Post by i3dmaster on 2005-11-04
Very nice! Thanks so much!!!

---

### Post by LaSSarD on 2005-11-11
P-E-R-F-E-C-T ! you're the man :P

---

### Post by vendetta red on 2005-11-11
After following the steps, I run:

```
/usr/local/bin/wish8.5 /usr/local/share/amsn/amsn
```

And I get:

```
Error in startup script: couldn't read file "/usr/local/share/amsn/amsn": no such file or directory
```

Any idea why?

---

### Post by dixonstalbert on 2005-11-12
Don't you hate it when you post a problem and the next post is somebody else with another problem? sorry Mr.  poster just above me....

Having lots of trouble with this; :confused: 


first error message comes when try to get imlib libraries:

E: Couldn't find package imlib11-dev




next error message is when I run amsn-installer script:


/home/melissac/amsn-installer: line 84: [: too many arguments
/home/melissac/amsn-installer: line 92: [: too many arguments

next error with running ./configure && make

./configure: line 3166: /usr/lib/tkConfig.sh: No such file or directory


any thoughts on how I can clean up this mess and start over?

---

### Post by Juippisi on 2005-11-12
Thanks for gathering this up! I was using only amsn-cvs, but with tk-cvs and tcl-cvs amsn looks much more beatifuler now.

Sweet.

---

### Post by Juippisi on 2005-11-12
[QUOTE=vendetta red]After following the steps, I run:

```
/usr/local/bin/wish8.5 /usr/local/share/amsn/amsn
```

And I get:

```
Error in startup script: couldn't read file "/usr/local/share/amsn/amsn": no such file or directory
```

Any idea why?[/QUOTE]

Because it doesn't exist? :-). Where did you build that amsn? For example, I did it on my /cvs and my startup script looks like: 
```
#!/bin/bash
/usr/local/bin/wish8.5 /cvs/msn/amsn
```

---

### Post by Juippisi on 2005-11-12
[QUOTE=dixonstalbert]Don't you hate it when you post a problem and the next post is somebody else with another problem? sorry Mr.  poster just above me....

Having lots of trouble with this; :confused: 


first error message comes when try to get imlib libraries:

E: Couldn't find package imlib11-dev




next error message is when I run amsn-installer script:


/home/melissac/amsn-installer: line 84: [: too many arguments
/home/melissac/amsn-installer: line 92: [: too many arguments

next error with running ./configure && make

./configure: line 3166: /usr/lib/tkConfig.sh: No such file or directory


any thoughts on how I can clean up this mess and start over?[/QUOTE]

Umm, did you change anything on that script? Like the working-directory? Because I did and got the same error. This is how I did it:

./amsn-installer
<errors here>
tar -xzvf amsn_cvs.tar.gz
cd msn
./configure --with-tcl=/usr/local/lib --with-tk=/usr/local/lib && make

and it compiled just fine :-).

And what it comes to imlib11-dev... that package is on Universe-repo. Add
```
deb http://se.archive.ubuntu.com/ubuntu breezy universe
deb-src http://se.archive.ubuntu.com/ubuntu breezy universe
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```
to your /etc/apt/sources.list -file. Remember to change that "se." to matching your countrycode, like "us.".

(Hope I understood your problem rightly)

---

### Post by LaSSarD on 2005-11-12
[QUOTE=vendetta red]After following the steps, I run:

```
/usr/local/bin/wish8.5 /usr/local/share/amsn/amsn
```

And I get:

```
Error in startup script: couldn't read file "/usr/local/share/amsn/amsn": no such file or directory
```

Any idea why?[/QUOTE]
that command was just an example, probably you installed amsn on ~/msn/amsn so you should replace /usr/local/share/amsn/amsn with it.

---

### Post by dixonstalbert on 2005-11-13
thanks juippisi!
I had just installed Breezy on new computer and forgot to add other repositories in sources.list - amsn installed without a problem now.
thanks again

---

### Post by ykpaiha on 2005-11-13
Sorry I mistaken the post not for you

---

### Post by vendetta red on 2005-11-14
Got it working. Thanks for your help.

---

### Post by galotzas on 2005-11-15
root@galotzas:~/tcl/unix# ~/amsn-installer

Don't run this script as root !! ;)

root@galotzas:~/tcl/unix# su galotzas
galotzas@galotzas:/root/tcl/unix$ ~/amsn-installer
bash: /home/galotzas/amsn-installer: No such file or directory


:(

---

### Post by dj_thom on 2005-11-15
You should download the amsn-installer to your home directory (/home/galotzas) and run it from there as the normal you (not root); /home/galotzas/amsn-installer.

---

### Post by monkeyface on 2005-11-16
... Screenshots?

---

### Post by hardclip on 2005-11-16
Hi, Can somebody please, please, please help me....

I am totally new to Linux and would really like to get this thing working...

I am going as far as loading aMSN in the instructions..this is the error I'm getting:

peter@linuxpc:~$ /usr/local/bin/wish8.5 /home/peter/amsn
Error in startup script: invalid command name "export"
    while executing
"export LD_ASSUME_KERNEL=2.2.5"
    (file "/home/peter/amsn" line 2)


What the hell am I doing wrong? The error shown is exactly what the how-to tells you to paste into the ~/amsn edit..if I leave this blank, amsn opens but it is just a blank window..my will is close to breaking..

Could somebody please point me in the right direction?? I would be most appreciative

---

### Post by -DarkMind- on 2005-12-06
thanks :)

---

### Post by sapo on 2005-12-06
[QUOTE=monkeyface]... Screenshots?[/QUOTE]
I wanna see it too :)

---

### Post by shadow on 2005-12-07
christ, what an improvement. I'd of never even looked at aMSN until I saw this guide.

You should mail the developers or something and try and get this the default apperance. The fact that the official screenshot from the site looks that bad is appalling.

Cheers anyway!

---

### Post by sapo on 2005-12-07
screenshot or die! :P

---

### Post by shadow on 2005-12-07
[QUOTE=sapo]screenshot or die! :P[/QUOTE]

Theres screenshots linked in the first post.

[http://img256.imageshack.us/img256/5505/amsngrystal4se.png](http://img256.imageshack.us/img256/5505/amsngrystal4se.png)

---

### Post by Neo40 on 2005-12-11
Hi,

When I type this command:

 /usr/local/bin/wish8.5 amsn

I get this error:

Picture.tcl: TkCximage not loaded

---

### Post by eriqk on 2005-12-16
When I do "/usr/local/bin/wish8.5 ~/msn/amsn", I get a segmentation fault.
I get no warnings when I build tcl, tk or aMSN.

---

### Post by rogeriovinhal on 2005-12-17
I also have the Segmentation Fault when I try to run aMSN with wish8.5...
wish8.4 will do the job, but with no improvements from Tcl 8.5.

There is also something diferent from the original tutorial. My amsn is located in /usr/share/amsn/amsn, not in /usr/local/share/amsn/amsn, second doesnt exist.
But i don't think there is a real problem. The Segmentation Fault yes.

EDIT: Nevermind, I was using an older version of aMSN CVS. Just followed the tutorial of getting it again, and it was fine.

---

### Post by eriqk on 2005-12-17
[QUOTE=rogeriovinhal]EDIT: Nevermind, I was using an older version of aMSN CVS. Just followed the tutorial of getting it again, and it was fine.[/QUOTE]

That's a good idea, actually. I see how far I get.

//edit
Redid the entire process, but I still get a segmentation fault. This time shortly after launch.

//edit again
When I open 0.94 (which is in /usr/share/amsn/amsn) all goes well. I wonder what's wrong with my 0.95.
apart from that cluncky motif stuff, 0.94 looks very nice and antialiased.

---

### Post by ubuntumaneh on 2006-02-02
This is a nice how-to.

My problem is the following: I have installed new fonts (cleartype, for instance) in my box. For other applications, like Firefox, I could choose to use these fonts. In amsn (preference+appearence+fonts), there is no options for this fonts, only the usual set. How can I insert new fonts for amsn?

Thanks a lot

---

### Post by CyberAngel on 2006-02-09
I have installed aMSN using this guide (On a Kubuntu Breezy AMD64) and it so much better than before (actually before it was a crap) but I have a problem now and I can`t connect to messenger service....

I am using an http proxy and when I am trying to connect I am getting a aMSN error...
When I am pressing details I can see the following:
```
bad variable name "options(-proxy_writing)": upvar won't create a scalar variable that looks like an array element
    while executing
"upvar ::ProxyHTTP::Snit_inst2::options(-proxy_writing) options(-proxy_writing)"
    ("uplevel" body line 1)
    invoked from within
"uplevel upvar ${selfns}::$varname $varname"
    (procedure "::snit::RT.variable" line 5)
    invoked from within
"variable options(-proxy_writing)"
    (procedure "::ProxyHTTP::Snit_methodHTTPRead" line 8)
    invoked from within
"::ProxyHTTP::Snit_methodHTTPRead ::ProxyHTTP ::ProxyHTTP::Snit_inst2 ::Proxy::ProxyHTTP1 ::Proxy::ProxyHTTP1 ns"
    ("uplevel" body line 1)
    invoked from within
"uplevel 1 $command $args"
    invoked from within
"$self HTTPRead $sb"
    (procedure "::ProxyHTTP::Snit_methodConnectReply" line 5)
    invoked from within
"::ProxyHTTP::Snit_methodConnectReply ::ProxyHTTP ::ProxyHTTP::Snit_inst2 ::Proxy::ProxyHTTP1 ::Proxy::ProxyHTTP1 ns sock9"
    ("uplevel" body line 1)
    invoked from within
"uplevel 1 $command $args"
    invoked from within
"::Proxy::ProxyHTTP1 ConnectReply ns sock9"
```

Anyway, finally I can`t connect even if I press the ignore button. :-k 
Please help!! :( 
I am attaching a screenshot of the error that popups..

---

### Post by NoWhereMan on 2006-03-01
damn, i have your same problem, it looks like a tcl issue :(
I had to recompile with 8.4 :( if anybody has an old working package let us know :(

**EDIT:** try to delete or move the .amsn/ dir in your home
bye

---

### Post by CyberAngel on 2006-03-01
[QUOTE=NoWhereMan]
**EDIT:** try to delete or move the .amsn/ dir in your home
bye[/QUOTE]

No luck.. Only if I compile it with 8.4 it works but it is not de-uglified....

---

### Post by NoWhereMan on 2006-03-02
[QUOTE=CyberAngel]No luck.. Only if I compile it with 8.4 it works but it is not de-uglified....[/QUOTE]
then send out the bug when comes up the dialog, and maybe aks on #amsn on irc.freenode.org , I'm afraid, I can't help more :(

---

### Post by CyberAngel on 2006-03-02
[QUOTE=NoWhereMan]then send out the bug when comes up the dialog, and maybe aks on #amsn on irc.freenode.org , I'm afraid, I can't help more :([/QUOTE]

I have already sent a bug report...
Anyway thanks man :)

---

### Post by NoWhereMan on 2006-04-27
proxy bug should now be fixed.
anyway, awesome skin: [http://www.kde-look.org/content/show.php?content=38202](http://www.kde-look.org/content/show.php?content=38202) !

---

### Post by panurge77 on 2006-06-05
Amsn wiki suggests compilin tcl/tk without the --enable-threads would avoid kernel hangs on 2.6 kernel.

---

### Post by [Nirvana] on 2006-06-19
I'm getting an error:
```
$ sudo apt-get build-dep tcl8.4 tk8.4 Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for tcl8.4
```

What can I do?

I'm on dapper btw.

---

### Post by NoWhereMan on 2006-06-20
[QUOTE='[Nirvana]']I'm getting an error:
```
$ sudo apt-get build-dep tcl8.4 tk8.4 Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for tcl8.4
```

What can I do?

I'm on dapper btw.[/QUOTE]


enable deb-src in your sources.list

so:

sudo nano /etc/apt/souces.list
remove the # before the lines beginning with deb-src

then save & quit

sudo apt-get update

then retry

bye

---

### Post by Xecuter on 2006-06-21
When I run this line ```
 cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl login
``` I get ```
bash: cvs: command not found

```

Am I noob? Or am I missing something?

---

### Post by CyberAngel on 2006-06-21
[QUOTE=Xecuter]When I run this line ```
 cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl login
``` I get ```
bash: cvs: command not found

```

Am I noob? Or am I missing something?[/QUOTE]


sudo apt-get install cvs ;)

---

### Post by panurge77 on 2006-06-21
You wont get it anyway. Amsn has moved from cvs to svn.

---

### Post by NoWhereMan on 2006-06-22
that line is for tcl.
You're not n00b, that line is now wrong, due to a change in sf internals

here are fixed (they should work, even if I haven't tested)

**To get CVS Tcl:**
```

cvs -d:pserver:anonymous@tcl.cvs.sourceforge.net:/cvsroot/tcl login 
<hit enter>
cvs -z3 -d:pserver:anonymous@tcl.cvs.sourceforge.net:/cvsroot/tcl co -P tcl
```
**To get CVS Tk:**
```
cvs -d:pserver:anonymous@tktoolkit.cvs.sourceforge.net:/cvsroot/tktoolkit login 
<hit enter>
cvs -z3 -d:pserver:anonymous@tktoolkit.cvs.sourceforge.net:/cvsroot/tktoolkit co -P tk
```

bye :)

---

### Post by panurge77 on 2006-06-22
Err. Sorry
I didnt really read it all
8)
And actually yes, I'm a noobie. Never even tried cvs.

---

### Post by Xecuter on 2006-06-22
Nevvermind!

---

### Post by [Nirvana] on 2006-06-22
lol, I figured it out and forgot to update my post.

And thanks for the updated lines... someone should edit the orig. post.

---

### Post by Moebius on 2006-06-28
I'm having a slight problem, not sure if it's a bug from the latest SVN (can't say CVS anymore) versions.

I have unfocused windows, and when someone talks to me, suddenly that window gains focus.

Is there a way do disable this?

EDIT: While testing solutions for this, it seems to be compiz related.

[COLOR="Red"]EDIT2: Seems to be fixed by disabeling "Auto Raise" on CompizTools. Not sure if it was enabled by default or if somewhat I had inavertedly activated it[/COLOR] - Didn't fix it, error still ocours.

---

### Post by nicorubiolo on 2006-06-28
**To get CVS Tcl:**
```

cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl login 
<hit enter>
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl co -P tcl
```
**To get CVS Tk:**
```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tktoolkit login 
<hit enter>
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tktoolkit co -P tk
```


Do not work...cannot find host....any solution??

Cheers

---

### Post by Moebius on 2006-06-28
[QUOTE=nicorubiolo]**To get CVS Tcl:**
```

cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl login 
<hit enter>
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl co -P tcl
```
**To get CVS Tk:**
```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tktoolkit login 
<hit enter>
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tktoolkit co -P tk
```


Do not work...cannot find host....any solution??

Cheers[/QUOTE]

You need to use the new instructions, located at post #49, on the page before this one.

---

### Post by devan on 2006-06-28
hey guys.

got this all installed and running, but when I try to login, it complains i dont have TLS installed on the system.

I checked Synaptic and it is showing as being installed on my system.

I tried to change the directory under advanced preferences to /lib/tls/ but still the same error.

aMSN tries to auto install at startup, but gives the error "Error installing TLS Module"

Any suggestions?

---

### Post by CyberAngel on 2006-06-29
[QUOTE=devan]hey guys.

got this all installed and running, but when I try to login, it complains i dont have TLS installed on the system.

I checked Synaptic and it is showing as being installed on my system.

I tried to change the directory under advanced preferences to /lib/tls/ but still the same error.

aMSN tries to auto install at startup, but gives the error "Error installing TLS Module"

Any suggestions?[/QUOTE]

I had/have the same problem but unfortunately I don`t have a solution yet (I hadn`t asked for it though)
So I would appreciate an answer to this one ;)

---

### Post by panurge77 on 2006-06-29
For the TLs, that fixed it for me:

If you get an error about tls, then:
sudo gedit /usr/lib/tls1.50/pkgIndex.tcl
And change
package ifneeded tls 1.5
To
package ifneeded tls 1.50

Now tell amsn where tls on amsn preferences>advanced> TLS: /usr/lib

---

### Post by bohboh on 2006-06-30
I followed the excellent instructions and all is well . So many thanks. :D

One thing, is it possible to somehow de-uglify the popups?

See screenshot:

[[IMG]http://img299.imageshack.us/img299/4079/untitled2cn1.jpg[/IMG]](http://imageshack.us)

I would like to change the font and font size and reduce the amount of space. Is that possible?

---

### Post by panurge77 on 2006-06-30
I never used the popups but I guess they change with the themes, so you might try changing theme

---

### Post by bohboh on 2006-07-01
Ok, I may make an attempt at changing it myself.

One question, now that i have the main amsn window looking how i want. My update manager keeps telling me that there is a newer version of amsn. I have locked it in synaptic to prevent it updating.

Will updating it undo the work i did by following this guide? Or is it ok to upgrade?

---

### Post by Moebius on 2006-07-06
[QUOTE=Moebius]I'm having a slight problem, not sure if it's a bug from the latest SVN (can't say CVS anymore) versions.

I have unfocused windows, and when someone talks to me, suddenly that window gains focus.

Is there a way do disable this?

EDIT: While testing solutions for this, it seems to be compiz related.

[COLOR="Red"]EDIT2: Seems to be fixed by disabeling "Auto Raise" on CompizTools. Not sure if it was enabled by default or if somewhat I had inavertedly activated it[/COLOR] - Didn't fix it, error still ocours.[/QUOTE]

With compiz, under the **fade** plugin, disabeling the "enable urgent flashing" solved the issues with aMSN and all other windows gain sudden focus.

---

### Post by Rackerz on 2006-07-08
darren@darren:~$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tcl login
bash: cvs: command not found

What am I doing wrong?

---

### Post by jan on 2006-07-08
Well I guess you use Gaim and have no problems with de-uglifying aMSN at all ;). Just a suggestion, of course! :KS

---

### Post by vivia on 2006-09-17
Rackerz : sudo apt-get install subversion

jan : what suggestion??

---

### Post by jcrnan on 2006-09-18
When I treid the cvs command from the second step it said cvs command wasnt found. any tips?

---

### Post by NoWhereMan on 2006-09-19
> **jcrnan said:**
> When I treid the cvs command from the second step it said cvs command wasnt found. any tips?

sudo apt-get install cvs

however, I'd suggest to follow this guide
[http://amsn.sourceforge.net/userwiki/index.php/Enabling_antialiasing](http://amsn.sourceforge.net/userwiki/index.php/Enabling_antialiasing)
which should be more updated

for any problem with amsn, go to [http://amsn.sf.net/forums](http://amsn.sf.net/forums) (search the forums first ;))

bye :)

---

