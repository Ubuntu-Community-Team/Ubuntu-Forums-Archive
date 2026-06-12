---
title: "HOWTO: Maya 6.5 under Hoary"
date: 2005-07-01
forum: Outdated Tutorials &amp; Tips
---

### Post by johannes on 2005-07-01
This is a tutorial to install the 3d graphics application [Alias Maya 6.5](http://www.atlantacad.com/News/Alias_Maya_6_5/Alias_Maya_6_5.html)  from the .rmp files you get on the cd if you purchase it. You should copy these to your hard drive, preferably to your home folder.

This install was made in Ubuntu Hoary 386 with the 2.6.10 kernel. It will also work in Breezy if you install the packages "xlibs" and "xlibs-data". I have no idea if it will work on other systems.

1. Maya needs the C shell program "csh" so you need to apt-get it.
```
sudo apt-get install csh
```
2. Install the program Alien to convert your maya .rmp files to .deb.
```
sudo apt-get install alien
```
3. Use "sudo alien -cv xxx.rpm": (i for install, v for verbose). Replace the x'es with the correct numbers of your packages. 
```
sudo alien -cv AWCommon-server-6.3-x.xxxx.rpm
sudo alien -cv AWCommon-6.3-x.xxxx.rpm
sudo alien -cv Maya6_5-x.x-xxx.xxxx.rpm
sudo alien -cv Maya6-5-docs_x.x-xxx_xxxx.rpm
sudo alien -cv Openmotif_2.1.xx-x_xxxx.rpm
```
4. Install them with "sudo dpkg -i"
```
sudo dpkg -i AWCommon-server-6.3-x.xxxx.deb
sudo dpkg -i AWCommon-6.3-x.xxxx.deb
sudo dpkg -i Maya6_5-x.x-xxx.xxxx.deb
sudo dpkg -i Maya6-5-docs_x.x-xxx_xxxx.deb
sudo dpkg -i Openmotif_2.1.xx-x_xxxx.deb
```
5. Create the following links:
```
sudo ln -s /usr/aw /aw
cd /usr/aw/maya6.5/lib
sudo ln -s libawcsprt.so.1 libawcsprt.so
sudo ln -s libpcwxml.so.1 libpcwxml.so

```
6. Maya wants to use the directory /usr/tmp/ for storing temporary files.
```
sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp
```
7. Run the license install script "installKey" in /usr/aw/COM/bin/ (you can do this in your window browser, in Gnome - Nautilus). Copy the contents from the licence file you got when you bought/registered the software, in my case it's "aw.dat", into the window that opens. You can also point installKey to the file.

8. Type "maya" (without "") in console to start, or use Smeg to create a shortcut in the Gnome panel. If you only get some configuration wizard window, and your console displays  an error like this:
```
you@yourhostname:/usr/aw/maya6.5/bin$ Failed to load m5opa from 
.:lib:../lib:/usr/aw/maya6.5/bin:/usr/aw/maya6.5/bin/..
/lib:/usr/aw/maya6.5/bin/lib
```Then there is probably something wrong with your licence file (aw.dat). Contact your support/reseller to get a new one.

9. As you probably will want to use the "Alt-key+mouse button" combination to pan and rotate in your viewport, open System/Preferences/Windows in the upper Gnome panel and change the Movement Key to Control or Super.

You also need to have graphics drivers (and card) with openGL support, but the drivers you get with Ubuntu will probably work. Otherwise, check the Ubuntu howtos for how to install your driver. 

Good Luck!

[[IMG]http://img359.imageshack.us/img359/4025/screenshot9gx.th.png[/IMG]](http://img359.imageshack.us/my.php?image=screenshot9gx.png)

---

### Post by kfc on 2005-07-02
Did u got the sound scrubbing supports working?
There's a sound problem in the maya that's i'm using now. The alsa driver isn't working well with the maya i have in ubuntu.

---

### Post by johannes on 2005-07-03
Actually I haven't tested that... I will check it and add it to the text if I get it to work.

---

### Post by Boggles3 on 2005-07-18
Hey i am new to linux and just switched from windows. ive got my vid drivers working 

   i am a 3d student and want to install maya 6.5.
   havent tried yet but sence im new i wanted to clerify some stuff...


              alien -iv AWCommon-server-6.3-x.xxxx.rpm
              alien -iv AWCommon-6.3-x.xxxx.rpm
              alien -iv Maya6_5-x.x-xxx.xxxx.rpm 

    where you are putting x's does that mean enter our info? like our kernel version or something or do i actually run that code exactly?? 
              
             sudo ln -s /usr/aw /aw

    what exactly does this do?? im not familiar with all commands yet

i understand the creating the directory so maya has its default place to store temps. still dont quit understand chmod.. 

           anyways please get back to me. thanx alot for the how to by the way :)

---

### Post by autocrosser on 2005-07-18
I am interested--where did you find the RPM's??--Maya's website??

Cheers!!
Dean

---

### Post by black hole sun on 2005-07-18
[QUOTE=Boggles3]Hey i am new to linux and just switched from windows. ive got my vid drivers working 

   i am a 3d student and want to install maya 6.5.
   havent tried yet but sence im new i wanted to clerify some stuff...


              alien -iv AWCommon-server-6.3-x.xxxx.rpm
              alien -iv AWCommon-6.3-x.xxxx.rpm
              alien -iv Maya6_5-x.x-xxx.xxxx.rpm[/quote]Fill the x's in with the complete filename of the maya rpm's.

> sudo ln -s /usr/aw /aw

    what exactly does this do?? im not familiar with all commands yetIt creates a link, /aw, that points to /usr/aw.

> i understand the creating the directory so maya has its default place to store temps. still dont quit understand chmod.. chmod changes a file or directory's permissions. In this case, `chmod 777` was used, which lets a non-root user (YOU) have read-write access to a directory.

---

### Post by Boggles3 on 2005-07-18
hi there... i fallowed ur instructuons and i cant find maya as in the application.., and if i type maya in console it ses unknown command??

how do i creat a shortcut of something i cant find.. do you know where it puts the file or why i cant find it ??

---

### Post by black hole sun on 2005-07-18
[QUOTE=Boggles3]hi there... i fallowed ur instructuons and i cant find maya as in the application.., and if i type maya in console it ses unknown command??

how do i creat a shortcut of something i cant find.. do you know where it puts the file or why i cant find it ??[/QUOTE]
 Well, did you download the maya rpm's? You have to do that first!! Note that Maya isn't free---you're looking at a hefty purchase.s

---

### Post by Boggles3 on 2005-07-18
lol i know it isnt free i bought it .. they have a good student discount.. $400(like i should have even spent that much lol..)

no but really i have it i bought it a while ago and was running xp. i just switch to linux cuz... well we all know why but im ganna be forced to go back if i cant get maya to run.. i cant go without.. yes i have rpm's.. they are on the install disc.. i got them and ran them.. but when i enter in console nothing happens...

if i enter the /usr/aw/maya6.5/bin and then do sudo ./maya.bin i get this error
   
         boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya.bin
         ./maya.bin: error while loading shared libraries: libMaya.so: cannot open shared                                 
         object file: No such file or directory

??????????????????????????????????????????????????????????????????????????????????????????

   im new to linux and dont want to mess up the os... but if anyone knows how to fix this and can give me a command and explain what it did so that i can still learn..
thanx

oh also another thing i noticed  if i go into bin through gui and dclick on  maya the console flashes but goes away really quike.. .. 
from what i have noticed the maya file is just a command that routs to maya.bin so im assuming it tries to run and hits the same error and quits instead of giving me the error because it is indirect..

please id love to get this running im exited to be running a full linux os that im actually puting to use

any one have any ideas...??
thanx its appriciated :)

