---
title: "Howto: Install emacs-snapshot 22.0.5 with gtk2 under Ubuntu 5.10 (Breezy)"
date: 2005-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2005-11-08
I love emacs, but have had some display problems with the emacs that comes with Breezy. I have built emacs-snapshot debs for Breezy from the Dapper archive. This version has some new features, including gtk2.

**Changes:**
[LIST]
[*]11-Nov-05: Rebuilt from Dapper archive.
[/LIST]

1. Get Files:
```
wget -c http://mikesplanet.net/deb/dictionaries-common_0.62.3ubuntu1~breezy_all.deb
wget -c http://mikesplanet.net/deb/emacs-snapshot-bin-common_20051103-1~breezy_i386.deb
wget -c http://mikesplanet.net/deb/emacs-snapshot-common_20051103-1~breezy_all.deb
wget -c http://mikesplanet.net/deb/emacs-snapshot-el_20051103-1~breezy_all.deb
wget -c http://mikesplanet.net/deb/emacs-snapshot-gtk_20051103-1~breezy_i386.deb
```
2. Uninstall emacs21 (if needed):
```
sudo apt-get remove emacs21
```
3. Install emacsen-common:
```
sudo apt-get install emacsen-common
```
4. Install dictionaries-common:
```
sudo dpkg -i dictionaries-common_0.62.3ubuntu1~breezy_all.deb
```
5. Install emacs-snapshot:
```
sudo dpkg -i emacs-snapshot_20051103-1~breezy_i386.deb emacs-snapshot-bin-common_20051103-1~breezy_i386.deb emacs-snapshot-common_20051103-1~breezy_all.deb emacs-snapshot-el_20051103-1~breezy_all.deb emacs-snapshot-gtk_20051103-1~breezy_i386.deb

```

Let me know if you have any issues,
Mike

---

### Post by realwhz on 2005-11-11
Excellent!  Thanks :KS

---

### Post by majikstreet on 2005-11-11
I was unable to install this, but it doesn't matter to me anyway :P

One issue I ran into was that there was no "emacs-snapshot_20051103-1~breezy_i386.deb" downloaded!

I would also suggest changing your wget commands to:
```

wget -c http://mikesplanet.net/deb/dictionaries-common_0.62.3ubuntu1~breezy_all.deb http://mikesplanet.net/deb/emacs-snapshot-bin-common_20051103-1~breezy_i386.deb http://mikesplanet.net/deb/emacs-snapshot-common_20051103-1~breezy_all.deb http://mikesplanet.net/deb/emacs-snapshot-el_20051103-1~breezy_all.deb http://mikesplanet.net/deb/emacs-snapshot-gtk_20051103-1~breezy_i386.deb

```

Anyway, it does _not_ matter to me, as I like vi :P


EDIT: And guess what? I was about to remove all the files that I downloaded and start over, and of course lucky me, I ran rm -rf * while in my home directory... *DOH* Luckly I caught it before it deleted too much- I dunno how much I deleted though, but I'll live :P


EDIT#2: I just was able to install it. Aaaaaand guess what? It's GTK2! Looks better than the whatever default is!

---

### Post by Spudgun on 2005-11-11
Worked for me, cheers.

---

### Post by bored2k on 2005-11-11
Mike, your apps need screenshots at the end of the guides :D !

---

### Post by kaamos on 2005-11-11
Some problems with the filenames, but got it installed. And looks great! Always disliked the way emacs used to look..

---

### Post by majikstreet on 2005-11-11
[QUOTE=bored2k]Mike, your apps need screenshots at the end of the guides :D ![/QUOTE]
I agree...


Mike, how do you do this????

---

### Post by Donovan on 2005-11-15
I get to install it and run it but while I install it i get these errors:

```
Loading 52semantic (source)...
Error while loading 52semantic
Wrote /etc/emacs-snapshot/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs-snapshot/site-lisp/debian-startup.elc

Se encontraron errores al procesar:
 emacs-snapshot_20051103-1~breezy_i386.deb

```

