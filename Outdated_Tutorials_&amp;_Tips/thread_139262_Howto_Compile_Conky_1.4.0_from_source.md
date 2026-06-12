---
title: "Howto: Compile Conky 1.4.0 from source"
date: 2006-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by towsonu2003 on 2006-03-03
= **Howto Install Conky 1.4.0 from source code** =

Conky is a very nice system monitor and it works better for me than gdesklets. This my second ever compile, and it was extremely easy, thanks to the nice notifications by its developer. 

**First things first**:
```

cd
cp .conkyrc conkyrcbackup
sudo apt-get update
sudo apt-get remove conky
sudo apt-get install linux-headers-`uname -r` checkinstall build-essential libdbus-1-dev libdbus-glib-1-dev libxext-dev

```

**Go to** [http://conky.sourceforge.net/](http://conky.sourceforge.net/) and download conky-1.4.0.tar.gz to your Desktop

**Now compile and install**:
```

cd
mkdir temp
cp /path/to/conky-1.4.0.tar.gz ./
tar -xvf conky-1.4.0.tar.gz
cd conky-1.4.0
./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-xmms --enable-bmp --enable-audacious --enable-infopipe
make
sudo checkinstall

```

**Notes** (read): 
*man conky will tell you all about variables and configurations :PpP (bc I'm not a master of conky ;) )
*cp .conkyrc conkyrcbackup will work if you used conky before [backing up your conky configuration].
*sudo apt-get remove conky was necessary for checkinstall to work
*I used /home/user/temp as a temporary folder. You can delete it afterwords. 
*If you never used conky, you may want to search the forums on how to set up your .conkyrc configuration file. This compilation does not support bmpx (I don't know what it is) because I couldn't find it in the package manager (it's a dependency). 
*Let me know in this thread if you prefer me to include descriptions of the commands I used. 
*Some relevant forum threads to check out:
[http://www.ubuntuforums.org/search.php?searchid=4111292](http://www.ubuntuforums.org/search.php?searchid=4111292) will search conky in titles in the forum. 
[http://www.ubuntuforums.org/showthread.php?t=110535](http://www.ubuntuforums.org/showthread.php?t=110535) which has screenshots and sample configuration files that you can study and use.
[https://wiki.ubuntu.com/HowtoConky140](https://wiki.ubuntu.com/HowtoConky140) wiki link, just for the sake of it.

**To Uninstall**:
Open Synaptic, search for conky, and remove it :p

---

### Post by b3nw on 2006-04-11
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for X... no
checking for XdbeQueryExtension in -lXext... no
configure: error: something went wrong when checking for Xdbe (double buffer extension)

:( suggestions?

Load "dbe" is in my xorg.conf

---

### Post by towsonu2003 on 2006-04-11
[QUOTE=b3nw]checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for X... no
checking for XdbeQueryExtension in **-lXext**... no
configure: error: something went wrong when checking for Xdbe (double buffer extension)

:( suggestions?

Load "dbe" is in my xorg.conf[/QUOTE]
I am not sure but try after doing these:
```
sudo apt-get update
sudo apt-get install libxext-dev
```
let me know if it works so I fix the howto :)

bf starting to recompile (again), after going to your /home/username/temp/conky-1.4.0, do ```
make clean
``` just in case. Than you'll do the usual stuff of ```
./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-xmms --enable-bmp --enable-audacious --enable-infopipe
make
sudo checkinstall
```

---

### Post by ranf on 2006-04-11
[QUOTE=towsonu2003]
**Now compile and install**:
```

cd
mkdir temp
cd Desktop
cp conky-1.4.0.tar.gz temp
cd temp
...

```
[/QUOTE]
Hmm either create `temp' under `Desktop' or copy and cd to `~/temp'.

---

### Post by towsonu2003 on 2006-04-11
[QUOTE=ranf]Hmm either create `temp' under `Desktop' or copy and cd to `~/temp'.[/QUOTE]
fixed, thanks :)
it's ~/temp

---

### Post by 5-HT on 2006-04-24
Thanks for posting this! :D

One small problem though, I cannot get xft fonts to work. 
```
Conky: Xft not enabled 
``` 

I do have it enabled in my .conkyrc though
```
use_xft yes 
``` 

I followed the How To's suggestions, so the Xft support should have been enabled on conky's side of things. 

Any ideas? :-k

If it helps: Breezy running a standard install + xubuntu-desktop with a 686 kernel (anything else I could add that would be of help?).

---

### Post by towsonu2003 on 2006-04-24
[QUOTE=5-HT]
One small problem though, I cannot get xft fonts to work. 
```
Conky: Xft not enabled 
``` 

I do have it enabled in my .conkyrc though
```
use_xft yes 
``` 
[/QUOTE]
uhm, sorry I don't know. did the compilation exited without errors? xft support was compiled to conky, but don't know why it wouldn't enable it...

---

### Post by towsonu2003 on 2006-05-02
for those whose conky flickers (blinks on every refresh), I filed a [bug report here]("https://launchpad.net/distros/ubuntu/+source/conky/+bug/42467") as well as the workaround (which was also posted by the 2nd replier of this thread) of loading dbe. please [comment to it]("https://launchpad.net/distros/ubuntu/+source/conky/+bug/42467") if you have any feedback. 
thanks

[quote=5-HT]One small problem though, I cannot get xft fonts to work.
Code:

Conky: Xft not enabled
[/quote]
I just realized that I don't have xft enabled in my conkyrc. but when enable it, it works. as I mentioned, the compiled conky (as well as breezy's and dapper's conky) have xft enabled during compilation. sorry I couldn't help.

---

### Post by 5-HT on 2006-05-04
[quote= towsonu2003]I just realized that I don't have xft enabled in my conkyrc. but when enable it, it works. as I mentioned, the compiled conky (as well as breezy's and dapper's conky) have xft enabled during compilation. sorry I couldn't help.[/quote]

No worries. I'm not going to bother looking into this anymore as playing around with xfontsel got me a nice looking font. Thanks again for the HOW TO.

---

### Post by daedalusman on 2006-05-08
Where can I find the default conkyrc file? I installed conky 1.4.1 from source and started it before a .conkyrc file was created in my home folder and it wasn't using the sample config file either. I have posted some screen shots of what I mean. Thanks for the help.

---

### Post by benplaut on 2006-05-08
[QUOTE=daedalusman]Where can I find the default conkyrc file? I installed conky 1.4.1 from source and started it before a .conkyrc file was created in my home folder and it wasn't using the sample config file either. I have posted some screen shots of what I mean. Thanks for the help.[/QUOTE]

it's hidden way back in /usr/share/doc/conky/examples/conkyrc.sample.gz

here's mine, taking advantage of the ability to put objects on top of each other:

---

### Post by daedalusman on 2006-05-08
I actually don't have that folder. And I'm not looking for the sample config, I'm looking for the config that displays what is shown the the "defaultconkyrc.png". It's different than the sample config.

---

### Post by towsonu2003 on 2006-05-08
> And I'm not looking for the sample config, I'm looking for the config that displays what is shown the the "defaultconkyrc.png". It's different than the sample config.I'm wondering the same thing (didn't have time to check out conky's site).

---

### Post by benplaut on 2006-05-08
i'm afraid i don't know which one you mean...

i could try and recreate it, if you want

---

### Post by daedalusman on 2006-05-08
[QUOTE=benplaut]i'm afraid i don't know which one you mean...

i could try and recreate it, if you want[/QUOTE]


Thanks but thats alright, Its not that big a deal. I have mine just about how I want it now and figured out most of what I was looking for. I just need to fiddle with a couple of things and I get lm_senors working with dapper and I will have it perfect. But thanks for the offer.

---

### Post by towsonu2003 on 2006-05-08
[QUOTE=benplaut]i'm afraid i don't know which one you mean...

i could try and recreate it, if you want[/QUOTE]
I think I know... Imagine you just installed conky and you do not have _any_ .conkyrc files laying around. When you run conk, it uses an unknown configuration file that doesn;t get created as ~/.conkyrc... When you close conky, you can't find what configuration file it just used... Maybe it's hardcoded to its source? No clue. If I knew what/where to find that file, finding a fix to this would be so much easy: [https://launchpad.net/distros/ubuntu/+source/conky/+bug/42467](https://launchpad.net/distros/ubuntu/+source/conky/+bug/42467)

---