---

### Post by black hole sun on 2005-07-18
[QUOTE=Boggles3]lol i know it isnt free i bought it .. they have a good student discount.. $400(like i should have even spent that much lol..)

no but really i have it i bought it a while ago and was running xp. i just switch to linux cuz... well we all know why but im ganna be forced to go back if i cant get maya to run.. i cant go without.. yes i have rpm's.. they are on the install disc.. i got them and ran them.. but when i enter in console nothing happens...

if i enter the /usr/aw/maya6.5/bin and then do sudo ./maya.bin i get this error
   
         boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya.bin
         ./maya.bin: error while loading shared libraries: libMaya.so: cannot open shared                                 
         object file: No such file or directory

??????????????????????????????????????????????????????????????????????????????????????????

   im new to linux and dont want to mess up the os... but if anyone knows how to fix this and can give me a command and explain what it did so that i can still learn..
thanx

oh also another thing i noticed  if i go into bin through gui and dclick on  maya the console flashes but goes away really quike.. .. 
from what i have noticed the maya file is just a command that routs to maya.bin so im assuming it tries to run and hits the same error and quits instead of giving me the error because it is indirect..

please id love to get this running im exited to be running a full linux os that im actually puting to use

any one have any ideas...??
thanx its appriciated :)[/QUOTE]
Alright, slow down :) 

