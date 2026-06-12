---
title: "Where is $PATH set up when Ubuntu boots ?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Cap'n Redbeard on 2008-06-05
Hi Folks,

Silly beginners question here: Where are the initial values for $PATH set up in Ubuntu. What is the equivalent of the DOS "autoexec.bat" file in which paths are set ?

:confused:

---

### Post by drs305 on 2008-06-05
The root path is set up in /etc/environment

You would normally set user PATH in ~/.bashrc with the following format:
```

export PATH=$PATH:$HOME/path_to_folder:$HOME/path_to_next_folder

```

---

### Post by bobbocanfly on 2008-06-05
If i am reading the question correctly you want to know what Ubuntu's default $PATH is?

```
bobbo@tiger:~/Code/terminator$ echo $PATH
/home/<username>/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by Cap'n Redbeard on 2008-06-05
Cheers bobbocanfly and drs305,

Reason i asked is 'cause if i do from terminal:

```

export PATH=$PATH:$HOME/path_to_folder:$HOME/path_to_next_folder

```

that path is forgotten when i close the terminal window and open another one.

Have just re-installed gEDA, so will try putting it's search paths into the "/etc/environment" file...

Will let you know if that works,

Cheers folks.

---

### Post by drs305 on 2008-06-05
> **Cap'n Redbeard said:**
> Cheers bobbocanfly and drs305,

Reason i asked is 'cause if i do from terminal:


that path is forgotten when i close the terminal window and open another one.

Have just re-installed gEDA, so will try putting it's search paths into the "/etc/environment" file...

Cheers folks.

That should work but it more properly should go in the user's ~/.bashrc folder unless it's going to be used by multiple users. It will be read during boot and available for the entire session.

---

### Post by Cap'n Redbeard on 2008-06-05
Ahaa,

So each user's paths are set up in their "/home/.bashrc" file whilst global paths are placed in the "/etc/environment" file ?

Another problem though is:

If i know where a programme has been installed and it's definitley there, why doesn't BASH find it ?

> 
redbeard@the-wintel-box:~$ cd geda-install
redbeard@the-wintel-box:~/geda-install$ ls
bin  html  include  info  lib  libexec  man  share
redbeard@the-wintel-box:~/geda-install$ cd bin
redbeard@the-wintel-box:~/geda-install/bin$ ls
bin          gnet_hier_verilog.sh  gschlas       lxt2miner        nghelp             pcb              smash_megafile  vcd2lxt2
cmpp         gnetlist              gschupdate    lxt2vcd          ngmultidec         refdes_renum     stdio-wcalc     vcd2vzt
convert_sym  gnucap                gsymcheck     makeidx          ngnutmeg           rtlbrowse        sw2asc          vertex
garchive     gnucap-modelgen       gsymfix.pl    Merge_dimPCBPS   ngproc2mod         sarlacc_schem    tex2vcd         vvp
gattrib      grenum                gsymupdate    MergePCBPS       ngsconvert         sarlacc_sym      tla2vcd         vzt2vcd
gerbv        gsch2pcb              gtkwave       mk_verilog_syms  ngspice            sch2eaglepos.sh  tragesym        vztminer
ghwdump      gschem                iverilog      mvl2lxt          olib               share            twinwave        wcalc
gmk_sym      gschemdoc             iverilog-vpi  mvl2vcd          pads_backannotate  shmidcat         vcd2lxt         wcalc-config
redbeard@the-wintel-box:~/geda-install/bin$ gschem
The program 'gschem' is currently not installed.  You can install it by typing:
sudo apt-get install geda-gschem
-bash: gschem: command not found
redbeard@the-wintel-box:~/geda-install/bin$ 


Any ideas ? Is this getting off topic ?

:)

---

### Post by spiderbatdad on 2008-06-05
if you use ls -l
you will also see the file permissions, to determine, whether gschem is executable. Also try running with ./gschem
though you shouldn't need ./ if PATH has been set...
You could troubleshoot by making sure gschem is executable, then try to run with ./gschem from within the /geda/install/bin directory, or by supplying the full path from /home

---

### Post by drs305 on 2008-06-05
> **Cap'n Redbeard said:**
> Ahaa,

So each user's paths are set up in their "/home/.bashrc" file whilst global paths are placed in the "/etc/environment" file ?
:)

*Your* PATH is set in ~./bashrc . *Sudo/root's* PATH is set in /root/.bashrc.  **God's** PATH is set in /etc/environment ;-)

You can see the difference if you run:
```

$PATH
sudo $PATH
su
$PATH

