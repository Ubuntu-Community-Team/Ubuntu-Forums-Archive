---
title: "New to Linux, have several issues."
date: 2013-11-26
forum: New to Ubuntu
---

### Post by ivanmazin on 2013-11-26
I'm relatively new to Linux and while I have used it a couple of years back, it now appears to have gotten more complicated and confusing. First of all I can't figure out how to install files that aren't in the the Ubuntu software center, I recall a file like a .jar would just plug and play out of the box, but now clicking on it results in the file being opened as an archive. Specifically I have downloaded the multibit Linux installer and that's what it's doing.

EDIT: I found some installation instructions that go like this:

> Download the [Linux / Unix installer]("https://multibit.org/releases/multibit-0.5.15/multibit-0.5.15-linux.jar").
 Open a terminal window and make the installer executable with:
 chmod +x multibit-0.5.15-linux.jar Run the installer with:
 java -jar multibit-0.5.15-linux.jar
But all this gets me I a statement that the file doesn't exist in the directory. I can see the file in my downloads folder however.

A couple of software that I have installed via the software center I can't find. I installed an alternative torrent client, but it created no easily visible shortcuts so I can't get it to work. And I have tried to look for something like an executable in the file system and found nothing.

Lastly I can't get the update manager to download any updates, it's telling me I have 84megs worth of pending updates, but when trying to download them it craps out and tells me to check the internet connection. And if there is an issue with the internet connection, you wouldn't be seeing this thread.

What do I do to fix this stuff?

---

