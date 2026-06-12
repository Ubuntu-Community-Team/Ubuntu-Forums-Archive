---
title: "Need HELP to play .rm and .rmvb movies"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by vlad1975 on 2008-08-18
hi guys, 

please help me.. i got a collection of .rm and rmvb movies that i cant open or watch. i have intalled all possible codec on package manager but still cant play it., 

any suggestions?

---

### Post by tuxxy on 2008-08-18
Are you sure you installed the codecs, totem can play real files so I dont think you did, or you could try downloading the linux realplayer from their site.

---

### Post by Pro-reason on 2008-08-18
I've never heard of rmvb, but .rm is the extension for Real Media.  You need to go into the Synaptic package manager and install the Real Player.  Alternatively, you can use this command from the terminal:

```

sudo apt-get install realplayer

```

---

### Post by Shippou on 2008-08-18
totem can play .rmbv and .rm files by default. Just download the codecs when it prompts to do so. Or you can download them yourself. I don't know the command, though. Sorry.

I am using Linux Mint right now. And it has all the required codecs installed by default.

---

### Post by shimmey on 2008-08-20
I tried type "sudo apt-get install realplayer" in the terminal, but there's error:
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

And tried another way--download the realplayer from the offical website, but the firefox showed me "Page Load Error"!

Why? Anybody can help me? Thanks for all!

---

### Post by superzorro on 2008-08-20
This is because the program you are trying to install is not in the repositories.

You can download the Real Player linux client from:

