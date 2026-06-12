---
title: "Building deb packages??"
date: 2006-05-02
forum: Programming Talk
---

### Post by hamil on 2006-05-02
Hello!

I am trying to find some easy information to how I can make deb files.
I found information regarding the checkinstall, but I can not get it to work properly, and people does not recommend checkinstall for making deb packages.

Is there anyone that can make an easy guide to how I can make deb files from tar.gz files?

Thank you for the responses!

Lasse

---

### Post by Kimm on 2006-05-02
Personaly I have nothing against checkinstall, it gives you a nice base to work on later.

After you run checkinstall, fire up Nautilus and move the .deb package to an empty folder, then rick click on it and select Extract.
You will now be facing two archives, data.tar.gz and control.tar.gz, delete any other files.
Now extract data.tar.gz in the same folder, then delete it, then create a new folder called "DEBIAN" (capital letters!) inside the same folder and move the control.tar.gz file to this folder and then extract it.

control.tar.gz should contain this file: "control"

Open "control" in your prefered text editor.
You should allredy have a decent base for your package, all you realy need to do is add dependencies, to do this you need to know what the program requires and what these libraries/programs are called.

For example, if the program requires GTK2, add this to Dependencies: "libgtk2.0-0 (> 2.8.0)" (the version number can be different, but that would apply pretty well to Dapper.

Now open up a terminal, and cd to the directory below the first that we created and run this command:

dpkg-deb -b <folder name>

That will build your new updated package.

I hope I managed to make this understandable... I'm not used to explaning things like this, this way. :)

---

### Post by darkarchon on 2006-05-02
can u specify what's the problem with checkinstall and why doesnt it work for u? instead of "sudo make install" u type "sudo checkinstall" (of course after configuring and compiling), and then fill in the details about the package name, version, etc.. and it creates a fine .deb package.

---

### Post by towsonu2003 on 2006-05-02
[QUOTE=darkarchon]can u specify what's the problem with checkinstall and why doesnt it work for u? instead of "sudo make install" u type "sudo checkinstall" (of course after configuring and compiling), and then fill in the details about the package name, version, etc.. and it creates a fine .deb package.[/QUOTE]
the biggest problem I can foresee is (if compilation succeeded) dependencies not being checked by the resulting package (hence the nice post by Kimm). I'm taking the OP wants his/her .debs portable.

---

### Post by hamil on 2006-05-02
[QUOTE=darkarchon]can u specify what's the problem with checkinstall and why doesnt it work for u? instead of "sudo make install" u type "sudo checkinstall" (of course after configuring and compiling), and then fill in the details about the package name, version, etc.. and it creates a fine .deb package.[/QUOTE]

Dohh... Seems like i hade a lineshift in version number, which gave me some errors... It is working fine now, and it did build me the deb file. Will try Kimms guide for polishing the deb.. :)

Thanks!

[quote=Kimm]I hope I managed to make this understandable... I'm not used to explaning things like this, this way. [/quote]

I understood everything, thank you very much! Someone should make a HOWTO from this... I searched the forum, but could not find anything like this.. 

Thanks!

---

### Post by hamil on 2006-05-02
Well, maybe I replied to fast... He he he..
Take my example, I have made an deb called mdf2iso.deb now with checkinstall. I have moved it to: /home/lasse/debs/
I unpacked the deb, deleted everything but the two archive files
Extracted data.tar.gz in /home/lasse/debs/
I then created /home/lasse/debs/DEBIAN/
I moved control.tar.gz to /home/lasse/debs/DEBIAN/ and unpacked it there.
The file "control" was opened in gedit, and edited to this content:
```

Package: mdf2iso
Priority: extra
Section: checkinstall
Installed-Size: 44
Maintainer: lasse@xx.nu
Architecture: i386
Version: 0.3.1-1
Depends: libc6 (>=2.3.4-1)
Description: mdf2iso

```
Is this correct, and if one deb depends on several others, how do I seperate them in the "Depends" part?
I then deleted the control.tar.gz
Went to terminal
cd /home/lasse/debs/
dpkg-dep -b /home/lasse/debs/

And I get the message "bash: dpkg-dep: command not found", I do not know what to install. If I search apt for dpkg-dep, it comes up with the result "devscript 2.9.10", which is allready installed, and the newest version.

Thanx in advance!

[QUOTE=Kimm]
Now open up a terminal, and cd to the directory below the first that we created and run this command:

dpkg-dep -b <folder name>

That will build your new updated package.

I hope I managed to make this understandable... I'm not used to explaning things like this, this way. :)[/QUOTE]

---

### Post by Kimm on 2006-05-02
That control file looks fine, if the package depends on several packages, just add packages after eachother on the same line, separated by commas.

On the "dpkg-dep" part, my misstake, that should be "dpkg-deb", sorry about that :)

Edit:
You should not run dpkg-dep inside /home/lasse/debs but rather run this "dpkg-deb -b debs" inside /home/lasse
Although the way you called dpkg-deb might still work.. since you include the full path name, but in case it doesnt, just do as I described above :)

---

### Post by hamil on 2006-05-02
[QUOTE=Kimm]That control file looks fine, if the package depends on several packages, just add packages after eachother on the same line, separated by commas.

On the "dpkg-dep" part, my misstake, that should be "dpkg-deb", sorry about that :)

Edit:
You should not run dpkg-dep inside /home/lasse/debs but rather run this "dpkg-deb -b debs" inside /home/lasse
Although the way you called dpkg-deb might still work.. since you include the full path name, but in case it doesnt, just do as I described above :)[/QUOTE]


Cool, thanks, worked like an charm now! :) Building debs as an pro now.. He he he..
Tack så mycket!

Lasse

---

### Post by hamil on 2006-05-10
Well, I have met the wall now...
I am building a pack for Mplayer from cvs. Everything works fine with checkinstall, it makes a deb file for me to edit.
I have moved the deb file to one empty folder called /home/lasse/debs/nya/
From that location I unpacked it, and got a new folder called mplayer_1.0-cvs/
This folder consisted of the normal two tar.z files, but when I unpacked it, it consisted of two folders, etc/ and usr/ Both these folders where moved to /home/lasse/debs/nya/mplayer_1.0-cvs
I edited the control file as usual, and moved it to /home/lasse/debs/nya/mplayer_1.0-cvs/DEBIAN/

After this, I went back to terminal, and cd /home/lasse/debs/nya/
From there I issued the command: dpkg-deb -b mplayer_1.0-cvs/
Then it builds a debian package inside /home/lasse/debs/nya/mplayer_1.0-cvs/ (This one always get called .deb, without any name, is that possible to change with some kind of syntax? Naggy to press ctrl+h all the time and rename the package... :))
When I try to install this package, it complains: ```

Trying to install '/.deb', which is also in package bmpx-0.15ubuntu-i386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```

At first i thought that I have messed things up in the control file, and checked it, but it looks nice. (Alot of unneccessary dependencies, but I will remove them later). Then I went on an checked the other two folders inside the deb, the /usr/ and /etc/
Inside the data.tar.gz, there is somehow created another .deb file??? This only consists of the normal control file..

I have no clue. I have tried to manually remove the .deb file that somehow got created, and then tried to build the package again, but somehow it always show up, and I am not able to install the mplayer.deb package ....

Looking forward to some guidance!

Lasse

---

