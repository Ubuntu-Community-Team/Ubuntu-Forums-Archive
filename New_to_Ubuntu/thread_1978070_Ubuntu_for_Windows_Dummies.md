---
title: "Ubuntu for Windows Dummies"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by broadway on 2012-05-11
Well actually she's my daughter who lives away from home.

Her Dell Inspiron laptop hard drive had problems and lost it's Windows 7 installation, of course she hadn't created a recovery disk. After a bit of messing I couldn't get Windows to install from some old disks so tried Ubuntu which was unbelievable quick and easy. So now I'm taking her laptop back tomorrow with a vanilla Ubuntu installation. Is there anything that will show a non-technical Windows user how to quickly get going on Ubuntu Desktop? 

A couple more questions.

Should I install a virus checker? I was going to put AVAST! on but it comes up with database error.

The only other application I can think of is a DVD player, what is recommended for an easy install?

---

### Post by Peripheral Visionary on 2012-05-11
**You** are actually your daughter's best resource for learning Ubuntu. Having a "Linux mentor" helped me quite a bit, even though I was using a so-called "kiddie distro with a Fischer-Price interface." A lot depends on what she's already used to - not just on the desktop, but perhaps on a PDA, cellphone, or tablet.

> 
Should I install a virus checker? I was going to put AVAST! on but it comes up with database error.

Not necessary. But if she insists on it, use ClamAV. It's lightweight and runs effortlessly in the background. Linux is safe unless you run as root ("Administrator") and *deliberately* do something risky. But having ClamAV on might reassure her that she's not passing on stuff to her Windows-using friends.

> 
The only other application I can think of is a DVD player, what is recommended for an easy install?

Ubuntu comes with it, but **VLC** is a very highly recommended favorite. Be sure that **ubuntu-restricted-extras **is installed as well (multimedia codecs). In 12.04 you can choose to have these downloaded and installed at installation of Ubuntu!

---

### Post by wilee-nilee on 2012-05-11
Should not need a av program. Trying to go from windows straight to linux is a bit of a tough ride for many. 

Here is the ubuntu manual.

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

A dvd should work, but there are codecs that can be installed to make sure dvd's and other media is read. This command will load flash, the codecs, and ms font.