Cd over to the main maya directory and type `ls`. Post the output here. I'm betting Maya has to startup with a shell script, as usually you can't directly run the main binary.

---

### Post by Boggles3 on 2005-07-18
i did that .. i created a file called MAYA on my home folder and put all the rpm's in there and then ran them with the alien

now i have all this maya crap everywhere on the system andi cant run the program

---

### Post by black hole sun on 2005-07-18
Sorry, I realized that and edited my post accordingly. See my updated post :) :

[QUOTE=black hole sun]Alright, slow down :) 

Cd over to the main maya directory and type `ls`. Post the output here. I'm betting Maya has to startup with a shell script, as usually you can't directly run the main binary.[/QUOTE]

---

### Post by Boggles3 on 2005-07-18
ok the closest i can get is /usr/aw/maya6.5/bin

then there are some extentions in there but maya is a script and then there is maya.bin
maya from what i can tell just goes to maya.bin

from this extention i can give comand to run them with ./

if i ./maya i get this...   boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya
bash: ./maya: /bin/csh: bad interpreter: No such file or directory


if i do ./maya.bin i get this ... boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya.bin
./maya.bin: error while loading shared libraries: libMaya.so: cannot open shared object f ile: No such file or director


?

---

### Post by black hole sun on 2005-07-18
[QUOTE=Boggles3]ok the closest i can get is /usr/aw/maya6.5/bin

then there are some extentions in there but maya is a script and then there is maya.bin
maya from what i can tell just goes to maya.bin

from this extention i can give comand to run them with ./

if i ./maya i get this...   boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya
bash: ./maya: /bin/csh: bad interpreter: No such file or directory


if i do ./maya.bin i get this ... boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya.bin
./maya.bin: error while loading shared libraries: libMaya.so: cannot open shared object f ile: No such file or director


?[/QUOTE]
 > ./maya i get this... boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya
bash: ./maya: /bin/csh: bad interpreter: No such file or directory

Install tcsh using Synaptic (run a search) and then run that script again.

---

### Post by Boggles3 on 2005-07-18
ok now atleast maya and maya.bin are working together cuz they have the same error but still this library thing whats with that

boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya
awpcw: error while loading shared libraries: libawcsprt.so: cannot open shared object file: No such file or directory
boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya.bin
./maya.bin: error while loading shared libraries: libMaya.so: cannot open shared object file: No such file or directory


by the way thanx alot for helping me keep it comin please  ;-)

---

