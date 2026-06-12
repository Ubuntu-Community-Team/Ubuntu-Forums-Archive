---
title: "Google Earth on Ubuntu 8.04"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Mario Ráez on 2008-05-02
Hello Dear Ubunters:

I installed Ubuntu today after a decade of suffering under Windows.

Now, how do I install Google Earth on Ubuntu 8.04?
I downloaded GoogleEarthLinux.bin from the Google Earth Homepage but really don't have any idea of what to do next.
The file is on my desktop staring at me...

What do I do?

---

### Post by tjwoosta on 2008-05-02
if i were you id just get it from the repository   

go to System-Administration-synaptic package manager then search googleearth

just mark it with a check and click apply
this will do everything automatically for you

---

### Post by damis648 on 2008-05-02
try

```
cd desktop
sudo sh ./GoogleEarthLinux.bin
```
in terminal.
i doubt this would work but try it anyway

---

### Post by iSplicer on 2008-05-02
just type this into a terminal (applications - accessories - terminal):


> cd Desktop

and then
> 
sh GoogleEarthLinux.bin

---

### Post by NightwishFan on 2008-05-02
This way will work with only a few commands. ;]
You need the medibuntu repo. I will supply howto in one min bear with me ;]

step one: copy paste this command
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
step two: copy paste this command
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
step three: copy paste this command
```
sudo apt-get install googleearth-4.3
```
when installed just press alt+f2 and type googleearth or find it under internet in the menu

enjoy!

---

### Post by damis648 on 2008-05-02
o yes i forgot googleeath is in the repos... use that

---

### Post by iSplicer on 2008-05-02
Edit: here is a rally good guide:

[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)

---

### Post by iSplicer on 2008-05-02
Forget everything. Just type this into the terminal:

sudo apt-get install googleearth

Thats it!

---

### Post by iSplicer on 2008-05-02
Whoops. My bad, its actually this:
```

sudo apt-get install googleearth-package
```

Thats it!
__________

---

### Post by tjwoosta on 2008-05-02
well if you want the newest version of google earth you would need the medibuntu repository but if you dont care as long as it works you dont need medibuntu

here is a guide to adding medibuntu

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by iSplicer on 2008-05-02
OH yeah, thats right, I forgot to mention you need the medibuntu repos before you can install.


This is what you need to do, step by step.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

```
sudo apt-get install googleearth-4.3
```

Ignore my previous posts.

---

### Post by NightwishFan on 2008-05-02
Sorry I had to edit my how to so much its final now that method will work. I just tested on Kubuntu. (remember to accept the license) also when you get a y/n question answer y.

---

### Post by iSplicer on 2008-05-02
> **iSplicer said:**
> OH yeah, thats right, I forgot to mention you need the medibuntu repos before you can install.


This is what you need to do, step by step.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

```
sudo apt-get install googleearth
```

Ignore my previous posts.


Yepp. Thats the final method, dont do anything else.

---

### Post by Mario Ráez on 2008-05-02
> **Mario Ráez said:**
> Hello Dear Ubunters:

I installed Ubuntu today after a decade of suffering under Windows.

Now, how do I install Google Earth on Ubuntu 8.04?
I downloaded GoogleEarthLinux.bin from the Google Earth Homepage but really don't have any idea of what to do next.
The file is on my desktop staring at me...

What do I do?

