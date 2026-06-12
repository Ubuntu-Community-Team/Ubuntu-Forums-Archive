---
title: "Installing applications"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by jed1347 on 2013-03-21
i have just switched from windows to Ubuntu12.04. i have no idea what i am doing. tryid to install a program but god knows how to. need help. want to install iplist. i have unpacked it but what to do now?? its not like win click on a icon and start instllation...i am bit lost.

---

### Post by Cheesemill on 2013-03-21
Take a read of this...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by ibjsb4 on 2013-03-21
Hi jed, welcome to the forums :)

To install software just go to the "Software Center" and pick what you want to install.  Is there some program that is giving you trouble?

---

### Post by jed1347 on 2013-03-21
Yeah thanks for reply. trouble with iplist, or peerguardian...and  every soft i download manually no Software Center. as said i am Very NEw to Ubuntu. command line = magic:)  at the moment just need something that will  filter my outgoing signal

---

### Post by ibjsb4 on 2013-03-21
You should stick with the Software Center untill you are more familiar with Ubuntu.  Do you wish to install a firewall?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=firewall+software+apps&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=firewall+software+apps&sa=Search&cof=FORID:9)

---

### Post by jed1347 on 2013-03-21
Got gufw enabled:) but it doestn filter ips.

---

### Post by bfmetcalf on 2013-03-21
They have some instructions on their website to enable a new PPA to use the software center or apt-get to install, with what you downloaded though I would guess you need to build the package so this should do it (I am assuming you have the tar.bz2 file in your ~/Downloads folder, you will need to change the code accordingly).  This should work, but I'm not on a computer I can look at it good with so I can't be fore sure.

in a terminal you will use these commands...
```
cd ~/Downloads
```
to get into your downloads directory
```
tar xvf iplist-0.29.tar.bz2
```
to unpack it (I think you have already done this, but thought I'd throw it in there)
```
cd iplist-0.29
```
to get inside the iplist source folder
```
./configure
```
to set up your build configurations
```
make
```
to build the package
```
make install
```
to install the package

You will need to keep the package up to date building form source like this yourself as the package manager will not know it's there, so adding the PPA is probably the better way, but building it should install it.  Also you may need to install some packages to use make, I'm not sure exactly which ones on Ubuntu though.

---

### Post by jed1347 on 2013-03-21
that doesnt work :( i have unpacked it, got inside dir..and thats it...

---

### Post by DuckHook on 2013-03-21
You are attempting to learn how to fly by starting out on a 747. This is most definitely not how to begin.

One of the big advantages of Ubuntu is its repositories. There is really nothing that a new user need or should go outside of the repositories for. In your case, specifically, IPtables are managed through UFW. The GUI front end is GUFW. It is downloaded from the repositories either through Software Center of by doing```
sudo apt-get install gufw
```
The whole download-from-I.own.you.com practice is a Windows convention that is one of the many reasons it is a rollicking malware playground. Please listen to @Cheesemill as he is very knowledgeable. I too highly recommend the link he has given you.

To filter IPs using UFW read [this]("http://ubuntuforums.org/showthread.php?t=823741") How-To.

---

### Post by sefs on 2013-03-22
Are you on 64-bit?

There's a 64 bit deb available that you can just double click on to in stall here... [http://sourceforge.net/projects/iplist/files/iplist/0.29/](http://sourceforge.net/projects/iplist/files/iplist/0.29/)

Where did you get your package from.

---

### Post by Frogs Hair on 2013-03-22
Ubuntu Manual:  [http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)

---

### Post by jed1347 on 2013-03-22
unfortunately is x86. yes i did saw that package on sourceforge website.

---

### Post by alphaamanitin on 2013-03-22
> **Frogs Hair said:**
> Ubuntu Manual:  [http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)


Might as well have said RTFM...

Geez, I thought Ubuntu was supposed to be the helpful place.

Seriously, though, take the advice of others and stick to the software center until you have learned more about linux.

AlphaA

---

### Post by oldos2er on 2013-03-22
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

What program are you trying to install?

---

### Post by DuckHook on 2013-03-22
> **oldos2er said:**
> What program are you trying to install?

From what I can gather, OP is just trying to configure his firewall and under the mistaken impression that GUFW won't do what he wants it to.

> **jed1347 said:**
> Got gufw enabled but it doestn filter ips.

Therefore, he is trying to download and install an alternate app. I've mentioned that:

1. GUFW does indeed filter IPs, and
2. It is not a good idea for new users to go outside of the repositories, much less compile a new program from source.

@OP

If you don't like GUFW, you can try *Firewall Builder*, which is also available in the repos and can be downloaded by doing:```
sudo apt-get install fwbuilder
```I use *fwbuilder* to build my rules set for my router which has been converted to dd-WRT and it works quite nicely. Documentation like users manual and tutorials can be downloaded straight from their [site]("http://www.fwbuilder.org/4.0/documentation.html") and are very clear and helpful with plenty of examples. ***REPEAT*** Do not download the app from the site--only the docs. Downloading apps outside of the repos is a bad Windows practice that is neither safe nor necessary.

---

### Post by oldos2er on 2013-03-22
> **DuckHook said:**
> From what I can gather, OP is just trying to configure his firewall and under the mistaken impression that GUFW won't do what he wants it to.

Thanks. For some reason none of the replies showed when I read the OP.

---

### Post by jed1347 on 2013-03-22
ok. i might messed up things a little bit. but i have never mantion i want to set up my firewall or even build it i just wanted to install peerguardian or ipblock or iplist program that can fillter information or whatever so i can safely use transmission or any other p2p software that deals with torrents...so i have found it on the source forge website but got trouble to install it. couse i dont know how couse i am new to that stuff all that command line, packages compilation or whatever else. so didi ask for help installing this ipblock thingy i was useing for years under windows only 2 clicks away,  i did ask for few lines of code/commands how to get this stuff working. is it realy that much??? though Ubuntu was made by people for people not for people that know how to use linux. and also ubuntu forums supposed to be place where people like me newbies could find help "How To" but so far only few of You, familiar with this OS was acctually bothered to read carefully my post and give seriouse advice, help with a code. which whom i am thankfull...

---

### Post by 3rdalbum on 2013-03-23
Then what you want is a blocklist for Transmission, not a whole new firewall builder.

A quick Google search should yield some URLs for Transmission blocklists. Paste the URL into the Transmission preferences window and it will keep you safe.

---

