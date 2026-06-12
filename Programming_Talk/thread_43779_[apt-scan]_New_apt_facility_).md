---
title: "[apt-scan] New apt facility :)"
date: 2005-06-23
forum: Programming Talk
---

### Post by globe_trotter on 2005-06-23
Hi all, i've build a new tool...
i don't know if this is the right place to talk about it,
if it isn't, sorry  :razz: 

i'm not so good in english, so i'll show details..:

If you perform a search for a file with apt-cache search.. it's not sure you will find the package..
user@host: apt-cache search dos2unix
[EMPTY]

So i wrote this simply, silly, useful (for me) code that makes query for the packages.ubuntu.com...

It has default searchs or advanced searchs.. can give html output or human readable output
(as u can see below)

user@host: apt-scan dos2unix
usr/bin/dos2unix                                            utils/sysutils


Surely if there will be changes to the answer layout, then the human readable output will need a fix... 


License GPL of course..

Suggestion and critics are wellcome

Cya :)

EDIT: quit stupid... i forgot the link  :grin:  :grin: 

[http://ecataldi.web.cs.unibo.it/free/code/apt-scan-1.0.tar.bz2](http://ecataldi.web.cs.unibo.it/free/code/apt-scan-1.0.tar.bz2)

---

### Post by Trojan1313 on 2005-06-23
Nice tool, I like it. :)

---

### Post by globe_trotter on 2005-06-23
Thanks man :)

---

### Post by skoal on 2005-06-23
yeah, apt-cace search never really worked well for me (probably since I don't know how to use it effectively).  Anyways, I find 'dpkg -l |grep <keyword>' seems more reliable and effective.  Thanks for the script.  I'll give it a shot and see how it compares with the other 2 methods I traditionally use. 

\\//_

---

### Post by globe_trotter on 2005-06-23
Hi :)
This is just to understand if i've missed something about dpkg -l

I tought dpkg -l gives you a list of files wich names match the regexp...
While apt-scan search wich package contains a file named exactly has the given parameter...

If i'm in wrong or i misunderstood your post, please let me know  ;-) 
Byez all

---

### Post by LordHunter317 on 2005-06-23
I'm not sure what this tool was meant to do.

If it's meant for searching for files in installed packages, dpkg -S does that. 

If it's meant for seraching for files in uninstalled packages, apt-file does that.

'dpkg -l' gives a list of every package that dpkg knows about.  This includes installed packages, packages uninstalled but not purged, packages not fully installed, and ocassionally some uninstalled packages (usually virtual ones related to installed software).  It doesn't give you a complete list of what's available for installation, only apt-cache can do that.

---

### Post by skoal on 2005-06-23
Ooops! I thought it was a script, but it's actually a binary from compiled source.  Anyways, I tried it out and it seems kind of handy.  Great work!  From my understanding of the output, it looks like it returns the repository of a package based on a keyword, but doesnt return the package name? Right? I did a simple little search for any packages with 'headers' (ie. kernel headers, dev headers, etc) but got this...
```
skoal@morpheus:///tmp/apt-scan-1.0/src $ ./apt-scan headers
usr/lib/GNUstep/System/Library/Frameworks/AddressView.framework/Headers libs/addressview.framework universe
usr/lib/GNUstep/System/Library/Frameworks/Addresses.framework/Headers libs/addresses.framework universe
usr/lib/GNUstep/System/Library/Frameworks/FSNode.framework/Headers x11/gworkspace.app universe
usr/lib/GNUstep/System/Library/Frameworks/GuiImageKit.framework/Headers libs/gnustep-imagekits-gui universe
usr/lib/GNUstep/System/Library/Frameworks/PDFKit.framework/Headers libs/gnustep-imagekits-pdf universe,libs/pdfkit.framework universe
usr/lib/GNUstep/System/Library/Frameworks/Postgres95EOAdaptor.framework/Headers libs/gnustep-dl2 universe
usr/lib/GNUstep/System/Library/Frameworks/ProjectCenter.framework/Headers devel/projectcenter universe
usr/lib/GNUstep/System/Library/Frameworks/StepTalk.framework/Headers libs/steptalk universe
usr/lib/GNUstep/System/Library/Frameworks/TalkSoupBundles.framework/Headers net/talksoup.app universe
usr/lib/GNUstep/System/Library/Frameworks/netclasses.framework/Headers libs/gnustep-netclasses universe
usr/share/wims/modules/tool/analysis/function.fr/headers    web/wims-modules-fr universe
```
By the way, I think you'll need a second release...
```

skoal@morpheus:///tmp/apt-scan-1.0/src $ ./apt-scan header
Segmentation fault
```
oops! I do have a tendency to break things.  I haven't really tried to track down the source of that error, but i was just trying to refine my search a bit (from the prior one).

