---
title: "HOWTO: Install Novel Client on Ubuntu"
date: 2007-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Prospero2006 on 2007-05-31
Hello all,

I am a technology teacher in San Antonio, Texas. I work with a program called iMAK, which stands for interactactive Media Applications at Krueger. (Northeast Independent School District.) We are a technology based magnet program, and all of our computers, over 150, run a dual-boot Ubuntu/Windows XP operating system image. 

I'm in charge of maintaining the network on campus, and one of the challenges I've resolved that others may be interested in involves interfacing Ubuntu with Novel servers that distribute shared resources. 

If your workplace utilizes Novel, and you want to use linux to access your resources, hopefully this step-by-step setup will get you up and running. This configuration has been tested with ubuntu Edgy/Feisty. I'm assuming you are working within  a root context. If not, you may have to preface many of these commands with 'sudo'

**Step 1:**
Download the stuff you need.

Download the linux novel client. I use novelclient-0.91-1.i386.tar.gz. 
I've provided a copy [HERE ]("http://www.imakmud.com/novelclient-0.91-1.i386.tar.gz")

Download this library file libstdc++-libc6.1-1.so.2.
Once again, I have provided a copy [ HERE.]("http://www.imakmud.com/libstdc++-libc6.1-1.so.2") 

You're going to need a C compiler to tweak the novel source code a bit. So, be sure you have the build-essential package installed. --We'll be using gcc. We'll also need a couple of extra packages.
```

apt-get install build-essential
apt-get install dialogue
apt-get install ncpfs

```

**Step 2: **
Unzip the novel and change the file permissions on everything in there. 
```

tar -xzvf novelclient-0.91-1.i386.tar.gz   
chmod -R 777 novelclient/

```

Copy the libstdc++-libc6.1-1.so.2  to /usr/lib/
```

cp  libstdc++-libc6.1-1.so.2 /usr/lib/

```

[B]Step 3: Set it up.
[/B]
cd to the scripts directory under novelclient.
```

cd novelclient/scripts/

```

Open up the file setup-United.sh in your favorite text editor. 
(emacs of course!)
 Lines 53-54 should look like this:
```

if [ "$1" = "9.0" ]; then
    RCFILE='/etc/rc.d/rc.local' # The local system configuration file

```

Change it read as follows
```


if [ "$1" = "9.0" ]; then
    RCFILE='/etc/rc.local' # The local system configuration file

```
(Point RCFILE to the correct rc.local.)

Now we're going to run setup-United.sh, but we have to do it from the novelclient directory
```

cd ..
scripts/setup-United.sh 9.0

```
 You'll be presented with a series of dialogues.
First window select tcp
Second window choose yes
Third window choose yes. 

