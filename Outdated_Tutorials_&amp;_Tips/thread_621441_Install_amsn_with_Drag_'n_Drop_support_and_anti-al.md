---
title: "Install amsn with Drag 'n Drop support and anti-aliased font"
date: 2007-11-23
forum: Outdated Tutorials &amp; Tips
---

### Post by FemiVeys on 2007-11-23
I wrote this script that automatically compiles and installs aMSN with **Drag 'n Drop support** and **anti-aliased fonts**.
The install can be done interactively or unattended.
It is done in several steps. When the interactive mode is chosen one will be able to choose at every step if you want to execute it.
The script also remembers what was the last successful step (in case something went wrong). Then you can choose to continue the installation from there on.

Following steps are executed:
[SIZE="1"]STEP 1 : Install prerequisites to compile (uses apt-get)
STEP 2 : Create new empty work folder
STEP 3 : Download TCL source code
STEP 4 : Extract tcl8.5.0-src.tar.gz
STEP 5 : Compile and install TCL
STEP 6 : Download TK source code
STEP 7 : Extract tk8.5.0-src.tar.gz
STEP 8 : Compile and install TK
STEP 9 : Download TKDND source code (from CVS)
STEP 10 : Compile and install TKDND
STEP 11 : Download aMSN source code (from svn)
STEP 12 : Compile and install aMSN
STEP 13 : Install aMSN plugins and skins (from svn)
STEP 14 : Install amsn start script in /usr/local/bin/amsn
STEP 15 : Add aMSN menu entry
STEP 16 : Download TLS source code
STEP 17 : Extract tls1.5.0-src.tar.gz
STEP 18 : Compile and install TLS[/SIZE]

[b]The script can be found in the attachment below.

First you'll have to make the file executable:
```
chmod +x aMSN_install.sh
```

To install in another directory or if you want to change other parameters, do:
 ```
./aMSN_install.sh -h
```

To execute the script, simply execute:
 ```
./aMSN_install.sh
```

If everything goes well you will have
- the latest aMSN from svn
- Anti-aliased fonts
- Drag 'n Drop support (for filetransfers)
- the latest skins and plugins (from svn)
- a working TLS plugin (for SSL)
- an executable: /usr/local/bin/amsn, which means you can start it by typing amsn
- a menu entry (following freedesktop.org standard)

The script should work on any **debian-based** distribution and should work on both 32-bit as 64-bit.

This script has been tested on Ubuntu Gutsy 7.10 on an AMD64 architecture.

Please provide some feedback if you tried the script.

Edit:
I have updated the script to version 0.4.2. Now the stable TCL/TK 8.5 is used instead.
I have updated the script to version 0.4.3:
   - Fix for svn (ssl) certificate question not showing up
   - Download progress for TCL/TK and TLS shows up now

---

### Post by NoobixCube on 2007-12-31
Thankyou!  This is exactly what me and every other lazy person needs :P.  I'm only competent enough to follow tutorials to the letter (with a little adaptation sometimes), and this just takes all the time out of doing it myself :D

---

### Post by Trinexx on 2008-01-01
"Firefox can't find the server at www.femiveys.cheapass.be."

:(

---

### Post by olskar on 2008-01-02
> **Trinexx said:**
> "Firefox can't find the server at www.femiveys.cheapass.be."

:(

Download attached file instead :)

---

### Post by xerox5555 on 2008-01-02
Good work...
;-) Thanks for you...

---

### Post by Puj on 2008-01-02
I had an error and it didn't work. Here is the log file, had to zip it as it was too big for the forum

---

### Post by xerox5555 on 2008-01-03
> **Puj said:**
> I had an error and it didn't work. Here is the log file, had to zip it as it was too big for the forum

For Setup questions Press:
- N ( First question )
- Enter ( svn password questions )
- P ( svn accept questions )

good work.. :)

---

### Post by FemiVeys on 2008-01-10
As cheapass is in trouble it has become impossible to reach the server.

While I looking for an alternative you can still se the script in attachment. I have updated the sctipt so it uses now the latest TCL/TK sources.
As some of you know, since December 18, version 8.5 is finally stable and released.

Questions are welcome

---