[http://www.real.com/linux]("http://www.real.com/linux")

However, you should check the forums first, when I installed it in Feisty it messed up my icons, and it was a pain to change them back. But, who knows maybe since then, they have upgraded the program and causes no problem now.

Also, in the ubuntuguide there is an entry:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin")

---

### Post by indy415 on 2008-08-20
Hi shimmey,

I remember it took me a while to work out how to get realplayer installed (though I don't really use it anymore). 

Follow this link: [http://www.real.com/linux](http://www.real.com/linux) to download it - put it somewhere nice to get to.

Then open up a terminal and navigate to the directory where you put it e.g. cd /home/myname/downloads

Run this command: 

sudo chmod +x RealPlayer10GOLD.bin    

- makes the file useable for us.

And lastly run this command:

./RealPlayer10GOLD.bin 
 
in the terminal window and follow the instructions. 

Hope that works for you!

---

### Post by Pro-reason on 2008-08-20
> **superzorro said:**
> This is because the program you are trying to install is not in the repositories.
Yes, it is!  If you enable the right repos!  ;-)

Let's see... looking in Synaptic, I can see two repos containing Realplayer.

```

## UbuntuLinux Japan
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy/
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy-ja/
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy-experimental/
#deb-src http://archive.ubuntulinux.jp/ubuntu-ja hardy-experimental/

```

```

## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 5 Elyssa (stable) +++
deb http://packages.linuxmint.com elyssa main upstream import

## +++ Backports (not as stable) +++
deb http://packages.linuxmint.com elyssa backport

## +++ Community (not as stable) +++
deb http://packages.linuxmint.com elyssa community

## +++ Romeo (unstable) +++
#deb http://packages.linuxmint.com elyssa romeo

## +++ Source Repositories +++
#deb-src http://packages.linuxmint.com elyssa main upstream import
#deb-src http://packages.linuxmint.com elyssa community
#deb-src http://packages.linuxmint.com elyssa backport
#deb-src http://packages.linuxmint.com elyssa romeo

```

Add either of those to the bottom of your */etc/apt/sources.list* file, and you'll have access to the software.

---

### Post by rocka on 2008-08-24
> **indy415 said:**
> Hi shimmey,

I remember it took me a while to work out how to get realplayer installed (though I don't really use it anymore). 

Follow this link: [http://www.real.com/linux](http://www.real.com/linux) to download it - put it somewhere nice to get to.

Then open up a terminal and navigate to the directory where you put it e.g. cd /home/myname/downloads

Run this command: 

sudo chmod +x RealPlayer10GOLD.bin    

- makes the file useable for us.

And lastly run this command:

./RealPlayer10GOLD.bin 
 
in the terminal window and follow the instructions. 

Hope that works for you!

Hi,

I've just recently downloaded a couple of .rmvb files and had trouble playing them too, so I'm trying to work out how.

First I tried mplayer and then went and downloaded the codecs but that didn't work.

Then I found this thread, and followed the instructions above. ChangingRealPlayer10GOLD.bin to RealPlayer11GOLD.bin, as that was the version on that page. It seemed to go ok, except for the first line, as you can see from this copy'n'paste:


```
Copying RealPlayer files...No write-permission to  /etc/profile.d ...skip.
Succeeded.
installing application icons resource...
.installing document icons resource...
........Succeeded.
Configuring Mozilla...
Installing .mo locale files...
Setting selinux context...
/usr/share or /usr/bin no write-permission...skip.

RealPlayer installation is complete.
Cleaning up installation files...
Done.

merlin@merlin-desktop:~/Desktop$
``` 

Now there is a new menu item in Sound And Video - Real Player 11
But when I click it, it comes up with an error:
"Failed to execute child process "realplay" (No such file or directory)"

What can I do from here?



thanks for any help...

---

### Post by Pro-reason on 2008-08-25
Why do it manually when I've already pointed out that you can install this in the standard way via Synaptic?  (and it works)

---

### Post by rocka on 2008-08-25
> **Pro-reason said:**
> Why do it manually when I've already pointed out that you can install this in the standard way via Synaptic?  (and it works)

Hi,

I had already tried that [sorry, I had not made that clear in my earlier post] but searching on "real" didn't find anything. Then, I went looking through various threads found on google, and chased down various mplayer downloads and codecs etc etc. None of that worked either.

Now, I have tried to install the realmedia player manually and it didn't work either.


Looking back to your post above, you say:
> Add either of those to the bottom of your /etc/apt/sources.list file, and you'll have access to the software.

So, I went to that file and opened it in a text editor and pasted the two sections of code from your post above to the end of that file. But when I went to save it, I got another error message:
```
Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again.
```

I don't understand - I am not typing any location, I just want to add the extra lines to that file, and then save it over itself. [ie: I mean, I just want to update it - I'm not trying to change it's location]

...or should I? Why would I need to change the location?
And how would I know where the new location should be?


BTW this is on 8.04, if that changes things...

---

### Post by Pro-reason on 2008-08-25
> **rocka said:**
> 
So, I went to that file and opened it in a text editor and pasted the two sections of code from your post above to the end of that file. But when I went to save it, I got another error message:
```
Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again.
```
The error is one of permissions, as it says.  The part about the checking location is just one suggestion that the application is making for you to work out what has gone wrong.  Don't get stuck on it.

Since the file we want to edit is not in your home directory, you need to use super-user rights.  Otherwise, you don't have &#8220;permission&#8221; to edit the file.  That's part of the Linux security model.

To open an app as &#8220;root&#8221; or &#8220;super-user&#8221;, put &#8220;sudo&#8221; in front of it, or &#8220;gksu&#8221; for graphical apps.  For example:

```

gksu gedit */etc/apt/sources.list*
sudo nano  */etc/apt/sources.list*

```

You can also use a GUI to edit that file indirectly.  For example, you can run &#8220;gksu software-properties-gtk&#8221;, go to the &#8220;Third Party Software&#8221; tab and then click on &#8220;Add&#8221;.  That's also accessible in Synaptic.  Editing it with &#8220;sudo nano&#8221; really is the easiest way, though,

---

### Post by rocka on 2008-08-25
ok, well first let me say thanks a lot for taking the time to reply to me. That last response enabled me to add the extra lines to the file.

Unfortunately I'm still not having a lot of luck, I seem to be only slowly progressing one step at a time.

After editing the file, I re-started Synaptic. Searching on "real" in the name list still didn't find anything. Unsure of what to do next, I tried the "reload" button, thinking maybe the software hadn't taken notice of the new lines in that file I had just edited.

I got another new error message:
```
W: GPG error: http://archive.ubuntulinux.jp hardy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 058A05E90C4ECFEC
W: GPG error: http://archive.ubuntulinux.jp hardy-ja/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 058A05E90C4ECFEC
W: GPG error: http://archive.ubuntulinux.jp hardy-experimental/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 058A05E90C4ECFEC
```

I re-edited the file and took out the Japanese ones and only left in the mint ones and re-started Synaptic.

Success!!!! - I thought - I could now see Realplayer in the list of programs.

So I marked it for installation, went past the warnings telling me it was not authenticated, and applied the changes. I noticed it was trying to install version 10 [when I already had installed version 11 before] and then it came up with this error:

```
E: /var/cache/apt/archives/realplayer_1%3a10.0.9.809-20070726-0ubuntu0ja1_i386.deb: trying to overwrite `/usr/share/locale/ja/LC_MESSAGES/libgtkhx.mo', which is also in package helix-player
```

Now, there is no version 10 in the menu, but there is still version 11, which still comes up with the original error message:
```
Failed to execute child process "realplay" (No such file or directory)
```

---

### Post by Pro-reason on 2008-08-25
It's clashing with your manually-installed version.  That's why it's best only to install things via the package manager.

You'll have to clear out the other version somehow.

---

### Post by tilai on 2008-08-27
Does it mean I need to go to the list file and edit it? Or do I type it in the terminal?

> **Pro-reason said:**
> 
## +++ Source Repositories +++
#deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa main upstream import
#deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa community
#deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa backport
#deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa romeo
[/code]

Add either of those to the bottom of your */etc/apt/sources.list* file, and you'll have access to the software.

---

### Post by Pro-reason on 2008-08-27
> **tilai said:**
> Does it mean I need to go to the list file and edit it? Or do I type it in the terminal?

I don't know anything about the file you installed.  I assume it came with some sort of uninstallation instructions.

---

### Post by tilai on 2008-08-27
Real Player doesn't seem to be in my repository. I was asking how to add it to the repository.
> **Pro-reason said:**
> I don't know anything about the file you installed.  I assume it came with some sort of uninstallation instructions.

---

### Post by Pro-reason on 2008-08-28
> **tilai said:**
> Real Player doesn't seem to be in my repository. I was asking how to add it to the repository.

Ah sorry, I thought you were the other person.

To add the repositories, you have to open */etc/apt/sources.list* in a text editor and add those lines.

---

### Post by Xiangxianni on 2008-08-29
Can this Guide give you some help
[How to play rmvb movies using Mplayer in Ubuntu]("http://www.admin-faq.cn/how-to-play-rmvb-movies-using-mplayer-in-ubuntu")

---

