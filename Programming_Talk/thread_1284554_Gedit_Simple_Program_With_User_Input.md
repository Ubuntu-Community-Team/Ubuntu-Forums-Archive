---
title: "Gedit Simple Program With User Input"
date: 2009-10-06
forum: Programming Talk
---

### Post by bengerszewski on 2009-10-06
Hey, i am trying to write a script to do the following: change the directory to /home/skippythegoat/cydia/apps/ then get user input ie: UserInput, then use that input to do: dpkg -b UserInput, then that makes a deb file in /home/skippythegoat/cydia/apps, and i want to move that file to /home/skippythegoat/cydia/upload/deb  then, change the directory to /home/skippythegoat/cydia/upload/ and issue the command dpkg-scanpackages -m . /dev/null >Packages  and then take file "Packages" and create an archive called "Packages.gz" out of it.  and thats it.  i have some idea how it will look:

#!/bin/sh

cd /home/skippythegoat/cydia/apps
Get UserInput (This is where i get lost)
dpkg -b UserInput
Move UserInput.deb | /home/skippythegoat/cydia/upload/deb/
cd /home/skippythegoat/cydia/upload
dpkg-scanpackages -m . /dev/null >Packages
Close Terminal

Obviously, i have no idea what the actual commands are, so do you think that you could take this idea and make it into a script that i could run?



OPTIONAL READING
-------------------
For those of you who are wondering, i have made a cydia repository ([http://repo.50g.com/apt/](http://repo.50g.com/apt/)) and i want to take the things i have to enter into the terminal and put that all into one script that i can run and just type in the name of the folder that has the package i want to add.

Also, if you have a jailbroken ipod, and you have some themes in mind, let me know and i will try to make that theme for you and get it on cydia.

---

### Post by ApEkV2 on 2009-10-06
something like this? (I'm not sure it will work, as I haven't tried it) 
```
#!/bin/bash

cd ~/cydia/apps
read -p "UserInput:" zIn
sudo dpkg-deb -b $zIn
mv $zIn.deb ~/cydia/upload/deb  #  Is this right??
cd ~/cydia/upload
if dpkg-scanpackages -m . /dev/null > Packages
	then
	zip -r name_of_file.zip Packages
fi 
```

---

### Post by bengerszewski on 2009-10-06
Ok, based on what you gave me, this is what i came up with:

#!/bin/sh

cd /home/skippythegoat/cydia/apps
echo -n "Type In The Package Name, Then Press [ENTER]: "
read package
dpkg -b "$package"
mv $package.deb ~/cydia/upload/deb
cd ~/cydia/upload
dpkg-scanpackages -m . /dev/null >Packages
gzip -c Packages.gz Packages



However, as far as the .gz archive, it isn't created.  I want it to keep the file "Packages" and also create a *****GZ***** archive.  What do i need to change?

---

### Post by bengerszewski on 2009-10-06
#!/bin/sh

cd /home/skippythegoat/cydia/apps
echo -n "Type In The Package Name, Then Press [ENTER]: "
read package
dpkg -b "$package"
mv $package.deb ~/cydia/upload/deb
cd ~/cydia/upload
dpkg-scanpackages -m . /dev/null >Packages
gzip -c Packages > Packages.gz

Nevermind, i figured it out, thanks!

---

