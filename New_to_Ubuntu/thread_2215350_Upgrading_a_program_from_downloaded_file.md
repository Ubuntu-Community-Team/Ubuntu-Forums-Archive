---
title: "Upgrading a program from downloaded file"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by BrianSwatton on 2014-04-06
I'm running Ubuntu Studio 12.04LTS.  I've tried a program via the Ubuntu Software center "KiCad" which works ok, but is quite old.

On the program's website there is a much newer version for this OS.  I've downloaded this .tgz file and extracted it to another folder in my home folder. I find I can run the new program as is, by going into it's bin drectory and running the program from there.

Is that it installed?  Do I need to further integrate it with the OS in some way, like with dpkg or apt-get or something?

The applications menu still brings up the old version of course.  Should I just change the launcher there to point at the new program?

I'm still a bit unclear on how programs have to tie in with the system in linux.

---

### Post by 23dornot23d on 2014-04-06
The PPA would probably have been the better method ........ but if you have it running now then you should just be able to run
it from the launcher by changing it to point to the new running version that you have.

[http://www.kicad-pcb.org/display/KICAD/Download](http://www.kicad-pcb.org/display/KICAD/Download)

```


[COLOR=#ffa500]It is often also better to have uninstalled previous versions before unzipping / untarring and installing as this way can
mix old and new files up ........[/COLOR]

The PPA way ..... but you do not really need this now if you have it installed and running - but this would have been the way I chose as it
ties it back into the package manager ........ and would have upgraded the system in a more controlled way - saying that - there
is nothing wrong with how you have it installed at the moment ..... and running it should be just a case of pointing the launcher
to the new executable file you installed.

[https://code.launchpad.net/~js-reynaud/+archive/ppa-kicad](https://code.launchpad.net/~js-reynaud/+archive/ppa-kicad)


```

Added the link to the ppa ..... but its probably not needed as the install was done manually ....

---

### Post by BrianSwatton on 2014-04-06
Thanks very much, you've answered my main question nicely.

I did try the linux and, I think, the Ubuntu PPA scripts on the KiCad download page, but they kept stopping, asking for bzr launchpad name and ID info. I had no idea what launchpad was, or what the ID would be.  I don't know what PPA is yet, I wondered if these links were for later OS than mine.

So, I went via the repository link underneath and downloaded from there.  I thought I'd end up with something I'd need to dpkg.

Anyway thanks again, it's all helping me gain understanding.

---

### Post by 23dornot23d on 2014-04-06
> 
I did try the linux and, I think, the Ubuntu PPA scripts on the KiCad  download page, but they kept stopping, asking for bzr launchpad name and  ID info. I had no idea what launchpad was, or what the ID would be.  I  don't know what PPA is yet, I wondered if these links were for later OS  than mine.


Launchpad is where most of the things go on to do with developers - bug reports - programs - database etc .......

I created a login there to at first get more involved with some of the things that go on in the background - tend to end up
in there when testing things out - as bug reports can be made or as you have noticed ppa's can be added

The ppa's are programmers repositories of programs that can be used to help others or themselves ..... but the times I 
use them ..... its to get things that are more uptodate or things that I cannot get through the normals methods

1 ..... USC ( Ubuntu Software Centre )
2 ..... Synaptic ( Older package manager that most people used before USC came on the scene )
3 ..... Muon ( not so sure about this one as I cannot remember when this was needed in my own case )
4 ..... sudo aptitude
5 ..... sudo apt-get
6 ..... installation by unzipping / untarring and running files from a directory the user creates
7 ..... sudo dpkg
8 ..... installation by compiling and make cmake etc ......


There are others - but above are the main ones that I have come across and use ......... but that list above would be my order in choosing how
to go about installing things .......

Its only my own order ........ and usually I stick to one method ....... which in my own personal case is to use aptitude - but its only because 
through the long term - this has served my purposes the best and kept my systems running without getting into dependency problems - but it
like most things in Linux works better when the user gets familiar with it ........

Hope something else here is of use ......... but everyone has there own personal preferences to what suits them and their own
way of working . 

[COLOR=#ff0000]*None are wrong as far as I know - but some can lead to more problems than answers and long times of pondering*[/COLOR] ;)

---

### Post by BrianSwatton on 2014-04-06
Thanks very much, very helpful indeed.

After your last post, I investigated the ppa and tried that.  I realised I hadn't done that before because I wasn't sure what I was actually doing.  On another machine, I've just added the repo and done an update, and the update manager took over and installed into system.

Progress is being made on many fronts :)

---

### Post by 23dornot23d on 2014-04-06
Good to hear .... hope that your system runs well and the updates and upgrades work without fault for you.

---

### Post by BrianSwatton on 2014-04-06
It's not quite working out unfortunately.  It falls over in the workflow when converting a schematic to pcb.  It fails to find the footprint libraries in /usr/share/kicad/modules, even though they are there.

Having reseached I found this : [http://www.eevblog.com/forum/open-source-kicad-geda/kicad-library-table-generator/](http://www.eevblog.com/forum/open-source-kicad-geda/kicad-library-table-generator/)

There is a table not getting populated with the list of module libraries as it should.  Someone has given a shell script to make a new table from the directory of files, but that doesn't work here.

---

### Post by 23dornot23d on 2014-04-06
sudo apt-get update

sudo apt-get install aptitude

sudo aptitude update

Run the above to update things and put aptitude in place.


Then run this one ( BUT POST BACK WHAT IT SAYS BEFORE ACCEPTING ANYTHING ) just so I can make sure
that its not going to remove anything that you might need ..... answering NO or QUIT will get you back out of it
to post the results ........ its reasonably safe anyway - but it may just come back and say it needs to remove somethings
usually by not accepting it will come back with new options .... often the one option that does not remove things - but just
upgrades is the one that I find is the best to choose )

sudo aptitude safe-upgrade

But answer no and post back what its got on the screen ........ please .........

Any problems just say ...... and we can go from there ...... 

I am just trying to make sure your system is as uptodate as it can
be for 12.04 ......... but as I say we are just investigating at the moment ........

_______________________________________________________________________

As an example doing it on my own system gives back this

> 
keith@keith-laptop:~$ sudo aptitude safe-upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  linux-headers-3.13.0-23{a} linux-headers-3.13.0-23-generic{a} 
  linux-image-3.13.0-23-generic{a} linux-image-extra-3.13.0-23-generic{a} 
The following packages will be upgraded:
  apport apport-gtk libcgmanager0 libruby1.8 linux-generic 
  linux-headers-generic linux-image-generic linux-libc-dev python-apport 
  python-problem-report python-ubuntu-sso-client python3-apport 
  python3-problem-report qemu-common qemu-keymaps ubuntu-sso-client 
  ubuntu-sso-client-qt unity-settings-daemon unity-settings-daemon-dev 
19 packages upgraded, 4 newly installed, 0 to remove and 84 not upgraded.
Need to get 64.6 MB of archives. After unpacking 221 MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
keith@keith-laptop:~$ 



Just answer[COLOR=#ff0000]** n**[/COLOR] .......... and nothing gets changed for now ........ 

or we can track down just the individual things you require ..... 
but I do prefer to work with systems that are  fully up to date first and that is what I am 
trying to ensure before adding other things.


[I]Not changing anything - but would rather do this first than just pick the odd libraries and
things that are just relative to one program ...... ( as we may miss something it also needs )[/I]

---

### Post by BrianSwatton on 2014-04-06
Thanks for that, sorry for delay, I was experimenting (with little success) before I read this

I've just done as you asked, the output from safe-upgrade was :

brian@Office:~$ sudo aptitude safe-upgrade
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

---

### Post by BrianSwatton on 2014-04-06
Weird, kicad does reference the problem I'm having and suggest I read the the documents.  There wasn't any so I used synaptic to add them.  I can't find them though, and kicad crashes when I try access the manual from the menu.

Quite discouraging.  I'm trying to lose my last windows XP machine by finding an alternative to DesignSpark for PCB design.  I don't really want to get into running virtual box or wine, I'd like to leave microsoft behind ideally.

---

### Post by 23dornot23d on 2014-04-06
Ok - I am reading the link you gave ........ kicad and electrics are not my thing .......

[http://www.eevblog.com/forum/open-source-kicad-geda/kicad-library-table-generator/](http://www.eevblog.com/forum/open-source-kicad-geda/kicad-library-table-generator/)

but I will try to understand what is going on with the libraries .... seems there is a place with the latest
but people are complaining about how to use them as they are bringing things in 90 degrees out of place.

With git repositories it is possible to get a clone of the full set of directories - but I cannot see where this
is being explained in that thread ........ maybe needs some more investigations .

Does the other system you upgraded from the PPA show the same problems or is it just the one you
manually upgraded ......... did I get it right that you upgraded 2 systems .......... or are we only on one.

Ok someone has written some python scripts here to clone the libraries ....... 

From this thread in January this year .......
Thread
[http://www.eevblog.com/forum/open-source-kicad-geda/kicad-new-footprint-libraries-%28-pretty%29-packet/](http://www.eevblog.com/forum/open-source-kicad-geda/kicad-new-footprint-libraries-%28-pretty%29-packet/)

Library
[https://github.com/KiCad/kicad-library](https://github.com/KiCad/kicad-library)

Python Scripts
[http://www.eevblog.com/forum/open-source-kicad-geda/kicad-new-footprint-libraries-(-pretty)-packet/?action=dlattach;attach=80613](http://www.eevblog.com/forum/open-source-kicad-geda/kicad-new-footprint-libraries-(-pretty)-packet/?action=dlattach;attach=80613)



but you say you already have the libraries ?

I may have to install this to see what is going on - as I have never used it before Kicad

But you might be as well writing on their Forum too - to explain the problem you are having
meanwhile I will try to work out what is going on from the thread and also from running the
Kicad program to see what it does.

---

### Post by BrianSwatton on 2014-04-06
I have been able to get the docs from site instead.   I can see I will have to construct the table line by line with a tool in the program, it will be a lot of typing.   There  is facility to use 2 environment variables to help reference the files, but I notice that the system one is not getting set by kicad. I wonder if that is why the table didn't get made in the first place.

I'm not sure how to get an environent variable set before a program runs, else I'd try setting it where I'm pretty sure it should point, delete the table and run it again.

I didn't take the first install that far through the work flow to see this problem, it is still on that machine though, so I will go and try, it will take a little while.  I suspect it will be ok because every thing is in my own folder, we'll see.  The program seemed to work, but wasn't installed in a system friendly way.

---

### Post by BrianSwatton on 2014-04-06
The original "wrongly" installed version doesn't have this problem.  I see it is a very different version to what apt-get has put here too, this has a date of Jan 2014, and different visuals.  I see in the documentation that the footprint handling has very recently changed radically.  I'm not sure I have a stable version or the latest in dev on this machine.  The original was 18/5/2013

I'd probably best remove it and start again just with downloading/extracting the 12.04 stable release as I did on the original machine.  I'll put up with it not being integrated into the system if I have to.

Thanks for getting so involved, but please don't feel obliged to. You've been very helpful.

---

### Post by 23dornot23d on 2014-04-06
Ok its installed and runs ok - the help files are there on my system - but I am at the moment in
14.04 32 bit .........

I will outline the procedure I use to see where things can be improved or changed to make
things any easier .....

```

keith@keith-laptop:~$ **sudo add-apt-repository ppa:js-reynaud/ppa-kicad**
 This ppa provide a daily build for KiCad bzr repo (lp:kicad).
 More info: https://launchpad.net/~js-reynaud/+archive/ppa-kicad

Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpc9htigya/secring.gpg' created
gpg: keyring `/tmp/tmpc9htigya/pubring.gpg' created
gpg: requesting key 910F124E from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpc9htigya/trustdb.gpg: trustdb created
gpg: key 910F124E: public key "Launchpad PPA for j2010" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

**sudo apt-get update**


```



then to download the files

and install it .........

```

laptop:~$ sudo aptitude install kicad
The following NEW packages will be installed:
  kicad kicad-common{a} zlib-bin{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 103 not upgraded.
Need to get 38.0 MB of archives. After unpacking 452 MB will be used.
Do you want to continue? [Y/n/?] y
Get: 1 http://fr.archive.ubuntu.com/ubuntu/ trusty/universe zlib-bin i386 1:1.2.8.dfsg-1ubuntu1 [34.5 kB]
Get: 2 http://ppa.launchpad.net/js-reynaud/ppa-kicad/ubuntu/ trusty/main kicad-common all 0.201404050750+4786~12~ubuntu14.04.1 [28.7 MB]
Get: 3 http://ppa.launchpad.net/js-reynaud/ppa-kicad/ubuntu/ trusty/main kicad i386 0.201404050750+4786~12~ubuntu14.04.1 [9,200 kB]
Fetched 38.0 MB in 35s (1,060 kB/s)                                             
Selecting previously unselected package kicad-common.
(Reading database ... 646973 files and directories currently installed.)
Preparing to unpack .../kicad-common_0.201404050750+4786~12~ubuntu14.04.1_all.deb ...
Unpacking kicad-common (0.201404050750+4786~12~ubuntu14.04.1) ...
Selecting previously unselected package zlib-bin.
Preparing to unpack .../zlib-bin_1%3a1.2.8.dfsg-1ubuntu1_i386.deb ...
Unpacking zlib-bin (1:1.2.8.dfsg-1ubuntu1) ...
Selecting previously unselected package kicad.
Preparing to unpack .../kicad_0.201404050750+4786~12~ubuntu14.04.1_i386.deb ...
Unpacking kicad (0.201404050750+4786~12~ubuntu14.04.1) ...
Processing triggers for man-db (2.6.6-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140310-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for python-gmenu (3.0.1-0ubuntu9) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Setting up kicad-common (0.201404050750+4786~12~ubuntu14.04.1) ...
Setting up zlib-bin (1:1.2.8.dfsg-1ubuntu1) ...
Setting up kicad (0.201404050750+4786~12~ubuntu14.04.1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
                                         

Then to run it ...... or choose from the menu system .....

$ kicad


```


[IMG]http://i.minus.com/ibhATYN0DTkwJy.png[/IMG]

> 
The original "wrongly" installed version doesn't have this problem.  I  see it is a very different version to what apt-get has put here too,  this has a date of Jan 2014, and different visuals.  I see in the  documentation that the footprint handling has very recently changed  radically.  I'm not sure I have a stable version or the latest in dev on  this machine.  The original was 18/5/2013


ok interesting .... stable versions are the ones users should use .....

The one from the PPA is this version

[IMG]http://i.minus.com/ibrl4oD25VmfY4.png[/IMG]


Well I have it installed - so if you want to lead me to show me where the problems lie
we could try to work through them - or come back later when you have worked out
which is the better version for you to work with ........

There are always solutions and often if a lot of people are using the programs 
then they soon get addressed .........

---

### Post by BrianSwatton on 2014-04-06
I see in your install that the PPA does say for the daily build, I don't think I should be trying to use that.

I've just searched for kicad a forum but haven't found anything.

To be honest, if you're not familiar with electronics and pcb design it could be pretty long winded to take you through the process to get to the fault.  I'm a very new user to it myself, it works a bit differently to my previous app.

---

### Post by 23dornot23d on 2014-04-06
Ok - maybe its now better on the forum for Kicad where people are familiar with the system.

Installations are better done from the package managers as they can easily be removed

- The - ppa - can be unticked in synaptic - settings - repositories ........ press reload ( top left ) ...... 

Then install the older version if that works better for you ....

Best of luck ..... with whatever you decide to do ..........

---

### Post by BrianSwatton on 2014-04-06
Yes 25 jan 2014 via the ppa here too.  It seems to have problems creating projects too as it can't find the templates, so I had to mess about a bit to get it to start something.  It was when converting a schematic to pcb that the showstopper happened.

It would be nice to get the latest version working if it should be stable, as this new footprint management is coming anyway.

It seems to me there are permissions issues, it doesn't seem to be accessing the files in /usr/share/kicad properly.  This is where the system templates, libraries and modules are that I wish to use. The libraries are read ok in the schematic editor, but in CvPCB I don't get the footprints from the modules. 

In CvPCB there is "Edit Library Tables" under "Preferences".  The table is empty here.  There are two system variables at the bottom of the page : KIPRJMOD and KISYSMOD.  KISYSMOD has nothing in it here.  KYPRJMOD has my home directory.
The variables  can't be set in this dialog.  I'd be interested to know what you have in them there.

---

### Post by 23dornot23d on 2014-04-06
I have the same as you do ...... 

also get this error as going into it

```

Error loading netlist.
IO_ERROR: Cannot open file /home/keith/noname.net for reading.
from /build/buildd/kicad-0.201404050750+4786~12~ubuntu14.04.1/kicad/pcbnew/netlist_reader.cpp : GetNetlistReader() : line 101

```

and

```

No PCB footprint libraries are listed in the current footprint library table.

```

what do you have in the older version though ......

or is that set up in a different manner ........

I will have a quick look at the python scripts that they used for cloning the Git repository

to see if I can make anything of them ...... as you really only seem to need a local library on

your own machine ....... ( what they appear to be doing is making a parts library online )

Which to my own way of thinking is a great idea - as long as they can manage it - and keep
version numbers for each part ...... not deleting old ones ......

Will get back in a bit ....

The first file looks like this .......

```

#!/usr/bin/python

import re, os, sys
import shutil

# change templatedir if you need to
templatedir = '/usr/local/share/kicad/template'

# set localdir to the location where you want to 
# store your local copy of the GitHub repository
localdir = '/usr/local/share/kicad/github-repo'

github_table = 'fp-lib-table.for-github'
sys_table = 'fp-lib-table.for-pretty'
default_table = 'fp-lib-table'

env = {}
env.update(os.environ)
sep = ';' if (re.compile('^[wW][Ii][Nn]').match(sys.platform)) else ':'
KIGITHUB = 'http://github.com/KiCad'

found = None
paths = env['PATH'].split(sep)
for path in paths: 
  fpath = os.path.join(path,'git')
  if (os.path.isfile(fpath) and os.access(fpath, os.X_OK)):
     found = True
     cmd = fpath
     break

if not found: 
  print "cannot find git executable"
  exit(1)

args = ['git', 'clone', 'x']

os.chdir(localdir)

template = os.path.join(templatedir, github_table)
for line in open(template,'rU'): 
    mo = re.search(r'^.*\(\W*uri\W?([^)]*).*$',line)
    if mo:
       repo = mo.group(1).replace('${KIGITHUB}', KIGITHUB)
       args[2]=repo
       print args
       os.spawnve(os.P_WAIT, cmd, args, env)

print "you now have a local copy of the GitHub repository"
print "in : ", localdir 
print "updating KiCad ... "

frompath = os.path.join(templatedir,sys_table)
topath   = os.path.join(env['HOME'],default_table)

print ".. copying: ", frompath
print "......  to: ", topath
shutil.copyfile(frompath, topath)

print ".. done"
print
print "before running kicad, you will need to set" 
print "the following environment variable:"
print
print "KISYSMOD=%s\n" % localdir

```


and the second file looks like this

```

#!/usr/bin/python

import re, os, sys
import shutil

# set localdir to the location where you want to 
# store your local copy of the GitHub repository
localdir = '/usr/local/share/kicad/github-repo'

env = {}
env.update(os.environ)
sep = ';' if (re.compile('^[wW][Ii][Nn]').match(sys.platform)) else ':'

found = None
paths = env['PATH'].split(sep)
for path in paths: 
  fpath = os.path.join(path,'git')
  if (os.path.isfile(fpath) and os.access(fpath, os.X_OK)):
     found = True
     cmd = fpath
     break

if not found: 
  print "cannot find git executable"
  exit(1)

args = ['git', 'pull']

dirs = [x for x in os.listdir(localdir) if os.path.isdir(os.path.join(localdir,x))]

for dir in dirs: 
    print dir,': ',
    sys.stdout.flush()
    os.chdir(os.path.join(localdir, dir))
    os.spawnve(os.P_WAIT, cmd, args, env)


```

---

### Post by BrianSwatton on 2014-04-06
The netlist not found error is probably because one wasn't written from the schematic editor to be read.

The older version doesn't use this "footprint library table" so doesn't suffer.  It also doesn't occupy system directories because of the way I installed it.  You'll probably find the table file in your home directory, "fp-lib-table", with no lib entries in it.  There should be pointers to the files in /usr/share/kicad/modules I would have thought, which is also what I expected to see KISYSMOD set to.   I tried setting it in terminal before running kicad, but it was still empty.

I did see reference to online libraries happening. I wonder why the program installed them in /usr/share/kicad/modules in that case though.

Very confusing.  I have just joined the eev forum.  I'm just wondering quite what to ask lol :)

---

### Post by 23dornot23d on 2014-04-06
Well I did find this - my idea is to get a clone copy of them and then point to them ........ but tried running the 
python programs first which led me to here finding out how others have managed.

```

laptop:~$ ls *.py
clone-kicad-repo.py  update-kicad-repo.py  vidrec3.py
keith@keith-laptop:~$ python clone-kicad-repo.py
Traceback (most recent call last):
  File "clone-kicad-repo.py", line 37, in <module>
    os.chdir(localdir)
OSError: [Errno 2] No such file or directory: '/usr/local/share/kicad/github-repo'


```

Just tested one of the clone commands in my home directory which fetches the kicad library part in
but this is going to get really messy .......... there has to be a better way - and this is not something
users are going to do to build a library up with ..........

-------------------------------------------------------------------------------------------------

So you may get some better answers on that website ....... you joined .........

[B]I do not want to put too much down here as people may try copying and then it will all go
pear shaped for people very quickly ........[/B]

There are many files there and their idea is to keep a central library which is good
and when its set up properly - I guess users will only have the parts they need locally
while the main library keeps all the other many parts that can be retrieved.

Wish we had something like this for other 3d things too ...... it would make modelling a breeze.
---------------------------------------------------------------------------------------------------

```

laptop:~$ git clone https://github.com/KiCad/kicad-library
Cloning into 'kicad-library'...
remote: Reusing existing pack: 5648, done.
remote: Counting objects: 53, done.
remote: Compressing objects: 100% (53/53), done.
remote: Total 5701 (delta 28), reused 0 (delta 0)
Receiving objects: 100% (5701/5701), 68.81 MiB | 988.00 KiB/s, done.
Resolving deltas: 100% (1852/1852), done.
Checking connectivity... done.
Checking out files: 100% (2692/2692), done.


```

So what did other users do ...... mmm

[https://groups.yahoo.com/neo/groups/kicad-users/conversations/topics/16658](https://groups.yahoo.com/neo/groups/kicad-users/conversations/topics/16658)

---

### Post by BrianSwatton on 2014-04-06
Ah.

The template directory says  /usr/_local_/share/kicad in your first file.   That path doesnt exist here, the files are in /usr/share/kicad.

I've no idea about python btw

---

### Post by 23dornot23d on 2014-04-06
Doing a search - someone might have made a easy script to sort this out ....... or left some detailed instructions
about how they went about setting it all up ....... will have a look now ........ as nothing is jumping out at me
as to how to quickly point the program to the files ...... although I did have a look in the directory to see
where the 3d models were ....... then ran thunar to quickly search the directories to see what is in them.

```

laptop:/usr/share/kicad$ ls

internat  library  modules  template

laptop:/usr/share/kicad$ thunar

```

_____________________________________________________________

Some interesting discussions on harvesting parts too - [https://lists.launchpad.net/kicad-developers/msg12807.html](https://lists.launchpad.net/kicad-developers/msg12807.html)
(but not solving the problem you face yet - maybe the users on that site - that already connect to it have the answers)

if it all works then it will be good - just read some reports from people with slower connections saying its a pain for
them though ...... but if everything needed is local and you just switched to the web/git based library when it is
needed then that would be good.

______________________________________________________________

Seems to be a good blog on it here too - [http://www.xess.com/blog/my-first-kicad-board/](http://www.xess.com/blog/my-first-kicad-board/)

[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=kicad+easy+script+access&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=TstBU9XRMYHL5Abt-4CADg&gws_rd=cr#channel=fs&q=kicad+easy+script+access+2014](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=kicad+easy+script+access&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=TstBU9XRMYHL5Abt-4CADg&gws_rd=cr#channel=fs&q=kicad+easy+script+access+2014)

---

### Post by BrianSwatton on 2014-04-06
I seem to get more confused the more I read.  I should have given it a break a while ago,  I had been hoping to get it sorted this weekend.

I need to sleep now, I may not get back to this until tomorrow evening.

Thanks again for your help, don't feel bad if it's more than you want to do to continue, I'm very grateful anyway.

All the best,

Brian

---

### Post by 23dornot23d on 2014-04-06
If it was something that I used on a regular basis it might become more obvious to me
how they have set this up to work .......

I too have been jumping back and forth tonight between a few things - so its not had my full
attention ... 3 or 4 times tonight I swapped back and forth between 32 bit and 64 bit OS's to
do different things ....... so sorry .... sometimes it gets more confusing before it becomes clear.

Someone that knows this program and that has set the latest version up might be more of a help
and that was what I last searched for ...... as I say their own site might be better as its got to
where it is specifically related to how they set those libraries up on the web and link to them.

Other option is as you said earlier - drop back to the older version that works locally ........

That can be done by going into 

synaptic package manager and unticking the ppa repository for kicad

search for kicad - click to remove it ......... then ......

reload the package manager in the top left of synaptic

Search for kicad again ..... in synaptic

and the older version should now be there ..... click on it to install it ........ as that points to the files locally.

I just did a install in 14.04 64 bit version which is the later version of Ubuntu which is due out on the 17th and this was the result below.

( The label says stable too 2013 - July - 07 on the one below ........ )

[IMG]http://i.minus.com/ib1cX6diTQ1Qpu.png[/IMG]

and the search paths shown in that version

[IMG]http://i.minus.com/ihBcHUwvO1qOI.png[/IMG]


Hope you get what you want though. best of luck .... for now I too am going to have a rest of sorts.

---

### Post by BrianSwatton on 2014-04-06
Some success, I couldn't sleep and had an idea.

I was able to construct the fp-lib-table by copying the modules directory to my home, where I could get the slightly modified script to run, (I had earlier swapped ${KISYSMOD} for  /usr/share/kicad/modules and removed the counter as that had stopped it previously.) 

It made a correct table, which I copied to my home.   CvPCB now gets the footprints correctly.

I won't be taking the workflow any further tonight, but it's a major step forward.

---

### Post by 23dornot23d on 2014-04-06
Good to hear - you sound similar to me - I can never sleep with a problem in my head until I have a way forward .... then I jot it down

and come back to it later ........ but you looked for a similar thing to what I had been looking at too ...... ${KISYSMOD}

I have 2 versions now - one at the old july 2013 version and one at the jan 2014 ......... so if you need anything checking like where things

are pointing to just leave a message and I could check them for you ....... 

This sounds good ........

> 
It made a correct table, which I copied to my home.   CvPCB now gets the footprints correctly.



---

### Post by 23dornot23d on 2014-04-06
This was on a earlier link I posted and shows how to get the cloned library ....... but it may not be exactly what you are after
as you may not need all of the parts and everything there ......... but its here should it be any use to you.

Doing the commands from your home directory - will download a complete copy of what they have in the git repos .......
but to keep them uptodate - some more work needs doing ...... this was the link to a yahoo discussion going on about
getting a local copy of the recent files in git

[https://groups.yahoo.com/neo/groups/kicad-users/conversations/topics/16658](https://groups.yahoo.com/neo/groups/kicad-users/conversations/topics/16658)

```

If you want a local copy you will need to clone from the git repository:

1. schematics and 3D models:
git clone [https://github.com/KiCad/kicad-library](https://github.com/KiCad/kicad-library)


2. PCB footprints (new format):
git clone [https://github.com/KiCad/Wire_Pads.pretty](https://github.com/KiCad/Wire_Pads.pretty)
git clone [https://github.com/KiCad/Wire_Connections_Bridges.pretty](https://github.com/KiCad/Wire_Connections_Bridges.pretty)

git clone [https://github.com/KiCad/Valves.pretty](https://github.com/KiCad/Valves.pretty)

git clone [https://github.com/KiCad/Transistors_TO-247.pretty](https://github.com/KiCad/Transistors_TO-247.pretty)

git clone [https://github.com/KiCad/Transistors_TO-220.pretty](https://github.com/KiCad/Transistors_TO-220.pretty)

git clone [https://github.com/KiCad/Transistors_SMD.pretty](https://github.com/KiCad/Transistors_SMD.pretty)

git clone [https://github.com/KiCad/Transformers_SMPS_ThroughHole.pretty](https://github.com/KiCad/Transformers_SMPS_ThroughHole.pretty)

git clone [https://github.com/KiCad/Terminal_Blocks.pretty](https://github.com/KiCad/Terminal_Blocks.pretty)

git clone [https://github.com/KiCad/TantalCapacitors_SMD.pretty](https://github.com/KiCad/TantalCapacitors_SMD.pretty)

git clone [https://github.com/KiCad/SSOP_Packages.pretty](https://github.com/KiCad/SSOP_Packages.pretty)

git clone [https://github.com/KiCad/SOIC_Packages.pretty](https://github.com/KiCad/SOIC_Packages.pretty)

git clone [https://github.com/KiCad/Sockets_WAGO734.pretty](https://github.com/KiCad/Sockets_WAGO734.pretty)

git clone [https://github.com/KiCad/Sockets_PGA.pretty](https://github.com/KiCad/Sockets_PGA.pretty)

git clone [https://github.com/KiCad/Sockets_MOLEX_KK-System.pretty](https://github.com/KiCad/Sockets_MOLEX_KK-System.pretty)

git clone [https://github.com/KiCad/Sockets.pretty](https://github.com/KiCad/Sockets.pretty)

git clone [https://github.com/KiCad/Sockets_Mini-Universal.pretty](https://github.com/KiCad/Sockets_Mini-Universal.pretty)

git clone [https://github.com/KiCad/Sockets_DIP.pretty](https://github.com/KiCad/Sockets_DIP.pretty)

git clone [https://github.com/KiCad/smd_lqfp.pretty](https://github.com/KiCad/smd_lqfp.pretty)

git clone [https://github.com/KiCad/SMD_Packages.pretty](https://github.com/KiCad/SMD_Packages.pretty)

git clone [https://github.com/KiCad/Resistors_Universal.pretty](https://github.com/KiCad/Resistors_Universal.pretty)

git clone [https://github.com/KiCad/Resistors_ThroughHole.pretty](https://github.com/KiCad/Resistors_ThroughHole.pretty)

git clone [https://github.com/KiCad/Resistors_SMD.pretty](https://github.com/KiCad/Resistors_SMD.pretty)

git clone [https://github.com/KiCad/Relays_ThroughHole.pretty](https://github.com/KiCad/Relays_ThroughHole.pretty)

git clone [https://github.com/KiCad/Printtrafo_CHK.pretty](https://github.com/KiCad/Printtrafo_CHK.pretty)

git clone [https://github.com/KiCad/Power_Integrations.pretty](https://github.com/KiCad/Power_Integrations.pretty)

git clone [https://github.com/KiCad/Potentiometers.pretty](https://github.com/KiCad/Potentiometers.pretty)

git clone [https://github.com/KiCad/Pin_Arrays.pretty](https://github.com/KiCad/Pin_Arrays.pretty)

git clone [https://github.com/KiCad/PFF_PSF_PSS_Leadforms.pretty](https://github.com/KiCad/PFF_PSF_PSS_Leadforms.pretty)

git clone [https://github.com/KiCad/Pentawatts.pretty](https://github.com/KiCad/Pentawatts.pretty)

git clone [https://github.com/KiCad/Oscillators.pretty](https://github.com/KiCad/Oscillators.pretty)

git clone [https://github.com/KiCad/Oscillator-Modules.pretty](https://github.com/KiCad/Oscillator-Modules.pretty)

git clone [https://github.com/KiCad/Opto-Devices.pretty](https://github.com/KiCad/Opto-Devices.pretty)

git clone [https://github.com/KiCad/OldSowjetAera_Transistor.pretty](https://github.com/KiCad/OldSowjetAera_Transistor.pretty)

git clone [https://github.com/KiCad/Oddities.pretty](https://github.com/KiCad/Oddities.pretty)

git clone [https://github.com/KiCad/NF-Transormers_ETAL.pretty](https://github.com/KiCad/NF-Transormers_ETAL.pretty)

git clone [https://github.com/KiCad/Muonde.pretty](https://github.com/KiCad/Muonde.pretty)

git clone [https://github.com/KiCad/Mounting_Holes.pretty](https://github.com/KiCad/Mounting_Holes.pretty)

git clone [https://github.com/KiCad/Mechanical_Sockets.pretty](https://github.com/KiCad/Mechanical_Sockets.pretty)

git clone [https://github.com/KiCad/Measurement_Scales.pretty](https://github.com/KiCad/Measurement_Scales.pretty)

git clone [https://github.com/KiCad/Measurement_Points.pretty](https://github.com/KiCad/Measurement_Points.pretty)

git clone [https://github.com/KiCad/LQFP_TQFP_RevA_06Oct2013.pretty](https://github.com/KiCad/LQFP_TQFP_RevA_06Oct2013.pretty)

git clone [https://github.com/KiCad/LEM_HallEffectTransducers_RevA_13Oct2012.pretty](https://github.com/KiCad/LEM_HallEffectTransducers_RevA_13Oct2012.pretty)

git clone [https://github.com/KiCad/LEDs.pretty](https://github.com/KiCad/LEDs.pretty)

git clone [https://github.com/KiCad/Labels.pretty](https://github.com/KiCad/Labels.pretty)

git clone [https://github.com/KiCad/lut.pretty](https://github.com/KiCad/lut.pretty)

git clone [https://github.com/KiCad/IR-DirectFETs.pretty](https://github.com/KiCad/IR-DirectFETs.pretty)

git clone [https://github.com/KiCad/Inductors_NEOSID.pretty](https://github.com/KiCad/Inductors_NEOSID.pretty)

git clone [https://github.com/KiCad/Inductors.pretty](https://github.com/KiCad/Inductors.pretty)

git clone [https://github.com/KiCad/Housings_TO-92.pretty](https://github.com/KiCad/Housings_TO-92.pretty)

git clone [https://github.com/KiCad/Housings_TO-78.pretty](https://github.com/KiCad/Housings_TO-78.pretty)

git clone [https://github.com/KiCad/Housings_TO-50.pretty](https://github.com/KiCad/Housings_TO-50.pretty)

git clone [https://github.com/KiCad/Housings_SOT.pretty](https://github.com/KiCad/Housings_SOT.pretty)

git clone [https://github.com/KiCad/Housings_SOT-89.pretty](https://github.com/KiCad/Housings_SOT-89.pretty)

git clone [https://github.com/KiCad/Housings_SOT-23_SOT-143_TSOT-6.pretty](https://github.com/KiCad/Housings_SOT-23_SOT-143_TSOT-6.pretty)

git clone [https://github.com/KiCad/Housings_SIP9.pretty](https://github.com/KiCad/Housings_SIP9.pretty)

git clone [https://github.com/KiCad/Housings_ROHM.pretty](https://github.com/KiCad/Housings_ROHM.pretty)

git clone [https://github.com/KiCad/Heatsinks.pretty](https://github.com/KiCad/Heatsinks.pretty)

git clone [https://github.com/KiCad/Fuse_Holders_and_Fuses.pretty](https://github.com/KiCad/Fuse_Holders_and_Fuses.pretty)

git clone [https://github.com/KiCad/Footprint_Symbols.pretty](https://github.com/KiCad/Footprint_Symbols.pretty)

git clone [https://github.com/KiCad/Filters_HF_Coils_NEOSID.pretty](https://github.com/KiCad/Filters_HF_Coils_NEOSID.pretty)

git clone [https://github.com/KiCad/Fiducials.pretty](https://github.com/KiCad/Fiducials.pretty)

git clone [https://github.com/KiCad/EuroBoard_Outline.pretty](https://github.com/KiCad/EuroBoard_Outline.pretty)

git clone [https://github.com/KiCad/Divers.pretty](https://github.com/KiCad/Divers.pretty)

git clone [https://github.com/KiCad/Display.pretty](https://github.com/KiCad/Display.pretty)

git clone [https://github.com/KiCad/Discret.pretty](https://github.com/KiCad/Discret.pretty)

git clone [https://github.com/KiCad/Diodes_ThroughHole.pretty](https://github.com/KiCad/Diodes_ThroughHole.pretty)

git clone [https://github.com/KiCad/Diodes_SMD.pretty](https://github.com/KiCad/Diodes_SMD.pretty)

git clone [https://github.com/KiCad/Crystals_Oscillators_SMD.pretty](https://github.com/KiCad/Crystals_Oscillators_SMD.pretty)

git clone [https://github.com/KiCad/Crystals.pretty](https://github.com/KiCad/Crystals.pretty)

git clone [https://github.com/KiCad/Converters_DCDC_ACDC.pretty](https://github.com/KiCad/Converters_DCDC_ACDC.pretty)

git clone [https://github.com/KiCad/Connectors_Serial_MOLEX.pretty](https://github.com/KiCad/Connectors_Serial_MOLEX.pretty)

git clone [https://github.com/KiCad/Connect.pretty](https://github.com/KiCad/Connect.pretty)

git clone [https://github.com/KiCad/CommonModeChoke_Wuerth_Type-WE-CMB_RevA_24Oct2010.pretty](https://github.com/KiCad/CommonModeChoke_Wuerth_Type-WE-CMB_RevA_24Oct2010.pretty)

git clone [https://github.com/KiCad/Choke_Toroid_ThroughHole_RevC_06Aug2010.pretty](https://github.com/KiCad/Choke_Toroid_ThroughHole_RevC_06Aug2010.pretty)

git clone [https://github.com/KiCad/Choke_SMD_RevB_28Dez2012.pretty](https://github.com/KiCad/Choke_SMD_RevB_28Dez2012.pretty)

git clone [https://github.com/KiCad/Choke_Radial_ThroughHole_CD_Bobin_RevA.pretty](https://github.com/KiCad/Choke_Radial_ThroughHole_CD_Bobin_RevA.pretty)

git clone [https://github.com/KiCad/Choke_Axial_ThroughHole_RevB.pretty](https://github.com/KiCad/Choke_Axial_ThroughHole_RevB.pretty)

git clone [https://github.com/KiCad/Capacitors_ThroughHole_RevA.pretty](https://github.com/KiCad/Capacitors_ThroughHole_RevA.pretty)

git clone [https://github.com/KiCad/Capacitors_SMD.pretty](https://github.com/KiCad/Capacitors_SMD.pretty)

git clone [https://github.com/KiCad/Capacitors.pretty](https://github.com/KiCad/Capacitors.pretty)

git clone [https://github.com/KiCad/Capacitors_Elko_ThroughHole.pretty](https://github.com/KiCad/Capacitors_Elko_ThroughHole.pretty)

git clone [https://github.com/KiCad/Buzzer_Beeper_RevA_25Oct2010.pretty](https://github.com/KiCad/Buzzer_Beeper_RevA_25Oct2010.pretty)

git clone [https://github.com/KiCad/BNC-Sockets_RevA.pretty](https://github.com/KiCad/BNC-Sockets_RevA.pretty)

git clone [https://github.com/KiCad/Air_Coils_SML_NEOSID.pretty](https://github.com/KiCad/Air_Coils_SML_NEOSID.pretty)

git clone [https://github.com/KiCad/7Segment_16Sep2013.pretty](https://github.com/KiCad/7Segment_16Sep2013.pretty)


Of course the list is subject to updates and you will have to maintain your own fp-libtables list.


```

(old thread - but I think you wanted to know how to set this ..... but below will only last one session)

They can be exported - or added into a bash script too ......... 

[http://2buntu.com/982/setting-environment-variables-in-linux-using-bash-shell-how-to/](http://2buntu.com/982/setting-environment-variables-in-linux-using-bash-shell-how-to/)

[https://groups.yahoo.com/neo/groups/kicad-users/conversations/topics/16658](https://groups.yahoo.com/neo/groups/kicad-users/conversations/topics/16658)

Note that you can change environment variables right on the command-line:

$ KISYSMOD=/new/path kicad
$ KISYSMOD=/diff/path kicad

This is true for all programs, not just kicad.

---

### Post by BrianSwatton on 2014-04-07
Thanks, I'll look into that later.   I've just found that when I re-ran kicad, those footprints were no longer showing, though the modules list is still there. 

I'll have to read up on github, something else I've not come into contact with before.

I did find out how to set env vars earlier, and did set KISYSMOD from the command line before starting kicad (also from cmd) , within the program the var still seemed to be empty though.

I need to go through the CvPCB.pdf section about this properly, now I have the doc.  I'll post here if/when I work out what to do.

Bleary eyed this morning...

---

### Post by 23dornot23d on 2014-04-07
I found this ...... related links ....... [http://kicadlib.org/Kicad_related_links.html](http://kicadlib.org/Kicad_related_links.html)


Will look through these now - see what is in progress .... and how this all works ....... 
( I may need to do a lot of reading first - was doing a search for a later pdf - the one I found seems to be 2012
[ftp://kicad.r4b.ru/pub/kicad/doc/ru_2012/en/cvpcb.pdf](ftp://kicad.r4b.ru/pub/kicad/doc/ru_2012/en/cvpcb.pdf)
and we can see things have changed in the way they are pointing to the library online in the newer version )

```

Also found this ....... [http://reprap.org/wiki/KiCad](http://reprap.org/wiki/KiCad)

Which led to this ...... [https://code.launchpad.net/kicad](https://code.launchpad.net/kicad)


Will try to keep you uptodate with what I am finding but some of this is just to keep tabs on the things I find

so do not look too deeply into it ......... keep with the setup ........ thats the main thing you need and no doubt

the developers will be working on the problems and sorting them out as we speak ........ seen that the last change

was 15 hours ago ..... so its still active ........


```

There are also some online videos on You-Tube .... what interested me was the Wings3d creation of parts and transfer
into the program Kicad as vrml files ....... on the right hand side of the page there are many other videos to do with
kicad ..... maybe there is one showing how to go about setting up the footprints properly to the only git library.

[http://www.youtube.com/watch?v=93KWoasatkQ](http://www.youtube.com/watch?v=93KWoasatkQ)

Seems a lot of people use this ....... so with its popularity should come more answers - I hope someone online
sees this thread and can add more to it ...... on how the setup to the git library works ........
but so far we have found a way to pull that library down locally - the main thing then is to link to it properly
using their own env variables ...... so it all integrates nicely ....... with no hacking .

---

### Post by BrianSwatton on 2014-04-07
Thanks.

I did get an update last night, though there seems to be no changes, I waited for the 176MB download to find all seems to be as it was, even the date is the same.  Looking at the ppa page it said "Auto Build" rather than giving any changes.  

I need to have a good read later of the docs again and get to grips with the github thing. I have work I need to do at the moment.

---

### Post by 23dornot23d on 2014-04-07
Ok well its dinner time for me too - will come back to it afterwards as it is interesting ...... 

github is used by many people and is a way of managing big projects with a lot of people having

rights to go in and either alter things or control the files in there ...... seems Kicad is making

use of that feature to give them a form of version control and access so people can read and write to it to

build up a bigger library of parts ..... ( which if its easy to link to and keep version control on parts will be good )

Just working out how to link to it properly - or to have a local library of all the parts so far put into it .......

cloning from it is just taking a complete copy / snapshot at a particular time from it .......

if that or pulling from it is done on a regular basis ...... then the files any one user has will reflect the ones on there.


Giving a almost real time way of accessing new parts as they are created by others online .........


ok dinner ......

_____________________________________________________________

I have only used github briefly for another project - so I am not fully uptodate with the way it works

but that is my brief view on what I have seen so far and know about ..... so anyone who knows more

about it please step in and comment - especially the way of linking git to kicad in easy steps ........

Seems to be a plugin - started by reading this

[https://github.com/blairbonnett-mirrors/kicad/blob/master/scripts/library-repos-install.sh](https://github.com/blairbonnett-mirrors/kicad/blob/master/scripts/library-repos-install.sh)

now where is it - and is it completed and how do you add / install into the present updated system

[http://dev.kicad-pcb.org/doxygen/classGITHUB__PLUGIN.html](http://dev.kicad-pcb.org/doxygen/classGITHUB__PLUGIN.html)

Also makes me wonder why they are not installing git as a dependancy ........

My installs so far from the PPA does not bring in git ...... 

**sudo apt-get install git**

now whether they can get to pull from the git repo some other way is not clear yet ....... but it just seems odd

Reading the explanation for use of the plugin though it should be able to point directly to the https website

> 
The fp-lib-table dialog is entered via menu choice "Preferences | Library    Tables". For easy options editing in the current row, click on the "Edit    Options" button. The "Library Path" in the fp-lib-table row for a Github library should be set to the full [https://](https://) URL.
 For example:
         [https://github.com/liftoff-sr/pretty_footprints](https://github.com/liftoff-sr/pretty_footprints)
   This is typically
         [https://github.com/user_name/repo_name](https://github.com/user_name/repo_name)
    The "Plugin Type" should be set to "Github".



Seems this is pretty recent though - talking about all the changes happening within the last 2 months from what

[https://code.launchpad.net/~blair-bonnett/kicad/git](https://code.launchpad.net/~blair-bonnett/kicad/git)

I have read ....... so what is complete and is there a list of completions on this part of the project somewhere.

_____________________________________________________________________

My advice on this after using what I can of the program

The development version is not complete ...... therefore my advice would be to wait till it is released to use it

The stable version in 12.04 is old ...... maybe too old for your requirements - but it works - so using this is a option

The stable version in 14.04 is july 2013 ..... this worked for me in my development install of 14.04 ...... but if you can wait
then the new 14.04 comes out on the 17th of this month ..... ( this to me seems the right option to take )

Otherwise you may waste a lot of time setting things up and still find on the 17th you have to install again and set everything up to suit.

```

_____________________________________________________________________

Think this is as far as I can go now with this as its too specialized for me - interesting though
 ( you have a way forward below too on the other forum and I also think that is the better place 
   now to continue with finding how to link that online library ..... )

A clean install of 14.04 alongside my current OS on the 17th is what I will be doing though to see 
how this all works when running kicad as a stable release - the 64 bit 2013 July one. 

_____________________________________________________________________


```

I did a small video on where I was upto and the errors still showing here ....... 
[http://youtu.be/gRe2TLbK6jY](http://youtu.be/gRe2TLbK6jY)


ok found your thread too - so will watch for answers there .....

[http://www.eevblog.com/forum/open-source-kicad-geda/mistake-to-use-daily-build-ppa-to-update-kicad/](http://www.eevblog.com/forum/open-source-kicad-geda/mistake-to-use-daily-build-ppa-to-update-kicad/)

---

### Post by BrianSwatton on 2014-04-07
Well, it seems to be working.  I added a github entry which worked, shortly after I realised I could select components and see their local footprints again too. Not sure if those things related.

There certainly seems to be something awry with KISYSMOD, it doesn't seem to be being set where CvPCB.pdf claims, and it doesn't help to set it manually it seems. I have noticed the configure button in the cvpcb's toolbar doesn't respond either.


Thanks for the help, much appreciated.

---

### Post by 23dornot23d on 2014-04-07
You are very welcome ...... I noticed too the KISYMOD was having little effect on anything ....... tried various things ........ as my main though was a direct link to the git repos .......  I have a feeling a plugin was being written though to make that task a simple one ........ but I could not see where there were any easy instructions to it ......... the website you are on seems best now and I tried following what they were saying linking and setting variables ........ but some seem to be to do with windows ..... and the other which was linux told me the file already existed ......... well it was a good investigation.  But I believe they need a little more time to finish the part off that links direct to the online web library ......... the other local one seems to work ok as that was their original way ....... but the updates would have been handy ...... but in 14 or so days time you may be able to get all you need.  Cheers for the  kind words ......

---

### Post by BrianSwatton on 2014-04-07
Heh, I spoke too soon.  The very next part of the workflow doesn't run at all, the program "pcbnew". 

If I run it from terminal it gives errors too :

x--

brian@Office:~$ pcbnew
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so: undefined symbol: PyExc_ValueError
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 66, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 16, in <module>
    from xml.parsers.expat import ExpatError
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: _Py_ZeroStruct

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so: undefined symbol: PyExc_ValueError
Segmentation fault (core dumped)
brian@Office:~$ 

x--

Ho hum...

---

### Post by 23dornot23d on 2014-04-07
Do you need help removing it - to get the older version back in place ........   

The instructions are already posted in the thread - but they may not be clear and possible you could run into other problems ..... 

but adding as a ppa was safer to remove to go back to the older version.  

1 . Basically uninstall the Kicad version you have now  

2 . untick the ppa in synaptic

 3 . Reload the repos with the new lists - which will no longer include that ppa  

4 . Then use the old version of Kicad by just picking it in synaptic and install it

Should be then back to the last version you were using .........


* most of those errors seem to point to python problems - maybe newer libraries that you are missing .......

---

### Post by BrianSwatton on 2014-04-07
Thanks.  I'll probably do that soon.

---

### Post by BrianSwatton on 2014-04-08
Not sure if you're still following the other thread, 23dornot23d, but there does seem to be a problem with python usage in latest stuff too.  It's getting way over my head, so will try and go back to the 12.04LTS stable I had previously.

All the best

---

### Post by 23dornot23d on 2014-04-08
Ok if you come across anything unusual just post back here ....... as I am still keeping a track on this thread
and a couple of others ...... including the one on their own forum as it now interests me ...... 

The 14.04 that I looked at also looks good to me ..... but with my limited knowledge of how it all does work
properly for electronics people it is over my head as how you go about laying circuit boards out.

I may have a glance at the You-Tube Tutorial videos - as they seem pretty good - looks impressive but like 
most things - we need a good background on them before understanding the terminology.

Its the 8th today so in 9 more days time the new release of 14.04 is due ......... unless the schedule has been changed
must check that out again ....... [https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule) , looks ok still for the 17 April .......

The people in the testing area are showing a few problems up now - but hopefully the ones to do with the new 
desktop and options should soon filter away [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

__________________________________________________________________________________



When I have watched the change to new versions in the past - upgrades can go wrong in the first month after a new release - my own advice
would be to install alongside what you have now ......... anyone upgrading needs to take care too as there is no way of going back without
you have additional backups or use a program before it to save things.

I found a handy system backup tool - that just keeps a snapshot of the operating system files ..... Timeshift .... 

But users have to take care of any of their own data files they have using this way 
( but it works for me as I store all my own data in external files on other partitions on my drive ......... )
when restoring Timeshift backups it will erase everything on the partition you restore it to and it also
creates a new grub file ........ not for the faint hearted ..... and in my own case I try things like this out
on old systems that do not matter to me too much first ......... just as words of warning .

Sticking with what we have is not a problem until like in cases where programs need newer libraries to function.
looking at Kicad this may be the case to get the later releases to work once they are released.
( Just something to bear in mind - if and when people are thinking of upgrading )

That is as much as I can say to try to help anyone watching this form any decisions ............

Hope some of it helps though ........

---

### Post by BrianSwatton on 2014-04-08
I haven't changed Ubuntu at all, still at 12.04LTS, and probably won't for a while after the new one comes out.  

I'll try it on another machine too probably. I'm usually pretty cautious about such things, I tend to be using older hardware.

---