```

---

### Post by Cap'n Redbeard on 2008-06-05
Cheers Spiderbatdad,

> 
-rwxr-xr-x  1 redbeard redbeard  1684924 2008-06-05 12:44 gschem


so it is an executable file.

Trying to run it from it's own directory:

> 
redbeard@the-wintel-box:~/geda-install/bin$ gschem
The program 'gschem' is currently not installed.  You can install it by typing:
sudo apt-get install geda-gschem
-bash: gschem: command not found
redbeard@the-wintel-box:~/geda-install/bin$ 


Just out of interest, what would be the proper syntax (grammar) for the path to this file ?

In "<tilde>/.bashrc" i've put:

> 
# My PATH information:
export PATH=$PATH:home/Documents/gEDA_stuff/Library/Neils:home/geda-install/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:home/geda-install/lib


O'course, the real path is "/home/redbeard/geda-install/bin", but as a logged in user isn't "home" taken as the user (redbeard) directory ?

i'm clearly wrong about this, any ideas ?
:)

---

### Post by Steveway on 2008-06-05
Question! Since GEDA is in the repositories why didn't you install it through your package-manager?
On that way you would get updates automatically and it would allready be ready to work with so you don't have to configure your PATH.

---

### Post by Cap'n Redbeard on 2008-06-05
Very good question Steveway,

i've installed gEDA four times on this machine trying to get it to work under Ubuntu.

First two installs was from the install CD ".iso", downloaded from Mr. Brorson via the gEDA website. i got fed up during the install with it failing due to missing files.

Then i installed it by the simple "sudo apt-get install geda-gaf" from command line.

The install worked, however some bits didn't due to PATH problems (i.e. not finding things clearly defined in PATH).

So, i removed it "sudo apt-get remove geda-gaf", tried a re-install the same way which didn't work for the same reason. Removed it as before.

Just did another install from the CD as recommended by "boz"'s post "Best Analogue Circuit Simulator" in the "Education & Science" forum.

Does that help ?

What am i doing wrong ?

:)

---

### Post by spiderbatdad on 2008-06-05
I set path like this in /.bashrc:

```
export PATH=$PATH:$HOME/bin
``` This example gives PATH to all the executables in /home/user_name/bin

Where user_name is my logged-in/admin account. id 1000

I still have to make files in /bin executable when I add to the folder new programs.

---

### Post by Cap'n Redbeard on 2008-06-05
Hi spiderbatdad,

Doesn't the "-rwxr-xr-x" mean that from all three points of view the file is executable ?

If so, why doesn't BASH know it exists ?

Sorry to go on,

---

### Post by spiderbatdad on 2008-06-05
It does indeed appear to be executable. So it seems your /.bashrc (at the end of the file) should contain:
```
export PATH=$PATH:$HOME/geda-install/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/geda-install/lib
```

This should make the path available to redbeard, and should run, simply, from the terminal with the command: ```
gschem
```

From your previous post I noticed:> -rwxr-xr-x 1 redbeard redbeard 1684924 2008-06-05 12:44 gschem
The "1" indicating that the link has not yet been created. It means 1 link, but I believe you should see 2, once the PATH is actually exported.

---

### Post by Cap'n Redbeard on 2008-06-05
Ahaa spiderbatdad,

Cheers mate, gschem now runs.

So "home" must be in upper case "export PATH=$PATH:$HOME/geda-install/bin". No wonder i'd had troubles and nowt could find 'owt !

Thank you sir,

:)

(how do i officially thank you ?)

---

### Post by drs305 on 2008-06-05
> **Cap'n Redbeard said:**
> 

(how do i officially thank you ?)

Ah, he's probably too modest to reply.

Thanks are given by clicking on the gold star at the lower right of the pertinent post.

The moderators would like you to mark the thread SOLVED by using the 'Thread Tools' link to the upper right of the original post once you are satisfied with the results.

---

### Post by spiderbatdad on 2008-06-05
Thanks goes to drs305 who showed us both how to do it. I had been unhappily having to set path each session, too immodest to ask for help. 

Anyway to thank him click the little gold star at the bottom of the persons post.

---

### Post by The Cog on 2008-06-05
Just to add info:
the current directory "." is not normally part of the path in *nix. Actually, it isn't in Widows either, but the difference is that in Windows the current directory is always searched regardless, whereas in *nix this is not the case. So in *nix, starting a program in your current directory always involves typing ./progname. You get used to it eventually. You could of course all . to your path, but that isn't normally done.

---

### Post by a7ndrew on 2009-01-16
> **spiderbatdad said:**
> I set path like this in /.bashrc:

```
export PATH=$PATH:$HOME/bin
``` This example gives PATH to all the executables in /home/user_name/bin

Where user_name is my logged-in/admin account. id 1000

I still have to make files in /bin executable when I add to the folder new programs.

when I try to run this command from bash, I am getting a response that says "Not a valid identifier". Would anyone know why this might be?

the ~/bin  directory has the following permissions: drwxr-xr-x

---