### Post by weed-n-linux on 2008-01-10
[COLOR="DarkOrange"]could you tell me what is the approxiative size of tk and tcl ? because when the script download it doesn't give info about the DL process , and i want to check out whether or not it's actually doing the thing (Downloading TCL source code...) it took 7 min with my connection that reaches 60 Kb/s with a dope server :) [/COLOR]

---

### Post by weed-n-linux on 2008-01-10
[COLOR="DarkOrange"]hey forget the first question :) now i have a more dark problem as dark as the terminal . when i am in step 7 it asks you if you want to extract Tk when i type Y the terminal disappears .
this is the last thing you see in it [/COLOR]
> STEP 7 : Extract tk8.5.0-src.tar.gz

Do you want to execute this step? [Default is Y] (y/n/c):  :KS

---

### Post by FemiVeys on 2008-01-10
Weed-n-linux, I don't have a clue how your terminal can disappear from extracting a file.
Can you send me the logfile?

FYI: TCL is 4.2MB, TK is 3.6 MB. Here the connection is very well. I reach approx. 400K/s.

---

### Post by weed-n-linux on 2008-01-10
[COLOR="Indigo"]i don't know how to extract the Log file , but let's look at the bright side i installed Tcl 8.5  :) could you send me some link to download Tk ? couldn't find it anywhere ...[/COLOR]

---

### Post by FemiVeys on 2008-01-11
Please follow the instructions and execute the script from the terminal.

I suspect you launch the script by double clicking on it and the choosing execute in terminal. That's a nice Ubuntu way of executing shel scripts in a terminal, but the problem is that once the script finishes, it closes the terminal so you don't see what happened.

If you execute the script from a real terminal (./aMSN_install.sh) you will see where to find the logfile if something went wrong.
For your convenience, the logfile is by default in: $HOME/amsn_install.log.

Looking at the bottom should tell what went wrong.

