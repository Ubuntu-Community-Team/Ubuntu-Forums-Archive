---
title: "Python Modules Question"
date: 2008-01-29
forum: Programming Talk
---

### Post by y-lee on 2008-01-29
I need the follwing three python modules to help me resolve an issue I'm having trying to compile a program, see  [Music applet - configure warnings]("http://ubuntuforums.org/showthread.php?t=680872") 

[LIST]
[*]pynotify
[*]gnomekeyring
[*]xmmsclient
[/LIST]

Where can  I find these modules and how do I install them? Can they be found in the repos and if so what are they called? Be aware I am using Dapper Drake and reverted back to Python 2.4.3. Any help would be appreciated.

Edit Sorry i put this in the wrong spot. I meant to put it in programming.

---

### Post by LaRoza on 2008-01-30
> Edit Sorry i put this in the wrong spot. I meant to put it in programming.

You should have reported it, I just noticed it. Hopefully it will resolved soon :)

---

### Post by pmasiar on 2008-01-30
> **y-lee said:**
> I am using Dapper Drake and reverted back to Python 2.4.3..

Check with applet author if s/he tested applet in ubuntu, and if, in what version. Dapper Drake is stable == not cutting edge.

---

### Post by deuce868 on 2008-01-30
Usually you can find them by doing a search in apt. 

```

$ apt-cache search python | grep notify
python-notify - Python bindings for libnotify
gmail-notify - A Gmail Notifier
python-pyinotify - Simple Linux inotify Python bindings
python-pyinotify-doc - Simple Linux inotify Python bindings

```

and 

```

$ apt-cache search python | grep xmms
python-xmms - Python interface to XMMS
python-xmms-doc - Python interface to XMMS (documentation)
python-xmmsclient - XMMS2 - Python bindings
pyxmms-remote - command-line interface to XMMS

```

The libraries in apt are generally python-$SOMETHING

Now as to the keyring, not sure what that is under.

---

### Post by y-lee on 2008-01-30
> **pmasiar said:**
> Check with applet author if s/he tested applet in ubuntu, and if, in what version. Dapper Drake is stable == not cutting edge.

Already have been in touch with the developer he is using Debian tho he didn't state which version. Also note he is using Python 2.4.*.   He has not tested this applet with Dapper tho he ***claims*** it should ***be possible*** to get it to work with Dapper. He has however been successful in me reducing the errors to just these three, regardless tho the program will not compile, i get multiple errors when I try to **make** it.

**deuce868**, thanks for the  tip but i was already aware of how to use apt-cache and searched everything i could think of and installed everything seemingly needed:

```
apt-cache search python | grep notify
gmail-notify - gmail new mail notifier
```


```
apt-cache search python | grep xmms
python-xmms - Python interface to XMMS
python-xmms-doc - Python interface to XMMS (documentation)
python2.3-xmms - Python interface to XMMS (Python 2.3 version)
python2.4-xmms - Python interface to XMMS (Python 2.4 version)
pyxmms-remote - command-line interface to XMMS
```

> Now as to the keyring, not sure what that is under. 

The developer told me in an e-mail that the python module is found in **python-gnome2-desktop** in Debian.

```
apt-cache search python | grep python-gnome2
python-gnome2-extras-doc - Python bindings for the GNOME desktop environment - documentation
python-gnome2 - Python bindings for the GNOME desktop environment
python-gnome2-desktop - Python bindings for the GNOME desktop environment
python-gnome2-desktop-dev - Python bindings for the GNOME desktop environment
python-gnome2-desktop-doc - Python bindings for the GNOME desktop environment - documentation
python-gnome2-dev - Python bindings for the GNOME desktop environment
python-gnome2-extras - Python bindings for the GNOME desktop environment
python-gnome2-extras-dev - Python bindings for the GNOME desktop environment
```

As I have installed the packages I seemed to need including the **dev** stuff, It appears to me at this point  that **python-notify** for example was added to[ Edgy ]("http://packages.ubuntu.com/cgi-bin//search_contents.pl?version=edgy&arch=i386&case=insensitive&word=python-notify&searchmode=filelist") but [*is not found in Dappe*r]("http://packages.ubuntu.com/cgi-bin//search_contents.pl?version=dapper&arch=i386&case=insensitive&word=python-notify&searchmode=filelist").

I posted here because at first I thought I could just find these python modules and add them to solve this problem, I don't know alot about python, but now it seems more likely Dapper just doesn't support the functions needed by this program. The version of **python-notify** found in edgy, for example, relies on ** libnotify1 (>= 0.4.0-1)** and dapper has only **[libnotify1 (0.3.2-0ubuntu4)]("http://packages.ubuntu.com/dapper/libs/libnotify1")**

Sadly, I am about to conclude that without upgrading ubuntu to at least Edgy I will unable to use this program :(

My thanks tho to you both for trying!

---

