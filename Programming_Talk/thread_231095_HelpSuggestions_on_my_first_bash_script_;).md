---
title: "Help/Suggestions on my first bash script ;)"
date: 2006-08-06
forum: Programming Talk
---

### Post by shawnrgr on 2006-08-06
Hello! Being new to linux (only a few months now) I find myself reinstalling ubuntu dapper often. I know most people would just tell me my problems don't need to be solved by reinstalling but oh well...

Anyway I thought this would be a good chance to try some bash scripting. I wanted to created a script that would automate the setup proccess after a fresh install. I know I could just get automatrix but I would rather try it myself ;)

I was counting on you guys to give me some pointers. Is there anything I'm doing wrong? Could something be done better? Let me know what you guys think...

p.s. everything is commented out with #- (i added the '-' so i can easily find/replace them all to null) so i can test different parts withought running the entire script..

This isn't complete.. just started tonight ;)

```
#!/bin/bash

## Update ect/apt/sources.list
	#-sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
	#-sudo cp sources.list /etc/apt/sources.list
	#-sudo chown root /etc/apt/sources.list
	#-wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
	#-sudo apt-get update

## linux-k7 kernel package (amd64)
	#-sudo apt-get install linux-k7

## Nvidia driver
	#-sudo apt-get install nvidia-glx nvidia-kernel-common
	#-sudo nvidia-glx-config enable

## Firefox/Swiftfox Plugins
	#-echo "*Firefox/Swiftfox Plugins*"
	#-echo " "
	#-echo " ** Sun Java **
	#-echo "    - agree (y) to all terms and conditions"
	#-sudo apt-get install sun-java5-jre sun-java5-plugin
	#-echo " "
	#-echo " ** Set J2SE as the default JVM **
	#-echo "    - please choose the option that corresponds to J2SE."
	#-sudo update-alternatives --config java

	#-echo " "
	#-echo " ** Macromedia Flash plug-in for Firefox/Swiftfox **
	#-sudo apt-get install flashplugin-nonfree
	#-sudo update-flashplugin

	#-echo " "
	#-echo " ** Mplayer w/Mozilla plug-in **	
	#-sudo apt-get install mozilla-mplayer

## Swiftfox (amd64)
	#-sudo wget http://getswiftfox.com/builds/releases/swiftfox-1.5.0.6-athlon64.tar.bz2
	#-sudo tar -jxf swiftfox-1.5.0.6-athlon64.tar.bz2
	#-sudo tar -jxf customsearch.tar.bz2
	#-sudo rm -R swiftfox/searchplugins
	#-sudo mkdir swiftfox/searchplugins
	#-sudo mv customsearch/* swiftfox/searchplugins
	#-sudo mkdir /opt/swiftfox
	#-sudo mv swiftfox/* /opt/swiftfox
	#-sudo ln -s /usr/lib/mozilla-firefox/plugins/* /opt/swiftfox/plugins/
	#-sudo ln -s /opt/swiftfox/swiftfox /usr/bin/swiftfox
	#-sudo rm swiftfox-1.5.0.6-athlon64.tar.bz2
	#-cp Swiftfox.desktop /home/shawn/Desktop/

## Multimedia
	#-sudo apt-get remove totem totem-gstreamer
	#-sudo apt-get install totem-xine libxine-extracodecs rhythmbox-applet
	

```

---

### Post by harisund on 2006-08-07
Did you try it out? 

I did the exact same thing .. and mine works fine. (After a lot of reinstalls :D but that's besides the point). 

Here's what I would suggest you do. First, reinstall and start from fresh. 

Then as and when you make some change, do it on the command line, and then immediately take a note of it. If you have affected some file in the progress, create a backup copy of the file. Consequently, start with a folder called 'backup' in your home directory. 

For example, you have a new sources.list (naturally!) so what you would want to do is copy the new sources.list into your ~/backup directory. 

Then in your script you would do 'sudo cp ~/backup/sources.list /etc/apt/sources.list' and you are good to go. 

I do that for plenty of files. Some of them include '/etc/fstab, /etc/apt/sources.list, /etc/inittab, /etc/dhcp3/dhclient' and so on. Create a backup copy and sudo mv it back to original. 

Also, for Firefox plugins, you could merely save your ~/.mozilla directory. That has all your saved plugins, bookmarks, extensions, themes, history and so on.

---