Last one is obvious since the instructions dont say anything about downloading that .deb. But downloaded it to test (from Mike's Page with wget) and I get even more errors. 

Are these warnings normal?

---

### Post by art on 2005-12-08
Mike I am having the following problem. Whenever I start a new file from command line, lets say emacs a.cxx, emacs loads and stays on the splash screen, and it says to do "Ctrl I" to start editing the file. I attach a screenshot. This wasn't the case with the old emacs? Do you know how to make it start at edit mode from the beginning? 
Thanks a lot!

---

### Post by N8K99 on 2005-12-22
Maybe it was just me but, I just followed teh directions at [http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian](http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian) and installed emacs-snapshot and it's beautiful!! so much better than the old version! Wow! Thanks to who ever made that!:razz:

---

### Post by viscount on 2005-12-26
[QUOTE=N8K99]Maybe it was just me but, I just followed teh directions at [http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian](http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian) and installed emacs-snapshot and it's beautiful!! so much better than the old version! Wow! Thanks to who ever made that!:razz:[/QUOTE]

Do you need to add a server to your /etc/apt/sources.list ?
$ sudo apt-get install emacs-snapshot-gtk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package emacs-snapshot-gtk
$

---

### Post by N8K99 on 2005-12-27
[QUOTE=viscount]Do you need to add a server to your /etc/apt/sources.list ?
$ sudo apt-get install emacs-snapshot-gtk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package emacs-snapshot-gtk
$[/QUOTE]It's very possible that there needs to be a change to your /etc/apt/sources.list. My list is quite altered as I have installed enlightenment from several places as well as skype and OOo2. Incidentially, when I installed emacs-snapshot my OpenOffice2.0 suite was removed. I don't mind as I use the other computer or that sort of stuff but someone who is not in the same position may find that this is undesirable. Perhaps there is a workaround. Someone?

---

### Post by i.herteleer on 2006-02-03
Hmm... the installation seems to have worked fine, but when i try running emacs snapshot, nothing happens... (Its listed in Applications -> Accessories by the way)
Thanks, 
Inti

---

### Post by hyg53 on 2006-02-07
Great, exactly was I was looking for
Off course,  remove emacs-snapshot_20051103-1~breezy_i386.deb in the dpkg -i and it works well

---

### Post by tadelste on 2006-02-16
I'm getting an error that makes little sense to me. 

When I attempt to start emacs I get:


No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1'

I would appreciate any one helping.

Thanks in advance.

---

### Post by jaypipes on 2006-02-27
I also am having issues getting *any* font to be recognized.   Simply says No fonts matched for anything I try...  Help would be most appreciated.  Thanks.

---

### Post by parktownprawn on 2006-02-27
[QUOTE=tadelste]
When I attempt to start emacs I get:


No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1'

[/QUOTE]

try installing the jmk fonts

```
sudo apt-get install xfonts-jmk
```

---

### Post by 3ntity on 2006-02-27
Installing these fonts did not help, i still get the same error (No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1')...
Any further suggestions?
Cheers

---

### Post by parktownprawn on 2006-02-27
you may need to restart gnome or rebuild your font cache - i think you need to type
```
sudo fc-cache -f -v
```
but I could be wrong

---

### Post by 3ntity on 2006-02-27
Still no success :S

---

### Post by 3ntity on 2006-02-27
I think i have some other problems in Ubuntu, since Add Applications doesn't work... Should i reinstall ubuntu or something of the kind? Or any other suggestions you might have?

---

### Post by parktownprawn on 2006-02-27
[QUOTE=3ntity]I think i have some other problems in Ubuntu, since Add Applications doesn't work... Should i reinstall ubuntu or something of the kind? Or any other suggestions you might have?[/QUOTE]

It may be that something  in your old preferences is causing problems with the new emacs. 

Try
```
mv ~/.emacs ~/.emacs.old
```
and see what happens when you run emacs

As for problems with Add Applications - could you be more specific?

Perhaps you should start a new thread detailing the problem with Add Applications.

---

### Post by jazzgossen on 2006-12-12
> **art said:**
> Mike I am having the following problem. Whenever I start a new file from command line, lets say emacs a.cxx, emacs loads and stays on the splash screen, and it says to do "Ctrl I" to start editing the file. I attach a screenshot. This wasn't the case with the old emacs? Do you know how to make it start at edit mode from the beginning? 
Thanks a lot!

Did you ever find a solution to this? I'm annoyed by this behaviour, too.

---

### Post by kaamos on 2006-12-12
Add
```

(setq inhibit-startup-message t)

```
to your ~/.emacs

---

