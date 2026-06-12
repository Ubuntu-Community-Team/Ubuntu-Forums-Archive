---
title: "How-To Install Click, Speak, a Web-page Reader (Text-to-Speech) Firefox Extension"
date: 2007-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by jackn on 2007-02-17
This is a minor how-to on *[Click, Speak]("http://clickspeak.clcworld.net/index.html") *, a Firefox text-to-speech (TTS) extension that can read out web pages.

The extension is extremely user-friendly: you only need to click one of three icons to have a highlighted web page segment read out, to have the whole page read out or to stop the reading.
*Click, Speak* is available for Windows, Mac and Linux environments. It was written by Charles L. Chen. who has kindly made it both free as in beer (free) and free as in speech (open-source).

A site dedicated to *Click, Speak* can be found at: [http://clickspeak.clcworld.net/index.html](http://clickspeak.clcworld.net/index.html).

**[FONT="Comic Sans MS"]_Why Click, Speak?_[/FONT]**
To me, it is fun to use when I'm cooking or cleaning. While I can't read web articles then, I can listen to any article I like, using wireless earphones, and *Click, Speak*. 

*Click, Speak*'s author, Charles L. Chen, cites the benefit for those who wish to learn foreign languages, as there are voices in different languages. The *Click, Speak* extension allows learners to listen to the spoken sounds of any text on the web.

**_[FONT="Comic Sans MS"]Installation[/FONT]_**
While the author provides a detailed installation [guide]("http://clickspeak.clcworld.net/installation.html"), I thought that system differences called for a specific guide for Ubuntu users. In addition, I've made some mistakes along the way. Hopefully, this mini-how-to will spare others the trouble - it's an easy install.
I'm running 32-bit Ubuntu Edgy Eft.

a. Install Firefox - Firefox is installed by default in Ubuntu Edgy Eft. 

b. Install the Java plugin for Firefox, if you don't have it yet. Instructions for Ubuntu at:
[How to install J2SE Runtime Environment (JRE) v5.0 with Plug-in for Mozilla Firefox]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v5.0_with_Plug-in_for_Mozilla_Firefox")
You should be able to check your Java plugin with [any old Java applet]("http://www.phy.ntnu.edu.tw/ntnujava/index.php?topic=49") on the web.

c. Symbolic link directing Firefox to the Java plugin - At this point, you should have a symbolic link in your ~/.mozilla/firefox/ywnocaac.default/ directory: *libjavaplugin.so* pointing to /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
(In my case, it does so through yet another symbolic link: etc/alternatives/firefox-javaplugin.so. I don't know why this is so.) 
To verify this link, launch the terminal (Applications -> Accessories -> Terminal in Gnome).
In all of the following code, it's best to use TAB completion in the terminal. This prevents typos.
```
cd ~/.mozilla/firefox/ywnocaac.default
ls
```
Now, long list the symlink which you should find in the previous listing:
```
ls -l libjavaplugin.so
```
If it links to etc/alternatives/firefox-javaplugin.so, long list this latter link:
```
ls -l etc/alternatives/firefox-javaplugin.so
```
If all's well, the latter link should point to /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so, as desired.
It seems to me that if you have the Java plugin in Firefox working, you should have this symbolic link. If you don't have the symbolic link, I'd check again whether the Java plugin is working (step b).
The Mozilla site [instructions]("http://plugindoc.mozdev.org/faqs/java.html#Linux"), [referred]("http://clickspeak.clcworld.net/installation.html") to by Chalres L. Chen, call for a symbolic link called *libjavaplugin_oji.so*, * but the above Ubuntu default, without the _oji extension, works*.
Bottomline, you only need to verify the existence of the above link. It should be there if you have successfully installed both Firefox and the Java plugin. You needn't do anything else.

d. Download and install the speech engine: [CLC-4-TTS to FreeTTS Interface 1.2]("http://clickspeak.clcworld.net/downloads.html"). 
Careful, while this is a Java archive (.jar file extension), the downloader suggests using 'file-roller' to unpack this as a tarball.
Do *not* open this archive from the downloader. Instead, save it (the default desktop option is fine). Now, from the terminal, decompress the archive:
```
sudo java -jar clc4tts_freetts_installer_1.2.jar
```

The 'sudo' is essential, as the installer will stop without the necessary permission override that a superuser status affords.

The files will unpack and self-install. To verify that they have properly installed:
```
ls /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/
```

Among other files and directories, you should see *META-INF* or *panelsOrder*. A complete list of the files that ought to be there can be had by right-clicking the downloaded archive on your desktop and opening it with 'Archive Manager'.


e. Download and install [CLC-4-TTS Suite with CLiCk, Speak - Bundle Pack 1.2 (Firefox extension)]("http://clickspeak.clcworld.net/downloads.htm") 

From the downloader dialgue box, save it to the desktop.
Next, (having started Firefox if it's not running) click File menu -> Open File. Browse to the file you have just downloaded to the desktop.
Click the 'Install now' button.

This will install a new *Click, Speak* toolbar in your browser. You can place the three *Click, Speak* icons elsewhere, and eliminate this chunky toolbar.

Last, but not least, make sure your browser is set to use the FreeTTS speech engine: Tools -> CLC Speak TTS selection -> Use FreeTTS.

_**[FONT="Comic Sans MS"]Uninstall[/FONT]**_
Both the speech engine and the Firefox extension can be easily unistalled. The .jar archive also installs an uninstall file to the same folder, and it calls your attention to it at the end of the install. The Firefox extension uninstalls easily by going to Tools -> Add-ons in Firefox.

[B][U][FONT="Comic Sans MS"]
Using *Click, Speak* and Heads-up[/FONT][/U][/B]

*Click, Speak* is a cinch and a pleasure to use. See brief [instructions]("How to use, three easy icons: a link http://clc4tts.clcworld.net/clc-clickspeak_doc.html").

*Click, Speak* takes a few seconds to launch. Wait.

Contrary to an audio player like Realplayer, say, the extension is Firefox-integrated. It is therefore strictly linked to the page displayed. If you open a new tab, or someone else does, the reading stops...

If it doesn't work for some reason, there is no error message. After a few seconds, you can safely conclude that something is wrong.

I'm available for questions. Feel free to post [here]("http://ubuntuforums.org/showthread.php?t=324120"), where I've linked to this 'how-to'. I don't feel very knowledgeable, but I'll be happy to try and give a hand with simple install issues.

Hearty thanks to Charles L. Chen, the author of *Click, Speak*, for writing it and for the kind, prompt help he is willing to provide [by e-mail]("http://clickspeak.clcworld.net/contact.html").

---

### Post by Tahir on 2007-03-09
I have been looking for something like this for a while when using windows.  Just my luck that when I was not looking for it did I find it.  Anyway, most people will have had gnu's java as the default java virtual machine to use.  I know this because I had a terrifying message when executing:

```
sudo java -jar clc4tts_freetts_installer_1.2.jar
```

Therefore I executed:

```
sudo update-alternatives --config java
```

and chose Sun's java. Then I executed the first thing and it worked.

---

### Post by Tahir on 2007-03-09
I have tried it out but I dont find it very impressive, I will try orca and let you know how it goes.

---

### Post by brahmaforces on 2010-03-04
Hello all:

I have spent a few hours trying to debug this but it is still not working. I have java running on my firefox on Ubuntu Studio 9.1. I see the 3 click to speak icons. I also have firevox installed. However upon clicking these icons no sound happens. Festival is working for me, however it does not read from the browser. I would love to have this work for me. Any idea why everything is installed correctly and no sound is coming, ie no text to speech. Please help...:popcorn:

---

### Post by gare on 2010-03-16
TTS - Text to Speech 

Try Google Chrome for Linux 

[http://www.google.com/chrome](http://www.google.com/chrome)

Extensions > Chrome Page Reader

install took less than a minute.

Not sure of quality of this reader vs others but appears cool!

---

### Post by wojox on 2010-03-16
Doesn't work. :-(

---

### Post by vampirefo on 2010-03-16
Old tutorial but still works thanks.

---

### Post by onepostdan on 2010-05-02
I actually updated Click, Speak for the latest FireFox. I emailed the  click, speak dude but he never replied, I think it may be semi abandoned.  Here's a working xpi:  [http://rapidshare.com/files/382768351/clc_clickspeak_v1.6.1.xpi.html](http://rapidshare.com/files/382768351/clc_clickspeak_v1.6.1.xpi.html)

The  issue was that cross package scripting is no longer allowed due to  security issues, so i just threw everything into a single package.

---

### Post by xtracool_protik on 2010-07-07
Hey onepostdan,
 If u r still following this thread here is the error message by rapidshare, I think u need to upload it somewhere else:

> This file is neither allocated to a Premium Account, or a Collector's Account, and can therefore only be downloaded 10 times.

This limit is reached.

To download this file, the uploader either needs to transfer this file into his/her Collector's Account, or upload the file again. The file can later be moved to a Collector's Account. The uploader just needs to click the delete link of the file to get further information.


---

### Post by macbeth76 on 2010-07-15
Found the link to the extension on [http://support.mozilla.com/en-US/forum/1/492350](http://support.mozilla.com/en-US/forum/1/492350)

---

