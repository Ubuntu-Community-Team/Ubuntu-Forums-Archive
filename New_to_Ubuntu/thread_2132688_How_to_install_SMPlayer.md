---
title: "How to install SMPlayer?"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Ashfaqur Rahman on 2013-04-05
Hello!
I am absolutely new to ubuntu.

I have visited SMPlayer site they have told to install SMPlayer by this code

```

[COLOR=#333333][FONT=Menlo]sudo add-apt-repository ppa:rvm/smplayer[/FONT][/COLOR]
sudo apt-get update 
[COLOR=#333333][FONT=Menlo]sudo apt-get install smplayer smtube smplayer-themes smplayer-skins
[/FONT][/COLOR]
```

But I cant connect internet in my Laptop( Which is using ubuntu ). So I want to download SMPlayer in my desktop first and then install SMPlayer in my laptop.How Can I Do That?

---

### Post by savi3000 on 2013-04-05
You need to connect to the Internet to download packages. Unless you want to install manually, which is probably too advanced for you at this time

---

### Post by Ashfaqur Rahman on 2013-04-05
Can U Explain Or Give Me A Link How To Install Manually I Want To Try.
I am already acquainted with .deb files.And I have installed some.

---

### Post by savi3000 on 2013-04-05
You'd need to compile this: [http://downloads.sourceforge.net/smplayer/smplayer-0.8.4.tar.bz2](http://downloads.sourceforge.net/smplayer/smplayer-0.8.4.tar.bz2)

Out of curiosity, why can't you use an internet connection on your laptop ?

---

### Post by Ashfaqur Rahman on 2013-04-05
The Problem Is My Internet Modem Is Not Connecting.I Have Installed The Driver (A tarball) In Ubuntu Which Is Provaided With It.Its successfully installed.But The Driver Isnt Working In Ububtu.So I Cant Connect My Internet Modem. :(

But the modem is working well in the desktop( Win 8 OS ).So, I Am Doing This.

And Thanks For The Link.Lets See If I Can Compile This.

---

### Post by Ashfaqur Rahman on 2013-04-05
"Install.txt" Is This The Guide?? ](*,) @savi3000
Ok I Am Trying! :cool:

---

### Post by Isamu715 on 2013-04-05
If you want to install manually go to [this site]("https://launchpad.net/~rvm/+archive/smplayer/+packages") and download the deb files for *smplayer*, *smtube*, *smplayer-themes* and *smplayer-skins*. Depending on your Ubuntu version - if you're running 12.04 it will be the "precise" ones, 12.10 is "quantal" and 13.04 is "raring". Also remember to choose the correct build for your architecture - i386 for 32-bit and amd64 for 64-bit. After you download all the correct packages install them with Software Center.

---

### Post by Ashfaqur Rahman on 2013-04-05
I am using Ubuntu Desktop 12.10 32bit.

---

### Post by Isamu715 on 2013-04-05
Here you go: [smplayer]("https://launchpad.net/~rvm/+archive/smplayer/+files/smplayer_0.8.4-1%7Equantal1_i386.deb"), [smtube]("https://launchpad.net/~rvm/+archive/smplayer/+files/smtube_1.6-1%7Equantal1_i386.deb"), [smplayer-themes]("https://launchpad.net/~rvm/+archive/smplayer/+files/smplayer-themes_20120919-1%7Equantal1_all.deb") and [smplayer-skins]("https://launchpad.net/~rvm/+archive/smplayer/+files/smplayer-skins_20121029-1%7Equantal1_all.deb") ;)

---

