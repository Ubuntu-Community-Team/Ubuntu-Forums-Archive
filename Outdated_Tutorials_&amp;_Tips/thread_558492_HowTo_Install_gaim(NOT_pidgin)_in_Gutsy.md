---
title: "HowTo: Install gaim(NOT pidgin) in Gutsy"
date: 2007-09-24
forum: Outdated Tutorials &amp; Tips
---

### Post by leftyfb on 2007-09-24
For anyone that is like me and dislikes the new [_Pidgin Philosohpy_]("http://developer.pidgin.im/wiki/DesignGuidelines") of "While Pidgin is a multiprotocol IM client, the goal is to hide protocols from the user as much as possible.", this guide is for you. When I found out they removed the independent protocols from the buddy list, I thought it was a mistake. Unfortunately, it is not. And until they come up with a way to bring that back ([_which they refuse to do_]("http://developer.pidgin.im/ticket/414")), I will be sticking with gaim.

Here is how to install gaim  2.00 beta 6 from the gaim source files in Ubuntu 7.10 Gutsy gibbon as of Dec 07 2007.

```
sudo apt-get remove pidgin
```

```
sudo apt-get install build-essential libxml2-dev libglib2.0-dev libgtk2.0-dev
```

Download the source files [_here_]("http://files.filefront.com/Gaim+v20+Beta6+Tarball/;6610793;/fileinfo.html")

```
tar -jxvf gaim-2.0.0beta6.tar.bz2
```

```
cd gaim-2.0.0beta6
```

```
./configure 
```

```
make
```

```
sudo make install
```

```
sudo ln -s /usr/local/lib/libgaim.so.0 /usr/lib/
```

Now you should have "Gaim Instant Messenger" under Applications -> Internet

---

### Post by avel on 2007-09-24
FYI, in pidgin 2.2.0 the protocol icons are back, and the information of which protocol is used is very nicely and unobtrusively displayed, in both the buddy list window and the chat window.

The feature can be enabled through Buddies -> Show -> Protocol Icons.

The .deb for pidgin 2.2.0 from getdeb.net worked perfectly for me.

HTH.

---

### Post by leftyfb on 2007-09-24
> **avel said:**
> FYI, in pidgin 2.2.0 the protocol icons are back, and the information of which protocol is used is very nicely and unobtrusively displayed, in both the buddy list window and the chat window.

The feature can be enabled through Buddies -> Show -> Protocol Icons.

The .deb for pidgin 2.2.0 from getdeb.net worked perfectly for me.

HTH.

I did not know this. However, this is a half-assed compromise. Instead of replacing the pointless and unsightly green orbs on every buddy with the protocol icons like it used to be, they went ahead and kept the useless orbs and wasted most space and introduced more clutter by adding the protocol icons to the right. These icons are only labels for the protocols and do not show the buddy status like the orbs do in their place. 

I'll stick with gaim until they start listening to their users a bit more.

---

### Post by avel on 2007-09-24
> **leftyfb said:**
> Instead of replacing the pointless and unsightly green orbs on every buddy with the protocol icons like it used to be, they went ahead and kept the useless orbs and wasted most space and introduced more clutter by adding the protocol icons to the right. These icons are only labels for the protocols and do not show the buddy status like the orbs do in their place. 

Well, of course you are entitled to your opinion, as I am entitled to disagree. :)

IMHO the unified status icons are much better. I do not need to distinguish between the MSN occupied status and the Jabber busy status; they *should* look the same. The status icon is very user-friendly and informative.

But again, this is very much a personal preference. I have a colleague here who agrees with you and still does not like the way 2.2.0 displays it.

---

### Post by AirRaven on 2007-09-24
I have to say that the large section of the conversation window devoted to the User Info and Display Picture is a ridiculous amount of wasted space- what on Earth was wrong with the old system of having the display picture next to the message entry box?

Heck- is there any point whatsoever in devoting a hundred pixels of screen space to duplicating something written in the chat window's title full stop?

Thanks for the tutorial- that's much better. :)

---

### Post by Izkata on 2007-10-10
Finally!  Someone with some sense!

I'm favorite-ing this tutorial for when I need it in the future.

---

### Post by foureight84 on 2007-10-10
i wish you could use adium. but i actually like the new pidgin. but yes this is personal preference. good tutorial nonetheless. could be useful later on.

---

### Post by michael37 on 2007-10-11
I just upgraded to Gutsy for two reasons: first, to get Pidgin instead of just outdated gaim and second, to get Thunderbird 2.0 instead of outdated Thunderbird 1.5.

I guess I am sticking to pidgin, even though I hate its avian purple head.

---

### Post by GavinZac on 2007-10-13
> **Izkata said:**
> Finally!  Someone with some sense!

I'm favorite-ing this tutorial for when I need it in the future.

While I consider this thread pointless pedantry, the 'tutorial' itself is just the normal procedure for installing via make.

---

### Post by sstusick on 2007-10-13
> **AirRaven said:**
> I have to say that the large section of the conversation window devoted to the User Info and Display Picture is a ridiculous amount of wasted space- what on Earth was wrong with the old system of having the display picture next to the message entry box?

Heck- is there any point whatsoever in devoting a hundred pixels of screen space to duplicating something written in the chat window's title full stop?
Thank you!!

---

### Post by Izkata on 2007-10-17
> **GavinZac said:**
> While I consider this thread pointless pedantry, the 'tutorial' itself is just the normal procedure for installing via make.

Yeah, but it includes a link to the Beta6 source files.  They've been taken off the official websites.

---

### Post by Andreesie on 2008-01-03
> **leftyfb said:**
> 
[_here_]("http://files.filefront.com/Gaim+v20+Beta6+Tarball/;6610793;/fileinfo.html")

```
tar -jxvf gaim-2.0.0beta6.tar.bz2
```

hi,
i can download the files, then i saved it in sbin. but i can't  execute 
```
tar -jxvf gaim-2.0.0beta6.tar.bz2
```. it says:
> 
andreas@andreas-desktop:~$ tar -jxvf gaim-2.0.0beta6.tar.bz2
tar: gaim-2.0.0beta6.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

what should i do?:confused:

---

### Post by leftyfb on 2008-01-03
Who told you to save it to /sbin? NEVER save anything to /sbin.  Save it to your home directory or your Desktop. Somewhere where you have access to work on it. Then go into that directory to untar it using my original instructions.

---

### Post by Andreesie on 2008-01-03
Well, i downloaded it, and the save-screen-thingy opened in sbin, so i saved it there:|

but thanks, i'l try it again;)

---

### Post by leftyfb on 2008-02-11
Well, I noticed recently that MSN has stopped working in gaim. I also have reinstalled my main workstation to Gutsy from Feisty. So I took it upon myself to ask some of the developers in the office IRC channel #pidgin on irc.freenode.net. I was shot down again, being told that my need for having protocol icons is not a valid request and has no concrete reason behind it. Apparently these developers don't know the meaning of preference. A simple non-default option would be nice. 
I also asked if they are still supporting gaim for protocol service changes and/or security fixed. This was also shot down.

So I am basically forced to use pidgin until I can find a new solution. You have no idea how frustrating I get when looking at such a disgusting buddy list window. They say protocol icons are confusing, try looking at this mess. 

Alternative suggestions are welcome.

---

### Post by sstusick on 2008-02-11
I agree. Although there is an option on Pidgin 2.2.1 (default with Gutsy) that displays the protocol icons.

Go to BUDDIES > SHOW > Protocol Icons.

Hope this helps.

---

