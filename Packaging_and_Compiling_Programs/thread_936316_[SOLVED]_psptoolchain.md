---
title: "[SOLVED] psptoolchain"
date: 2008-10-02
forum: Packaging and Compiling Programs
---

### Post by xXZeroXx on 2008-10-02
I'm trying to start programming for the psp under Linux so I got this:
[http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2](http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2)
And once I unpacked it, and started to follow the readme I got an error here:
> xxzeroxx@L-desktop:~/psptoolchain$ ./toolchain.sh
ERROR: Set $PSPDEV before continuing.            
../depends/check-pspdev.sh: Failed.              

This is the readme:
> 
 ====================
  What does this do?
 ====================

  This program will automatically build and install a compiler and other
  tools used in the creation of homebrew software for the Sony Playstation
  Portable handheld videogame system.

 ==================
  How do I use it?
 ==================

 1) Set up your environment by installing the following software:

  autoconf, automake, bison, flex, gcc, make, ncurses, patch, subversion, texinfo, wget

 2) Add the following to your login script:

  export PSPDEV=/usr/local/pspdev
  export PATH=$PATH:$PSPDEV/bin

 3) Run the toolchain script:

  ./toolchain.sh

 ==========================
  Where do I go from here?
 ==========================

  Visit the following sites to learn more:

   [http://www.ps2dev.org](http://www.ps2dev.org)
   [http://forums.ps2dev.org](http://forums.ps2dev.org)

I don't have any idea about what does it mean by:
>  2) Add the following to your login script:

  export PSPDEV=/usr/local/pspdev
  export PATH=$PATH:$PSPDEV/bin

So any help would be apreciated.
Thanks in advance.

---

### Post by ajtaggs on 2008-11-01
open a terminal and type 

```
cd
ls -a
```

please post what you get

---

### Post by xXZeroXx on 2008-11-02
> **ajtaggs said:**
> open a terminal and type 

```
cd
ls -a
```

please post what you get

> xxzeroxx@L-desktop:~$ cd
xxzeroxx@L-desktop:~$ ls -a
.                                        Imágenes
..                                       .inkscape
.adobe                                   .kde
.amsn                                    .kde4
amsn_received                            .kderc
.aMule                                   .ktorrent.lock
.aptitude                                .lesshst
.asoundrc                                .libao
.avidemux                                .limewire
.bash_history                            LimeWire
.bash_logout                             .local
.bashrc                                  .macromedia
.bashrc~                                 .mandvdconfig
bin                                      .mcop
.bogofilter                              .mcoprc
.cache                                   .metacity
.clamtk                                  .miro
.compiz                                  .mozilla
.config                                  .mozilla-thunderbird
Conversor_CISO                           .mplayer
.convert_2_mp4                           Música
.covers                                  MVI_0173.avi
.cups                                    .nautilus
.dbus                                    .openoffice.org2
.devede                                  .opera
.directory                               PDF
.dmrc                                    Plantillas
Documentos                               .profile
Downloads                                Pro Media Director
.dvdcss                                  Pro Media Director.desktop
.dvdrip                                  psptoolchain
.dvdriprc                                psptoolchain-20070626.tar.bz2
.emerald                                 PSP Video 9.desktop
enc.sh~                                  PSP Video Express.desktop
Escritorio                               Público
.esd_auth                                .pulse
.evolution                               .pulse-cookie
Examples                                 .purple
ffmpeg                                   .q3a
ffmpeg-0.cvs20070307                     .qt
ffmpeg_0.cvs20070307-5ubuntu7.1.diff.gz  .recently-used
ffmpeg_0.cvs20070307-5ubuntu7.1.dsc      .recently-used.xbel
ffmpeg_0.cvs20070307.orig.tar.gz         .registry
.fltk                                    .scim
.fontconfig                              silenthillcollection-thumb[1].jpg
.fonts.conf                              .smplayer
.fr-86Ve8d                               .spumux
.fr-jNX1no                               .ssh
.fr-ldZrfk                               .subversion
.fr-ZXAWEs                               .sudo_as_admin_successful
Fuentes                                  .sudoku
.gconf                                   .themes
.gconfd                                  .thumbnails
.giFT                                    .tomboy
gift-ares-0.3.0                          .tomboy.log
.gimp-2.4                                .transmission
.gksu.lock                               .update-manager-core
.gnome                                   .update-notifier
.gnome2                                  .vba
.gnome2_private                          Videos
.gnupg                                   .vlc
GNUstep                                  .wapi
.googleearth                             .wine
.gstreamer-0.10                          .winff
.gtk-bookmarks                           x264
.gtkpod                                  .Xauthority
.gtk_qt_engine_rc                        .xine
.gtkrc-2.0-kde                           .xscreensaver-getimage.cache
.gvfs                                    .xsession-errors
HandBrake                                .xsession-errors-:1
.hardinfo                                yasm-0.7.1
.ICEauthority                            yasm-0.7.2
.icons
xxzeroxx@L-desktop:~$

This is what I get

---

### Post by ajtaggs on 2008-11-02
good,

now try the following

```
sudo nano .bashrc
```

you will now be editing your login script. arrow down to the very bottom of the file and type in those lines you posted (make sure they are exact). Once you typed in those lines hit cntrl X, it will ask you if you want to save, answer y, and then hit enter to save over your old file.

Now you will have to run the new script, use

```
. .bashrc
```

Now try to run toolchain.sh

If you still run into an error, redo the steps except replace your lines with these ones:

```
export PSPDEV=/usr/local/pspdev
export PATH=$PATH:$PSPDEV/bin
export PSPSDK=$PSPDEV/psp/sdk/lib
```

---

### Post by xXZeroXx on 2008-11-02
I don't really understand what I am supposed to do, you mean that I should copy and paste all the .xxxx things? but, I should not copy paste the xxzeroxx@L-desktop thing, right? just the .whatever the name is

---

### Post by ajtaggs on 2008-11-02
Just open a terminal and do the following, and hopefully it will work.

```
xxzeroxx@L-desktop:~$sudo nano .bashrc
```

Note that the "xxzeroxx@L-desktop:~$" will already be there for you, just type the command "sudo nano .bashrc".

Ok, something like this should come up:
(You may need to type your password first)

```
  GNU nano 2.0.7               File: .bashrc                                    

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

                               [ Read 97 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

Hold down the down arrow key until you reach the bottom of the document, and type those export exaclty as they are in there. so it looks like this:

```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

#TYPE THIS ~~~~~~~~~~~~~~~~~~~~~
export PSPDEV=/usr/local/pspdev
export PATH=$PATH:$PSPDEV/bin
#~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

```

Of course, you dont need the TYPE THIS line or the ~~~~~ things.

Then just hit Control X, anwer y to the question, and hit enter.
After that the prompt should come back, type the following commands:

```
xxzeroxx@L-desktop:~$. .bashrc
xxzeroxx@L-desktop:~$cd psptoolchain
xxzeroxx@L-desktop:~/psptoolchain$sudo ./toolchain.sh
```

Then, hopefully you can come back here and tell me, "Hurray it worked" :)

Otherwise post what happened and I'll see what I can do

---

### Post by xXZeroXx on 2008-11-02
Well, it almost worked, you see, after I did what you told me, it displayed an error about some missing libraries (I don't really know if they are called libraries) well I started installing everything and it was ok, but then there is a package called ncurses that I can't install because it is too old or it has no candidate for installation, so I don't really know what to do, I've tried looking in google for this package but I find nothing. What can I do?

---

### Post by ajtaggs on 2008-11-02
hmm, do you get an error when you do:

```
xxzeroxx@L-desktop:~$sudo apt-get install build-essential autoconf automake bison flex \
  libncurses5-dev libreadline-dev libusb-dev texinfo libmpfr-dev \
  libgmp3-dev

```

If you do, tell me what the output is of this:

```
xxzeroxx@L-desktop:~$cd /usr/bin
xxzeroxx@L-desktop:/usr/bin$ls pyth*
```

If you didn't get an error, then great. Just do this:

```
xxzeroxx@L-desktop:~$cd psptoolchain
xxzeroxx@L-desktop:~/psptoolchain$ ./toolchain.sh

```

---

### Post by xXZeroXx on 2008-11-04
More Problemas When I did the firs thing I did'nt got any error so I did the tird thing here are the last lines of the output:
 ```
checking for psp-as... (cached) psp-as
checking for psp-ar... (cached) psp-ar
checking for psp-ranlib... (cached) psp-ranlib
checking for psp-readelf... (cached) psp-readelf
checking for a BSD-compatible install... /usr/bin/install -c
checking whether to enable maintainer-specific portions of Makefiles... no
checking for build system executable suffix... no
updating cache .././config.cache
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
make[1]: se sale del directorio `/home/xxzeroxx/psptoolchain/build/newlib-1.15.0/build-psp'
make: *** [all] Error 2
../scripts/004-newlib-1.15.0.sh: Failed.
xxzeroxx@L-desktop:~/psptoolchain$ 
```

---

### Post by ajtaggs on 2008-11-04
Try again, it could just be a currupt install attempt.

---

### Post by ajtaggs on 2008-11-04
If that doesn't work, try the following.

```
sudo gedit psptoolchain/build/newlib-1.15.0/build-psp/psp/newlib/Makefile
```

Scroll down till you find a line simular to this:

MAKEINFO = /home/xxzeroxx/Public/psptoolchain/build/newlib-1.15.0/missing makeinfo --split-size=5000000 

replace the entire line with this:

MAKEINFO = makeinfo

save and close the window and it should jump back to the terminal. (if it doesnt just open a new terminal)

Now do the following.

```
cd psptoolchain/build/newlib-1.15.0/build-psp/psp/newlib/
make
sudo make install
cd ~/psptoolchain/scripts/
sudo rm 004-newlib-1.15.0.sh
cd ~/psptoolchain/
sudo ./toolchain.sh
```

and hopefully that will fix it!!

---

### Post by xXZeroXx on 2008-11-05
```
xxzeroxx@L-desktop:~/psptoolchain$ sudo ./toolchain.sh
[sudo] password for xxzeroxx: 
ERROR: Set $PSPDEV before continuing.
../depends/check-pspdev.sh: Failed.
```

That is what I get

---

### Post by ajtaggs on 2008-11-05
That is strange, it is the same error you got at the start of the thread. It means your login script has been changed back to default... No worries, I have an easier way of editing it this time.

```
sudo gedit .bashrc
```

This will bring up your login script in a new window. Just scroll down to the very bottom of the file and make sure these lines are still there:

```
export PSPDEV=/usr/local/pspdev
export PATH=$PATH:$PSPDEV/bin 
```

If they aren't, type them in that order(or just copy and paste). Dont forget to save, then close that window. 

Go back to your terminal or get a new one, and try this:

```
. .bashrc
cd psptoolchain
sudo ./toolchain.sh
```

Good luck :)

