---
title: "HOWTO: Sun Java 1.5 and Flash in 64-bit Konqueror browser! (No chroot required)"
date: 2005-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Ribs on 2005-11-16
This guide will show you how to get Sun's java 1.5 release working as a plug-in for 64-bit Konqueror, and how to get Macromedia's 32-bit flash plug-in working in 64-bit Konqueror.

I've tried to make this guide as newbie friendly as I can. Hence a lot of steps, but they are baby steps. It really isn't much hassle to get these things working.

Please note: The flash part of this guide is only helpfull for 64-bit users. As Macromedia refuse to release a 64-bit version, getting it working in a 64-bit browser is nigh-on impossible. This guide will not work for Firefox, Mozilla or similar browsers... This is only for Konqueror users, ideally using a KUbuntu (amd64 release) install.

_Sun Java_
Sun do not release a netscape compatible plug-in for Java for 64-bit systems. Only for 32-bit systems. However, due to the way Konqueror uses Java, it's not really a problem.

1) Go download Sun's 64-bit release of Java for Linux from here: [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) (Make sure to grab the 'Linux AMD64' release. Do not download the RPM.

2) Add universe and multiverse into your /etc/apt/sources.list file if you haven't already done so. See here if you're not sure how to do this; HowToEnableTheMultiverseRepositoryInUbuntu?action=show (Note: It lists Ubuntu instructions first. then KUbuntu after, so scroll towards the bottom).

3) Get the required packages installed into your system. Open up Konsole (K Menu, then System, then Terminal Program) and copy and paste the following into the Konsole window:```
sudo apt-get install fakeroot java-package java-common
```
Enter your password if you get asked for it. Apt will then probably confirm what you want installing. Just press 'Y' then Enter.

4) Stay with the Konsole window. Now copy and paste the following:```
fakeroot make-jpkg jre-1_5_0_05-linux-amd64.bin
```

5) You'll see the following. Press Y (enter isn't needed):```
Detected product:
    Java(TM) Runtime Environment (J2RE)
    Standard Edition, Version 1.5.0+update05
    Sun Microsystems(TM), Inc.
Is this correct [Y/n]:

```

6) Now you'll need to accept the agreement. Press Enter when prompted. Have a read (SpaceBar to scroll through the contents). Press 'q' when you've read that. If you agree with Sun's licencing terms, type in 'yes' and press enter. If not, type 'no' and enter and stop, this guide isn't for you...

7) Load of text will scroll past. Don't worry about it.

8) When that's done. Copy and Paste this: ```
sudo dpkg -i sun-j2re1.5_1.5.0+update05_amd64.deb
``` Enter your password if asked for it.

9) Nearly there! Now run this: ```
sudo update-alternatives --config java
``` This will activate Sun's java instead of using what KUbuntu ships with. Enter password if asked for it. Select the entry for '/usr/lib/j2re1.5-sun/bin/java' by putting in the number next to it, and pressing enter. For me, this was 3.

10) Open Konqueror. Goto the 'Settings' Menu. 'Configure Konqueror'. In the new window that opens, goto the 'Java and Javascript' picture on the left hand side (click on it). Change the 'Path to Java executeable, or 'java':' Setting to read '/usr/bin/java'. Click okay.

11) Now to test. Go here: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) And you should see a dancing cartoon, along with information showing Sun's Java 1.5 is installed!

_Macromedia Flash_:
Macromedia refuse to release a 64-bit version of their flash player. However, it can be forced to work with 64-bit Konqueror, with a little coaxing. Be warned, there are pitfalls to this approach:

* You'll be replacing the plug-in system Konqueror uses with a 32-bit version. This means any 64-bit plugins you already have will not work anymore.

* You'll be installing some required 32-bit libraries outside of apt or dpkg. This means that security updates for these packages that the KUbuntu/Ubuntu team release will not update these 32-bit libraries. It's unlikely to cause any issues. But just be aware of what you're doing. I'll try and release updated libraries when I see them

* This is a dirty hack. You will be copying library files to force flash to work. It should work, as it works very well here. But bear this is mind if you have problems. If you do have problems, let me know!

* Sometimes I have problems with sound not playing. I'm sure what the problem is. But I am working on this, and will keep everyone here posted.

* A nice side-effect of this, is that CrossOver Office's plug-ins now work!

1) Goto [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) in Konqueror.

2) Click 'Download now' and save the file in your home directory.

3) Goto [http://riblet.plus.com/kubuntu/](http://riblet.plus.com/kubuntu/) and download the latest set of libraries. This archive contains all the 32-bit stuff you need. Remember, this is a dirty hack, but should work well. I will update this page with newer versions of the libraries if I see any problems. At the time of writing, the latest file is ia32-for-flash-1.0.tar.gz

4) Open up Konsole (K menu, System, Terminal Program). Type in the following:
```
tar -zxvf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux/
chmod +w flashplayer-installer
nano -w flashplayer-installer
```
This will extract the flash player, go to where it extracts to, and will then open the install script. As we have to edit it.

5) Scroll down until you see the section labled:
```
##############################
# Main Section
##############################
```
A bit after that, you'll see: 
```
# check architecture
TEMPARCH=`uname -m`
case $TEMPARCH in
  i[3456]86)
```
Change that last line to read x86_64) - So the edited bit should be:
```
# check architecture
TEMPARCH=`uname -m`
case $TEMPARCH in
  x86_64)