### Post by Boggles3 on 2005-07-18
oh nvm lol there not the same errors.. :((

---

### Post by black hole sun on 2005-07-18
[QUOTE=Boggles3]oh nvm lol there not the same errors.. :(([/QUOTE]
 cd to  the `lib` directory in the maya directory and do the following

sudo ln -s libawcsprt.so.1 libawcsprt.so
sudo ln -s libpcwxml.so.1 libpcwxml.so 

Then run the shell script again and you should be golden :D

---

### Post by Boggles3 on 2005-07-18
wow man thanx alot  really .. im still a little stuck tho because it opened the product config wizard.. the only problem is i cant go anywhere from there.. i click on all tasks and nothing shows up but i cant click next or anything eccept for done

---

### Post by Boggles3 on 2005-07-18
i found the stuff in the com folder  and i start the awinfo in root and the terminal comes up asking me a few questions

then it creats/var/tmp/AWINFO."myusername"@"myusername"

what is this for .. i tried going back into maya but i still dont have any options

---

### Post by black hole sun on 2005-07-18
Now I'm in unfamiliar territory. You see, I dont have Maya so I dont know what this dialogue box is asking for. You're running this from a terminal, yes? Are any errors or messages written to the terminal when you click on something? 

Maybe a screenshot would help me understand, but I'm afraid you've reached the limits of my knowledge, you might ask in the maya forums or call up ther support #

---

### Post by Boggles3 on 2005-07-18
ok.  wow you must just be linux savy to get me through that and not have done it .. thanx alot for your help

usually i have to install a product licsense.. its not in console its may actually opening but it stops you so you have to enter your liscence.. i sent an email to alias so they should get back to me soon...

thanx alot man for getting me this far ..you have no idea how much i appriciat it \\:D/  :)  :) thanx again

---

### Post by black hole sun on 2005-07-18
[QUOTE=Boggles3]ok.  wow you must just be linux savy to get me through that and not have done it .. thanx alot for your help

usually i have to install a product licsense.. its not in console its may actually opening but it stops you so you have to enter your liscence.. i sent an email to alias so they should get back to me soon...

thanx alot man for getting me this far ..you have no idea how much i appriciat it \\:D/  :)  :) thanx again[/QUOTE]
 No problem. If Alias (a great TV show, BTW ;) ) doesn't help, come back here and post a screenshot of the problem and I'll see if I can make sense of why it isn't working.

---

### Post by Boggles3 on 2005-07-18
ok man i actually am getting an error i just didnt notice it earlier .. here it is...
  boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya
boggles3@boggles3:/usr/aw/maya6.5/bin$ Failed to load m5opa from .:lib:../lib:/usr/aw/maya6.5/bin:/usr/aw/maya6.5/bin/../lib:/usr/aw/maya6.5/bin/lib


think you can work your magic lol ](*,)

---

### Post by black hole sun on 2005-07-19
[QUOTE=Boggles3]ok man i actually am getting an error i just didnt notice it earlier .. here it is...
  boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya
boggles3@boggles3:/usr/aw/maya6.5/bin$ Failed to load m5opa from .:lib:../lib:/usr/aw/maya6.5/bin:/usr/aw/maya6.5/bin/../lib:/usr/aw/maya6.5/bin/lib


think you can work your magic lol ](*,)[/QUOTE]
 From what I have seen it is the license. According to one user with a similar problem, as soon as he "placed the license file" it worked. So apparently you have to put your license somewhere? Maybe the maya readme or other documentation that came with maya will have the answer. I think the config dialogue box you were referring to generates this license...

Try this;

rm -rf ~/.maya

And then start that wizard again. If the same thing happens -- try starting it with sudo as a prefix, ala

sudo ./maya

---

### Post by couje on 2005-07-19
[QUOTE=johannes]I successfully installed Maya 6.5 on Ubuntu for a friend a while ago. I made it like this:

1. Use "alien -iv xxx.rpm": (i for install, v for verbose)

alien -iv AWCommon-server-6.3-x.xxxx.rpm
alien -iv AWCommon-6.3-x.xxxx.rpm
alien -iv Maya6_5-x.x-xxx.xxxx.rpm

2. Create following link:

sudo ln -s /usr/aw /aw

