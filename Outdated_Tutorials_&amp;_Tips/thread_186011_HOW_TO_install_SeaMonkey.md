---
title: "HOW TO install SeaMonkey"
date: 2006-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by rcarring on 2006-06-01
I am still working on my report regarding the installation clean of Dapper Drake 6.06, but in the meantime, here are some notes on SeaMonkey.

SeaMonkey is a worldwideweb browser based on the old Mozilla Application Suite, and includes the browser, the html editor and various other tools, including Personal Security Manager that is installed in a full installation.

It can be downloaded in gz format from [http://www.mozilla.org/projects/seamonkey/](http://www.mozilla.org/projects/seamonkey/)

++

Installation is relatively simple, and involves using the archive-manager to extract the files to disk, in my case I had created a folder called docs, and a sub folder called tools, and I extracted the files to /docs/tools/seamonkey-installer). 

Run 
```

sudo ./seamonkey-installer 

```
and accept the default installation folder of /usr/local/seamonkey.

Now, the readme accompanying the program says that it must be first run as root. Except this doesn't work. If you do sudo su - and password and then run the shell script, it throws an error GTK+ cannot open display. Run 

```

sudo ./seamonkey 

```
within the installed folder will open the program.

Next, creating a launcher pathed to where the shell script is, and running it doesn't work either. However it will run using sudo.

This led me to suspect a permissions issue. I checked hidden files in my profile and found the ./mozilla folder was root only. I guess this kind of figures. I changed the permissions to let me as a user read/write/execute the folder, then ran the launcher again, and this time it works.

While I expect many users might prefer alternative products, I have found that it is relatively fast when compared to Mozilla, it displays fonts better than Mozilla and is not prone to crashing so often as Firefox.

So far I have bug-reported on the Moz-Bugzilla that SeaMonkey can't cope with aspx pages.

This is my first HOW TO so I welcome feedback.

---

### Post by MintabiePete on 2006-11-02
How did you  end up setting your  shortcut ?

for me I just  set  a launcher with  the  command /home/myfolder/seamonkey/seamonkey and  it seems to open ok   after I set up a  folder in my home  directory and was able to open & install it  in there . Not too sure  if that is the  right way to  do it or not , but  I dont need to be  root  to open it :) 

Actually  I like it , it is  fast , I dont like the  favorites setup , but it is  passable  and  I havnt had any crashes yet since using it .

---

### Post by Solsticiary on 2006-11-29
You should consider doing it the way rcarring did it.  That way you can lock the permissions back down after setting it up,  Unless you plan to lock down your home folder in like manner. The default is /usr for good reason.  You're going to need that security.

---

### Post by vu.ja.de on 2006-11-30
Pretty good How-To.  I was able to successfully install Seamonkey and set up the launcher in only 3 hours.  Brings my Linux experience up to about 7 hours.  I had to find a discussion to changing the permissions to ./mozilla and I had to learn how add the launcher to the main menu.  Thanx

---

### Post by XandR on 2006-12-13
I did it!!!
to tie up the loose ends:
```
root@myuser-desktop:/home/myuser# chown -R myuser:myuser .mozilla
```

Add at the end of the line: /usr/local/seamonkey

```
root@myuser-desktop:~# nano /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/local/seamonkey"
LANG="es_ES.UTF-8"
```

If you dont have access, then add these lines to your ~/.bash_profile
```
PATH=$PATH:/usr/local/seamonkey
export PATH
```

