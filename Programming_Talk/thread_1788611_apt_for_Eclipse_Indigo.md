---
title: "apt for Eclipse Indigo?"
date: 2011-06-22
forum: Programming Talk
---

### Post by tedder on 2011-06-22
So Eclipse Indigo (3.7) was released today. I'd really love to upgrade it through eclipse rather than install it from a tarball. It's not there yet. Is there a PPA people are using, or what?

---

### Post by noah++ on 2011-06-23
I don't usually do this, but: ME TOO.

---

### Post by noah++ on 2011-06-27
[https://answers.launchpad.net/ubuntu/+source/eclipse/+question/162664](https://answers.launchpad.net/ubuntu/+source/eclipse/+question/162664)

---

### Post by VernonA on 2011-06-27
You don't really need a PPA with Eclipse since, like Firefox, the application runs entirely from its own directory. If you want to install it, and you know a bit about how Linux works, consider doing it this way:

i) At a cmd prompt type 'which eclipse', and you will probably be told /usr/bin/eclipse. (If you get nothing back, you don't have any version of Eclipse installed. Use the Software Centre to install one (it doesn't matter what it is) and start again at (i).)

ii) Go to the /usr/bin dir (or wherever else it said Eclipse was installed). Type 'cat eclipse' at the prompt and you will see this is actually a small shell-script which starts the real Eclipse binary located in /usr/lib/eclipse.

iii) To install another version of Eclipse, you need to download the gzip file, unzip it into, say, /usr/lib/eclipse_indigo, and update the shell-script to point to the new binary.

If the last instruction was too terse for you, let me expand it a bit. However, if you really had no clue what I was talking about you might need to wait for the PPA ;-)

a) Download the Indigo installer for Linux. There are various flavours depending upon what sort of a developer you are, but for Java on 32-bit Linux you would probably want eclipse-SDK-3.7-linux-gtk.tar.gz. Whatever you download, let's assume it's in your Downloads directory. If it is somewhere else, like your Desktop for example, adjust the instructions below.

b) Create a new directory using 'sudo mkdir /usr/lib/eclipse_indigo' at a prompt.

c) Unzip the .gz file contents into this newly created dir. You need to be root to do this, so use 'gksudo file-roller ~\Downloads\whatever.gz' to open a gui to the unzipper. Extract all the files in the eclipse dir to /usr/lib/eclipse_indigo. Note, don't install the eclipse dir itself into eclipse_indigo - install its contents.

d) OK you've done the bulk of the hard work. At a cmd prompt you should be able to type '/usr/lib/eclipse_indigo/eclipse' and Eclipse 3.7 will start. (If it doesn't, go to /usr/lib/eclipse_indigo and check it contains the Eclipse binary amongst other things. If it doesn't you did step (c) wrong.) The only nicety remaining is to edit the shell script in /usr/bin to point to 3.7 too. On my machine I keep old versions of Eclipse for support reasons, so I have scripts in bin called eclipse_3.4, eclipse_3.5 etc which point to Eclipse installs in /usr/lib/eclipse_gannymede, /usr/lib/eclipse_galileo etc. Then I have one shell called eclipse which points to the one I want to work with (normally the latest, but I sometimes revert to an older one if I have to). You can do this too if you want, but in your case, the simplest thing is probably to go to /usr/bin and make a copy of the script using 'sudo cp eclipse eclipse_old'. Then edit the current script using 'gksudo gedit eclipse' and change the line which declares ECLIPSE so it points to /usr/lib/eclipse_indigo/eclipse. You can also update any references to old versions of eclipse if you want (eg if it mentions getting updates from galileo, change them to say indigo too). You don't have to understand the file, just use common-sense.

Good luck!

---

### Post by livelite on 2011-07-29
Thanks VernonA!  Worked like a charm!

For those who don't need to keep the old version:

Rename the eclipse folder /usr/lib/eclipse to eclipse_3.5.
Then move into it's place the eclipse folder with 3.7 indigo from eclipse.org.
Once everything is verified working, remove the old /usr/lib/eclipse_3.5.

---

### Post by bcrudo on 2011-09-25
What about updating the repos in the shell script?


repositories/http\:__download.eclipse.org_releases_indigo/enabled=true
repositories/http\:__download.eclipse.org_releases_indigo/isSystem=false
repositories/http\:__download.eclipse.org_releases_indigo/nickname=Indigo Update Site
repositories/http\:__download.eclipse.org_releases_indigo/uri=http\://download.eclipse.org/releases/indigo/


Everywhere I saw Galileo I changed it to Indido, but is anyone sure what the links are?

---