\\//_

---

### Post by globe_trotter on 2005-06-23
Ahaha.. i missed apt-file  :-) 
That's right  :razz: 
Also i saw apt-file does a deeper search, while apt-scan does exact match...

Other difference is that you can use apt-file locally, whitout network use...
It downloads something like 8MB when you update it, and then perform searches on the database...

In the other front you need network, becouse it only does query to the packages.ubuntu.com
doesn't need database, but has i see it is faster than apt-file...

user@host:~$ time apt-file search dos2unix
[CUT]
real    0m5.849s
user    0m3.836s
sys     0m0.221s

user@host:~$ time apt-scan dos2unix
[CUT]
real    0m0.901s
user    0m0.000s
sys     0m0.003s


And also whit -a option, you can choose between searches for more architecturs, version of ubuntu, case sensitive, and if searchin for different kind of searchs...

Maybe if i knowed apt-file before this silly code, i wouldn't develop it...
However, that's it, now everyone could have this 2 choiche for this kind of query...

---

### Post by globe_trotter on 2005-06-23
[QUOTE=skoal]
```
skoal@morpheus:///tmp/apt-scan-1.0/src $ ./apt-scan headers
usr/share/wims/modules/tool/analysis/function.fr/headers    web/wims-modules-fr universe
```
By the way, I think you'll need a second release...
[/QUOTE]
It should be the 2nd field, in this case wims-modules-fr.. as the output from packages.ubuntu.com

[QUOTE=skoal]
```

skoal@morpheus:///tmp/apt-scan-1.0/src $ ./apt-scan header
Segmentation fault
```
oops! I do have a tendency to break things.  I haven't really tried to track down the source of that error, but i was just trying to refine my search a bit (from the prior one).
[/QUOTE]

Uhm... that's new for me...
tomorrow i'll give a look at it.....

Thanks  :smile:  :smile:

---

### Post by globe_trotter on 2005-06-23
Fixed... new src is at
[http://ecataldi.web.cs.unibo.it/free/code/apt-scan-1.1.tar.bz2](http://ecataldi.web.cs.unibo.it/free/code/apt-scan-1.1.tar.bz2)

I forgot to update a char * and on long answer from the server, it update the int size,
but not the answer pointer  :) 

Cya  ;-)

---

### Post by globe_trotter on 2005-06-26
Hi all, i fixed another bug...
apt-scan -a with the 4th kind of search gives SIGSEGV for a missing string comparison..
fixed it on atp-scan-1.2.tar.bz2... Hope is the last fix..
Byez

---

### Post by globe_trotter on 2005-06-27
Uhmm.. that wasn't the last bug fix..
cut&paste error in cli.c on argument parsing...

added a parameter -u || --check-update wich checks the last version available... (Since i would like to close this thread)

Also, with -a argument you can however specify the package name in command line...


Cya and have a good day...
(I'll not go on with this thread... byez  :razz: )

EDIT:
[http://ecataldi.web.cs.unibo.it/free/code/apt-scan-1.3.tar.bz2](http://ecataldi.web.cs.unibo.it/free/code/apt-scan-1.3.tar.bz2)

---

