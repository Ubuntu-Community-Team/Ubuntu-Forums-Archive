---
title: "HOWTO: Install aMSN 0.98b with anti-aliasing in Ubuntu"
date: 2008-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by holy_fire on 2008-08-06
I recently made a fresh install of Ubuntu Hardy 8.04 on my desktop computer and I found out that the aMSN 0.97 package available via Synaptic Package Manager was not quite useful. I experienced a lot of connection problems. Although those problems are gone with version 0.98b, enabling anti-aliasing fonts is not an easy task. A lot of resources are available about this but I thought I'd make a tutorial especially about how to compile aMSN 0.98b with anti-aliasing in Ubuntu.

[COLOR="Magenta"]Step 1[/COLOR]
Open a terminal session by pressing "Alt+F2" then typing "gnome-terminal". Make sure your computer is connected to the Internet.


[COLOR="Magenta"]Step 2 : Install the g++ compiler (can be skipped if already installed)[/COLOR]
First, you need to make sure the g++ compiler is installed on you computer. At the prompt, simply enter the following code

```
sudo aptitude install g++
```


[COLOR="Magenta"]Step 3 : Install subversion (can be skipped if already installed)[/COLOR]
We are going to download the aMSN source code via subversion, so you need to have it installed. At the prompt, simply enter the following code

```
sudo aptitude install subversion
```

[COLOR="Magenta"]Step 4 : Install the latest tcl/tk libraries[/COLOR]
Since aMSN is written in tcl/tk, we need to download the latest libraries in order to compile properly. The good news is that v8.5 supports anti-aliasing. At the prompt, simply enter the following code

```
sudo aptitude install tk8.5-dev
```

It should install everything you need to compile aMSN, including the tcl8.5 libraries.

[COLOR="Magenta"]Step 5 : Get the aMSN source code[/COLOR]

Simply enter the following code at the prompt

```
svn co https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn amsn

```

This will download all the source code in your home directory. For more info, visit this page [http://www.amsn-project.net/wiki/Enabling_antialiasing]("http://www.amsn-project.net/wiki/Enabling_antialiasing")


[COLOR="Magenta"]Step 6 : Build aMSN[/COLOR]

Change your working directory by entering

```
cd amsn
```

Then you use the usual commands to build the app.

```
./configure
make
sudo make install
```

Now, some people have experienced problems while running the configure script, something about the tcl/tk libraries not found. If you experience such a problem, or if your compiler builds using an old version of tcl/tk, use the following commands instead

```
 ./configure --with-tcl=$HOME$INST_PATH/lib --with-tk=$HOME$INST_PATH/lib
make
sudo make install

```

And that's it! You should find your shiny new aMSN under Applications->Internet->aMSN. Enjoy and feel free to comment about this tutorial.

Here is a screenshot showing those nice anti-aliasing fonts

---

### Post by Jeroen de Lange on 2009-01-26
did exactly as you said in intrepid ibis and got an error with at the end no make file etc

---

### Post by fatihsanli58 on 2009-02-18
hi
I acually manges to install amsn 0.98b svn version 10018 but the problem is when  i try make and audio call it gives two types of error;
1. XIO: fatal IO error 11 (Resource temporarily unavailable) x server(it was something like this)
2. (<unknown>:8609): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GstGConfAudioSrc' has no property named `blocksize'

(<unknown>:8609): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GstGConfAudioSrc' has no property named `blocksize'
Original stack trace :
invalid command name ".container_0.msg_0.f.bottom.f.voip.amplifier"
    while executing
"$frame_in.amplifier configure -state normal"
    (procedure "::ChatWindow::UpdateVoipControls" line 25)
    invoked from within
"::ChatWindow::UpdateVoipControls $chatid $sip $callid"
    (procedure "::amsn::SIPInviteSent" line 16)
    invoked from within
"::amsn::SIPInviteSent $email $sip $callid"
    (procedure "::MSNSIP::invitePrepared" line 11)
    invoked from within
"::MSNSIP::invitePrepared ::MSNSIP::SIPConnection1 [xxxx@live.com[/email]"
    ("eval" body line 1)
    invoked from within
"eval $options(-prepared)"

Stack trace of bgerror :
bad window path name ".bug_dialog"
    while executing
"winfo screenwidth $w"
    (procedure "::bugs::show_bug_dialog" line 54)
    invoked from within
"::bugs::show_bug_dialog [privacy $errorInfo]"
    (procedure "::bugs::bgerror" line 48)
    invoked from within
"::bugs::bgerror $args"
bug report windows appear and audio call finishes with this messege "user did not answer your call. Can anyone help me please? Thanks in advance.

---

### Post by fatihsanli58 on 2009-02-18
still waiting? someone there?

---

### Post by rbernardes on 2009-03-17
[http://rmbernardes.wordpress.com/2008/08/13/amsn-098svn-no-ubuntu-804-hardy-heron-cold-skin/](http://rmbernardes.wordpress.com/2008/08/13/amsn-098svn-no-ubuntu-804-hardy-heron-cold-skin/)

---

### Post by meeples on 2009-04-26
hey when i do ./configure it tells me i need libpng, so i went into synaptic and downloaded libpng but its still not working, anybody?

---

### Post by Stemp on 2009-05-07
Another way to install amsn 0.98b (with audio/video support) :

[aMsn-Daily PPA]("https://edge.launchpad.net/~amsn-daily/+archive/ppa")

---

### Post by binbash on 2009-05-09
> **Stemp said:**
> Another to install amsn 0.98b (with audio/video support) :

[aMsn-Daily PPA]("https://edge.launchpad.net/~amsn-daily/+archive/ppa")

Thanks for the repository

---

### Post by solixxx on 2010-02-21
Just for help, if you got the same problem as me.

My problem was, I need to install tcl/tk.
```

checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev

```

Just use the following command, and the problem should be fixed
```

sudo apt-get install tcl-dev tk-dev

```

---

