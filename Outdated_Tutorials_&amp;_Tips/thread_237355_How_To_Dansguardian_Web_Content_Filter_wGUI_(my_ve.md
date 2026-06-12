---
title: "How To: Dansguardian Web Content Filter w/GUI (my version)"
date: 2006-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by mhancoc7 on 2006-08-16
There are now two flavors of the dansguardian w/gui scripts. One for Dapper and one for Edgy. You can download them from their respective download pages using the link below. 

[www.mirror.christianubuntu.com]("http://www.mirror.christianubuntu.com")

Thanks, Jereme

***The info below is only for historical purposes.*** 

> I have built a script to install Dansguardian web content filtering with a GUI that allows you to easily edit the filter settings. This is a modified script that I use for the building of Ubuntu Christian Edition as well as in the scripts to "convert" to Ubuntu Christian Edition. I figured there are probably some people who do not want Ubuntu Christian Edition, but do want Dansguardian web content filtering with a GUI.

First let me thank those who inspired and guided this script through their work and posts.

nanomad: [http://www.ubuntuforums.org/showthread.php?t=226298&highlight=dansguardian+gui](http://www.ubuntuforums.org/showthread.php?t=226298&highlight=dansguardian+gui)
tonhou:[ http://www.ubuntuforums.org/showthread.php?t=207008&highlight=setup+dansguardian]("http://www.ubuntuforums.org/showthread.php?t=207008&highlight=setup+dansguardian")

[B]Instructions:

Packages Installed:[/B]
Dansguardian Web Content Filtering (dansguardian, tinyproxy, clamav, firehol)
Graphical tool to easily change the Dansguardian filter settings (gambas, libqt3-mt)

**How to run the script:**
1. Download the attached script archive to your Home directory.
2. Right click on the archive and select Extract Here.
3. Open a terminal window (Applications > Accessories > Terminal).
4. Type the following then hit Enter:
cd /home/YOURUSERNAME/install_dansguardian_gui
5. Type the following then hit Enter:
sudo ./install_me
6. Type your password then hit Enter.

Once you have finished running the script **_immediately reboot your computer_**. Dansguardian _**WILL NOT**_ function correctly until after you reboot. Your original sources.list file will be restored when the script is finished.

*Note: This is a powerful script. It will be making changes to your system and should be **USED AT YOUR OWN RISK!!**

**Note: This script has only been tested on a fresh install of Ubuntu 6.06 Dapper. Results may vary with other flavors of Ubuntu or different configurations.

***Note: You may want to make backup copies of the following files:
/etc/apt/sources.list

****Note: You may see a few errors during the script regarding dansguardian and clamav. These should be ignored. Once you reboot your computer these configuration issues will be resolved.

*****Note: This script is somewhat disposable. If you need to run the script a second time you will need to extract it from the original archive.

After you reboot you will have Dansguardian web content filtering working in all browsers. You can modify the filter settings using the GUI. The GUI is located at System > Administration > Configure Parental Controls. After making any changes be sure to save the file in gedit and click "Save & Exit" on the GUI.

I hope you all enjoy. 

Jereme

---

### Post by tonhou on 2006-08-16
Thanks Jereme.

It seems to install very well. Incidentally I have successfully set it up on Xubuntu and everything works fine (adds menu entries also).

Well done!

--Tony

---

### Post by mhancoc7 on 2006-08-16
> **tonhou said:**
> Thanks Jereme.

It seems to install very well. Incidentally I have successfully set it up on Xubuntu and everything works fine (adds menu entries also).

Well done!

--Tony

Thanks Tony,
I am glad that it is working. I always test a lot before I release something, but I always worry. I hope you enjoy.
Jereme

---

### Post by tonhou on 2006-08-17
Further to above comment about the script installing successfully:

Xubuntu : also requires that gedit be installed to enable the gui to work for changing the filters.

Kubuntu : everything installs and works fine but note these:
1. At install there are many error messages that are not critical.
2. For functioning of the filter changing gui then you must again install gedit which pulls in a number of gnome libraries (approx 7Mb download) and must also install gksu which is needed for password entry.

Edubuntu : have yet to try the script here but don't expect there to be any problems.

--Tony

---

### Post by mhancoc7 on 2006-08-18
> **tonhou said:**
> Further to above comment about the script installing successfully:

Xubuntu : also requires that gedit be installed to enable the gui to work for changing the filters.

Kubuntu : everything installs and works fine but note these:
1. At install there are many error messages that are not critical.
2. For functioning of the filter changing gui then you must again install gedit which pulls in a number of gnome libraries (approx 7Mb download) and must also install gksu which is needed for password entry.

Edubuntu : have yet to try the script here but don't expect there to be any problems.

--Tony

Thanks for posting your results. I built the script for the default Ubuntu. It is nice to see what happens in the other flavors.
Jereme

---

### Post by Mithrilhall on 2006-08-18
Ok...I just installed this on Kubuntu (Dapper).

Here is my setup.

Router <-----> Kubuntu (Dansguardian) <----> Switch <----> Computers


I can no longer pull an IP from the router through my Kubuntu box. I have bridged my eth0 & eth1 and it was working fine before running the script.

Is there anything I need to adjust? :confused:

---

### Post by Mithrilhall on 2006-08-18
A little more information.


My router is giving out IP addresses on a 10.2.176.0/24 network. I want to allow all computers on my network out to the internet (filtered of course). ;)

---

### Post by mhancoc7 on 2006-08-18
> **Mithrilhall said:**
> Ok...I just installed this on Kubuntu (Dapper).

Here is my setup.

Router <-----> Kubuntu (Dansguardian) <----> Switch <----> Computers


I can no longer pull an IP from the router through my Kubuntu box. I have bridged my eth0 & eth1 and it was working fine before running the script.

Is there anything I need to adjust? :confused:

> **Mithrilhall said:**
> A little more information.


My router is giving out IP addresses on a 10.2.176.0/24 network. I want to allow all computers on my network out to the internet (filtered of course). ;)

Sorry, but I am not sure. The script was intended to be used on Ubuntu. Hopefully someone here with a little more knowledge can help you get this sorted out. Please keep me updated. 

Jereme

---

### Post by tonhou on 2006-08-19
Briefly, this script is for setting up dansguardian on a single desktop system - you seem to be wanting a setup to serve a number of systems which will be quite a different arrangement.

--Tony

---

### Post by Mithrilhall on 2006-08-20
Well...I'm sure it's a problem with Firhol. Once turned off it I can pull and IP address through my Kubuntu server. I just need to figure out what needs to be changed in the firewall.

---

### Post by PacShady on 2006-08-23
Is there a way to set up Dansguardian to use a web interface?

One of my previous threads asked about personal filtering software (I use SafeEyes for my Windows partition) but so far I haven't found a good program for Linux that suits my needs. A web filter for a Christian-based Linux distro should at least be modified for use by a single person to filter for THEMSELF, having someone else (in my case, someone outside my palce of residence) as administrator for accountability purposes. For this to work, I need to be able to set up the program to use a web interface to make changes to config files.

Do you know if this is possible?

'Shady

---

### Post by mhancoc7 on 2006-08-23
> **PacShady said:**
> Is there a way to set up Dansguardian to use a web interface?

One of my previous threads asked about personal filtering software (I use SafeEyes for my Windows partition) but so far I haven't found a good program for Linux that suits my needs. A web filter for a Christian-based Linux distro should at least be modified for use by a single person to filter for THEMSELF, having someone else (in my case, someone outside my palce of residence) as administrator for accountability purposes. For this to work, I need to be able to set up the program to use a web interface to make changes to config files.

Do you know if this is possible?

'Shady

That is actually a great idea. I am not sure if it is possible, but thanks for mentioning it.

Dansguardian is very powerful and there may be a way to set that up. There site has a lot of info on configuring the settings. You might want to check there as well. dansguardian.org

Jereme

---

### Post by PacShady on 2006-08-23
Also, might be a good idea to discourage Kubuntu users to install this script. Ran it, it installed everything, added the extra packages mentioned by Tonhou, and tested it in Firefox. Seemed to be filtering, but much too strongly (all Google searches were blocked). Tried to change the settings, after a reinstall (for some reason the script failed to copy the GUI properly the first time round) and the from that point my connection to the internet was severed. Only just got back on after an hour of playing with settings and removal of Dansguardian, and for some reason my profile for Firefox was destroyed and I had to recover from backups. I'm assuming it's because I'm using Kubuntu (I hate Gnome, always preferred KDE well and truly over it), so yeah might be good to warn those using a distro other than plain vanilla Ubuntu to be wary of installing this script for the time being.

In the meantime, I'm seriously considering installing regular Ubuntu (or your Christian Ubuntu version perhaps) and just downloading KDE on top of it. Kubuntu just doesn't seem to carry the same level of support as Ubuntu (there again, KDE always seems to be regected in favour of Gnome anyway, so that's probably why).

'Shady

---

### Post by honda on 2006-08-24
The install went fine and filtering works. But it seems as excluding users from the filtering does not work. Is it because it is set up as a transparent proxy? It says that 'basic proxy authentication' must be enabled, and without knowing much about the subject I came to the conclusion that it can't be used with a transparent proxy. So, how can I exclude users from filtering?

---

### Post by mhancoc7 on 2006-08-24
> **honda said:**
> The install went fine and filtering works. But it seems as excluding users from the filtering does not work. Is it because it is set up as a transparent proxy? It says that 'basic proxy authentication' must be enabled, and without knowing much about the subject I came to the conclusion that it can't be used with a transparent proxy. So, how can I exclude users from filtering?

Yeah, I am still trying to figure that one out too. I haven't had time to dig into the dansguardian/tinyproxy documentation to see how to do it. 

Jereme

---

### Post by Vector Calculus on 2006-08-24
I liked your dansguardian script/install. 

To allow other users to bypass filtering, you will have to install someform of "identd" (eg. oidentd, pidentd, etc) for user authentication. Weird thing, i can't seem to find them. Have they been removed from apt-get?

There is info in the link (scroll up for more info on other systems):
[Identd and dansguardian]("http://contentfilter.futuragts.com/wiki/index.php?title=Using_IDENT_for_User_Identification#Enabling_ident_in_DansGuardian")

Hopefully this makes some sense.

Peace.

---

### Post by mhancoc7 on 2006-08-24
> **Vector Calculus said:**
> I liked your dansguardian script/install. 

To allow other users to bypass filtering, you will have to install someform of "identd" (eg. oidentd, pidentd, etc) for user authentication. Weird thing, i can't seem to find them. Have they been removed from apt-get?

There is info in the link (scroll up for more info on other systems):
[Identd and dansguardian]("http://contentfilter.futuragts.com/wiki/index.php?title=Using_IDENT_for_User_Identification#Enabling_ident_in_DansGuardian")

Hopefully this makes some sense.

Peace.

I am not sure, but thank you for bringing to my attention. I will look into it.
Thanks, Jereme

---

### Post by jbeiter on 2006-08-24
Thank you VERY MUCH for this! thankyouthankyouthankyou!

---

### Post by calvinthomas on 2006-08-28
Excellent, really good! Thankyou very much, I don't know if this is relevant but it is working perfectly for me in an XGL session.

A question: Is it possible to allow certain website extensions? Like i'd like to allow all .edu and all .ac.uk sites? Can I do this?

A tip: Putting education into the allowed phrases list makes accessing things like sex education etc accessible and from a basic internet search doesn't allow any unwanted things through.

Calv

---

### Post by mhancoc7 on 2006-08-28
> **calvinthomas said:**
> Excellent, really good! Thankyou very much, I don't know if this is relevant but it is working perfectly for me in an XGL session.

A question: Is it possible to allow certain website extensions? Like i'd like to allow all .edu and all .ac.uk sites? Can I do this?

A tip: Putting education into the allowed phrases list makes accessing things like sex education etc accessible and from a basic internet search doesn't allow any unwanted things through.

Calv

I am glad to hear you that it is working for you. I am not sure about allow certain web extensions. You may want to check at the Dansguardian site ([www.dansguardian.org)](www.dansguardian.org)). Let me know what you find.
Jereme

---

### Post by calvinthomas on 2006-08-28
Ok after editing things, i've messed it up and its not filtering at all any more! I tryed reinstalling the script but that hasn't helped, is there any way to completely remove this so I can reinstall it from scratch? The problem I think is this, from a terminal:

calvin@calvin-laptop:~$ dansguardian
Error opening /etc/dansguardian/dansguardian.conf

Help much appreciated!

Calv

---

### Post by mhancoc7 on 2006-08-28
> **calvinthomas said:**
> Ok after editing things, i've messed it up and its not filtering at all any more! I tryed reinstalling the script but that hasn't helped, is there any way to completely remove this so I can reinstall it from scratch? The problem I think is this, from a terminal:

calvin@calvin-laptop:~$ dansguardian
Error opening /etc/dansguardian/dansguardian.conf

Help much appreciated!

Calv

Well, you can go to Synaptic and "Completely Remove" dansguardian, tinyproxy, firehol, clamav. That should uninstall it. Then you can run the script again. Be sure that you use a fresh copy of the script. I mean delete the folder and extract it fresh from the archive. That should get everything back up and running. Don't forget to reboot after you run the script. Keep me posted.
Jereme

---

### Post by honda on 2006-08-28
Using ident on linux seems to be more of a hack than a solution: "For Unix systems where only a single user will be logged in at a time, you can use oidentd and set it up to return a user-specified string of "USERID : <OS> : <USERNAME>" where <USERNAME> is taken from an environment variable in a startup script. This isn't fool-proof, nor perfect, but it works." 

In my case however I'm not trying to build a filter that can't be cheaten, it's just that I'd like to set up somewhat ridicoulusly tight filters for the 3-6 years old kids and still allow the rest of the family to be able to use the internet. So I just disabled the iptables rule that blocks direct connection to the proxy on port 3128, and configured firefox to use the proxy directly to bypass the filter.

---

### Post by calvinthomas on 2006-08-28
Thanks Jereme, that worked great, all is back working again! After disabling the downloading restrictions i'm very happy!

Calv

---

### Post by Marsolin on 2006-08-28
Thanks for working on this. I have a young kid who will be using computers before long so I really appreciate making content filtering easier to use.

I'm going to add a link to this thread from the [DansGuardian]("http://linuxappfinder.com/package/dansguardian") entry on [Linux App Finder]("http://linuxappfinder.com/").

---

### Post by mhancoc7 on 2006-08-28
> **calvinthomas said:**
> Thanks Jereme, that worked great, all is back working again! After disabling the downloading restrictions i'm very happy!

Calv

Great! I am glad we got it going again. :)

