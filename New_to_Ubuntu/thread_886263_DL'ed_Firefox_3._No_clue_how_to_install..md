---
title: "DL'ed Firefox 3. No clue how to install."
date: 2008-08-11
forum: New to Ubuntu
---

### Post by penguinv on 2008-08-11
I have Ubuntu 7.04 with a P-3/300MB-RAM so I'm sticking with it.

I am running FF2 and it works fine. I downloaded FF3 from the mozilla site.

Now what? 

1. I can open in Archive Manager. But there's no "install file" evident.

2. I can open Add/Remove Programs, but it does not appear.

3. I can start the Synaptic Package Manager but FF3 does not show up on any  of the repositories.

History: Ubuntu works great. I have not figured out how to install programs.

Some have auto-install so I got these: LostIRC, Flash on FF2, Opera.
But I failed to get Flash for Opera, Java (I really don't know if it worked or not), several bit-torrent clients, some other IRC program.

I like mirc, mibbit, even chatzilla. I'd like a better irc program than LostIRC: ability to click on links, log files, click on a name to start a private chat.

4. I thought of learning to do it in terminal. I can well do dos things in a tcsh shell. On the other hand, some site listed almost a dozen dependencies and I'd also have to learn to check and install each of them.

Thank you very much I'd like to learn to use Ubuntu as a GUI, the way Canonical God meant it to be.

--> I truly appreciate your help! TIA

---

### Post by tuxxy on 2008-08-11
This link may be of use

[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by Rolcol on 2008-08-11
there's no need to install the one from mozilla.  It should be pre-compiled.  Open up the firefox file inside the folder.

---

### Post by rockerphil on 2008-08-11
ok, i hope this is of some assistance, as far as your chat client goes. i personally use mIRC and love the feel of it. i do this through the Windows emulator Wine. this can be installed through the terminal by running this code:

sudo apt-get install wine

once that's done simply download the mIRC installer and run the program through Wine to install it. somthing like this

wine mirc64.exe

be sure to replace mirc64.exe with whatever version you're using. this will install mIRC in your Wine folder. now all you need to do is cd to the installed program file (works just like the DOS command). it's more than likely somthing like this

cd ~/.wine/drive_c/Program\ Files/mIRC

once there simply run

wine mirc.exe

and that will launch your mIRC, but, since it's running through Wine you won't be able to click links, but everything else works fine. alternatively if you like the feel of mIRC you might want to try xchat, it's got a very similar feel to mIRC and works natively in Linux. it can be installed with

sudo apt-get install xchat

hope this info helps,

Phil

edit: just about all the programs you need can be installed either through your Synaptic Package Manager, Add/Remove, or via the command line with "sudo apt-get install <package name>" or "sudo aptitude install <packagename>"

----------------
Now playing: [Black Sabbath - The Wizard](http://www.foxytunes.com/artist/black+sabbath/track/the+wizard)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by tuxxy on 2008-08-11
or just install xchat in synaptic if its not already installed at applications > internet > xchat 

```
sudo apt-get install xchat*
```

---

### Post by penguinv on 2008-09-07
That page says it's for 7.10 
(Danger! I have 7.04 and directions for the 6.something didn't work but in desperation I continue and trust.
--------------------- here's the text from the page -------------------
Installing Firefox3.0 beta2 in Ubuntu

Preparing your system

sudo apt-get install libstdc++5

Now you need to take backup of your old Firefox preferences

sudo cp -R ~/.mozilla ~/.mozillabackup

Now you need to download Firefox 3.0b2 from here

Now you have firefox-3.0b2.tar.bz2 file   
** *----> I got FF-3.0.2.tar.bz2   -NOT EXACTLY THE SAME***

Unzip the .tar.bz2 file in /opt directory using the following command

sudo tar -C /opt -jxvf firefox-3.0b2.tar.bz2

Now you need to link the plugins using the following command

cd /opt/firefox/plugins/

sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

Now you need to create a link to your new firefox launcher using the following command

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox

sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

This will complete the installation of firefox 3.0b2

If you want to open firefox 3 beta 2 go to Applications—>Internet—>Firefox Web Browser
---------------------------------------------------------
That's the text: I'll see if I can comment here.

First, thanks for telling me what is going on in each command.. 
Previously I have never followed any terminal instructions like DO THIS.
I don't want a mess. But things cannot remain stopped forever.

   And I really appreciate the difference between the XP computer upstairs and all that I have to do to maintain it, and this one, where I have to do nothing but click an update from time to time.
   
So I load the needed library (is this all for FF or just for an upgrade from 2 to 3.? How could I have found this out on my own?)

Then I back up my preferences in FF.

then I download from "here", [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html) and am surprised that it is still beta.
OOPS an unexpected thing happens. It asks me Save It or Use the Roller (recommended). Of course I do the recommended thing. Then I ask myself, where is this file? The window shows it in / but when I open an explorer window (I dont know what to call it?  "LS in GUI"?) it does not show FF in the / directory. 

  Naturally I continue my trust, I execute the next command. 
OOPS, it cant find FF. (Well we have that in common.) I get this:

THIS@THAT-desktop:~$ sudo tar -C /opt -jxvf firefox-3.0b2.tar.bz2
tar: firefox-3.0b2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

And so?

Now what. I had downloaded it previously from the same page and that time the dl box suggested the Archive Manager. I extracted it and expected an install file. So I guessed. The "diamond icon" did not execute. At that point I was lost.

----------------------------------------------------------
Later **Rolcol** posted and said:
there's no need to install the one from mozilla. It should be pre-compiled. Open up the firefox file inside the folder.

Well a. I cant run it (see just above) and b. It does not show up in applications.
Three strikes and you're out and I don't want to end the inning. (heh)
------------------------------------------------------------
**Rockerphil** tells me to pretend I am in windows. Using an emulator won't help me learn to install. It's not my path.

I don't want to be in Windows. We are here not there. Get the picture. I want to learn how to use Ubuntu.
[B][FONT="Arial"]-----------------------------------
And thanks for the help - I am still working on it.
-----------------------------------
[/FONT][/B]I might need to be the one to write the documentation. :-)

---

### Post by adobrakic on 2008-09-07
i just kinda skimmed over this thread, because I'm doing an essay, but I have a question; why don't you just do:

```

sudo apt-get install firefox-3.0

```

in terminal?

---

### Post by Xiong Chiamiov on 2008-09-07
The firefox-3.0 package isn't in the Fiesty repos (which is what he's running, right?).  However, he should be able to [download the .deb]("http://packages.ubuntu.com/gutsy/firefox-3.0") and just install that.

> **penguinv said:**
> 
History: Ubuntu works great. I have not figured out how to install programs.

[How to install Anything in Ubuntu]("http://209.85.141.104/search?q=cache:IfbspYjsGWIJ:www.monkeyblog.org/ubuntu/installing.html+how+to+install+anything+in+ubuntu&hl=en&ct=clnk&cd=1&gl=us")

---

### Post by aysiu on 2008-09-07
I wouldn't mix and match Gutsy and Feisty packages. That may lead to breakage or dependency hell.

Just follow these easy instructions:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

---

### Post by Xiong Chiamiov on 2008-09-07
> **aysiu said:**
> I wouldn't mix and match Gutsy and Feisty packages. That may lead to breakage or dependency hell.

Just follow these easy instructions:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)
Ah, well, yes, you're right.  I'm so used to rolling-releases that I don't think about dependency hell, and when I get it, it's not my fault. :)

And, as usual, aysiu had instructions done perfectly well on his site, which is where we should have looked in the first place.

---