Ok, I did it (Forgot to mention that I use the desktop in Spanish where Aplications is Aplicaciones, Accesories is Accesorios, Terminal is Terminal but ¡Desktop is Escritorio.

It did all the rest by itself but now it seems like does not recognize my graphic card. I will post details when I have them.

Thanks a lot.

---

### Post by NightwishFan on 2008-05-02
Follow mine or splicers howtos (they are exactly alike except use googleearth-4.3)
final command is: sudo apt-get install googleearth-4.3

It should work right then hopefully. When I use the sh ./googleearth.bin method it fails to log into the server.

---

### Post by iSplicer on 2008-05-02
> **NightwishFan said:**
> No the command is: sudo apt-get install googleearth-4.3
Damn, hes right. The googleearth by itself only installs 4.2, you should run googleearth-4.3

I have updated my instruction post.

Thanks nightwish for that

---

### Post by NightwishFan on 2008-05-02
np
Google earth 4.3 is a world away from the previous version trust me. It even has weather and such now. Googleearth 5 will like be a 3d existence at this rate :D :popcorn:

---

### Post by iSplicer on 2008-05-02
> **NightwishFan said:**
> np
Google earth 4.3 is a world away from the previous version trust me. :popcorn:

What is the difference?

---

### Post by NightwishFan on 2008-05-02
I edited, also there is street views which are like panoramas, they have them all over my area. (well all of that might have been in 4.2 actually) lol

Last one I used before 4.3 was way less full featured.

---

### Post by Mario Ráez on 2008-05-02
> **Mario Ráez said:**
> Ok, I did it (Forgot to mention that I use the desktop in Spanish where Aplications is Aplicaciones, Accesories is Accesorios, Terminal is Terminal but ¡Desktop is Escritorio.

It did all the rest by itself but now it seems like does not recognize my graphic card. I will post details when I have them.

Thanks a lot.

OK, I did it and now I am waiting...A screen showing a Terms Acceptance Page appeared and there was no way to accept it.

---

### Post by NightwishFan on 2008-05-02
Press tab to change to different options and enter to select.

---

### Post by Mario Ráez on 2008-05-02
> **Mario Ráez said:**
> OK, I did it and now I am waiting...A screen showing a Terms Acceptance Page appeared and there was no way to accept it.

I must have spoiled something while installing, now the prompt shows this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

How do I dpkg --configure -a? It requests for superuser privileges.

---

### Post by NightwishFan on 2008-05-02
```
sudo dpkg --configure -a
```

Then try the install again if googleearth is not installed.

(perhaps use synaptic for graphical method of install, rememeber to check 'googleearth-4.3' and not 'googleearth')

---

### Post by stinger30au on 2008-05-03
> **iSplicer said:**
> OH yeah, thats right, I forgot to mention you need the medibuntu repos before you can install.


This is what you need to do, step by step.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

``````
sudo apt-get install googleearth-4.3
```Ignore my previous posts.


awesome , thanks
worked for me!

---

### Post by iSplicer on 2008-05-03
> **stinger30au said:**
> awesome , thanks
worked for me!

Happy to help a fellow Aussie out =)

---

### Post by captkit on 2008-05-03
Fellow Google Earth fans:

I followed this technique up hill and down dale--finally got it installed, went to the apps menu, clicked on GE--nothing--just nothing. It was my 8th or 9th try in 3 versions of ubu. 
For those of you who have lost hope as I have, I offer a workaround. Enter "houses for sale" in Google > open Google's search > click on satellite on the map > zoom out. You won't get the north pole, but most of the world is there.

---

### Post by arpakette on 2008-05-04
I successfully installed 4.3 on Hardy following the most uptodate isplicer/nightwish instructions - thank you very much guys, great howto - with no trouble.  GE suggested I update my video driver for faster response, so I Used System|Administration|Hardware Drivers and installed the ATI accelerated graphics card.  That was a wonderful upgrade for everything else.  My 24" Samsung finally displayed realistically, but GE went nuts.  What I could see was great, but the screen blinked wildly and I couldn't control anything.  Does anyone know what happened?  Is there a resolution to my resolution?  TIA

---

### Post by the8thstar on 2008-05-04
> **arpakette said:**
> I successfully installed 4.3 on Hardy following the most uptodate isplicer/nightwish instructions - thank you very much guys, great howto - with no trouble.  GE suggested I update my video driver for faster response, so I Used System|Administration|Hardware Drivers and installed the ATI accelerated graphics card.  That was a wonderful upgrade for everything else.  My 24" Samsung finally displayed realistically, but GE went nuts.  What I could see was great, but the screen blinked wildly and I couldn't control anything.  Does anyone know what happened?  Is there a resolution to my resolution?  TIA


Try to turn off the Desktop effects. Right click on the desktop to access the menu.

---

### Post by webcoded612 on 2008-05-04
> **the8thstar said:**
> Try to turn off the Desktop effects. Right click on the desktop to access the menu.

Worked like a charm for me.  GE bugged like crazy on me, too...blinking and flickering.  Turned off desktop effects (which kind of sucks that I have to have a boring desktop to use GE, but oh well) and all is well.

TY!  :)

---

### Post by the8thstar on 2008-05-04
Don't forget to click on the little medal next to the "quote" button then ;)

---

### Post by arpakette on 2008-05-04
Thankyou 8thstar, works fine now.  How do you know that stuff?

---

### Post by the8thstar on 2008-05-04
I'm just a normal human being, like you :) I learnt what I know with the help of the good people on these forums. I'm more advanced than you, but you'll get there in no time!

---

### Post by mitchauer on 2008-05-04
> **iSplicer said:**
> just type this into a terminal (applications - accessories - terminal):




and then
Thank you for the Google Earth install info

---

### Post by ubername on 2008-05-06
Odd problem here:

I have installed GE from both the repositories and from the .bin file. 

When I first run it from the .bin file, all is OK. However when I close it and restart it I get the application window showing with a load of stars (I suppose) but no globe

With the repository version it doesn't even work first time. (i.e. I get the app window but no globe)

It's like it's not connecting to a server with the google earth data on it (at least that is my current analysis)

Can anyone help?

TIA

---

### Post by Twizzle on 2008-05-06
I got exactly the same - no earth. I removed it and re installed and now I get a white box when I run Google Earth! Nothing at all :confused:

---

### Post by NightwishFan on 2008-05-06
That happens to me when I install with the bin, it will not log in. When I install from repos it works perfectly.

---

### Post by BGThree on 2008-05-07
I originally installed 4.3 but it flickered like crazy and basically wouldn't work, even with desktop effects turned off.  I installed 4.2 and it works like a charm.

Is my computer too old/slow to run 4.3 or is there another problem?

Intel Centrino Duo, 2 gigs RAM, 945GM/GMS 943/940GML integrated graphics controller

Do you guys need more info from me (please tell me what), or should I be able/not be able to run Google Earth 4.3?

---

### Post by TunaCanTommy on 2008-05-07
I too am playing around with getting GE 4.3 installed.  I'm running Hardy on a desktop with a NVIDIA 6200 graphics card. I started by downloading the new version of of Google Earth (v4.3) and installed it using the .bin file.  But it's not working right . . all I get is a 'star-field'. I can rotate the star-field but the Earth View won't load.  I think the problem is I'm not linking to the GE server.
After reading all the helpful advice in this thread what I'd like to do is uninstall the .bin version and install via the repositories.
Long post for maybe a simple answer . . . How do I uninstall the .bin version ? ? :confused:
I'd like to clean it all out and reinstall according to the posts in this thread.
Thanks !!

---

### Post by stchman on 2008-05-07
> **Mario Ráez said:**
> Hello Dear Ubunters:

I installed Ubuntu today after a decade of suffering under Windows.

Now, how do I install Google Earth on Ubuntu 8.04?
I downloaded GoogleEarthLinux.bin from the Google Earth Homepage but really don't have any idea of what to do next.
The file is on my desktop staring at me...

What do I do?

Googleearth is in the Medibuntu repos.

[http://www.medibuntu.org](http://www.medibuntu.org)

---

### Post by krcabrer on 2008-05-08
Hello:

I try with mithubuntu repos.
But it works only the 4.2 version.
I got AMD64 Ubuntu 8.04 for AMD64.

When I install from the bin... it works only the first time.

Should I use sudo to execute GE? always?

Thank you for your help.

Kenneth

---

### Post by Solrac924 on 2008-05-08
i can't get it going. i've been trying for 2 days now. 
i've tried installing it by entering those 3 lines in the terminal (on page#3 of this thread). i've also tried using the synaptic package manager. everytime i click on the Google Earth icon, it results in the monitor blacking out, & then the system rebooting. :confused:

i've downloaded .bin file from Google. i'm gonna trying installing it using the instructions given here.

---

### Post by BGThree on 2008-05-09
> **BGThree said:**
> I originally installed 4.3 but it flickered like crazy and basically wouldn't work, even with desktop effects turned off.  I installed 4.2 and it works like a charm.

Is my computer too old/slow to run 4.3 or is there another problem?

Intel Centrino Duo, 2 gigs RAM, 945GM/GMS 943/940GML integrated graphics controller

Do you guys need more info from me (please tell me what), or should I be able/not be able to run Google Earth 4.3?

I've figured out my problem, sort of -

All I did was disable "atmosphere" in the view menu of GE.  It went from PAINFULLY slow to as fast as any other GE version I've ever used on Windows (new Ubuntu user).

I installed 4.3 in my XP partition and it worked there, but now I realize that atmosphere was defaulted OFF in XP and defaulted ON in Linux.  I'll be curious to see if GE4.3 runs smooth in XP with atmosphere on, if I ever boot into Windows again!:)

---

### Post by TunaCanTommy on 2008-05-09
Some info from a Google Earth discussion forum:


"Google Earth 4.3 only works in Linux on machines with processors
that support SSE2. This means a P4, A64, or greater is now required."

[http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5#](http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5#)

So, if your system/CPU can't support 4.3 you need to stay with 4.2.

To find out if you system/CPU will support GE 4.3 type cat /proc/cpuinfo at the command line in terminal.  In the "flags" section you'll see things like "fpu mmx".  Look for an "sse2" - if your processor has it, it'll be in that list.

---

### Post by wombil on 2008-05-09
hey guys, 
I am trying to install google earth to heron 8.04 via NightwishFan's instructions  and stalled at the last stage.[I think]
Trying to do this stage again I get this message,

oigle@oigle-desktop:~$ sudo apt-get install googleearth-4.3
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
oigle@oigle-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
oigle@oigle-desktop:~$ 

Where do I go from here? I tried entering my password at the end and got the same message that I have to be superuser.How do I do that?
Thankyou.

---

### Post by TunaCanTommy on 2008-05-09
Just put sudo in front of "dpkg --configure -a"

sudo dpkg --configure -a

The "sudo" give you "superuser-privilege" . . .

---

### Post by wombil on 2008-05-10
Thanks tommy,
After I type in"sudo dpkg --configure -a " the terminal asks for my password but will not accept any text.I think it's getting close but just will not accept anything after password

---

### Post by tjwoosta on 2008-05-10
when typing your password in the terminal it will never show what you are typing, it **wont** even show theese things *** (you just have to type it anyway and hope its right then hit enter)

---

### Post by Cpuboye11 on 2008-05-10
never mind!

---

### Post by kystorms on 2008-05-11
> **TunaCanTommy said:**
> Some info from a Google Earth discussion forum:


"Google Earth 4.3 only works in Linux on machines with processors
that support SSE2. This means a P4, A64, or greater is now required."

[http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5#](http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5#)

So, if your system/CPU can't support 4.3 you need to stay with 4.2.

To find out if you system/CPU will support GE 4.3 type cat /proc/cpuinfo at the command line in terminal.  In the "flags" section you'll see things like "fpu mmx".  Look for an "sse2" - if your processor has it, it'll be in that list.


okay, see on the google help forum for google earth that there is a new download??? that is workable for those of us who do not have sse2, but how do we uninstall the version we got from the mediubuntu repos?

thanks for any help

---

### Post by TunaCanTommy on 2008-05-11
> **kystorms said:**
> okay, see on the google help forum for google earth that there is a new download??? that is workable for those of us who do not have sse2, but how do we uninstall the version we got from the mediubuntu repos?

thanks for any help

@kystorms . . 
If you installed it using synaptic, you remove it using synaptic.

I you used "sudo apt-get install googleearth-4.3" to install it, to uninstall it you type "sudo apt-get autoremove googleearth-4.3".

The "new" version of Google Earth mentioned in the forum is Version 4.2. It's a perfectly good version of Google Earth and runs fine on my machine running Ubuntu Hardy and NOT SSE2. If you need help getting it installed look at some previous posts in this thread.

---

### Post by Slackpacker on 2008-05-11
I've tried installing from both the Google binary and medibuntu, with the same result: running "googleearth" on the command line produces a segmentation fault error. Trying to start from the launcher icon does nothing, as others have noted. I've got 64-bit Hardy, cpu is an Athlon 64X dual-core 4400. I've also got an nvidia 9600GT which is running a beta driver which might produce graphical errors/crashes, but I don't think that explains this problem.
Any insight? Hoping this is just a bug with newer hardware that Google will get around to fixing...

---

### Post by a.v.l on 2008-05-14
I've downloaded the 4.3 bin file from Google Earth and installed it but when going to Application> Internet > Google Earth nothing opens up. 

Typing google earth in the terminal gives me the bug report below. How do I now remove the 4.3 downloaded instalation of Google Earth from my system please?


We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/myname/.googleearth/crashlogs/crashlog-F9C926C5.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

---

### Post by TunaCanTommy on 2008-05-14
@a.v.l
Search the "General Help" forum for 'Uninstall Google Earth' - lot's of excellent help there.  Or search for a poster called 'fakie-flip', he provided a useful tip.

---

### Post by mdalacu on 2008-05-22
I have just found a solution for the NO GLOBE problem.
Note that i have installed Google Earth from the .bin file.
Here you go : [COLOR="DarkRed"]sudo googleearth[/COLOR]    :)
That simple!

---

### Post by NightwishFan on 2008-05-22
I don't think I would want to run Google Earth as root.

---

### Post by dppowell on 2008-05-29
> **mdalacu said:**
> I have just found a solution for the NO GLOBE problem.
Note that i have installed Google Earth from the .bin file.
Here you go : [COLOR="DarkRed"]sudo googleearth[/COLOR]    :)
That simple!

This is my experience, too.  Google Earth, installed from either the Google .bin or the medibuntu package, only displays a starfield unless it's run as root.  This is doubly baffling to me, because on my previous machine (running Dapper), I installed it from the .bin and used it as a normal user for quite some time.

What could have changed?  I'm not comfortable running GE as root every time I want to use it.

---

### Post by dppowell on 2008-06-04
/bump

---

### Post by manimal on 2008-06-09
In your HOME directory, there is a ".googleearth" directory (the "." makes it hidden, but it should be there).  Try deleting this directory (it contains all your Google Earth preferences, so be careful - maybe make a backup).  In a terminal, you would type:
> 
sudo rm -rf ~/.googleearth

I think the when you run the ".bin" installer, there is a checkbox at the very end of the install process that says something like "Start Google Earth."  If this is checked, it starts the application as the "root" user (since you have to use "sudo" to install the app) and creates the ".googleearth" directory with root privileges.  When you run the app. without these privileges, all sorts of problems seem to occur.  They should probably make the checkbox default to unchecked.

---

### Post by dppowell on 2008-06-11
Thanks, Manimal--I returned to this thread to post that I found a solution elsewhere on the forums.  It differs somewhat from yours but the concept is the same:

[http://ubuntuforums.org/showthread.php?t=757521&page=3](http://ubuntuforums.org/showthread.php?t=757521&page=3)

---

### Post by asif_1088119 on 2009-10-06
i hav ubuntu 8.04 & installed google earth 5 & having this displayed whenever i try 2 run it.... p, li { white-space: pre-wrap; }   

"Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
 My Places Path: "/home/asif/.googleearth"
Cache Path: "/home/asif/.googleearth/Cache"
please som1 giv an answer

---

### Post by NightwishFan on 2009-10-08
You need to have read/write access to those directories. I would create them if they do not exist, and make sure you have the permissions. Did you install Google Earth correctly?

I believe you can install google earth using medibuntu. If you wish to do this, just uninstall the google earth you have, and follow the directions at the medibuntu site.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