3. Maya wants to use the directory /usr/tmp/ for storing temporary files.

sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp

4. That's about it.

You also need to have graphics drivers (and card) with openGL support, but the drivers you get with Ubuntu will probably work.

Just type "maya" in the console, or make a shortcut. 

Oh, and before Maya starts you of course have to point to your registration file in the window that pops up. The file is usually called "aw.dat".

Good Luck![/QUOTE]
 i tried to do as you say, but i can't get maya start. irun hoary amd64... perhaps the reason is the architecture.i really need to install maya but ican't get it works...... please help me!

---

### Post by couje on 2005-07-19
i have some question:
[list=1]
[*]where have i to put the file mentioned when a I run alien?
[*]is it possible to run it on amd64 distros of kubuntu?
[/list] 
i hope you will reply ot me thank you however byez

---

### Post by Boggles3 on 2005-07-19
Ya.. it still gives the same error

root@boggles3:/usr/aw/maya6.5/bin # Failed to load m5opa from .:lib:../lib:/usr/aw/maya6.5/bin:/usr/aw/maya6.5/bin/../lib:/usr/aw/maya6.5/bin/lib


i can see these files but i dont know for sure if they are in the right directory

is this error saying exactly where its looking for this file .. ??

---

### Post by black hole sun on 2005-07-19
[QUOTE=Boggles3]Ya.. it still gives the same error

root@boggles3:/usr/aw/maya6.5/bin # Failed to load m5opa from .:lib:../lib:/usr/aw/maya6.5/bin:/usr/aw/maya6.5/bin/../lib:/usr/aw/maya6.5/bin/lib


i can see these files but i dont know for sure if they are in the right directory

is this error saying exactly where its looking for this file .. ??[/QUOTE]
 You know what, this is a LONG SHOT, but try this. Perhaps the dynamic linker just isn't finding the files because they aren't listed in ld.so.conf.

Add the path /usr/aw/maya6.5/lib to the aforementioned file. Edit it using this command:

```
sudo gedit /etc/ld.so.conf
```
Save when you're done of course ;) Now run```
sudo ldconfig
```
That might help. If it doesn't, then I'm sorry, you'll have to see Alias for further support :(

---

### Post by Boggles3 on 2005-07-20
nope still didnt work thanx for tying man ill stop buggin ya now :)

---

### Post by cwashdee on 2005-08-09
You have to put your aw.dat (the license file) in /var/flexlm, that directory may not exist, and it has to have world write permissions (or at least root and your normal user :)

---

### Post by johannes on 2005-08-11
I installed Maya once more, and realized I forgot a couple of steps. :?  Sorry for the problems it seems to have caused... The howto is now edited. Thanks "black hole sun" for helping people and "cwashdee" for reminding me of step 7. :)

---

### Post by atomikku on 2005-08-12
well, i have quite a different problem..
i'm trying to install Maya 5.0 on my ubuntu box. all the steps are the same, and all the problems, i've encountered were the same.
I've installed the license in the proper directory and runned the license tool (the license procedure was successful) - everything worked like a charm, thanks for the lovely guide.

but when i've runned the start script i had that output:
```
placid@d-ngn:/aw/maya5.0/bin$ ./Maya5.0
/usr/aw/maya5.0/bin/maya.bin: /usr/aw/maya5.0/lib/libgcc_s.so.1: version `GCC_3.3' not found (required by /usr/lib/libstdc++.so.5)
placid@d-ngn:/aw/maya5.0/bin$
```

i thought it was a gcc version error, so i runned synaptic to install the missing C compiler. i was a little bit confused, because there are multiple versions.. i picked the the version required by Maya - "gcc-3.3". after its installation i runned again the starting script and i had the same output. even after the installation of the newer version the result was the same...

what's wrong with this libgcc_s.so.1 - gcc_3.3 thing?

---

### Post by aaron on 2005-08-12
Thank you for updating the guide! That got things working for me. Totally happy that I don't have to install windows when classes start.

