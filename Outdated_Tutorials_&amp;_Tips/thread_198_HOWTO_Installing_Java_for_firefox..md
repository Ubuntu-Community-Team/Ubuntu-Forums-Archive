---
title: "HOWTO: Installing Java for firefox."
date: 2004-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-11
If you want to install java with firefox [download the java file here]("http://java.sun.com/webapps/download/AutoDL?BundleId=9718") and then run:
 
 > 
 sudo chmod a+x j2re-1_4_2_05-linux-i586.bin
  ./j2re-1_4_2_05-linux-i586.bin
 sudo mv j2re-1_4_2_05 /usr/local/
 cd /home/username/.mozilla/plugins
 ln -s /usr/local/j2re1.4.2_05/plugin/i386/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so 
 This will give you working java in firefox :)

---

### Post by flygmaskin on 2004-10-11
Well, It did not give me working java. But it broke firefox, always something :)

---

### Post by disposable on 2004-10-11
You just need to add a "libjavaplugin_oji.so" to the end of the last command.

```
ln -s /usr/local/j2re1.4.2_05/plugin/i386/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so
```

---

### Post by ubuntu-geek on 2004-10-11
fixed  :shock:

---

### Post by Jakomcbean on 2004-10-11
Sounds great . Any Idea how to do this on a PPC machine?

---

### Post by ubuntu-geek on 2004-10-11
check out this info over at the mozilla site for firefox and mac..

[http://plugindoc.mozdev.org/faqs/java.html#MacOSX](http://plugindoc.mozdev.org/faqs/java.html#MacOSX)

---

### Post by Perfect Storm on 2004-10-12
Funny my firefox doesn't have a plugin folder  :? 

This is what I have:

[email]root@Universe:/home/orion/.mozi[/email]lla # dir
appreg  firefox  pluginreg.dat

then I checked under firefox folder:

[email]root@Universe:/home/orion/.mozi[/email]lla # cd firefox
[email]root@Universe:/home/orion/.mozi[/email]lla/firefox # dir
default.7zs  profiles.ini
[email]root@Universe:/home/orion/.mozi[/email]lla/firefox #

anysuggestions?

---

### Post by ubuntu-geek on 2004-10-12
just do a quick

mkdir  /home/username/.mozilla/plugins

that should do it for you.

---

### Post by Perfect Storm on 2004-10-12
okay thanks :)

---

### Post by spoetnik on 2004-10-14
Problem after:
"sudo chmod u+x j2re-1_4_2_05-linux-i586.bin 
./j2re-1_4_2_05-linux-i586.bin 
"
I get an, "Cannot execute binary file"

Please help.....

---

### Post by FLeiXiuS on 2004-10-14
chmod a+x filename.bin

Do that then execute filename.

---

### Post by johanvrt on 2004-10-15
Instead of "chmod a+x filename.bin" and then "./filename.bin" , 
you can also do "sh filename.bin"
The "chmod a+x" bit is not needed with the "sh"  command. :)

deFrysk

---

### Post by spoetnik on 2004-10-15
[quote=spoetnik]Problem after:
"sudo chmod u+x j2re-1_4_2_05-linux-i586.bin 
./j2re-1_4_2_05-linux-i586.bin 
"
I get an, "Cannot execute binary file"

Please help.....[/quote]

I have downloaded the file again from the Java site, and now it works!!
Thanks for all the help.

---

