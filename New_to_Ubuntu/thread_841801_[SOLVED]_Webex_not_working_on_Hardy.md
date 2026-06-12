---
title: "[SOLVED] Webex not working on Hardy"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by HDave on 2008-06-26
I recently upgraded from Gutsy to Hardy and somewhere along they way I broke webex.

Whenever I go to start the meeting manager it says 'downloading' and the progress bar goes to 100% and then nothing!

I am using the sun 6 java plugin for firefox.  Webex's site says they support Ubuntu 7.04 and Java 1.5 so I should be ok.

Does webex work for anyone else on Hardy?  Any suggestions on how to track down the source of this problem?

---

### Post by HDave on 2008-06-27
I'll save everybody the ugly details of 1.5 hours on the phone with webex and a day of experimenting.  Suffice to say that the Webex meeting manager is a java app and is launched from firefox without a bash script.

So my .bashrc lines that read:

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.66
export PATH=$JAVA_HOME/bin:$PATH
```

didn't work.

Moving these two lines to my .profile did the trick.  Webex is back up and running and now I can see people's app shares...NICE.

The Webex folks say have limited support for Ubuntu 7.04, but that they will have 100% full support for Ubuntu with version 8.10.  Wish it was sooner, but it's still cool to see a huge commercial company paying us some genuine attention. :)

---

### Post by HDave on 2008-06-30
As another follow-up, I also found out *why* webex was broken with Java 1.5 on Hardy.  Webex requires libstdc++5.

So I reverted BACK to java 1.5 (from Sun) to test out and did a:

```
sudo aptitude install libstdc++5
```

and VIOLA it worked.  Much easier solution than migrating to Sun Java 6.

I figured this out from examining my JVM log files in ~/.java/deployment/log directory.  I was missing these log files until I enabled logging in Java via System->Preferences->Sun Java 5 Plug-in Contol Panel.

The error message in there was:

```
Exception in thread "Thread-572" java.lang.UnsatisfiedLinkError: /home/dvredenburgh/.webex/824/libatdv.so: libstdc++.so.5: cannot open shared object file: No such file or directory.
```

---

### Post by s_baramov on 2008-07-01
Installing the libstdc++5 fixed the problem under Java 6 as well.

---

### Post by branbuntu on 2008-07-02
Thanks for this recent post; I've been struggling with the WebEx connection since installing 8.04.


I installed jre-1_5_0_15-linux-i586.bin from Java website then ran,

aptitude install libstdc++5

I created a symbolic link in my firefox plugins directory:

ln -s  /home/subran/jre1.5.0_15/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox-addons/plugins/libjavaplugin_oji.so

and then logged into my webex session.  The client downloaded successfully and I was viewing the session - at this point, I don't see the "shared application" from the host working yet...

---

### Post by lorubenet on 2008-08-06
Same problem here. I complained few months ago to WebEx and they basically didn't reply (I had bugged them before with the poor sound quality... and then they did do something... (propose to upgrade to beta for testing, tja..) finally we do the sound via skype)...
Anyway... 
I do have libstdc++5 installed in my system, and I don't see the Exception reported by HDave (I have as well libstdc++6, libstdc++6-4.1-dev, libstdc++6-4.2-dev; do they interfere??).
I can show my desktop to other attendants but I cannot see theirs. The window is white. My mouse clicks are (were, I tried a couple of long ago) transferred to the remote machine if remote control was enabled.

The only error I see in the file HDave reports is:
[jmeetingclient] HandleConferenceResource i=0 Error Happened.
[jmeetingclient] HandleConferenceResource i=1 Error Happened.

googling there was no help for me. 

The webex faq says that what's needed is:
    * Kernel: 2.4.21 or above
    * X Lib: X11R6 or above compatible
    * C++ Lib: libstdc++ 5
    * Desktop Environment: XFce 4.0 or above, KDE, Ximian, Gnome
    * GDK/GTK+ version: 2.0 or above
    * Glib: 2.0 or above
    * Sun Java 1.5 or above
    * OSS Interface (for Audio)
    * Firefox 1.5 or higher or Mozilla 1.7 or higher
    * JavaScript and cookies need to be enabled
    * 56K or faster Internet connection 

So I guess I miss some libs from there. Strangely enough it was working on Feisty. I investigated a bit on the GDK/GTK+ and Glib, but I there are many different options there when I do apt-get install glib<TAB><TAB> ... so I don't know what to try. Could you guys report which of those libraries you have installed on your system so I could see the differences?

Any other ideas?

Thanks!

---

### Post by HDave on 2008-08-06
> **lorubenet said:**
> Could you guys report which of those libraries you have installed on your system so I could see the differences?

I have libstdc versions 5 & 6 so it can't be that.

Check your "java -version" -- on my system it reports:

```
java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) Server VM (build 1.5.0_15-b04, mixed mode)
```

Oddly enough it could be a video card & driver issue.  Other that this I am out of ideas...sorry.

---

### Post by lorubenet on 2008-08-27
Tja, I have exactly the same java version.

I put as well this lines in .profiles, .bash_profiles and .bashrc with no luck...
There must be a stupid trick I'm missing... 
Thanks anyway!

---

### Post by thebluestreak on 2008-09-03
works great for me with hardy heron

i simply edited .profile to reflect:

export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06
export PATH=$JAVA_HOME/bin:$PATH

and did an

sudo apt-get install libstdc++5

opened firefox 3 from a terminal to avoid logging in to make changes effective and it loaded up immediately.  java app used to just hang at 65%

---

### Post by lorubenet on 2008-09-11
OK issue solved...

I had done everything fine... the only problem left was the version of WebEx our server was using. Now they updated it and it works fine.

Thanks for all your help!

---

### Post by atownley on 2009-01-06
Just to note that this fix is only for the x86 and not amd64 versions of Ubuntu.  WebEx will not currently work (as of today) with amd64 (8.04) and Firefox 3.

Using the 64-bit Java plug-in from [https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html), everything seems to go fine, however WebEx's JNI library libatdv.so is potentially downloaded without checking the appropriate system architecture.  WebEx silently dies with the following:

```
Exception in thread "Thread-13" java.lang.UnsatisfiedLinkError: /home/ast/.webex/824/libatdv.so: /home/ast/.webex/824/libatdv.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(Unknown Source)
	at java.lang.ClassLoader.loadLibrary(Unknown Source)
	at java.lang.Runtime.loadLibrary0(Unknown Source)
	at java.lang.System.loadLibrary(Unknown Source)
	at JNRW.<init>(JNRW.java:33)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at java.lang.Class.newInstance0(Unknown Source)
	at java.lang.Class.newInstance(Unknown Source)
	at jDocView.CreateDocViewUI(jDocView.java:470)
	at jDocView.PDNewInstance(jDocView.java:3797)
	at MeetingClientFrame.<init>(MeetingClientFrame.java:271)
	at jmeetingclient.connectToMeeting(jmeetingclient.java:444)
	at jmeetingclient.init(jmeetingclient.java:394)
	at JDownload.run(JDownload.java:233)
	at java.lang.Thread.run(Unknown Source)
