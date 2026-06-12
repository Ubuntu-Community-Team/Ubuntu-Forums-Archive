---
title: "The same... HOW TO INSTALL &quot;*.tar.gz&quot;"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Kharlo on 2012-09-09
i have about two hours reading on internet how to install that packaged and i cant get it....


i am not going to argue about how difficult some things that shouldnt be in ubuntu ARE....  because the plain solution would be to choose to another OS....

but still make me a little bt mad....  


i am trying to install opera (opera-9.64.gcc295-static-qt3.i386.tar.gz)
and i cant get it!!!!!!

is there any way i could just select and click install, why i should the learning process to use the tool be more complicated than the use i am going to give to the tool.

---

### Post by eddietours on 2012-09-09
I think you can use a deb file [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by oldos2er on 2012-09-09
Not sure why you downloaded that particular file; however, see [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by shadedpixel on 2012-09-09
> **Kharlo said:**
> i have about two hours reading on internet how to install that packaged and i cant get it....


i am not going to argue about how difficult some things that shouldnt be in ubuntu ARE....  because the plain solution would be to choose to another OS....

but still make me a little bt mad....  


i am trying to install opera (opera-9.64.gcc295-static-qt3.i386.tar.gz)
and i cant get it!!!!!!

is there any way i could just select and click install, why i should the learning process to use the tool be more complicated than the use i am going to give to the tool.

Try following the instructions on this page

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

However, installing from the .deb would be much easier.

---

### Post by mcduck on 2012-09-09
> **Kharlo said:**
> 
is there any way i could just select and click install, why i should the learning process to use the tool be more complicated than the use i am going to give to the tool.

Yes, there is. Download the .deb package, not the .tar.gz. ;)

---

### Post by Hekabe on 2012-09-09
This may not be the correct version, but there is a .deb for Opera (essentially like a .msi for Windows) available at this link. [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/) In other words, you should just be able to open and install using ubuntu-software-center. Like you wanted.

---

### Post by mips on 2012-09-09
If you want to install the latest version of Opera just do this in a terminal:

```
sudo add-apt-repository 'deb http://deb.opera.com/opera/ stable non-free'
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install opera
```

If you really need such an old version (opera-9.64.gcc295-static-qt3.i386) of opera you can download the .deb file here [http://arc.opera.com/pub/opera/linux/964/final/en/i386/static/](http://arc.opera.com/pub/opera/linux/964/final/en/i386/static/) simply double clicking on it should install it.


.

---

### Post by Lars Noodén on 2012-09-09
@mips, there is a transposition in the first line, it should read 'apt-add-repository'  But yes, that's the easy (right) way to install Opera.

---

### Post by newb85 on 2012-09-09
A .tar.gz file is a compressed archive file (analogous to a .zip file in Windows, though .zip files can be used in Ubuntu, as well).  One would have to extract the contents of the archive first, and then the specific installation method would depend on the extracted file type.

Right-clicking the .tar.gz file and selecting "Extract Here" would take care of the first step.  The extracted file would probably open with the Software Center, where you could simply click "Install".  Not sure what's so difficult about that--or why it would seem more difficult than installing from a .zip-ped .exe in Windows.

That said, installing from an archive (as mips directed) is definitely a better approach, as the program will be automatically updated by the package manager.

---

### Post by critin on 2012-09-09
> **Kharlo said:**
> i

i am trying to install opera (opera-9.64.gcc295-static-qt3.i386.tar.gz)
and i cant get it!!!!!!

is there any way i could just select and click install, why i should the learning process to use the tool be more complicated than the use i am going to give to the tool.

Whenever you want a file that is both linux/ubuntu and windows compatible,  always look for the linux version--- .deb version.  It will be where you choose your download.  

Every time I visit the Opera site, it automatically goes to the linux download.  It reads my version without me choosing.    It offered me 12.02, did you want to get 9.64 for some reason?

When the package is in your download page, click or right click and choose 'let software center install.
You can also just click on the Download list immediately and click open file.  Easy...

It works exactly like choosing a windows version and clicking, and then choosing Install.

I've even installed tars by right clicking and letting the default choose what to do.
Explore...

---

### Post by Kharlo on 2012-09-09
> **oldos2er said:**
> Not sure why you downloaded that particular file; however, see [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)


that particular file? what you mean?

i just went to Opera and hitted the download for UBUNTU and thats it?

you are talking about the debian vs the tar.gz? or the version?


if is the version, the problem is that i downloaded it months ago and i forget to check for a new version, but that doesnt matter because if i would have gone to the Opera site today i would have done the same
i would have selected, opera, and ubuntu version...

i didnt know i should use debian.

so is that the solution? can i then download the debian version?

another thing...  is there a way to disable the annoying 12.4 sidebar?
since the scroll in that side bar is not speed sensitive with the mouse cursor, i use to work with several windows and sometimes it takes lot of seconds to reach the window i am working with...

And another thing....
i am couple of minutes to decide to switch back to 10.04lts
the installation problems (but i could handle it), the sidebar stupidity and...
how do i see the softwares i have installed? i mean sometimes i dont remember the name of the software i need.. but with such an interface were i have to write down the application.... come on... that's a backward, anyway to remove that sidebar and get back to the menu 

and i found this 12.04 more restrictive, i have less options to manipulate my hardware  this is still the date (i have 4 months with the 12.04) i havent been able to listen to my laptops microphone with this ubuntu...

---

### Post by Lars Noodén on 2012-09-09
@Kharlo, follow the instructions that mips wrote in [post #7](http://ubuntuforums.org/showpost.php?p=12228288&postcount=7) above.  There is just one correction.  The first line should have "apt-add-repository" instead of "add-apt-repository"

Using the package manager and repositories is by far the easiest and safest way of dealing with installing programs.

---

### Post by newb85 on 2012-09-09
> **Lars Noodén said:**
> @Kharlo, follow the instructions that mips wrote in [post #7](http://ubuntuforums.org/showpost.php?p=12228288&postcount=7) above.  There is just one correction.  The first line should have "apt-add-repository" instead of "add-apt-repository"

Using the package manager and repositories is by far the easiest and safest way of dealing with installing programs.

Incorrect.  The command is definitely "add-apt-repository".

---

### Post by critin on 2012-09-09
> **Kharlo said:**
> that particular file? what you mean?

i just went to Opera and hitted the download for UBUNTU and thats it?

you are talking about the debian vs the tar.gz? or the version?


if is the version, the problem is that i downloaded it months ago and i forget to check for a new version, but that doesnt matter because if i would have gone to the Opera site today i would have done the same
i would have selected, opera, and ubuntu version...

i didnt know i should use debian.

so is that the solution? can i then download the debian version?

.

No, not debian--.deb.  It's like .exe in windows.  
You won't get ver.9 today.  I downloaded opera a half hour ago and it gave me 12.02.  The 9 is way out of date.

.deb is given automatically if you are on the linux page.

---

### Post by Lars Noodén on 2012-09-09
> **newb85 said:**
> Incorrect.  The command is definitely "add-apt-repository".

Ah. That's what I get for using Quantal beta.  Looking closer at it, up to Precise it is [add-apt-repository](http://manpages.ubuntu.com/manpages/precise/en/man1/add-apt-repository.1.html).  In Quantal, it becomes apt-add-repository.

---

### Post by newb85 on 2012-09-09
> **Lars Noodén said:**
> Ah. That's what I get for using Quantal beta.  Looking closer at it, up to Precise it is [add-apt-repository](http://manpages.ubuntu.com/manpages/precise/en/man1/add-apt-repository.1.html).  In Quantal, it becomes apt-add-repository.

Good to know.  Actually, the first time I tried to use the command, I entered it as apt-add-repository, because in my mind, that was the logical way for it to be arranged.  :)

---

### Post by d3v1150m471c on 2012-09-09
```

tar xvf file.tar
cd file
cat README || cat INSTALL || ls -A

```

---

### Post by Kharlo on 2012-09-09
> **critin said:**
> No, not debian--.deb.  It's like .exe in windows.  
You won't get ver.9 today.  I downloaded opera a half hour ago and it gave me 12.02.  The 9 is way out of date.

.deb is given automatically if you are on the linux page.


Then.. which should i download?  Ubuntu or Debian version?

(i was not able to stand the 12.04, that OS was focused in everything, but not productivity and agility, i have installed back the ubuntu 10.04lts and all its updates)

i solved some things.. but i am stuck again in installations since 3 hours ago between Opera, Wine 1.4 and Libre office..

honestly.. for me this is one of the very main reason why linux is far away from the other two OS.. that MUST be solved, neither the compatibility nor if is easy to use or not... but the ability to EASILY install soft and apps.... the current way... is not for humans...


but lets try to go by parts....

can someone tell me which opera version should a download to install in this ubuntu 10.04LTS?

---

### Post by Kharlo on 2012-09-09
ok i was able to install Opera (debian version, not ubuntu)

Can someone tell me how to install Wine 1.4?

it givies me two options; debian and ubuntu, but the ubuntu version is for 11.04 and beyond...

ad knowing that debian packages are easier to install i chose debian...
 but again; the linux stufff..   i dont understand the page..
[http://www.winehq.org/download/debian](http://www.winehq.org/download/debian)
then
[http://dev.carbon-project.org/debian/wine-unstable/](http://dev.carbon-project.org/debian/wine-unstable/)

if that lat one is the download page...  why not just a single big button that says : "download" and thats it?

which one of those packages do i have to download?


i tried the other winde for ubuntu... and God.. the same again... WHICH ONE?
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

WHY not just a simple download -> OS version and thats it?

i tried all those steps and nothing.. i tried the repository stuff.. the installable link stuff and the alternative command. stufff.... and nothing...

i really admire you guys... 
how much mental power are used to do stuff that should and COULD be simplier...  and  have the patience to keep it that way....
i really admire you...

this is more difficult than recovering an airplane from a spin.. the main difference is that, in the spin, there is no other way that the known one and IT must be learned THAT way because it SAVES LIVES.

---

### Post by critin on 2012-09-10
Some of the links you posted are for patches, betas, etc.  They are for someone who is experienced with linux and is able to test for them.  They aren't ready to be released yet.

Wine is not an easy program to set up and use.  You can try, but it's going to be difficult.   I suppose you have some windows apps that you just have to run.

> [I][COLOR=Red]WARNING: BETA PACKAGES![/COLOR]
[/I]
*The 1.5 packages here are beta packages.  This means they will  periodically suffer from  [regressions]("http://wiki.winehq.org/Regression"), and as a result a**n  update may break functionality in Wine.** If the stable 1.4 Wine version works  for you, then you may not want to use these beta packages.*

[http://dev.carbon-project.org/debian/wine**[COLOR=Red]-unstable/[/COLOR]**]("http://dev.carbon-project.org/debian/wine-unstable/")
[COLOR=Red]unstable [/COLOR]means it isn't reliable yet--they're still working on it.

[COLOR=Red]Beta [/COLOR]means it isn't ready, it's still being tested and worked on.


Wine is available in the Software Center, why not install from there and save yourself some stress?  

A good rule of thumb is to install the version that matches the OS in your system.  ubuntu--use ubuntu version.  Debian--use debian version, and so on.  The Software Center will have the correct, stable version for your OS.

---

### Post by critin on 2012-09-10
> but the ability to EASILY install soft and apps...

The Software Center.

---

### Post by Kharlo on 2012-09-10
> **critin said:**
> Some of the links you posted are for patches, betas, etc.  They are for someone who is experienced with linux and is able to test for them.  They aren't ready to be released yet.

Wine is not an easy program to set up and use.  You can try, but it's going to be difficult.   I suppose you have some windows apps that you just have to run.

[COLOR=Red]unstable [/COLOR]means it isn't reliable yet--they're still working on it.

[COLOR=Red]Beta [/COLOR]means it isn't ready, it's still being tested and worked on.


Wine is available in the Software Center, why not install from there and save yourself some stress?  

A good rule of thumb is to install the version that matches the OS in your system.  ubuntu--use ubuntu version.  Debian--use debian version, and so on.  The Software Center will have the correct, stable version for your OS.

Thank you for answering!

i know about the software center... and about the beta and unstable stuff.. (thanks for the advice)
i just wanted the lates version, i read in wine page that the1.4 was already available for my linux version but their instructions doesnt works clearly...

if theres no much difference between 1.2 (the one form software center) and 1.4 then i'll install it...

i just have been able to install LibreOffice...
God.. why!...

a friend was trying to help me...
and told me to run the installation from terminal.. i barely know what the terminal is (despite i didnt knw where to write those codes)....
i got instruction to rick click aand hit install.. come on WHERE? this 10.04 doesnt have that option.. then they clarify me that i have to install the nautilus (why you didnt told me that before if most 10.04 dot have it?)

then i installed it.. but still no "open in terminal" WHY you didnt tell me tht i had to enable it then after install [why is not enabled by itself after installed?]  and after that i had to make some config_data... stuff..

all this after trying to introduce the repository to software center {dont ask me how..}. and modifying software stuff...  
why most linux user i have been assisted by explain in the same way..? 

i mean me as windows user. i know when somebody has experience or not if i notice it have not experience i explain in a simpler step by step way to avoid losing time explaining and correcting twice...
  i dont knwo and i apologize but i dont know... its the same behavior in almost all linux user...

( and i am not saying this because the guys who assited me in this post, you have been very kind and i thank you for that!... but 80% of other users and linux procedures explications [from softwares, form OS, from packages] explains in the same way...)

---

### Post by Paqman on 2012-09-10
> **Kharlo said:**
> that particular file? what you mean?

i just went to Opera and hitted the download for UBUNTU and thats it?


I just went to opera.com to check and the version it offered me was a proper .deb for Ubuntu. Where have you downloaded this from? If it's from anywhere except opera.com or a trusted repo I wouldn't use it.

---

### Post by Paqman on 2012-09-10
> **Kharlo said:**
> 
a friend was trying to help me...
and told me to run the installation from terminal.. 

Sounds like your friend doesn't really know their stuff. There are much easier ways than using the terminal. Sometimes you'll get folks on Linux who will give terminal instructions to newbies for stuff that doesn't need to be done in the terminal. Probably best to politely thank/ignore them and find someone who can give you better instructions. There's no need to be falling back on the terminal for something as simple as installing software.

---

### Post by Vaphell on 2012-09-10
terminal: ctrl+alt+t, or win key/ubuntu icon, 'terminal' in search box

forget how things are done in windows, think app store and android whatever-it's-called. We don't scour the internet for random crap to install here.

considering you are new you should always try this path:
official repos ---> 3rd party repos -> .deb files ----------> (tar.gz, source code, compilation)

if you go back to post #7 while having the terminal window opened, highlight the commands and middleclick paste them in terminal (or use ctrl+c, ctrl+shift+v) one by one.
it will add official opera repo and you won't have to do anything around opera ever.


Most often you will get instructions in text form for terminal, because it's faster and more foolproof than going with page long description of click here, then click there.

---

### Post by mastablasta on 2012-09-10
as mentioned in post #7 you can open software center and then add repository there, you then add the key to repository (this is ment to protect you form getting any malware) and then you update the software list and Opera will apear in software center, where you can choose it to install it. once installed all or any updates to the software will be done automaticly via software package manager/updater. post #7 did all this in a few short command lines you can copy and paste to terminal. but all this can be doen via GUI.
 
Check the Ubuntu manual link in my signature to learn a bit more about ways to install things.
 
additionally i saw you mentioned that you dont' like the look of Ubuntu 12.04 and you have for that reaosn went to 10.04. but did you knwo oyu can easilly install and select different looks such as Gnome fallback (same look as the one in 10.04), Mate (for and continuing development of old look), Cinamonn (traditional desktop look). aside form these gnome desktops you can also use a completely different desktop environment form Gnome (for example the one found in Kubuntu, Xubuntu, Lubuntu, ...) there are also plenty widnows managers (Icewm, jwm, openbox...). each of these can be customized a lot and themes are offered on internet. for example it's quite easy to make Xubuntu look like old Ubuntu (involves right clicking on stuff and selecting propperties and then changing them to match the old look). so with so much choice i see really no good reason to change to 10.04 just because of the look. 10.04 is supported unitl april 2013, while 12.04 will be supported until April 2017

---

### Post by mastablasta on 2012-09-10
> **Vaphell said:**
> Most often you will get instructions in text form for terminal, because it's faster and more foolproof than going with page long description of click here, then click there.
 
not only that, but each user has different software package manager. some use synaptic, some software center, Kubuntu i use has Muon. 
[http://almostconnecticut.net/linuxismylife/wp-content/uploads/2011/11/kubuntu-muon.png](http://almostconnecticut.net/linuxismylife/wp-content/uploads/2011/11/kubuntu-muon.png) 
 
  
So things are in different place. But same commands will work in all of them and also most Ubutnu based distributions (such as for example Linux Mint, Bodhi linux etc.)

---

### Post by Kharlo on 2012-09-10
> **Paqman said:**
> I just went to opera.com to check and the version it offered me was a proper .deb for Ubuntu. Where have you downloaded this from? If it's from anywhere except opera.com or a trusted repo I wouldn't use it.

i got the debian version from opera page.. i have ubuntu.. but the one that worked was the debian...

> **Paqman said:**
> Sounds like your friend doesn't really know their  stuff. There are much easier ways than using the terminal. Sometimes  you'll get folks on Linux who will give terminal instructions **to newbies for stuff that doesn't need to be done in the terminal**. Probably best to politely thank/ignore them and find someone who can give you better instructions. **There's no need to be falling back on the terminal for something as simple as installing software.**


 that's it, and dont get surprised but thats comom for us  (newbies), we ussually found that kind of instrunction at our very first  steps into ubuntu nowadays, and MANY webpages explain the same way...

---

### Post by Kharlo on 2012-09-10
> **Vaphell said:**
> terminal: ctrl+alt+t, or win key/ubuntu icon, 'terminal' in search box

forget how things are done in windows, think app store and android whatever-it's-called. We don't scour the internet for random crap to install here.

considering you are new you should always try this path:
**official repos ---> 3rd party repos -> .deb files ----------> (tar.gz, source code, compilation)**

if you go back to post #7 while having the terminal window opened, highlight the commands and middleclick paste them in terminal (or use ctrl+c, ctrl+shift+v) one by one.
it will add official opera repo and you won't have to do anything around opera ever.


Most often you will get instructions in text form for terminal, because it's faster and more foolproof than going with page long description of click here, then click there.

how do i use that? where do i enter it?

---

### Post by critin on 2012-09-10
> **Kharlo said:**
> Thank you for answering!

i know about the software center... and about the beta and unstable stuff.. (thanks for the advice)
i just wanted the lates version, i read in wine page that the1.4 was already available for my linux version but their instructions doesnt works clearly...

if theres no much difference between 1.2 (the one form software center) and 1.4 then i'll install it...

Do you know where your Software Center is?  You don't have to follow instructions from the wine page for that.  Open Software Center, type in 'wine' in the search box, and it will come up.  all you have to do is click INSTALL.  

But I warn you, configuring it and getting it to work isn't easy.

>   i just have been able to install LibreOffice...
God.. why!...

a friend was trying to help me...
and told me to run the installation from terminal.. i barely know what the terminal is (despite i didnt knw where to write those codes)....
i got instruction to rick click aand hit install.. come on WHERE? this 10.04 doesnt have that option..  

10.04 already has Open Office doesn't it?   If you want Libra Office, again, go to Software Center and search for that name.  Then click INSTALL.  You're done.

> then they clarify me that i have to install the nautilus (why you didnt told me that before if most 10.04 dot have it?)

Why did you need nautilus?

> then i installed it.. but still no "open in terminal" WHY you didnt tell me tht i had to enable it then after install [why is not enabled by itself after installed?]  and after that i had to make some config_data... stuff..

Forget about the terminal--learn the Software Center way first.  Learn the terminal later.  If you spell something wrong in the terminal, you could break the whole system.

> all this after trying to introduce the repository to software center {dont ask me how..}. and modifying software stuff...  

Wait until you learn a bit more before trying to do this.  Using the terminal is easier, but only for those who know how.  You'll learn, but give yourself some time.

Whatever you want to install, check in the Software Center for it first--not on the web.  It really does have almost anything you'd need.  It does all the work of installing for you.

Relax and smile.  ;)

---

### Post by Kharlo on 2012-09-10
> **mastablasta said:**
> as mentioned in post #7 you can open software center **and then add repository there, you then add the key to repository (**this is ment to protect you form getting any malware) and then you update the software list and Opera will apear in software center, where you can choose it to install it. once installed all or any updates to the software will be done automaticly via software package manager/updater. post #7 did all this in a few short command lines you can copy and paste to terminal. but all this can be doen via GUI.

add repository WHERE?, and how? and what key? the code?

> **mastablasta said:**
> 
 
additionally i saw you mentioned that you dont' like the look of Ubuntu  12.04 and you have for that reaosn went to 10.04. but did you knwo oyu  can easilly install and select different looks such as Gnome fallback  (same look as the one in 10.04), Mate (for and continuing development of  old look), Cinamonn (traditional desktop look). aside form these gnome  desktops you can also use a completely different desktop environment  form Gnome (for example the one found in Kubuntu, Xubuntu, Lubuntu, ...)  there are also plenty widnows managers (Icewm, jwm, openbox...). each  of these can be customized a lot and themes are offered on internet. for  example it's quite easy to make Xubuntu look like old Ubuntu (involves  right clicking on stuff and selecting propperties and then changing them  to match the old look). so with so much choice i see really no good  reason to change to 10.04 just because of the look. 10.04 is supported  unitl april 2013, while 12.04 will be supported until April 2017

not just the look.. i mean.. i dont knwo if those "skins" you mentioned change that awful sidebar.. but my two main problems with THAT ubuntu were.. that sidebar... i dont know which app or window are sotred there or not, if so i have to scrool down several econds to get it.. or just to know if it's still open... but then i needed a softwae that help me to analize sounds.. i didnt remember the name but i didnt know how to see all the programs installed (not going to the application store and see what i have installed) i mean.. a menu with my apps or softwares or whatever...so was not just the look...

i know learning new things its ok (i am not old) but there are some things that shouldn't be learned, isntead just used.. its like to learn to use anew tool to do the same the other tool used to do.  for me was unpractical since i use ubuntu just for backup (in case everything fails in this machine) and couple of apps.

---

### Post by Vaphell on 2012-09-10
what i meant was:
if you need program X
1) check if it's available in standard repos right off the bat
2) if not, check with google if there are 3rd party repos/PPAs (personal package archives) - '<program name> ppa' or '<program name> repository' or something like that, the more official the better
3) if not, check with google if there are .deb files to be found (your classic setup.exe/msi way)
4) tar.gzipped source code, not exactly rocket science, but intimidating for beginners nonetheless ;) Combo of *./configure && make && sudo make install* works in 90% of cases

opera fits in #2, you can add the repo with either gui tools (Software Sources or something, i am at 10.04 so i don't know the exact procedure in newer releases) or terminal - instructions are most likely to be found earlier in this thread. After that opera will be available in software management program and will update automatically once installed.

Personally i use the terminal path described in #7 - paste few commands and it just works. Magic!



ctrl+alt+t or in unity win-key/ubuntu icon, 'terminal'
ctrl+c/ctrl+shift+v one command at a time (or use highlight/middle-click paste)

this one adds the repo:
```
sudo add-apt-repository 'deb http://deb.opera.com/opera/ stable non-free'
```
this one sets up authorization for the repo
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```
refresh the list of packages so opera is available
```
sudo apt-get update
```
install opera
```
sudo apt-get install opera
```

---

### Post by Kharlo on 2012-09-10
> **critin said:**
> Do you know where your Software Center is?  You don't have to follow instructions from the wine page for that.  Open Software Center, type in 'wine' in the search box, and it will come up.  all you have to do is click INSTALL.  

But I warn you, configuring it and getting it to work isn't easy.


yes i know where it is..

its just that the wine in software center is 1.2 version

curiously i have had almost all the windows apps that i wanted working fine in wine

> **critin said:**
> 
10.04 already has Open Office doesn't it?   If you want Libra Office,  again, go to Software Center and search for that name.  Then click  INSTALL.  You're done.

Nop, Libre is not there

> **critin said:**
> 
Why did you need nautilus?



to install the Libreoffice (i downloaded it from its webpage) 

i had to do this
> **Installation of LibreOffice on Debian/Ubuntu-based Linux systems**

 The instructions here are for installing LibreOffice in US English,  on a 32-bit system; there will be slight differences in some directory  names if you are installing LibreOffice on a 64-bit system, but the  process is basically the same and – hopefully – you will not find these  instructions difficult to follow.
 For instructions on how to install a language pack (after having  installed the US English version of LibreOffice), please read the “[Installing a Language Pack]("http://www.libreoffice.org/get-help/installation/linux/#Installing_a_Language_Pack")” section.
 1) After downloading the installer archive file, use Nautilus to decompress it in a directory of your choice (your Desktop directory, for example). After decompressing it, you will see that the contents have been unpacked into a directory called LibO_3.3.0rc1_Linux_x86_install-deb_en-US or LibO_3.4.5rc2_Linux_x86_install-deb_en-US. Open a Nautilus file manager window, and change directory to that directory.
 2) The directory contains a subdirectory called DEBS. Change directory to the DEBS directory.
 3) Right-click within the DEBS directory and choose *“Open in Terminal”*.  A terminal window will open. From the command line of the terminal  window, enter the following command (you will be prompted to enter your  root user's password before the command will execute):
  sudo dpkg -i *.deb
 4) The above dpkg command does the first part of the installation  process. To complete the process, you also need to install the desktop  integration packages. To do this, change directory to the desktop-integration directory that is within the DEBS directory, using the following command:
  cd desktop-integration
 Now run the dpkg command again:
  sudo dpkg -i *.deb
 The installation process is now completed, and you should have icons  for all the LibreOffice applications in your desktop's  Applications/Office menu.


the problem was, { ias i told you before, as many explanations over the net....]

i didnt had the right click option of "Open in Terminal" i had to find another instruction of how to enable it:
[http://askubuntu.com/questions/117452/how-do-you-add-open-in-terminal-to-the-right-click-mouse-menu-for-folders-dire](http://askubuntu.com/questions/117452/how-do-you-add-open-in-terminal-to-the-right-click-mouse-menu-for-folders-dire)

after that i was able to "smoothly" install the Libreoffice

---

### Post by Vaphell on 2012-09-10
libre office PPA
[https://launchpad.net/~libreoffice/+archive/libreoffice-3-5](https://launchpad.net/~libreoffice/+archive/libreoffice-3-5)
instructions are there

look for PPAs before you resort do .debs

---

### Post by Kharlo on 2012-09-10
> **critin said:**
> 
Whatever you want to install, check in the Software Center for it first--not on the web.  It really does have almost anything you'd need.  It does all the work of installing for you.


i just wanted newer version in couple of soft.. but it doesnt worth the time i spend....


> **critin said:**
> 
Relax and smile.  :wink:


thanks!

(that REALLY was the most difficult part)

but i still consider that's not right, it's like if linux would be a pizza served in a table but is not finished, the diners must eat it just how it is or to learn to cook it just right there over the table while the others are already eating the dessert. or some have even left the restaurant

---

### Post by Kharlo on 2012-09-10
> **Vaphell said:**
> libre office PPA
[https://launchpad.net/~libreoffice/+archive/libreoffice-3-5](https://launchpad.net/~libreoffice/+archive/libreoffice-3-5)
instructions are there

look for PPAs before you resort do .debs

.............................
thank you but .......  i hope that way change in future...

---

### Post by Kharlo on 2012-09-10
i am almost done here..

the last app i need to install

teamspeak...

the one from the software center is old.. but it seems to work.. 

what do you suggest me?

i downloaded the one from the author page

it has another neeeeew file extension  *.run  how do i eat that

(i had to use my gray stuff not to learn to use the software.. but to install it..., i really admire linux users)

---

### Post by Vaphell on 2012-09-10
> thank you but ....... i hope that way change in future...
what's wrong with it? PPAs kick ***, deb files not so much.


> it has another neeeeew file extension *.run how do i eat that
it's meant to be run (like setup.exe)
set it to executable in file properties or in terminal: chmod +x file.run
```
chmod +x file.run
```
and then run it (assuming you are in the correct directory):
```
sudo ./file.run
```

---

### Post by Kharlo on 2012-09-10
> **Vaphell said:**
> what's wrong with it? PPAs kick ***, deb files not so much.



it's meant to be run (like setup.exe)
set it to executable in file properties or in terminal: chmod +x file.run
```
chmod +x file.run
```and then run it (assuming you are in the correct directory):
```
sudo ./file.run
```

ahhh the poit is the same again

 i didnt know that...

and now that i remember, the window asking me to run it.. its familiar to me.. why i had to make it executable in this linux version? i thought i have done it before without marking it as executable

anyway  it did not installed it, it extracted it
now i have a folder "TeamSpeak3-Client-linux_x86"

what do i have to do to get it running?

---

### Post by mastablasta on 2012-09-10
> **Kharlo said:**
> add repository WHERE?, and how? and what key? the code?
 .
See the manual in my siganture. key is to validate that repository is correct one.
 
> 
not just the look.. i mean.. i dont knwo if those "skins" you mentioned change that awful sidebar.. .
 
oh yeah they change it. some dont' even have it.
Kubuntu looks like windows. you can right click K menu and slect classic view. it then looks like windows XP enhanced. : [http://news.softpedia.com/news/Kubuntu-12-04-LTS-Screenshot-Tour-266524.shtml](http://news.softpedia.com/news/Kubuntu-12-04-LTS-Screenshot-Tour-266524.shtml)
 
Xubuntu: [http://xubuntu.org/screenshots/](http://xubuntu.org/screenshots/)
 
Cinamonn (default in Linux mint) looks like this: [http://news.softpedia.com/news/Linux-Mint-13-RC-Cinnamon-Screenshot-Tour-270113.shtml](http://news.softpedia.com/news/Linux-Mint-13-RC-Cinnamon-Screenshot-Tour-270113.shtml)
 
> **Kharlo said:**
>  
and now that i remember, the window asking me to run it.. its familiar to me.. why i had to make it executable in this linux version?  
because the file itself can't execute or be executable. the user must allow it to execute. why? well let's say you install a userfriendly windows  OS. then you insert a USB key with malware on it. virus can then automaticly install (autorun anyone?). Ubuntu is an OS from server and this kind of automatic instalation is a no-no there. and it is also a very good protection on desktop OS:
>  
what do i have to do to get it running?
there should be a file inside that you war executable and then just create a shortcut to it. or run it from terminal. 
 
> **Kharlo said:**
> .............................
thank you but ....... i hope that way change in future...
 i doubt PPA way will change. especially since it is still relatively safe way. not as safe as official repos, but still quite safe. additionally it provides updates.
 
and besides ubuntu mostly has .deb files that can be used which are kind of like .exe installers in windows. and can be run by double click and then entering the user pasword (i.e. allowing them to be run)

---

### Post by Kharlo on 2012-09-10
> **mastablasta said:**
> 

**there should be a file inside that you war executable and then just create a shortcut to it. or run it from terminal. **
 

 i doubt PPA way will change. especially since it is still relatively safe way. not as safe as official repos, but still quite safe. additionally it provides updates.
 
and besides ubuntu mostly has .deb files that can be used which are kind of like .exe installers in windows. and can be run by double click and then entering the user pasword (i.e. allowing them to be run)


:confused:

i marked as executable any file that looks like to "start installation" and nothing



now i am also stuck with the java runtime package

[http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)

i read and i read... i am tired...

---

### Post by mips on 2012-09-10
Kharlo,

May I ask why you are running 10.04 in the first place as the software will be outdated and you seem to want newer versions of things?

Why not use 12.04 or the soon to be release 12.10 when it comes out?

---

### Post by mastablasta on 2012-09-10
you want oracle java (open JDK is there by default)? read here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
 
do you get the file ts3client_runscript.sh or similar? have you seen this? : [http://community.customcms.net/topic/57-tut-install-teamspeak3-on-debianubuntu/](http://community.customcms.net/topic/57-tut-install-teamspeak3-on-debianubuntu/)
 
yeah it seems a bit complicated. i wonder what the reason was (License?) they are not incuded in official repositories or at least they could give users the .deb file.
 
EDIT: yup, it's the license issue. As a "bonus" their code is not open source.

---

### Post by shreepads on 2012-09-10
> **Kharlo said:**
> 

now i am also stuck with the java runtime package

[http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)

i read and i read... i am tired...

Hmm did you read the line near the top which links you to:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Just look for openjdk-6-jre package via Synaptic... BTW avoid the browser plugin if you can, given the multitude of Java vulnerabilities being exploted...

On the whole, I feel your pain, but if you stick with a bit it does get a lot easier!!! 

As mentioned by everyone your install methods should be in this order
a. Official repositories via Software Centre/ Synaptic
b. PPAs
c. .deb files
d. Download source and compile

---

### Post by jerome1232 on 2012-09-10
--- quip----

double post

---

### Post by Kharlo on 2012-09-10
> **mips said:**
> Kharlo,

May I ask why you are running 10.04 in the first place as the software will be outdated and you seem to want newer versions of things?

Why not use 12.04 or the soon to be release 12.10 when it comes out?


you are right, new version of things, but i dont want the 12.04

ok this is my situation

this is how i ussually use windows (windows 7):
-Firefox and opera opened
    firefox with about 50 tabs (using half of them and the other half in standby[i mean not for using it right now]) 
  and opera mainly for pages with videos (about 15 tabs more) while i investigate from those videos i open about 2 tab per video...  (i use opera for the videos because its faster to dig between video loaded tabs)
- three or four MS exel windows
-three or four Ms word windows
-video editor
-3d modeling
-image editor
-three or four MS Paint windows
-6 to 10 note pad (most of them unsaved)
-one audio editing software windows (audacity [the best]
-calculator
-a video player
-a music player
-outlook

its about 27 opened windows...
(and it's not an out-of-this-world machine, just a well administrated and maintained one)

i dont pretend to put that quantity of work on linux

Just the necesary;
-firefox
-the notepads (x6 minimum), the calc, the spreadsheets (x3), word (x3)
-image editor
-video player

Only with that, abot 14 windows on ubuntu 12.04 was AWFUL to use.. a headache to dig in the sidebar....
and now i remember the name of the softare...  Xoscope (an analog oscilloscope) but the shiny ubuntu 12.04 did not show me what i have installed in the machine, i needed the application and since i didnt remember the name i was unable to get it because the ubuntu 12.04 doesnt show all the aps in a human view...

in any other ubuntu.. i just hit; "Applications" and there was it....

who was the one who had the idea to hide all the apps and to bring it them by its name?

i have read several comments on internet about the guys of Unity...

anyway thats past i have ubuntu 10.04LTS

---

### Post by jerome1232 on 2012-09-10
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

3 liner to install Oracle Java in all of it's "glory", you can thank Oracles licensing for this difficulty, and their refusal to make a .deb



> **mastablasta said:**
> 
EDIT: yup, it's the license issue. As a "bonus" their code is not open source.

Reasons I switched to Mumble as my voice server, this licensing crap is ridiculous.

---

### Post by Kharlo on 2012-09-10
> **shreepads said:**
> Hmm did you read the line near the top which links you to:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Just look for openjdk-6-jre package via Synaptic...[B] BTW avoid the browser plugin if you can, given the multitude of Java vulnerabilities being exploted...
[/B] 
On the whole, I feel your pain, but if you stick with a bit it does get a lot easier!!! 

As mentioned by everyone your install methods should be in this order
a. Official repositories via Software Centre/ Synaptic
b. PPAs
c. .deb files
d. Download source and compile


Opss...
thts exactly what i did..
what can i do?

---

### Post by Kharlo on 2012-09-10
Well... i have to go..
i have to sleep about 15 continuous hours in a computer... not working.. just installing opera, libreoffice, java, teamspeak, wine and couple more..
i'll be back in 4 or 5 hours
 ( i will wont sleep too much, i should, but i hate to have pending things, an i want to finish this linux stuff )

see you later guys

---

### Post by mips on 2012-09-10
> **Kharlo said:**
> you are right, new version of things, but i dont want the 12.04

ok this is my situation

<snip>

You can't stay on 10.04 for ever either as support for it will end early next year.

There are other options to Unity as well like gnome shell, kde & xfce. A lot of the old gnome users have move to xfce as it's very similar to the old gnome. Maybe try them out in virtualbox and see if any of those three suite your needs maybe and then switch? There's also linux mint using ubuntu repos with different user interface options.

---

### Post by mastablasta on 2012-09-10
> **Kharlo said:**
> Opss...
thts exactly what i did..
what can i do?
 
you can (should?) disable it in browser.
 
> **Kharlo said:**
> Well... i have to go..
i have to sleep about 15 continuous hours in a computer... not working.. just installing opera, libreoffice, java, teamspeak, wine and couple more..
i'll be back in 4 or 5 hours

 
LOL i have it all done in 15 minutes on clean install. i also add more programmes. perhaps this would be even faster with an automated a script. and i am very new to this as well and use GUI as much as possible. 
 
btw do you need picture editor (Gimp) or vector graphis (inkscape).
 
the many windows complaint i think i read about before. and as suggetsed a different interface might be better for you. it can be installed from software center. 
 
also note that you can have multiple dekstops open. each can even be made to look different.
 
i am not sure why searchign for aplication would be better, but new things will come when you will search for things like File-> print in menu (it will be called HUD menu). it makes sense in some devices but if you mostly use mouse as input device then it is useless. hence try Kubuntu desktop (can be installed from software center).

---

### Post by Paqman on 2012-09-10
> **Kharlo said:**
> you are right, new version of things, but i dont want the 12.04

You can't have it both ways. If you want up-to-date packages, you need to use an up-to-date release of Ubuntu.

> 
Only with that, abot 14 windows on ubuntu 12.04 was AWFUL to use.. a headache to dig in the sidebar....

12.04 comes with the option of several different desktop environments. The sidebar versions (Unity) is not the only one. You can choose from several such as:

Kubuntu
[IMG]http://www.kubuntu.org/themes/kubuntu10.04/images/feature-tour/office/feature-tour-apps-ooo4.png[/IMG]

Xubuntu
[IMG]http://xubuntu.org/wp-content/uploads/2011/09/precise_01-400x300.png[/IMG]

Lubuntu
[IMG]http://upload.wikimedia.org/wikipedia/en/thumb/c/cc/Lubuntu_12.04.png/600px-Lubuntu_12.04.png[/IMG]

These are all versions of Ubuntu, and use the same repositories. Installing one would allow you to use up-to-date applications without having the Unity interface. You might also want to check out Linux Mint, which is a version of Ubuntu with a desktop style closer to the old one you have on 10.04.

You can actually install any of these desktops on any version of Ubuntu, and you can have more than one installed if you want to try them out without reinstalling everything.

---

### Post by newb85 on 2012-09-10
@ Kharlo,

I want to reiterate and expound on a few good points others have made here.

The alternatives to Unity aren't "Skins".  They're different Desktop Environments, and if you run them, Unity will not be running at all.  You will be a lot better off if you use 12.04 with one of them than if you use 10.04.  Despite still being supported, 10.04 is still two years old, and won't be able to (easily) do some of the things you see others doing with 12.04.  Gnome Fallback will give you the closest experience to Ubuntu 10.04, but given how you use your machine, Mate will give a better experience and still offer the layout flexibility you want.

Wine isn't easy to use.  Before using it, I strongly urge you to search for linux-native alternative applications for what you want to run in Wine.  Start your search with the Software Center, as the software you find there is easiest to install.  If you're not satisfied with the options in the main repositories, the next place you should look is PPAs.  

Two great sites I've found indispensable for adding PPAs are [webupd8.net]("webupd8.net") and [omgubuntu.co.uk]("omgubuntu.co.uk").  I've added several PPAs from these sites, and it was as easy as copying and pasting to the terminal.  As an example, I recommend you go to the article [here]("http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets") and install Caffeine according to the instructions.  (Note, this may not work for 10.04.) The article gives a description of what Caffeine does.

You mentioned that you hope the ppa method for installing in the future changes.  I strongly hope it doesn't.  Centralized package management is one of the great strengths of Linux.  Sure, the installation mindset takes a little adjustment coming from Windows/Mac, but it's definitely worth it.  Someone trying to install all their software in Linux the Windows way (browse the web and download the package they want, and then manually install it) is analogous to someone driving an airplane down the highways from New York to Chicago, complaining all the way that it would be so much easier in a car.

---

### Post by newb85 on 2012-09-10
I should add that the instructions in that article are commands that should be copied and pasted one-line-at-a-time into the terminal.  In 12.04, the terminal is opened by Ctrl+Alt+T.

---

### Post by newb85 on 2012-09-10
> **Kharlo said:**
> you are right, new version of things, but i dont want the 12.04

ok this is my situation

this is how i ussually use windows (windows 7):
-Firefox and opera opened
    firefox with about 50 tabs (using half of them and the other half in standby[i mean not for using it right now]) 
  and opera mainly for pages with videos (about 15 tabs more) while i investigate from those videos i open about 2 tab per video...  (i use opera for the videos because its faster to dig between video loaded tabs)
- three or four MS exel windows
-three or four Ms word windows
-video editor
-3d modeling
-image editor
-three or four MS Paint windows
-6 to 10 note pad (most of them unsaved)
-one audio editing software windows (audacity [the best]
-calculator
-a video player
-a music player
-outlook

its about 27 opened windows...
(and it's not an out-of-this-world machine, just a well administrated and maintained one)

i dont pretend to put that quantity of work on linux



I fully expect that you should be able to do all this in Linux--with the exception, of course, that you're best off not using the MS Office applications.  Instead of Outlook, you can try Thunderbird (more mainstream), but I recommend Evolution.

---

### Post by oldos2er on 2012-09-10
> **newb85 said:**
> Someone trying to install all their software in Linux the Windows way (browse the web and download the package they want, and then manually install it) is analogous to someone driving an airplane down the highways from New York to Chicago, complaining all the way that it would be so much easier in a car.

I'd not heard that one before. Nice analogy.  :)

---

### Post by Kharlo on 2012-09-10
> **newb85 said:**
> I fully expect that you should be able to do all  this in Linux--with the exception, of course, that you're best off not  using the MS Office applications.  Instead of Outlook, you can try  Thunderbird (more mainstream), but I recommend Evolution.

i don plan to use my emails from ubuntu because i use outlook with 7 accounts some of then non hotmail (which mean messages are saved in the pc) changing that back.... the less i have the balls all around.. the best are to keep safe

fore safety reasons.. some things.. i dont like to run it at the same times.. due sync issues  and the most important when disasters come... its easier and safer to keep control and backup of only one thing

> **newb85 said:**
> 
Someone trying to install all their software in Linux the Windows way  (browse the web and download the package they want, and then manually  install it)

i beg to differ... many complain that windows force users to do what bill gates want..... 
ANd i disagree, thats why windows is my main OS (beside MS flight simulator:P) i choose the software i want from wherever i want not what the OS  suggest me, ok i have experience using windows and in 14 years using computers i only have had ONE problem related to virus/spyware or malware, and you guys already know how i use the computer... (instead the computer using me) i mean I USE IT HARD.. even when i am not working on it i still use it with that quatity of windows opened... example.. if i want to read about a new car.. i open 5 to 10 youtube, about 15 to 20 pages with user reviews.. comparisons, pages with price infos... and since i like the type of engine it uses.. i open 10 pages more with info about that specific engine.. (lol i know it sounds crazy but i like to read a lot and in a flash...)
the point is.. i use the pc hard so it can be said that i am not prone to infections nor erros because i only use it to write a note while i check facebook and heard a music...

in all those 14yeas of use..  (one with mac, but i quit mac since i dont what the system telling me what to do lol) only want serious infection with security risk and system failure...  

> **newb85 said:**
> 
is analogous to someone driving an airplane down the  highways from New York to Chicago, complaining all the way that it would  be so much easier in a car.

it depends... lol it could be lot easier by car (if you are the pilot lol) JFK to ORD, busy skies, long holding times.... stressing as hell...

---

### Post by Kharlo on 2012-09-10
Guys... one of the point here is...
id like a free and "safe" OS where i could just use it right out of the box with minor emendations  and fixtures, each time i receive a recomendation for a mod not  included itn the options/preference of the OS itselft (At least for me)  its like a car i buy but now i have to purchase tires (its a car its  supposte to be used over roads), also a battery, and i have to add an additive to the oil...

(i  know the one particular and famous thing of linux is its customization  (at my judge... in excess.. affecting focus and agility)

this is working from fixture over fixture...  

> **mastablasta said:**
> you can (should?) disable it in browser.
ifferent interface might be better for you. it can be installed from  software center. [/QUOTE

that was chinesse
is that a skin.. a theme?

[QUOTE=mastablasta;12229615]also note that you can have multiple dekstops open. each can even be made to look different.
nooo  thats too much ( i already have 3 OS in this laptop) and to familiarize  with diferent desktop looks... i could imagine myself working in one  with couple of dozen of windows then i switch to another desktop...  since probably would have different controls i can clearly imagine  myselft loosing time or a job due hitting the wrong button since the  other desktop has different controls layout or something like that....

i am sorry i think you wont get the point since you are used to that, i understand you but i think you cant..

f  i compare this with a career.. it would by like a career where i past  most of the time learning how to use an alligator clamp and NOT in what i  can use it for.

> **Paqman said:**
> You can't have it both ways. If you want  up-to-date packages, you need to use an up-to-date release of Ubuntu.

12.04 comes with the option of several different desktop environments.  The sidebar versions (Unity) is not the only one. You can choose from  several such as:
Kubuntu
Xubuntu
Lubuntu

These are all versions of Ubuntu, and use....
I appreciate that.. i really didt know about it, i have heard it before but i thought those OS where more like skins Or like puppy linux (which i have installed too, and i love it!)

those OSs catched my attention... but the time i have invested in this 10.04 version.. i cant throw it down the toilet doing it again with another OS, i have many material pending to study and work to do that i have accumulated in this two days dealing with ubuntu.. may be for December so i need to leave this in a decent shape (ready to work if disaster happen, i just need to swich to linux and to continue using it not to learning using it)

but now i want to continue with the pending thins and TWO NEW MORE issues (that are common in ubuntu since i had it in other versions following me)

pending... install the right java stuff

new;
****the windows buttons move to the right when i saved the theme... the only difference in the theme from the original "ambience" are the colors... i did not installed theme so why does those windows button moved to the right? i wanted it to the left.. i did the mod of All + F2 gconfig...   */apps/metacity/general* 

but when i restart ubuntu the theme are changed to ambience, and when i select my theme (ambience but with two colors changed) the windows buttons move to the right

****the screen. when i restarted the pc.. the screen is set to 1024x768
the funny part is.. i am happy with that res (i am using a 19 inch monitor (so its quite big) but since i work with many windows mainly letter.. bigger resolution looks really nice but not for hard reader.... and a people who move fast between windows...
Ok, no probelm with the resolution... the point here is the same reason i quit mac. i dont want the system do what it wants if i want 1024x768 I change it, not the system. (sounds funny but i hate that)

this is a laptop with a docking station, this would be normal if tha laptop were open, but i use it with lid close, so there is not reason why ubuntu find a compatible resolution for bot screens.

and i was using it 1280x1024 yesterday so why after restart switch to 1024x768? and give me no option to increase it?

the only way to get a bigger reso is to open the laptop's lid and to hit the button for selecting the screen (to remember to the ubuntu that the screen i am using it is the big one) and then close back the lid, but if i hit any key it switch back to 1024x768.

---

### Post by Kharlo on 2012-09-10
Crap...  Kubuntu looks pretty nice and comfortable for hard work..

i have the remaining of this day to decide if i keep the 10.04 or if i switch... but i cant spend 14 hours again in bringing the OS to a fully operative and trouble free status...


some quick questions...
if i swich to one of those buntus... do i have to change forum.. i mean can you assit me (i ask this because this form is ubuntu.org not kubuntu/lubunt/xubuntu org.....) the answer could be obvious but i dont like to suppose things

does it come with libre or open office?

does the apps i got from software center install in those buntus?

does hibernates without problem?

safety... doest it let me to chose to encryp the whole system like ubuntu does (it ask it when installing)

i guess those buntus has grub 2 too, so i can continue using grub to manage all the other OS in the pc right?

i already have 15 tabs with infos (looking for the main differences betwen lu, xu and ku

im most between ku and xu.... the lubuntu.net page has problem (one point less)

---

### Post by Lars Noodén on 2012-09-10
Lubuntu, Xubuntu, Kubuntu and Ubuntu users all can use this forum.  It's all the same basic system.  Mainly only the desktop environment is different, plus a few default applications.  Other than that you can add or remove any packages that you wish.

Some come with LibreOffice, some don't.  But it is easy to add it from the software center if it is not there.  

And, yes, it's all software from the same repositories so you can add the same software from the software center on any of them.

Disk and home directory encryption are still options if you wish.

Grub2 is there also.

Hibernate should work but that is more dependent on your hardware than on the distro.

---

### Post by Kharlo on 2012-09-10
[[IMG]http://www.freeimagehosting.net/t/w5dvr.jpg[/IMG]]("http://www.freeimagehosting.net/w5dvr")
[http://www.freeimagehosting.net/w5dvr](http://www.freeimagehosting.net/w5dvr)

there it says that Kubuntu is not for entry level...

the Xubuntu would be for me?

---

### Post by jerome1232 on 2012-09-10
> **Kharlo said:**
> [[IMG]http://www.freeimagehosting.net/t/w5dvr.jpg[/IMG]]("http://www.freeimagehosting.net/w5dvr")

there it says that Kubuntu is not for entry level...

the Xubuntu would be for me?
 
hogwash, just try them out. You can even add them to your current install just for testing purposes, then go for a clean install once you find you like one.

Kubuntu:
```
sudo apt-get install kubuntu-destkop
```Gnome-shell:
```
sudo apt-get install gnome-shell
```Gnome-classic (very much like gnome2)
```
sudo apt-get install gnome-session-fallback
```Xubuntu:
```
sudo apt-get install xubuntu-desktop
```Lubuntu:
```
sudo apt-get install lubuntu-desktop
```To change sessions, click the Ubuntu Icon next to your name at the login screen and select the session you want to login as, it will be your default next time you log in.

---

### Post by Kharlo on 2012-09-10
> **jerome1232 said:**
> hogwash, just try them out. You can even add them to your current install just for testing purposes, then go for a clean install once you find you like one.

kde:
```
sudo apt-get install kubuntu-destkop
```Gnome-shell:
```
sudo apt-get install gnome-shell
```gnome-classic (very much like gnome2)
```
sudo apt-get install gnome-session-fallback
```Xfce:
```
sudo apt-get install xubuntu-desktop
```lxde:
```
sudo apt-get install lubuntu-desktop
```To change sessions, click the Ubuntu Icon next to your name at the login screen and select the session you want to login as, it will be your default next time you log in.

chinesse again


then.. after installing  xubuntu... do i have to run ```
sudo apt-get install gnome-shell
```
?
and the others linsk/codes are options or is it necessary to install it too?

are thos optios? necesaries? skins? updates? doesnt the xubuntu come with it?
(getting complicated again)

---

### Post by jerome1232 on 2012-09-10
I'm saying there is no need to reinstall to try a flavor of Ubuntu out, you can just install a package and try it out.

the single line below xfce will install everything that comes with an Xubuntu install, so that you can try it out to see if you like it or not without reinstalling. Each line would install the respective environment.

If I wanted to try out gnome-classic (I recommend you try it) I would run the single command below "Gnome-classic".

I hope that helps clarify things a little. I edited that post to hopefully clear it up a little.

---

### Post by Kharlo on 2012-09-10
> **jerome1232 said:**
> I'm saying there is no need to reinstall to try a flavor of Ubuntu out, you can just install a package and try it out.

the single line below xfce will install everything that comes with an Xubuntu install, so that you can try it out to see if you like it or not without reinstalling. Each line would install the respective environment.

If I wanted to try out gnome-classic (I recommend you try it) I would run the single command below "Gnome-classic".

I hope that helps clarify things a little. I edited that post to hopefully clear it up a little.

uhmu..
what' is gnome classic?
and whats the difference between gnome classic and the equivalent that came with xubuntu?

---

### Post by jerome1232 on 2012-09-10
Gnome Classic is Gnome3 but it looks a lot like the old gnome2 (which is what you used on your older install) It's less customizable than gnome2 but you get your old application menu's like your used to having.
Gnome3 is what Unity and Gnome-shell are built on top of.

Xubuntu isn't gnome at all. It's xfce. I'm not sure what you mean by "equivalent that came with Xubuntu"

---

### Post by Kharlo on 2012-09-10
> **jerome1232 said:**
> Gnome Classic is Gnome3 but it looks a lot like the old gnome2 (which is what you used on your older install) It's less customizable than gnome2 but you get your old application menu's like your used to having.
Gnome3 is what Unity and Gnome-shell are built on top of.

Xubuntu isn't gnome at all. It's xfce. I'm not sure what you mean by "equivalent that came with Xubuntu"

by equivalent.... i men.. since i didn't knew that xubuntu was xfce..

then now i know that the equivalent to gnome in xubuntu is xfce, am i wrong?

another doubt

now i realize that Gnome has  its bunch of software
i know and i use;
Gparted (pretty nice!)
Gperiodic (a periodic table)
Gedit

and some other Gstuff...

since xubuntu es not Gnome.... can i still use those apps that belong wiht G?

---

### Post by Norm24 on 2012-09-10
If you install the lubuntu,xbuntu or kubuntu desktops you will also install every single program that comes with those distros and said programs will show up regardless of what desktop you log in under.This can create a giant confusing mess of programs.

For example if you install the lubuntu desktop and you decide you don't like it and uninstall the lubuntu desktop you will still have all the programs that came with it still on your machine and you must manually remove these.

---

### Post by Kharlo on 2012-09-10
Great.. so i dont have to worry for most known and common apps i see in ubuntu, the all will work in xubuntu (i decide for xubuntu, i am downloading it (1:30hours left.... i am slow connected)

i have more questions

what about safety and security?
the same?
i have a concern about the MBR and encryption.. since my ubuntu files are encrypted untill i log in... can the grub info be stored in the partition where linux is?
 currently, my  "menu.lst" is in the windows partition... so with only opening "my Pc -> C:/ = there it is the menu.lst" with just a simple delete from the windows itselft, the pc can be left unbootable...

what do you recommend me for protecting the boot?

*i have two primary partition;
-one for windows
-and another for linuxs
*the one for linux has three logical ones;
-one for ubuntu (that will be replaced by xubuntu)
-another for puppy linux
-and the last one is the swap for both linux distros

that order and combination has worked rock solid for me
but i dont want the menu.lst so vulnerable in the windows (the most used partition) partition.

---

### Post by newb85 on 2012-09-10
> **Kharlo said:**
> 

now i realize that Gnome has  its bunch of software
i know and i use;
Gparted (pretty nice!)
Gperiodic (a periodic table)
Gedit

and some other Gstuff...

since xubuntu es not Gnome.... can i still use those apps that belong wiht G?

Certainly.  There are two main differences between the Gnome-based apps and, for example, the KDE-based apps.  [LIST]
[*]For one, they are based on different libraries, which are basically under-the-hood packages that they need to run.  If you try to install--through the centralized package management system--a program that requires libraries you don't have, the package management system will automatically install them for you.
[*]Look and feel--this is a result of the common libraries, but the overall look and feel of a "set" of apps is usually unified.  The buttons, scrollbars, tabs, etc. all usually look the same.  (These things can be changed through themes.)
[/LIST]

---

### Post by jerome1232 on 2012-09-10
> **Norm24 said:**
> If you install the lubuntu,xbuntu or kubuntu desktops you will also install every single program that comes with those distros and said programs will show up regardless of what desktop you log in under.This can create a giant confusing mess of programs.

For example if you install the lubuntu desktop and you decide you don't like it and uninstall the lubuntu desktop you will still have all the programs that came with it still on your machine and you must manually remove these.

Which is why I mentioned it for testing purposes only, to get an idea of the look and feel of some without going through an entire install.

-----

You shouldn't have a menu.lst on your windows drive. I don't think even Wubi puts on one there. :?:

---

### Post by Vaphell on 2012-09-10
> If you install the lubuntu,xbuntu or kubuntu desktops you will also install every single program that comes with those distros and said programs will show up regardless of what desktop you log in under.This can create a giant confusing mess of programs.

*-desktop are metapackages that include tons of packages (associated apps and whatnot), but it's not necessary. You can install only bare environments, eg xfce4, lxde, kde instead of [xkl]ubuntu-desktop.

---

### Post by Kharlo on 2012-09-10
Ok i need help!

i instaleld xubuntu (looks pretty nice but) and after isntallation complete, it restarts but was not able to boot, there was no grub sight, only somethink about; "grub error"

---

### Post by Kharlo on 2012-09-10
this is the error i got:


error: the symbol 'gurb_xputs' not found.
grub rescue>



i got this 
sudo mount /dev/sd**XY** /mnt sudo grub-install --root-directory=/mnt /dev/sd**X**from here
[http://ubuntuforums.org/showthread.php?t=1580752](http://ubuntuforums.org/showthread.php?t=1580752)


Windows is in sda1
xubuntu in sda7
puppy in sda6

i choose the encryption option when installing xubuntu.. can i choose sda7 to install the grub or the boot or the MBR (i am not too clear with that)
i know how to modify both grub 1 and 2, but i confuse MBR with grub and with boot

the idea i have... MBR the space of the disk designated for boot, and the gru is who manage the boot? is it that way?

---

### Post by Kharlo on 2012-09-10
this is the image of the disk/partition where the boot/grub/mbr is..
[[img]http://www.freeimagehosting.net/t/ce9mn.jpg[/img]](http://www.freeimagehosting.net/ce9mn)

what should i delete, whicho of those files doesn't belong to windows? can i delete it and install then in the proper linux partition?


i need HELP

---

### Post by Kharlo on 2012-09-10
nobody?

---

### Post by Kharlo on 2012-09-10
i was able to solve it with grub4dos

---

### Post by Kharlo on 2012-09-11
do i have to uninstall grub nor grub2 when i have grub4dos?

---

### Post by critin on 2012-09-11
> **Kharlo said:**
> i was able to solve it with grub4dos

do i have to uninstall grub nor grub2 when i have grub4dos?

No--If all boots now, don't touch anything else.  


>  this is the image of the disk/partition where the boot/grub/mbr is..

That image is the file manager of Windows, not the actual disk partition--
Those are the files you're sharing with xubuntu.  You can open them and work with them, but don't mess with the boot files.

Glad you got it going.

---

### Post by newb85 on 2012-09-11
Sounds like when you installed Xubuntu, you selected the Windows partition for the MBR.

---

### Post by Kharlo on 2012-09-11
oh oh...

more problems...

grub4dos makes my windows 7 pirate (i have read that it is because it changes something and windows 7 interpret it has a hardware change then... "this is a non genuine copy.... which it isnt't)

this happened to me a year ago in another machine but i didnt relationate it with grub4dos, but i had the doubt about it, but now i confirms it.


> **newb85 said:**
> Sounds like when you installed Xubuntu, you selected the Windows partition for the MBR.
no, when i installed xubuntu i chose sda7, whcih is the xubuntu partition
but after it finished installing, the installation never worked, at the first reboot i got this:

error: the symbol 'gurb_xputs' not found.
grub rescue>

i used the live cd to reinstall grub (check my past comments) and didnt work, but i used a puppy linux live cd to install grub4dos (always work, even if youu install grub4dos in a tomato... if you get to install it in a tomato.. the tomato will boot up) it worked but the windows 7 genuinity stuff...

now i habe all kind of grub installed in almos every partition of the disk... the windows boot, the puppy linux boot, the grub 1, the grub 2 the xubuntu grub...


i need help
(sunked again in the very linux mud-like situations)

---

### Post by Zill on 2012-09-11
> **Kharlo said:**
> i have about two hours reading on internet how to install that packaged and i cant get it....

i am not going to argue about how difficult some things that shouldnt be in ubuntu ARE....  because the plain solution would be to choose to another OS....

but still make me a little bt mad....
As an enthusiastic Linux user I *do* like to support the use of Linux systems such as Ubuntu.  However, I also accept that Linux is not always the best choice for all users.

Having followed this thread, I  must suggest, reluctantly, that the OP might get the best outcome by a fresh installation of Windows 7 and then forget about installing Ubuntu or any of its variants.

---

### Post by zombifier25 on 2012-09-11
> **Zill said:**
> As an enthusiastic Linux user I *do* like to support the use of Linux systems such as Ubuntu.  However, I also accept that Linux is not always the best choice for all users.

Having followed this thread, I  must suggest, reluctantly, that the OP might get the best outcome by a fresh installation of Windows 7 and then forget about installing Ubuntu or any of its variants.

Exactly. If you want to work productively, use what you're comfortable with.

---

### Post by Kharlo on 2012-09-11
> **zombifier25 said:**
> Exactly. **If you want to work productively, use what you're comfortable with**.

You are right sir...

i just forget to mention from my very first comment

all this is to continue **working** productively IN CASE my windows fail
(could be a failure or any other situation that need the window to be left alone; example some updates or modifications that the system require before to continue working but i dont have time to attend it.. then i continue in linux)

this is like ma spare tire, but the main difference from me and other users is that i take more care of the spare tire than the main ones ( because i think of may spare tire as my lifeguard)

---

### Post by Kharlo on 2012-09-11
I was able to solve it again with the "boot-repair"
[http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

and i have restarted the machine 3 or 4 times and no problem wiht the genuine of windows, so i hope this to be the definitive solution.


thanks to the ones that suggested me the other ubuntu flavors, 
by now i have installed several apps and the only inconvenience i have had is that i haven been able to hibernate

when i try it i get this message:
failed to hibernate session
not authorized

---

### Post by oldos2er on 2012-09-11
Since your original issue seems to be solved, please mark the thread as "Solved" under Thread Tools, and start a new thread for your new question. Thanks!

---

### Post by Kharlo on 2012-09-12
> **oldos2er said:**
> Since your original issue seems to be solved, please mark the thread as "Solved" under Thread Tools, and start a new thread for your new question. Thanks!


Ok

Bye!

---