```
Press Ctrl+X to exit the editor. Press 'Y' when it asks about saving the modified buffer (Towards the bottom of the window...). Then press enter.

6) Now install flash! Enter in the following lines (enter your password if asked). The first three lines create a home for flash, then make it accessable to all users, the fourth line starts the installer that we modified earlier.
```
sudo mkdir /opt/netscape
sudo mkdir /opt/netscape/plugins
sudo chmod 755 /opt/netscape/plugins
sudo ./flashplayer-installer
```

7) Follow the prompts from the installer. When asked for a 'installation path', enter in '/opt/netscape' (without the quotes). Press y and enter at the next prompt. On 'Perform another installation?' press n and enter.

8) Nearly there! Flash is now installed. Now we have to make Konqueror work with it... This is actually the easiest bit. Run these:
```
cd ~
sudo tar -zxvf ia32-for-flash-1.0.tar.gz -C /
```

9) Go back to Konqueror. Goto the Settings menu, 'Configure Konqueror'. Goto the 'Plugins' option along the left (you may have to scroll down). Click 'Scan for new plugins'. In the 'Plugins' tab, you should now see a entry for 'Netscape plugins', and a entry for '/opt/netscape/plugins/libflashplayer.so'. If so, everything should be working! I suggest you play with the 'Use artsdsp to pipe plugin sound through aRts' option if you have sound problems.

10) Test flash, visit [www.badgerbadgerbadger.com](www.badgerbadgerbadger.com) for a little flash animation.

_If you have problems_:
Respond to this thread. If you can't get the flash plug-in working, please give me the output of the following commands (I can't do much without this information, second command may give no output at all, but I'd like it all the same):
```
file /usr/bin/nsplugin*
nspluginscan
```

---

### Post by ubuntu_demon on 2005-11-16
why don't you use the plf repo for sun java 1.5 ?

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by Ribs on 2005-11-16
[QUOTE=ubuntu_demon]why don't you use the plf repo for sun java 1.5 ?[/QUOTE]Yes, this is possible. But it's not legal, the sun jre licence agreement specifically states that the software cannot be re-distributed. Therefore the plf are breaking this agreement. Also, it appears that support for anything other than i386 is fairly poor:> We support only i386 mainly because that’s all we’ve got ... ;) But you can try to build packages from source (this is what deb-src is for ...) for your architecture. There is absolutely no warranty that it will work, but it is worth the try.

---

### Post by Terracotta on 2005-11-17
Hye your link to  [http://riblet.plus.com/flash/](http://riblet.plus.com/flash/)  doesn't work, de site doesn't even exist. Nice how to, I got my java plugin finally working. Now I hope to get flash working as well.

Would another possibility for flash be to install 32 bit firefox (since I just use firefox for the things that don't open in konqueror, so I don't need it much). The solution might be euhm, a bit less hacky. But I just have no idea how to install the 32bit one, since in the repos there's a 64bit one.

---

### Post by Ribs on 2005-11-17
[QUOTE=Terracotta]Hye your link to  [http://riblet.plus.com/flash/](http://riblet.plus.com/flash/)  doesn't work, de site doesn't even exist. Nice how to, I got my java plugin finally working. Now I hope to get flash working as well.[/QUOTE]

Whoops! The correct URL is [http://riblet.plus.com/kubuntu/](http://riblet.plus.com/kubuntu/) - I have now corrected the guide.

---

### Post by kuja on 2006-01-19
The java fix worked beautifully for me. The Flash... not so. It's showing the plugin under the plugins list, but say I try to open an swf file, it will say "Unable to load netscape plugin for [insert-url-here]". Strange eh?

As for the output of those two commands, 
kuja@terra:~ $ file /usr/bin/nsplugin*
/usr/bin/nspluginscan:   ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped
/usr/bin/nspluginviewer: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped
kuja@terra:~ $ nspluginscan
kuja@terra:~ $

---

### Post by megadodo on 2006-03-26
Hey
Thanks to this howto, I know have Java working which is great. However, flash doesnt.
I have kde-3.5.0, could this be the problem? As looking at a similar gentoo thread there are different library versions for different kde versions.
Here are the requested output commands:
```
richard@ubuntu:~$ file /usr/bin/nsplugin*
/usr/bin/nspluginscan:   ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped
/usr/bin/nspluginviewer: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped
richard@ubuntu:~$ nspluginscan
richard@ubuntu:~$

```
When I run konqueror from a terminal and visit [www.badgerbadgerbadger.com](www.badgerbadgerbadger.com), it says "Qt: Locales not supported on X server"

Thanks in advance

Richard

---

### Post by spearfish on 2006-03-26
Hi, 

I get stuck on the following line:

sudo apt-get install fakeroot java-package java-common

my system can't find the package called "java-package"

need help please. :)

---

### Post by megadodo on 2006-03-27
You have to add the multiverse repositry [https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu]("https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu")

Have fun, and let me know if your flash works! Still cant get mine working...
Rich

---

### Post by henriquemaia on 2006-03-29
I got java to work.
Thanks a lot for this guide. Very helpful.

---

### Post by Ribs on 2006-04-30
[QUOTE=megadodo]Hey
Thanks to this howto, I know have Java working which is great. However, flash doesnt.
I have kde-3.5.0, could this be the problem? As looking at a similar gentoo thread there are different library versions for different kde versions.
When I run konqueror from a terminal and visit [www.badgerbadgerbadger.com](www.badgerbadgerbadger.com), it says "Qt: Locales not supported on X server"[/QUOTE]
KDE 3.5 is likley to be the problem. Are you running Breezy? This guide will not work with Dapper or newer releases of KDE as the files I made are for the Breezy standard version of KDE.

To be honest, I'm not using KDE anymore, I missed Gnome too much. Once Dapper comes out, this guide should be considered useless, as I won't be updating it anymore. Sorry.

Java should still 'just work', as Konqueror has a sexy way of using Java, so you can still use Sun's Java in this respect. For 64-bit flash, check out the Gnash project ( [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/) ) -- there is now a konqeuror plugin. This project is very new and still green around the edges. But progress is being made now, so it's worth checking out.

---