```
sudo apt-get install ubuntu-restricted-extras
```Also install this and the commands after for more codecs, just copy and paste the whole line

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``````
sudo apt-get install libdvdcss2 
```then

```
sudo apt-get install w32codecs
```An excellent media player

```
sudo apt-get install vlc
```Have her use the forum, and there is a IRC channel for ubuntu as well #ubuntu

The IRC can be reached through xchat just install it and choose freenode, and type in /join #ubuntu in the bottom line to get there.

Hope this helps.

---

### Post by sadaruwan12 on 2012-05-11
Welcome to the forums friend !

For your first question this might help you follow the [link]("http://answers.yahoo.com/question/index?qid=20100930100055AAjAJx6").

Learning ubuntu is not a very big thing but if you have installed the very latest version of ubuntu then she might have get used to the unity and the new HUD.

But once she gets used to it then theres no turning back.

To your second question well, Linux is not Windows we don't have the issue of having to always look over our shoulder for various threats so no need to have a virus guard. If you fear that things that effect windows will effect Ubuntu don't worry 'cos this is completely a deferent platform and no software can run unless the user permits it.

As DVD player TOTEM is there in the OS but better to install VLC which is a very powerful player. You can find it in the Ubuntu Software Center.

And another thing please remember to make your daughter a member of this forum so she can ask anything and learn from us.

Have fun.

---

### Post by broadway on 2012-05-11
Thanks for the replies, I've not used Ubuntu, but do have some Linux experience from work, so Ubuntu is totally new to me, hence the cry for help. 

I didn't realise there was a DVD player in the installation, the DVD player was just a thought as I composed the message. I hadn't thought about VLC, but I will install it for her. 

Is there anything else she will need, I assume Ubuntu will handle camera connections and most of the Windows stuff, cd/DVD burning, pdfs flash etc without any problems.

Thanks for the manual link, looks just what she will need.

---

### Post by wilee-nilee on 2012-05-11
> **broadway said:**
> Thanks for the replies, I've not used Ubuntu, but do have some Linux experience from work, so Ubuntu is totally new to me, hence the cry for help. 

I didn't realise there was a DVD player in the installation, the DVD player was just a thought as I composed the message. I hadn't thought about VLC, but I will install it for her. 

Is there anything else she will need, I assume Ubuntu will handle camera connections and most of the Windows stuff, cd/DVD burning, pdfs flash etc without any problems.

Thanks for the manual link, looks just what she will need.

There is a program called cheese for web cams, usually an on board one, I have not used cams at all my self others might know better. Here is a link that might help.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

```
sudo apt-get install cheese
```The restricted extras will install flash, there is a stock pdf reader but you can install acroread which is the adobe reader.

```
sudo apt-get install acroread
```cd /dvd ripping and burning is easily done brasero is the stock app, some like kb3, that can be installed as well. With the codec installs previously given and the extras reading a dvd should be fine.

The doc writer libreoffice is installed I always install abiword as well some times a word .docx can have problems in libreoffice if it has been highly tweaked. You want to make sure she knows about saving stuff in a .doc at the least if it is to be opened in windows word  doc writer as well.

```
sudo apt-get install abiword
```

Keep asking questions though, we want you and the daughter to be comfortable at the least. :)

---

### Post by broadway on 2012-05-11
Thanks for the help.

 I'm getting to the stage now where I think she may be OK. I'll print the getting started bit of the manual for her which will give her somewhere to start.

The machine is at home so I can't check, but I checked install restricted extras so I may have some the codecs for DVDs. I've asked what other applications she may need and will try to get it sorted for tomorrow when I do the handover.  I'll have a play later on with word and excel docs.

So far things have been pretty simple, the last time I tried a Linux GUI LiveCD I couldn't get it to boot and gave up on it. I'll try installing a copy for myself so I can help her. 

So far so good:)

---

### Post by nothingspecial on 2012-05-11
You could tell her about here :)

---

### Post by wilee-nilee on 2012-05-11
> **broadway said:**
> Thanks for the help.

 I'm getting to the stage now where I think she may be OK. I'll print the getting started bit of the manual for her which will give her somewhere to start.

The machine is at home so I can't check, but I checked install restricted extras so I may have some the codecs for DVDs. I've asked what other applications she may need and will try to get it sorted for tomorrow when I do the handover.  I'll have a play later on with word and excel docs.

So far things have been pretty simple, the last time I tried a Linux GUI LiveCD I couldn't get it to boot and gave up on it. I'll try installing a copy for myself so I can help her. 

So far so good:)

Cool, make sure you get that wget run and the extra codecs W32 and libdvdcss2 as well they are dvd stuff.

---

### Post by grahammechanical on 2012-05-11
Why don't you put the icon for Help in the launcher? Then she can open the Ubuntu Desktop Guide whenever she needs it.

Open the Dash (Ubuntu icon at top of launcher), Type Help. Press enter. when the Desktop Guide loads it will put an icon in the launcher. right click the icon and select Lock to Launcher. When she no longer needs it she can right click and select Unlock from Launcher to get rid of it.

Also, should where to find System Settings. Power/cog icon, first on the list. The Appearance utility will let her change the desktop background wallpaper and if this is Ubuntu 12.04 she can also change to size of the launcher icons and whether the launcher is also on screen or only appears when the mouse is moved to the left side of the screen.

Again, if this is 12.04 show her that holding down the Super key (flying windows logo on it) will bring up an overlay of keyboard shortcuts.

Regards.

---

### Post by Curtis6767 on 2012-05-11
> **broadway said:**
> Thanks for the help.

 I'm getting to the stage now where I think she may be OK. I'll print the getting started bit of the manual for her which will give her somewhere to start.

The machine is at home so I can't check, but I checked install restricted extras so I may have some the codecs for DVDs. I've asked what other applications she may need and will try to get it sorted for tomorrow when I do the handover.  I'll have a play later on with word and excel docs.

So far things have been pretty simple, the last time I tried a Linux GUI LiveCD I couldn't get it to boot and gave up on it. I'll try installing a copy for myself so I can help her. 

So far so good:)

One thing you can do is teach your daughter how to use the Software Center. For instance, Acroread and Cheese are in there. One click installs them. One click uninstalls them.

You haven't said so I'm assuming you have 12.04 installed. If so, then the Software Center's icon on the Launcher is the bag that is stuffed with goodies. 

The Ubuntu development team has spent countless hours and $$ setting up the Software Center to make Ubuntu more accessible to noobs, like myself. Might as well take advantage of their efforts which lessens the learning curve for someone coming from Windows.

IMHO

---

### Post by xedi on 2012-05-11
Even though I have used Ubuntu a long time before the Unity desktop environment, I had to relearn a lot of stuff when it was introduced, so some tips from my experience:

The launcher on the left side is quite straight forward and intuitive so that does not need much explanation I think. The only thing you might consider is that if the screen is small, you can set it to autohide to have more screen space. So this might be quite advantageous for notebooks. (To reveal it you have to push the left border)

Unity offers a lot of screen space due to the global menus but they might be quite confusing for a windows user. You should probably tell her that to access her menus she has to hover over the panel to find file, edit, and so on. Alternatively or additionally you could also show her HUD (press alt and search for the menu entry you want).

Another thing is to encourage to take advantage of the intention driven design. The fastest way to open an application or a file is not to click yourself through menus and file managers but to type in the name/description/something associated of the application/file/folder into the dash (click on the ubuntu sign or windows/super key) if you know what you're looking for.

Shortcuts make Unity much more fun, e.g. the super key + w is great for windows switching. You can have an overview of all shortcuts when you push and hold the super key (on a blank desktop)

Edit: I was too slow regarding my last point :)

Finally, showing the software center and how to get and install apps would be good even though that should be totally straight forward.

---

### Post by Shadius on 2012-05-11
Your daughter may benefit from the Ubuntu tour on Ubuntu's website ([Ubuntu Tour]("Ubuntu.com")) to get her acquainted to Ubuntu. Although, it's a bit lacking in my opinion.
 
That's why I've come up with this idea: [Ubuntu Tour Idea]("http://brainstorm.ubuntu.com/idea/29706/"). 
If you support it, vote for it!

---

### Post by morhin on 2012-05-11
I love telling people about my experience with Ubuntu. 
I tried mepis and pclinux but struggled with some of it.
 
I found the book **Ubuntu for Non-Geeks (by Rickford Grant with Phil Bull) for the Lucid Lynx version 10.04** which is the last stable release. 12.04 is out now (release number is the year.month of the release) but it's going through the tweaking stages. 

Without this book I'd probably have gone back to windows. 

I'm so new I didn't even know what questions to ask.

I'll be getting the new book, for 12.04 when it comes out. It's great.

Good luck

Morhin

):P

---

### Post by deadflowr on 2012-05-11
In terms of DVD playing on ubuntu here:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

In terms of anti-virus and security here:

[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

In terms of basic Ubuntu introduction here:

[https://help.ubuntu.com/12.04/ubuntu-help/index.html]("https://help.ubuntu.com/12.04/ubuntu-help/index.html")

---

### Post by jaycee23 on 2012-05-11
Have a look at the link below. A fairly comprehensive post installation guide to useful / useless software!

[http://www.my-guides.net/en/guides/linux/330-ubuntu-1204-precise-pangolin-post-installation-guide](http://www.my-guides.net/en/guides/linux/330-ubuntu-1204-precise-pangolin-post-installation-guide)

You should find all the software you'll need.

---

### Post by broadway on 2012-05-11
Version 12.04 is installed.

I took the tour and it leaves a lot to be desired, I've sat thru more interesting power point presentations, aT least it was short so I didn't waste that much time. :lolflag:
I've got a DVD to play now after installing the codecs.

 I'm meeting her at a library and will spend an hour or going thru the basics. Abiword is in and the default for word docs. She can install VLC to learn about the software centre. Help is on the launcher and the manual on the desktop. She can  connect to the wi-fi using System Setting and I'll show her the forum should she need help. That should be enough to be going on with.

Super key and alt are very useful to know about, I've spent a lot of time wondering where the menu are, out of sight out of mind.

Thanks for the help, much appreciated

---

### Post by vandamme on 2012-05-11
I like Cinnamon better than Unity, because there's menus where you can pick out the apps out of categories even if you don't know what you have or what the names are. Unity is fine for touch screens and you only have seven apps, or you know what the names are. Everybody remembers what Gimp does, but Evince or Remmina??

---

### Post by evilsoup on 2012-05-11
> **morhin said:**
> I found the book **Ubuntu for Non-Geeks (by Rickford Grant with Phil Bull) for the Lucid Lynx version 10.04** which is the last stable release. 12.04 is out now (release number is the year.month of the release) but it's going through the tweaking stages.

It should be noted that 12.04 is pretty radically different from 10.04 so far as the GUI is concerned, to the extent that it might as well be a different operating system. So getting a book about 10.04 probably wouldn't be useful for someone who wants to know about 12.04.

---

### Post by QIII on 2012-05-11
Yes, you should install antivirus for two reasons:

1.  Attachments in emails from, and then forwarded to, Windows friends may contain viruses that will attack the recipient's machine.

2.  We should not convince ourselves of our invulnerability.  Although there are no Linux viruses "in the wild" YET, we don't know what some PFY in Des Moines is cooking up in his mom's basement at this very moment.  It probably won't be a virus in the current sense because the mechanisms of virus infection as in Windows is foreign to Linux.  BUT, it could be that we will be attacked by "ticks" or "chiggers" or whatever something like that might be called.

We should be practicing the same basic security measures as Windows users.

There is the misconception that there are no Linux viruses because the share is so low it's not worth it.  That's hogwash.  There is a substantial incentive to break into Linux:  Most of the internet backbone runs on Linux as do a great majority of corporate servers.  Simple access attacks occur all the time.  A mechanism for achieving in Linux what a virus can do in Windows or a Microsoft Server would be very profitable to crooks.

We should not count on "security by obscurity" or believe that there is no way to get in without being root or having temporarily raised privileges.

If you don't believe that, turn your machine off, reboot and hold the space bar down during the BIOS launch, wait for the GRUB menu to come up, go to recovery and select "root".  Take a look at who you are at that point.

Although that currently takes physical access, do we really believe that some smart teenager with a case of Mountain Dew wouldn't love to figure out a way to get there without access just to tell all of his friends what a Jedi Haxor he is?  Anti virus won't protect us from that, but having the anti-virus/security mindset will help us react when that time comes.  And it will come.

"Social Engineering" is also every bit as much a threat in Linux as Windows.

"Hey, cool, I found this!  Install it!", start the install, type your sudo password and you now have malware.

---

### Post by QIII on 2012-05-11
Hmmm.  Deleted.  Somehow that double posted.

---

### Post by Swagman on 2012-05-11
Should be interesting hearing her comments re: iTunes & iPhone connectivity !!

---

### Post by broadway on 2012-05-11
> **Swagman said:**
> Should be interesting hearing her comments re: iTunes & iPhone connectivity !!


She has a dumb phone and and I think her iPod nano broke so hopefully that won't be a problem :)

---

### Post by broadway on 2012-05-11
> **vandamme said:**
> I like Cinnamon better than Unity, because there's menus where you can pick out the apps out of categories even if you don't know what you have or what the names are. Unity is fine for touch screens and you only have seven apps, or you know what the names are. Everybody remembers what Gimp does, but Evince or Remmina??


Tried installing from here like this [http://www.linuxbsdos.com/2012/04/26/install-the-latest-and-greatest-cinnamon-desktop-on-ubuntu-12-04/](http://www.linuxbsdos.com/2012/04/26/install-the-latest-and-greatest-cinnamon-desktop-on-ubuntu-12-04/).

The install came up with a error:

sudo apt-get install cinnamon 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 cinnamon : Depends: gir1.2-muffin-3.0 but it is not going to be installed
            Depends: libcogl5 (>= 1.7.4) but it is not installable
            Depends: libmuffin0 (>= 1.0.0-0ubuntu1~precise) but it is not going to be installed
            Recommends: gnome-themes-standard but it is not going to be installed
            Recommends: gnome-session-fallback but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