Now, installing TCL/TK manually is a possibility, but it is exactly what this script wants to automate. But if you really want to, TK can be found on: [http://garr.dl.sourceforge.net/sourceforge/tcl/tk8.5.0-src.tar.gz](http://garr.dl.sourceforge.net/sourceforge/tcl/tk8.5.0-src.tar.gz)

But installing it manually, you need to know what you do as you need specific install flags.

**So please send me the log so I can analyze the problem and if needed optimize the script if there is really something wrong in it.**

---

### Post by weed-n-linux on 2008-01-11
thank you Femiveys a lot and this is the log file you prompted : 
> Thu Jan 10 22:10:40 WET 2008
[34mChecking for a previous run...
[32mA previous run has been found. Last successfull step was: 
STEP 2 : Create new empty work folder.

Do you want to try to continue? [Default is Y] (y/n): [32mDo you want to do an interactive install? If you choose Yes, 
before every step you will be prompted. [Default is N] (y/n): [31mYou have chosen to enter the interactive mode.
[31mThis means you will be prompted at every step.
[31mPress 'C' to accept the default and continue in non-interactive mode
[32mSTEP 1 : Install prerequisites
[32mDo you want to execute this step? [Default is Y] (y/n/c): [32mSTEP 2 : Create new empty work folder
[32mDo you want to execute this step? [Default is Y] (y/n/c): [32mSTEP 3 : Download TCL source code
[32mDo you want to execute this step? [Default is Y] (y/n/c): [32mSTEP 4 : Extract tcl8.5.0-src.tar.gz
[32mDo you want to execute this step? [Default is Y] (y/n/c): [32mSTEP 5 : Compile and install TCL
[32mDo you want to execute this step? [Default is Y] (y/n/c): [32mSTEP 6 : Download TK source code
[32mDo you want to execute this step? [Default is Y] (y/n/c): [32mSTEP 7 : Extract tk8.5.0-src.tar.gz
[32mDo you want to execute this step? [Default is Y] (y/n/c): [34mExtracting tk8.5.0-src.tar.gz...
[31mAn error occured. For details, look at /home/fadel/amsn_install.log.

---

### Post by FemiVeys on 2008-01-11
This is not the logfile.

The logfile can be found in: /home/fadel/amsn_install.log

---

### Post by j.anus on 2008-01-18
Thanks man, worked great!!! not even a single problem!

---

### Post by theodore_kh on 2008-01-18
I've tried it and it works. 

Everything run smoothly without an error.

Thanks

---

### Post by McAbre on 2008-01-19
Went ok for everything except step 13, so I skipped it. Works ok.

---

### Post by powertothelinux on 2008-01-21
yeah problem solved =D> 
thanks for help!

---

### Post by seibaby on 2008-01-25
I unfortunately cannot get it to work... I run the script in Terminal and after answering the first question, it just sits there at "Installing pre-requisites..." and nothing happens. For hours.
Any help?
I had aMSN installed when I ran this script if that matters..

Edit: Nevermind! I finally got it to work. Somehow I got past the first step when I had the ubuntu cd in my cdrom. I had a few other hiccups but managed to solve them by monitoring the install log. Thanks!

---

### Post by SECProto on 2008-01-29
> **seibaby said:**
> Edit: Nevermind! I finally got it to work. Somehow I got past the first step when I had the ubuntu cd in my cdrom. I had a few other hiccups but managed to solve them by monitoring the install log. Thanks!

I had the same problem as him, putting the ubuntu cd in also fixed it for me. i also thought i had problems with other parts, but it was always when downloading or compiling and whatnot, took quite a while. but they all worked out in the end, and i love the drag and drop. thanks a lot!! :)

---

### Post by LukeCarrier on 2008-02-15
Doesn't work.

I just get loads of errors at step 14. I would post a log but even when zipped it's still to big to post as an attachment.

Any other people had this problem? Have you managed to work around it?

Luke.

---

### Post by LukeCarrier on 2008-02-16
> **SECProto said:**
> I had the same problem as him, putting the ubuntu cd in also fixed it for me. i also thought i had problems with other parts, but it was always when downloading or compiling and whatnot, took quite a while. but they all worked out in the end, and i love the drag and drop. thanks a lot!! :)

You guys probably still had your Ubuntu installation CD checked in your repositories, which would explain why putting the CD in the drive would make it work.

FemiVeys, may I suggest you let your clever little scripts echo out the progress when downloading and installing files? There's loads of massive pauses in between the steps, it'd be nice to see a little more information so it's actually working, if you catch my drift?

Anyone got any ideas about the problem I'm having? I end up with a file called amsn_bin on my desktop, 
when I open this file aMSN opens, and gets to a dialog asking me to install tls, but when I select my architecture from the dialog and click OK, it doesn't work. I trued running it with 'gksudo' and 'sudo' but with no luck. I'm going to try compiling it from source....Which options do I need to run with the tls1.50 configure script? I'm running it in terminal and getting this error:

```

loading cache ./config.cache
configure: error: /usr/local/ssl is not a valid directory

```

This just gets better and better :P

---

### Post by Jean__ on 2008-03-04
Well I was gonna say , it worked without an error but for the life of me I can't figure out how to drag and drop. I'm trying to drop a file into the conversation window, at all possible places, but I get no reaction.

Jean.

---

### Post by FemiVeys on 2008-03-04
Normally you should drag 'n drop into the text area of your conversation.
I used gnome and nautilus.

Are there other people who have problems with the drag 'n drop?

---

### Post by Jean__ on 2008-03-04
Kde here. When I use nautilus, the icon 'flies back' to nautilus so the msn window definately does not accept the drop.

---

### Post by prioprio on 2008-03-10
I had this error at STEP 12:
Compile and install aMSN
Compiling aMSN...
configure: error: Your current Tcl/Tk installation has a version number of 8.3. The minimal version required for aMSN to run is Tcl/Tk 8.4

---

### Post by FemiVeys on 2008-03-11
Strange, as it is exactly the purpose to install the latest TCL/TK (8.5). Did you execute all steps?

---

### Post by prioprio on 2008-03-11
> **FemiVeys said:**
> Strange, as it is exactly the purpose to install the latest TCL/TK (8.5). Did you execute all steps? Yes ! This is the output of my log file.

---

### Post by FemiVeys on 2008-03-12
I installed especially for you a fresh Ubunutu in VMware. I really don't see how you can get such an error.

Did you use the -T flag perhaps or any other flag?

All I can think of is that maybe there was a temporary bug in amsn, but I would doubt so.

Maybe just try again. :-k

---

### Post by prioprio on 2008-03-12
**Solution found !**

Before i added those repository:
```
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
```
than added the key
```
wget http://3v1n0.tuxfamily.org/DD800CD9.gpg -O- | sudo apt-key add -
```
after i installed tcl/tk
```
sudo apt-get install libsnack2 tcl8.5 tcl8.5-dev tcllib tile tk8.5 tk8.5-dev
```
and than when i run your script i skipped the installation of tcl/tk.

8) **Thanks !**

---

### Post by FemiVeys on 2008-03-13
I am happy it worked likke this. But the purpose of the script is exactly to avoid this.
I wonder if others have that problem as when I look at the code it is almost impossible with the default settings TCL/TK is not foud.

Good luck with it.

---

### Post by bongo on 2008-03-26
-please delete-

---

### Post by Jean__ on 2008-04-01
I reported before that the drag & drop didn't work. 

Well, it started working. :) Must have been one of those things...

Thanks.
Jean.

---

### Post by luisgls on 2008-04-27
Hi, I just use the script and it was a perfect installation. I am using hardy. But there is a problem with the sound, when I try to choose snack as sound server it shows: "Snack failed to load reverting to default"

How can I solve it?
Many many Thanks

---

### Post by kommizzarr on 2008-05-11
hello 
I get this "(try: 6) => `tls1.5.0-src.tar.gz'
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... failed: Connection timed out.
Retrying."
Can anyone help me? 
I'm using Hardy on amd 64

EDIT ***** 

Well nevermind I found this [http://ubuntuforums.org/showthread.php?t=500768](http://ubuntuforums.org/showthread.php?t=500768)  and solved it :)

works great now thanks for this

---

### Post by ChrisHodgkins on 2008-06-17
Just tried to use your script with Hardy and unfortunately it's failing.

-L/usr/local/tcltk8.5/lib -ltclstub8.5   -Wl,-rpath,/usr/local/tcltk8.5/lib
/usr/bin/ld: cannot find -ltclstub8.5

collect2: ld returned 1 exit status

make: *** [libtk8.5.so] Error 1

cheers

---

### Post by Demothesis on 2008-07-28
Just wanted to say thanks! This script worked perfectly for me on Ubuntu Hardy x64 and saved me a whole lot of pain and frustration. I'm sure something would have gone wrong had I tried it myself.

---

### Post by alecz20 on 2008-08-15
I try this on my friends computer and I get:

Input:
[/code]
sudo chmod +x aMSN_install.sh
./aMSN_install.sh
[/code]

Output:
```

bad interpreter
no such file or directory

```


why isn't ./ working?
BTW, this is a very fresh installation of hardy

Edit:
I found the problem. We sent the sh file via Hotmail, and I guess it got corrupted, because after I "rewrote" the 1st line and saved it worked perfectly.
Apparently bash was seeing an ^M at the end of line 1 in the script.

---

### Post by offbyte on 2008-11-08
and how do I uninstall it ?

---

### Post by astathios on 2009-03-01
hello and thank you very much for the script
everything works perfect except the sound for video calls.
When i run the wizard from prefferencies amsn can load my webcam but says that cant find farsight. farsight is compiled in my system .
i made a test from the official amsn site and and i run amsn dev package from terminal and the soundworked perfect !! any idea how to make it work with your code? 
thank you very much in advance

---

### Post by fferreira on 2009-04-12
I've tried to use the script. Everything seemed nice during the instalation..

However I am getting this message when I try to run amsn:

```
Application initialization failed: Can't find a usable tk.tcl in the following directories: 
    /usr/local/tcltk8.5/lib/tcl8.5/tk8.5 /usr/local/tcltk8.5/lib/tk8.5 /usr/local/lib/tk8.5 /usr/local/tcltk8.5/library

/usr/local/tcltk8.5/lib/tk8.5/tk.tcl: no event type or button # or keysym
no event type or button # or keysym
    while executing
"bind Listbox <MouseWheel> {
        %W yview scroll [expr {- (%D / 120) * 4}] units
    }"
    invoked from within
"if {[tk windowingsystem] eq "aqua"} {
    bind Listbox <MouseWheel> {
        %W yview scroll [expr {- (%D)}] units
    }
    bind Listbox <Option-Mou..."
    (file "/usr/local/tcltk8.5/lib/tk8.5/listbox.tcl" line 182)
    invoked from within
"source /usr/local/tcltk8.5/lib/tk8.5/listbox.tcl"
    (in namespace eval "::" script line 1)
    invoked from within
"namespace eval :: [list source [file join $::tk_library $file.tcl]]"
    (procedure "SourceLibFile" line 2)
    invoked from within
"SourceLibFile listbox"
    (in namespace eval "::tk" script line 4)
    invoked from within
"namespace eval ::tk {
	SourceLibFile button
	SourceLibFile entry
	SourceLibFile listbox
	SourceLibFile menu
	SourceLibFile panedwindow
	SourceLibFile ..."
    invoked from within
"if {$::tk_library ne ""} {
    proc ::tk::SourceLibFile {file} {
        namespace eval :: [list source [file join $::tk_library $file.tcl]]
    }
   ..."
    (file "/usr/local/tcltk8.5/lib/tk8.5/tk.tcl" line 404)
    invoked from within
"source /usr/local/tcltk8.5/lib/tk8.5/tk.tcl"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list source $file]"


This probably means that tk wasn't installed properly.

Error in startup script: no event type or button # or keysym
    while executing
"bind Pixmapscroll <MouseWheel> {
        tk::ScrollByUnits %W v [expr {- (%D)}]
    }"
    invoked from within
"if {![catch {tk windowingsystem} wsystem] && $wsystem == "x11"} {
    bind Pixmapscroll <MouseWheel> {
        tk::ScrollByUnits %W v [expr {- (%D)}]
..."
    (file "pixmapscroll.tcl" line 717)
    invoked from within
"source [file join pixmapscroll.tcl]"
    ("package ifneeded pixmapscroll 0.9" script)
    invoked from within
"package require pixmapscroll"
    invoked from within
"if { $initialize_amsn == 1 } {

	if {![::picture::Loaded]} {
		if { [OnDarwin] } {	
			tk_messageBox -default ok -message "There's a problem loading a..."
    (file "gui.tcl" line 4)
    invoked from within
"source gui.tcl		"
    ("uplevel" body line 22)
    invoked from within
"uplevel \#0 {

	# amsncore.tcl is already loaded but we'll re-source it here in case we manually do reload_files
	source amsncore.tcl
	source audio.tc..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/local/amsn/share/amsn/amsn" line 276)

``` 

DO you know what did it happen?

---

### Post by Phalco on 2009-04-24
I Have the same problem...
Any ideas?

---

### Post by IraGainesUK on 2009-08-08
To fix the loading problem, just open up the original aMSN_install.sh script and do a find/replace for 8.5.0/8.5.6 - save and re-run the script.  That should solve your problem.

And I can also confirm that it works (drag and drop of files into the chat window) in Ubuntu Jaunty 64, however some things do not work.  

As mentioned above, there is a sound error when running the webcam wizard from preferences, and also I cannot view some of my friends' webcams through amsn (however it works fine in windows on the same computer using WLM - if only WLM worked in Ubuntu, all my problems would be solved :).)  

I think the webcams not connecting are a more fundamental fault with microsoft not supporting anyone but themselves again, to quote an amsn forum ([http://www.amsn-project.net/forums/viewtopic.php?t=6289&start=0&postdays=0&postorder=asc&highlight=](http://www.amsn-project.net/forums/viewtopic.php?t=6289&start=0&postdays=0&postorder=asc&highlight=))
> 
"the problem is when you are both firewalled and you use the reflector (third party server to act as a relay), then it will fail with the white screen bug or get canceled because the microsoft relay servers do not work anymore..."

Hmmn, so if anyone has any insights into *that* problem, then Ill be happy to hear from you! :)

Hope that helps someone!

---

### Post by Kosmi4 on 2009-09-19
> **Phalco said:**
> I Have the same problem...
Any ideas?

Same problem & error report..

The suggestion ''To fix the loading problem, just open up the original aMSN_install.sh script and do a find/replace for 8.5.0/8.5.6 - save and re-run the script. That should solve your problem'' didn't work

Any other suggestion ??

---

