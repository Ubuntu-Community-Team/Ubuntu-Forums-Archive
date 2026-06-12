---
title: "uninstalling aircrack on 12.04"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by mootaph on 2012-06-20
hi friends, i want to uninstall aircrack-ng 1.1 but i can not. when i try in terminal, it says "Virtual packages like 'aircrack-ng' can't be removed". how to uninstall?

---

### Post by CharlesA on 2012-06-20
How did you install it in the first place?

I don't believe it is in the Ubuntu repos.

---

### Post by mootaph on 2012-06-20
> **CharlesA said:**
> How did you install it in the first place?

I don't believe it is in the Ubuntu repos.

It was not in the Ubuntu repos. So i installed like there: [http://www.riyazwalikar.com/2010/12/installing-aircrack-ng-on-ubuntu-1204.html](http://www.riyazwalikar.com/2010/12/installing-aircrack-ng-on-ubuntu-1204.html)

---

### Post by CharlesA on 2012-06-20
Check the instructions in the tar.gz you installed.

---

### Post by mootaph on 2012-06-20
> **CharlesA said:**
> Check the instructions in the tar.gz you installed.

There is no instructions in the tar.gz. only it says "make uninstall".

---

### Post by wildmanne39 on 2012-06-20
Hi, change into the directory that it is installed into then this should get rid of it:
```
make clean
sudo make uninstall

```

---

### Post by mootaph on 2012-06-20
sorry but how can i do it? i don't know where the program installed and where is running. :(

---

### Post by Mopar1973Man on 2012-06-20
Actually AirCrack is listed in the Synaptic Package Manager and it will install and uninstall it for you.

```
sudo apt-get install synaptic
```

---

### Post by mootaph on 2012-06-20
no sir, it is not in the synaptic.

---

### Post by Curtis6767 on 2012-06-20
```
whereis aircrack
```

Try that. You'll probably have to get the name perfect so if it is **aircrack-ng1.1**, then type that in exactly.

---

### Post by mootaph on 2012-06-21
> **Curtis6767 said:**
> ```
whereis aircrack
```Try that. You'll probably have to get the name perfect so if it is **aircrack-ng1.1**, then type that in exactly.

yes i tried it but not helped. perfect name "aircrack". then i tried that : sudo apt-get remove aircrack. but terminal said that E: unable to locate package aircrack.

please, i don't know how to fix the problem. help me.

---

### Post by CharlesA on 2012-06-21
> **wildmanne39 said:**
> Hi, change into the directory that it is installed into then this should get rid of it:
```
make clean
sudo make uninstall

```
This is the way to uninstall a program compiled from source.

I doubt it will be listed in synaptic or any other package manager.

---

### Post by mootaph on 2012-06-21
> **CharlesA said:**
> This is the way to uninstall a program compiled from source.

I doubt it will be listed in synaptic or any other package manager.

when i write in terminal it says:

```
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~$ make clean
make: *** No rule to make target `clean'.  Stop.
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~$ sudo make uninstall
[sudo] password for yusuf: 
make: *** No rule to make target `uninstall'.  Stop.
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~$ 
```

and it is not listed in synaptic.

---

### Post by CharlesA on 2012-06-21
You need to run it from the aircrack-ng-1.1 folder you unzipped from the tar.gz file.

---

### Post by mootaph on 2012-06-21
> **CharlesA said:**
> You need to run it from the aircrack-ng-1.1 folder you unzipped from the tar.gz file.

how can i do it? i tried, it is in the home folder. first is tar.gz and second is folder. in the folder there are executable icons. i clicked aircrack-ng but not work.

---

### Post by CharlesA on 2012-06-21
```
cd ~/aircrack-ng-1.1
make clean
sudo make uninstall
```

---

### Post by mootaph on 2012-06-21
> **CharlesA said:**
> ```
cd ~/aircrack-ng-1.1
make clean
sudo make uninstall
```

thank you very much, sir. (i think) it s deleted the aircrack:

```
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~$ cd ~/aircrack-ng-1.2.1
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~/aircrack-ng-1.2.1$ make clean
make -C src clean
make[1]: Entering directory `/home/yusuf/aircrack-ng-1.2.1/src'
make -C osdep clean
make[2]: Entering directory `/home/yusuf/aircrack-ng-1.2.1/src/osdep'
make -C radiotap clean
make[3]: Entering directory `/home/yusuf/aircrack-ng-1.2.1/src/osdep/radiotap'
rm -f *.o
make[3]: Leaving directory `/home/yusuf/aircrack-ng-1.2.1/src/osdep/radiotap'
rm -f libosdep.a  *.o .os.*
make[2]: Leaving directory `/home/yusuf/aircrack-ng-1.2.1/src/osdep'
rm -f aireplay-ng airodump-ng airserv-ng airtun-ng airbase-ng aircrack-ng airdecap-ng packetforge-ng ivstools kstats makeivs-ng airdecloak-ng aircrack-ng-opt-prof_gen aircrack-ng-opt aircrack-ng-opt-prof prof/* airolib-ng *.o wesside-ng tkiptun-ng easside-ng buddy-ng
make[1]: Leaving directory `/home/yusuf/aircrack-ng-1.2.1/src'
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~/aircrack-ng-1.2.1$ sudo make uninstall
[sudo] password for yusuf: 
make -C src uninstall
make[1]: Entering directory `/home/yusuf/aircrack-ng-1.2.1/src'
make -C osdep uninstall
make[2]: Entering directory `/home/yusuf/aircrack-ng-1.2.1/src/osdep'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/home/yusuf/aircrack-ng-1.2.1/src/osdep'
rm -f /usr/local/bin/aircrack-ng
rm -f /usr/local/bin/airdecap-ng
rm -f /usr/local/bin/packetforge-ng
rm -f /usr/local/bin/airolib-ng
rm -f /usr/local/bin/ivstools
rm -f /usr/local/bin/kstats
rm -f /usr/local/bin/buddy-ng
rm -f /usr/local/sbin/airodump-ng
rm -f /usr/local/sbin/airserv-ng
rm -f /usr/local/sbin/airtun-ng
rm -f /usr/local/sbin/aireplay-ng
rm -f /usr/local/sbin/wesside-ng
rm -f /usr/local/sbin/easside-ng
rm -f /usr/local/sbin/airbase-ng
rm -f /usr/local/bin/makeivs-ng
rm -f /usr/local/sbin/airdecloak-ng
rm -f /usr/local/sbin/tkiptun-ng
rm -rf /usr/local/etc/aircrack-ng 
make[1]: Leaving directory `/home/yusuf/aircrack-ng-1.2.1/src'
rm -fr /usr/local/share/doc/aircrack-ng
make -C manpages uninstall
make[1]: Entering directory `/home/yusuf/aircrack-ng-1.2.1/manpages'
rm -f /usr/local/man/man1/aircrack-ng.1
rm -f /usr/local/man/man1/airdecap-ng.1
rm -f /usr/local/man/man1/airdriver-ng.1
rm -f /usr/local/man/man1/aireplay-ng.1
rm -f /usr/local/man/man1/airmon-ng.1
rm -f /usr/local/man/man1/airodump-ng.1
rm -f /usr/local/man/man1/airserv-ng.1
rm -f /usr/local/man/man1/airtun-ng.1
rm -f /usr/local/man/man1/ivstools.1
rm -f /usr/local/man/man1/kstats.1
rm -f /usr/local/man/man1/makeivs-ng.1
rm -f /usr/local/man/man1/airbase-ng.1
rm -f /usr/local/man/man1/packetforge-ng.1
rm -f /usr/local/man/man1/airdecloak-ng.1
rm -f /usr/local/man/man1/airolib-ng.1
rm -f /usr/local/man/man1/wesside-ng.1
rm -f /usr/local/man/man1/tkiptun-ng.1
rm -f /usr/local/man/man1/buddy-ng.1
rm -f /usr/local/man/man1/easside-ng.1
make[1]: Leaving directory `/home/yusuf/aircrack-ng-1.2.1/manpages'
make -C scripts uninstall
make[1]: Entering directory `/home/yusuf/aircrack-ng-1.2.1/scripts'
rm -f /usr/local/sbin/airmon-ng
rm -f /usr/local/sbin/airdriver-ng
rm -f /usr/local/sbin/airodump-ng-oui-update
make[1]: Leaving directory `/home/yusuf/aircrack-ng-1.2.1/scripts'
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~/aircrack-ng-1.2.1$ 
```

it is right?

but in home folder there are aircrack and tar.gz folders. and in this directory there is airdecloak-ng : /usr/local/bin

can i manually delete them?

---

### Post by CharlesA on 2012-06-21
Yes. You can delete those two.

Please mark the thread as solved from thread tools. :)

---

### Post by mootaph on 2012-06-21
> **CharlesA said:**
> Yes. You can delete those two.

Please mark the thread as solved from thread tools. :)

last thing, please :) airdecloak working. when i write the name in terminal it is working. so what i can do?

---

### Post by wildmanne39 on 2012-06-21
Hi, how to get aircrack and airdecloak working is no longer a supported topic on the forum, it is best discussed on the backtrack forum .
Thanks

---

### Post by mootaph on 2012-06-21
> **wildmanne39 said:**
> Hi, how to get aircrack and airdecloak working is no longer a supported topic on the forum, it is best discussed on the backtrack forum .
Thanks

i don't know but where is the backtrack forum?

---

### Post by wildmanne39 on 2012-06-21
Hi, it is here.
[http://www.backtrack-linux.org/forums/forum.php?](http://www.backtrack-linux.org/forums/forum.php?)
Thanks

---

### Post by mootaph on 2012-06-21
> **wildmanne39 said:**
> Hi, it is here.
[http://www.backtrack-linux.org/forums/forum.php?](http://www.backtrack-linux.org/forums/forum.php?)
Thanks

i saw this but i can't write there. please, i just want to delete this program and why it is now in my computer i don't know. i deleted aircrack and deleted other programs. only airdecloak. i'm very bored :( it is in this directory:  /usr/local/bin/airdecloak-ng

if i delete it, it wil be dangerous?

thanks.

---

### Post by wildmanne39 on 2012-06-21
Hi, okay I see sorry for the misunderstanding try:
```
rm -f /usr/local/sbin/airdecloak-ng
```
copy and paste for accuracy.
Thanks

---

### Post by mootaph on 2012-06-21
> **wildmanne39 said:**
> Hi, okay I see sorry for the misunderstanding try:
```
rm -f /usr/local/sbin/airdecloak-ng
```copy and paste for accuracy.
Thanks

hi, i tried. in the third trying i wrote:  rm -f /usr/local/bin/airdecloak-ng. because program is in not "sbin" but in "bin" folder. 

```
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~$ rm -f /usr/local/sbin/airdecloak-ng
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~$ rm -f /usr/local/sbin/airdecloak-ng
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~$ rm -f /usr/local/bin/airdecloak-ng
rm: cannot remove `/usr/local/bin/airdecloak-ng': Permission denied
yusuf@yusuf-Lenovo-IdeaPad-S10-2:~$ 

```

---

### Post by CharlesA on 2012-06-21
```
sudo rm -v /usr/local/sbin/airdecloak-ng
```

Generally this is not the best way to remove a program, though.

---

### Post by mootaph on 2012-06-21
> **CharlesA said:**
> ```
sudo rm -v /usr/local/sbin/airdecloak-ng
```Generally this is not the best way to remove a program, though.

yes, it's removed now. but its documents or other things which are work the program are still in my system?

thanks

---

### Post by CharlesA on 2012-06-21
> **mootaph said:**
> yes, it's removed now. but its documents or other things which are work the program are still in my system?

thanks
Probably.

---

### Post by Mopar1973Man on 2012-06-21
> **mootaph said:**
> no sir, it is not in the synaptic.

Sorry about that... I know I had it in the synaptic list back when I was on 11.10 but now its gone with 12.04...

---

### Post by mootaph on 2012-06-21
> **CharlesA said:**
> Probably.

so you have any idea to how can we delete that things?

---

### Post by CharlesA on 2012-06-21
> **mootaph said:**
> so you have any idea to how can we delete that things?
Outside of using find and removing them manually, no.

---

### Post by mootaph on 2012-06-21
> **CharlesA said:**
> Outside of using find and removing them manually, no.
very hard to find :(

---

### Post by Curtis6767 on 2012-06-21
Why not go back to the site where you originally got the info on how to download and install aircrack and ask how it can be removed?

---

### Post by mootaph on 2012-06-22
> **Curtis6767 said:**
> Why not go back to the site where you originally got the info on how to download and install aircrack and ask how it can be removed?
i know that this is "ubuntu forum". problem which i have "related to ubuntu operating system and a program running on ubuntu". and people in this forum here because helping to each other about ubuntu operating system. and i want to that program (which program is for me not important) removed. i'm using ubuntu for idea "help".

---