### Post by heir4c on 2013-11-26
Right click on the file and choose the Permission Tab. There you can check the little box below to make the file executable. 
But!! Look for the settings of Nautilus. There is something changed. (why? I don't now)
Set the window of nautilus bigger and go with the mouse over the top of the screen. Now you see the menu-bar and something like "Files" (I have not a English version).
Click on it and see for the Preferences and choose the Tab with 'Behavior' (or something like that).
There you see in the middle some settings for the executable files. Change that to: "Ask each time" or "automatic run the executable file" or something like that in English. You find the right settings by yourself.
If you doubleclick now on a executable file you get a window with the options like in the past. (Or it run directly if you choose the other option).
I hope this will help you.

For the Update Manager: Just click on OK. (More people have this, it's a bug or something)
For the shortcuts. Start the program up from the Dash (UbuntuLogo in the top left) and than you see a icon in the Launcher at the left. Rightclick on it and there you can choose to pin it in the Launcher.

---

### Post by jdeca57 on 2013-11-26
> **ivanmazin said:**
> 
But all this gets me I a statement that the file doesn't exist in the directory. I can see the file in my downloads folder however.



In a terminal go to the Downloads folder
cd ~/Downloads
And then
java -jar ./multibit-0.5.15-linux.jar

That directory isn't in your path, and once you're in the directory you have to say to search there with the prefix ./

---

### Post by grahammechanical on 2013-11-26
Installing files that we download from web sites is as complicated as it has ever been if we insist on doing it through the terminal. Nothing has changed there. If a file is an archive then right clicking it in File Manager will give the option to open the file with Archive Manager. It makes sense. If the file is a program's installation file then right clicking will get the option of opening with software centre and the software centre will do the job for us. Now, that is a lot less complicated than it used to be.

What is the error message that Update Manager is giving you? Sometimes it gives advice on how to fix it. This morning I had the error message that there was a missing header in one of the package lists in /var/lib/apt/lists/. But then again I am using Trusty Tahr (14.04 under development) and I expect stuff like that. The answer is simple.

```
sudo rm /var/lib/apt/lists/* -rf
sudo apt-get update
```

The first command removes/deletes the scripts in the lists folder. The second command replaces them. After doing that the update progressed as normal.

We have to assume that you are running the latest version of Ubuntu because you do not actually say which version you have installed. The applications that you have installed through the software centre should have put an icon in the Dash. Provided you are running standard Ubuntu with Unity and not one of the flavours of Ubuntu. You do not inform us. So, advice may be inaccurate.

Regards.

---

### Post by ian-weisser on 2013-11-26
> **ivanmazin said:**
> 
Lastly I can't get the update manager to download any updates, it's telling me I have 84megs worth of pending updates, but when trying to download them it craps out and tells me to check the internet connection. 

Please show us the EXACT error messages. Include all mysterious lines that you don't understand, in the presented order. They usually mean something to us.

---

### Post by ivanmazin on 2013-11-26
I can't show the download manager for now becuase it has disappeared from my system try.

The file is a .jar and I have never heard of there being a .jar archive. Inside the archive there is nothing resembling an installation file, it looks more like a java program would if you opened it with eclipse. It does not unfortunately have an option to open with software center. I tried setting permission to open as executable as well.

cd ~/Downloads
Returns "No such directory" I also tried cd ~/Home to point to desktop, same story.

I don't know what Nautilus is, and I can't find it by searching system settings, althoug there is a bunch of what appears to be extensions in the software center.

Here's some pics of what this mess looks like
[http://imgur.com/nW27m8Z](http://imgur.com/nW27m8Z)
[http://imgur.com/F52RV93](http://imgur.com/F52RV93)
[http://imgur.com/qGywiV7](http://imgur.com/qGywiV7)

EDIT: Seerched the entire computer for Nautilus [http://imgur.com/qkUGESj](http://imgur.com/qkUGESj)

---

### Post by jdeca57 on 2013-11-26
> **ivanmazin said:**
> 
cd ~/Downloads
Returns "No such directory" I also tried cd ~/Home to point to desktop, same story.



Well,in your screenshot I see a backslash \ for the cd, not a slash / and that does make a difference.
~ is short for your home directory. By the way from the top it's called /home no Capital.
And the desktop is
~/Desktop
With Capital. I'm sorry, but in the terminal you need to be precise.

---

### Post by The Cog on 2013-11-26
It's ```
cd ~/Downloads
```, not ```
cd ~\downloads
```

Nautilus is the name of the file manager, which you seem to be using OK.

---

### Post by oldos2er on 2013-11-26
A *.jar file is an java archive. You can see its contents with Archive Manager, but in order to run it you need to have Java installed; see [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) for help with that. I'd give OpenJDK a try first, if that doesn't work you'll need Oracle's java.

---

### Post by heir4c on 2013-11-26
I downloaded the file and install it to help you:

First open a terminal and type:

```
cd Downloads
```

you see something like that after the prompt:  ~/Downloads$ 
There you type:
```
chmod +x multibit-0.5.15-linux.jar 
```
That makes the file executable and after that type:
```
java -jar multibit-0.5.15-linux.jar
```

After that I get a error message about not having java on the system and that it can be find in the following packages:
  * default-jre
 * gcj-4.6-jre-headless
 * gcj-4.7-jre-headless
 * openjdk-7-jre-headless
 * openjdk-6-jre-headless

So I install simple the first one: default-jre
```
sudo apt-get install default-jre
```
Type your password.

After the installing of default-jre you type again the command:

```
java -jar multibit-0.5.15-linux.jar
```
Now it open a graphic installer. Follow the instructions and after installing you find multibit via the Dash (UbuntuLogo at the top left).

---

### Post by ivanmazin on 2013-11-26
Ok, I fixed the problem with the using the worng slash, I instinctively saw the backwards one for some reason. But the error that renders me unable to update is back, this time in console. I copy-pastad the error this time:

> The following extra packages will be installed:
  ca-certificates-java default-jre-headless icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icedtea-netx icedtea-netx-common java-common
  libatk-wrapper-java libatk-wrapper-java-jni libgif4 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib ttf-dejavu-extra tzdata tzdata-java
Suggested packages:
  equivs icedtea-plugin sun-java6-fonts fonts-ipafont-gothic
  fonts-ipafont-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts
The following NEW packages will be installed:
  ca-certificates-java default-jre default-jre-headless icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icedtea-netx icedtea-netx-common java-common
  libatk-wrapper-java libatk-wrapper-java-jni libgif4 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib ttf-dejavu-extra tzdata-java
The following packages will be upgraded:
  tzdata
1 upgraded, 16 newly installed, 0 to remove and 579 not upgraded.
Need to get 37.4 MB/37.9 MB of archives.
After this operation, 97.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main openjdk-6-jre-lib all 6b27-1.12.6-1ubuntu0.12.04.2
  404  Not Found [IP: 91.189.91.13 80]
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main ca-certificates-java all 20110912ubuntu6 [8,186 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main tzdata-java all 2012e-0ubuntu0.12.04.1 [140 kB]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main openjdk-6-jre-lib all 6b27-1.12.6-1ubuntu0.12.04.2
  404  Not Found [IP: 91.189.92.201 80]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main java-common all 0.43ubuntu2 [61.7 kB]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main openjdk-6-jre-headless amd64 6b27-1.12.6-1ubuntu0.12.04.2
  404  Not Found [IP: 91.189.91.13 80]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main default-jre-headless amd64 1:1.6-43ubuntu2 [3,336 B]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libgif4 amd64 4.1.6-9ubuntu1 [31.0 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main default-jre amd64 1:1.6-43ubuntu2 [882 B]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libatk-wrapper-java all 0.30.4-0ubuntu2 [30.9 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libatk-wrapper-java-jni amd64 0.30.4-0ubuntu2 [30.5 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main ttf-dejavu-extra all 2.33-2ubuntu1 [3,420 kB]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main openjdk-6-jre-headless amd64 6b27-1.12.6-1ubuntu0.12.04.2
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main openjdk-6-jre amd64 6b27-1.12.6-1ubuntu0.12.04.2
  404  Not Found [IP: 91.189.92.201 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main icedtea-6-jre-cacao amd64 6b27-1.12.6-1ubuntu0.12.04.2
  404  Not Found [IP: 91.189.91.13 80]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main icedtea-netx-common all 1.2.3-0ubuntu0.12.04.3 [600 kB]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main icedtea-6-jre-cacao amd64 6b27-1.12.6-1ubuntu0.12.04.2
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main icedtea-6-jre-jamvm amd64 6b27-1.12.6-1ubuntu0.12.04.2
  404  Not Found [IP: 91.189.92.201 80]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main icedtea-netx amd64 1.2.3-0ubuntu0.12.04.3 [16.2 kB]
Fetched 4,343 kB in 6s (658 kB/s)                                              
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b27-1.12.6-1ubuntu0.12.04.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b27-1.12.6-1ubuntu0.12.04.2_all.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b27-1.12.6-1ubuntu0.12.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b27-1.12.6-1ubuntu0.12.04.2_amd64.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b27-1.12.6-1ubuntu0.12.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b27-1.12.6-1ubuntu0.12.04.2_amd64.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b27-1.12.6-1ubuntu0.12.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b27-1.12.6-1ubuntu0.12.04.2_amd64.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-jamvm_6b27-1.12.6-1ubuntu0.12.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-jamvm_6b27-1.12.6-1ubuntu0.12.04.2_amd64.deb)  404  Not Found [IP: 91.189.92.201 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
anon5446@sacc-ubuntu:~/Downloads$ java -jar multibit-0.5.15-linux.jar
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>
anon5446@sacc-ubuntu:~/Downloads$ 



---

### Post by jdeca57 on 2013-11-26
A simple question: what is the result of [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) in a browser?

---

### Post by ian-weisser on 2013-11-26
We all know what http code 404 means: File does not exist in the place you are looking for it.
That's not an Ubuntu failure. You likely just caught the repository during an update.
Try it again.

---

### Post by ivanmazin on 2013-11-26
The link loads just fine, but I'm still having the same issue. I am beggining to suspect a corrupt install because the screen hangs in a strage pixilated state between selecting ubuntu in grub and the system loading the log in screen. Could windows be interfering? I am running Windows 8.0 in a separate partition and never had any issues with it, but I know it has a ton of bugs under the hood. Is it possible for it to simply be bad at sticking to its own partition?

Also tried update manager again, here are the errors from that.

```
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulsedsp_1.1-0ubuntu15.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulsedsp_1.1-0ubuntu15.3_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/isc-dhcp/isc-dhcp-client_4.1.ESV-R4-0ubuntu5.8_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/isc-dhcp/isc-dhcp-client_4.1.ESV-R4-0ubuntu5.8_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/isc-dhcp/isc-dhcp-common_4.1.ESV-R4-0ubuntu5.8_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/isc-dhcp/isc-dhcp-common_4.1.ESV-R4-0ubuntu5.8_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.7.3-6ubuntu2.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.7.3-6ubuntu2.1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu4.2_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/multiarch-support_2.15-0ubuntu10.4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/multiarch-support_2.15-0ubuntu10.4_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsyslog/rsyslog_5.8.6-1ubuntu8.4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsyslog/rsyslog_5.8.6-1ubuntu8.4_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp12ubuntu10.12_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp12ubuntu10.12_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_2.0.1-0ubuntu17.4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_2.0.1-0ubuntu17.4_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_2.0.1-0ubuntu17.4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_2.0.1-0ubuntu17.4_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_2.0.1-0ubuntu17.4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_2.0.1-0ubuntu17.4_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_2.0.1-0ubuntu17.4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_2.0.1-0ubuntu17.4_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/checkbox/checkbox_0.13.9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/checkbox/checkbox_0.13.9_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/checkbox/checkbox-qt_0.13.9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/checkbox/checkbox-qt_0.13.9_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.9.7.12-0ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.9.7.12-0ubuntu2_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins-default_0.9.7.12-0ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins-default_0.9.7.12-0ubuntu2_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.9.7.12-0ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.9.7.12-0ubuntu2_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.9.7.12-0ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.9.7.12-0ubuntu2_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.9.7.12-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.9.7.12-0ubuntu2_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/duplicity/duplicity_0.6.18-0ubuntu3.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/duplicity/duplicity_0.6.18-0ubuntu3.1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.4.2.3-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.4.2.3-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_3.4.2.3-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_3.4.2.3-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_3.4.2.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_3.4.2.3-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_23.0+build2-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_23.0+build2-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_23.0+build2-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_23.0+build2-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_3.0.2-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_3.0.2-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_3.0.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_3.0.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_3.0.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_3.0.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/printer-driver-hpijs_3.12.2-1ubuntu3.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/printer-driver-hpijs_3.12.2-1ubuntu3.1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libsane-hpaio_3.12.2-1ubuntu3.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libsane-hpaio_3.12.2-1ubuntu3.1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_3.12.2-1ubuntu3.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_3.12.2-1ubuntu3.1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libhpmud0_3.12.2-1ubuntu3.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libhpmud0_3.12.2-1ubuntu3.1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.12.2-1ubuntu3.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.12.2-1ubuntu3.1_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/printer-driver-hpcups_3.12.2-1ubuntu3.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/printer-driver-hpcups_3.12.2-1ubuntu3.1_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.9.7-0ubuntu7.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.9.7-0ubuntu7.10_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.9.7-0ubuntu7.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.9.7-0ubuntu7.10_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib-vpn1_0.9.4.0-0ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib-vpn1_0.9.4.0-0ubuntu4.2_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libr/libraw/libraw5_0.14.4-0ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libr/libraw/libraw5_0.14.4-0ubuntu2.1_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.79.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.79.6_all.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.2.0.52.62_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.2.0.52.62_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.52.62_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.52.62_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.52.62_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.52.62_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/printer-driver-postscript-hp_3.12.2-1ubuntu3.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/printer-driver-postscript-hp_3.12.2-1ubuntu3.1_all.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-utils_1.1-0ubuntu15.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-utils_1.1-0ubuntu15.3_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio_1.1-0ubuntu15.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio_1.1-0ubuntu15.3_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-gconf_1.1-0ubuntu15.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-gconf_1.1-0ubuntu15.3_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-x11_1.1-0ubuntu15.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-x11_1.1-0ubuntu15.3_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.6_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.6_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.6.3-2ubuntu2.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.6.3-2ubuntu2.6_all.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.6.3-2ubuntu2.6_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.6.3-2ubuntu2.6_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-common_0.82.7.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-common_0.82.7.3_all.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.82.7.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.82.7.3_all.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vino/vino_3.4.2-0ubuntu1.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vino/vino_3.4.2-0ubuntu1.2_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-bluetooth_1.1-0ubuntu15.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-bluetooth_1.1-0ubuntu15.3_amd64.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sessioninstaller/sessioninstaller_0.20+bzr128-0ubuntu1.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sessioninstaller/sessioninstaller_0.20+bzr128-0ubuntu1.2_all.deb) 404  Not Found [IP: 91.189.91.14 80]
```

---

### Post by ian-weisser on 2013-11-26
Your package index is out of date.
Refresh it with [B]sudo apt-get update
[/B]You should refresh the package index before updating or installing software to prevent precisely this problem.

Let's look at a random one of those 404s:
```
http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib-vpn1_0.9.4.0-0ubuntu4.2_amd64.deb
```
That's for the package libnm-glib-vpn1, version 0.9.4.0-0ubuntu4.[COLOR=#ff0000]2[/COLOR], arch amd64
Checking the repo manually, that package's current version is now 0.9.4.0-0ubuntu4.[COLOR=#ff0000]3[/COLOR]
Older versions are removed from the repositories when superseded. If you look for an older version, you will properly get a 404 - the version you asked for really isn't there.

---

### Post by ivanmazin on 2013-11-27
Thanks! That solved all my problems including installing multibit.

---

