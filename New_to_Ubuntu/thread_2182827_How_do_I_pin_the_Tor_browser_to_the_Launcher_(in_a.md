---
title: "How do I pin the Tor browser to the Launcher (in addition to Firefox)?"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by Jim_Granite on 2013-10-22
EDIT: [Jump to post #22]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610") to get a good summary of what the problem is:
> 
The Unity launcher and Dash use .desktop files to generate their  entries. Different .desktops represent different entries (even if they  have the same icon). So separating Tor and Firefox is a matter of  creating separate .desktop files. 

The Vidalia Control Panel runs a customized version of Firefox found in  .../tor-browser_en-US/App/Firefox. Since this customized version of  Firefox is executed directly, and not through a .desktop, Unity  automatically ties it to the default Firefox .desktop, making the two  processes occupy the same entry in the launcher. The same thing happens  when you simply run 'firefox' from the terminal.

However, running the firefox executable in  .../tor-browser_en-US/App/Firefox/firefox doesn't run the custom Firefox  version that is the Tor Browser, it simply runs normal Firefox as if  you had typed "firefox" into a terminal (you can check this by looking  at the version number of the window that pops up - Tor uses FF 17 ESR).  This is because Firefox uses 'profiles' to separate the custom settings  each user/program has created, and running .../App/Firefox/firefox by  itself will simply use the default profle (the one you use in normal  Firefox). 

So we have to force .../App/Firefox/firefox to use the tor profile.




QUESTION: How do we add a separate launcher onion icon for the [Tor Browser Bundle]("https://www.torproject.org/projects/torbrowser.html.en") on Unity Ubiquiti 13.10?

On all other operating systems, including Windows & on RHEL6, when you start the Tor Browser Bundle, two things happen.
1. The Tor Browser Bundle browser is clearly separate from the Firefox browser icon (so that you don't have to constantly keep checking which browser you're using)
2. The Vidalia control panel has its own purple-and-green onion icon that goes to green when it's done connecting you to the Tor  nodes, or to white with a red x when you're not connected properly. 
In addition, you can always right click on that Vidalia settings onion icon to change settings (e.g., to exit the process so that you may start anew, since you can't have more than one Vidalia process running at a time).

Yet, on the Ubuntu 13.10 Launcher, the Tor Browser Bundle is inexplicably melded into the Firefox icon (which makes absolutely no sense) - and - there is no Vidalia control panel icon, by default.

Clearly, the Tor Browser Bundle is a wholly different beast than Firefox, comprised of Vidalia, Polipo, and Firefox. Everything about the Tor Browser Bundle is different from Firefox, from the way Tor is installed, to the way it's launched, to its setup, and to the way it's used, and to the way it's reset during use (to gain new identities).

Yet, for some strange reason, when I launch the Tor Browser Bundle, it's icon is inexplicably MERGED onto the Firefox icon

This is bad for many reasons, not the least of which is you can't START Tor from the Firefox icon, nor do you get any access to the Tor-specific Vidalia setup commands, nor can you tell via the lack of the onion icon color and shape what's going on.

** But, the worst problem is that, on Ubuntu 13.10, you can never trust which browser you're bringing up! **

What this means, in actuality, is that a user who wishes to remain private (for whatever reason), will inevitably type a URL into the wrong browser, since you have to doublecheck every single time you type in a URL which browser you're using. At some point, the user will make a mistake - and - depending on how badly they wanted to remain anonymous - they have to scrap their login (at the very least) on all accounts on the Internet - or to move out of the country (again, depending on the person's reasons for wanting privacy). Without getting too outlandish, I can see cases where their life would be in danger, simply because Ubuntu 13.10 makes it difficult to distinguish between the two Firefox implementations.

So, my simple question is:
Q: **How do I create an onion launcher icon pinned to the Ubuntu Launcher for the Tor Browser Bundle wholly separate from Firefox **(*similar to how it works on all other operating systems*)?

$ alias tor='ibus exit; /usr/local/sbin/tor-browser_en-US/start-tor-browser &'
[ATTACH=CONFIG]247157[/ATTACH]

---

### Post by sha1sum on 2013-10-22
Yes, at some point the Tor browser icon on the launcher merged with the firefox icon. I also found that very annoying. However, Ubuntu is not to blame for that. It has to do with the Tor browser bundle. I use Ubuntu 12.04 and after some browser bundle update they (inadvertently?) changed it.

I guess this makes it impossible to lock Tor to the launcher, unless you edit the tor software yourself (not recommended unless you know what you're doing). That said, why would you really want to? The recommended procedure for using Tor is (as far as I know) to close all other applications, especially those that also require internet connection like firefox, and only then start the Tor browser. Then when you're done, you carefully close the Tor browser, and you start using other applications again. It's not as convenient but it's good security practice anyway.

---

### Post by Frogs Hair on 2013-10-22
I downloaded the bundle and tried an experiment creating a launcher via ala carte/main menu ,but it didn't work very well. Strangely enough the icon appeared in dash but not in the main menu application and when using the launcher I couldn't get passed the password dialog. For the launcher command browsed directly to the tor start up file.

---

### Post by Jim_Granite on 2013-10-22
> **sha1sum said:**
> It has to do with the Tor browser bundle.
Now that is interesting because I don't have the background in Ubuntu to know any better. 
All I know is last week I was on RHEL6 and Win7 and the TBB icon on the start menus is definitely different (as it should be, IMHO).
I'm certain I was up to date because, as you know, Tor checks, by default, and let's you know you're protected in the default home page.

So, it doesn't "appear" to be a Tor thing.
Maybe it's a Ubuntu thing that spans releases?

> **sha1sum said:**
> That said, why would you really want to?

My use model is to start Tor, and use it to be anonymous while browsing certain sites. 
At the same time, I'm browsing with Firefox at other sites where I don't wish to be anonymous.
(I'm not hiding from a state-sponsored agency such as the NSA.)

So, I'm basically using Tor as a simple "proxy". 

My use model, with respect to the Tor icon, is:
a) I click on that (purple) onion to start Tor.
b) This, as you know, takes time to turn green (if, at any time, it has a red X, you know something is wrong).
c) I right click on the (green) onion to change "identities" (i.e., to change the anonymity path)

Very often, after visiting a few sites, I kill the Tor browser, which doesn't kill Vidalia.
Since Vidalia is still running, I can't start another Tor session, but, that's no problem, because ...
d) I right click on the (still green) icon to kill Vidalia graphically (and then I go back to step "a" above).

This is the use model I've been employing on Windows & RHEL6 for years. 
It's essentially the same use model we employ for every other program that we often use from our Launcher.

> **sha1sum said:**
> The recommended procedure for using Tor is (as far as I know) to close all other applications.

While this may very well be true, why does Windows 7 and RHEL6 not enforce a single Firefox icon?

Plus, there is nothing in the setup that prevents you (or even warns you) that you're running Firefox & Tor at the same time.
In fact, the Firefox icon simply shows that you're running two (or more) firefox processes. 
So, if it was a warning mechanism, it's *a really bad implementation* of one (which makes me doubt that's the reason).

Even if it were a warning mechanism, [B]we still would want a launcher so that we could START the Tor browser. 
Right?

