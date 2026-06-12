---
title: "Software centre has disappeared - how do I get it back ?"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by hebdave on 2014-04-25
High I have been using this article to install many of the necessaries on Ubuntu 12.04 [https://debianhelp.wordpress.com/2012/11/10/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](https://debianhelp.wordpress.com/2012/11/10/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/) . It was very good until it recommended what to remove to improve start up times. This was the list it told me to remove -

sudo apt-get purge oneconf popularity-contest python-ubuntuone-client python-ubuntuone-storageprotocol ubuntuone-installer gir1.2-ubuntuoneui-3.0 libsyncdaemon-1.0-1 libubuntuoneui-3.0-1 python-ubuntuone-control-panel rhythmbox-ubuntuone ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-couch unity-scope-musicstores deja-dup libfreerdp1 remmina remmina-common vino remmina-plugin-rdp remmina-plugin-vnc activity-log-manager-common python-zeitgeist activity-log-manager-control-center rhythmbox-plugin-zeitgeist unity-lens-video unity-scope-video-remote zeitgeist  zeitgeist-core zeitgeist-datahub rsync

sudo apt-get autoremove
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192
sudo apt-get update

Will the above somehow remove the software centre by mistake ? It also removed Ubuntu one and I also need that back again too just in case I need it. Since directly after these commands it disappeared. Is there anything else above I should be concerned about ? Can I just reverse the above by adding it all back with one command ?

Really sorry guys I feel a little stupid having done this. I guess the temptation was there to speed my computer start up. It in actual fact made no notable speed difference so I don't mind adding the commands all back somehow if you think thats best. I just need to add back what I removed and certainly get back software centre. I'd appreciate it if you'd check the commands above through for me too as I am a touch worried about them. 

Thanks very much indeed :)

---

### Post by Impavidus on 2014-04-25
```
sudo apt-get update
sudo apt-get install oneconf ... (that whole list)
```should get all those packages back. You might have to reconfigure some of them, if you did any system wide configuration. User config files should still be there.

---

### Post by hebdave on 2014-04-25
Hi thanks very much for taking a look at it all. Are you saying I should copy and paste the two things seperately. ie sudo apt-get update 

and then
 
