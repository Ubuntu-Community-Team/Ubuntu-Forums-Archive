---
title: "How do i install openoffice 3?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by g2bandrew on 2008-10-20
I can't figure it out. I don't want to go into terminal and type in some complicated codes just to install a program, i just want it to install. So how do i install it normally (as in using some sort of GUI).

---

### Post by kellemes on 2008-10-20
I'm afraid you have no choice but to go terminal.. ;-)
[http://www.linuxpromagazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/installing_openoffice_org_3_0?blogbox]("http://www.linuxpromagazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/installing_openoffice_org_3_0?blogbox")

---

### Post by thomas228 on 2008-10-20
> **g2bandrew said:**
> I can't figure it out. I don't want to go into terminal and type in some complicated codes just to install a program, i just want it to install. So how do i install it normally (as in using some sort of GUI).

Went back and read the ubuntu installation tutorial on a SUN openoffice forum and sucseded in a complete installation on 2 laptops.

This is what I did

Selected "System > Administration > Synaptic Package Manager" and entered my password

In the package manager I selected the "Search" button and typed "openoffice" in Search and selected the Search button which gave me all of the openoffice packages.

I went thru all of the installed openoffice packages and markedthem with the "Mark for Complete Removal"
including "Mark" additional required changes.

Next I selected the "Apply" button and confirmed in the summary by selecting the "Apply" button

When this was finished I opened a terminal and did th following

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz 
cd OOO300_m9_native_packed-1_en-US.9358 
cd DEBS 
sudo dpkg -i *.deb 
cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

The only warnings I got were:

Setting up openoffice.org3-dict-en (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 

Setting up openoffice.org3-dict-es (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 

Setting up openoffice.org3-dict-fr (3.0.0-9) ...
javaldx: Could not find a Java Runtime Environment! 

These did not seem to harm anything for I was able to go in the "Applications > Office " and choose any of the 7 OpenOffice.org 3.0 options.   

(edit) These warnings would dissappear if I installed "ubuntu-restricted-extras" first.

:)The main key was to be sure I had removed all the OpenOffice packages with System Aministration Synaptic Packge Manager before installing the new tarball.:lolflag:

Hope this helps as ubuntu is not including OpenOffice3 either as an update for Hardy nor as part of Intrepid.

Tom

---

### Post by thomas228 on 2008-10-20
The tutorial I used as a guide

http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68

:)

Tom

---

### Post by drakeman007 on 2008-10-20
Hello! thanks for this useful post! another thing the instalattion replaces the actually installed  openoffice 2.4? or i have to uninstall it first?
Thanks!

---

### Post by g2bandrew on 2008-10-20
I got to step 1 of putting the code into terminal and it said "No such file or directory"

---

### Post by meho_r on 2008-10-20
It doesn't replace existing 2.4 so you can use both (I found a case in which I had to use old one ;))

---

### Post by drakeman007 on 2008-10-20
Ok, then im going to uninstall the 2.4 version before, my other question is if the installation programs impress, word, etc, puts automatically in the gnome menu under office?

Thanks

---

### Post by drakeman007 on 2008-10-20
Ok, then im going to uninstall the 2.4 version before, my other question is if the installation programs impress, word, etc, puts automatically in the gnome menu under office?

Thanks

---

### Post by swisscow on 2008-10-20
> **g2bandrew said:**
> I got to step 1 of putting the code into terminal and it said "No such file or directory"

Did you download the file and cd to the directory you put it in

```
cd Desktop
``` (probably)

---

### Post by drakeman007 on 2008-10-20
Anyone can confirm if when you install the openoffice3 it puts links automatically in the gnome menu under "office"

thanks!

---

### Post by Bölvaður on 2008-10-20
The reply number 3 did not mention that you are supposed to download a file from the openoffice.org website.

What he also fails to do is to tell you that these terminal commands are unnessecarly if you feel unconfortable with the terminal.
The only thing you need to do (what his commands are saying) is that you need to untar (unzip) the file, navigate to the .deb files and double click on openoffice.org3.0-debian-menus_3.0-9354_all.deb
When you double click that file, it will prompt you that you are going to install open office 3 and ask for your password when you accept the installation.

There is no reason to use terminal when installing most programs. But it is much easier and less text that goes into writing commands, because they are almost indipendant of the distro you are using, but every distro has different programs (almost same CLI, almost never same GUI)

---

### Post by thomas228 on 2008-10-20
> **drakeman007 said:**
> Ok, then im going to uninstall the 2.4 version before, my other question is if the installation programs impress, word, etc, puts automatically in the gnome menu under office?

Thanks

Yes the last 2 terminal steps put them in gnome under office

cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

hope this helps
Tom

---

### Post by thomas228 on 2008-10-20
> **Bölvaður said:**
> The reply number 3 did not mention that you are supposed to download a file from the openoffice.org website.

What he also fails to do is to tell you that these terminal commands are unnessecarly if you feel unconfortable with the terminal.
The only thing you need to do (what his commands are saying) is that you need to untar (unzip) the file, navigate to the .deb files and double click on openoffice.org3.0-debian-menus_3.0-9354_all.deb
When you double click that file, it will prompt you that you are going to install open office 3 and ask for your password when you accept the installation.

There is no reason to use terminal when installing most programs. But it is much easier and less text that goes into writing commands, because they are almost indipendant of the distro you are using, but every distro has different programs (almost same CLI, almost never same GUI)

THANKS 
I assumed the tarball had been downloaded.  I'm a ubuntu/linux newbe and was trying to help by telling him what worked for me.
I thank you for helping to clairify what I was trying to help him with.  It can be very frustrating trying to get a program or a set of packages installed.
Again thanks and I wish the original poster the best.
Tom

---

### Post by drakeman007 on 2008-10-20
> **thomas228 said:**
> Yes the last 2 terminal steps put them in gnome under office

cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

hope this helps
Tom


Thanks for you answer! Thats the answer im looking for! :lolflag:

---

### Post by thomas228 on 2008-10-20
> **drakeman007 said:**
> Thanks for you answer! Thats the answer im looking for! :lolflag:

You are more than welcome. 
.:guitar:

Again good luck with your ubuntu experiences.
Tom

---

### Post by g2bandrew on 2008-10-20
I don't have a DEBS folder inside the extracted folder. What do i do now?

---

### Post by thomas228 on 2008-10-20
> **g2bandrew said:**
> I don't have a DEBS folder inside the extracted folder. What do i do now?

Please doublecheck your tarball. It should be about 150,613 KB.
note that the name on the tarball is not the same as the extracted file you need to cd to.

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz 
cd OOO300_m9_native_packed-1_en-US.9358 
cd DEBS 
sudo dpkg -i *.deb 
cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

I hope that this helps a little. 
Tom

---

### Post by jmcgovern on 2008-10-20
Ok, followed all these instructions to the letter, cd'd into the right directory, ran sudo dpkg -i *.deb, ran sudo dpkg -i for the .deb in desktop-integration...and it stil comes out with three broken packages.   The three packages listed are

ooobasis3.0-binfilter
 openoffice.org3-draw
 openoffice.org3-en-us


I tried to open those .debs individually but they tell me they're missing a dependency.  it seems that the dependency is oobasis3.0-en-US but that package is already installed........

---

### Post by thomas228 on 2008-10-20
> **jmcgovern said:**
> Ok, followed all these instructions to the letter, cd'd into the right directory, ran sudo dpkg -i *.deb, ran sudo dpkg -i for the .deb in desktop-integration...and it stil comes out with three broken packages.   The three packages listed are

ooobasis3.0-binfilter
 openoffice.org3-draw
 openoffice.org3-en-us


I tried to open those .debs individually but they tell me they're missing a dependency.  it seems that the dependency is oobasis3.0-en-US but that package is already installed........


I ran into the same problem when I first tried to install 003
Error: Dependency is not
satisfiable: ooobasis3.0-en-US
for each of the following debs
ooobasis3.0-en-us-base_3.0.0-9_i386.deb
ooobasis3.0-en-us-binfilter_3.0.0-9_i386.deb
ooobasis3.0-en-us-calc_3.0.0-9_i386.deb
ooobasis3.0-en-us-draw_3.0.0-9_i386.deb
ooobasis3.0-en-us-help_3.0.0-9_i386.deb
ooobasis3.0-en-us-impress_3.0.0-9_i386.deb
ooobasis3.0-en-us-math_3.0.0-9_i386.deb
ooobasis3.0-en-us-res_3.0.0-9_i386.deb
ooobasis3.0-en-us-writer_3.0.0-9_i386.deb
what I finally had to do was start over by cleaning out all of openoffice as indicated in post # 3.
I later learned that I could clear out existing openoffice using the terminal command
sudo apt-get remove openoffice*.*

Try this and then copy and paste the following terminal commands one at a time. 

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz 
cd OOO300_m9_native_packed-1_en-US.9358 
cd DEBS 
sudo dpkg -i *.deb 
cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb


Let me know if that gets it done for you

Tom

---

### Post by jmcgovern on 2008-10-20
That seems to work...sorta.....OOo3 is now installed and running, but I still have 3 broken packages, which causes synaptic to not be able to update.  The three broken packages are the same as i reported earlier.  fixing the broken packages breaks OOo3 so that it won't start, so I appear o be going in a circle here...

---

### Post by thomas228 on 2008-10-20
> **jmcgovern said:**
> That seems to work...sorta.....OOo3 is now installed and running, but I still have 3 broken packages, which causes synaptic to not be able to update.  The three broken packages are the same as i reported earlier.  fixing the broken packages breaks OOo3 so that it won't start, so I appear o be going in a circle here...

I'm not sure whats going on with synaptic as I gave up using it for ubuntu 8.04 with openoffice.  Ubuntu is not supporting the openoffice 3 version for hardy and I don't think they plan on supporting Intrepid either. To me that means you should not be using synaptic for 003 as yet. you may have to just clean out openoffice as i did and using the tarball and terminal commands install 003 and not try to update them with synaptic at this time.  I found all 7 003 applications in application>office when I finshed the last terminal command.
If you are concerned about updating 00o3 you should have been given the option for updates in 00o3 when you first opened 003 and it gave you the option of registering (or not).
hope that clears it up a little for you.
Tom

---

### Post by issih on 2008-10-20
in order to try and give the OP what they wanted, although as a general rule wanting to install bang up to the minute stuff like OO3 is not always possible without resorting to terminal usage, in this case it might just be.

Go here:
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

download the linux deb version of release 3.0.0 in the language you want.

once that file is downloaded, find it, right click on it and select to extract the file. Now go into the extracted files and double click on the file with the extension ".deb".

With a bit of luck that should be all that is required as long as you don't run into any dependancy issues.

Hope that helps

---

### Post by thomas228 on 2008-10-20
> **issih said:**
> in order to try and give the OP what they wanted, although as a general rule wanting to install bang up to the minute stuff like OO3 is not always possible without resorting to terminal usage, in this case it might just be.

Go here:
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

download the linux deb version of release 3.0.0 in the language you want.

once that file is downloaded, find it, right click on it and select to extract the file. Now go into the extracted files and double click on the file with the extension ".deb".

With a bit of luck that should be all that is required as long as you don't run into any dependancy issues.

Hope that helps

With 00o3 you end up with 48 debs and I was unable to resolve a dependency problem with 9 debs as indicated in post #20. I found the terminal method worked for me. Thanks for putting the website location for the download.
Tom

---

### Post by issih on 2008-10-20
fair enough, if it comes as that many separate packages, you really are going to be stuck with using the terminal if you want to get it right away, unless some kind soul has set up a repository (although that always carries risks)

---

### Post by drakeman007 on 2008-10-20
I tried to install openoffice with the info given here and everything is ok, everything installed without problems!
Thanks...

---

### Post by jmcgovern on 2008-10-20
Then why am i Having so many problems? and to clarify the last post after mine, its not that im trying to install OOo3 via synaptic, its that,after i do install via dpkg, Synaptic quits working and wont function again until i fix broken packages which breaks OOo3.  Terminal method doesnt work, using the gui .deb installer doesnt work.  It always leaves me with 3 broken packages.  I guess ill stick with 2.4 after i reinstall it.  +1 for putting 3.0 in the backports for Hardy or Intrepid once this issue is fixed, unless its just me.

---

### Post by drakeman007 on 2008-10-20
> **jmcgovern said:**
> Then why am i Having so many problems? and to clarify the last post after mine, its not that im trying to install OOo3 via synaptic, its that,after i do install via dpkg, Synaptic quits working and wont function again until i fix broken packages which breaks OOo3.  Terminal method doesnt work, using the gui .deb installer doesnt work.  It always leaves me with 3 broken packages.  I guess ill stick with 2.4 after i reinstall it.  +1 for putting 3.0 in the backports for Hardy or Intrepid once this issue is fixed, unless its just me.


Hello, jmcgovern, you alread uninstall the 2.4 version that comes with 8.04lts? if you already have it uninstalled try to run this command in the terminal "sudo dpkg -l | grep openoffice" without the quotes and tell me how many files you get!
Regards!

---

### Post by jmcgovern on 2008-10-20
heres the output.  It appears some 2.4 packages are still installed, even though I thought i had purged everything....```
rc  openoffice.org-base                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - database
rc  openoffice.org-calc                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - spreadsheet
rc  openoffice.org-common                      1:2.4.1-1ubuntu2                                     OpenOffice.org office suite architecture ind
rc  openoffice.org-core                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite architecture dep
rc  openoffice.org-debian-menus                3.0-9354                                             OpenOffice.org desktop integration
rc  openoffice.org-draw                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - drawing
rc  openoffice.org-filter-binfilter            1:2.4.1-1ubuntu2                                     Legacy filters (e.g. StarOffice 5.2) for Ope
rc  openoffice.org-hyphenation                 0.3                                                  Hyphenation patterns for OpenOffice.org
rc  openoffice.org-hyphenation-en-us           2.3.1-2ubuntu1                                       US English hyphenation patterns for OpenOffi
rc  openoffice.org-impress                     1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - presentation
rc  openoffice.org-math                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - equation edito
rc  openoffice.org-thesaurus-en-au             2.1-3ubuntu1                                         Australian English Thesaurus for OpenOffice.
rc  openoffice.org-thesaurus-en-us             1:2.4.0~m240-1ubuntu1                                English Thesaurus for OpenOffice.org
rc  openoffice.org-writer                      1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - word processor

```

not sure how to remove these, if they are indeed installed (they do not show in synaptic)

---

### Post by drakeman007 on 2008-10-20
> **jmcgovern said:**
> heres the output.  It appears some 2.4 packages are still installed, even though I thought i had purged everything....```
rc  openoffice.org-base                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - database
rc  openoffice.org-calc                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - spreadsheet
rc  openoffice.org-common                      1:2.4.1-1ubuntu2                                     OpenOffice.org office suite architecture ind
rc  openoffice.org-core                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite architecture dep
rc  openoffice.org-debian-menus                3.0-9354                                             OpenOffice.org desktop integration
rc  openoffice.org-draw                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - drawing
rc  openoffice.org-filter-binfilter            1:2.4.1-1ubuntu2                                     Legacy filters (e.g. StarOffice 5.2) for Ope
rc  openoffice.org-hyphenation                 0.3                                                  Hyphenation patterns for OpenOffice.org
rc  openoffice.org-hyphenation-en-us           2.3.1-2ubuntu1                                       US English hyphenation patterns for OpenOffi
rc  openoffice.org-impress                     1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - presentation
rc  openoffice.org-math                        1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - equation edito
rc  openoffice.org-thesaurus-en-au             2.1-3ubuntu1                                         Australian English Thesaurus for OpenOffice.
rc  openoffice.org-thesaurus-en-us             1:2.4.0~m240-1ubuntu1                                English Thesaurus for OpenOffice.org
rc  openoffice.org-writer                      1:2.4.1-1ubuntu2                                     OpenOffice.org office suite - word processor

```

not sure how to remove these, if they are indeed installed (they do not show in synaptic)

Ok, that appear that you try to remove every package using sudo dpkg -r packagename ? right? well i start in this way too but i think you have to install all the office again from Applications/Add/REmove, add the packages again until you see
ii insted of rc in the list you get!! when you have this write me, the second step is to remove all the packages using sudo apt-get --purge remove openoffice*, this command is going to remove all the openoffice packages and dependences in the correct way.... that make sense? ok, tell me when you finish this part...

Regards!

---

### Post by thomas228 on 2008-10-20
Try
sudo apt-get remove openoffice*.* in the terminal and see if that helps
You may want to fix Synaptics first
rerun the pipe command to doublecheck that all openoffice has been removed then if it has rerun the terminal commands from post # 3

Hope that helps
Tom

---

### Post by drakeman007 on 2008-10-20
Im trying to explain in the way that worked for me! and this is my prove that my method works, well is not my method i got help from the great community here!
hehee

---

### Post by jmcgovern on 2008-10-20
here's the output of that command.  I fixed synaptic already
note the output is so long i had to redirect it to a file to get it all..
```
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting openoffice.org2-math for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-lt for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-nl for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-lv for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-nn for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-nr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ns for regex 'openoffice*.*'
Note, selecting openoffice.org-updatedicts for regex 'openoffice*.*'
Note, selecting dictionaries-common instead of openoffice.org-updatedicts
Note, selecting openoffice.org-l10n-pl for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-pt for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ro for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-tg for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sl for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-th for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ru for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-rw for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-tn for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ss for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ve for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-st for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-uk for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sv for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-tr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sw for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-vi for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ts for regex 'openoffice*.*'
Note, selecting mozilla-openoffice.org for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-xh for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-za for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-uz for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-zu for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-fr-fr for regex 'openoffice*.*'
Note, selecting myspell-fr-gut instead of openoffice.org-spellcheck-fr-fr
Note, selecting openoffice.org-qa-tools for regex 'openoffice*.*'
Note, selecting openoffice.org-filter-so52 for regex 'openoffice*.*'
Note, selecting openoffice.org-gnome for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org-core for regex 'openoffice*.*'
Note, selecting openoffice.org-writer for regex 'openoffice*.*'
Note, selecting openoffice.org-style-default for regex 'openoffice*.*'
Note, selecting openoffice.org3-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-af for regex 'openoffice*.*'
Note, selecting openoffice.org-impress for regex 'openoffice*.*'
Note, selecting openoffice.org-style-hicontrast for regex 'openoffice*.*'
Note, selecting openoffice.org-bin for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ca for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-bg for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-da for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ar for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-bn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-de for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-br for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-bs for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-fa for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-cs for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ga for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-el for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-fi for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-eo for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-cy for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-es for regex 'openoffice*.*'
Note, selecting openoffice.org-desktop-integration for regex 'openoffice*.*'
Note, selecting openoffice.org-debian-menus instead of openoffice.org-desktop-integration
Note, selecting openoffice.org2-l10n-he for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-et for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-eu for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-dz for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-gl for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-fr for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ja for regex 'openoffice*.*'
Note, selecting openoffice.org2-hunspell for regex 'openoffice*.*'
Note, selecting openoffice.org-dev for regex 'openoffice*.*'
Note, selecting openoffice.org3-draw for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ka for regex 'openoffice*.*'
Note, selecting openoffice.org-filter-mobiledev for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-hr for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-hu for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-it for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-km for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-kn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ko for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-nb for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ne for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-lo for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-mk for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ku for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-lt for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-nl for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-lv for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-nn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-nr for regex 'openoffice*.*'
Note, selecting openoffice.org-draw for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ns for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-pl for regex 'openoffice*.*'
Note, selecting openoffice.org-filter-binfilter for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-pt for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ro for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-gcj for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-tg for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sl for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-th for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ru for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sr for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-rw for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-tn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ss for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ve for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-st for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-uk for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sv for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-tr for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sw for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-vi for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ts for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-xh for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-uz for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-zu for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-fi for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-eo for regex 'openoffice*.*'
Note, selecting myspell-eo instead of openoffice.org-spellcheck-eo
Note, selecting libming-fonts-openoffice for regex 'openoffice*.*'
Note, selecting ming-fonts-opensymbol instead of libming-fonts-openoffice
Note, selecting openoffice.org-spellcheck-es for regex 'openoffice*.*'
Note, selecting myspell-es instead of openoffice.org-spellcheck-es
Note, selecting openoffice.org-spellcheck-fo for regex 'openoffice*.*'
Note, selecting myspell-fo instead of openoffice.org-spellcheck-fo
Note, selecting openoffice.org-spellcheck-et for regex 'openoffice*.*'
Note, selecting myspell-et instead of openoffice.org-spellcheck-et
Note, selecting openoffice.org-spellcheck-eu for regex 'openoffice*.*'
Note, selecting myspell-eu-es instead of openoffice.org-spellcheck-eu
Note, selecting openoffice.org-ogltrans for regex 'openoffice*.*'
Note, selecting openoffice.org-dtd-officedocument1.0 for regex 'openoffice*.*'
Note, selecting openoffice.org-java-common for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-nb for regex 'openoffice*.*'
Note, selecting myspell-nb instead of openoffice.org-spellcheck-nb
Note, selecting openoffice.org-ctl-he for regex 'openoffice*.*'
Note, selecting openoffice.org-gtk for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-lv for regex 'openoffice*.*'
Note, selecting myspell-lv instead of openoffice.org-spellcheck-lv
Note, selecting openoffice.org-spellcheck-nn for regex 'openoffice*.*'
Note, selecting myspell-nn instead of openoffice.org-spellcheck-nn
Note, selecting openoffice.org2-dev for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-nr for regex 'openoffice*.*'
Note, selecting myspell-nr instead of openoffice.org-spellcheck-nr
Note, selecting openoffice.org-spellcheck-ns for regex 'openoffice*.*'
Note, selecting myspell-ns instead of openoffice.org-spellcheck-ns
Note, selecting openoffice.org-kde for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-ru for regex 'openoffice*.*'
Note, selecting myspell-ru instead of openoffice.org-spellcheck-ru
Note, selecting openoffice.org-spellcheck-tn for regex 'openoffice*.*'
Note, selecting myspell-tn instead of openoffice.org-spellcheck-tn
Note, selecting openoffice.org-spellcheck-ss for regex 'openoffice*.*'
Note, selecting myspell-ss instead of openoffice.org-spellcheck-ss
Note, selecting openoffice.org-hyphenation-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-ve for regex 'openoffice*.*'
Note, selecting myspell-ve instead of openoffice.org-spellcheck-ve
Note, selecting openoffice.org-spellcheck-st for regex 'openoffice*.*'
Note, selecting myspell-st instead of openoffice.org-spellcheck-st
Note, selecting openoffice.org-hyphenation-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-xh for regex 'openoffice*.*'
Note, selecting myspell-xh instead of openoffice.org-spellcheck-xh
Note, selecting openoffice.org-spellcheck-uz for regex 'openoffice*.*'
Note, selecting hunspell-uz instead of openoffice.org-spellcheck-uz
Note, selecting openoffice.org-spellcheck-zu for regex 'openoffice*.*'
Note, selecting myspell-zu instead of openoffice.org-spellcheck-zu
Note, selecting openoffice.org-hunspell for regex 'openoffice*.*'
Note, selecting openoffice.org2-impress for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-af for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ca for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-bg for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-da for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-da
Note, selecting openoffice.org-hyphenation-ar for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-bn for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-de for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-br for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-bs for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-fa for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-cs
Note, selecting openoffice.org-hyphenation-ga for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-ga
Note, selecting openoffice.org-hyphenation-el for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-el
Note, selecting openoffice.org2 for regex 'openoffice*.*'
Note, selecting openoffice.org3 for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-fi for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-en for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-en
Note, selecting openoffice.org-hyphenation-eo for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-cy for regex 'openoffice*.*'
Note, selecting openoffice.org2-kde for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-es for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-es
Note, selecting openoffice.org-hyphenation-he for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-et for regex 'openoffice*.*'
Note, selecting myspell-et instead of openoffice.org-hyphenation-et
Note, selecting openoffice.org-hyphenation-eu for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-dz for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-gl for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-fr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-fr
Note, selecting openoffice.org-hyphenation-id for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-id
Note, selecting openoffice.org-hyphenation-ja for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ka for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-hr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-hu for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-is for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-is
Note, selecting openoffice.org-hyphenation-it for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-km for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-kn for regex 'openoffice*.*'
Note, selecting openoffice.org-style-industrial for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ko for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-nb for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ne for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-lo for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-mk for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ku for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-lt for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-nl for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-nl
Note, selecting openoffice.org-hyphenation-lv for regex 'openoffice*.*'
Note, selecting myspell-lv instead of openoffice.org-hyphenation-lv
Note, selecting openoffice.org-hyphenation-nn for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-gu-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-nr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ns for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-pl for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-hi-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-pt for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-pt
Note, selecting openoffice.org-hyphenation-ro for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-ro
Note, selecting openoffice.org-hyphenation-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-sk
Note, selecting openoffice.org-hyphenation-tg for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-sl for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-th for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ru for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-ru
Note, selecting openoffice.org-hyphenation-sr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-rw for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-tn for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ss for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ve for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-st for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-uk for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-uk
Note, selecting openoffice.org-hyphenation-sv for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-sv
Note, selecting openoffice.org-hyphenation-tr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-sw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.4 for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-vi for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ts for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-writer2latex for regex 'openoffice*.*'
Note, selecting openoffice.org2-writer for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-xh for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-uz for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-zu for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org-java for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-common for regex 'openoffice*.*'
Note, selecting openoffice.org2-base for regex 'openoffice*.*'
Note, selecting openoffice.org-ure for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-mimelnk for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org-style-human for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-sdbc-postgresql for regex 'openoffice*.*'
Note, selecting openoffice.org2-calc for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-hi-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ta-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-filter-so52 for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-hi-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org-1.9.125 for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-1.9.108 for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-1.9.114 for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-1.9.121 for regex 'openoffice*.*'
Note, selecting openoffice.org-bundled for regex 'openoffice*.*'
Note, selecting openoffice.org-gtk-gnome for regex 'openoffice*.*'
Note, selecting openoffice.org-help-hi-in for regex 'openoffice*.*'
Note, selecting openoffice.org-presentation-minimizer for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ta-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org3-math for regex 'openoffice*.*'
Note, selecting openoffice.org-help-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org-help-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org-evolution for regex 'openoffice*.*'
Note, selecting openoffice.org-math for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ta-in for regex 'openoffice*.*'
Note, selecting openofficeorg-desktop-integration for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-af for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ca for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-bg for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-da for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ar for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-bn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-de for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-de instead of openoffice.org2-thesaurus-de
Note, selecting openoffice.org2-thesaurus-br for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-bs for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-fa for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-cs instead of openoffice.org2-thesaurus-cs
Note, selecting openoffice.org2-java-common for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ga for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-el for regex 'openoffice*.*'
Note, selecting openoffice.org-common for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-fi for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-eo for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-cy for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-es for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-he for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-et for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-eu for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-dz for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-gl for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-fr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ja for regex 'openoffice*.*'
Note, selecting openoffice.org-dev-doc for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ka for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-hr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-hu for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-it for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-it instead of openoffice.org2-thesaurus-it
Note, selecting openoffice.org2-thesaurus-km for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-kn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ko for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-nb for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ne for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-lo for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-mk for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ku for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-lt for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-nl for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-lv for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-nn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-nr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ns for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-pl for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-pl instead of openoffice.org2-thesaurus-pl
Note, selecting openoffice.org2-core for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-pt for regex 'openoffice*.*'
Note, selecting openoffice.org2-evolution for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ro for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-sk instead of openoffice.org2-thesaurus-sk
Note, selecting openoffice.org2-thesaurus-tg for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sl for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-th for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ta-in for regex 'openoffice*.*'
Note, selecting openoffice.org for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ru for regex 'openoffice*.*'
Note, selecting openoffice.org3-writer for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-rw for regex 'openoffice*.*'
Note, selecting openoffice.org-debian-menus for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-tn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ss for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ve for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-st for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-uk for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sv for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-tr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sw for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-vi for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ts for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-xh for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-uz for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-zu for regex 'openoffice*.*'
Note, selecting openoffice.org-voikko for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-au for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-us instead of openoffice.org-thesaurus-en-gb
Note, selecting openoffice.org-hyphenation for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-draw for regex 'openoffice*.*'
Note, selecting openoffice.org-base-core for regex 'openoffice*.*'
Note, selecting openoffice.org-unbundled for regex 'openoffice*.*'
Note, selecting openoffice.org-debian-menus instead of openoffice.org-unbundled
Note, selecting openoffice.org-spellcheck-de-ch for regex 'openoffice*.*'
Note, selecting openoffice.org-style-andromeda for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-de-de for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-de-at for regex 'openoffice*.*'
Note, selecting openoffice.org-debian-files for regex 'openoffice*.*'
Note, selecting openoffice.org2-officebean for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org2-dev-doc for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-help-af for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ca for regex 'openoffice*.*'
Note, selecting openoffice.org-help-bg for regex 'openoffice*.*'
Note, selecting openoffice.org-help-da for regex 'openoffice*.*'
Note, selecting openoffice.org-report-builder for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ar for regex 'openoffice*.*'
Note, selecting openoffice.org-help-bn for regex 'openoffice*.*'
Note, selecting openoffice.org-help-de for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-2.4 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-br for regex 'openoffice*.*'
Note, selecting openoffice.org-help-bs for regex 'openoffice*.*'
Note, selecting openoffice.org-help-fa for regex 'openoffice*.*'
Note, selecting openoffice.org-help-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ga for regex 'openoffice*.*'
Note, selecting openoffice.org-help-el for regex 'openoffice*.*'
Note, selecting openoffice.org-help-fi for regex 'openoffice*.*'
Note, selecting openoffice.org-help-en for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-eo for regex 'openoffice*.*'
Note, selecting openoffice.org-help-cy for regex 'openoffice*.*'
Note, selecting openoffice.org-officebean for regex 'openoffice*.*'
Note, selecting openoffice.org-help-es for regex 'openoffice*.*'
Note, selecting openoffice.org-help-he for regex 'openoffice*.*'
Note, selecting openoffice.org-help-et for regex 'openoffice*.*'
Note, selecting openoffice.org-help-eu for regex 'openoffice*.*'
Note, selecting openoffice.org-help-dz for regex 'openoffice*.*'
Note, selecting openoffice.org-help-gl for regex 'openoffice*.*'
Note, selecting openoffice.org-help-fr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-gu-in for regex 'openoffice*.*'
Note, selecting openoffice.org-style-crystal for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ja for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ka for regex 'openoffice*.*'
Note, selecting openoffice.org-help-hr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org-help-hu for regex 'openoffice*.*'
Note, selecting openoffice.org-help-it for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.0.0 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.0.1 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.0.2 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-km for regex 'openoffice*.*'
Note, selecting openoffice.org-help-kn for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.0.3 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ko for regex 'openoffice*.*'
Note, selecting openoffice.org-help-nb for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ne for regex 'openoffice*.*'
Note, selecting openoffice.org-help-lo for regex 'openoffice*.*'
Note, selecting openoffice.org-help-mk for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ku for regex 'openoffice*.*'
Note, selecting openoffice.org-help-lt for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-lv for regex 'openoffice*.*'
Note, selecting openoffice.org-help-nl for regex 'openoffice*.*'
Note, selecting openoffice.org-help-nn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-us instead of openoffice.org2-thesaurus-en-us
Note, selecting openoffice.org2-l10n-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-nr for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ns for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org-help-pl for regex 'openoffice*.*'
Note, selecting openoffice.org-help-pt for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ro for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-help-tg for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sl for regex 'openoffice*.*'
Note, selecting openoffice.org-help-th for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ru for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sr for regex 'openoffice*.*'
Note, selecting openoffice.org-help-rw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-tn for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ss for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ve for regex 'openoffice*.*'
Note, selecting openoffice.org-help-st for regex 'openoffice*.*'
Note, selecting openoffice.org-help-uk for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sv for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-tr for regex 'openoffice*.*'
Note, selecting openoffice.org-help-vi for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ts for regex 'openoffice*.*'
Note, selecting openoffice.org-help-xh for regex 'openoffice*.*'
Note, selecting openoffice.org-help-uz for regex 'openoffice*.*'
Note, selecting openoffice.org-help-zu for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org2-common for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-crashrep for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-de-ch for regex 'openoffice*.*'
Note, selecting openoffice.org-style-tango for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-gu-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org3-base for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-gu-in for regex 'openoffice*.*'
Note, selecting openoffice.org-base for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org-help-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-hi-in for regex 'openoffice*.*'
Note, selecting openofficeorg-debian-menus for regex 'openoffice*.*'
Note, selecting openoffice.org3-calc for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-de for regex 'openoffice*.*'
Note, selecting openoffice.org-headless for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-gu-in for regex 'openoffice*.*'
Note, selecting openclipart-openoffice.org for regex 'openoffice*.*'
Note, selecting openoffice.org-calc for regex 'openoffice*.*'
Note, selecting openoffice.org-qa-api-tests for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-it for regex 'openoffice*.*'
Note, selecting openoffice.org3-dict-en for regex 'openoffice*.*'
Note, selecting openoffice.org3-dict-es for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-ne for regex 'openoffice*.*'
Note, selecting openoffice.org-help-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-help-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-pl for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-ru for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org-reportdesigner for regex 'openoffice*.*'
Note, selecting openoffice.org-qa-ui-tests for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org-starter-guide for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ta-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-af for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ca for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-bg for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-da for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ar for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-bn for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-de for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-br for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-bs for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-fa for regex 'openoffice*.*'
Note, selecting openoffice.org-help-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ga for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-el for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-en for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-gl-es for regex 'openoffice*.*'
Note, selecting myspell-gl-es instead of openoffice.org-spellcheck-gl-es
Note, selecting openoffice.org-l10n-fi for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-eo for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-cy for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-es for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-he for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-et for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-eu for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-dz for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-gl for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-fr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ja for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org2-gnome for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ka for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-hr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-hu for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-it for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-km for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-kn for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ko for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-nb for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ne for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-lo for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-mk for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ku for regex 'openoffice*.*'
E: Couldn't find package openoffice*.*

```

EDIT: Just had a thought...I have 2.4 on my Vista partition.  Could it be seeing that?  Doesnt seem likely but...

---

### Post by drakeman007 on 2008-10-20
> **jmcgovern said:**
> here's the output of that command.  I fixed synaptic already
note the output is so long i had to redirect it to a file to get it all..
```
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting openoffice.org2-math for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-lt for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-nl for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-lv for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-nn for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-nr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ns for regex 'openoffice*.*'
Note, selecting openoffice.org-updatedicts for regex 'openoffice*.*'
Note, selecting dictionaries-common instead of openoffice.org-updatedicts
Note, selecting openoffice.org-l10n-pl for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-pt for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ro for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-tg for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sl for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-th for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ru for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-rw for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-tn for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ss for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ve for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-st for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-uk for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sv for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-tr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-sw for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-vi for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ts for regex 'openoffice*.*'
Note, selecting mozilla-openoffice.org for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-xh for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-za for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-uz for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-zu for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-fr-fr for regex 'openoffice*.*'
Note, selecting myspell-fr-gut instead of openoffice.org-spellcheck-fr-fr
Note, selecting openoffice.org-qa-tools for regex 'openoffice*.*'
Note, selecting openoffice.org-filter-so52 for regex 'openoffice*.*'
Note, selecting openoffice.org-gnome for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org-core for regex 'openoffice*.*'
Note, selecting openoffice.org-writer for regex 'openoffice*.*'
Note, selecting openoffice.org-style-default for regex 'openoffice*.*'
Note, selecting openoffice.org3-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-af for regex 'openoffice*.*'
Note, selecting openoffice.org-impress for regex 'openoffice*.*'
Note, selecting openoffice.org-style-hicontrast for regex 'openoffice*.*'
Note, selecting openoffice.org-bin for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ca for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-bg for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-da for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ar for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-bn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-de for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-br for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-bs for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-fa for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-cs for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ga for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-el for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-fi for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-eo for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-cy for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-es for regex 'openoffice*.*'
Note, selecting openoffice.org-desktop-integration for regex 'openoffice*.*'
Note, selecting openoffice.org-debian-menus instead of openoffice.org-desktop-integration
Note, selecting openoffice.org2-l10n-he for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-et for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-eu for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-dz for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-gl for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-fr for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ja for regex 'openoffice*.*'
Note, selecting openoffice.org2-hunspell for regex 'openoffice*.*'
Note, selecting openoffice.org-dev for regex 'openoffice*.*'
Note, selecting openoffice.org3-draw for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ka for regex 'openoffice*.*'
Note, selecting openoffice.org-filter-mobiledev for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-hr for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-hu for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-it for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-km for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-kn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ko for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-nb for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ne for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-lo for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-mk for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ku for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-lt for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-nl for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-lv for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-nn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-nr for regex 'openoffice*.*'
Note, selecting openoffice.org-draw for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ns for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-pl for regex 'openoffice*.*'
Note, selecting openoffice.org-filter-binfilter for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-pt for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ro for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-gcj for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-tg for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sl for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-th for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ru for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sr for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-rw for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-tn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ss for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ve for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-st for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-uk for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sv for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-tr for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-sw for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-vi for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ts for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-xh for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-uz for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-zu for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-fi for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-eo for regex 'openoffice*.*'
Note, selecting myspell-eo instead of openoffice.org-spellcheck-eo
Note, selecting libming-fonts-openoffice for regex 'openoffice*.*'
Note, selecting ming-fonts-opensymbol instead of libming-fonts-openoffice
Note, selecting openoffice.org-spellcheck-es for regex 'openoffice*.*'
Note, selecting myspell-es instead of openoffice.org-spellcheck-es
Note, selecting openoffice.org-spellcheck-fo for regex 'openoffice*.*'
Note, selecting myspell-fo instead of openoffice.org-spellcheck-fo
Note, selecting openoffice.org-spellcheck-et for regex 'openoffice*.*'
Note, selecting myspell-et instead of openoffice.org-spellcheck-et
Note, selecting openoffice.org-spellcheck-eu for regex 'openoffice*.*'
Note, selecting myspell-eu-es instead of openoffice.org-spellcheck-eu
Note, selecting openoffice.org-ogltrans for regex 'openoffice*.*'
Note, selecting openoffice.org-dtd-officedocument1.0 for regex 'openoffice*.*'
Note, selecting openoffice.org-java-common for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-nb for regex 'openoffice*.*'
Note, selecting myspell-nb instead of openoffice.org-spellcheck-nb
Note, selecting openoffice.org-ctl-he for regex 'openoffice*.*'
Note, selecting openoffice.org-gtk for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-lv for regex 'openoffice*.*'
Note, selecting myspell-lv instead of openoffice.org-spellcheck-lv
Note, selecting openoffice.org-spellcheck-nn for regex 'openoffice*.*'
Note, selecting myspell-nn instead of openoffice.org-spellcheck-nn
Note, selecting openoffice.org2-dev for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-nr for regex 'openoffice*.*'
Note, selecting myspell-nr instead of openoffice.org-spellcheck-nr
Note, selecting openoffice.org-spellcheck-ns for regex 'openoffice*.*'
Note, selecting myspell-ns instead of openoffice.org-spellcheck-ns
Note, selecting openoffice.org-kde for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-ru for regex 'openoffice*.*'
Note, selecting myspell-ru instead of openoffice.org-spellcheck-ru
Note, selecting openoffice.org-spellcheck-tn for regex 'openoffice*.*'
Note, selecting myspell-tn instead of openoffice.org-spellcheck-tn
Note, selecting openoffice.org-spellcheck-ss for regex 'openoffice*.*'
Note, selecting myspell-ss instead of openoffice.org-spellcheck-ss
Note, selecting openoffice.org-hyphenation-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-ve for regex 'openoffice*.*'
Note, selecting myspell-ve instead of openoffice.org-spellcheck-ve
Note, selecting openoffice.org-spellcheck-st for regex 'openoffice*.*'
Note, selecting myspell-st instead of openoffice.org-spellcheck-st
Note, selecting openoffice.org-hyphenation-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-xh for regex 'openoffice*.*'
Note, selecting myspell-xh instead of openoffice.org-spellcheck-xh
Note, selecting openoffice.org-spellcheck-uz for regex 'openoffice*.*'
Note, selecting hunspell-uz instead of openoffice.org-spellcheck-uz
Note, selecting openoffice.org-spellcheck-zu for regex 'openoffice*.*'
Note, selecting myspell-zu instead of openoffice.org-spellcheck-zu
Note, selecting openoffice.org-hunspell for regex 'openoffice*.*'
Note, selecting openoffice.org2-impress for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-af for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ca for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-bg for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-da for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-da
Note, selecting openoffice.org-hyphenation-ar for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-bn for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-de for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-br for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-bs for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-fa for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-cs
Note, selecting openoffice.org-hyphenation-ga for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-ga
Note, selecting openoffice.org-hyphenation-el for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-el
Note, selecting openoffice.org2 for regex 'openoffice*.*'
Note, selecting openoffice.org3 for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-fi for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-en for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-en
Note, selecting openoffice.org-hyphenation-eo for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-cy for regex 'openoffice*.*'
Note, selecting openoffice.org2-kde for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-es for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-es
Note, selecting openoffice.org-hyphenation-he for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-et for regex 'openoffice*.*'
Note, selecting myspell-et instead of openoffice.org-hyphenation-et
Note, selecting openoffice.org-hyphenation-eu for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-dz for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-gl for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-fr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-fr
Note, selecting openoffice.org-hyphenation-id for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-id
Note, selecting openoffice.org-hyphenation-ja for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ka for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-hr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-hu for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-is for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-is
Note, selecting openoffice.org-hyphenation-it for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-km for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-kn for regex 'openoffice*.*'
Note, selecting openoffice.org-style-industrial for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ko for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-nb for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ne for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-lo for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-mk for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ku for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-lt for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-nl for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-nl
Note, selecting openoffice.org-hyphenation-lv for regex 'openoffice*.*'
Note, selecting myspell-lv instead of openoffice.org-hyphenation-lv
Note, selecting openoffice.org-hyphenation-nn for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-gu-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-nr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ns for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-pl for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-hi-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-pt for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-pt
Note, selecting openoffice.org-hyphenation-ro for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-ro
Note, selecting openoffice.org-hyphenation-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-sk
Note, selecting openoffice.org-hyphenation-tg for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-sl for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-th for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ru for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-ru
Note, selecting openoffice.org-hyphenation-sr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-rw for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-tn for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ss for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ve for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-st for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-uk for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-uk
Note, selecting openoffice.org-hyphenation-sv for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation instead of openoffice.org-hyphenation-sv
Note, selecting openoffice.org-hyphenation-tr for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-sw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.4 for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-vi for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ts for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-writer2latex for regex 'openoffice*.*'
Note, selecting openoffice.org2-writer for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-xh for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-uz for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-zu for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org-java for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-common for regex 'openoffice*.*'
Note, selecting openoffice.org2-base for regex 'openoffice*.*'
Note, selecting openoffice.org-ure for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-mimelnk for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org-style-human for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-sdbc-postgresql for regex 'openoffice*.*'
Note, selecting openoffice.org2-calc for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-hi-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ta-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-filter-so52 for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-hi-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org-1.9.125 for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-1.9.108 for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-1.9.114 for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-1.9.121 for regex 'openoffice*.*'
Note, selecting openoffice.org-bundled for regex 'openoffice*.*'
Note, selecting openoffice.org-gtk-gnome for regex 'openoffice*.*'
Note, selecting openoffice.org-help-hi-in for regex 'openoffice*.*'
Note, selecting openoffice.org-presentation-minimizer for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ta-in for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org3-math for regex 'openoffice*.*'
Note, selecting openoffice.org-help-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org-help-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org-evolution for regex 'openoffice*.*'
Note, selecting openoffice.org-math for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ta-in for regex 'openoffice*.*'
Note, selecting openofficeorg-desktop-integration for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-af for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ca for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-bg for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-da for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ar for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-bn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-de for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-de instead of openoffice.org2-thesaurus-de
Note, selecting openoffice.org2-thesaurus-br for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-bs for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-fa for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-cs instead of openoffice.org2-thesaurus-cs
Note, selecting openoffice.org2-java-common for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ga for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-el for regex 'openoffice*.*'
Note, selecting openoffice.org-common for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-fi for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-eo for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-cy for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-es for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-he for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-et for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-eu for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-dz for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-gl for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-fr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ja for regex 'openoffice*.*'
Note, selecting openoffice.org-dev-doc for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ka for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-hr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-hu for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-it for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-it instead of openoffice.org2-thesaurus-it
Note, selecting openoffice.org2-thesaurus-km for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-kn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ko for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-nb for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ne for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-lo for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-mk for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ku for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-lt for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-nl for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-lv for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-nn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-nr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ns for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-pl for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-pl instead of openoffice.org2-thesaurus-pl
Note, selecting openoffice.org2-core for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-pt for regex 'openoffice*.*'
Note, selecting openoffice.org2-evolution for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ro for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-sk instead of openoffice.org2-thesaurus-sk
Note, selecting openoffice.org2-thesaurus-tg for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sl for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-th for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ta-in for regex 'openoffice*.*'
Note, selecting openoffice.org for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ru for regex 'openoffice*.*'
Note, selecting openoffice.org3-writer for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-rw for regex 'openoffice*.*'
Note, selecting openoffice.org-debian-menus for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-tn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ss for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ve for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-st for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-uk for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sv for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-tr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-sw for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-vi for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ts for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-xh for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-uz for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-zu for regex 'openoffice*.*'
Note, selecting openoffice.org-voikko for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-au for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-us instead of openoffice.org-thesaurus-en-gb
Note, selecting openoffice.org-hyphenation for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-draw for regex 'openoffice*.*'
Note, selecting openoffice.org-base-core for regex 'openoffice*.*'
Note, selecting openoffice.org-unbundled for regex 'openoffice*.*'
Note, selecting openoffice.org-debian-menus instead of openoffice.org-unbundled
Note, selecting openoffice.org-spellcheck-de-ch for regex 'openoffice*.*'
Note, selecting openoffice.org-style-andromeda for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-de-de for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-de-at for regex 'openoffice*.*'
Note, selecting openoffice.org-debian-files for regex 'openoffice*.*'
Note, selecting openoffice.org2-officebean for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org2-dev-doc for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-help-af for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ca for regex 'openoffice*.*'
Note, selecting openoffice.org-help-bg for regex 'openoffice*.*'
Note, selecting openoffice.org-help-da for regex 'openoffice*.*'
Note, selecting openoffice.org-report-builder for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ar for regex 'openoffice*.*'
Note, selecting openoffice.org-help-bn for regex 'openoffice*.*'
Note, selecting openoffice.org-help-de for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-2.4 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-br for regex 'openoffice*.*'
Note, selecting openoffice.org-help-bs for regex 'openoffice*.*'
Note, selecting openoffice.org-help-fa for regex 'openoffice*.*'
Note, selecting openoffice.org-help-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ga for regex 'openoffice*.*'
Note, selecting openoffice.org-help-el for regex 'openoffice*.*'
Note, selecting openoffice.org-help-fi for regex 'openoffice*.*'
Note, selecting openoffice.org-help-en for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-eo for regex 'openoffice*.*'
Note, selecting openoffice.org-help-cy for regex 'openoffice*.*'
Note, selecting openoffice.org-officebean for regex 'openoffice*.*'
Note, selecting openoffice.org-help-es for regex 'openoffice*.*'
Note, selecting openoffice.org-help-he for regex 'openoffice*.*'
Note, selecting openoffice.org-help-et for regex 'openoffice*.*'
Note, selecting openoffice.org-help-eu for regex 'openoffice*.*'
Note, selecting openoffice.org-help-dz for regex 'openoffice*.*'
Note, selecting openoffice.org-help-gl for regex 'openoffice*.*'
Note, selecting openoffice.org-help-fr for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-gu-in for regex 'openoffice*.*'
Note, selecting openoffice.org-style-crystal for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ja for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ka for regex 'openoffice*.*'
Note, selecting openoffice.org-help-hr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org-help-hu for regex 'openoffice*.*'
Note, selecting openoffice.org-help-it for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.0.0 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.0.1 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.0.2 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-km for regex 'openoffice*.*'
Note, selecting openoffice.org-help-kn for regex 'openoffice*.*'
Note, selecting openoffice.org-help-2.0.3 for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ko for regex 'openoffice*.*'
Note, selecting openoffice.org-help-nb for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ne for regex 'openoffice*.*'
Note, selecting openoffice.org-help-lo for regex 'openoffice*.*'
Note, selecting openoffice.org-help-mk for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ku for regex 'openoffice*.*'
Note, selecting openoffice.org-help-lt for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-lv for regex 'openoffice*.*'
Note, selecting openoffice.org-help-nl for regex 'openoffice*.*'
Note, selecting openoffice.org-help-nn for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-en-us instead of openoffice.org2-thesaurus-en-us
Note, selecting openoffice.org2-l10n-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-nr for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ns for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org-help-pl for regex 'openoffice*.*'
Note, selecting openoffice.org-help-pt for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ro for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-help-tg for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sl for regex 'openoffice*.*'
Note, selecting openoffice.org-help-th for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ru for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sr for regex 'openoffice*.*'
Note, selecting openoffice.org-help-rw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-tn for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ss for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ve for regex 'openoffice*.*'
Note, selecting openoffice.org-help-st for regex 'openoffice*.*'
Note, selecting openoffice.org-help-uk for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sv for regex 'openoffice*.*'
Note, selecting openoffice.org-help-sw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-tr for regex 'openoffice*.*'
Note, selecting openoffice.org-help-vi for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ts for regex 'openoffice*.*'
Note, selecting openoffice.org-help-xh for regex 'openoffice*.*'
Note, selecting openoffice.org-help-uz for regex 'openoffice*.*'
Note, selecting openoffice.org-help-zu for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-zh-cn for regex 'openoffice*.*'
Note, selecting openoffice.org2-common for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-pa-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-crashrep for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-de-ch for regex 'openoffice*.*'
Note, selecting openoffice.org-style-tango for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-gu-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-zh-tw for regex 'openoffice*.*'
Note, selecting openoffice.org-help-te-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-be-by for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org3-base for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-gu-in for regex 'openoffice*.*'
Note, selecting openoffice.org-base for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org-help-en-gb for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-hi-in for regex 'openoffice*.*'
Note, selecting openofficeorg-debian-menus for regex 'openoffice*.*'
Note, selecting openoffice.org3-calc for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-de for regex 'openoffice*.*'
Note, selecting openoffice.org-headless for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-help-ur-in for regex 'openoffice*.*'
Note, selecting openoffice.org-help-gu-in for regex 'openoffice*.*'
Note, selecting openclipart-openoffice.org for regex 'openoffice*.*'
Note, selecting openoffice.org-calc for regex 'openoffice*.*'
Note, selecting openoffice.org-qa-api-tests for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-pt-br for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-mr-in for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-it for regex 'openoffice*.*'
Note, selecting openoffice.org3-dict-en for regex 'openoffice*.*'
Note, selecting openoffice.org3-dict-es for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-ne for regex 'openoffice*.*'
Note, selecting openoffice.org-help-en-us for regex 'openoffice*.*'
Note, selecting openoffice.org-help-en-za for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-pl for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-or-in for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-sk for regex 'openoffice*.*'
Note, selecting openoffice.org-thesaurus-ru for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org-reportdesigner for regex 'openoffice*.*'
Note, selecting openoffice.org-qa-ui-tests for regex 'openoffice*.*'
Note, selecting openoffice.org2-l10n-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org2-thesaurus-ml-in for regex 'openoffice*.*'
Note, selecting openoffice.org-starter-guide for regex 'openoffice*.*'
Note, selecting openoffice.org-hyphenation-ta-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-af for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ca for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-bg for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-da for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ar for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-bn for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-de for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-br for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-bs for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-fa for regex 'openoffice*.*'
Note, selecting openoffice.org-help-as-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-cs for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ga for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-el for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-en for regex 'openoffice*.*'
Note, selecting openoffice.org-spellcheck-gl-es for regex 'openoffice*.*'
Note, selecting myspell-gl-es instead of openoffice.org-spellcheck-gl-es
Note, selecting openoffice.org-l10n-fi for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-eo for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-cy for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-es for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-he for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-et for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-eu for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-dz for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-gl for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-fr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ja for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ti-er for regex 'openoffice*.*'
Note, selecting openoffice.org2-gnome for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ka for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-hr for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-in for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-hu for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-it for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-km for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-kn for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ko for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-nb for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ne for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-lo for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-mk for regex 'openoffice*.*'
Note, selecting openoffice.org-l10n-ku for regex 'openoffice*.*'
E: Couldn't find package openoffice*.*

```

But you already install your 2.4 version again? using the add/remove programs?
the last line you get is that? E:couldn find package openoffice? you put the command using --purge?

Regars

---

### Post by drakeman007 on 2008-10-20
Remember you have to reinstall your office 2.4 again until when you run this command sudo dpkg -l |g grep oppenoffice, you have to see all the installed packages and with the ii in every beginning of line, in your last msg with this command you have RC instead.....

---

### Post by thomas228 on 2008-10-20
Looks like Drakeman007 has a handle on this so I'll bow out for the night.

Keep up the good work everyone and have a good night

Tom

Just read your post #35 Why do you have to reinstall 2.4??
seems to me I had to remove all of 2.4 to install 00o3

Nite
Tom

---

### Post by drakeman007 on 2008-10-20
> **thomas228 said:**
> Looks like Drakeman007 has a handle on this so I'll bow out for the night.

Keep up the good work everyone and have a good night

Tom

Hello tom, well i just trying to explain the way that work for me, i have problems installing it too but in this forums i get the answers with you heheh and other person here, im a totally newbie i just trying to help in the way the people help me! i dont know if the things im saying are right but thats the way it works for me, i bet that you know the os much more than me, i just have like 3 days with linux and ubuntu!!!
Thanks for your help tom, in all my post you help me too hehe...
good night!

---

### Post by thomas228 on 2008-10-20
jmcgovern
Read your edit in post #33 and I have a vista/ubuntu dual boot system with 00o3 installed on both OS. I dont think that is your problem.
When you'r sure you've removed 2.4 try the four terminal commands in post # 3 and see if it installs correctly.
Hope it does
Nite
Tom

---

### Post by drakeman007 on 2008-10-20
I suggest to reinstall again only because that is the method that works for me i have to reinstall openoffice again because when i tried to uninstall i damage something that didnt let me uninstall openoffice correctly, but when i reinstall openoffice again and then remove everything works ok! But you can try both and see what is the solution for you! but definitly the thomas228 post are tottaly right and thats the way to install it too!

---

### Post by jmcgovern on 2008-10-21
Ok this is truly weird.  I did a complete removal, using the --purge switch, and the pipe command still comes up with what i posted earlier.  I even deleted couple hidden folders in my home directory that were openoffice related, and it still comes up.  As of how it is now, no trace of ANY version of OOo should be on this partition, and yet the pipe command shows there is.

---

### Post by fr.theo on 2008-10-21
try this site it worked for me, just follow the instructions.


[http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/](http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/)

---

### Post by fr.theo on 2008-10-21
or try this post:
[http://ubuntuforums.org/showthread.php?t=953065](http://ubuntuforums.org/showthread.php?t=953065)

---

### Post by drakeman007 on 2008-10-21
> **jmcgovern said:**
> Ok this is truly weird.  I did a complete removal, using the --purge switch, and the pipe command still comes up with what i posted earlier.  I even deleted couple hidden folders in my home directory that were openoffice related, and it still comes up.  As of how it is now, no trace of ANY version of OOo should be on this partition, and yet the pipe command shows there is.

Ok, you tell me that when  you run this sudo dpkg -l | grep openoffice, you still see the list with openoffice files? and showing the 2.4 version? before you make the remove you install the openoffice again in the add / remove programs?

Regards

---

### Post by jmcgovern on 2008-10-21
> **drakeman007 said:**
> Ok, you tell me that when  you run this sudo dpkg -l | grep openoffice, you still see the list with openoffice files? and showing the 2.4 version? before you make the remove you install the openoffice again in the add / remove programs?

Regards

Thats exactly what im saying, and when I do the install, step by step, exactly as several people have posted, it always comes up with the same three broken packages.  I've uninstalled and reinstalled both 2.4 and 3.0 about three times each.  currently its back to as it was before i attempted all this, with 2.4 installed (or it least it will be after synaptic finishes.

---

### Post by drakeman007 on 2008-10-21
What are the three broken packages? from openoffice 2.4 or 3.0?

---

### Post by jmcgovern on 2008-10-21
> **drakeman007 said:**
> What are the three broken packages? from openoffice 2.4 or 3.0?

ooobasis3.0-binfilter
openoffice.org3-draw
openoffice.org3-en-us

---

### Post by drakeman007 on 2008-10-21
> **jmcgovern said:**
> ooobasis3.0-binfilter
openoffice.org3-draw
openoffice.org3-en-us

All are from a bad openoffice 3 installation, mmm, you try to remove it, with something like 
```
sudo apt-get --purge remove openoffice.org3*
or
sudo dpkg -r ooobasis3.0-binfilter 

```

you cannot install the new because this three broken packages, you alredy tried to remove it?

---

### Post by jmcgovern on 2008-10-21
> **drakeman007 said:**
> All are from a bad openoffice 3 installation, mmm, you try to remove it, with something like 
```
sudo apt-get --purge remove openoffice.org3*
or
sudo dpkg -r ooobasis3.0-binfilter 

```

you cannot install the new because this three broken packages, you alredy tried to remove it?


Right, and if i do remove it , the whole installation breaks. on top of that, when i ussue sudo apt-get --purge remove openoffice.org3* i get 

E: Couldn't find package openoffice.org3_3.0.0-9_i386.deb

---

### Post by thomas228 on 2008-10-21
> **jmcgovern said:**
> Right, and if i do remove it , the whole installation breaks. on top of that, when i ussue sudo apt-get --purge remove openoffice.org3* i get 

E: Couldn't find package openoffice.org3_3.0.0-9_i386.deb

I'm not sure but you may want to follow up on 
[http://ubuntuforums.org/showthread.php?p=6006042#post6006042](http://ubuntuforums.org/showthread.php?p=6006042#post6006042)

Just a thought. 

Tom
Post #43 above has some info worth looking at too.

---

### Post by HsSrvnt on 2008-10-21
I looked all over the internet and tried many different ways to get Openoffice 3.0 to install properly.  I didn't find anyone that had the same problem I was having.  After playing around for 3 days I finally found the solution.  I am posting it here for those of you that are having problems, in hopes that this may be your solution as well.

I found it easier to use the "Terminal" program under Applications
Please follow all steps taking note of upper/lower casings.

Uninstall the old Openoffice programs by typing:
sudo apt-get remove openoffice*.*

I FIRST had already extracted "OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz" onto my desktop

Installing the New Openoffice program
cd /home/administrator/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i openoffice.org3.0-debian-menus_3.0_9354_all.deb

This installed everything onto my system, including the menus.

Hope this helps you all.[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by brunolabs on 2008-10-21
Will this new version of OOo be available in the repos? Or will it be possible to be automatically updated through the update manager?

---

### Post by drakeman007 on 2008-10-21
> **brunolabs said:**
> Will this new version of OOo be available in the repos? Or will it be possible to be automatically updated through the update manager?

I dont think so, i dont know if its going to be available in backports, but you can download directly from openoffice.org site, and the new version comes with ubuntu 8.10 that release in 9 days...

regards!

---

### Post by thomas228 on 2008-10-21
> **brunolabs said:**
> Will this new version of OOo be available in the repos? Or will it be possible to be automatically updated through the update manager?

If you are able to install 00o3 with no errors you'll find that 00o3 has an option for auto updates independent of the update manager. Just be sure to uninstall 2.4 first. Thats what worked for me. See post #3 of this thread.

Good luck
Tom

---

### Post by desicratn on 2008-10-22
> **thomas228 said:**
> 
I later learned that I could clear out existing openoffice using the terminal command
sudo apt-get remove openoffice*.*

Try this and then copy and paste the following terminal commands one at a time. 

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz 
cd OOO300_m9_native_packed-1_en-US.9358 
cd DEBS 
sudo dpkg -i *.deb 
cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb


Let me know if that gets it done for you




This worked flawlessly for me. 
Thankyou

---

### Post by brunolabs on 2008-10-26
Is there a way to unistall OOo 2.4 exclusively with the GUI (without terminal commands)?

---

### Post by Zularan on 2008-10-26
There are OpenOffice 3 Repositories available to allow install/updates by just using Synaptic/Update.

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)
Shows Hardy (8.04) and Intrepid (8.10) repos, you have to add these to your /etc/apt/sources.list either manually or by using Synaptic.

I use Intrepid so I have
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main #Open Office 3
```
Substitute intrepid for hardy if your using that.

AFAIK ooo3 won't be included officially in Ubuntu for a couple of months, perhaps the next release after Interpid as the developers haven't been able to test it thoroughly. 

Hope this helps.

---

### Post by thomas228 on 2008-10-26
> **Zularan said:**
> There are OpenOffice 3 Repositories available to allow install/updates by just using Synaptic/Update.

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)
Shows Hardy (8.04) and Intrepid (8.10) repos, you have to add these to your /etc/apt/sources.list either manually or by using Synaptic.

I use Intrepid so I have
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main #Open Office 3
```
Substitute intrepid for hardy if your using that.

AFAIK ooo3 won't be included officially in Ubuntu for a couple of months, perhaps the next release after Interpid as the developers haven't been able to test it thoroughly. 

Hope this helps.

Your method looks good (I havent tried it as I havent upgraded to 8.10 yet and I installed 00o3 as per post #3). 

In answer to brunolabs question the first half of post # 3 shows the step by step Synaptic method for removal of 2.4.

Good work 
Tom

---

### Post by lenwood on 2008-10-26
I was able to install OO without difficulty, but the desktop integration didn't work for me. I don't mind updating the application menu manually, but where can I find the images (icons) that go with each application?

Thanks,
Chris

---

### Post by Jo21 on 2008-12-03
bump i need help 

i try installing using the deb.

but it i can't open the apps,

not one, only printers setup

each time i try to open any open office crash it crash.

doesn't include any info just crash.

i am ubuntu 8.10

---

### Post by stevebond001 on 2008-12-04
Hi
I also had problems upgrading from OpenOffice 2.4 to 3.0.

I eventually solved it as per the link below **(post #9)**

[http://ubuntuforums.org/showthread.php?t=947388](http://ubuntuforums.org/showthread.php?t=947388) 

This essentially allowed me to completely remove OpenOffice 2.4 and install 3.0 (and add all icons into the "Applications > Office" Menu.

this worked perfectly for me - hope it helps.

---

### Post by gjoellee on 2008-12-04
you can add this repo: ```
*deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main*
```
 
or
 
you can download the DEB folder of OOo3 to your Desktop
now extract it the file
open the terminal:
```
cd Desktop
```
```
cd Open*
```
```
cd DEBS
```
```
sudo dpkg -i *.deb
```
```
cd d*
```
```
sudo dpkg -i *.deb
```

---

### Post by fferreira on 2008-12-05
> **gjoellee said:**
> you can add this repo: ```
*deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main*
```
 
or
 
you can download the DEB folder of OOo3 to your Desktop
now extract it the file
open the terminal:
```
cd Desktop
```
```
cd Open*
```
```
cd DEBS
```
```
sudo dpkg -i *.deb
```
```
cd d*
```
```
sudo dpkg -i *.deb
```

I had installed OOffice3 packages previously in my computer. But I had to reinstall Ubuntu and now I am no longer able to upgrade OOffice to the newest version. I added the address to my repo and then apt-get update... Nothing is happening... Why???

---

### Post by Skripka on 2008-12-05
> **fferreira said:**
> I had installed OOffice3 packages previously in my computer. But I had to reinstall Ubuntu and now I am no longer able to upgrade OOffice to the newest version. I added the address to my repo and then apt-get update... Nothing is happening... Why???

There PPAs are still down, and have been for a week and a half.


The only way to get OOo3 for *buntu is to download the big deb archive and install that away.

---

### Post by kuberprok on 2008-12-07
Thank you for the explanation (post #3) however, I did it as mentioned in your post and it installed the Menus (albeit it a successful terminal output) but for the life of me, I can not get it to display under Applications>office.

I went through the whole removal of 2.4 but to no avail.

Using 3.0 on my other ubuntu box - Hardy with no problems.

Just another note, after my fresh install of 8.10,  Office 2.4 on this install did not show any text under any of the task bars i.e. File> View> etc. it only showed them when you move your mouse at a speed over them.

Any assistance appreciated.

---

### Post by thomas228 on 2008-12-08
> **kuberprok said:**
> Thank you for the explanation (post #3) however, I did it as mentioned in your post and it installed the Menus (albeit it a successful terminal output) but for the life of me, I can not get it to display under Applications>office.

I went through the whole removal of 2.4 but to no avail.

Using 3.0 on my other ubuntu box - Hardy with no problems.

Just another note, after my fresh install of 8.10,  Office 2.4 on this install did not show any text under any of the task bars i.e. File> View> etc. it only showed them when you move your mouse at a speed over them.

Any assistance appreciated.

A few questions
Did you remove 2.4 before you installed 00o3?
 If not you may have to remove both 2.4 and 00o3 before reinstalling.

I assume you downloaded the tar.gz file from Sun

To make things a litle more convenient I'm going to paste my 00o3 instructions including the download link. Hope this helps.

Download from
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US) 

Remove existing openoffice 2.4 by doing the following

Selected "System > Administration > Synaptic Package Manager" and entered my password

In the package manager select the "Search" button and type "openoffice" in Search and select the Search button which gave me all of the openoffice packages.

Go thru all of the installed openoffice packages and marked them with the "Mark for Complete Removal"
including "Mark" additional required changes.

Next selecte the "Apply" button and confirm in the summary by selecting the "Apply" button

In terminal you can remove ver 2.4 with
sudo apt-get remove openoffice*.* 

If you have already installed Openoffice 00o3 and need to remove it before reinstalling here is a rather long termianal command (just cut and paste)

sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure


When this is finished open a terminal and do the following

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz 
cd OOO300_m9_native_packed-1_en-US.9358 
cd DEBS 
sudo dpkg -i *.deb 
cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb
 
You should have all 7 options in Applications>Office

Most of the instructions above are a repeat of post #3 with snipits from several other posts.

Hope it helps:)

Tom

---

### Post by kuberprok on 2008-12-09
Thank you Stevebond001, I'll give it a go!

---

### Post by kuberprok on 2008-12-09
Thomas228,

Thank you. 

I suspect with my 1 try I might have negeleted to remove 2.4 completely. I might have marked it just for removal and not complete removal.

I'll take your advice and see what the result is!

Cheers,

---

### Post by hobo89 on 2008-12-09
OpenOffice 3 is now back in the repositories (typical after I installed from source last night). So to install:

Remove 2.4:
```
sudo apt-get remove $(dpkg -l |grep ^ii|grep openoffice|cut -f3 -d' ')
```

Add the repository:
System > Administration > Synaptic Package Manage > Settings > Repositories > Third Party Software > Add > "deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu" (copy and paste without quotes into the "APT line" box)
Click Close, message box will come up saying something about needing to reload packages, close the message box and click Reload in the top left corner of Synaptic.

Install:
Type in the Quick search box "openoffice", you should now see "openoffice.org" in the list with Latest Version "1:3.0.0-6ubuntu0intrepid1", select the checkbox and "Mark for Installation" It will list other changes it needs to make, such as installing other packages. Click Apply at the top, and confirm any message boxes that pop up and leave it to do it's thing.

You should now have OpenOffice.org 3.0 installed. If, in the menu, clicking the launchers does not work, log out and log back in again and it should be fine.

Hope this helps

---

### Post by acreech on 2008-12-09
When I went to upgrade to OpenOffice 3.0 there was a warning message. 

"Warning
You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system."

What do you make of this Warning? I have not installed it yet.

---

### Post by hobo89 on 2008-12-09
> **acreech said:**
> When I went to upgrade to OpenOffice 3.0 there was a warning message. 

"Warning
You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system."

What do you make of this Warning? I have not installed it yet.

I did also get that message, but I OKd it and carried on as normal. I assume it's because it is being installed from a third party repository and not Ubuntu's own. If there were real dangers I would have thought someone would have mentioned it before now, as it is from the same repository source as before.

---

### Post by acreech on 2008-12-09
> **hobo89 said:**
> I did also get that message, but I OKd it and carried on as normal. I assume it's because it is being installed from a third party repository and not Ubuntu's own. If there were real dangers I would have thought someone would have mentioned it before now, as it is from the same repository source as before.

That was my thought too. So I just installed it. I sure hope I didn't screw something up. But I think it probably has to do with being in the third party repos.

---

### Post by calc on 2008-12-12
> **acreech said:**
> When I went to upgrade to OpenOffice 3.0 there was a warning message. 

"Warning
You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system."

What do you make of this Warning? I have not installed it yet.

I believe this happens because the PPAs are not cryptographically signed repositories, the regular Ubuntu repositories are signed.

What you should do when you see messages like this is go through the list and verify what is going to be installed. If it looks like packages you actually want to be updated, in this case the OOo packages, then approving the install is ok. If it looks like it is replacing other packages, a hypothetical rogue ppa, then you may want to cancel at the point it brings up the message.

---

### Post by timzak on 2008-12-12
I followed this howto from Tombuntu and it worked perfectly:

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by rlunger on 2008-12-12
> **g2bandrew said:**
> I can't figure it out. I don't want to go into terminal and type in some complicated codes just to install a program, i just want it to install. So how do i install it normally (as in using some sort of GUI).

The easiest way is to get into a terminal and type:

sudo apt-get install openoffice.org 

then answer yes to the download.

Next time you go to your apps menu, it should be there.

---

### Post by pjalegria on 2008-12-13
Do i need to clean OpenOffice2 files from Synaptic after upgrade to Openoffice3???

Thanks

---

### Post by rlunger on 2008-12-13
> **pjalegria said:**
> Do i need to clean OpenOffice2 files from Synaptic after upgrade to Openoffice3???

Thanks

I think you are supposed to remove any earlier version of OO you have before installing the new one.  Use 'sudo apt-get remove openoffice.org' is you do have a previous version installed.  Or try 'sudo apt-get autoremove' to remove all unnecessary packages.  Other than that, it should install fine with 'apt-get'.

Hope that helps.

---

### Post by pjalegria on 2008-12-13
I have installed openoffice3 by repository, i think i do not need to remove first openoffice2...

---

### Post by Desert Sailor on 2008-12-13
> **rlunger said:**
> The easiest way is to get into a terminal and type:

sudo apt-get install openoffice.org 

then answer yes to the download.

Next time you go to your apps menu, it should be there.


OK...did that, and I downloaded a lot of files, things clicked and whirred, but in the end, NO open office 3. on my menu.  However, I did NOT removed version 2.4, is that the problem do you think?  I believe I have OO 3 on my machine, but I don't know how to start it and get it on the menu.

---

### Post by HsSrvnt on 2008-12-16
> **Desert Sailor said:**
> OK...did that, and I downloaded a lot of files, things clicked and whirred, but in the end, NO open office 3. on my menu.  However, I did NOT removed version 2.4, is that the problem do you think?  I believe I have OO 3 on my machine, but I don't know how to start it and get it on the menu.

Yes you have to uninstall OO 2.4 first.  Then try reinstalling OO 3.  If you have problems, use the Terminal and try Post #50.  It's what worked for me.

---

### Post by dimeotane on 2008-12-17
I got it installed using the repositories (see below)  the deb files on the OO.org website did not work for me.

I'm using Hardy and I tried installing from the .deb file on the OOO website.  It did not work when I tried following the online guides.  First of all I had dependency problems that no one else seemed to have:  
inside the directory OOO300_m9_native_packed-1_en-US.9358/ was missing these two debs:
ooobasis3.0-ooofonts_3.0.0-9_i386.deb
openoffice.org-ure_1.4.0-9_i386.deb
they were both listed as a dependencies so I went surfing around online to download them separately.  After installing them and everything else, Openoffice gave me some "ISO" error and wouldn't load so I uninstalled everything again.    A frustrating waste of time in trying to upgrade to version 3 that way.  

So I tried another method:  adding to my repositories:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

and then looked in synaptic for OO 3 base package to install.

It installed perfectly this way and actually ran.

---

### Post by starcannon on 2008-12-17
Read post #82 before even considering my post. 

Just download the .deb file from OOo here:
[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

double click the package when download is complete, put in password, enjoy.

---

### Post by thomas228 on 2008-12-17
> **starcannon said:**
> Just download the .deb file from OOo here:
[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

double click the package when download is complete, put in password, enjoy.

Hi

If you download from sun DO NOT DOUBLE CLICK or you will get a number of dependency errors. (There are around 30+ .debs in the DEB dir )

Please read post # 65 and follow the terminal method laid out.

Post #65 is a combination of post #3 and a few others.

The repository method for installing oo03 should also work now as it has been fixed. edit: post #68 and/or post #84

Good luck.

Tom

---

### Post by starcannon on 2008-12-17
> **thomas228 said:**
> Hi

If you download from sun DO NOT DOUBLE CLICK or you will get a number of dependency errors. (There are around 30+ .debs in the DEB dir )

Please read post # 65 and follow the terminal method laid out.

Post #65 is a combination of post #3 and a few others.

The repository method for installing oo03 should also work now as it has been fixed.

Good luck.

Tom
Thanks for the heads up Tom, I didn't have issues myself, but if there are possible landmines I'd hate to be the cause.

---

### Post by fooman on 2008-12-17
try this:

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

---

### Post by mistypotato on 2009-05-29
This worked perfect 4 me...THANkS!
Intrepid 8.10

> **gjoellee said:**
> you can add this repo: ```
*deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main*
```
 
or
 
you can download the DEB folder of OOo3 to your Desktop
now extract it the file
open the terminal:
```
cd Desktop
```
```
cd Open*
```
```
cd DEBS
```
```
sudo dpkg -i *.deb
```
```
cd d*
```
```
sudo dpkg -i *.deb
```

---

### Post by SunnyRabbiera on 2009-05-29
This is why I use PPA repos.

---

### Post by Johan-Steyn on 2009-05-29
Hi All,

For hassle-free updating of Open Office 2.4 to 3.0 check out this website (Interpid 8.10): [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml).

or 

(9.04 Jaunty) [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

Just update the Software Sources with the PPA from the OpenOffice.org Scribblers.

Also add the save the key and import it to Software Sources Authentication tab.

Just run Update to, uhm well, update 2.4 to 3.0. or 3.1

Works like a charm.

Regards,

JS

---

### Post by dgermann on 2009-06-01
Hi--

My keyboard shortcuts are all messed up, now that I have upgraded from 3.0 to 3.1 using this ppa method.

Have tried also downloading the debs from the OOo site and installing using dpkg -i, but that will not even load for me--it crashes over and over.

Using 8.04.1 hardy.

Examples: Ctrl-Home does nothing. Shift-home and Shift-end do nothing. Until I fixed it, Backspace did nothing.

Anybody else experiencing this? Have the same thing on three machines.
I hope somebody has a fix!

---

### Post by Steelmourne on 2009-06-01
No terminal. 

news.**softpedia**.com/news/How-to-**Install**-**OpenOffice**-org-3-1-on-Ubuntu-9-04-111105.shtml

---