Finally, restart your X and add the program to your KDE or GNome menu :D
copy [http://mozilla.nicubunu.ro/sm_remake.svg]("http://mozilla.nicubunu.ro/sm_remake.svg")  to your /usr/share/icons/hicolor/scalable/apps/seamonkey.svgz

---

### Post by lolwhites on 2007-01-07
I tried running the installer, but it is unable to create the directory usr/local/seamonkey. Nor can I create the directory manually - I get atold"permission denied" even though I though I was logged in as the owner. Any idea where I'm going wrong?

I currently have the installer in my Home folder.

---

### Post by Kateikyoushi on 2007-01-09
I tried the last few versions even the beta but all of the segfaults, did anyone encounter this ?

---

### Post by tagginannie on 2007-01-12
Quote

"Run 
```

sudo ./seamonkey-installer 

```
and accept the default installation folder of /usr/local/seamonkey.

Now, the readme accompanying the program says that it must be first run as root. Except this doesn't work. If you do sudo su - and password and then run the shell script, it throws an error GTK+ cannot open display. Run" 

Running the install as root dose work. All you have to do is right click and chose run command and type in the command to where you unpacked the SeaMonkey setup files  for example 
/home/your name/seamonkey-1.0.7.en-US.linux-i686.installer/seamonkey/seamonkey.than click on 
options run as different user and enter your password After the installation is done you 
have to  run SeaMonkey one time as root  you enter in the command field /usr/local/seamonkey/seamonkey so it can set up the directories. Also Mozilla has script 
so you  can use Seamonkey as a different user, you don't need it. before you get done 
making the link  click on "Advance ->run as different user

Suzy

---

### Post by Kateikyoushi on 2007-01-12
Thanks I give it a try, as far as I knew there is no root account enabled by default but if that's the price I gladly pay it.

I tried to follow your instructions and it did not work. The seamonkey installer hangs and does not respond if I run it from root account, using sudo or my user account the installer window pops up and disappears after a second.

Any ideas ? Where should I look for the logs ? Tried var/etc/logs but could not find anything relevant.

Thanks in advance.

---

### Post by Kateikyoushi on 2007-01-13
Does not seem to work, neither as root nor sudo I get segfault.

I used alien to create a deb from the rpm, it installs the package but it won't run segfault again.

Where should I dig for logs to find out what is wrong ?

---

### Post by Kateikyoushi on 2007-01-19
There is an Iceape package for debian testing which I managed to install after upgrading a few packages from the debian testing repo, probably feisty packages would do the job.
I guess as the package gets to the ubuntu repos from the debian this is history.

---

### Post by lolwhites on 2007-02-13
I downloaded and extracted the tarball to the desktop and now have a folder called "seamonkey-installer". When I run the installation program I get asked if I want to create a folder usr/local/seamonkey, but when I click on "yes" I get the response "Error [-624]: Can't make destaination directory". Typing *sudo ./seamonkey* simply gets the message *command not found*.

I'm logged in as the administrator, so where am I going wrong?

---

### Post by lolwhites on 2007-02-24
Ooops, managed to get that one sorted in the end. I really should start reading these threads properly.

---

### Post by vincentvee on 2007-02-27
> **lolwhites said:**
> I downloaded and extracted the tarball to the desktop and now have a folder called "seamonkey-installer". When I run the installation program I get asked if I want to create a folder usr/local/seamonkey, but when I click on "yes" I get the response "Error [-624]: Can't make destaination directory". Typing *sudo ./seamonkey* simply gets the message *command not found*.

I'm logged in as the administrator, so where am I going wrong?
yeah the easiest way to do it is to right click on the installer and select copy, then open the terminal and type "sudo" then leave a space, then right click and select paste which will paste in the path to seamonkey installer then enter and password, it will run as root then and the folder can be created
My biggest problem is that now i cant find the command to launch it and there was no menu item installed by default, even thought the app is there, i keep lookin i guess

---

### Post by Nemix77 on 2007-03-01
Works great!  

How do I uninstall?

---

### Post by lotusleaf on 2007-03-31
[color=red]**EDIT 05-02-2007: I prefer and recommend nanotube's suggestion in the post below rather than using the installer!**[/color]

Since I don't see mozilla-browser or seamonkey in the Feisty repo as of this posting, I thought I'd try this out and install Seamonkey in Feisty beta.

I downloaded Seamonkey 1.1.1 and checked out the readme file for installing included with it. It says something in it about not running the installer with sudo because it may corrupt the profile, I asked around and was told that this wouldn't be a problem if I wasn't planning on using the updater. So, I installed using sudo and once installed, ran it from /usr/local/seamonkey/seamonkey with gksudo (as instructed to run as root or something to that effect in the readme for the first time following installation) and from there made a Launcher on the desktop to run it as a user (just pointing it to /usr/local/seamonkey/seamonkey and it runs just fine.

I haven't tried an uninstall yet. :)

Disclaimer: I'm just stating my experiences with this, I could've done something incorrect and if so please correct me, YMMV

---

### Post by nanotube on 2007-04-06
here's my simple two-step procedure for installing seamonkey that worked like a charm.

download seamonkey tar.gz - NOT the installer, just the tar.gz. you can get it if you go to "other systems and languages" and under linux they have the plain tar.gz option ([http://www.mozilla.org/projects/seamonkey/releases/](http://www.mozilla.org/projects/seamonkey/releases/))

extract the contents of the archive into /opt directory, with command:
```
sudo tar -C /opt -xzf seamonkey-1.1.1.en-US.linux-i686.tar.gz
```

then, all you have to do is run /opt/seamonkey/seamonkey as regular user and it is all good to go.

of course, feel free to add a shortcut to the panel or to your applications menu for extra convenience :) also feel free to substitute /usr/local instead of /opt, if you prefer. also feel free to add the path to wherever you install seamonkey to your $PATH.

i find this to be a much simpler procedure than fiddling around with the installer and permissions and stuff.

edit: and to uninstall, just delete the directory to where you extracted seamonkey - in my example, that would be /opt/seamonkey. what could possibly be simpler? ;)

---

### Post by lotusleaf on 2007-05-02
I tried it via nanotube's suggestion and it works very well. Perhaps the top post could be modified to include the info. nanotube provided?

---

### Post by sdowney717 on 2007-07-23
yes BUT, what about all the plugins??

I went to a site and it wants java 6

[http://nyctmc.org/](http://nyctmc.org/)

which I thought was installed


then cnn wants the flash plugin, which iis installed.

---

### Post by nanotube on 2007-07-24
the [ubuntuzilla project]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla") now includes the installation of seamonkey. this integrates the java and flash plugins from firefox, so you don't have any plugin problems. give it a go. :)

---

### Post by wnelson on 2007-07-28
If you have already install firefox to activate your plugins go into the directory where you installed seamonkey. For instance I install mine in /opt/seamonkey. Go to /opt/seamonkey/plugins and 'cp -s /usr/lib/firefox/plugins/* .'
this will create a copy of the symbolic links to you plugins.
I am not sure if this works without not already installing firefox and its plugins?

Walt
Tacoma, WA

---

### Post by nanotube on 2007-07-28
obviously, if firefox and plugins are not installed, that will not actually link to anything. 

also, it is better to just link the whole plugins directory in /opt/seamonkey to the firefox plugins dir. that way if you ever install new plugins, they will automatically be picked up by seamonkey. (this is what ubuntuzilla does.)

---

### Post by Varchild2021 on 2007-10-26
okay, so im a first tiem linux user, and having a hard time with installing seamonkey, obviously. 
so i downloaded the other seamonkey file, not the instal lone, and put in the command "/home/chris/seamonkey1.1/seamonkey-1.1.5.en-US.linux-i686.installer.tar.gz"
and now its asking for a password, but wont let me type anything in!
for clarification, there is only one accoutn, and its mine, and i have admin capabilities, so why does it need a password? and why isnt it accepting any text?
please help!

---

### Post by nanotube on 2007-10-26
> **Varchild2021 said:**
> okay, so im a first tiem linux user, and having a hard time with installing seamonkey, obviously. 
so i downloaded the other seamonkey file, not the instal lone, and put in the command "/home/chris/seamonkey1.1/seamonkey-1.1.5.en-US.linux-i686.installer.tar.gz"
and now its asking for a password, but wont let me type anything in!
for clarification, there is only one accoutn, and its mine, and i have admin capabilities, so why does it need a password? and why isnt it accepting any text?
please help!

if you are using ubuntu gutsy (7.10), seamonkey is in the repositories as package "iceape". that's the best way to install.

a general note about the password prompt in the shell: you can type stuff, it just wont appear. it's designed that way for security. so just type your password and hit enter.

---

### Post by MSchenker on 2007-10-26
I just installed 7.10, and I tried to find IceApe.  I see it listed in the repository, but it's ghosted out.  Can someone please tell me how to get it un-ghosted?

Thanks,
Matt

---

### Post by MSchenker on 2007-10-26
Sorry, I should have made it clear in my last message -- I am running Kubuntu 7.10.

---

### Post by jviscosi on 2007-10-26
> **MSchenker said:**
> Sorry, I should have made it clear in my last message -- I am running Kubuntu 7.10.

Try opening a terminal and running **sudo apt-get install iceape**.  A lot of times the output from that is more informative than synaptic.  (For instance it told me why update wasn't able to update gnome-themes-extras and some other packages -- there were conflicts with existing packages.)

---

### Post by ishwar on 2007-11-19
hi everyone.. i am not a expert . so pls consider my suggestions to be reviewed.. i am writting this because i managed to get the latest fire fox and seamonkey on my system.. i m glad it worked for me.. well now to the point. 

this all as per the ubuntu help page!

i followed the 
**Automated Install of the Latest Firefox**

by installing ubuntuzilla in the terminal.. rest all are taken care by ubuntuzilla package!!! but if u need to install you need to run the scripts from the terminal.. everything works perfect for me!! 

bellow are the useful links..
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

how to use ubuntuzilla details in the bellow link, including installation pacakges for ubuntuzilla.. 

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

good luck

---

### Post by Mel Thompson on 2007-11-25
Seamonkey won't install on most Ubuntu systems no matter what.

Try the rpm thing:  doesn't work.

Try the convert to deb thing:  doesn't work.

Try sudo:  doesn't work.

Try gksudo:  doesn't work.

Try apt-get:  doesn't work.

Sea Monkey is a good browser that works on every platform.
Windows, Mac, and an Linux system where it's pre-installed
with the system.

It's inexcusable that the folks at Seamonkey and Ubuntu
just added 1,000 security updates.  (I can't imagine the
time that took.)  But, as usual, a decade into this Linux
thing, and they, like all other distros just won't budge on
the issue of actually making a real installing system.  They
just won't.  Try googling "seamonkey" and "can't install."
There is something about installing:

Synaptic Package Manager:  Doesn't work.

RPM Package Installer:  Doesn't work.

They don't work and nobody's listening.

---

### Post by Mel Thompson on 2007-11-25
Ah yes, well, I was partly wrong.  It turns out there is a solution to get Seamonkey onto Ubuntu consistently.  (Some people get lucky and their
distro and their hardware all line up like dominoes, but most people
would have to have lightning strike to get so lucky.)

So the answer is, UBUNTUZILLA.  One goes to their website to find that
in order to solve another of the mountain of install problems that make
Linux almost absurd, they've in essence had to form an entire foundation
of volunteer and donators to patch up the mess.

Ubuntuzilla, fixes the Seamonkey install issue, and all the other major
Mozilla browser installs, like Firefox, etc. by creating an entire program
that does nothing but allow installs to go somewhat sanely between
Ubuntu and Mozilla.

Could you imagine, like in Mac or Windows, how people would react if
you told them:  First you get the operation system, then you get a word-
processor software, then you get software to get the word-processor and
the operating system to agree.  God help us.

Here's an idea.  How about the developers doing something like giving
the OS folks a call and working out the install without having to form whole
foundations for simple installations.  Just a thought.

---

### Post by nanotube on 2007-11-26
> **Mel Thompson said:**
> 
So the answer is, UBUNTUZILLA.  One goes to their website to find that
in order to solve another of the mountain of install problems that make
Linux almost absurd, they've in essence had to form an entire foundation
of volunteer and donators to patch up the mess.


well, while i'm glad that ubuntuzilla looks so professional :), i have to point out that it is not nearly as tremendous in scope as you make it out to be. it is not some kind of fancy foundation - it's just small software project that simplifies the "install official build of mozilla XX on ubuntu" process. 

thanks for your vote of confidence, though! :)

---

### Post by Major Squirrel on 2009-10-14
Hey Guys!!

So I was having the same problem before when I tried installing Seamonkey, but I found out that if you open terminal and type in

sudo apt-get install seamonkey

it not only installs it but also adds the shortcut to the internet application list!! It's so much easier this way :)

---