[/B]> **Frogs Hair said:**
> tried an  experiment creating a launcher via ala carte/main menu
Thank you for trying that experiment, and for posting the graphical results.
I don't yet know enough how to create a launcher (which is why I openened this post).

For me, the "tor" command is aliased to the following:
$ alias tor='ibus exit; /usr/local/sbin/tor-browser_en-US/start-tor-browser &'

Note: The "ibus exit" is to work around a Ubuntu 13.10 bug, and the "start-tor-browser" is the standard Tor script (which goes one level deeper in the hierarchy).

All I'd want to figure out is how to create my own launcher that performed that alias above. 
Of course, it wouldn't have the right-click niceties that the RHEL6 & Win7 Tor icon have; but it would be better than having to get out of the graphical environment to open an xterm to then start Tor (and then to being able to manage the TOR outside of Firefox, which is really what it is).

Q: Since this seems to be a real bug, do you think we should report it to Canonical as such?

---

### Post by sha1sum on 2013-10-23
> **Jim_Granite said:**
> Now that is interesting because I don't have the background in Ubuntu to know any better. 
All I know is last week I was on RHEL6 and Win7 and the TBB icon on the start menus is definitely different (as it should be, IMHO).
I'm certain I was up to date because, as you know, Tor checks, by default, and let's you know you're protected in the default home page.

So, it doesn't "appear" to be a Tor thing.
Maybe it's a Ubuntu thing that spans releases?

Well, about a year ago I was using Tor with Ubuntu (12.04) and it did have two separate icons in the launcher for firefox and Tor. However at some point an update in the TBB changed it to the current situation. But if you say that in other linux distributions it does work correctly, then maybe it is indeed some kind of incompatability.

---

### Post by Jim_Granite on 2013-10-23
> **sha1sum said:**
> if you say that in other linux distributions it does work correctly, then maybe it is indeed some kind of incompatibility.

There is absolutely no doubt that the latest TOR Browser Bundle on the latest RHEL6 just last week had two separate icons.
I'm new to Ubuntu, so I don't know how to file bug reports yet. 
Where do I look to see if there's already a bug filed against this?

---

