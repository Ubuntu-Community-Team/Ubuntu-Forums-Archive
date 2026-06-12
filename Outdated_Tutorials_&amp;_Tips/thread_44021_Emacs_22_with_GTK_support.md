---
title: "Emacs 22 with GTK support"
date: 2005-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Manny C on 2005-06-24
Hi Everyone...

I recently moved from Kubuntu to Ubuntu and found that there were no real TeX editors for Gnome. Argggh..

Ever since I started using Linux (about five years ago), I have used Emacs on an on and off basis. So I decided to install emacs, auctex, whizzytex and preview-latex from the repositories. The only problem is that the emacs on the repo is XaW enabled. That is, it looks decidedly crap. 

A Kubuntu friend of mine suggested that since I was using Ubuntu, I should look into [EmacsCVS](http://www.emacswiki.org/cgi-bin/wiki/EmacsFromCVS) and compile it from CVS with Gtk toolkit enabled. 

Here is what I did to successfully compile and install Emacs from CVS:

```

# Need CVS from repositories
sudo apt-get install cvs
# Enable ssh and download sources from CVS anonymously
cd /tmp
CVS_RSH=ssh
export CVS_RSH
cvs -z3 -d:ext:anoncvs@savannah.gnu.org:/cvsroot/emacs co emacs
# Then configure the install path and tell configure to install emacs with gtk
./configure --prefix=/usr --with-x-toolkit=gtk
# Need to rebuild all necessary files before compiling final Emacs binary and then
# complete install
sudo make bootstrap
sudo make install

```

I am not sure if the ```
make bootstrap
``` requires su privileges.

Then type ```
emacs &
``` at a shell and you get....GTK enabled Emacs! :)

See screenshot attached
Now to figure out how to get Whizzytex working...  :???:

---

### Post by GTvulse on 2005-06-24
Installing into /usr was a baaaad idea (tm), because it creates a maintainability problem later on as in removing without trashing your operating system.

Rather you should have intalled into /usr/local (the default) or in /opt/gnu or /opt/emacs and then add the /opt/blah/bin directory to your $PATH, if you decide to follow the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/) or FHS.

Answering your doubts: ```
make bootstrap
``` does not require root privileges, it compiles the initial elisp interpreter and bytecode necessary to dump a miniemacs that will compile the real emacs (that is, emacs  compiles itself). BTW, the version of Xemacs in universe **supports both gtk and gnome**, so that could have been a better choice for you...   :-)

---

### Post by Manny C on 2005-06-24
Looking at [this](http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian), I think install of gtk enabled emacs would be easier.

However, I am getting dependency problems.

---

### Post by Alexander Kirillov on 2005-06-24
You can use Kile under Gnome - this is what I do. Yes, it is a KDE app - but you can use KDE apps in GNOME. The only problem is slightly longer start time.

---

### Post by Manny C on 2005-06-24
Alexander,

How do you manage the large ugly fonts apparent in Kile on Gnome. Do you have to install the KDE base and libraries?

I don't think gtk-qt has helped. 

Kile is a great program, however the look n feel in gnome is putting me off.

---

### Post by Alexander Kirillov on 2005-06-24
[QUOTE=Manny C]Alexander,

How do you manage the large ugly fonts apparent in Kile on Gnome. Do you have to install the KDE base and libraries?

I don't think gtk-qt has helped. 

Kile is a great program, however the look n feel in gnome is putting me off.[/QUOTE]
 I did install kdebase, and a lot of other KDE stuff (kdegraphics, kate, kviewshell, ...). So I fixed the fonts by running K Control Center (kcontrol). After this, the fonts look great - and you only need to do it once.

---

### Post by Manny C on 2005-06-24
Ok...thanks.

---

### Post by Technoviking on 2005-06-25
This page work for me to build my own deb file.
[http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian](http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian)

---

### Post by N8K99 on 2005-12-22
[QUOTE=Mike Basinger]This page work for me to build my own deb file.
[http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian](http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian)[/QUOTE]
so all I do is add this to my /etc/apt/sources.list and then apt-get update/install emacs22?

EDIT: after viewing website- I see the instructions are already there for me!! Although why does OpenOffice2 get removed when I install?

---

