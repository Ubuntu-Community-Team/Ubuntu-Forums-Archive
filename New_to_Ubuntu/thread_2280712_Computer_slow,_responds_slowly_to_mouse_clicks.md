---
title: "Computer slow, responds slowly to mouse clicks"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by AbleTassie on 2015-06-01
My computer often responds very slowly to mouse clicks and often switches between tabs on Firefox very slowly. When writing emails, text often appears very slowly after keystrokes.

Any idea what the problem could be?

Thank you,

Able

---

### Post by QIII on 2015-06-01
It *could *be many things.

Let's start by discussing your hardware.  Could you give us your machine's specs?

Which release of Ubuntu are  you using?

---

### Post by night_sky2 on 2015-06-01
Is Firefox the sole culprit or do you experience the same thing in another browser/application?

It would be useful to know more about your PC specs indeed.

---

### Post by AbleTassie on 2015-06-01
Ubuntu 14.04.2 LTS Lubuntu

Intel Celeron M Processor 1.60 GHz Memory 1154MB

---

### Post by AbleTassie on 2015-06-01
I will check out another browser and let you know

---

### Post by mörgæs on 2015-06-01
Yes, better to try several of them. Many alternative browsers are available, not only Firefox and Chromium.

---

### Post by sudodus on 2015-06-02
Lubuntu 14.04.2 LTS should work with that processor and RAM, while standard Ubuntu needs more horsepower and memory to work well. ***Seamonkey*** might be a good alternative as a lighter web browser. You could try a dedicated mail program, for example ***Thunderbird*** instead of managing mail via the web browser.

And as already suggested by mörgæs, please search for and try other browsers - some are ultra light but a little harder to learn, for example ***Links2***, some are a medium light and fairly easy to use ... pick what works best for you :-)

---

### Post by mattharris4 on 2015-06-02
It would also help if you could state the sites that cause this the most.  In my case I have plenty of RAM and a newer CPU in my laptop but that CPU is a power-saver CPU (the AMD E1-2100) that does not process some sites well using a mainline browser, other sites work fine.  I have been able to narrow the problem down to the CPU in the computer not being powerful enough to handle those websites properly (even though the task manger may say the CPU is only at 70% at times, I am unsure why the CPU can bog down at less than 100% but it does).  SFGate.com and Mlive.com are two of the worst offenders lately.

Your CPU Passmarks at 376 which is not much more than half of my AMD E1's already abysmal score (620).  A Passmark score is not a perfect measure of a CPU's capabilities but without going into very complicated specific-purpose tests and a lot of them it is the best quick-indicator we have and it is fairly reliable IME. Today's full-power CPUs usually score above 2000, many way above.  This may explain a lot of your problem.  Also if I understand correctly your computer has 1154MB RAM.  Some sites with multiple tabs in Firefox or Chrome using Lubuntu send my laptop in the 1200-1350MB range (note some -- not all or even most).  If your computer is using that much RAM you are likely going into swap.  In my experience with another computer and a buntu swap is slow, slow, slow -- did I remember to say slow.  Use your task manager to monitor the RAM usage on your computer, this could also be an aggravating factor here.  If you must use this computer for internet I would try a browser like Midori even though for most I hate to recommend them.  Search for browsers in the Lubuntu Software Center, Google them and pick some to try that use less CPU power and RAM.  None are perfect, however -- some features such as video playback and picture slideshow display are not great in some low-power web browsers IME.  

Seamonkey doesn't show up in the Software Center at least on my computer but is available at [www.seamonkey-project.org]("http://www.seamonkey-project.com") .  I haven't used it so I cannot comment on the install process or how well it works with special features but it is mentioned in this thread so I posted the website address and will let you decide for yourself if you are interested in it.  Its website does say "Powered by Mozilla", the same organization behind Firefox which works quite well on appropriate equipment and Mozilla is a legitimate software developer dealing mainly in mostly open-source applications (unfortunately web browsers require some closed-source programs such as Flash in them nowadays to function properly which Mozilla itself has complained about time and time again).

---

