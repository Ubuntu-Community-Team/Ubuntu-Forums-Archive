---
title: "Synaptic manager"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by 3v3rgr33n on 2011-10-01
:( I need  help! I just installed Linux yesterday. I have a Samsung RV510 pc, I installed Ubuntu 11.04. I wanted to listen to mp3's and it kept telling me something about mp3 plugins blah-blah (whatever that means). I've searched all over the net and nothing seems to work. I read somewhere that if you need to download stuff you use the Synaptic  manager.  Fortunately for me, i saw VLC listed in their list. I clicked on vlc, and i pressed the "use this source" button. I was looking good for about five sec and then i gave me some kind of Error, connection isn't established or something. the connection is excellent though, when i log on using windows the connection is awesome. i cant even connect to the internet with firefox, but frustratingly  it connects to the intranet. I dont understand all these command line prompts which dont seem to be helping. HELP!

---

### Post by Rasa1111 on 2011-10-01
Hi, 

Just open either Ubuntu software center, or synaptic package manager..

then seacrh for "ubuntu restricted extras"

and install it. 

Once it installs, accept the rems of use, and restart.

Then you can play your mp3's, videos, and anything else you want! :)

Good luck, hope it helps.

edit..
Are you using wireless or ethernet?

---

### Post by 3v3rgr33n on 2011-10-01
I have a wireless connection. I went to the "Software-Manager-thingie" you were talking about. I found what i was supposed to download. I clicked to download and was looking good, the following appeared ; "Updating Cache -- downloaded 0 B of 4 B". The "4 B" increased to "7 B" . Then the whole thing just stopped... told me, the respository connection failed. what should i do now, please help; I dont wana go back to Windows anymore!

---

### Post by Frogs Hair on 2011-10-01
It could be a temporary  problem on the other end . Have you tried again ?

---

### Post by dFlyer on 2011-10-01
> **3v3rgr33n said:**
> :( I need  help! I just installed Linux yesterday. I have a Samsung RV510 pc, I installed Ubuntu 11.04. I wanted to listen to mp3's and it kept telling me something about mp3 plugins blah-blah (whatever that means). I've searched all over the net and nothing seems to work. I read somewhere that if you need to download stuff you use the Synaptic  manager.  Fortunately for me, i saw VLC listed in their list. I clicked on vlc, and i pressed the "use this source" button. I was looking good for about five sec and then i gave me some kind of Error, connection isn't established or something. the connection is excellent though, when i log on using windows the connection is awesome. i cant even connect to the internet with firefox, but frustratingly  it connects to the intranet. I dont understand all these command line prompts which dont seem to be helping. HELP!

Open a terminal and enter the following command:

sudo apt-get update

sudo apt-get install ubuntu-restricted-extras

Than go to [http://www.medibuntu.org/](http://www.medibuntu.org/)

Download the following file: w32http://www.medibuntu.org than download w32codecs_20110131-0.1medibuntu3_i386.deb or the 64 bit version if your os is 64 bits.

you can install the package with 

sudo dpkg -i w32codecs_20110131-0.1medibuntu3_i386.deb

---

### Post by fantab on 2011-10-01
... or simply INSTALL** VLC MEDIA PLAYER** from UBUNTU SOFTWARE CENTER after **you make sure you are connected to the Internet.**

---

### Post by Abhinav Kumar on 2011-10-02
First check if u are getting wireless connection or not.
If u are using a proxy make sure you give proper IP at proper places . Also edit /etc/apt/apt.conf file by providing ur user name and password 
Then check for wireless driver on a system. Install the drivers by connecting through wired connection.
Update using sudo apt-get update with ur password.
Most of the audio formats that we counter are proprietary and therefore don't come with Ubuntu distribution. 
We have to later install these codecs later. once u run any song ,it will ask you to search for a suitable plug in.
 Once you have installed these drivers , u r gonna enjoy the music :P
Hope this works

---

### Post by 3v3rgr33n on 2011-10-04
> **dFlyer said:**
> Open a terminal and enter the following command:

sudo apt-get update

sudo apt-get install ubuntu-restricted-extras

Than go to [http://www.medibuntu.org/](http://www.medibuntu.org/)

Download the following file: w32http://www.medibuntu.org than download w32codecs_20110131-0.1medibuntu3_i386.deb or the 64 bit version if your os is 64 bits.

you can install the package with 

sudo dpkg -i w32codecs_20110131-0.1medibuntu3_i386.deb



I opened the terminal and entered the "sudo apt-get update" line. Its says theres a problem connecting to the repository. looks like theres something wrong with the connection. Im using a wireless connection and it's fine with windows. Is the line on linux you have to type in order to connect to the net.

---

### Post by Frogs Hair on 2011-10-04
If your web browser is working and the update manager is not , it is a repository connection problem . Sometimes changing the server connection in the update manager helps . Open the Update Manager > Settings > Ubuntu Software .

Go to  Download From select other from the menu . A dialog box will open , select choose best server and Ubuntu will check for the best server . This works for some users in certain locations .

---

### Post by technosysind on 2011-10-04
Have you tried downloading FFMPEG Codecs from Ubuntu Software Center? It should solve your problem.

---

### Post by audiomick on 2011-10-04
> **Frogs Hair said:**
> If your web browser is working .


Is your internet connection working properly? Can you get around in the internet with Firefox?

---

### Post by ajsoulmate on 2011-10-04
> **3v3rgr33n said:**
> the connection is excellent though, when i log on using windows the connection is awesome. i cant even connect to the internet with firefox, but frustratingly  it connects to the intranet. I dont understand all these command line prompts which dont seem to be helping. HELP!

Perhaps you have problems with your drivers? I mean network drivers!

---

