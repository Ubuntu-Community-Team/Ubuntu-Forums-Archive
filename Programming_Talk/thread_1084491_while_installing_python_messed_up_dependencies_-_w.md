---
title: "while installing python messed up dependencies - way to solve?"
date: 2009-03-02
forum: Programming Talk
---

### Post by Claus7 on 2009-03-02
Hello,

I tried to install a new version of python in my system from source. The installation went ok, because if I typed :
python
in the command line, I was able to see that the version depicted was the right one.

Unfortunately this resulted in having in my system 86 missing dependencies. This was due to the fact that probably the installation of python was done "above" the old python. The process of installing python 2.5.2 was that I left the default paths. I wanted on purpose to install 2.5.2 above 2.4.3 because that way I thought that automatically I would be able to take advantage on the newest version and getting rid of the old one.

That seemed not to be the case, and this is where this thread takes place. I tried this thread before:
[http://ubuntuforums.org/showthread.php?t=955389](http://ubuntuforums.org/showthread.php?t=955389)
yet, the 86 missing dependencies still remained in synaptic. That would have been no real issue, if every time I opened synaptic and wanted to make a change it didn't prompt me to remove these 86 packages.

I didn't know exactly where to start...
My intention is to be able to restore my system back to normal, while understanding what this problem is all about. Apart from synaptic I can do everything I was doing before without any complaint from my system.

So I started like that. 

i)One command that people in the net propose for such things is :
sudo aptitude install -f

this command prompts me a lot of things and in the end to downgrade python. Yet, it also prompts me to get rid the 86 brocken packages, which I do not think is a good idea.

ii) Go to synaptic in Edit-> Fix Broken packages and hit apply. Nice, yet still this prompts me to get rid of 139 packages! So I avoid this solution as well.

iii) Another idea might be to go and uninstall from my system python 2.5.2. While I was installing it I did:
./configure
make 
make checkinstall
so, I can see this package in synaptic. An easy way to see it is to go to: Installed packages (localy or obsolete). Yet, even with that way, you guessed it, it prompts me to get rid of the 86 broken packages...

I tried to see one package of these 86 in order to check the information I could get from it. My thought was not so bad. I opened synaptic and saw the dependencies of this package (it was alacarte).
I went in its properties and saw that this one depended on python in the following way:
depends on: python (<2.5)
depends on: python (>=2.4)

On my surprise I found that if I type:
/usr/bin/alacarte
the program opens normaly.

It was clear to me that my way of installing python had created all this fuss(not python-my installation of it). This was more clear looking at the package:
python-xdg
which had only one depencency and it was the aforementioned one.

In the end typing:
sudo apt-get install --reinstall python

it produces an output of these 86 packages informing me that in each one of them the 2.5.2 version will be installed, yet these are depended on <2.5 (including the alacarte package).

Finding out that these packages are working I think that this is a configuration issue I should solve.
Is there any way that I can inform all these packages to restore back to normal their missing dependency? Having tried all these things I cannot see any other solution on how I will be able to restore my system.

Thank you,
Regards!

---

### Post by Claus7 on 2009-03-17
Hello,

I opened synaptic and went to the package python which had in its description:
Package created with checkinstall 1.6.0

In general I think that someone should go to the faulty package (the one he or she thinks that has caused the dependency problems). 

So I highlighted it and went in the option:
Package
(it's File Edit Package Configuration Help, as a direct translation from the hellenic language).
There it had the option Force version (just under the option Lock version). I chose it and it gave me two options:
The version of python I had installed and caused all these dependency issues (version 2.5)
and the default one for Dapper (version 2.4).
I checked the latter, waited a little and everything was back to normal. 

I hope that this might help.

Regards!

---

### Post by slavik on 2009-03-17
if you install things later on that replace currently installed things, you want to keep both and install a newer one in /usr/local/

this way if a script uses the old python, it will continue doing so, and if you want, you can still use the newer one.

---

