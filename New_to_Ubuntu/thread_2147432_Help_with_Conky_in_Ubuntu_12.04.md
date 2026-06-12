---
title: "Help with Conky in Ubuntu 12.04"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by Potter117 on 2013-05-21
As the title said, I need help running Conky in Ubuntu 12.04. I want to customize my desktop. I want it to be uniquely mine. From what I understand, Conky is the way to do this. Now, that said, everything I have found so far about Conky has been over my head. Will someone PLEASE explain it to me in a way that is for the ABSOLUTE. BEGINNER. Talk to me as if I was dumb, because in this instance I might as well be. 
Specifically, I need to understand how to make Conky run automatically when my profile is opened, how to customize what my Conky looks like because I do not want a big clunky black window, and how to run more than one at once. Basically everything, because all other explanations I have found in Ubuntu forums have been unhelpful to the true beginner. Very, VERY simple would be much appreciated.

---

### Post by dankojoffrey on 2013-05-22
Hi,
first you need to install conky
```
sudo apt-get install conky conky-all
```

then you need a startup script, which is usually packed with theme file, if not it should look like this:
```
#!/bin/sh

sleep 20   

conky -c ~/.conky/conkyrc
 
exit
```
save this file to your home dir "/home/username/" and name it something like "**.conky_start**" - the dot will make the file hidden and run in terminal **chmod +x ~/.conky_start**.

Then add conky to your startup apps, name it whatever you want and command like is **/home/username/.conky_start **
 
Create folder I mentioned in startup script (~/.conky/) - it is folder in your home dir, so **/home/username/.conky** and again the dot will make it hidden.

Now you need to put conkyrc file into your /home/username/.conky directory

there are plenty of theme for conky online... search deviantart... for simple use of conkyrc file try this one [http://browse.deviantart.com/art/Conky-Metro-Clock-245432929](http://browse.deviantart.com/art/Conky-Metro-Clock-245432929)

in the archive you will find start script, as well as conkyrc file...

If you are looking for completely custom theme, you will have to write it yourself, but I do not suggest that if you are complete begginer.

Hope it helps...

---

### Post by stylintile on 2013-05-22
Hello Potter117,
     You may want to check out the conky screenshots thread here:

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

It is a vey loooong thread, but you can find many good 'starter' configurations that you can modify into what you want.  I have found the answer to every conky question I've had there, either by searching or by asking.  It is also the best place I've found to get help setting it up.

Hope to see you there:D

---

### Post by deadflowr on 2013-05-22
No need to go as far as to create a script.
All you need is the add conky to the startup applications.
Of course this depends on the DE in use, Unity or xfce or kde are all different in how their guis work.
But for unity, open the dash and type startup which will give you an entry for startup applications, open it.
Then add a name, whatever you want.
then add the command
```
conky 
```
or
```
conky --config path/to/file
```

sometimes the conky set to run at startup overlaps with the panel, so a workaround it is delay the launching of conky by using the pause flag
```
conky -p 10
```
which delays it from starting for ten seconds.
set the -p to whatever you want though, it ain't sacrosanct. 

For help though look over these
[http://linux.die.net/man/1/conky](http://linux.die.net/man/1/conky)
This one gives some basic commands.
And this[URL="https://help.ubuntu.com/community/SettingUpConky"]
https://help.ubuntu.com/community/SettingUpConky[/URL]
And for fun, a really help howto on an impressive conky
[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

---

### Post by KoRnKloWn on 2013-05-22
If you want to customize your desktop, all Conky is, is a system monitoring tool, and yeah, you can customize it a lot, but it's not going to make the whole desktop unique, if you use Unity (the default Ubuntu desktop), then checkout Unity Tweak Tool, it allows a lot of customization, then keep in mind you can replace most apps with those you wish to use, like VLC instead of Totem, for music I use Guayadeque. Do a google search for different GTK3 themes also, there's easier ways to make your desktop unique if Conky is over your head. There are actually even GTK3 themes that have matching Firefox themes. Checkout [gnome-look.org]("http://gnome-look.org"). There are countless programs out there for customizing Linux. Also checkout the compiz configuration tool, but you'd want to be EXTREMELY careful with that, because you can break stuff.

---

### Post by thatguy2 on 2013-11-03
I was wanting a transparent system monitoring embedded to the desktop. I was able to get the terminal embedded like I wanted with compiz,  but I'm still working on the system monitoring.

---

### Post by Mopar1973Man on 2013-11-03
Here one of the super Conky threads.
[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

Here is my current desktop. It's still VinDSL source code but just modified to taste.
[ATTACH=CONFIG]247525[/ATTACH]

---