### Post by Frogs Hair on 2013-10-23
Bug reporting Ubuntu :[https://launchpad.net/](https://launchpad.net/)

I downloaded tor again without trying to create a launcher and did get a separate icon, but the Firefox icon also became active when opening tor. In the main menu if installed the command to open FF is the following. ```
firefox %u
``` . I thought by linking the start-tor-browser script in a launcher command it wouldn't activate the default version of FF. This worked except for the password dialog problem.

---

### Post by Jim_Granite on 2013-10-24
> **Frogs Hair said:**
> Bug reporting Ubuntu :[https://launchpad.net/](https://launchpad.net/)
Thanks for that pointer. 
I'll search for an existing bug, and if I don't find it, I'll file it.
How does this sound as a concise, yet informative, title?
**"Lost functionality, Tor Browser Bundle functionality is both missing & mistakenly inexplicably associated with the Firefox icon"**

BTW, when I installed Launchpad, I was surprised to see that "it" clearly had its own icon! 
Just like the Tor Browser Button is supposed to have! :)
[ATTACH=CONFIG]247201[/ATTACH]
> **Frogs Hair said:**
> 
I downloaded tor again without trying to create a launcher and did get a separate icon, but the Firefox icon also became active when opening tor. In the main menu if installed the command to open FF is the following. ```
firefox %u
``` . I thought by linking the start-tor-browser script in a launcher command it wouldn't activate the default version of FF. This worked except for the password dialog problem.

I'm sorry, but I'm confused. 
You said when you installed the Tor Browser Bundle, you DID get a separate icon?
How? 
I didn't ever see a separate icon, and I installed the TBB from this web page:
[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

Are you saying that there is a specific workaround way to install TBB on Ubuntu 13.10 that doesn't exhibit the bug that the icon is merged with Firefox?
If so, can you show me what to do to repeat that result? Thanks!

---

### Post by Jim_Granite on 2013-10-25
Would someone just clarify where I can find a tutorial for making a separate icon in the Launcher for this command?
```
alias tor='ibus exit; /usr/local/sbin/tor-browser_en-US/start-tor-browser &'
```

Googling, I find this
 * [How to add a launcher]("https://help.ubuntu.com/community/HowToAddaLauncher") *
 * [How to create a custom launcher]("http://askubuntu.com/questions/78730/how-do-i-add-a-custom-launcher") * 
 * [Howto create Application launcher and add icon to Unity in Ubuntu 13.04 / 12.10 / 12.04]("http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/") *
 etc.

But they all seem dated since I'm on Ubuntu 13.10.
Plus, the kind folks above intimated that the custom launcher doesn't work (I think).

So, I wanted to try to create a custom launcher for that Tor command to see for myself.

Q: Where would you point me for a tutorial on creating a custom launcher for that Tor command on Ubuntu 13.10?

---

### Post by Frogs Hair on 2013-10-25
> [COLOR=#000000]You said when you installed the Tor Browser Bundle, you DID get a separate icon?[/COLOR]
[COLOR=#000000]How? [/COLOR]

The Tor bundle starts with the script from the folder regardless of where it is in the  home directory . I did get the onion icon by double clicking the start script but it also activated the Firefox icon in the Unity panel.

---

### Post by Jim_Granite on 2013-10-25
> **Frogs Hair said:**
> The Tor bundle starts with the script from the folder regardless of where it is in the  home directory . I did get the onion icon by double clicking the start script but it also activated the Firefox icon in the Unity panel.

I tried to test what you said above ... but, for some reason, even though the "start-tor-browser" script is clearly executable:
-rwxr-xr-x 1 foo foo 7325 Sep 19 12:05 start-tor-browser

When I double-click on it in Nautilus, it merely opens up in gedit.

What do I need to set so that doubleclicking on the default 'start-tor-browser' script actually executes the script?
[ATTACH=CONFIG]247237[/ATTACH]

---

### Post by 3rdalbum on 2013-10-26
The icon you're talking about in RHEL actually appears in the notification area, doesn't it?

Ubuntu has depreciated the Notification Area system since 2009 in favour of the newer (and better) Indicators system. I think you can still "whitelist" individual Notification Area icons so they will be displayed, or alternatively whitelist them all. Might be worth looking on Google for a howto, this is another hidden setting so it requires dconf-editor.

---

### Post by Frogs Hair on 2013-10-26
> What do I need to set so that doubleclicking on the default 'start-tor-browser' script actually executes the script?
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=247237&d=1382754172&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=247237&d=1382754172")

Enter the scripts properties and make it executable as a program under permissions and also make sure Nautilus is set to do so in preferences.

---

### Post by Jim_Granite on 2013-11-05
> **Frogs Hair said:**
> Enter the scripts properties and make it executable as a program under permissions and also make sure Nautilus is set to do so in preferences.

I'm going to give up on trying to workaround this bug since it's pretty clear that nothing is working.
I do appreciate the suggestions. They would work, if the bug didn't exist. 
For example, my permissions have been 777 for weeks now, and the problem isn't how Nautilus brings it up.

Anyway, as I'm certainly not knowledgeable enough to solve this bug on my own, or even to file the bug report adequately, I'll just live with it (like so many others) and wait for someone else to know more than I do in order to propose a viable workaround (that they've actually tested) or for the Unity team to realize the error and fix it in a later release.

Thanks for all the help. Is there a way to mark this as "give up" or "abandoned"?

---

### Post by Jim_Granite on 2013-11-07
It's pretty sad that Tor was never tested with Ubuntu, such that a dumb user has to figure out how to get a simple launcher icon to show up.

Anyway, proceeding (almost comically) forward, I did try to create the launcher icon using the onion icon that comes with the Tor Browser Bundle:
 /usr/share/app-install/icons/vidalia.png

I created the following desktop.tor file (from the firefox.tor file):
$ sudo cp /usr/share/applications/firefox.desktop /usr/share/applications/tor.desktop 
$ sudo vi /usr/share/applications/tor.desktop 
> 
[Desktop Entry]
Version=1.0
Name=Tor Browser Bundle 1
Comment=Tor Browser Bundle 2
GenericName=Tor Browser Bundle 3
Keywords=Internet;tor;browser;bundle;tbb
Exec=tor
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/usr/share/app-install/icons/vidalia.png
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;video/webm;application/x-xpinstall;
StartupNotify=true
Actions=NewWindow;

[Desktop Action NewWindow]
Name=Open a New Window
Exec=tor
OnlyShowIn=Unity;


But, when I executed "tor", nothing happened any differently than before:
$ alias tor='ibus exit; /usr/local/sbin/tor-browser_en-US/start-tor-browser &'
$ tor

The result was that the Tor/Vidalia process was still errantly associated with Firefox in the Unity launcher (which makes absolutely no sense).
In order to continue working around this bug, I ask for advice on why the desktop.tor above didn't bring up its own vidalia icon?

---

### Post by Jim_Granite on 2013-11-08
It looks like the whole problem is in Unity not having been tested, since the TOR people have closed the bug report 3 years ago:
 [Tor Ticket #3508]("https://trac.torproject.org/projects/tor/ticket/3058"): Vidalia indicator icon does not show up in Unity, in Ubuntu 11.04
> 
**Description**

             There is no Vidalia indicator icon in the top right corner of the screen  in Ubuntu 11.04 running the new Unity desktop environment. When you  click "Hide" in Vidalia, the window gets hidden but there is no way to  re-open it. When you try running Vidalia again it tries to start a new  process instead of opening the window of the existing process.

[LIST]
[*]       **Status**         changed from *new* to *closed* 
[*]       **Resolution**         set to *not a bug* 
[/LIST]
                    This is a problem with Unity, Vidalia handles its tray icon through Qt.
See this: [&#8203;https://bugs.launchpad.net/ubuntu/+bug/773307]("https://bugs.launchpad.net/ubuntu/+bug/773307")

[URL="https://bugs.launchpad.net/ubuntu/+bug/773307"]Apps are missing their tray icons in Unity 

I'm also trying this advice:
 [/URL][URL="http://askubuntu.com/questions/312692/howto-run-tor-and-vidalia-on-ubuntu-easily-browse-and-im-anonymously"]http://askubuntu.com/questions/312692/howto-run-tor-and-vidalia-on-ubuntu-easily-browse-and-im-anonymously
[ATTACH=CONFIG]247659[/ATTACH][/URL]

---

### Post by Jim_Granite on 2013-11-08
While all this work could have been avoided had the Tor Browser Bundle just worked propertly on Unity, I do have a use model now that seems to work, given that Vidalia now finally shows up (with the additional desktop work performed as described above).

So, now when I start tor, I at least finally get a Vidalia Control Panel (onion) icon in the launcher, which when right clicked, affords me control over the Tor network. 

There still is the problem that the browser is intimately associated with the Firefox icon, which is crazy, but, with the Vidalia icon finally showing up, at least I know when Tor is running, and, more importantly, I can control the relays. 

Most importantly, I can kill Vidalia by hitting the Vidalia Control Panel exit button, which is important since closing the browser doesn't kill Vidalia automatically, yet, restarting the browser without having killed Vidalia causes an error every time. So, you must kill Vidalia anyway, and having the Vidalia Control Panel show up on the launcher when Vidalia is running makes all the difference in ease of use (since it has a big fat red exit button, clear as day).

So, for now, I have a workaround use model that isn't horrendous, which is better than it was out of the box.
[ATTACH=CONFIG]247672[/ATTACH]

---

### Post by Jim_Granite on 2013-11-09
> **Jim_Granite said:**
> For now, I have a workaround use model that isn't horrendous

I'm not sure exactly WHAT I did to make the use model work, since I tried so many things.
To help others follow in my footsteps, I tried to reconstruct what I did, and I think it's the following:

** The first thing I did was to obtain the latest Tor Browser Bundle for Linux:**
```
TASK: Install tor browser bundle
READ: https://www.torproject.org/docs/tor-doc-unix.html.en
$ gunzip tor-browser-gnu-linux-x86_64-2.3.25-13-dev-en-US.tar.gz
$ tar -xvf tor-browser-gnu-linux-x86_64-2.3.25-13-dev-en-US.tar
$ cd ./tor-browser_en-US
$ ./start-tor-browser &
```

**The next thing was to choose where to place the Tor Browser Bundle:**
```
TASK: Move Tor TBB to where it belongs in the existing path:
$ echo $PATH
=> /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
$ sudo mv /tmp/tor/tor-browser_en-US/ /usr/local/sbin/.
$ cd /usr/local/sbin/.
$ sudo ln -s ./tor-browser_en-US/start-tor-browser tor
$ cd
$ which tor
=> /usr/local/sbin/tor
```

**When the startup script was executed, I worked around the bug where the browser wouldn't accept keyboard input:**
```
BUG: Tor Browser wont' accept any inputs from the keyboard
SOL: Run "ibus exit" before starting tor (or remove ibus)
READ: http://askubuntu.com/questions/361238/ibus-incompatible-with-tor-browser-in-13-10
$ ibus exit
$ sudo apt-get remove ibus
$ vi ~/.bash_aliases
ADD:
alias tor='ibus exit; /usr/local/sbin/tor-browser_en-US/start-tor-browser &'
```

**The worst use-model bug was there was no control over Vidalia visible and present, so I worked around that bug:**
```

PBLM: The problem is that killing the tor browser doesn't kill Vidalia; and
Vidalia won't restart if it's already started; so you're constantly killing
Vidalia; which is easy from its control panel; but a pain from the shell:
$ ps -elfww | grep vidalia
$ kill -9 [PID]
SOL: Create a launcher icon for Vidalia so that starting tor brings it up.
http://ubuntuforums.org/showthread.php?t=2182827
noobrescue.com/blog/vidalia-detected-that-the-tor-software-exited-unexpectedly

To create a Vidalia Control Panel launcher icon when the TBB runs:
$ cd /usr/share/applications
$ sudo cp firefox.desktop tor.desktop
$ vi tor.desktop

[Desktop Entry]
Version=1.0
Name=Tor Browser Bundle 1
Comment=Tor Browser Bundle 2
GenericName=Tor Browser Bundle 3
Keywords=Internet;tor;browser;bundle;tbb
Exec=tor
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/usr/share/app-install/icons/vidalia.png
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;video/webm;application/x-xpinstall;
StartupNotify=true
Actions=NewWindow;NewPrivateWindow;

[Desktop Action NewWindow]
Name=Open a New Window
Exec=tor
OnlyShowIn=Unity;
```

**The remaining use-model bug is that the Tor Browser is, inexplicably, merged with the Firefox browser (which it has nothing to do with):**
```

BUG: Tor browser is inexplicably linked to the Unity Firefox browser icon.
SOL: None known. This is a serious usability bug.

```

*** STARTUP USE MODEL: ***
It is currently impossible (for me, anyway) to start the Tor Browser from a Unity launcher, since the associated launcher only starts Firefox.
To start the Tor Browser, I open an xterm, and type "tor", which runs the alias, which kills the ibus, and runs the supplied start script.
With the workarounds implemented above, that brings up Vidalia, which (now) DOES have a launcher icon (which is key to the use model).

***KILL USE MODEL:***
To kill the Tor Browsing session, once can kill the Tor Browser, and then right click on the Vidalia launcher to exit out of Vidalia.
Or, even easier, one can just press the "Exit" button in the Vidalia Control Panel (which had not shown up until the workarounds above were implemented).
*(Previously we had to open an xterm to grep for the Vidalia process and kill -9 it, which didn't always work properly, and which is a lousy use model anyway.)*

***RESTART USE MODEL:***
Then, to start another Tor Browser session, one simply repeats the process above from the x terminal.

***USE-MODEL IMPROVEMENTS:***
If you know of a better, cleaner, simpler use model workaround, please advise, as this is the best I can come up with so far (to mimic the originally intended use model which is what I use on all other operating systems).

---

### Post by mc4man on 2013-12-02
In regards to ask ubuntu, ect., -  a specific .desktop can be run from a terminal (or alt+F2), with gtk-launch 
As in -
gtk-launch name where 'name' is the name of the .desktop minus .desktop

Ex. I've a .desktop in .local/share/applications named players.desktop
To run that specific .desktop from cli - 
gtk-launch players 
This then uses the Exec= Icon= ,ect. from that .desktop

Whether matters in this particular case no idea...

---

### Post by jimmyh1972 on 2013-12-03
Don't go complicated.
1. sudo apt-get install tor
2. add foxy-proxy plugin/addon to firefox
3. define foxy-proxy:
  a. ip address 127.0.0.1
  b. sock4
  c. port 9050
enable / dissable foxy-proxy if you want to surf via TOR or not.
works great!!!

---

### Post by Lrpbpb on 2013-12-03
> **mc4man said:**
> In regards to ask ubuntu, ect., -  a specific .desktop can be run from a terminal (or alt+F2), with gtk-launch 
As in -
gtk-launch name where 'name' is the name of the .desktop minus .desktop

Ex. I've a .desktop in .local/share/applications named players.desktop
To run that specific .desktop from cli - 
gtk-launch players 
This then uses the Exec= Icon= ,ect. from that .desktop

Whether matters in this particular case no idea...

@mc4man Thank you so much! I've been looking for a long time for a way  to launch .desktops from a script in order to solve this problem. With your insight I can finally propose a complete solution (posted below). I had been cracking my head over this for the last 3 days, trying to use xdg-open, which due to a bug can't launch .desktops, even compiling xdg-open and xdg-autostart from source, but to no avail. So thank you, you and the poster doug [here]("http://askubuntu.com/questions/5172/running-a-desktop-file-in-the-terminal") who almost simultaneously posted these answers (pure concidence,  I suppose? ;)).

---

### Post by Lrpbpb on 2013-12-03
The Unity launcher and Dash use .desktop files to generate their entries. Different .desktops represent different entries (even if they have the same icon). So separating Tor and Firefox is a matter of creating separate .desktop files. 

The Vidalia Control Panel runs a customized version of Firefox found in .../tor-browser_en-US/App/Firefox. Since this customized version of Firefox is executed directly, and not through a .desktop, Unity automatically ties it to the default Firefox .desktop, making the two processes occupy the same entry in the launcher. The same thing happens when you simply run 'firefox' from the terminal.

However, running the firefox executable in .../tor-browser_en-US/App/Firefox/firefox doesn't run the custom Firefox version that is the Tor Browser, it simply runs normal Firefox as if you had typed "firefox" into a terminal (you can check this by looking at the version number of the window that pops up - Tor uses FF 17 ESR). This is because Firefox uses 'profiles' to separate the custom settings each user/program has created, and running .../App/Firefox/firefox by itself will simply use the default profle (the one you use in normal Firefox). 

So we have to force .../App/Firefox/firefox to use the tor profile. To do that run:

```
/path/to/tor-browser_en-US/App/Firefox/firefox -p tor -no-remote
```

Replace /path/to with the path to the directory where Tor is installed. The '-p tor' forces the app to use the tor profle, and '-no-remote' makes it run in a separate process from any other running instances of Frefox. Since a profile named 'tor' doesn't exist (in the ~/.mozilla/profiles.ini), the Profile Manager will open,  prompting you to create a new profile. Give it a name (tor) and point it to the profile that came in the Tor Browser Bundle: .../tor-browser_en-US/Data/profile. 

If all went well, you should now see an app called Tor Browser, complete with the Tor Button and NoScript in the toolbar, and running Firefox 17 ESR. But it is still attached to the Firefox entry in the Unity Launcher, because we ran it from a terminal (which uses the default .desktop) and not from a custom .desktop. Here is the .desktop I used to separate the Tor Browser from Firefox:

```

[Desktop Entry]
Name=Tor Browser
Name[en_US]=Tor Browser
Comment=
Exec=/path/to/.tor-browser_en-US/App/Firefox/firefox -p tor -no-remote
Type=Application
Icon=/path/to/.tor-browser_en-US/tor-browser.png
Categories=Network;WebBrowser;
Hidden=false
Terminal=false

```

Replace /path/to/... with the location you choose for the correspondng files. Save that as 'tor-browser.desktop' in either /usr/share/applications or in ~/.local/share/applications. I also used a [custom icon]("https://trac.torproject.org/projects/tor/ticket/5467"), but you can use the more standard one that comes preckaged in .../.tor-browser_en-US/App/Firefox/icons/mozicon128.png.

Now you can launch 'Tor Browser' from the Unity Dash, and it will occupy a separate entry from Firefox, using the icon you specified. However, running Vidalia still launches the merged Tor Browser, which makes sense because Vidalia has no idea the tor-browser.desktop you just created even exists. So I wrote a script which runs Vidalia, then kills Vidalia's merged Tor Browser as soon its process is created and finally launches the tor-browser.desktop.

```

#!/bin/bash

chk_vidalia(){
    #killall sends a null signal to vidalia, which fails if it isn't running
    killall -s 0 vidalia 2> /dev/null
}

cd $(dirname $0)

tor_exec='./App/Firefox/firefox'
tor_desktop='tor-browser.desktop'

if [ ! -f start-tor-browser ] ; then
    echo "The '$0' script must be in the tor-browser installation directory."
    exit 1
fi

if chk_vidalia ; then 
    echo "Error: Vidalia is already runnng"
    exit 2
fi

./start-tor-browser &

while ! killall $tor_exec 2> /dev/null ; do #Loops until $tor_exec is killed
    sleep 1
    echo -n "."
    if ! chk_vidalia; then echo "Error: Vidalia was closed."; exit 3; fi
done

echo -e \\n"Killed Vidalia's Tor Browser"

if gtk-launch ${tor_desktop/.desktop/} ;then echo "Launched separate Tor Browser"; fi

exit 0

```

And save the script as 'tor-browser-separate' in .../.tor-browser_en-US/.

The 'echos' in the above script are mostly for debugging and for understating what the script is doing in each step. These will only be shown if you run the script from a terminal. Kudos to @mc4man for teaching me about gtk-launch (used in the 3rd to last line), which allows the script to launch .desktops on its own. Without it one would have to open the Tor Browser separatley, either through the Dash or the Launcher, which, though a relatively minor setback, was stll pretty annoying :D.

Finally, you can create a .desktop file for the script above, which will essentially replicate the Tor Browser Bundle's intended behavior (i.e. launch the Vidalia Control Panel, connect to the Tor Network and finally launch the Tor Browser as a unique process, separate from firefox or any other applications). Here is the .desktop file I used:

```

[Desktop Entry]
Name=Vidalia Control Panel
Name[en_US]=Vidalia Control Panel
Comment=
Exec='path/to/tor-browser_en-US/tor-browser-separate'
Type=Application
Icon=path/to/.tor-browser_en-US/vidalia-control-panel.png
Categories=Network;WebBrowser;
Hidden=false
Terminal=false

```

Again, replace /path/to/... with the location you choose for the correspondng files and save it as 'vidalia.desktop' in either  /usr/share/applications or in ~/.local/share/applications. I used the icon [here]("http://from http://archive.roaringapps.com/app:1739"), since the Tor Browser Bundle doesn't provide a separate Vidalia icon (it comes integrated with the Vidalia executable). Finally, simply run 'Vidalia Control Panel' from the Unity Dash or pin it to the launcher.

I hope this helps and that it is what you were looking for. :)

---

### Post by Jim_Granite on 2014-01-03
> **Lrpbpb said:**
> separating Tor and Firefox is a matter of creating separate .desktop files.

EDIT: I wrote this up for a separate thread where a user asked to install Tor, however, I still haven't gotten either the Vidalia control panel to work properly on Ubuntu 13.10, nor for Ubuntu to show a separate icon for the browser when it's running. So, I will update the steps below, with [Lrpbpb's seminal instructions]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610") in the next few posts.

Basically, the goal is a step-by-step cut-and-paste installation and update sequence. 
Remember, the TBB is updated about a half-dozen times a year, so, the sequence has to cover the updates also.
Every time I update the TBB, it takes me a while as I lose all my prior customizations (e.g., I previously had the Vidalia control panel showing up but now I can't get it to show up anymore because I don't know which of the dozens of tricks I tried was the one that had actually worked).

So, to help others, here's my latest TBB installation sequence, for my own use. 

This sequence needs to be updated with the information in this thread, in order to add three critically needed features:
A. Separate the TBB icon from the Firefox icon
B. Vidalia control panel should show up when the TBB is started
C. Update instructions must be supplied (not just initial installation instructions)
** As always, improvements are welcome ... **

> 
0. These setup steps have to be repeated about a half-dozen times a year, due to constant updates in the Tor Browser Bundle.

Location of the latest Tor Browser Bundle for Linux is here:
- [https://www.torproject.org/download/download-easy.html](https://www.torproject.org/download/download-easy.html)

The latest 64-bit Linux version is here:
- [https://www.torproject.org/dist/torbrowser/linux/](https://www.torproject.org/dist/torbrowser/linux/)
The current file name (for 64-bit Linux) is:
- tor-browser-gnu-linux-x86_64-2.3.25-16-dev-en-US.tar.gz

1. **Obtain the latest 64-bit Linux Tor Browser Bundle (tbb):**
mkdir /tmp/tor
cd /tmp/tor
wget [https://www.torproject.org/dist/torb...5_en-US.tar.xz]("https://www.torproject.org/dist/torbrowser/3.5/tor-browser-linux64-3.5_en-US.tar.xz")

1. **Extract the tar.xz file:**
$ tar -xvJf tor-browser-linux64-3.5_en-US.tar.xz 

3. **Test that it works out of the box **(you just want to see that it comes up at this step):
$ ./tor-browser_en-US/start-tor-browser

** 4. Check previous installation setup**  (it is critical that instructions show how to install,and how to update the TBB, which is updated often):
$ alias tbb
=> alias tbb='ibus exit; /usr/bin/tor &'

$ which tor
=> /usr/bin/tor

$ ls -l /usr/bin/tor
=> -rwxr-xr-x 1 user1 root 65 Aug 17 05:50 tor

$ cat /usr/bin/tor
=> #!/bin/bash
=> 
=> sh /usr/bin/tor-browser/start-tor-browser

** 5. Replace the old tbb with the new tbb (save the old one just in case):**
$ DATE=$(date +"%Y%m%d")
$ sudo mv /usr/bin/tor-browser /usr/bin/tor-browser_$DATE
$ sudo cp -r ./tor-browser_en-US/ /usr/bin/tor-browser
$ cd /usr/bin
$ sudo chown -R $USER tor-browser
$ sudo chmod -R +x tor-browser

** 6. Test the newly relocated TBB:**
$ tbb
* This should bring up the Tor browser - but - unlike installing TBB on every other operating system on the planet, two problems will remain:*
A. Unfortunately, the desktop TBB won't be separate from the Firefox icon (which is extremely inconvenient and very dangerous)
B. Unfortunately, the Vidalia control panel won't come up so you'll have no control over your results.

**NOTE**:
Unfortunately, due to Ubuntu bugs which I still don't fully understand, Tor will be constantly confused with  Firefox (which it isn't); this lack of distinction will eventually lead  to human mistakes, which can easily lead to severe repercussions, even death,  if you're attempting to maintain privacy. This is bad; very bad. But there is  nothing you can do about it except never trust which browser comes up  when you use TBB on Ubuntu 13.10 with Unity. Always manually  doublecheck, and, when you make mistakes (which are inevitable since the  use model is the opposite of every other use model in Unity), then you  must create a new persona on the web, and perhaps move to a new country  (depending on why you wished to be anonymous) because you have instantly  compromised your identity, simply by the use of Ubuntu as an operating  system.

In addition, again for reasons that I really do not understand, Vidalia on every other operating system except Ubuntu 13.10  will come up with its panel; but it won't come up without herorics on  your part in Unity. I had the Vidalia control panel working; but it is  no longer working and I don't even know what I had done that finally had gotten it working, it  was that complicated. Unfortunately, with the latest TBB update, Vidalia no longer shows up. So, I'm back to where I was before I had somehow (heroically) gotten it working. Again, these heroics are not needed for any other operating system, except for Ubuntu 13.10 (that I know of).

---

### Post by Jim_Granite on 2014-01-03
> **Lrpbpb said:**
> The Vidalia Control Panel runs a customized version of Firefox found in .../tor-browser_en-US/App/Firefox. 

I'm NOT a Linux guru - but I'm trying to reproduce the steps in [Lrpbpb's seminal instructions]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610") above.

But, I'm having problems reproducing the steps.
For example, I don't have any file named "~/.mozilla/profiles.ini" in my Ubuntu 13.10 setup:
$ ls ~/.mozilla
=> extensions  firefox

Also, the default TBB hierarchy is DIFFERENT on the latest TBB (which is currently using Firefox ESR 24.2.0).
So please doublecheck what I say here, but, **I *think* that "App" directory no longer exists in the latest Tor Browser Bundle.**

When I run the "locate" command, I only see that directroy in the OLDER TBBs (like more than a week or two old):
$ sudo updatedb
$ locate tor|grep App
=> /usr/bin/tor-browser_en-US_20140101/App/Firefox <== the date indicates an archive time of an old installation

As of at least a few days ago, the latest 64-bit TBB does NOT contain that hierarchy anymore!
- [https://www.torproject.org/dist/torbrowser/linux/](https://www.torproject.org/dist/torbrowser/linux/)

The new TBB Firefox hierarchy appears to be in:
$ locate tor|grep Browser
=> /usr/bin/tor-browser_en-US/tor-browser/Browser/

How much this affects the installation instructions for obtaining the Vidalia control panel icon and for separating TBB from Firefox via desktop files, I don't know.

[ATTACH=CONFIG]249177[/ATTACH]

EDIT:
1. Change 
/path/to/tor-browser_en-US/App/Firefox/firefox -p tor -no-remote
TO:
/path/to/tor-browser_en-US/Browser/Firefox/firefox -p tor -no-remote
EG:
/usr/bin/tor-browser_en-US/Browser/Firefox/firefox -p tor -no-remote

WIP[ATTACH=CONFIG]249178[/ATTACH]

---

### Post by Jim_Granite on 2014-01-03
> **Lrpbpb said:**
>  Since a profile named 'tor' doesn't exist (in the ~/.mozilla/profiles.ini), the Profile Manager will open,  prompting you to create a new profile. Give it a name (tor) and point it to the profile that came in the Tor Browser Bundle: .../tor-browser_en-US/Data/profile. 

[Lrpbpb's seminal instructions]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610") are fantastic - but we need to modify them to be applicable today because this "/path/tor-browser_en-US/Data/profile file also does not (apparently) exist in the latest TBB Linux.

$ ls /usr/bin/tor-browser_en-US/Data/
=> Browser/            Tor/

$ ls /usr/bin/tor-browser_en-US/Data/Browser
=> Caches  profile.default/              profiles.ini

$ cat /usr/bin/tor-browser_en-US/Data/Browser/profiles.ini
=>
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=profile.default
Default=1 

So, I guess this is the profile file we should point to?
/usr/bin/tor-browser_en-US/Data/Browser/profiles.ini

EDIT: 
But it's not clear, to me, WHICH profile we should be entering when the Tor profile GUI comes up, since the default is the profiles.ini in the /usr/bin installation directory.
So, I had to guess what steps to take, so, would you kindly doublecheck these 12 steps, to see if I'm already guessing incorrectly what to do?
[ATTACH=CONFIG]249181[/ATTACH]

---

### Post by r3dd on 2014-01-03
> **jimmyh1972 said:**
> Don't go complicated.
1. sudo apt-get install tor
2. add foxy-proxy plugin/addon to firefox
3. define foxy-proxy:
  a. ip address 127.0.0.1
  b. sock4
  c. port 9050
enable / dissable foxy-proxy if you want to surf via TOR or not.
works great!!!

For the sake of anonymity, you should NEVER use the same browser for TOR or I2P browsing that you use for normal internet browsing. The The browser bundle comes with a customized Firefox for anonymity. Organizations and malicious users have been known to use tracking cookies to monitor TOR / I2P traffic. The only way you should install TOR as mentioned above is if you are advanced use, not concerned with anonymity (in which case, what is the point) or you intend to use TOR as a proxy for other applications as well.

---

### Post by Jim_Granite on 2014-01-03
> **alan.e.redding said:**
> you should NEVER use the same browser for TOR or I2P browsing that you use for normal internet browsing.

Exactly!

That's why this bug is so bad. 

As [Lrpbpb's seminal instructions show]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610"), this bug basically mixes up two VERY DIFFERENT use models!
Since Ubuntu 13.10, by default, makes absoluelty no distinction between them, you're always mistrusting WHICH BROWSER was brought up from the Unity GUI.

This is the only operating system on the planet which, by default, mixes these two very different use models as one.

So, it behooves us to SEPARATE the two as much as we can.
Unfortunately, I've spent hour and hours on this, and it's just a royal mess.

It's almost impossible, on this operating system, to get all the complexities down right, for a normal user.

I wish SOMEONE can write a simple setup that works for the average user. 
(tested on the latest TBB, not on a version that has all different paths)
Please.... ... ... 

Note: I'd write the darn thing, if I only knew what steps. 
For example, I'm guessing left and right just trying to set up the profile.
Here are, for example, the first dozen steps, in which you have to guess what to do to get it right.
$ /usr/bin/tor-browser_en-US/Browser/firefox
Brings up the following windows:
[ATTACH=CONFIG]249186[/ATTACH][ATTACH=CONFIG]249187[/ATTACH][ATTACH=CONFIG]249188[/ATTACH][ATTACH=CONFIG]249189[/ATTACH][ATTACH=CONFIG]249190[/ATTACH]
DRAT. The forum only allows five attachments of the dozen first steps, unfortunately.

---

### Post by Jim_Granite on 2014-01-03
Here are the next five sets of guesses to setting up Tor correctly (a basic user should not have to guess just to set up something as seemingly simple as this!)...
[ATTACH=CONFIG]249191[/ATTACH][ATTACH=CONFIG]249192[/ATTACH][ATTACH=CONFIG]249193[/ATTACH][ATTACH=CONFIG]249194[/ATTACH][ATTACH=CONFIG]249195[/ATTACH]

---

### Post by Jim_Granite on 2014-01-03
And here are the last two attempts at following [Lrpbpb's seminal instructions]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610"), showing either that the guesses were wrong somewhere, or that there is more to do...
[ATTACH=CONFIG]249196[/ATTACH][ATTACH=CONFIG]249197[/ATTACH]

---

### Post by r3dd on 2014-01-03
It looks like you are trying to create the profile "tor" inside the Tor Browser Bundle itself. The default profile is already configured for TOR so adding the "tor" profile seems redundant. Perhaps I am misunderstanding the line of thought, but don't you just want the icon to show separately in Unity?

I am a Kubuntu fan rather than Ubuntu, but it seems to me that the unity panel activates the indicators for the icons based on the services that are running (shown by 'ps -A'). If that is actually the case, regardless of what profile or other script you use the process will still run as "firefox" so it will activate the icon no matter what. Unless you can figure out a way to change the name of the process, you will be stuck like the proverbial chuck.

---

### Post by Jim_Granite on 2014-01-03
> **Lrpbpb said:**
> If all went well, you should now see an app called Tor Browser, complete with the Tor Button and NoScript in the toolbar, and running Firefox 17 ESR. 

I think I'm at this stage of the [seminal instructions]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610"), but, I can't figure out what it means that I "should see an app called Tor Browser".
Where should I look for this app?
It's not on my desktop.

Ah, I almost never use that little "search your computer and online sources" circular button that came with Unity, so, maybe that is where we are supposed to "see" the app called the "Tor Browser"?

EDIT: I seem to have TWO of these onion icons; the second of which is  probably a leftover from my previous attempts at getting the Vidalia  control panel to show up in the launcher.
[ATTACH=CONFIG]249198[/ATTACH]

Moving on, I clicked on the first of these two icons (the red one, which seems to be new):
[ATTACH=CONFIG]249199[/ATTACH]

So, now I can "pin" this new (red) Vidalia onion icon to the launcher.

---

### Post by Jim_Granite on 2014-01-03
> **Lrpbpb said:**
> Here is the .desktop I used to separate the Tor Browser from Firefox

At this point, I'm only halfway through [Lrpbpb's seminal instructions]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610"), but I seem to be already done.
So, I'm confused. 
Notice I already have a separate Firefox icon and a separate Tor Icon on my launcher now.
So, why do I need to follow the additional instructions? (I'm confused.)

[ATTACH=CONFIG]249200[/ATTACH]

EDIT: To try to figure out why it's working already, without me following ANY of the next steps, I see I already have a desktop file for Tor from my previous attemps weeks ago to get a working Vidalia desktop entry:

$ sudo updatedb; locate /tor.desktop
=> /usr/share/applications/tor.desktop

$ cat /usr/share/applications/tor.desktop
=> 
[Desktop Entry]
Version=1.0
Name=Tor Browser Bundle 1
Comment=Tor Browser Bundle 2
GenericName=Tor Browser Bundle 3
Keywords=Internet;tor;browser;bundl;tbb
Exec=tor
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/usr/share/app-install/icons/vidalia.png
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;video/webm;application/x-xpinstall;
StartupNotify=true
Actions=NewWindow;NewPrivateWindow;

[Desktop Action NewWindow]
Name=Open a New Window
Exec=tor
OnlyShowIn=Unity;

[Desktop Action NewPrivateWindow]
Name=Open a New Private Window
Exec=tor 
OnlyShowIn=Unity;

Where this is the icon file:
/usr/share/app-install/icons/vidalia.png
[ATTACH=CONFIG]249201[/ATTACH]

---

### Post by Jim_Granite on 2014-01-04
> **Lrpbpb said:**
> Here is the .desktop I used to separate the Tor Browser from Firefox:
Success at last!

Somehow, without actually following [Lrpbpb's seminal instructions]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610") completely, I'm able, for the first time ever, to do the following:
A. Right clicking on the firefox icon on my launcher launches & selecting "Open a New Window" opens up Firefox 26.0 (Canonical)
B. Right clicking on the Tor icon on my launcher & selecting "Tor Browser" launches Firefox ESR 24.2.0 (TBB)
C. Each browser instance shows up as a tick mark on the respective launcher (only one Tor browser can be launched).
[ATTACH=CONFIG]249207[/ATTACH]
Yet, even flush with the elation of success at last, I'm a bit confused because I never had to create that desktop file, nor the Vidalia script, as described in [Lrpbpb's seminal instructions]("http://ubuntuforums.org/showthread.php?t=2182827&p=12864610#post12864610").

Notice "my" (previously created from earlier in this thread) tor.desktop file does NOT run the command like this:
... Exec=/usr/bin/tor-browser_en-US/App/Firefox/firefox -p tor -no-remote
My existing tor.desktop file runs the command like this:
... Exec=tor

But, since mine seems to work perfectly now - I wonder if we really **need** those additional options to firefox (-p & -no-remote)?
> **Lrpbpb said:**
> Save that as 'tor-browser.desktop' in either /usr/share/applications or in ~/.local/share/applications.
My previously existing desktop entry for Tor was already named the following, so I skipped this step in the instructions:
/usr/share/applications/tor.desktop

> **Lrpbpb said:**
> I also used a [custom icon]("https://trac.torproject.org/projects/tor/ticket/5467"), but you can use the more standard one that comes preckaged in .../.tor-browser_en-US/App/Firefox/icons/mozicon128.png
The standard icon is actually now in a new location, based on a recent download of the TBB:
$ locate mozicon128.png
=> /usr/bin/tor-browser_en-US_20140101/App/Firefox/icons/mozicon128.png <-- old location
=> /usr/bin/tor-browser_en-US/Browser/browser/icons/mozicon128.png <-- new location
=> /usr/lib/firefox/browser/icons/mozicon128.png

Here is the default /usr/lib/firefox/browser/icons/mozicon128.png
[ATTACH=CONFIG]249202[/ATTACH]
Here is the default /usr/bin/tor-browser_en-US/Browser/browser/icons/mozicon128.pnp
[ATTACH=CONFIG]249204[/ATTACH]
EDIT: I'm not sure **why** my desktop launcher has the firefox chasing the onion icon by default though (since it should have the green-and-gray world icon instead).

---

### Post by Jim_Granite on 2014-01-04
The only thing missing is that I no longer see the Vidalia control panel; but, I can live without that since I seem to have the Tor Browser working separately from Firefox now. 

I'm not even sure if I need the Vidalia control panel anymore, simply because now, for the first time, Tor and Firefox appear as separate icons, so I can start and stop the Tor Browser Bundle at will.

---

### Post by Jim_Granite on 2014-01-04
> **alan.e.redding said:**
> It looks like you are trying to create the profile "tor" inside the Tor Browser Bundle itself. 

If this is directed at [**[COLOR=#000000]Lrpbpb[/COLOR]**]("http://ubuntuforums.org/member.php?u=1032960") based on post 22, then ignore what I say below.
If it's asked of me, then realize that I'm mostly just shooting bullets wildly as I don't understand this stuff.
I just want Firefox and the TBB to be independent, like they are on all other platforms.

> **alan.e.redding said:**
> don't you just want the icon to show separately in Unity?

Woo hoo!

Thanks to all of you, I thinkwe have what we want, which is:
A) When I right-click on the Firefox icon on the Unity launcher, firefox runs.
B) When I right click on the TBB icon on the Unity launcher, the tbb runs.
C) All those running processes are now showing up as tick marks in their respective icons on the launcher.

And, I only had to perform half the steps documented, in order to accomplish this.
I wish I understood it all - but - at least it's working like I had wanted it to from the beginning (with the exception of the Vadalia control panel, which isn't showing up yet).
[ATTACH=CONFIG]249214[/ATTACH]

---

### Post by Jim_Granite on 2014-01-05
I just marked this thread as solved because, despite the fact I'm not sure what specific steps are needed, I now have the Tor Browser launcher working separately from the Firefox launcher.
To help others, and pay my way forward, I wrote up the following installation instructions (using absolute paths so that users may simply cut and paste for the same results).
Notice I only performed half the steps, as suggested in the [seminl post #22]("http://ubuntuforums.org/showthread.php?t=2182827&page=3"), so I ask the next person who tries this to clarify which steps are needed and which can be omitted.
As always, please correct where I omit or err so that others benefit from your effort.

> 
How to safely install the Tor Browser Bundle on 64-bit Ubuntu 13.10

See also:


Note: Tor can never be trusted in a default Ubuntu 13.10 environment!
      You must modify the default setup in order to preserve your privacy.

Note: Setup steps need to be repeated about a half-dozen times a year, 
      due to constant updates in the Tor Browser Bundle, so the commands 
below use absolute paths, for cut-and-paste repeat efficiency.

0. Location of the latest Tor Browser Bundle for Linux is here:
   [https://www.torproject.org/download/download-easy.html](https://www.torproject.org/download/download-easy.html)

   The latest 64-bit Linux version is here:
   [https://www.torproject.org/dist/torbrowser/linux/](https://www.torproject.org/dist/torbrowser/linux/)

   The current (Jan 1, 2014) file name (for 64-bit Linux) is:
   tor-browser-gnu-linux-x86_64-2.3.25-16-dev-en-US.tar.gz

1. Obtain the latest 64-bit Linux Tor Browser Bundle (tbb):
   $ mkdir /tmp/tor
   $ cd /tmp/tor
   $ wget [https://www.torproject.org/dist/torb...5_en-US.tar.xz](https://www.torproject.org/dist/torb...5_en-US.tar.xz)

2. Extract the tar.xz file:
   $ cd /tmp/tor
   $ tar -xvJf tor-browser-linux64-3.5_en-US.tar.xz

3. Quick test (just to see if the Tor Browser comes up):
   $ /tmp/tor/tor-browser_en-US/start-tor-browser
   Note: Firefox should come up with the following message: 
         "This browser is configured to use Tor."
   Exit the browser: TBB:File->Quit

4. Check your previous installation setup:
   $ alias tbb
     => alias tbb='ibus exit; /usr/bin/tor &'
   $ which tor
     => /usr/bin/tor
   $ ls -l /usr/bin/tor
     => -rwxr-xr-x 1 user1 root 65 Aug 17 05:50 tor
   $ cat /usr/bin/tor
     => #!/bin/bash
     => sh /usr/bin/tor-browser_en-US/start-tor-browser
$ file /usr/bin/tor-browser_en-US/start-tor-browser
=> POSIX shell script, ASCII text executable

Note: Most of the time you will be re-installing Tor, 
        but if this is your first intallation, add this:
$ vi ~/.bash_aliases
   ADD:
   alias tbb='ibus exit; /usr/bin/tor &'

5. Replace the old tbb with the new tbb (save the old one just in case):
   $ DATE=$(date +"%Y%m%d")
   $ sudo mv /usr/bin/tor-browser /usr/bin/tor-browser_$DATE
   $ sudo cp -r /tmp/tor/tor-browser_en-US/ /usr/bin/tor-browser
   $ sudo chown -R $USER /usr/bin/tor-browser_en-US
   $ sudo chmod -R +x /usr/bin/tor-browser_en-US

6. Test the newly relocated TBB:
   $ tbb
Exit the browser: TBB:File->Quit

   Note: This should bring up the Tor browser - but - unlike TBB 
         on all other operating systems, two serious privacy-related
         bugs will reveal themselves on Ubuntu 13.10 with Unity:
         A. There will be no Tor launcher on the desktop  
            (which means you can never trust which browser you are using, 
             and, since mistakes will inevitably happen, this means you
             will inevitably compromise your anonymity using Ubuntu, by 
defaul, if you don't run the additional steps below).
         B. There will be no Vidalia control panel.

7. According to Lrpbpb, the Unity launcher & Dash use .desktop files to 
   generate their entries. Different .desktops represent different entries 
   (even if they have the same icon). So separating the Tor Browser and 
the Firefox browser is a matter of creating separate .desktop files.

   The Vidalia Control Panel runs a customized version of Firefox found in 
   /usr/bin/tor-browser_en-US/Browser/firefox

   Since the Tor-customized-and-supplied version of Firefox is executed 
   directly, and not through a .desktop, Ubuntu 13.10 Unity automatically 
   ties the Tor-customized Firefox to the default Firefox .desktop, making 
   the two very different processes occupy the same entry in the launcher. 
   The same thing happens when you simply run 'firefox' from the terminal.

   Therefore, running the customized firefox executable in 
   /usr/bin/tor-browser_en-US/Browser/firefox 
   doesn't actually run that custom Firefox version that is the Tor Browser; 
   it simply runs normal Firefox as if you had typed "firefox" into a terminal.

   Note: Double-check by looking at the version number of the Firefox that 
   pops up when you type each of the following commands: 
   $ /usr/bin/firefox
   $ /usr/bin/tor-browser_en-US/Browser/firefox         
   $ /usr/bin/tor-browser_en-US/Browser/firefox -p tor -no-remote

   It's not at all intuitive that the first two commands above will actually 
   bring up the same version of Firefox, which is currently version 26.0, 
   even though the Tor Browser Bundle is actually currently configured for 
   Firefox version ESR 24.2.0, as shown by the results of the third command.

   This is because Firefox uses 'profiles' to separate the custom settings 
   that each user/program has created; therefore, running 
   /usr/bin/tor-browser_en-US/Browser/firefox         
   will simply use the default profle (the one you use in normal Firefox).

   So we have to force the Tor Browser Bundle
   /usr/bin/tor-browser_en-US/Browser/firefox         
   to use the tor profile instead of the Firefox profile. 

   To force the Tor Browser Bundle to use the Tor profile, type:
   $ /usr/bin/tor-browser_en-US/Browser/firefox -p tor -no-remote

   This will bring up the "TorBrowser - Choose User Profile" window.
   In that "Choose User Profile" window, press "Create Profile...".
   Up will come a "Welcome to the Create Profile Wizard" dialog.
   Press "Next" in that "Welcome to the Create Profile Wizard" dialog box.
   When it asks "Enter new profile name", type "tor" (sans quotes).
   Notice that same forms says your user settings will be stored in:
    /usr/bin/tor-browser_en-US/Data/Browser/qgnzi9oi.Default User
   Change that by clicking on the "Choose Folder" button.
    /usr/bin/tor-browser_en-US/Data/Browser/qgnzi9oi.Default User
   In the "Choose Profile Folder" box that comes up, enter:
    Location: /usr/bin/tor-browser_en-US/Data/Browser/profiles.ini

8. Now it's time to pin the Tor icon to the Unity launcher:
   Press the Ubuntu "Search your computer and online sources" launcher, 
   and type "Tor" as your search term.

   You should see an icon labeled "Tor Browser" which looks like a 
   reddish-firefox-curled-around-a-purple-onion icon.

   Launch the Tor Browser from that icon, and, after doublechecking that
   the firefox version is the Tor Browser Bundle version, then right click 
   on the firefox-curled-around-the-onion icon to pin the icon to the 
   Unity launcher panel. 

RECAP:
   You've installed the Tor Browser Bundle on 64-bit Ubuntu 13.10 Linux.
   You've separated the Tor Browser launcher from the Firefox launcher.
   The Vidalia control panel still doesn't come up (unfortunately).


---

### Post by impliedconsent2 on 2014-05-06
Yes, I read it's resolved - just offering 'another' way:

I read this through and through and no issues with it, other than this is probably not the answer for absolute beginners. Might scare the crap outa them and suggesting to copy-n-paste and using sudo without them knowing what the commands are for.  I suggest (just a suggestion - not bible) taking a look at the [[COLOR=#b22222][FONT=arial]HOW-TO KUBUNTU GUI Beginners Install of Tor - As of 6MAY2014[/FONT][/COLOR]]("http://ubuntuforums.org/showthread.php?t=2222470") I just created.  I too had a problem (not permissions related) with no launcher. Took me roughly 2min to create the launcher without terminal, sudo, or elevating permissions.

---