### Post by mattharris4 on 2015-06-02
I just attempted to install SeaMonkey both by downloading the file from the SeaMonkey webpage and when that did not work by following the directions on this page:  [http://sourceforge.net/p/ubuntuzilla/wiki/Main_Page/](http://sourceforge.net/p/ubuntuzilla/wiki/Main_Page/) .  They do not work and it is not available in the Software Center.  Downloading off of the SeaMonkey site directly only opens up an Archive Manager that unzips but does not allow for install.  Next I tried the instructions linked above -- they did not work.  I cannot get it to open in the Software Center after downloading it off of the SeaMonkey page either, the Software Center is not an option to select.  I am capable of entering words into a terminal but in this case the instructions do not work (although they act like they are going to including the terminal giving other instructions on what to do before this program can be installed).  I attempted this more than once and triple-checked my data-entry each time to ensure it is exactly as shown (it is not possible to copy from a webpage and paste into the terminal with the usual methods, I have tried on several occasions).  My attempts were in Lubuntu 14.04 LTS.  I gave the site address after sudodus recommended it (he is usually very reliable in his recommendations and is a valued moderator here, I am sure he meant well recommending this program and he thought the the instructions available via either the program's website or a Google search were accurate -- they aren't in this case.  I emphasize that I know sudodus is not a bad or malicious person and meant well here); usually the rigamarole for a non-Software Center program is to download the .deb file from the applicable site, then after download the Software Center opens and installs the program.  That does not happen here.  If there is an easier manner of installing SeaMonkey please explain and sticky the explanation so others can refer to it (I would still like to try SeaMonkey if that is the case).  If not please, please, please, please, please do not recommend it here or anywhere other than a coders-only forum.  Recommending an evidently extremely difficult or impossible to install program will unfortunately only get someone requesting assistance a borked 'Buntu install, 95% of 'Buntu users don't know the difference between a .deb file and a root partition and should not need to -- I am attempting to protect that user base with my request here.  I went way beyond what I would instruct anyone requesting assistance here to do attempting to install this program.  Fortunately my Lubuntu install still seems to be working (I will find out after a reboot which I intend to do when I am done with this post) but that doesn't mean others will be so fortunate.

I am sorry if I sound Linus-esque but I am attempting to protect others from creating a bigger issue than they came here with.  I don't know how to explain this any other way (and my natural personality is very similar to Linus' anyway, I have to consciously tone it down when dealing with people in settings such as this).

---

### Post by sudodus on 2015-06-03
@mattharris4

Thank you for checking out Seamonkey and being concerned about your problems with it.

I'm using Seamonkey successfully in [ToriOS]("http://torios.net/"), a re-spin based on Ubuntu 12.04 LTS. You can download it from this link (and try it live without installing). I have to check the problems in 14.04 LTS and I'll come back to this thread, either with a solution, or I will remove the recommendation.

Anyway, my experience of Seamonkey is from ToriOS. I find it better than Midori. However, both browsers work for me. [COLOR=#696969][s]Debian Jessie comes with ***Iceweasel*** which is also an alternative, that I think is lighter than standard Firefox.[/s][/COLOR]

Edit: 

ToriOS uses Seamonkey version 2.33.1 - and it works (in ToriOS)

Edit 2:

Lubuntu 14.04.2 LTS can use Seamonkey too. See the description how to install it in the next post :-)

Edit 3:

Iceweasel is probably not lighter than Firefox, it is basically a re-branding.

---

### Post by sudodus on 2015-06-03
Seamonkey works for me in an up to date (updated/dist-upgraded) installation of Lubuntu 14.04.2 LTS i386 (32-bit version).

```
tester@tester-SATELLITE-PRO-C850-19W:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
```

Install it like this:

1. Download a tarball from

