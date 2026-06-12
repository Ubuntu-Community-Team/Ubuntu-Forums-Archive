---
title: "SRWare Iron doesn't load???"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by zaivala on 2014-03-22
OK, I now have my "new' computer up and running, Precise Pangolin 64-bit, went to get my favorite browser (SRWare Iron), found the .deb package, installed it, ran it... and nothing happens. Am I missing a library? What is wrong?

Moss

---

### Post by Korkel on 2014-03-22
Can you open the browser in a terminal?

---

### Post by zaivala on 2014-03-22
Might not be in the right directory... tried a few things, no luck yet.

What directory should I be in? I've tried cd / and nothing happens. Probably in /usr?

LOL dummy here used backslash. Got my directories working... still haven't found the right one.

---

### Post by Frogs Hair on 2014-03-22
There may be a missing lib and that was affecting Chrome last year . I haven't used iron in a while and I think I had to install a lib the last time I did.
[http://askubuntu.com/questions/369310/how-to-fix-missing-libudev-so-0-for-chrome-to-start-again](http://askubuntu.com/questions/369310/how-to-fix-missing-libudev-so-0-for-chrome-to-start-again)

---

### Post by zaivala on 2014-03-22
> **Frogs Hair said:**
> There may be a missing lib and that was affecting Chrome last year . I haven't used iron in a while and I think I had to install a lib the last time I did.
[http://askubuntu.com/questions/369310/how-to-fix-missing-libudev-so-0-for-chrome-to-start-again](http://askubuntu.com/questions/369310/how-to-fix-missing-libudev-so-0-for-chrome-to-start-again)

Seems to be affecting 13.x releases, I'm still using Precise.

And I still can't find the directory it installed Iron in... it's not in /opt ...

---

### Post by zaivala on 2014-03-22
OK, I'm checking usr/bin and usr/lib ... but the ls command doesn't have a pause on it... and only scrolls back so many entries.

Now using |more and still cannot find google, chrome, srware, or iron in my usr/bin or usr/lib directories... found chrome libraries but no proggies.

---

### Post by Frogs Hair on 2014-03-22
If you have synaptic installed you can check for libs mentioned in the post, but they may not be required for 12.04 . I installed Chrome on a 12.04 installation recently with no need to add anything. I will download Iron and give it a try on 13.10.


Edit: Installed Iron successfully with the Gdebi package installer because the software center wasn't cooperating .

---

### Post by zaivala on 2014-03-22
OK, looked it up in Synaptic, and it installed to usr/share/iron . I went to that directory, and tried to run iron, to no avail.

zaivala@zaivala-desktop:/usr/share/iron$ iron
No command 'iron' found, did you mean:
 Command 'cron' from package 'cron' (main)
 Command 'imon' from package 'isdnutils-base' (universe)
iron: command not found

zaivala@zaivala-desktop:/usr/share/iron$ ls |more
chrome_100_percent.pak
chrome.pak
chrome_remote_desktop.pak
chrome_sandbox
chrome-wrapper
content_resources.pak
extensions
iron
libavcodec.so.52
libavformat.so.52
libavutil.so.50
libffmpegsumo.so
locales
product_logo_48.png
resources
resources.pak
zaivala@zaivala-desktop:/usr/share/iron$ 

When I try to run iron, it says there is no such command. I checked for a subdirectory iron, no such directory.

I assume I'm missing a library... but I know what a faulty assumption is.

---

### Post by Frogs Hair on 2014-03-22
It is named iron32 or iron64 in synaptic depending what version you installed. Normally that is the command used to launch from the terminal. The lib that was causing the Chrome problem is available at the linked page in section 22 .

[http://askubuntu.com/questions/286075/dependency-error-while-installing-google-chrome-on-ubuntu-13-04](http://askubuntu.com/questions/286075/dependency-error-while-installing-google-chrome-on-ubuntu-13-04)

---

### Post by zaivala on 2014-03-22
Tried that. No such animal. It's just named 'iron' in the directory... should I be launching it from a different directory?

---

### Post by Frogs Hair on 2014-03-22
Try the following which is the name of configuration file in hidden folders.

```
chromium
```

Edit: [https://www.srware.net/forum/viewtopic.php?f=18&t=3764](https://www.srware.net/forum/viewtopic.php?f=18&t=3764)

---

### Post by zaivala on 2014-03-22
> **Frogs Hair said:**
> Try the following which is the name of configuration file in hidden folders.

```
chromium
```

Edit: [https://www.srware.net/forum/viewtopic.php?f=18&t=3764](https://www.srware.net/forum/viewtopic.php?f=18&t=3764)

Nope. Tried that in Home, usr, usr/share and usr/share/iron directories (in Terminal). No luck.

A friend pointed out that I was not using the 'sudo' command when using 'where". I tried it, and it just showed me the same thing I already knew, that iron is in /usr/share/iron . Still does not run in Terminal.

Question:  THere are several *.pak files in that directory. Is it possible they need to be unzipped by something? Or am I treeing up the wrong bark?

---

### Post by zaivala on 2014-03-22
OK, stupid person here.  I tried loading iron using 'sudo'.

zaivala@zaivala-desktop:/$ sudo /usr/share/iron/iron
/usr/share/iron/iron: error while loading shared libraries: libudev.so.1: cannot open shared object file: No such file or directory
zaivala@zaivala-desktop:/$ 

So it is, indeed, a missing library.  Where/how do I get this? I'll go try Synaptic. Or look in my current directories and see if it is misplaced.

OK, Synaptic says I have libudev0 installed. Is this the lib I need, or ???

---

### Post by zaivala on 2014-03-22
zaivala@zaivala-desktop:/usr/share/iron$ sudo apt-get --reinstall install iron
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package iron
zaivala@zaivala-desktop:/usr/share/iron$ 


...and just because I'm stupid, I ran that in Home, usr, and usr/share as well as the shown usr/share/iron

Is the package broken?

Edited to add: I'm getting a bit ready to give up... I would also state that my Windoze machine has Precise Puppy on it (32-bit), and iron32 runs just fine on it...

---

### Post by A.O._Stanley on 2014-03-23
I gave up on Iron quite some time ago. I couldn't even get it to work in Windows. Not sure what happened between various upgrade versions but, like you, I could download it and see it the Dash but it wouldn't load. I'll keep watching this thread for a solution so good luck with that.

---

### Post by vasa1 on 2014-03-23
OP, did you choose the 64-bit version of the browser? Your OS is 64-bit according to your first post.

I don't use Iron and so can't comment for sure.

---

### Post by zaivala on 2014-03-23
Iron works great for me in WIndows 8 32-bit and has worked great in Windows 7 32-bit. It also works great for me in Precise Puppy 32-bit, which, other than being 32-bit, is based on the same kernel and repositories as Ubuntu Precise Pangolin.

If you had read all the messages, you could see that we have been talking about iron64, which is the 64-bit.

I did get a copy of Chromium. It is not as satisfactory but I'll fake it.  Iron saves my bookmarks and all on the web, so no matter what computer I load it on (assuming it runs) I have all my bookmarks, which is a major feature for me. Firefox used to have a plugin which did that, but they stopped using it; Iron has it automatic when I log in.

Those of you who don't know this, which is maybe one or two of those reading this, know that chromium is the open-source project which Google ran to see if they could make a good, fast browser. Chrome is taking that code and adding a bunch of Googleness to it. Iron is chromium with almost all the Googleness, which was in chromium, stripped out. So that is also a selling point if you're not big into Google.

---

### Post by vasa1 on 2014-03-23
> **zaivala said:**
> ...
If you had read all the messages, you could see that we have been talking about iron64, which is the 64-bit.
...
Yes, I did. Nowhere did you mention that you're trying 64-bit Iron. Anyway, all the best.

---

### Post by zaivala on 2014-03-23
Sorry, I thought that replying to Frog telling me to run "iron64" would have given it away.

---

### Post by Dennis N on 2014-03-23
If the executable (**iron**) is located in the folder **/usr/share/iron** (as post #8 indicates) then you need to cd to /usr/share/iron and then use the command **[FONT=Courier New]./iron[/FONT]** in the terminal instead of **iron**

That's because **/usr/share/iron** is not in $PATH which is where bash looks for the location of executables. That's also why you get "iron: command not found".

---

### Post by zaivala on 2014-03-23
Aha! I'll try that. See, told you I'm a n00b.

---

### Post by zaivala on 2014-03-24
Tried it. No difference. Guess Iron just isn't meant for Precise. No response from the Iron forum -- in fact I don't think the moderators have even approved my post yet.

---

### Post by zaivala on 2014-04-24
I updated to Trusty and tried again. Iron installed OK... 

Now it says it can't use my Iron profile because I'm using an older version. This is truly weird, as I am using 31 on both my Windoze Notebook PC and my Ubuntu Desktop PC. (yes, the download page still says 29 but the version you get with the download link is now 31)

So I sort of have Iron working. As usual, the Iron forum at SRWare requires all posts to be approved by the Administrator, and it seems like s/he gets around to that at least once a month.

---