sudo apt-get install oneconf [COLOR=#000000]sudo apt-get purge oneconf popularity-contest python-ubuntuone-client python-ubuntuone-storageprotocol ubuntuone-installer gir1.2-ubuntuoneui-3.0 libsyncdaemon-1.0-1 libubuntuoneui-3.0-1 python-ubuntuone-control-panel rhythmbox-ubuntuone ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-couch unity-scope-musicstores deja-dup libfreerdp1 remmina remmina-common vino remmina-plugin-rdp remmina-plugin-vnc activity-log-manager-common python-zeitgeist activity-log-manager-control-center rhythmbox-plugin-zeitgeist unity-lens-video unity-scope-video-remote zeitgeist zeitgeist-core zeitgeist-datahub rsync

.... after.  

Also where does my command end  ?  I had copied and pasted the entire section in my first post above including the below bit - 

[/COLOR][COLOR=#000000]sudo apt-get autoremove[/COLOR]
[COLOR=#000000]sudo add-apt-repository "deb [/COLOR][http://archive.canonical.com/](http://archive.canonical.com/)[COLOR=#000000] $(lsb_release -sc) partner"[/COLOR]
[COLOR=#000000]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192[/COLOR]
[COLOR=#000000]sudo apt-get update[/COLOR][COLOR=#000000]


So it had been done like this in one block (which I know need to reverse) -

[/COLOR][COLOR=#000000]sudo apt-get purge oneconf popularity-contest python-ubuntuone-client python-ubuntuone-storageprotocol ubuntuone-installer gir1.2-ubuntuoneui-3.0 libsyncdaemon-1.0-1 libubuntuoneui-3.0-1 python-ubuntuone-control-panel rhythmbox-ubuntuone ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-couch unity-scope-musicstores deja-dup libfreerdp1 remmina remmina-common vino remmina-plugin-rdp remmina-plugin-vnc activity-log-manager-common python-zeitgeist activity-log-manager-control-center rhythmbox-plugin-zeitgeist unity-lens-video unity-scope-video-remote zeitgeist zeitgeist-core zeitgeist-datahub rsync[/COLOR]
[COLOR=#000000]sudo apt-get autoremove[/COLOR]
[COLOR=#000000]sudo add-apt-repository "deb [/COLOR][http://archive.canonical.com/](http://archive.canonical.com/)[COLOR=#000000] $(lsb_release -sc) partner"[/COLOR]
[COLOR=#000000]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192[/COLOR]
[COLOR=#000000]sudo apt-get update
[/COLOR][COLOR=#000000]
Thanks very much perhaps I should of mentioned this prior. Do I copy and paste the whole lot with the last 4 lines of sudos also or just the part ending with ...[/COLOR][COLOR=#000000]zeitgeist-datahub rsync which are before the last sudos.[/COLOR][COLOR=#000000]

Please ask for clarification if I am not being clear. Thank you.


 [/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by deadflowr on 2014-04-25
You don't need to add the partner repos, with your command.That is already included, keys and all.
All you need to do is enable it.
Open the update manager(this is the easiest way) then go down to Settings and open that.
Now go to the tab marked Other Software.
Partners should be listed in that list.
Click on the entries to enable.
After you enable, close the window, and back at the update manager, click on the button marked Check.
After it runs, you will have access to whatever packages are included in the partner repos.

No comment on the other stuff you need help with, aside from reinstalling what you removed is probably the best course of action.
Simply replacing purge with install should suffice.

---

### Post by Impavidus on 2014-04-25
Just the sudo apt-get update and the sudo apt-get install blahblahblah commands. Those final four lines (the autoremove line and the things below) don't have to be undone separately.

And indeed, adding the partner repositories was not needed.

---

### Post by hebdave on 2014-04-25
Oh sorry Impavidus I still haven't quite understood you. Am I adding the whole thing or just up to a certain point. Perhaps if you did a quick copy and paste for me I'd know what you were saying when you said I'm 'not having to undo seperately' in relation to my question. Many apologies its not quite 'clicking' for me with the light bulb moment so to speak :) Thanks. I do understand the concept you are both talking about in installing rather than purging. ALthough purging is a new concept to me being new to Linux and Ubuntu. Don't feel you need to explain this as I am picking it up pretty much in terms of there meanings. Its just the practical copy and pasting I'm trying to completely understand initially . Thanks !

---

### Post by Impavidus on 2014-04-25
```

sudo apt-get update
sudo apt-get install oneconf popularity-contest python-ubuntuone-client python-ubuntuone-storageprotocol ubuntuone-installer gir1.2-ubuntuoneui-3.0 libsyncdaemon-1.0-1 libubuntuoneui-3.0-1 python-ubuntuone-control-panel rhythmbox-ubuntuone ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-couch unity-scope-musicstores deja-dup libfreerdp1 remmina remmina-common vino remmina-plugin-rdp remmina-plugin-vnc activity-log-manager-common python-zeitgeist activity-log-manager-control-center rhythmbox-plugin-zeitgeist unity-lens-video unity-scope-video-remote zeitgeist  zeitgeist-core zeitgeist-datahub rsync
```That will get your packages back.

Purging is the opposite of installing, so after you purged some packages we can undo it by installing them again. The autoremove command removed the dependencies of all those purged packages insofar as no other packages depended on them. apt-get install reinstalls all those dependencies automatically, so you don't have to worry about that. apt-get update refreshes the list of available software. It never does any harm and is good to run before you install any software. Some more advanced tools run it automatically.

Finally the add-apt-repository and apt-key command are to setup access to a new repository. There was no need to do that, as the partner repository can be enabled by just clicking a box in the GUI. I don't think it willl do any harm, but you can always go to your software sources and untick the partner repository.

---

### Post by hebdave on 2014-04-26
Hi thanks very much for all the information. Is it the case that when ever you remove a program you always should do sudo apt-get purge onconf 'package name' even if it is just one package or program your removing. And then if you think you will not need dependencies to always to sudo apt-get autoremove after. And as you say prior to doing anything do a sudo apt-get update. Also when you uninstall from software centre is it doing the equivilent through the GUI or is it just doing apt-something else ?

Thanks for your time its all very helpfull.:)

---

### Post by Impavidus on 2014-04-26
If you want to remove a package using the command line you can use sudo apt-get purge or sudo apt-get remove. The difference is that purge will also remove all config files belonging to the package, which remove does not. Usually there is little difference. When you have removed something and or not planning to install something else with the same dependencies, you can autoremove the now unneeded dependencies. This saves some disk space and bandwidth, as you don't have to upgrade these packages anymore. Just some house cleaning.

The graphical tools like the software centre and synaptic (which I use most of the time) all perform the same steps. The software centre has it all highly automated, which is good for beginning users. Synaptic or the command line provide more flexibility, making them better for advanced users or for problem solving. Because it's easier to communicate command lines over forum posts than GUI instructions we use the command line tools most of the time on these fora.

---