---

### Post by xXZeroXx on 2008-11-05
I checked that before I posted, sorry for not telling that to you.
Yup, the lines are still there.
```
xxzeroxx@L-desktop:~$ sudo gedit .bashrc
[sudo] password for xxzeroxx: 
xxzeroxx@L-desktop:~$ . .bashrc
xxzeroxx@L-desktop:~$ 
xxzeroxx@L-desktop:~$ cd psptoolchain
xxzeroxx@L-desktop:~/psptoolchain$ sudo ./toolchain.sh
ERROR: Set $PSPDEV before continuing.
../depends/check-pspdev.sh: Failed.
xxzeroxx@L-desktop:~/psptoolchain$ 
```

This is what I get, the same as before, just as if I haven't done anything to it.

This is my .bashrc
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

export PSPDEV=/usr/local/pspdev
export PATH=$PATH:$PSPDEV/bin
```

As you can see they have always been there but, I still get the same error.

---

### Post by ajtaggs on 2008-11-05
Try logging out and logging back in. That will force your login script to run. Then try the ./toolchain.sh again.

---

### Post by xXZeroXx on 2008-11-05
> **ajtaggs said:**
> Try logging out and logging back in. That will force your login script to run. Then try the ./toolchain.sh again.

No, nothing happens, same error, you know, I¡m getting tiredfrom this, I believe my computer hates me, BTW THANKS for all the help.
Let's see if we can solve this.:lolflag:

---

### Post by ajtaggs on 2008-11-05
OK, well we can make sure your download of psptoolchain is not currupt and is up to date.

try this:

```
cd /tmp
svn checkout svn://svn.pspdev.org/psp/trunk/psptoolchain
cd psptoolchain
sudo ./toolchain.sh
```

---

### Post by xXZeroXx on 2008-11-05
```
xxzeroxx@L-desktop:~$ cd /tmp
xxzeroxx@L-desktop:/tmp$ svn checkout svn://svn.pspdev.org/psp/trunk/psptoolchain
A    psptoolchain/toolchain-sudo.sh
A    psptoolchain/depends
A    psptoolchain/depends/check-gcc.sh
A    psptoolchain/depends/check-texinfo.sh
A    psptoolchain/depends/check-make.sh
A    psptoolchain/depends/check-autoconf.sh
A    psptoolchain/depends/check-flex.sh
A    psptoolchain/depends/check-patch.sh
A    psptoolchain/depends/check-subversion.sh
A    psptoolchain/depends/check-pspdev.sh
A    psptoolchain/depends/check-ncurses.sh
A    psptoolchain/depends/check-gmp.sh
A    psptoolchain/depends/check-readline.sh
A    psptoolchain/depends/check-mpfr.sh
A    psptoolchain/depends/check-automake.sh
A    psptoolchain/depends/check-wget.sh
A    psptoolchain/depends/check-bison.sh
A    psptoolchain/patches
A    psptoolchain/patches/gdb-6.4-PSP.patch
A    psptoolchain/patches/gdb-6.8-PSP.patch
A    psptoolchain/patches/gcc-4.1.0-PSP.patch
A    psptoolchain/patches/insight-6.4-PSP.patch
A    psptoolchain/patches/binutils-2.16.1-PSP.patch
A    psptoolchain/patches/gcc-4.3.1-PSP.patch
A    psptoolchain/patches/newlib-1.15.0-PSP.patch
A    psptoolchain/scripts
A    psptoolchain/scripts/003-pspsdk-stage1.sh
A    psptoolchain/scripts/007-gdb-6.8.sh
A    psptoolchain/scripts/001-binutils-2.16.1.sh
A    psptoolchain/scripts/006-pspsdk-stage2.sh
A    psptoolchain/scripts/002-gcc-4.3.1-stage1.sh
A    psptoolchain/scripts/008-insight-6.4.sh
A    psptoolchain/scripts/009-psplinkusb.sh
A    psptoolchain/scripts/004-newlib-1.15.0.sh
A    psptoolchain/scripts/005-gcc-4.3.1-stage2.sh
A    psptoolchain/toolchain.sh
A    psptoolchain/readme-ubuntu.txt
A    psptoolchain/readme.txt
 U   psptoolchain
