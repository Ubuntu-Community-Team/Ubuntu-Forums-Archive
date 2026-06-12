---
title: "How to Install Thunderbird"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by swarup on 2012-04-30
I need to install an earlier version of TB because I use a certain extension (Xnotes) which is not available for the later TB versions. I've downloaded TB 3.1.20, which is the version I want, and unarchived it from the tar.bz2. What is the command to install it? I've tried cd to the TB folder and "install", but it isn't working.

CORRECTION: The Xnotes add-on DOES say it works with TB 11.1. But there are a lot of reports of problems with general TB11.1 functionality. That is the reason I wish to stay with 3.1.20 for now.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
just run the thunderbird file inside of the extracted archive
also there is a updated version of that addon 
[https://addons.mozilla.org/en-US/thunderbird/addon/xnotepp/](https://addons.mozilla.org/en-US/thunderbird/addon/xnotepp/)

---

### Post by swarup on 2012-04-30
Thank you for your reply--

1. Yes, I am already running that version of Xnotes ++2.2.7.
2. When you say "run the thunderbird file inside of the extracted archive"-- there is a file by the name "thunderbird" in the extracted archive. When I double click on it, nothing happens. And if I select the option to run it in terminal, even then nothing happens.

---

### Post by SysBoot on 2012-04-30
```
sudo apt-get install thunderbird 
``` Does this work?

---

### Post by QIII on 2012-04-30
You are aware of this, are you not?

[http://www.mozilla.org/en-US/thunderbird/3.1/start/](http://www.mozilla.org/en-US/thunderbird/3.1/start/)

---

### Post by swarup on 2012-04-30
@ SysBoot: That command is going to download Thunderbird, and then install. And it is not specifying any version. I specifically want version 3.1.20. And I have already downloaded it. So I do not need the apt-get command. I just need to know how to install what I've already downloaded.

---

### Post by QIII on 2012-04-30
> **SysBoot said:**
> ```
sudo apt-get install thunderbird 
``` Does this work?

That will get the most recent version, which is what the OP is trying to avoid.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **swarup said:**
> Thank you for your reply--

1. Yes, I am already running that version of Xnotes ++2.2.7.
2. When you say "run the thunderbird file inside of the extracted archive"-- there is a file by the name "thunderbird" in the extracted archive. When I double click on it, nothing happens. And if I select the option to run it in terminal, even then nothing happens.
[http://www.mediafire.com/?x2sm2l002k9n0bn](http://www.mediafire.com/?x2sm2l002k9n0bn)
i recorded myself doing it

---

### Post by QIII on 2012-04-30
Does the Thunderbird "file" from the archive have an .sh extension?

---

### Post by swarup on 2012-04-30
> **QIII said:**
> You are aware of this, are you not?

[http://www.mozilla.org/en-US/thunderbird/3.1/start/](http://www.mozilla.org/en-US/thunderbird/3.1/start/)

Yes, thank you. For the benefit of others here, your link says:

> This version of Thunderbird will be obsolete from April 24th, 2012. You will no longer have the benefit of security and stability enhancements.

I made the decision not to go to version 11.*, because everyone is complaining about it. 

So I just need to know how to install the 3.1.20 which I've downloaded.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **QIII said:**
> Does the Thunderbird "file" from the archive have an .sh extension?
no, at least not in recent versions but no the less it is a shell script

---

### Post by swarup on 2012-04-30
> **QIII said:**
> Does the Thunderbird "file" from the archive have an .sh extension?

No, it does not. It is a "shell script" though, which I think should be executable.

There is however another file, called "run-mozilla.sh". Having used files like this before as executables, I have also tried to run this one-- both by double-clicking, and in terminal. But it did not work either.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **swarup said:**
> Thank you for your reply--

1. Yes, I am already running that version of Xnotes ++2.2.7.
it should work on thunderbird 11.1 *goes to try it*
edit 
no issues here 
[http://i.imgur.com/NtKBx.png](http://i.imgur.com/NtKBx.png)

---

### Post by QIII on 2012-04-30
Everyone?

An absolute statement is rendered void by a single anecdotal example to the contrary.

Consider me that anecdote.  There are millions more, I suspect.

Your conflict seems to be an add-on.  That is a valid reason for you to use an older version, but it does not mean there is something wrong with the current version.  What is means is that an add-on developer hasn't kept up.

---

### Post by swarup on 2012-04-30
> **pqwoerituytrueiwoq said:**
> [http://www.mediafire.com/?x2sm2l002k9n0bn](http://www.mediafire.com/?x2sm2l002k9n0bn)
i recorded myself doing it

Thank you. I am downloading it. My download speed is very slow right now; it is going to take 20 minutes. Then I'll listen to it,

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **swarup said:**
> Thank you. I am downloading it. My download speed is very slow right now; it is going to take 10 minutes. Then I'll listen to it,
good thing i compressed it then saved about 700kb lol
edit:
so glad i don't have sub 1MB DSL anymore :)

---

### Post by swarup on 2012-04-30
@pqwoerituytrueiwoq & QIII: Both of you have made correct points. Let me clarify: Xnotes does indeed say it works with 11.1. The thing is that there have been many complaints in general with TB 11.1, with losing mail, with problems with the inbox, etc. Due to which many users are sticking with 3.1.20. And that is what I want to do for the time being, until it becomes clear the 11.1 is working smoothly.

---

### Post by CharlesA on 2012-04-30
> **QIII said:**
> You are aware of this, are you not?

[http://www.mozilla.org/en-US/thunderbird/3.1/start/](http://www.mozilla.org/en-US/thunderbird/3.1/start/)

This. I would rather have to stop using a depreciated addon than deal with a mail client that isn't getting security updates.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **swarup said:**
> @pqwoerituytrueiwoq & QIII: Both of you have made correct points. Let me clarify: Xnotes does indeed say it works with 11.1. The thing is that there have been many complaints in general with TB 11.1, with losing mail, with problems with the inbox, etc. Due to which many users are sticking with 3.1.20. And that is what I want to do for the time being, until it becomes clear the 11.1 is working smoothly.
i suggest you check your account settings (Edit -> Account Setting)

@CharlesA
but this addon** does** work on TB11.1

---

### Post by swarup on 2012-04-30
@pqwoerituytrueiwoq: Well the download finished and I decompressed it. It is an mpeg file, but it doesn't play. At least not on my IMAC.

---

### Post by swarup on 2012-04-30
Everyone: The add-on does work on TB11.1. But complaints about 11.1 are rampant all over the internet, and on the TB support forum. Many threads on the TB support forums are there where people are writing they want to go back to 3.1.20 or 3.1.21 because 11.1 is a huge problem. Even though there are no security updates, but even the TB support forum moderators are suggesting that people stay with the 3.1.20 and 3.1.21 for now. 

Is anyone here using TB11.1 and if so, what is your experience? It certainly would be easy to install it, via the install center.

Can someone please tell me how to install my TB 3.1.20 which I've installed? Which is the file that one uses as the installer file? I'll just cd to the directly and it should install.

---

### Post by CharlesA on 2012-04-30
> **pqwoerituytrueiwoq said:**
> 
@CharlesA
but this addon** does** work on TB11.1

Thank you. I haven't had any problems when I was running TB 11.1, but I'm running TB 12 now.

If the addon works in 11.1, it should work in 12, no?

EDIT: That said, I haven't run Thunderbird 3.x in a long while. I upgraded to TB 5 when it was released and have been upgraded as new versions are released.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
i recored it with xvidcap
do you have ubuntu restricted extras installed?
it plays fine in my totem,smplayer,vlc, and firefox on my 10.04

---

### Post by swarup on 2012-04-30
> **CharlesA said:**
> Thank you. I haven't had any problems when I was running TB 11.1, but I'm running TB 12 now.

If the addon works in 11.1, it should work in 12, no?

I do not know. Their [website]("https://addons.mozilla.org/en-US/thunderbird/addon/xnotepp/") only reports that it works up to 11.*. So I cannot say. 

What version of TB installs from the repository for Ubuntu 12.04? Is it TB11.*, or 12?  CharlesA, did you say you found 11.1 to work fine? If so, maybe I should try it. At least the Ubuntu software center will install it for me.

---

### Post by mastablasta on 2012-04-30
> **swarup said:**
>  But complaints about 11.1 are rampant all over the internet, and on the TB support forum. 

there are also many thread all over internet how linuzx doesn't really work. on the same "internet" that uses linux mostly to be able to give these websties and all that. so....

i am not sure about your extension. i only use lightning calendar. and it works well both on windows and linux with latest version of TB.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **swarup said:**
> I do not know. Their [website]("https://addons.mozilla.org/en-US/thunderbird/addon/xnotepp/") only reports that it works up to 11.*. So I cannot say. 

What version of TB installs from the repository for Ubuntu 12.04? Is it TB11.*, or 12?  CharlesA, did you say you found 11.1 to work fine? If so, maybe I should try it. At least the Ubuntu software center will install it for me.
you have not tried 11.1 yet!?
have not had any issues but i have been using the latest version of tb since before the day 10.04 came out
only one bug (pre-dates tb11) sometimes html messages are displayed as plain text but i just click a different email and go back to it

---

### Post by CharlesA on 2012-04-30
It looks like the version of TB in the Precise repos in 11.0.1.

---

### Post by swarup on 2012-04-30
> **pqwoerituytrueiwoq said:**
> i recored it with xvidcap
do you have ubuntu restricted extras installed?
it plays fine in my totem,smplayer,vlc, and firefox on my 10.04

I didn't have ubuntu restricted extras installed, but now I am installing it. 

But the odd thing is, it wouldn't even allow me to past your mpeg file onto the ubuntu desktop! (I running ubuntu virtually on my mac-- it is working beautifully!) Anyhow, perhaps it will allow me to paste it there once the ubuntu restricted extras is installed...

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **swarup said:**
> I didn't have ubuntu restricted extras installed, but now I am installing it. 

But the odd thing is, it wouldn't even allow me to past your mpeg file onto the ubuntu desktop! (I running ubuntu virtually on my mac-- it is working beautifully!) Anyhow, perhaps it will allow me to paste it there once the ubuntu restricted extras is installed...
if you are trying to copy it into a virtual machine i would give the virtual machine a briged net adapter and install openssh-server and copy it from the host OS into the virtual machine
[FONT=Courier New]scp /path/to/test-0000.mpeg user@192.168.1.125:~/Desktop/[/FONT]

---

### Post by swarup on 2012-04-30
> **pqwoerituytrueiwoq said:**
> if you are trying to copy it into a virtual machine i would give the virtual machine a briged net adapter and install openssh-server and copy it from the host OS into the virtual machine
[FONT=Courier New]scp /path/to/test-0000.mpeg user@192.168.1.125:~/Desktop/[/FONT]

I'm sorry, this virtualization technology is new to me--I just installed it last week--I just looked in the ubuntu software center for a bridged net adapter, but there isn't anything like that. Where do I get it?

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **swarup said:**
> I'm sorry, this virtualization technology is new to me--I just installed it last week--I just looked in the ubuntu software center for a bridged net adapter, but there isn't anything like that. Where do I get it?
that is done from the Host OS
i have never used a MAC for more than 5 min but this is how i do it on a ubuntu's virtual box

a bridged net adapter puts the virtual machine on the same network as the host OS so it is not isolated on the network, thus allowing yuo to access your local file servers/ssh servers or run a server in a virtualbox and access it from another box

---

### Post by Irihapeti on 2012-04-30
I'm using Thunderbird 12.01 and xnote seems to be working OK (I don't use it a lot).

I don't use the version from the repositories. I prefer to download the version from the Mozilla website. You can do this using Ubuntuzilla (I believe it's in the repositories). Or you can install manually, which happens to be my preference.

I've had no problems with lost mail or any of the other things mentioned.

---

### Post by swarup on 2012-05-01
> **Irihapeti said:**
> I'm using Thunderbird 12.01 and xnote seems to be working OK (I don't use it a lot).

I don't use the version from the repositories. I prefer to download the version from the Mozilla website. You can do this using Ubuntuzilla (I believe it's in the repositories). Or you can install manually, which happens to be my preference.

I've had no problems with lost mail or any of the other things mentioned.

Ok, sounds very good. I'll try 12.01 then. Once I download it from the mozilla website, can you tell me the exact steps used to install it manually?

---

### Post by Irihapeti on 2012-05-01
Whichever method you use, backup your ~/.thunderbird folder first. That contains all your mail and settings.

I would suggest using Ubuntuzilla because it automates the installation.

Instructions for installing Ubuntuzilla PPA are at [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

There's also a help area in the third party projects section of this forum.


The purely manual method involves the following:

Download the tar.bz2 file from Mozilla
Extract the archive where you want to run it. (/opt is my preference but there are no doubt other options.)

You can then either change your launcher so that it points to where you've installed Thunderbird, or make a symlink. In my case, it's:

```
sudo ln -s /opt/thunderbird/thunderbird /usr/bin

```
For the update function to work, your installation folder needs to be owned by you. It's probably best to change ownership only when you are updating and then change it back again when finished.

---

### Post by swarup on 2012-05-01
Thanks! I'll definitely try the ubuntuzilla approach. Now, using ubuntuzilla, the final step they give--and this is where TB actually gets installed--is:

```
sudo apt-get install thunderbird-mozilla-build

```

Does that automatically select the latest version of TB available, i.e. 12.0.1? Or if not, then how would I specify that this is the version I want?

---

### Post by Irihapeti on 2012-05-02
I've not used Ubuntuzilla myself for several years now, so I can't answer that question.

I'd suggest trying it and seeing what happens, and if there's an issue, post a message in the Ubuntuzilla sub-forum.

Best of luck.

---

### Post by swarup on 2012-05-02
Now, if I select the manual method, then once I extract the archive, which file in the folder do I have to run to install it? If you can tell me the exact name of the file and what the command is, that will be marvelous. 

Also, on another forum someone had instructed me to place the TB folder in my home folder:

> Then, move that folder to where your user has permissions. When I do a local install like this, I make an applications folder in my home folder.So, you would have ~/applications/thunderbird

Would you agree to this as a good approach? Being in my folder I guess I would have ownership of the folder, right-- so that way updates would automatically come?

---

### Post by pqwoerituytrueiwoq on 2012-05-02
that would be a good approach IMO personally i would make it .applications or .apps just so i dont see it in my home folder without a ctrl+h key cobo but that is just me

---

### Post by alphacrucis2 on 2012-05-02
> **swarup said:**
> Everyone: The add-on does work on TB11.1. But complaints about 11.1 are rampant all over the internet, and on the TB support forum. Many threads on the TB support forums are there where people are writing they want to go back to 3.1.20 or 3.1.21 because 11.1 is a huge problem. Even though there are no security updates, but even the TB support forum moderators are suggesting that people stay with the 3.1.20 and 3.1.21 for now. 

Is anyone here using TB11.1 and if so, what is your experience? It certainly would be easy to install it, via the install center.

Can someone please tell me how to install my TB 3.1.20 which I've installed? Which is the file that one uses as the installer file? I'll just cd to the directly and it should install.

I use T'Bird 12 in both Linux and Windows. Can't say I have seen any issues with it

---

### Post by Irihapeti on 2012-05-02
There are sometimes differences between the version in the Ubuntu repos and the version available on the Mozilla website - at least, in my experience, which is why I choose to get the Mozilla version. (Plus I sometimes share the profile with Windows.)

Also remember that with any piece of software, complaints will always seem more obvious. After all, if something is working well, there's much less reason to go to the trouble of registering and posting about it on a forum.


Re the location of the install, /opt just happens to be the one I prefer, but somewhere in your home folder would also be fine. (I have some apps in ~/bin).

---

### Post by swarup on 2012-05-02
If I select the Ubuntuzilla method, I am installing a PPA, first. So I'll get whatever the latest version is in that PPA. How can I find out what is the latest version in that PPA? I want TB 12.0.1. If that is what they have, then I can use this method. Otherwise I will have to install it manually.

I am reposting the below question, because I do not think anyone replied to it:

> If I select the manual method, then once I extract the archive, which file in the folder do I have to run to install it? If you can tell me the exact name of the file and what the command is, that will be marvelous.

---

### Post by jtarin on 2012-05-02
Note the web address:
[http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/)

---

### Post by Irihapeti on 2012-05-02
Swarup:

Unlike most tarballs, the Mozilla downloads aren't source code. Once you have extracted the tarball, you run the file /path/to/thunderbird/thunderbird, which is a binary and launches thunderbird.

So, in my case, it's 

```
cd /opt
sudo tar -xjvf [tarball.tar.bz2]
/opt/thunderbird/thunderbird
```

Replace "tarball.tar.bz2" with the real name of the download, obviously.

---

### Post by swarup on 2012-05-02
Ok, wonderful! 

jtarin-- thank you for pointing out that 12.0.1 is indeed the latest version. I see that there is an i386 as well as an amd64 version. When I run the ubuntuzilla install, will it automatically select the amd64 version since my Ubuntu OS is 64bit?

Irihapeti, thank you! Now that is all very clear. 

Perhaps my last question is, if we need to uninstall ubuntuzilla's TB for any reason (i.e. still not working well and we want to go back to 3.1.x), then what is the process for the uninstall? Any time something is to get installed any other way but the Ubuntu software center, then I like to know in advance how to uninstall since it is sometimes quite a complex task.

---

### Post by Irihapeti on 2012-05-02
With a manual install, removal is done via

```
sudo rm -r /opt/thunderbird
```

Change that according to where you've done your installation.

For the procedure with Ubuntuzilla, perhaps you could ask in the Ubuntuzilla sub-forum. I've not used Ubuntuzilla for several years, so I'm not up with all the details.

---

### Post by swarup on 2012-05-02
Ok, great. Thank you for all your help! It has been perfect, as always.

As for the ubuntuzilla subforum, it doesn't seem very active-- I did post one question there and no one replied yet-- it's been 19 hours...anyhow, jtarin has ultimately given the answer in this current thread here.

But I can try again with this other question and see if anyone responds. Thanks again, and I'll mark this thread as [solved].

---