### Post by emperor on 2004-10-16
1.Links to sun's java site and other available plugins: 
[http://plugindoc.mozdev.org/linux.html#Java](http://plugindoc.mozdev.org/linux.html#Java)

2. I installed Sun's jre1.5 and it works OK.

3. To install java for firefox globally, make your simlink in this directory :
/usr/lib/mozilla-firefox/plugins

For example, when positioned in the above directory, execute the following:
sudo ln -s /usr/local/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so

Note: the jre1.5 has a "ns7-gcc29" and a "ns7" for  gcc3x.

---

### Post by rjl on 2004-10-17
I'm new to Ubuntu and "sudo", so this might be a very basic question, but--

I followed the procedure to install java with firefox and got java installed, but when I try the last command, I get:
   "bash: In: command not found"

When I tried to cut and past the plugin into firefox I was not able to, I assume because I was not Root.

Thanks,

---

### Post by FLeiXiuS on 2004-10-17
sudo passwd root

Enter in the root password, then I would sudo whenever.

---

### Post by muypill on 2004-10-17
I got up until the end where I get the error: "In: command not found"

help.

---

### Post by FLeiXiuS on 2004-10-17
sudo apt-get update &amp;&amp; apt-get upgrade

Also be sure to login as root when your doing this install

---

### Post by muypill on 2004-10-17
Tried  that, it still tells me that it cannot find the In command. Is there anything else I can try?

---

### Post by Rancoras on 2004-10-17
This may sound stupid, but are you sure you're typing ln (el en) and not In (eye en) ?

---

### Post by johanvrt on 2004-10-18
you did "In" as in  (In)sert
It should be "ln" , short for link. 
ln -s , meaning link symbolicly  

deFrysk. 8)

---

### Post by rjl on 2004-10-18
Thanks guys!

I was typing In as (In)sert.  I now have java 1.5 working in firefox.

I find it easy to make dumb mistakes with computers.

---

### Post by muypill on 2004-10-18
Yeah, that was it. Thanks a lot. I now feel more dumb. :D

---

### Post by CyberSeal on 2004-10-19
why doesn't Ubuntu include a package for installing java automatically?
like the one made for flash plugin. 
are there any legal issues ?

---

### Post by smoothrt on 2004-10-21
I am still looking for newbie-friendly directions on how to do this for amd64 and can't find anything.  Can someone post directions, or at least a link of a way to get java installed and working in firefox for ubuntu amd64.  It's been very frustrating, and would finish my tweaking of my OS.  Thank you.

---

### Post by adbak on 2004-10-21
I don't know if there are any legal issues, but I do know that Sun wants everyone to download Java from them.  Although this only leads to people hating them....

---

### Post by LongTooth on 2004-10-21
Quick question: If I have Mozilla installed as well as Firefox (and I do) will I have to do anything different or will this procedure install Java in both browsers?

---

### Post by smoothrt on 2004-10-22
I don't know how it can be true that you have to go to sun's website for legal reasons.  I have tried many other linux distributions, and while I have found Ubuntu to be my favorite, other distributions, even amd64 versions, had java already working upon installing (i.e. Mandrake).  This really should be easier, it's the last "major" thing I can't get working on my system.

---

### Post by butters on 2004-10-23
ubuntu has adopted a completely free/open-source strategy like that of Red Hat, Debian, and Fedora.  This is fine, but I would like to see the following happen:

1. Give users the option to install a selected "non-free" software set during installation, right before grabbing updates from the internet.  This set would include mpeg123, libdvdcss, flash, and possibly some others (the most common non-free packages).  The only major one that could not be installed at this point is Java, since it requires manual download from the net.

2. Include the universe repositories by default, but clearly warn users when they mark universe packages for installation (or print a confirmation message if using CLI).

3. Include every package that ubuntu devs know how to install, even if the process requires manual intervention.  In the case of Java, the terminal ouput during the package installation should stop and prompt for users to follow the provided link to the vendor's download page and get the binary.  After loading the binary from the user's home directory (determined by querying which user sudo is speaking for), or whichever download directory is specified, and running, it should create the appropriate symlinks/registry keys.  This is sort of how Gentoo handles Java, only it provides the link and requires the user to gain root and place the binary in /usr/portage/distfiles before running emerge again. 

Because if the recipe for installing the java sdk and mozilla plugin is so simple, then it might as well have an ubuntu deb package.  Users shouldn't have to search for some howto on installing the java plugin.  They should ask Synaptic to find java and have Synaptic guide them through the installation process.

---

### Post by butters on 2004-10-23
[QUOTE=smoothrt]I don't know how it can be true that you have to go to sun's website for legal reasons.  I have tried many other linux distributions, and while I have found Ubuntu to be my favorite, other distributions, even amd64 versions, had java already working upon installing (i.e. Mandrake).  This really should be easier, it's the last "major" thing I can't get working on my system.[/QUOTE]