[http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)
or select locale manually from
[http://www.seamonkey-project.org/releases/#official](http://www.seamonkey-project.org/releases/#official)

See attachment #1

2. Extract the content from the tarball. It is easy with the archiver program ***file-roller*** in Lubuntu which starts by default. I made a local installation in the user's home directory, but a more advanced installation, available for all users, can be made according to the detailed description in [Installing the light-weight web browser seamonkey]("http://ubuntuforums.org/showthread.php?t=2281120")

See attachment #2

So now there is a directory **seamonkey** in my home directory.

```
tester@tester-SATELLITE-PRO-C850-19W:~$ ls ~/seamonkey/
application.ini             icons             libnssutil3.so    precomplete
blocklist.xml               isp               libplc4.so        removed-files
chrome                      libfreebl3.chk    libplds4.so       run-mozilla.sh
chrome.manifest             libfreebl3.so     libprldap60.so    seamonkey
components                  libldap60.so      libsmime3.so      seamonkey-bin
crashreporter               libldif60.so      libsoftokn3.chk   searchplugins
crashreporter.ini           libmozalloc.so    libsoftokn3.so    Throbber-small.gif
crashreporter-override.ini  libmozsqlite3.so  libssl3.so        updater
defaults                    libnspr4.so       libxul.so         updater.ini
dependentlibs.list          libnss3.so        license.txt       update-settings.ini
dictionaries                libnssckbi.so     omni.ja
distribution                libnssdbm3.chk    platform.ini
extensions                  libnssdbm3.so     plugin-container
tester@tester-SATELLITE-PRO-C850-19W:~$
```

[COLOR=#696969]3. I created a small batch file, that starts seamonkey from a terminal window. This is not necessary, but may be convenient for some people.

```

cd
mkdir -p bin
nano ~/bin/seamonkey
```
Write the following into the editor
```
$HOME/seamonkey/seamonkey
```
save it and close the editor. Make it executable with the following command.
```
chmod ugo+x ~/bin/seamonkey
```

**~/bin** will be in **$PATH** after reboot, so that links and executable files  in that directory will be found directly (without explicit path). So it  is enough to type ```
seamonkey
``` (and launch it with the Enter  key) in a terminal window.

You can also make a symbolic link or an alias.
[/COLOR]
4. I created a desktop file, that starts seamonkey from the desktop. (I use the Swedish locale for Lubuntu, where 'Skrivbord' is used instead of 'Desktop').

```
$ cat ~/Skrivbord/seamonkey.desktop
```
```
[Desktop Entry]
Version=1.0
Categories=Application;System;
Type=Application
Name=seamonkey-local
Comment=Install system to mass storage device, typically USB pendrive
Exec=/home/tester/seamonkey/seamonkey
Path=/home/tester/
Icon=/home/tester/seamonkey/chrome/icons/default/seamonkey.png
Terminal=false
StartupNotify=false
```

5. Run seamonkey

See attachment #3.

---

### Post by newb85 on 2015-06-03
I was under the impression that iceweasel was basically a re-brand of firefox (which is trademarked), so it wouldn't really be lighter than firefox.

Thunderbird was suggested for email.  Sylpheed comes preinstalled in Lubuntu.  I don't really know the difference (haven't done much testing with sylpheed), but I would imagine sylphed was chosen as the default because it's lighter.

---

### Post by sudodus on 2015-06-03
@ 				 				 					 						 	newb85

You are probably right about Iceweasel - I'll remove the lines about it in my previous posts.

I use thunderbird. What I meant is to use a mail client rather than using the web browser for email. If sylpheed is good enough for the user, yes, that's lighter than thunderbird, but I think dedicated mail clients are lighter than using a web browser for mail.

-o-

In computers with low RAM it is important to

- close programs that are not used
 - close tabs, and not leave them open when you browse to another web page.

---

### Post by newb85 on 2015-06-03
That is an interesting question.  Is a dedicated mail client lighter than a webmail interface in a browser?  I don't know or have numbers available.

However, it does strike me that there are distros out there, like ChromeOS and Peppermint, that aim for a smaller resource footprint by moving towards cloud computing.  If moving applications for word processsing, spreadsheets, playing games like solitaire, etc. into the cloud reduces demands, wouldn't doing the same with email have the same effect?

I don't know.  That's just my un-educated guess.

Sorry if this is a derail.

---

### Post by sudodus on 2015-06-04
Theory may indicate what works better. We can test in an old computer, what works better. We can also measure how much resources (CPU and RAM) that is used by each application program.

What we discuss and suggest here is theory for the original poster until it is tested in their particular computer :-)

---

### Post by sudodus on 2015-06-05
I'll list a few links discussing and describing light-weight web browsers

[https://www.starryhope.com/10-alternative-browsers-for-ubuntu-linux/](https://www.starryhope.com/10-alternative-browsers-for-ubuntu-linux/)

[http://www.techrepublic.com/blog/10-things/10-web-browsers-for-the-linux-operating-system/](http://www.techrepublic.com/blog/10-things/10-web-browsers-for-the-linux-operating-system/)  <-- this one is from 2011, but maybe still relevant descriptions

[http://beebom.com/2015/03/best-web-browsers-for-linux](http://beebom.com/2015/03/best-web-browsers-for-linux)

[http://www.computerworld.com/article/2485269/web-apps-5-lesser-known-browsers-free-lightweight-and-low-maintenance.html?page=6](http://www.computerworld.com/article/2485269/web-apps-5-lesser-known-browsers-free-lightweight-and-low-maintenance.html?page=6)

I think a quick summary of these links gives a good record for Midori.

Previous comment by me: > Anyway, my experience of Seamonkey is from ToriOS. I find it better than Midori. However, both browsers work for me.

Midori is definitely lighter than Seamonkey. When the computer is slow, speed and responsiveness can be very different, so try several web browsers and select the one that is best for you and your computer :-)

---

### Post by flaymond on 2015-06-05
[QUOTE=sudodus]Midori is definitely lighter than Seamonkey.[/QUOTE]

+1

Midori is the third best web browser I ever use other than Firefox and Chrome/Chromium. I really like that web browser. It's somehow fast. ;)

---

### Post by mattharris4 on 2015-06-12
I am a little late here checking back on this thread, I just bought a new (refurbed) computer and have been busy setting it up and making sure everything works (I have been checking this forum daily but not spending as much time on it).  I will probably install a 'Buntu on it in a few months once I am reasonably sure I won't need to use the warranty on it.  Thank you sudodus for instructions on how to install Seamonkey onto Lubuntu or on my old computer with Xubuntu on it.  I will attempt to install it on my laptop in the next couple of days and report back.

I also re-read my last post in this thread.  Sudodus, my intent was good but I just about bit your head off in it.  It did not occur to me that you could have used it on a different OS where it was included in the base install.  For that I apologize.

---

### Post by sudodus on 2015-06-12
No worries mattharris4,

You post gave us a tutorial how to install seamonkey. I think it can be useful for many people :-)

-o-

By the way, I think it is a good idea to buy refurbed computers. I've done it myself (for me and for my children), and with good results - professional class computers for a very decent price.

---

