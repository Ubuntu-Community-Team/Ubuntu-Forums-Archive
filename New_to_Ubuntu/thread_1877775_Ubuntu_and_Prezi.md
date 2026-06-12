---
title: "Ubuntu and Prezi"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by suomalainen on 2011-11-08
Ubunteros,

Has anyone had any success with Ubuntu and Prezi? I have Ubuntu 10.04LTS and Firefox and trying to play the movie.swf file following the number of instructions on the Internet but nothing is working for me.

Here is one typical instruction I followed but never worked:

Use Prezi Presentations On Linux In Offline Mode

Normally you can present Prezi-Presentations using two methods:

1. You can use the online presentation mode offered by the Prezi site itself ([http://www.prezi.com/](http://www.prezi.com/)).

2. Or you can download a presentation-zip file which includes a Prezi-Presentation Application (prezi.exe) for executing an offline presentation.

Unfortunately this app is a windows app. But luckily the kernel off a Prezi-Presentation is a flash file. So we "only" have to "extract" the pure flash file data if we want to present a Prezi-Presentation on an Ubuntu Linux System. On the internet this idea was already described in a more general way. For all the sticklers of detail I list all single steps here:

Install a modern Ubuntu System like Lucid Lynx and its firefox package.

Install adobe-flashplugin using synaptic

Generate a new top-directory for all your Prezi-Presentations.
Call the Adobe-Flash-Configurator being offered as Adobe Web-Flash-Application.

Using the buttons "Edit locations" (offered in the tab "Global Security Settings") and the button "Add location" (being
embedded into the called dialog) add your generated prezi-top-directory as a location from which the flash player always trusts new reloadable files.

Goto [http://www.prezi.com/](http://www.prezi.com/) and load down your Prezi-presentation as zip file ("export to Portable prezi to present offline").

Unzip the zip file inside of your prezi-top-directory (by which your generate the prezi-specific-top-directory)

Change into the generated prezi-specific-top-directory.

Call a shell and insert "mv prezi.app/Contents/Resources/movie.swf ."

Open the Firefox and open the file "prezi-top-directory/prezi-specific-top-directory/movie.swf"

---

### Post by suomalainen on 2011-11-10
bump..................

---

### Post by mastablasta on 2011-11-10
never heard of Prezi, but since it's a windows application why not try to run it in Wine?
 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23114](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23114)

---

### Post by suomalainen on 2011-11-10
> never heard of Prezi, but since it's a windows application

With all respect.... If you haven't heard of Prezi then how can you make such assumption that you have? Wierd???

Dear Readers... If it's ok with everyone, let's limit responses to those familiar with the issue and who fully understand how Prezi works.

Thanks!

---

### Post by Tom-Freudenberg on 2012-09-11
Hey guys, I know that this might be an outdated thread but I just want to let you know, that I have written a small script to use your prezzis offline.

Please have a look on:

[https://github.com/TomFreudenberg/preziplayer/wiki](https://github.com/TomFreudenberg/preziplayer/wiki)

And maybe on a small usage demo at:

[http://prezi.com/5w9yvnnzmnir/prezi-player-on-linux/](http://prezi.com/5w9yvnnzmnir/prezi-player-on-linux/)

Bye
Tom

---

### Post by staartmees on 2012-10-18
just install Wine and your Prezi exe-file works fine.

---

