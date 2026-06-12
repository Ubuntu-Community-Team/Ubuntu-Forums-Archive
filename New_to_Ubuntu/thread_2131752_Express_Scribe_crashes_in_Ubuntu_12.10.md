---
title: "Express Scribe crashes in Ubuntu 12.10"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by budmoon on 2013-04-02
hi,

i'd appreciate any assistance offered.  i'm a newbie to ubuntu - i'm running 12.10.  i've been trying for days to get express scribe to run - either the linux version or the windows version with wine.

when i install the windows version with the wine program launcher, then try to open the app, i can see the express scribe program window behind a small button which states "Express Scribe Free Version - This free version of Express Scribe is licensed only for non-commercial use."  when i click the OK button, everything vanishes.

i've had no luck attempting to install the linux version either.  any suggestions would be greatly appreciated.

thank you :rolleyes: for helping this confused geekgrrl!

---

### Post by Kiddalee on 2013-04-19
Same here. I'm trying to run the Linux version of Express Scribe in Ubuntu 12.04. I've decompressed the tar.gz, and I've checked "Allow executing the file as a program." When I choose to "Run in terminal" it appears to run. The terminal asks me for my password and when I type it, and press Enter, the terminal simply closes. This is not the first shell script that I haven't been able to install things with.

---

### Post by budmoon on 2013-08-19
hi,
i originally posted the question in april 2013 about ubuntu crashing when i try to run express scribe.  i've come up with a solution which works great.  for me, wine has been problematic and unstable (perhaps it's user error?) - in any case, i've installed Oracle VirtualBox through ubuntu software center.  the app is extremely user-friendly.  after installation, it allowed me to install win xp (even though i lost my original license code).  it essentially functions (as its name implies) as a virtual OS.  when i want to run windows programs, i launch VirtualBox and open them from within the app.  i've used quite a few windows programs through VirtualBox and have had no problems.  i'm a big fan of VirtualBox :o
hope that helps a bit :-P

---

### Post by Vladlenin5000 on 2013-08-20
Extract the installation file - scribe - somewhere then open a terminal and CD to the path. Obs.: It's easier to just extract it to your personal folder (/home/<yourusername>); the terminal opens in that location by default. Then:

```
sudo ./scribe
```

It's then installed to /opt/nch/scribe/bin .

---

### Post by jessica-roberson on 2014-06-24
[B]::EDIT:: 06/25/2014 This originally worked perfectly, then after a restart, the program refused to open. So I navigated to the /.wine folder (it's hidden), then went to the NCH Software folder and found "scribe.exe". When I double clicked on it, the program automatically opened in Wine and runs. So I just copied the .exe file and made a folder in the home folder titled "Windows Launchers" to access it more easily. 
[/B]
Hello. I'm not sure if this will help now, since this is over a year old now, but I wrote a blog post today addressing this. I have been trying for weeks to get Express Scribe working on Ubuntu 14.04. The native Linux problem just didn't work (it would fast-forward instead of rewind, the play with auto-pausing never worked, and it would start 2:07 into the audio file). It was horrible, so it's obvi/ously buggy. 

However, I was having the same issue you described until about 2 weeks ago. My husband had installed a bunch of libraries and some Linux headers. We were actually trying to get VirtualBox to work rather than figuring out what was wrong in running it through Wine, and in the process, he got it to work through Wine. 

Now, I am a complete Linux newbie. So, some of this may not actually have to be done, but I did it anyway and it worked. I had to do a fresh install last night, and didn't follow these steps and got the same warning you were getting, so I did another fresh install today and got it to work using the following.

You can find the blog post here: [The Perils of Express Scribe]("http://confessionsofalinuxbeginner.wordpress.com/2014/06/25/the-perils-of-express-scribe/"), but I will post everything here for the sake of everyone else reading this.

First, I installed some libraries:
[PHP]sudo apt-get install libgtk2.0-0:i386 
sudo apt-get install lib32stdc++6
sudo apt-get install lib32z1
sudo apt-get install lib32ncurses5
sudo apt-get install lib32bz2-1.0
sudo apt-get install build-essential
sudo apt-get install libz-dev
sudo apt-get install libreadline-gplv2-dev:i386
sudo apt-get install libncursesw5-dev
sudo apt-get install libssl-dev
sudo apt-get install libgdbm-dev
sudo apt-get install libsqlite3-dev
sudo apt-get install libbz2-dev
sudo apt-get install liblzma-dev
sudo apt-get install tk-dev
sudo apt-get install libdb-dev
sudo apt-get install libc6-dev
[/PHP]

Then I installed some old headers:[PHP]sudo apt-get install linux-generic 
sudo apt-get install linux-headers-generic[/PHP]

Then I downloaded wine:
[PHP]sudo apt-get install wine[/PHP]

Then I downloaded [Express Scribe for Windows]("http://www.nch.com.au/components/essetup.exe").

Then I decided to do the following commands because my husband did them when it worked properly the first time, so I figured, why not?
[PHP]sudo apt-get update
sudo apt-get upgrade[/PHP]

Then I opened Wine, found my .exe file in the file manager, and installed Express Scribe. 

Works flawlessly for now. Not sure what those steps do/did, but it works now. And I'm also not sure if those will work for you or not. It's just what worked for me.

---