One question, do you have slightly buggy rendering of the scene in Maya? When I open a dialogue window  (for example to configure animation settings) and drag it around it grays out whatever should be rendered behind it. This isn't a big deal except for when I start trying to use the graph editor to fix an animation, selecting something on the graph editor changes the scene, so the scene redraws and masks the graph editor, making it impossible to use. 

If this doesn't happen to you then I probably just broke something playing with Ubuntu to much, maybe I'll try to go back to original Ubuntu settings (like a reinstall or something).

---

### Post by atomikku on 2005-08-13
[QUOTE=atomikku]well, i have quite a different problem.. blablabla...

when i've runned the start script i had that output:
```
placid@d-ngn:/aw/maya5.0/bin$ ./Maya5.0
/usr/aw/maya5.0/bin/maya.bin: /usr/aw/maya5.0/lib/libgcc_s.so.1: version `GCC_3.3' not found (required by /usr/lib/libstdc++.so.5)
placid@d-ngn:/aw/maya5.0/bin$
```

blablanana

what's wrong with this libgcc_s.so.1 - gcc_3.3 thing?[/QUOTE]

i found myself the solution of my problem and it looks like this:
```
cd aw/maya5.0/lib/
mv libgcc_s.so.1 libgcc_s.so.1.old
ln -s /usr/lib/libgcc_s.so.1
```

---

### Post by atomikku on 2005-08-14
no rest for the wicked...
yesterday i managed to install successfully the 5.0 version of maya, everything was ok, until i rebooted the machine and tried to run maya again... 

```
placid@d-ngn:/$ /aw/maya5.0/bin/Maya5.0
/aw/maya5.0/bin/maya.bin: relocation error: /aw/maya5.0/lib/libFoundation.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
placid@d-ngn:/$
```

what exactly is GLIBC_2.0 and how can i install it. and the main question is why yesterday everything was ok, and today it's a mess..


what's going on, my linux getting crazy?  ](*,) 
please, help me with that issue..

---

### Post by atomikku on 2005-08-14
yeah, my friends, i think i did it..

after an hour of mad google enquiries i found that many people had similar problem with that glibc thing.

for maya here's the solution:
edit the starting script located in /aw/maya.../bin/MayaX.X
add the following line:
**setenv LD_ASSUME_KERNEL 2.4.1**
just before maya_exec = maya.bin

my kernel version is higher than 2.4.1 and when i tried to replace it in this line - the program didn't start...

i'm not sure what this piece of ascii means, but it makes my maya work..   :wink: 

i hope it will help you too.
good luck!

---

### Post by johannes on 2005-08-14
[QUOTE=aaron]One question, do you have slightly buggy rendering of the scene in Maya? When I open a dialogue window  (for example to configure animation settings) and drag it around it grays out whatever should be rendered behind it. This isn't a big deal except for when I start trying to use the graph editor to fix an animation, selecting something on the graph editor changes the scene, so the scene redraws and masks the graph editor, making it impossible to use. [/QUOTE]

No, I don't have this problem. I think it sounds like an issue with the graphics drivers. Have you installed the latest for your card? A reinstall might also be good.

[QUOTE=atomikku]
...
for maya here's the solution:
edit the starting script located in /aw/maya.../bin/MayaX.X
add the following line:
setenv LD_ASSUME_KERNEL 2.4.1
just before maya_exec = maya.bin
...
[/QUOTE]

A litte googeling often does the trick. Thanks for sharing if someone else has this problem.

---

### Post by szr4321 on 2005-08-23
[QUOTE=Boggles3]ok man i actually am getting an error i just didnt notice it earlier .. here it is...
  boggles3@boggles3:/usr/aw/maya6.5/bin$ ./maya
boggles3@boggles3:/usr/aw/maya6.5/bin$ Failed to load m5opa from .:lib:../lib:/usr/aw/maya6.5/bin:/usr/aw/maya6.5/bin/../lib:/usr/aw/maya6.5/bin/lib
[/QUOTE]I had exactly the same problem. For some strange reason, it helped to run "alien -c" on all of the rpms to convert them to debs and install these later on with dpkg -i. It seems that some more symlinks get installed this way (for example, I couldn't run "maya" on the shell before). The opa wizard starting up is a license issue because of a non-valid aw.dat file.
Links concerning these problems:
[http://www.highend3d.com/boards/index.php?showtopic=208134](http://www.highend3d.com/boards/index.php?showtopic=208134)
[https://knecht.homelinux.net/phpBB2/viewtopic.php?p=3037#3037](https://knecht.homelinux.net/phpBB2/viewtopic.php?p=3037#3037)

---

### Post by szr4321 on 2005-08-23
By the way, what's the preferred method of automatically starting the documentation server (/usr/aw/maya/docs/startDocServer.sh) at boot-time?

---

### Post by johannes on 2005-08-25
[QUOTE=szr4321]I had exactly the same problem. For some strange reason, it helped to run "alien -c" on all of the rpms to convert them to debs and install these later on with dpkg -i. It seems that some more symlinks get installed this way (for example, I couldn't run "maya" on the shell before). The opa wizard starting up is a license issue because of a non-valid aw.dat file.
Links concerning these problems:
[http://www.highend3d.com/boards/index.php?showtopic=208134](http://www.highend3d.com/boards/index.php?showtopic=208134)
[https://knecht.homelinux.net/phpBB2/viewtopic.php?p=3037#3037](https://knecht.homelinux.net/phpBB2/viewtopic.php?p=3037#3037)[/QUOTE]
"Alien -c" worked great. Thanks for the tip, I updated the howto.

[QUOTE=szr4321]By the way, what's the preferred method of automatically starting the documentation server (/usr/aw/maya/docs/startDocServer.sh) at boot-time?[/QUOTE]
I don't know but if someone else does, I would also like to know.

---

### Post by szr4321 on 2005-08-27
double post because of forum server problems... sorry!

---

### Post by szr4321 on 2005-08-27
double post because of forum server problems... sorry!

---

### Post by szr4321 on 2005-08-27
double post because of forum server problems... sorry!

---

### Post by szr4321 on 2005-08-27
double post because of forum server problems... sorry!

---

### Post by szr4321 on 2005-08-27
[QUOTE=szr4321]By the way, what's the preferred method of automatically starting the documentation server (/usr/aw/maya/docs/startDocServer.sh) at boot-time?[/QUOTE]The following might be worth a try:
Create the script **/etc/init.d/maya-doc-server** (as root) with the following content:
```
#! /bin/sh
#
# maya-doc-server
#
# Starts and stops the Maya Documentation Server
#

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
PATH=$PATH:/usr/aw/maya/docs
DESC="Maya Documentation Server"
NAME=maya-doc-server
SCRIPTNAME=/etc/init.d/$NAME