> **Marsolin said:**
> Thanks for working on this. I have a young kid who will be using computers before long so I really appreciate making content filtering easier to use.

I'm going to add a link to this thread from the [DansGuardian]("http://linuxappfinder.com/package/dansguardian") entry on [Linux App Finder]("http://linuxappfinder.com/").

Thanks for the links.

Jereme

---

### Post by carney1979 on 2006-08-31
Another script in these forums killed my internet connection. But this one worked perfectly on my stand-alone desktop.

Thanks!

David

---

### Post by calvinthomas on 2006-09-21
Is there any way to temporarily disable the whole filtering software rather than editing each bit individually?

Calv

---

### Post by mhancoc7 on 2006-09-21
> **calvinthomas said:**
> Is there any way to temporarily disable the whole filtering software rather than editing each bit individually?

Calv

Here is a thread that discusses this.
[http://www.ubuntuforums.org/showthread.php?t=261966](http://www.ubuntuforums.org/showthread.php?t=261966)

Be aware that some of the techniques are untested and not supported.

Hope that helps, Jereme

---

### Post by mrhealthpatriot on 2006-09-22
I tried to adjust DansGuardian in Ubuntu 6.0.6 (gnome) using "System - Administration - Configure Parental Controls" but nothing happens when I click on the icon. Dansguardian is installed. How do I adjust it?

---

### Post by mhancoc7 on 2006-09-22
> **mrhealthpatriot said:**
> I tried to adjust DansGuardian in Ubuntu 6.0.6 (gnome) using "System - Administration - Configure Parental Controls" but nothing happens when I click on the icon. Dansguardian is installed. How do I adjust it?

The dansguardian GUI was built with Gambas so you will need the gambas runtime files. Open a terminal and run the following commands.

    apt-get install gambas-runtime
    apt-get install gambas-gb-qt

Once you have these installed the GUI should be functioning. Just let me know if you still have problems.

Jereme

---

### Post by mhancoc7 on 2006-09-26
I have added this script to the Ubuntu CE project. The original post is only for historical purposes. If you would like to add Web Content Filtering powered by Dansguardian with GUI please visit this link.

[http://www.whatwouldjesusdownload.co...ring-only.html]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html")

Thanks, Jereme

---

### Post by A-star on 2006-09-29
is there any way to just use the gui for dansguardian?
I'm installing dansguardian and squid so I only need the gui and not the installation script.

---

### Post by mhancoc7 on 2006-09-29
> **A-star said:**
> is there any way to just use the gui for dansguardian?
I'm installing dansguardian and squid so I only need the gui and not the installation script.

If you would like I can throw together a little script to only install the GUI. Just PM me and I will get to work on it.
Thanks, Jereme

---

### Post by Nopposan on 2006-12-11
I appreciate your work, Mhancoc, but I think I'm going to go with the manual install.  I've Got Xubuntu Edgy Eft, and I tried your script; 'seems like something it did interrupted my access via symbolic links to my cdrom and I'm having trouble getting streaming audio to play as well.

---

### Post by mhancoc7 on 2006-12-11
> **Nopposan said:**
> I appreciate your work, Mhancoc, but I think I'm going to go with the manual install.  I've Got Xubuntu Edgy Eft, and I tried your script; 'seems like something it did interrupted my access via symbolic links to my cdrom and I'm having trouble getting streaming audio to play as well.

Sorry for your trouble. All of the scripts were built for the default Ubuntu. None have been tested on (X,K,Ed)Ubuntu.

Thanks,  Jereme

---

### Post by bodhi.zazen on 2006-12-13
Nice How-to

This thread has been added to the UDSF wiki.

[Dansguardian](http://doc.gwos.org/index.php/Dansguardian)

---

### Post by mhancoc7 on 2006-12-13
> **bodhi.zazen said:**
> Nice How-to

This thread has been added to the UDSF wiki.

[Dansguardian]("http://doc.gwos.org/index.php/Dansguardian")

Awesome thanks!

I wanted to point out a few things that need to be changed a bit.

I noticed that the sidebar notes that the script works with "[SIZE=-1]Breezy 5.10". Their are currently two scripts, one for Dapper and one for Edgy. So [/SIZE][SIZE=-1]Breezy 5.10 is not supported.

I also noticed that the sidebar notes that the script works on "[/SIZE][SIZE=-1](U,K,X)buntu". The scripts only work with Ubuntu. You can use them on Kubuntu and Xubuntu, but you would need to install gedit, gksudo, zenity, and possibly others that I may be forgetting. So only Ubuntu is supported.

I noticed that there isn't a link to the page to download the scripts. The link is [http://www.mirror.christianubuntu.com](http://www.mirror.christianubuntu.com). This will take you to a page to select the Edgy or Dapper version. 

The code, "[/SIZE][SIZE=-1]cd /home/YOURUSERNAME/install_dansguardian_gui", would need to be adjusted since there are now two scripts (Edgy, Dapper). 

The note "[/SIZE]Note: This script is somewhat disposable. If you need to run the script a second time you will need to extract it from the original archive.", no longer applies to the latest releases of the scripts.

Also the scripts now make dated backup copies of the sources.list file.

Let me know if you have any questions.

Thanks, Jereme


[SIZE=-1]

[/SIZE]

---

### Post by Nopposan on 2006-12-13
Actually, it turns out my problem with the cdrom may not have anything to do with your script.  Sorry for misplacing blame; after  I reinstalled Xubuntu, I still have the problem with not being able to access the cdrom.

Still, the caution about installing on Xubuntu should remain, I guess.  'Would be good to have the gui though.  'Need something like this that will work on slow machines with low memory.

Thanks again.

---

### Post by bodhi.zazen on 2006-12-13
Edit: My mistake :(

---

### Post by azwxman on 2006-12-27
Jereme,

No help needed, I just had a laugh...I'm already running DG and tried to download your "GUI-only" option.  

I say "try" because DG blocked the .gz file as a banned extension.

Worth a smile anyway.

Mark

---

### Post by whiten on 2007-01-03
Many thanks - worked well for me on Edgy.

---

### Post by whiten on 2007-01-03
I have also installed on my amd64 acer alptop and although it works the gui does not - anybody with any ideas?

I have manually edited the files, but this isn't ideal.

Many thanks.

you can either post here or email me on nick dot white at btinternet dot com

---

### Post by mhancoc7 on 2007-01-13
> **whiten said:**
> I have also installed on my amd64 acer alptop and although it works the gui does not - anybody with any ideas?

I have manually edited the files, but this isn't ideal.

Many thanks.

you can either post here or email me on nick dot white at btinternet dot com

 Did you use the script on Kubuntu or Xubuntu? If so you will need to install zenity, gksu, and gedit for the GUI to work.  Thanks, Jereme

---

### Post by Josh1 on 2007-01-17
Where is the download? Can't find it on the site.

---

### Post by mhancoc7 on 2007-01-17
> **Josh1 said:**
> Where is the download? Can't find it on the site.

Just go to the [download page]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html") and choose Dapper or Edgy. Then scroll down and you should see it.

Jereme

---

### Post by noobsyd on 2007-04-18
> **mhancoc7 said:**
> There are now two flavors of the dansguardian w/gui scripts. One for Dapper and one for Edgy. You can download them from their respective download pages using the link below. 

[www.mirror.christianubuntu.com]("http://www.mirror.christianubuntu.com")

Thanks, Jereme

***The info below is only for historical purposes.***

Hi Jereme - many thanks for the great work!

Will this script also work for Feisty Fawn? 

Also - I presume FireStarter cannot be installed for this script to work as I installed the script with FireStarter and had problems getting it to work. Is enough to 'sudo apt-get remove firestarter' prior to running the script, or do i need to modify any other configs (iptables?)? Or does the script only work with a clean install of Feisty Fawn?

Many thanks again,

Prad

---

### Post by mhancoc7 on 2007-04-18
Thanks very much for your kind words. 

I will be releasing a version for Feisty once Ubuntu CE v3.0 (Feisty) comes out.

I am not sure about firestarter. Probably just removing it will do.

Thanks, Jereme

---

### Post by noobsyd on 2007-04-18
Thanks again Jereme,

I actually tried to install on Feisty using the CE script by - 

- run the Edgy script in Feisty to install DG, 
- reboot, and
- update /etc/apt/sources.list and update && upgrade

However this didn't work, even after I removed Firestarter.

Does the script configure DG for 'young child' filtering 'out of the box'? Or does it need further configuring after install is completed?

I have gone to Feisty for a production system and am very keen on getting the filtering up and running for my family's sake...:)

Many thanks again - and if your answer is that I should wait for the Ubuntu CE v3.0 (Feisty) script then that is OK:)

Prad

---

### Post by mhancoc7 on 2007-04-18
> **noobsyd said:**
> Thanks again Jereme,

I actually tried to install on Feisty using the CE script by - 

- run the Edgy script in Feisty to install DG, 
- reboot, and
- update /etc/apt/sources.list and update && upgrade

However this didn't work, even after I removed Firestarter.

Does the script configure DG for 'young child' filtering 'out of the box'? Or does it need further configuring after install is completed?

I have gone to Feisty for a production system and am very keen on getting the filtering up and running for my family's sake...:)

Many thanks again - and if your answer is that I should wait for the Ubuntu CE v3.0 (Feisty) script then that is OK:)

Prad


Thanks for letting me know how it went.

Yes, it is probably best to wait for the script for Ubuntu CE v3.0. It should be coming out fairly soon.

Yes, the DG configuration is set for "young children" by default. 

Thanks, Jereme

---

### Post by tjoel99 on 2007-06-10
Jereme, 

I tried to follow your instructions, but they didn't work for me.  Here are the results.  I typed my password even though none shows up below.

family@c1:~$ cd /home/family/install_dansguardian_gui
bash: cd: /home/family/install_dansguardian_gui: No such file or directory
family@c1:~$ sudo ./install_me
Password:
sudo: ./install_me: command not found
family@c1:~$ 

Why didn't it work?  Thank you.

tjoel99

---

### Post by mhancoc7 on 2007-06-10
> **tjoel99 said:**
> Jereme, 

I tried to follow your instructions, but they didn't work for me.  Here are the results.  I typed my password even though none shows up below.

family@c1:~$ cd /home/family/install_dansguardian_gui
bash: cd: /home/family/install_dansguardian_gui: No such file or directory
family@c1:~$ sudo ./install_me
Password:
sudo: ./install_me: command not found
family@c1:~$ 

Why didn't it work?  Thank you.

tjoel99

Did you download the latest script from here?

[http://www.mirror.christianubuntu.com](http://www.mirror.christianubuntu.com)

If not give that a try.

Jereme

---

### Post by darundal on 2007-06-10
Can I set up different permissions for different accounts with dansguardian, or no? Say, let account A download compressed files, and don't let account B do that?

---

### Post by mhancoc7 on 2007-06-10
> **darundal said:**
> Can I set up different permissions for different accounts with dansguardian, or no? Say, let account A download compressed files, and don't let account B do that?

I believe that it is possible with dansguardian. However, the script that I have put together is not setup for it.
Jereme

---

### Post by merlin114 on 2007-06-28
Hi, I've just switched to Dapper from WinXP and have been trying to get Dansguardian working for days.  I've read zillions of how-to's and I've installed DG 2.8.0.6, TinyProxy 1.6.3.3, and firehol 1.231-4 per the instructions from one of the threads.  I also edited dansguardian.conf and tinyproxy.conf as instructed. After reboot, I have no indication that dg is working at all, and I'm not getting any content filtering in Firefox or Epiphany.  I found one other thread that suggested typing "sudo dpkg-reconfigure dansguardian", so I did that and got the following error:

Stopping DansGuardian: dansguardian.
Starting DansGuardian: Error reading file:
Error reading file:
Error opening exceptionvirussitelist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration fil es
/etc/init.d/dansguardian: line 33:  7304 Segmentation fault      start-stop-daem on --start --quiet --pidfile /var/run/$NAME.pid --exec $DAEMON
invoke-rc.d: initscript dansguardian, action "start" failed.

I'm new to Linux and don't understand most of the instructions I'm trying to follow.  I've also looked for the dansguardian_install_gui which is mentioned in the threads and is supposed to make this easier, but all I find at the christianubuntu link is the gui for Feisty -- it seems like they removed the downloads for dapper and edgy.  I'm beginning to think it would be easier to just install ubuntuCE-Feisty, but it took me so long to get things set up to see my other hard drive (NTFS) and get some 3rd party commercial software installed, I'm afraid to start over with a new load.  Can anyone help me get DG working on Dapper?  Please?!

---

### Post by mhancoc7 on 2007-06-28
> **merlin114 said:**
> Hi, I've just switched to Dapper from WinXP and have been trying to get Dansguardian working for days.  I've read zillions of how-to's and I've installed DG 2.8.0.6, TinyProxy 1.6.3.3, and firehol 1.231-4 per the instructions from one of the threads.  I also edited dansguardian.conf and tinyproxy.conf as instructed. After reboot, I have no indication that dg is working at all, and I'm not getting any content filtering in Firefox or Epiphany.  I found one other thread that suggested typing "sudo dpkg-reconfigure dansguardian", so I did that and got the following error:

Stopping DansGuardian: dansguardian.
Starting DansGuardian: Error reading file:
Error reading file:
Error opening exceptionvirussitelist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration fil es
/etc/init.d/dansguardian: line 33:  7304 Segmentation fault      start-stop-daem on --start --quiet --pidfile /var/run/$NAME.pid --exec $DAEMON
invoke-rc.d: initscript dansguardian, action "start" failed.

I'm new to Linux and don't understand most of the instructions I'm trying to follow.  I've also looked for the dansguardian_install_gui which is mentioned in the threads and is supposed to make this easier, but all I find at the christianubuntu link is the gui for Feisty -- it seems like they removed the downloads for dapper and edgy.  I'm beginning to think it would be easier to just install ubuntuCE-Feisty, but it took me so long to get things set up to see my other hard drive (NTFS) and get some 3rd party commercial software installed, I'm afraid to start over with a new load.  Can anyone help me get DG working on Dapper?  Please?!

You can get previous versions here.
[http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/previous/](http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/previous/)

Thanks, Jereme

---

### Post by merlin114 on 2007-06-29
Jereme, thank you SOOOOOOOOOOOO MUCH!  I couldn't find that for the life of me before.  Now it took me about 2 minutes to overcome days of frustration.  That little program is WONDERFUL. 

 I think I agree with an article I read that indicated the Linux community's biggest shortcoming in getting people to bail on MS Windows is simply that despite the wealth of information on Linux, it seems to be hard for us newcomers to find the real basic info as we try to get our feet wet.  That gui, and things like it that make converting easier for us newbies are absolutely KEY.  Thanks for pointing me in the right direction!!!!

---

### Post by mhancoc7 on 2007-06-30
> **merlin114 said:**
> Jereme, thank you SOOOOOOOOOOOO MUCH!  I couldn't find that for the life of me before.  Now it took me about 2 minutes to overcome days of frustration.  That little program is WONDERFUL. 

 I think I agree with an article I read that indicated the Linux community's biggest shortcoming in getting people to bail on MS Windows is simply that despite the wealth of information on Linux, it seems to be hard for us newcomers to find the real basic info as we try to get our feet wet.  That gui, and things like it that make converting easier for us newbies are absolutely KEY.  Thanks for pointing me in the right direction!!!!

No problem at all. I am glad you are enjoying my work. I remember when I first started with Linux. I was LOST. Now I am starting to feel comfortable and it is great. 

Thanks, Jereme

---

### Post by hungry on 2007-07-14
Hi, 
I followed this thread [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008) on debian sid and got dansguardian running. I have one question left, how do I add a GUI to my configuration?

Thanks,

Hungry

---

### Post by ananaboogie on 2007-07-22
Thanks for all your hard work Jereme. I just set up a computer lab for a small Christian School using Ubuntu Christian Edition, they love it. I have a question though.

The network for the lab looks like this: internet>router>Ubuntu CE 7.04>switch>10 XP Pro machines. When i installed Ubuntu CE 7.04 on the server dansguardian was functioning. I then installed firestarter, and dansguardian was still functioning. I then configured internet connection sharing and that broke dansguardian. All the computers in the lab can reach the internet and the server can see all the clients. Firestarter functions perfectly and reports all connections properly. Tinyproxy and dansguardian services are running and reporting no errors. The problem is that i get no filtering at all. its like ICS bypassed tinyproxy or something. If you know of any documentation on setting up dansguardian for a network enviroment it would be very helpful. Sorry for the long post.

---

### Post by mhancoc7 on 2007-07-22
> **ananaboogie said:**
> Thanks for all your hard work Jereme. I just set up a computer lab for a small Christian School using Ubuntu Christian Edition, they love it. I have a question though.

The network for the lab looks like this: internet>router>Ubuntu CE 7.04>switch>10 XP Pro machines. When i installed Ubuntu CE 7.04 on the server dansguardian was functioning. I then installed firestarter, and dansguardian was still functioning. I then configured internet connection sharing and that broke dansguardian. All the computers in the lab can reach the internet and the server can see all the clients. Firestarter functions perfectly and reports all connections properly. Tinyproxy and dansguardian services are running and reporting no errors. The problem is that i get no filtering at all. its like ICS bypassed tinyproxy or something. If you know of any documentation on setting up dansguardian for a network enviroment it would be very helpful. Sorry for the long post.

Thank you for letting me know how you are using Ubuntu CE. It is awesome to hear about it.

Honestly, my knowledge of setting up the filtering on a network is limited. There are several other forum members who are much more likely to know the answer. I am sorry that I can't be more help. :( I will watch this thread closely to see what comes of your question.

God Bless, Jereme

---

### Post by Jon Bn on 2007-08-15
I know this will sound stupid but where exactly is my home directory? Is it a folder, the desktop where?

---

### Post by bcalder01 on 2007-12-28
Thanks Jereme, just installed this on a machine I built for my friends kids, and so far it seems perfect. Many thanks for your hard work!!

---

### Post by silv3rback on 2008-03-05
Is there a way to remove the script?
It messed up my install on 7.10 and Im on not keen to reinstall everything over again

---

### Post by viliti on 2008-04-08
Do you have plan to support V7.10? or can I edit the script? any suggestion please

---

### Post by Toyota on 2009-01-22
The links seem to be dead.

I suppose this means no more awesome Dansguardian gui...
Now I have to use horrible hackery to configure Dansguardian again :sad:.

---

### Post by jpincheira on 2009-02-06
could you share this GUI script again?

thank you!


greets.

---

### Post by mhancoc7 on 2009-02-06
> **jpincheira said:**
> could you share this GUI script again?

thank you!


greets.

I have not worked on this script in a long while. I have focused my Ubuntu CE efforts with the distro itself. In fact I am behind on getting it updated. 

Jereme

---

### Post by plowdawg on 2010-11-17
There is a new GUI released on SourceForge.net called DansGUI, it is very basic at the time, but allows an in-browser OVERRIDE.  It is written in PHP, and is looking for developers if anyone wants to join. [https://sourceforge.net/projects/dansgui/]("https://sourceforge.net/projects/dansgui/")

---