It should go through and install everything. (Most of the files have been dropped into /usr/local/bin. We'll be overwriting them soon if we need to. 
**Fire it up!**
```

novelclient

```

This should bring up a window that prompts you for a novel username and password.

Click on the '**advanced**' button and find the '**Location Profiles**' tab. 

Select Default and choose properties.

Select the '**DHCP Settings**' tab.
This tab has 4 boxes. 
We only need fill in an ip address for the first one and check 'Get from DHCP ' for the bottom three.

The first box takes an ip address. This is where you need to log into a windows machine that has everything configured. Locate the ip address of the novel server. If you've gotten this far in the tutorial, a little poking around should turn up the correct address. 

Select ok when finished and now choose the '**NDS**' tab, which is next to the '**Location Profiles**' tab
we selected earlier.
 
The first window has a little picture of a tree to the right. Click on the tree and wait a minute. If it turns up your novel server tree, you will be able to easily select a context in the box underneath.

The '**server**' box under '**NDS**', the third box under '**NDS**' to be more specific, takes the ip address of the NDS Server you located on the windows machine. --If you are able to authenticate with a username and password, your novel shares will be
located under /home/user/ip_address_of_novel_server

If not, keep reading.

If you clicked on the tree and it flipped a blank window, the first thing you want to do is check your device configuration. 

```

ifconfig

```

If your active network device is eth0, you need to go back and look at your Novel configurations. The novel source code is configured 
to work with eth0. 

If your active network device is something other than eth0, do one of the following

==Wired Ethernet==
My network device is eth1, eth2, eth3:

cd to the novelclient directory and open the 
file called portping.c in a text editor
Line 73 looks like this:
```

strcpy(ifn,"eth0"); // interface name

```
Change eth0 to reflect your device.

Recompile portping.c
```

gcc portping.c
cp a.out /usr/local/bin/portping

```

Open rc.local and see that the last line, which starts with the word multicast, 
also reflects your active internet device. 

Now try the tree button. If it doesn't display a novel server tree, 
check your configurations in the panel. Restart the machine.


==Wireless Ethernet==

If your active network device is wlan0, wlan1, or any wlanX for that matter:
cd to the novelclient directory and open the 
file called portping.c in a text editor
Line 73 looks like this:
```

strcpy(ifn,"eth0"); // interface name

```
Change eth0 to reflect your device.
Line 46 looks like this
```

char ifn[16];

```

Change it to
```

char ifn[100];

```
Recompile portping.c
```

gcc portping.c
cp a.out /usr/local/bin/portping

```

Open rc.local and see that the last line, which starts with the word multicast, 
also reflects your active internet device. 

Now try the tree button. If it doesn't display a novel server tree, 
check your configurations in the panel. Restart the machine.

I presently have 400+ kids happily using novel on Linux using this configuration.
I hope it helps.

Josh Beck
IT Coordinator.
iMAK Magnet School
Northeast ISD.
San Antonio, TX.
[http://www.neisd.net/imak](http://www.neisd.net/imak)

---

### Post by BenWilson on 2007-06-11
Isn't it "Novell?"

---

### Post by tvich on 2007-07-16
Spelling is not important, when your solutions works so nice. If I'm in your area, I'm buying you a drink.

P.S. Registered just to say THANK YOU! That is not enough, I LOVE YOU!
LOVE YOU, LOVE YOU, LOVE YOU...

---

### Post by BDNiner on 2007-07-23
This is great. I can now try and reinstall ubuntu over my SLED computer and see if it works. Now all i need is to get console one working and that is that.

---

### Post by BDNiner on 2007-07-23
Great work with this novell client solution. I had to make one change. 

sudo cp libstdc++-libc6.1-1.so.2 /usr/local/bin/

I had to copy this library to the directory  /usr/local/bin as well. I am sorry i don't know how to make that line show up as code in the forum. But i am able to log in. Nothing shows in the results window but i am able to browse to the network shares. What happened to the desktop icon? I am rather new with linux so be a little patient with me.

Thanks again for getting this done, now you should work on the interface. The text is too large so it can be difficult to read some of the options since the top or bottom of the letters may be cut off. Can i download the latest Linux Novell client from their website? I will try anyways and see hoe far i get.

---

### Post by wtzup on 2007-07-30
When I do this command (with root access):

scripts/setup-United.sh 9.0

I get an endless loop with this error:


...
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
...

I have followed the steps a few times and not sure what to do
Any ideas?

Thanks
James

---

### Post by sanxiago on 2007-08-03
> **wtzup said:**
> When I do this command (with root access):

scripts/setup-United.sh 9.0

I get an endless loop with this error:


...
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
scripts/setup-United.sh: 121: dialog: not found
...

I have followed the steps a few times and not sure what to do
Any ideas?

Thanks
James

James,
you need dialog to be installed
use
apt-get install dialog 
instead of the above
apt-get install dialogue

Santiago

---

### Post by jawbreaker on 2007-08-04
> **BenWilson said:**
> Isn't it "Novell?"

Actually, no. This software is not made by Novell. See [Novel Client]("http://novelclient.sourceforge.net/"). Novell does have an official "Novell Client" for Linux, but as you can imagine it's only available as a SuSe package.

---

### Post by BDNiner on 2007-08-06
I can only run the novel client with root privileges. Is there anyway to run it as a regular user?

/usr/local/bin/Novel: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

This is the error i receive when i run novelclient. when i run sudo novelclient it works fine. I have changed the permissions of the file it is trying to access in /usr/local/bin but this doesn't help. 

Also i did not get any desktop or applications menu icons. I ran all the instruction using sudo.

Any help will be appreciated.

---

### Post by tworkemon on 2007-08-23
I get an error when I try to login. I can view the Tree and Context.

```
failed;server BLAH belongs to tree BLAH2 and you are not authorized to it
```
or at times I get
```
Could not mount server. failed:ncplogin: Server not found (0x8847) when trying to find BLAH
```
Of course BLAH and BLAH2 are not the real server/tree.

---

### Post by porter238 on 2007-09-17
> **tworkemon said:**
> I get an error when I try to login. I can view the Tree and Context.

```
failed;server BLAH belongs to tree BLAH2 and you are not authorized to it
```
or at times I get
```
Could not mount server. failed:ncplogin: Server not found (0x8847) when trying to find BLAH
```
Of course BLAH and BLAH2 are not the real server/tree.

I am getting the same error.  The "Not authorized to it" error.  Please advise.  Thanks.

---

### Post by Weazl2000 on 2007-11-06
> **porter238 said:**
> I am getting the same error.  The "Not authorized to it" error.  Please advise.  Thanks.

I am also receiving this error:confused:

---

### Post by Weazl2000 on 2007-11-06
I'm wondering if this has something to do with LDAP, Is there something else I have to do?

---

### Post by mezcla on 2007-11-12
I'm getting the same error as well. I've tried to mount to the server using ncpmount as well but neither are working for me.  Any help would be much appreciated.

```
failed;server BLAH belongs to tree BLAH2 and you are not authorized to it
```

---

### Post by ycardinal on 2007-11-19
I am getting the same error, please help us!

```
failed;server BLAH belongs to tree BLAH2 and you are not authorized to it
```

---

### Post by Antikx on 2007-11-19
After pulling my hair out all day, I figured it out. Ya! :)
Downgrade your ncpfs package to 2.2.6-3
There is a bug in 2.2.6-4 that causes this exact problem on Gutsy.

Because I'm all about the love I'll even link to the package:
[http://packages.ubuntu.com/edgy/net/ncpfs](http://packages.ubuntu.com/edgy/net/ncpfs)

Install it via command line:
```
sudo dpkg -i packagename.deb
```

Please, post below if this helped, or didn't help.

---

### Post by Mttechserv on 2007-11-20
Hey there...
Just stepped back to 2.2.6-3 ( ncpfs ) and I still seem to be having the same issue. 

First rolled back ncpfs itself. Same issue. 
Then rolled back libncp. Same issue
Then rolled back libpam-ncp. Same issue. 

Not a lot of time to play with this right now, but if anyone has any suggestions, I'm willing to listen.

---

### Post by asaturn on 2007-11-20
I downgraded all 3 ncp packages in dependent order... then I got this error:

```
ncpmap must be installed suid root
```

... so I used this command:

```
sudo chmod u+s `which ncpmap`
```

... which gets rid of that error and brings back this error:

```
Error: Could not mount server.
failed:Server servername.abc.def belong to tree ABC
and you are not authenticated to it
```

:mad:

does this have anything to do with SLP?

---

### Post by Antikx on 2007-11-20
Yes, in order to run the client as a regular user I had to do the following as well:
```

	sudo chmod u+s /usr/bin/ncplogin 
	sudo chmod u+s /usr/bin/ncpmap
	sudo chmod u+s /usr/bin/ncpmount
	sudo chmod u+s /usr/bin/ncpumount

```
Not sure if I needed to do all of them, but oh well.

can you mount via commandline?
This is the kind of string I'm using to test:
```

ncpmount -S 130.179.19.56 -A hsl-nw.cc.umanitoba.ca -U username.hsl.corporate.local.umb -V hsl -u username /mnt/novell/

```

---

### Post by Mttechserv on 2007-11-21
This gets more and more interesting... if I attempt to log in via a command line, here is what I get... ( some things replaced for security, of course )

mturner@cfs-testbed:~$ ncpmount -S 198.XXX.XX.XX -A blahdns.blah -U mfturner.blah.blahgov -u mturner /home/mturner/mnt/novell/
Logging into 198.XXX.XX.XX as MFTURNER.BLAH.BLAHGOV
Password: 
Get host address `blahdns.blah': Server not found (0x8847)

Next, the odd part...
Blahdns.blah is one of the two internal name servers... it is pingable, responds to nslookup, etc... though it is on a different subnet from myself. I am also unsure if there are firewalls separating the subnets, etc. ( This is a gov't office, none of this information if available to me )

Though, when I boot into Windows XP ( it's a dual boot machine ) - I log in... no issues.

---

### Post by asaturn on 2007-11-21
try that with all IP addresses...

---

### Post by Mttechserv on 2007-11-21
Same deal when I replaced the DNS Server's name with it's IP address. Or with the alternate DNS server's address. 
Only a little odd, I find...

---

### Post by asaturn on 2007-11-21
I want to meet the guy who got this working the first time with no problems. or the guy at novell in charge of client development on linux and ask him to rationalize why novell doesn't have an official version that works on anything but their $50 linux suite.

---

### Post by Mttechserv on 2007-11-21
Trust me, I do agree with you there. 
I've been using linux for over 5 years now, often times from an administrative point of view... 3 years now using strictly Ubuntu... and I've never once seen anything this complex to get running. 
I really wish that using Alien to convert the Novell RPMs to Debian packages worked... but of course, there's some stricly SUSE dependencies thrown in... mostly due to the fact that Novell is an aging dinosaur, and scared of the threat that Ubuntu poses to them. Sad, really... that a company that used to be a major competitor in the network server field is scared of an Open Source project... lol. 

In my case, I'm not too worried about it, though it would help me out. All I have to do is boot to Windows ( Which I despise ) and copy the files over... nothing major, but quite an annoyance... 
I'm Kind of wondering what a Virtual Machine under Ubuntu might do... might try that out later today... though it seems to be needless work to copy a few files to the network for a backup...

---

### Post by asaturn on 2007-11-21
try Innotek Virtualbox

I tried the command line login, got the -330 error just like the novel client gets! (invalid server response)

maybe this is a protocol compatibility issue?

if I don't type out my full novell context and I use just my username, I get error: ncpmount: No such entry (-601) in nds login. Login denied.

---

### Post by Mttechserv on 2007-11-21
As far as I can see, the (-601) seems to simply indicate that it can't find your user ( and without the NDS context, this does seem pretty normal )
It would seem to be some form of protocol issue, either server side, or client side... 

Thanks for the suggestion, btw. :-D

---

### Post by ycardinal on 2007-11-22
I downgraded my ncpfs package to 2.2.6-3. 

I am now getting the following error:

Error: Could not mount server.
failed:ncpmap must be installed suid root

---

### Post by Antikx on 2007-11-22
> **ycardinal said:**
> I downgraded my ncpfs package to 2.2.6-3. 

I am now getting the following error:

Error: Could not mount server.
failed:ncpmap must be installed suid root

See:
[http://ubuntuforums.org/showpost.php?p=3807440&postcount=19](http://ubuntuforums.org/showpost.php?p=3807440&postcount=19)

---

### Post by ycardinal on 2007-11-22
Thank you fro your great help, that worked but now I'm getting the following error:

Error: Cannot map home directory.
failed:Volume path 'NEWHOME///USERNAME' is 
invalid: 'Invalid argument'

---

### Post by Antikx on 2007-11-23
> **ycardinal said:**
> Thank you fro your great help, that worked but now I'm getting the following error:

Error: Cannot map home directory.
failed:Volume path 'NEWHOME///USERNAME' is 
invalid: 'Invalid argument'

Your welcome.
hmmm... can you try doing a command line mount (see one of my previous posts) you may be able to figure out what you need to plug into the client easier that way.
I don't know your Novell environment and I'm not really a Novell Admin, but I'll try and help the best I can. My guess is that you may need to put something different for your tree, or it's having problems creating a directory in your Linux home directory because of all the forward slashes. I'm not sure why you are seeing so many slashes. hmmm

---

### Post by ycardinal on 2007-11-26
When I try the console i get this :

bob@bob-laptop:~$ sudo ncpmount -S 10.*.*.* -A 10.*.*.* -U BOB.GROUP.DIVISION.LOCATION.BRANCH.COMPANY -u bob /mnt/novell/
Logging into 10.*.*.* as BOB.GROUP.DIVISION.LOCATION.BRANCH.COMPANY
Password: 
ncpmount: No such entry (-601) in nds login
Login denied.

AND

bob@bob-laptop:~$ sudo ncpmount -S 10.*.*.* -A SERVER.BRANCH.COMPANY -U BOB.GROUP.DIVISION.LOCATION.BRANCH.COMPANY -u bob /mnt/novell/
Logging into 10.*.*.* as BOB.GROUP.DIVISION.LOCATION.BRANCH.COMPANY
Password: 
Get host address `SERVER.BRANCH.COMPANY ': Server not found (0x8847)

---

### Post by ycardinal on 2007-12-04
Does anyone know what could be wrong?

---

### Post by asaturn on 2007-12-04
mostly just that the client itself probably has issues with the novell protocols (it's a bit outdated...) plus it isn't meant to be run on ubuntu... I'm sure if the original developer or another programmer who understood ubuntu and novell were around they could figure this out.

unfortunately I'm neither of those.

---

### Post by nailbnny on 2007-12-04
I can't really help you troubleshoot because I can't tell you why this works, but here's the script that I use:

```


ncplogout -a > /dev/null

ncplogin -S *Auth. Server Name* -A *Tree* -U *User*.*Context* -P *Password* -o tcp

ncpmount tcp -A *Server IP* -S *Server Name* -U *User*.*Context* -P *Password* /mnt/Novell


```

---

### Post by durand on 2007-12-04
I wish my school in the UK runs linux.... :(

Anyway, cool idea.

---

### Post by ycardinal on 2007-12-07
> **nailbnny said:**
> I can't really help you troubleshoot because I can't tell you why this works, but here's the script that I use:

```


ncplogout -a > /dev/null

ncplogin -S *Auth. Server Name* -A *Tree* -U *User*.*Context* -P *Password* -o tcp

ncpmount tcp -A *Server IP* -S *Server Name* -U *User*.*Context* -P *Password* /mnt/Novell


```

Thank you everyone who has helped! I got it to work ! with these commands! /\ /\ /\ and with the help from everyone else! Linux Rocks!

---

### Post by nailbnny on 2007-12-07
Sweet.  =)

---

### Post by Weazl2000 on 2007-12-07
When I try to use the client I get a results window that stays blank and then disappears. Any ideas?

---

### Post by nailbnny on 2007-12-10
When I use the client, I don't get a results window.  You might want to try to connect using the terminal.  That way you might get a somewhat helpful error message.

---

### Post by dxxvi on 2008-01-07
Please help me (for those who made it work).

This is the information I can see when I right click | Novel Login ... the Novell icon in my XP system tray:

Username: 190482
Tree: FEDEX
Context: SRS.WRCS.ITD.ORLANDO.FEDEX
Server: WRCS-ORL1

In my gutsy I can ping to WRCS-ORL1.corp.fedex.com. I tried the ncplogin with:

sudo ncplogin -S WRCS-ORL1 -A FEDEX -U 190482.SRS.WRCS.ITD.ORLANDO.FEDEX -P hannah -o tcp

and the error is Get host address `FEDEX': Server not found (0x8847).

Then I tried 

sudo ncplogin -S WRCS-ORL1 -A WRCS-ORL1.corp.fedex.com -U 190482.SRS.WRCS.ITD.ORLANDO.FEDEX -P hannah -o tcp

ant the error is : Invalid server response (-330) failed in nds login.

Do you know where I was wrong and how to fix it?

Thanks for any help.
-------------------------------------------------------------------------------
Solution: use the ncpfs of hardy (this is what I did: change gutsy in sources.list to hardy, sudo apt-get update, sudo apt-get install ncpfs, then hardy in sources.list back to gutsy, sudo apt-get update)

---

### Post by adrien214 on 2008-02-20
[COLOR="Silver"]Hi 

I wish I was as far as ending the installation, but I cannot even see the setup :

```

me@myxubuntu-box: ~/novelclient$ sudo scripts/setup-United.sh 9.0

cannot initialize curses
Setup Canceled

```

what does this mean ?

any help is welcome :) [/COLOR]

Problem solved, it was a terminal issue - thanks to The_Sheep on #xubuntu

---

### Post by Bufke on 2008-04-30
I had an issue with the novell mounts being unable to unmount.  This causes the system to not shut down.  It can be fixed by manually unmounting files with ncpumount through a terminal or bash script.  Thought I would report this in case anyone else had this problem.  Ideally this should happen automatically.  Are other's experiencing this problem?

By the way great guide otherwise!

---

### Post by dxxvi on 2008-05-01
> **Bufke said:**
> I had an issue with the novell mounts being unable to unmount.  This causes the system to not shut down.  It can be fixed by manually unmounting files with ncpumount through a terminal or bash script.  Thought I would report this in case anyone else had this problem.  Ideally this should happen automatically.  Are other's experiencing this problem?

By the way great guide otherwise!

we're in the same boat :(

---

### Post by Bufke on 2008-05-03
> 
Quote:
Originally Posted by Bufke View Post
I had an issue with the novell mounts being unable to unmount. This causes the system to not shut down. It can be fixed by manually unmounting files with ncpumount through a terminal or bash script. Thought I would report this in case anyone else had this problem. Ideally this should happen automatically. Are other's experiencing this problem?

By the way great guide otherwise!
we're in the same boat 

The best way I figure to handle this is edit /etc/gdm/PostSession/Default and add

```
ncpumount ~/ncp/MOONSRVR/SYS/
ncpumount ~/RMC/MOONSRVR/
ncpumount ~/RMC/My\ Network\ Home/

```

Note these are my settings, you won't have things like RMC and MOONSRVR.

I can live with this.  Looks like there's an option for login scripts.  Anyone know how to use these?  I'd love to say set a global variable for the user name and password entered.  This way they could be used in printing.  Could even do some serious scripting and set up profile settings.

---

### Post by netjess on 2008-05-22
After making a selection at the "Add Multicast Route" prompt I get the error 
scripts/setup-United.sh: 257: cannot create : Directory nonexistent

It doesn't matter if I select yes or no. line 257 is modifying the /etc/rc.local file and it does exist.

Anyone have an idea?
Thanks.

---

### Post by Prospero2006 on 2008-06-04
Hello there,
In the install directory, there is a file called Setup-United.sh

Go to line 257 and change the directory there to match what is on your computer.

I think that will help.

---

### Post by acrobrat on 2008-07-02
Hi was trying it on the latest version of ubuntu (8.04) tried your instructions.. got as far as it looked like it ran the install.. didn't find the shortcuts on the desktop or anywhere... 
but when i try to run the code 'novelclient' it gives an error:

bash:novelclient: command not found

Thanks in advance.

GJ

---

### Post by Lord C on 2008-08-12
[Edit]
Got it working in the end by using an IP address for the Server box

---

### Post by bobbyxmail on 2008-08-14
I have an Error : "Cannot Create: Directory nonexistent"

---

### Post by mitanka on 2008-08-21
Thx for this great post, it really did help me finally connect to a Novell Netware OS. I'm working on Ubuntu 8.04 and the Netware version is 6.5. To be honest i had to do some updates to this post to be able wiht Ubuntu 8.04 login and mount the Novell volumes. so the first thing i've changed to succesfully install the Novell client is to use "sudo" on almost all command especially with 
> sudo scripts/setup-United.sh 9.0 Without "**sudo**" Novell client won't install. Next, i had to add line with Novell address and name in **etc/hosts** file. So folowing the guide step by step and taking this modified steps i was able to succefully mount Netware 6.5 volumes to Ubuntu 8.04. 
There are still some oddies for me about this, for example i haven't figured out still how to "tell" the client to mount on folder of my own then the default it uses > home/localusers/servername/servertree/.

And i think it would be helpfull from some one to tell if he managed to print on Novell Netware attached printer.

---

### Post by Lord C on 2008-09-19
> **netjess said:**
> After making a selection at the "Add Multicast Route" prompt I get the error 
scripts/setup-United.sh: 257: cannot create : Directory nonexistent

It doesn't matter if I select yes or no. line 257 is modifying the /etc/rc.local file and it does exist.

Anyone have an idea?
Thanks.

> **bobbyxmail said:**
> I have an Error : "Cannot Create: Directory nonexistent"

You have to make sure you're typing 

scripts/setup-United.sh **9.0**

---

### Post by micheljacobs on 2008-10-05
Great work, until I read on i was stumped with the loop as a result of the misspelling of dialog!!!

---

### Post by tombott on 2008-11-04
I got this installed without any problems on Ubuntu 8.10, but was unable to view tress, context or servers.

In the end I installed IPX, changed the default protocol in the Novel Client to IPX and was then able to login without any problems.

```
sudo apt-get install ipx
```

```
sudo sudo ipx_interface add -p eth0 802.2
```

Now I just need to mount the volumes....

---

### Post by tombott on 2008-11-04
Well that was easy:

I created a folder for Novell to mount too

```
sudo mkdir /mnt/novell
```

Granted my user 'administrator' rights:

```
sudo chown administrator:administrator /mnt/novell
```

Then entered the following:

```
ncpmount -S server1 -U admin.context -P password /mnt/novell
```

The following will unmount

```
ncpumount /mnt/novell
```

server1 being the Novell Server name admin being my Novell Admin user and context being the context.

Thanks for everybody who has posted in here!

---

### Post by rufia on 2008-12-12
I have installed Novel Client and it works beautifully, except for 1 problem.  I don't have rights to do anything on the folders anymore, not even in my Home dir.

If I use the following ncpmount I do have my rights on the folders back:

sudo ncpmount -S <server> -A <server.DomainName> -U <Novellusername>.<context> -V data/soft -u <Ubuntu username> /mnt/Novell/soft

The problem is that I have to do this a couple of times for each dir I have to access on the server.

Need some help with this.

---

### Post by sliggy on 2008-12-30
For some reason when I try to install I get this error:

```
scripts/setup-United.sh: 258: cannont create : Directory nonexistent
```

Any ideas as to what could be causing this?

---

### Post by justoffthecoast on 2009-01-07
Having a strange problem accessing our web server at work (NetWare 5.70.07 environment) via ncpfs...I mount the server with the following command:

```
sudo ncpmount -S wc-web02 -A westminster.edu -U username.acad.staff.wc /mnt/wc-web02
```

The server appears to map correctly, and I am able to browse its folders via terminal and Nautilus, but no files show up at all. I am able to open known files through the terminal with **nano <filename>**, but I haven't managed to pull a directory listing no matter what I try.

I've tried logging in first with ncplogin and specifying countless other parameters for ncpmount (file permissions, directory permissions, my Ubuntu username, etc.) with no luck. I've also verified permissions on the directory I'm mounting to and tried mounting via IP address instead of hostname.

Any suggestions? I'm running Ubuntu 8.10 (Intrepid Ibex).

---

### Post by sornman on 2009-01-20
> **justoffthecoast said:**
> Having a strange problem accessing our web server at work (NetWare 5.70.07 environment) via ncpfs...I mount the server with the following command:

```
sudo ncpmount -S wc-web02 -A westminster.edu -U username.acad.staff.wc /mnt/wc-web02
```

The server appears to map correctly, and I am able to browse its folders via terminal and Nautilus, but no files show up at all. I am able to open known files through the terminal with **nano <filename>**, but I haven't managed to pull a directory listing no matter what I try.

I've tried logging in first with ncplogin and specifying countless other parameters for ncpmount (file permissions, directory permissions, my Ubuntu username, etc.) with no luck. I've also verified permissions on the directory I'm mounting to and tried mounting via IP address instead of hostname.

Any suggestions? I'm running Ubuntu 8.10 (Intrepid Ibex).

You happen to have any luck finding a fix for this? It seems a patch/update to our Novell servers in December broke listing of files but I haven't found a fix yet.

---

### Post by justoffthecoast on 2009-01-20
Nope...scoured the Internet and spent nearly a week testing different methods to no avail. In the meantime, I've just been running Ubuntu as a virtual machine on top of a Windows XP host using VirtualBox OSE. Since the client for Windows works fine, I log in that way and share all of my network folders with my guest OS.

---

### Post by savek on 2009-02-05
I have some question about this topic.

When I login with novell client which I've installed with above method. It say **'ncplogin invalid option --b'**, I don't know why it error like that.

In Novell Client property, I choose login with bindery (Because my server is netware 3.12) and use IPX protocol.

Sorry for my poor english.

---

### Post by CR34M3 CR4CK3R on 2009-02-26
Prospero2006, you are a legend. Thanks for this. I managed to solve my own problem before my University's IT department even had time for me.

Except for a sudo added to the install command, everything worked fine (as per instruction). I even skipped the whole Location Profiles setup and just entered the Tree, Context and Server (which worked instantly).

Drive mounting works fine, but seeing that I only use the Novel login to authenticate myself to use a proxy server, I don't really care. ;)

Thanks for saving me loads of time and effort (as I was heavily considering dual-boot by now...)

---

### Post by tristanbob on 2009-04-03
> **sornman said:**
> You happen to have any luck finding a fix for this? It seems a patch/update to our Novell servers in December broke listing of files but I haven't found a fix yet.

I am so glad you guys are running into the exact same problem as me.  I can login to the Novell shares and see all directories, but no files are appearing.

The strange thing is that I can use a Fedora computer that runs the same version of NCPFS (version 2.2.6) and connect to the Novell shares without any problem!

This makes me think this problem is related to Ubuntu, and not the Novell servers. Is there a bug filed for this yet?

Has anyone found a work-around to make the files show up?

Thanks!

Tristan Rhodes

---

### Post by tristanbob on 2009-04-07
> **tristanbob said:**
> I am so glad you guys are running into the exact same problem as me.  I can login to the Novell shares and see all directories, but no files are appearing.

The strange thing is that I can use a Fedora computer that runs the same version of NCPFS (version 2.2.6) and connect to the Novell shares without any problem!

This makes me think this problem is related to Ubuntu, and not the Novell servers. Is there a bug filed for this yet?

Has anyone found a work-around to make the files show up?

Thanks!

Tristan Rhodes

I have some interesting results to share:  If you change the mount options I can get my files to be displayed, although they are truncated to 8.3 filenames.

Here is the command to do this:

```
ncpmount -m -s tcp -A server.domain.com -S server.domain.com -N os2 -U username -V cnet /home/usermount
```

---

### Post by tarzan_055 on 2009-11-11
hey
i get this message when i run novelclient command
 
/usr/local/bin/Novel: error while loading shared libraries: /usr/lib/libstdc++-libc6.1-1.so.2: ELF file data encoding not little-endian
 
does anyone know what that means. any help will be appriciated

---

### Post by asaturn on 2009-11-11
it means it isn't compatible with your CPU

[http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

---

### Post by rockoprem on 2010-03-03
It is great to see the elaborate discussion on this topic. I, however have a question regarding the server name and the address. Can someone tell me how do I derive those details from my Novell Client running on Windows, so that I can plug them in ncpfs. Thanks!

---

### Post by Mttechserv on 2010-03-03
> **rockoprem said:**
> It is great to see the elaborate discussion on this topic. I, however have a question regarding the server name and the address. Can someone tell me how do I derive those details from my Novell Client running on Windows, so that I can plug them in ncpfs. Thanks!

Should be able to click on advanced and grab them from here :
[http://support.novell.com/techcenter/articles/img/ana2003060103.gif](http://support.novell.com/techcenter/articles/img/ana2003060103.gif)

It's been a couple years since I've had to use the Novell Client though. :-P

---

### Post by rockoprem on 2010-03-09
> **Mttechserv said:**
> Should be able to click on advanced and grab them from here :
[http://support.novell.com/techcenter/articles/img/ana2003060103.gif](http://support.novell.com/techcenter/articles/img/ana2003060103.gif)

It's been a couple years since I've had to use the Novell Client though. :-P
Hey, thanks for that Matt. Looks like the code is correct. I get the password prompt for login and once I enter that, I get the following error:

ndslib.c:1051: Invalid start: 1835008 00010000 00010000 00100006
ncpmount: Invalid server response (-330) in nds login
Login denied

A quick search through the forum for 330 error revealed that the older versions of ncpfs were much more stable. I am currently trying to do downgrade. Is there any other solution??

---

### Post by Mttechserv on 2010-03-09
Even when I did have this working somewhat properly, the NCPFS module was somewhat flaky at best.
In your current situation ( and also depending on the network you're joining ) a downgrade is probably the best thing to do.

---

### Post by magahugu on 2010-04-14
Hey Guys,

the software links in the howto are broken. can you actualize them?

peace love and light
urs

---

### Post by Mttechserv on 2010-04-14
A quick search of Google indicates that there are other sites mirroring these same files.

Cheers,
Matt

---

### Post by akhirah on 2011-01-06
Super post, good to see a forum still alive and kicking since the initial post way back in 2007!!

I wanted share that I followed the guide (with few minor changes) and got the client to load on UBUNTU 10.10 MAVERICK

At present, i've only just configured the client with my novell server ip address and tree, as i'm home I cannot test.  Will update tomorrow.

tally ho  :)

---