case "$1" in
  start)
        echo -n "Starting $DESC"
        startDocServer.sh
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC"
        shutdownDocServer.sh
        echo "."
        ;;
  restart|force-reload)
        echo -n "Restarting $DESC"
        shutdownDocServer.sh
        startDocServer.sh
        echo "."
        ;;
  *)

        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0
```Now run```
sudo chmod +x /etc/init.d/maya-doc-server
sudo update-rc.d maya-doc-server defaults
```This should basically do it. Unfortunately I'm not at home, so I can't try it right now.

Thanks a lot for this nice HowTo!
By the way, there's a small typo: It's *.rpm*, not *.rmp* ;-).

---

### Post by mattb_ on 2005-09-17
We now have a new problem...
textCurve function cannot find fonts!
Try and create a textCurves using 
create->text

Now it should tell you to check the script editor for error. Can't find anything but people with the same problem...

Thanks.

---

### Post by sparkling_twinkle on 2005-09-17
Hello there guys! i am a new user of ubuntu 5.04. previously, i am using ms office. from my secondary years up to last week to when at that time, i am working as a data encoder and layout artist. for a personal reason, our cafe have to use open office. and now, i am trying to cope with it. i mean, im learning how to use the open office. and its fun! but the problem is, sorry if i am not in the right site to ask help, i cant find the tabs which i have learned to use from ms. u know, different set ups and im currently learning about it. but cant find some applicatins.. waiting for your help. Thank's a lot..

---

### Post by szr4321 on 2005-09-18
For information on installing Maya **7.0**, have a look [here](http://ubuntuforums.org/showthread.php?p=357905).

---

### Post by mech7 on 2006-07-10
I get this error..

chris@acerChris:~$ sudo apt-get install csh
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chris@acerChris:~$

im using ubuntu 6.0.6

---

### Post by Ashur on 2006-07-20
> **mattb_ said:**
> We now have a new problem...
textCurve function cannot find fonts!
Try and create a textCurves using 
create->text

Maya looks in the following paths for postscript fonts:
[B]/usr/share/fonts/default/ghostscript
/usr/X11R6/lib/X11/fonts/Type1[/B]

Just link some fonts to any of this locations and the TextCurve tool
should work.

---

### Post by roystonvasey on 2007-04-15
> **atomikku said:**
> i found myself the solution of my problem and it looks like this:
```
cd aw/maya5.0/lib/
mv libgcc_s.so.1 libgcc_s.so.1.old
ln -s /usr/lib/libgcc_s.so.1
```

I had a similar issue and this worked for me installing on Edgey Eft. thanks!

---

### Post by roystonvasey on 2007-09-09
I've switched over to the x86_64 version of ubuntu so that I can get at a bunch of new ram I've installed. sadly, this new system is giving me grief when I try to convert my rpms to debs.

when I run this:
> sudo alien -cv AWCommon-server-6.3-1.i686.rpm


I get a bunch of OK returns and then this:
> dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
        find AWCommon-server-6.3 -type d -exec chmod 755 {} ;
find: AWCommon-server-6.3: No such file or directory
        rm -rf AWCommon-server-6.3


Initially I had also received errors about alien not being able to find a bunch of libs, but I used the firefox32 install script and that provided those missing libs. I'm thinking I need to trick alien into thinking my system is non-64 bit flavored?

maybe I need to break down and get a newer, 64bit flavor of maya?

---

### Post by jolofj on 2010-12-29
Hi!
I got a proper Maya 6.0 licence that is bound to my network cards MAC-address . I tried to install it in my Linux Ubuntu 10.4 Lucid OS. It doesn't start when I run plain maya. Instead it tell me about a seg fault.

But it starts with MEL prompt, when I write   maya -prompt  in the console.

It works fine in MEL mode. Therefore, I guess the problem hasn't anything to do with the licence.


Here is the result when I run maya -prompt  (X: some number)
"
Maya (R), Version 6.0, 2004 XXXXXX
Copyright 1997-2004 Alias Systems, a division of Silicon Graphics Limited.
All rights reserved.

Result: ./untitled
mel:
"

I followed the instruction  in this thread (
[http://ubuntuforums.org/showthread.php?t=45748](http://ubuntuforums.org/showthread.php?t=45748) )

Does it have anything to do with libs etc?

This Maya version worked fine in my Linux Fedora 3.

   // Regards J-O Janson, [URL="http://www.lightmotion.se"]www.lightmotion.se
[/URL]

---

### Post by jolofj on 2010-12-29
It certainly have something to do with connecting to X-windows and not the licence.

Because, I got Maya partially working through networked X-windows!! :KS ;)

 I wrote export DISPLAY=mylaptopsIPnr and run Linux Maya on the X-server software Xming on MS Windows XP
 
But, I guess it is some problem with glx in Xming, because it did only display the GUI correct but not the Viewport

I have working NVDIA drivers. What can be the X related problem? 

:popcorn:

// Regards J-O Janson, [www.lightmotion.se]("http://www.lightmotion.se/")

---