You can find a binary for sun-jdk-1.5.0-rc-amd64 here:

[http://public.planetmirror.com/pub/java-sun/JDK-1.5.0_RC/amd64/jdk-1_5_0-rc-linux-amd64.bin](http://public.planetmirror.com/pub/java-sun/JDK-1.5.0_RC/amd64/jdk-1_5_0-rc-linux-amd64.bin)

download it to your home directory and open a terminal:

sh ./jdk-1_5_0-rc-linux-amd64.bin
<scroll down through license and type 'yes'>
sudo mv jdk-1_5_0-rc /usr/local
cd .mozilla/plugins
ln -s /usr/local/jdk-1_5_0-rc/plugin/amd64/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so

Then restart firefox and type 'about:plugins' in the URL box, this opens a page that summarized your installed plugins, and a healthly list of different java MIME types should be listed.

I don't have an AMD64 machine so I haven't run through this myself.  The directory paths might be named slightly differently, tab completion is your friend.

Good luck.

---

### Post by gecko on 2004-10-24
[QUOTE=butters]You can find a binary for sun-jdk-1.5.0-rc-amd64 here:

[http://public.planetmirror.com/pub/java-sun/JDK-1.5.0_RC/amd64/jdk-1_5_0-rc-linux-amd64.bin](http://public.planetmirror.com/pub/java-sun/JDK-1.5.0_RC/amd64/jdk-1_5_0-rc-linux-amd64.bin)

download it to your home directory and open a terminal:

sh ./jdk-1_5_0-rc-linux-amd64.bin
<scroll down through license and type 'yes'>
sudo mv jdk-1_5_0-rc /usr/local
cd .mozilla/plugins
ln -s /usr/local/jdk-1_5_0-rc/plugin/amd64/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so

Then restart firefox and type 'about:plugins' in the URL box, this opens a page that summarized your installed plugins, and a healthly list of different java MIME types should be listed.

I don't have an AMD64 machine so I haven't run through this myself.  The directory paths might be named slightly differently, tab completion is your friend.

Good luck.[/QUOTE]

Actually this does not seem to work with JRE 1.5.0 (Version 5.0) because when you open the [Java Test Page](http://www.java.com/en/download/help/testvm.jsp)  the browser will hang. Has anyone got version 5.0 working?

When I link to the ns7-gcc29 version the browser will not even open. When I try the ns7 version the browser opens, about:plugins shows it is installed but the test page hangs the browser.

NB:I am doing everything in sudo bash. I cannot get the damn think working.

Gecko

---

### Post by gecko on 2004-10-24
Update,

Ok I tried everything and only 1.4.2 would work so I would stick with that for the moment. I suspect it may have something to do with my proxy environment. The authentication window is not displaying, or it is displaying in the background!

**Java installation instructions**

Open firefox and navigate to [http://java.sun.com](http://java.sun.com). Download J2SE 1.4.2 JRE Linux self extracting binary. Now Open a terminal window Applications->System Tools->Terminal. Enter the sudo bash command and press enter.  Enter the password and you will then have a root prompt. Copy and paste the following code.

```

sh j2re-1_4_2_06-linux-i586.bin
install -d j2re1.4.2_06 /usr/java
ln -s /usr/java/j2re1.4.2_06/plugins/i386/ns610-gcc32/libjavaplugin_oji.so \
/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so

```

Done!

Regards

Gecko

---

### Post by brschmid on 2004-10-25
how do i know i have java working, i went thru and did everything?

---

### Post by FLeiXiuS on 2004-10-25
[QUOTE=brschmid]how do i know i have java working, i went thru and did everything?[/QUOTE]


Best way to test is to actually preform a browser test on java.  Go to a java website such as [http://games.yahoo.com](http://games.yahoo.com) and see if you can participate in a game.  There are many ways but this is the mose rewarding out there. :-)

---

### Post by brschmid on 2004-10-26
[QUOTE=FLeiXiuS]Best way to test is to actually preform a browser test on java.  Go to a java website such as [http://games.yahoo.com](http://games.yahoo.com) and see if you can participate in a game.  There are many ways but this is the mose rewarding out there. :-)[/QUOTE]
 thanks :)

---

### Post by princemackenzie on 2004-10-27
Thanks so much for this.

---

### Post by jcscar on 2004-10-29
I did all of the commands listed in the first post
They all worked great

However when I go to [http://www.java.com/en/download/help/testvm.jsp](http://www.java.com/en/download/help/testvm.jsp) The test does not work. I am running an amd athlon 2500 nothing special... ??

---

### Post by arrowhead on 2004-10-29
Me to jcscar  :sad: .
I followed gecko's instruction and no errors occured (I don't think I did anything wrong). I thought it had worked but when I go to a page with java on all I get is a box from Firefox saying I don't have the plugin to open the file.

David

---

### Post by ubuntu_demon on 2004-10-31
For those who installed j2sdk :

sudo ln -s /opt/SUNWappserver/jdk/jre/plugin/i386/ns610-gcc32/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so

---

### Post by optik on 2004-10-31
Thanks, worked a treat

---

### Post by Patrick on 2004-11-03
ok,  ( i use the .1 extention because the file i d/l has it to )

i did these to commands
 sudo chmod a+x j2re-1_4_2_05.1-linux-i586.bin
./j2re-1_4_2_05-linux-i586.bin

and everything went ok,

then i did this command

 sudo mv j2re-1_4_2_05.1 /usr/local/

and i get this error

mv: cannot stat `j2re-1_4_2_05.1': No such file or directory



 :???:

---

### Post by Verlager on 2004-11-05
[QUOTE=brschmid]how do i know i have java working, i went thru and did everything?[/QUOTE] **[SIZE=3] java -version[/SIZE]**

---

### Post by BugsyMalone on 2004-11-06
[QUOTE=Patrick]ok,  ( i use the .1 extention because the file i d/l has it to )

i did these to commands
 sudo chmod a+x j2re-1_4_2_05.1-linux-i586.bin
./j2re-1_4_2_05-linux-i586.bin

and everything went ok,

then i did this command

 sudo mv j2re-1_4_2_05.1 /usr/local/

and i get this error

mv: cannot stat `j2re-1_4_2_05.1': No such file or directory



 :???:[/QUOTE]
 I got the same error as Patrick. What can we do to fix it?

---

### Post by mattyh on 2004-11-06
your command is wrong, it is **a**+x...

---

### Post by FLeiXiuS on 2004-11-06
[QUOTE=BugsyMalone]I got the same error as Patrick. What can we do to fix it?[/QUOTE]


I would recommend typing
```

ls

```

Then seeing if the directory is there.  If not, then what's the correct name of the jr2e directory.

---

### Post by MarkJMK on 2004-11-07
[QUOTE=BugsyMalone]I got the same error as Patrick. What can we do to fix it?[/QUOTE]
For me this is what worked
sudo mv j2re1.4.2_05 /usr/local/

---

### Post by krietor on 2004-11-10
Check out [http://www.ubuntulinux.org/wiki/FirefoxHowTo/view?searchterm=plugins%20Firefox](http://www.ubuntulinux.org/wiki/FirefoxHowTo/view?searchterm=plugins%20Firefox)
Here's the instructions. Sorry for the lousy format. They're from memory, too, sort of but they worked. At least if I didn't leave anything out:
 I downloaded [http://java.sun.com/webapps/download/AutoDL?BundleId=9718](http://java.sun.com/webapps/download/AutoDL?BundleId=9718) 
In a terminal I cd'd to the directory I downloaded the file to and I did:
"sudo chmod a+x j2re-1_4_2_05-linux-i586.bin" (makes it executable)
and then I did: 
"./j2re-1_4_2_05-linux-i586.bin" To run the installer script. It didn't run smoothly for me. I didn't know how to exit from the program that displayed the license agreement. {edit: It was probably less . push <q> to quit.} I think there was supposed to be a "button" to choose to indicate acceptance, but all I got was "END" or something, Finally I was able to exit using <shift>+<alt>+Q or something.{edit: It was probably less . push <q> to quit.} Then I had a chance to type "yes" and the installation proceeded. Then, 
"sudo mv j2re1.4.2_05 /usr/local/" -and then
"cd /usr/lib/mozilla-firefox/plugins" -and-[I think here I was superuser]?
"ln -s /usr/local/j2re1.4.2_05/plugin/i386/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so"
And then after restarting Firefox, Java worked! I tested it  at [www.arachnoid.com](www.arachnoid.com) - just loading the front page quickly lets you know whether it works. :D :p

---

### Post by Nomad on 2004-11-14
Not working, at all.  [www.arachnoid.com](www.arachnoid.com) said that Java was NOT enabled in my browser.  In 'preferences' it is enabled.

Any ideas?

---

### Post by mongolito404 on 2004-11-14
I've used another method to install Java an the Java plugins for Firefox. This one is not listed on the Ubuntu Wiki and I can't find it here too.
It seems to be the (new) correct way to install Sun JDK on Ubuntu/Debian.

1) Install **java-common** and **equivs** with apt-get.
```
sudo apt-get install java-common equivs
```
2) Follow (with adaptations) instructions in [file:///usr/share/doc/java-common/debian-java-faq/ch11.html#s11.3](file:///usr/share/doc/java-common/debian-java-faq/ch11.html#s11.3) (installed by java-common). In a Root Terminal (Applications > System Tools > Root Terminal).
```
# cd /var/install
# mkdir java
# cd java
# wget [http://copy.the.correct/url/from/your/browser](http://java.sun.com/j2se/downloads.html) -O jdk-1_5_0-linux-i586.bin
# chmod +x jdk-1_5_0-linux-i586.bin
# ./jdk-1_5_0-linux-i586.bin
# mv jdk1.5.0 /usr/local/lib
# ln -s /usr/local/lib/jdk1.5.0 /usr/local/lib/jdk
# mkdir pkg
# cd pkg
# cp /usr/share/doc/java-common/dummy-packages/*.control .
# equivs-build java1-runtime-dummy.control
# equivs-build java-compiler-dummy.control
# equivs-build java2-compiler-dummy.control
# equivs-build java2-runtime-dummy.control
# equivs-build java-virtual-machine-dummy.control
# dpkg -i *.deb
# update-alternatives --verbose --install /usr/bin/java java /usr/local/lib/jdk/bin/java 500 --slave /usr/share/man/man1/java.1 java.1 /usr/local/lib/jdk/man/man1/java.1
# ln -s /usr/local/lib/jdk/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so
# java -version
```

The output of the last command should be something like
```
java version "1.5.0"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0-b64)
Java HotSpot(TM) Client VM (build 1.5.0-b64, mixed mode, sharing)
```

You should now have a full and working Java environment.

---

### Post by krietor on 2004-11-18
I'm looking forward to trying the instructions for installing Java 1.5! I'll be building a new Ubuntu system soon. However, I got Java 1.4.2 working well, and it does all I need. If it ain't broke, don't fix it . . . I can wait . . .
    Anyway, I wanted to say thanks for the instructions, mongolito404 !

---

### Post by bazuka on 2004-11-27
[QUOTE=ubuntu-geek]If you want to install java with firefox [download the java file here]("http://java.sun.com/webapps/download/AutoDL?BundleId=9718") and then run:
 
  
 This will give you working java in firefox :)[/QUOTE]


I had to change "sudo mv j2re-1_4_2_05 /usr/local/" to "sudo mv j2re1.4.2_05 /usr/local" to work. Thanks for the help with the rest of it though!

---

### Post by wallijonn on 2004-12-02
Stupid question, but how do you test Java?

---

### Post by adbak on 2004-12-02
To test Java, I go to [http://indystar.com/living/crosswords](http://indystar.com/living/crosswords) .  If the crossword puzzle loads, you have Java.

---

### Post by wallijonn on 2004-12-02
Thanks. I installed j2re-1_4_2_06-linux-i586.bin and wanted to see if it was really working. I went to a few googled 'java test' sites and some worked and some didn't.

---

### Post by LongTooth on 2004-12-02
A sure way to test Java is to do what I do. I go to Yahoo.com. Look for 'Games'. I usually choose the 'Collapse' game but any one will do. That will let you know if you have Java working.

---

### Post by wallijonn on 2004-12-07
[http://games.yahoo.com/games/downloads/cl.html](http://games.yahoo.com/games/downloads/cl.html)

man, that game is addicting. [img]http://www.ubuntuforums.org/images/icons/icon14.gif[/img]

---

### Post by Hikaru79 on 2004-12-07
Well, if you *have* to play a Yahoo game, there's no doubt-- Go is still the best! :D
[http://games.yahoo.com/go](http://games.yahoo.com/go)


--Certified Go Addict  :D

---

### Post by ZEN on 2004-12-14
[QUOTE=ubuntu-geek]
  sudo chmod a+x j2re-1_4_2_05-linux-i586.bin
./j2re-1_4_2_05-linux-i586.bin
sudo mv j2re-1_4_2_05 /usr/local/
cd /home/username/.mozilla/plugins
ln -s /usr/local/j2re1.4.2_05/plugin/i386/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so
  [/QUOTE]

works great with firefox 1.0, had to change 1 thing in the this command:
sudo mv j2re-1_4_2_05 /usr/local/ 

had to be 

sudo mv j2re1_4.2.05 /usr/local/

---

### Post by afrifreak on 2004-12-17
Wow, my first Linux-config kick! I managed to succesfully install Java for Firefox. 

 \\:D/

---

### Post by afrifreak on 2004-12-17
[QUOTE=ubuntu-geek]If you want to install java with firefox [download the java file here]("http://java.sun.com/webapps/download/AutoDL?BundleId=9718") and then run:
 
 sudo chmod a+x j2re-1_4_2_05-linux-i586.bin
./j2re-1_4_2_05-linux-i586.bin
sudo mv j2re-1_4_2_05 /usr/local/
cd /home/username/.mozilla/plugins
ln -s /usr/local/j2re1.4.2_05/plugin/i386/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so

  
 This will give you working java in firefox :)[/QUOTE]

These commands have made me succesfully install Java, but there's one comment: 
I think you have to change the "sudo mv j2re-1_4_2_05 /usr/local" command to:
sudo mv j2re1.4.2_05 /usr/local 
because this is the name of the directory that the compiler creates. 

 =D>

---

### Post by monkeyshaman on 2004-12-18
I can't get past this part:

j2re-1_4_2_06-linux-i586.bin: line 364: ./install.sfx.4225: cannot execute binary file

This happens right after I ./ the binary file.  Any ideas?   :-( 

Arnold

---

### Post by hammett111 on 2005-05-28
When installing java plugin for firefox is the .mozilla essential, can you just call the directory mozilla without the "."??

---

### Post by hantms on 2005-06-05
As for XMMS, you have to rememer to right-click on the xmms window and go into Options->preferences and select 'eSound' as the Output plugin. 

The default one will cause xmms to freeze up and die when opening an mp3 file.

---

### Post by desdinova on 2005-06-10
[QUOTE=hammett111]When installing java plugin for firefox is the .mozilla essential, can you just call the directory mozilla without the "."??[/QUOTE]
 yes you have to use the "." - a directory in Linux starting with a "." is a hidden directory - and ".mozilla" is a totally different directory to "mozilla"

---

### Post by rykel on 2005-06-11
Hi,

The easiest way to install the latest Firefox with Flash, Java, Adobe Reader plugins is to simply remove the current one, then *Save and Install* the [**Firefox autopackage**](http://www.wildgardenseed.com/Taj/autopackage/firefox-1.0.4.x86.package).

1.   Remove **mozilla-firefox** through Synaptic Package Manager.
      (it will remove some other stuff, but don't worry, because they can be reinstalled using autopackage or are seldom used.)

2.   Go to [**Autopackage Downloads**](http://autopackage.org/downloads.html) --> "More Packages" --> Firefox
      (Or download here --> [**Firefox autopackage**](http://www.wildgardenseed.com/Taj/autopackage/firefox-1.0.4.x86.package))

3.   Save the file to your Home directory.

4.   Open a terminal, type: **sudo ./firefox*.package** and follow the instructions accordingly.

5.   Copy everything in /usr/lib/mozilla-firefox/plugins to **/usr/lib/firefox/plugins**.
      (if you already have all your plugins installed previously)

To set up Java plugin, *adapt* the instructions from the [Unofficial Ubuntu Guide](http://www.ubuntuguide.org). Just remember, the Firefox autopackage is installed in /usr/lib/**firefox** instead of /usr/lib/*mozilla-firefox*.

That is it! A ***spanking, brand new Firefox 1.0.4*** with that cool foxy icon.

I have used Firefox 1.0.4 autopackage since it came out with no problems, and it is faster and more responsive than the Ubuntu Firefox.


You might also like to check out my 2 posts on [URL=http://www.linuxquestions.org/questions/showthread.php?s=&threadid=332407][B]
LinuxQuestions Forum[/B][/URL] and the [**Autopackage Forum**](http://autopackage.org/forums/viewtopic.php?t=21).

---

### Post by EmoDx on 2008-01-21
> **ubuntu-geek said:**
> If you want to install java with firefox [download the java file here]("http://java.sun.com/webapps/download/AutoDL?BundleId=9718") and then run:
 
  
 This will give you working java in firefox :)

Will this allow all user logins to use java or do I have to do this for each user?

-Emo

---

### Post by davidwashere2003 on 2009-03-06
I tried a bunch of stuff from this thread but nothing worked.

I went to a different site and found this step which worked like a charm:

sudo aptitude install sun-java6-jre sun-java6-plugin

---

### Post by uncr347ivenam3 on 2009-04-16
After agreeing to the license, I get this message

```
Do you agree to the above license terms? [yes or no] 
yes
Unpacking...
tail: cannot open `+479' for reading: No such file or directory
Checksumming...
1
The download file appears to be corrupted.  Please refer
to the Troubleshooting section of the Installation
Instructions on the download page for more information.
Please do not attempt to install this archive file.
```

I'm running ubuntu 9.04.  It's a pretty fresh install.  Any suggestions?

---

### Post by uncr347ivenam3 on 2009-04-16
> **davidwashere2003 said:**
> this step worked like a charm:

```
sudo aptitude install sun-java6-jre sun-java6-plugin
```



Same here.  I'm still interested to know what was causing that problem above.

---

### Post by jomminum2 on 2009-06-16
> **uncr347ivenam3 said:**
> After agreeing to the license, I get this message

```
Do you agree to the above license terms? [yes or no] 
yes
Unpacking...
tail: cannot open `+479' for reading: No such file or directory
Checksumming...
1
The download file appears to be corrupted.  Please refer
to the Troubleshooting section of the Installation
Instructions on the download page for more information.
Please do not attempt to install this archive file.
```I'm running ubuntu 9.04.  It's a pretty fresh install.  Any suggestions?

i've the same problem...plzz

---

### Post by wulfgang on 2009-10-30
Thanks! Now I can go play runescape. :)

---

### Post by rolandw on 2009-12-04
well so far it works for me! it enabled it for all my browsers on ubuntu without any extra work

---

### Post by dutchglory on 2009-12-24
follow instructionds here:

[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)


to test, go here: [http://www.java.com/nl/download/help/testvm.xml](http://www.java.com/nl/download/help/testvm.xml)

[IMG]http://www.verwijs-pc.nl/shares/java.png[/IMG]

---

### Post by odzk on 2010-07-04
done all the steps,
no errors or whatsoever, after I restart firefox, i still dont have the java.
about:plugins, i still dont see the java.

its been almost 5 hours i havent still figure this out, just a stupid java. Well i dont have a choice, its looks like im going back to windows xp for browsing with java. geez.

---

### Post by zerwas on 2010-07-04
> **odzk said:**
> its been almost 5 hours i havent still figure this out, just a stupid java.

Because i have seen this thread directly above mine: Have a look if [this howto]("http://ubuntuforums.org/showthread.php?t=1517979") helps you.

---