```

Is there someone with WebEx support who can ask them about this?  Is this part of the support they're promising for 8.10?

It would be very useful if this could be fixed sometime in Q109.

Cheers,

ast

---

### Post by hector2 on 2009-04-03
Hello,
Did anybody test webex on firefox3+ubuntu8.10 ? Is is true that it is now fully supported ? (i have a 64 bits ubuntu)

Moreover, is there a mean  to verify it works in the case we are not member ?

Thanks a lot

---

### Post by HDave on 2009-04-03
I tried it on a clean install and it didn't work without the hacks mentioned above....

---

### Post by hector2 on 2009-04-06
Thanks a lot !
euh, There are several tricks above...Do you know those which are absolutely necessary ? 
Should they work on 64 bits ?

Thanks again ...

---

### Post by johnkaplantech on 2009-08-31
This also applies to 9.0.4 jaunty. You have to set JAVA_HOME and install libstdc++5 or webex just downloads it's plugin and sits there forever. Once I installed libstdc++5 as instructed above, webex started working.

Thanks,
- John

---

### Post by zzyzx1 on 2009-09-01
johnkaplantech, i have read the thread and tried the hack and am able to connect but I get a a blank "share desktop" screen. The only think I can think of is the set JAVA_HOME you mention, can you elaborate on that one, how to?

Thanks!

---

### Post by odony on 2010-11-02
> **atownley said:**
> Just to note that this fix is only for the x86 and not amd64 versions of Ubuntu.  WebEx will not currently work (as of today) with amd64 (8.04) and Firefox 3.


Just to confirm that Webex is still not working on Ubuntu 64 as of today on Lucid or Maverick. Probably not a top priority for them (I thought I saw somewhere they support Ubuntu 100%?). 

You're not out of luck if you can install a 32-bit browser and Java plugin on your 64-bit Ubuntu.

More details:

At least 2 important webex shared libraries fail to load on a 64-bit java plugin:
   - libatdv.so
   - libdbr.so (apparently used for audio input/output)
You can see similar Java exceptions by enabling the Java console:
java.lang.UnsatisfiedLinkError: ~/.webex/926/libatdv.so: ~/.webex/926/libatdv.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
java.lang.UnsatisfiedLinkError: ~/.webex/926/libdbr.so: ~/.webex/926/libatdv.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)

Possible solutions until the Webex guys fix it (number 1 worked for me):

1. Install a 32-bit version of at least firefox and the java plugin, but you need to know your way with the command-line and dpkg. I used this thread for starters: [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435) (using Hardy option in installl script), and then processed manually for the missing pieces looking at the script source for the links and package names etc. Got it to work and webex behaves fine so far on my Firefox 3.2.3 + Java 6 32bit.

2. Or try to run Windows' Firefox and Java through Wine (haven't tested this one, seems it doesn't solve everything... You can find lots of howtos and info in google. E.g at the bottom of this page:
[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#32-bit%20Firefox%20and%20plugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#32-bit%20Firefox%20and%20plugins)

3. Or just run your browser/java inside a 32-bit VM (Ubuntu, Windows) and all should be fine, as long as the performance and setup works for you...

---

### Post by HDave on 2010-11-02
Is anyone able to share their Ubuntu desktop with Webex>

---

### Post by odony on 2010-11-02
Following-up to my previous post, here's the quick and dirty log of what I did to get "solution 1" running on my Lucid laptop. I was saving the log in case I need to redo it, might as well post it for the record:

Not all commands are to be executed in the same directory, you need to know your way with command-line and use common sense, sorry.
And for those wondering why we still need this: in my case I need to run a full Webex session and Webex's Java Applet is still broken on Ubuntu 64bits, trying to load 32bit shared libs.
```

 wget [http://home.comcast.net/~ubuntume/ff32_3in1_6294.tar.gz]("http://home.comcast.net/%7Eubuntume/ff32_3in1_6294.tar.gz")
 tar xvzf ff32_3in1_6294.tar.gz
 ./3in1  (choose Hardy + no browser, no flash; no java - but some packages will still fail to install...)
 
 #finish installing ff32bit
 wget -c "http://home.comcast.net/~ubuntume/firefox32-3.0.1-ubuntu_7.10-8.04_amd64.deb"
 wget -c "http://fr.archive.ubuntu.com/ubuntu/pool/main/x/xutils-dev/xutils-dev_7.2.ds2-1ubuntu1_amd64.deb"
 sudo dpkg -i xutils-dev_7.2.ds2-1ubuntu1_amd64.deb
 sudo dpkg -i firefox32-3.0.1-ubuntu_7.10-8.04_amd64.deb 
 
 #so far should work on lucid, start it via menu or:
 /usr/local/bin/firefox32-3 
 
 # now install java 32bits
 wget [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/ia32-sun-java6-bin_6.22-0ubuntu1~8.04.1_amd64.deb]("http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/ia32-sun-java6-bin_6.22-0ubuntu1%7E8.04.1_amd64.deb")
 wget [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6.22-0ubuntu1~8.04.1_all.deb]("http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6.22-0ubuntu1%7E8.04.1_all.deb")
sudo dpkg -i sun-java6-jre_6.22-0ubuntu1~8.04.1_all.deb ia32-sun-java6-bin_6.22-0ubuntu1~8.04.1_amd64.deb 
 ln -fs /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib32/firefox32/plugins/
 sudo chown -R `whoami` /usr/lib32/firefox32/plugins/
 
 # Java should now work if you restart ff
 /usr/local/bin/firefox32-3 
```
Hopefully this will save someone some trouble...

---