### Post by Ashfaqur Rahman on 2013-04-05
I Have Downloaded All The Debian Pakages You Gave Link. But When I Tried To Install Those Through Software Centre Its Showing Dependency Problem :(
What Can I Do Now?

---

### Post by Isamu715 on 2013-04-05
What dependencies is it missing exactly? Installing the packages in different order may help. I'd say start with themes and skins, then smtube with smplayer itself being the last package installed.

---

### Post by Ashfaqur Rahman on 2013-04-05
1. For SMPlayer Its Saying " Dependency Not Satisfiable: mplayer|mplayer-nogui|mplayer-mt|mplayer2  "
2. For SMplayer Skin Its Saying " Dependency Not Satisfiable: smplayer "
3. For SMPlayer Theme Its Saying " Dependency Not Satisfiable: smplayer "
4. For SMtube its saying " Only Install if you trust " but i cant click on the install tab!!!

---

### Post by stinkeye on 2013-04-05
You may need to also download mplayer2. (smplayer is a front-end for MPlayer)
Try placing all your deb downloads in a folder named smplayer in your home directory.
Open a terminal and run...
```
cd smplayer; sudo dpkg -i *.deb
```

---

### Post by Dennis N on 2013-04-05
smplayer is a front end for mplayer, so you need to install mplayer, plus a number of other dependencies which may or may not be on your system. If you had internet connection, all those dependencies would be pulled in as needed by the installer.

Try **apt-cache showpkg  smplayer** to see the dependencies.

Installing from the internet is the way to go. I would wait till I had internet. Just sayin'.

---

### Post by Ashfaqur Rahman on 2013-04-05
Stinkey, It Works!!
Now I Can Find SMPlayer When I Right Click On Video/Audio.But When Installing It Gives Following Errors In Terminal

dependency problem prevent configuration of smplayer:
smplayer depend on mlayer| mplayer nogui | mplayer-mt | mplayer2
pakage mlayer is not installed.
pakage mplayer nogui is not installed.
pakage mplayer-mt is not installed.
pakage mplayer2 is not installed.
dpkg: error processing smplayer(--install):
 dependency problem - leaving unconfigured

as package smplayer is not configured yet dependency prevent configuration of smplayer-skin and smplayer-theme.
Now What should I Do.Should I Download and install those dependency?

---

### Post by Ashfaqur Rahman on 2013-04-05
With This Code:
```
apt-cache showpkg smplayer
```
I Have Found What Dependency I Have To Download. Thanks.
But The Problem Is After Downloading Those Dependencies When I Will Try To Install Them I Will See That They Have Also Some Dependency!!! :P @Dennis N

---

### Post by stinkeye on 2013-04-05
> **Ashfaqur Rahman said:**
> With This Code:
```
apt-cache showpkg smplayer
```
I Have Found What Dependency I Have To Download. Thanks.
But The Problem Is After Downloading Those Dependencies When I Will Try To Install Them I Will See That They Have Also Some Dependency!!! :P @Dennis N

...and that's what your facing...
I would be looking at fixing your laptops internet connectivity.

Also have a read of this documentation
_[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)_
Using the method here using a live cd (of the same release) will pull in package dependencies not included in a default install.

---

### Post by Dennis N on 2013-04-05
> **Ashfaqur Rahman said:**
> With This Code:
```
apt-cache showpkg smplayer
```
... The Problem Is After Downloading Those Dependencies When I Will Try To Install Them I Will See That They Have Also Some Dependency!!! :P @Dennis N

That's why we use package managers. They do all the dependency chasing and installing for you. With persistence you may be successful in the end.

---

### Post by Ashfaqur Rahman on 2013-04-05
I Have Installed My Internet Modem's Driver Successfully.(After Downloading at least 10 Dependency :) )
Modem Also Connect Twice. Now When I Insert Modem To USB Port The Driver Open.It Shows Initializing Status But Dont Initialize And Cant Detect Modem :(
One Time It Gives Following Errors:

[B][COLOR=#333333]MSISDN: Not Found
IMSI: Not Found
IMEI: Not Found[/COLOR][/B]

---

### Post by Ashfaqur Rahman on 2013-04-06
At Last Found A Way To Connect To The Internet.Found A Clue From Terminal.If I First Open Driver Software And Then Insert Modem Then Driver Works.

But Still I Cant Install SMPlayer!! :(
After Connecting To Internet I Have Tried With Following Code As They Said

```


sudo add-apt-repository ppa:rvm/smplayer sudo apt-get update sudo apt-get install smplayer smtube smplayer-themes smplayer-skins
```

But Its Giving Following Information In The Terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
smtube is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 smplayer : Depends: mplayer but it is not installable or
                     mplayer-nogui but it is not installable or
                     mplayer-mt but it is not installable or
                     mplayer2 but it is not installable
E: Unable to correct problems, you have held broken packages.

What Can I Do Now?

---

### Post by Ashfaqur Rahman on 2013-04-06
Solved!
First I Have Downloaded MPlayer
```
sudo apt-get install mplayer
```

Then Install SMPlayer With Following Code:
```


sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update
sudo apt-get install smplayer smtube smplayer-themes smplayer-skins

```

It Installed Successfully!

---

