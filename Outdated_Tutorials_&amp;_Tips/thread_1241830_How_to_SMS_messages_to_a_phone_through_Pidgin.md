---
title: "How to SMS messages to a phone through Pidgin"
date: 2009-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by kevdog on 2009-08-16
Package Requirements

1. **Pidgin** - version 2.5.4 or higher
2. **A Gmail account** -- Gtalk as used as the IM Message <-> SMS text gateway
3. **Google Talk SMS Plugin** : [http://snarfed.org/space/google_talk_sms+pidgin+plugin](http://snarfed.org/space/google_talk_sms+pidgin+plugin)

Service only known to work within United States.  I know of no known incidences were people located in other areas of the world are able to make this work.

**Optional Pidgin Character Counting Plugin** - To Give Character Count of SMS messages that should not eclipse 140 characters (Homepage: [http://dossy.org/2008/02/debian-package-of-character-counting-plugin-for-pidgin/](http://dossy.org/2008/02/debian-package-of-character-counting-plugin-for-pidgin/))
- Deb File - [http://static.panoptic.com/pidgin/pidgin-convcharcount-plugin_2.3.1-1_i386.deb](http://static.panoptic.com/pidgin/pidgin-convcharcount-plugin_2.3.1-1_i386.deb)

**Setup**
**1. Gmail Account** -- Ensure that in the Gmail Settings that SMS messaging is enabled.  This is located within: Settings->Labs->Text Messaging (SMS) in Chat.

**2. Ensure Pidgin is installed**  
If you haven't installed Pidgin this can be done by:
```
sudo aptitude install pidgin
```
I will leave the details how to add your individual gmail account into pidgin to the reader.  It should be self explanatory.

**Installation of Plugins:**
**1. Google Talk SMS plugin :** Download the plugin ([http://snarfed.org/space/google_talk_sms.pl](http://snarfed.org/space/google_talk_sms.pl)) and place it within the ~/.purple/plugins folder.  If you do not have this directory tree, you will have to create the appropriate directories and place the perl plugin within this directory.  I would verify the permissions on this file and ensure they are at least executable by the user.  I changed the permissions on my file to 755.  This can be done via

```
chmod 755 ~/.purple/plugins/google_talk_sms.pl
```

**2. Optional Character Counting plugin** - Download the plugin .deb file: [http://static.panoptic.com/pidgin/pidgin-convcharcount-plugin_2.3.1-1_i386.deb](http://static.panoptic.com/pidgin/pidgin-convcharcount-plugin_2.3.1-1_i386.deb)  This may be installed via the following:

```
sudo dpkg -i pidgin-convcharcount-plugin_2.3.1-1_i386.deb
```

The are other methods to install this plugin additionally if you are interested in compiling pidgin from source or mtn: [http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

**Activating the plugins:**
The plugins must be first activated within Pidgin prior to be able to utilize their functionality.  This may be accomplished by first enabling the plugins:
Pidgin->Tools->Plugins->Google Talk SMS (Make sure this is checked)
Pidgin->Tools->Plugins->Conv. input chars count (Make sure this is checked)

**Adding a cellular phone to use:**
Pidgin->Buddies->Add Buddy
The format for adding a phone number is the following:
+1xxxxxxxxxx@sms.talk.google.com (Where xxxxxxxxxx is the area code and phone number)

After adding the buddy, the name within the Buddy List will always be shown as Not Authorized, and there is no way to verify that the buddy is "Online" since communications are going through an IM-to-SMS gateway.  

**Windows Instructions:**
For those running a mix of Windows and Linux boxes as I do, this plugin can be used in Windows.  Additional requirements are installation of a perl interpreter.  This can be either through the installation of Active Perl ([http://downloads.activestate.com/ActivePerl/](http://downloads.activestate.com/ActivePerl/)) or through the installation of cygwin.  After installation of either the above the appropriate windows version of the script is placed within the %APPDATA%/.purple/plugins subfolder.  In some cases you may need to change the properties of this file to something like 744 to make it executable (YMMV).  The difference between the windows and linux versions of the plugins are the Linux CR/LF are converted to windows style CR/LF.  Ive included the windows version as this is not distributed on the original site.

---

### Post by wieman01 on 2009-08-16
Nice one, thanks, Kevdog.

---

### Post by venator260 on 2009-08-17
This will be nice when I'm at my parents house with no cell service. Thanks kevdog

---

### Post by kevdog on 2009-08-17
Because of Google's restriction with their SMS-IM gateway, the service is only available in the United States for right now.  This is a google limitation and not a limitation of either Pidgin or linux.

---

### Post by MetalMusicAddict on 2009-08-23
Seems like Google has found out about this little workaround. Isn't working for me or other folks using the plugin from the original authors site. But, if you have an AOL (or ICQ) screenname, you can do it. Format is about the same just shorter: +1xxxxxxxxxx. Documented on the Pidgin site also: [http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#CanIsendSMSmessages](http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#CanIsendSMSmessages)

---

### Post by kevdog on 2009-08-23
Yea 

About a day after I wrote this thread -- Gmail cut off the ability of third party apps to forward IM's through their gateway.  What a bummer!!

---

### Post by go_beep_yourself on 2009-09-02
Seems to be working great, Thanks! Now I can send sms on yahoo, aim, icq, and gmail. I wonder if this works from my jabber account as well. I don't use Skype because they charge for what you can do for free, and I'm still looking into Google Voice. Info is in my blog :popcorn:

---

### Post by kevdog on 2009-09-02
Interesting how you made this work since gmail cut there service to third party providers.

---

### Post by mdwittenberg on 2009-12-21
So wait, is this working for other people or not? The author seems to say in post #6 that it no longer works, but then someone after him says that it does.

For me, I've installed the plugin, activated it from the plugin menu, and no it doesn't work.


Any suggestions?

---

### Post by rocuan on 2009-12-22
Only works with AIM (AOL Instant Messanger) or ICQ
so unless you have an account with either of these your SOL

Haven't found an easy solution, other than build a gateway, so I used the web YIM
[http://webmessenger.yahoo.com/index.php](http://webmessenger.yahoo.com/index.php)
then logged out & back into pidgin to get the response.  
ugly hack but I only needed to send a few SMS.

Let us know if you find a *real* solution

---

### Post by go_beep_yourself on 2010-07-08
It works for me in Linux but not Windoze. I didn't use any of the files from here. I downloaded them directly from the site they come from.

For now, I'll just be using the gmail in Firefox to send sms in Windoze.

---

### Post by go_beep_yourself on 2010-07-08
And I had already compiled the character counter a long time ago. I put the C file in the pidgin source directory to compile it.

---

### Post by go_beep_yourself on 2010-08-25
It works from Linux for me and not windows. In windows, I use either aim or yahoo or through the google voice and gmail interface. Are you using Windows. Shame on you.

---

### Post by ProfStosh on 2011-05-29
I can confirm that the sms plugin works for Ubuntu 11.04 x64.  I couldn't get the character counting compiled properly. I was probably missing packages.

---

### Post by cdizzle on 2011-06-08
Just followed the instructions, and I can confirm this works in debian testing, 32-bit. With character counting, too!

Thanks!

EDIT: used the .deb package for character counting plugin

---

### Post by MarkReaves on 2011-07-02
Well for Windows this does not work, seems the windows zip file may be corrupt? Not yet tested on Ubuntu.

However for Character counting this has been tested on Windows and seems to work:
[http://dossy.org/2007/10/character-counting-plugin-for-pidgin/](http://dossy.org/2007/10/character-counting-plugin-for-pidgin/)

---