Revisión obtenida: 2441
xxzeroxx@L-desktop:/tmp$ cd psptoolchain
xxzeroxx@L-desktop:/tmp/psptoolchain$ sudo ./toolchain.sh
[sudo] password for xxzeroxx: 
ERROR: Set $PSPDEV before continuing.
../depends/check-pspdev.sh: Failed.
xxzeroxx@L-desktop:/tmp/psptoolchain$ 
```

The same thing happens.

---

### Post by ajtaggs on 2008-11-05
I have no idea what could be wrong here, lets try a little script:

right click on you desktop, point to new Document, and click empty file. Name it psp.sh. Then open it and paste this into it:


```
if ( ! grep '$PSPDEV' ~/.bashrc > /dev/null 2>&1 ); then
echo "export PSPDEV=/usr/local/pspdev" >> ~/.bashrc
echo 'export PATH=$PATH:$PSPDEV/bin' >> ~/.bashrc
fi
export PSPDEV=/usr/local/pspdev
export PATH=$PATH:$PSPDEV/bin
cd /tmp
svn checkout svn://svn.pspdev.org/psp/trunk/psptoolchain
cd psptoolchain
./toolchain.sh
```

Save and close it. Then right-click it and click properties, click the permissions tab, and check the "allow executing file as program" check box. Close the properties window and open a terminal. Then type the following:

```
cp Desktop/psp.sh psp.sh
sudo ./psp.sh
```

---

### Post by xXZeroXx on 2008-11-11
It finally Worked!!!
Hurray it worked!!!
Just one last thing, what do I do from here, how do I run it?

---

### Post by ajtaggs on 2008-11-11
Well, you run it by first writing a program, then writing a make file, then typing make. If I where you I'd look for a tutorial to help get started. 

This one looks good, just skip Lesson 1 becuase you already set it up.

[http://www.psp-programming.com/tutorials/c/lesson02.htm](http://www.psp-programming.com/tutorials/c/lesson02.htm)

---

### Post by xXZeroXx on 2008-11-11
> Well, you run it by first writing a program, then writing a make file, then typing make. If I where you I'd look for a tutorial to help get started.

This one looks good, just skip Lesson 1 becuase you already set it up.

[http://www.psp-programming.com/tutorials/c/lesson02.htm](http://www.psp-programming.com/tutorials/c/lesson02.htm)

Yeah, this is what I was exactly looking for, thanks.
A lot of thanks, Thank You for all of your patience.

---

### Post by ajtaggs on 2008-11-12
No problem :), just gald we could make it work!!

---

