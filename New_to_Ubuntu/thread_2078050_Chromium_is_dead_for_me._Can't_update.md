---
title: "Chromium is dead for me. Can't update"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-10-30
As an "average" user I can't be bothered making my own build which is what you seem to have to do now to update. I hope I'm wrong.

Chromium is the open source version of Google's Chrome web browser.

When Google released the Chrome web browser in 2008, it also released its source code to the public through the Chromium project. The code was issued under the BSD (Berkeley Software Distribution) license, which meant that the source code for Chromium may be freely used, copied, modified, and distributed for use in other programs.

But the Chromium Project seems to be controlled by Google again. Their website 
[http://code.google.com/p/chromium/wiki/LinuxBuildInstructions](http://code.google.com/p/chromium/wiki/LinuxBuildInstructions)
says: "We don't provide any sort of "install" step."

Please tell me I'm wrong.

---

### Post by monkeybrain2012 on 2012-10-30
Install chromium from this ppa

 [https://launchpad.net/~a-v-shkop/+archive/chromium](https://launchpad.net/~a-v-shkop/+archive/chromium) 

Here are the  steps, 

open a terminal and type

```
sudo add-apt-repository ppa:a-v-shkop/chromium 
```Then run 

```
sudo apt-get update
sudo apt-get upgrade
```If you already has chromium installed, this will upgrade it to the latest version (or the latest version offered by the ppa) Henceforth it will be part of the regular Ubuntu updates.

If you have not installed chromium yet,  replace "sudo apt-get upgrade" with
```

sudo apt-get install chromium-browser
```

This will install the latest stable version and it will be updated as a part of regular Ubuntu updates.

If you want the latest beta, replace

"ppa:a-v-shkop/chromium"

  with
"ppa:a-v-shkop/chromium-dev" above.

---

### Post by AlexDudko on 2012-10-30
Isn't it in the universe repository?

---

### Post by monkeybrain2012 on 2012-10-30
> **AlexDudko said:**
> Isn't it in the universe repository?

It is already installed by default since OP uses Lubuntu, but it won't get updated. The ppa provides the updated version.

---

### Post by Kevin McCready on 2012-10-30
Thanks guys, but I think I might look for another browser unless you persuade me otherwise. My reasoning is this. When I ran 
sudo add-apt-repository ppa:a-v-shkop/chromium

a message came up saying

"While Chromium Team won't release new versions of Chromium browser I will try to maintain more-or-less fresh releases of Chromium
 More info: https://launchpad.net/~a-v-shkop/+archive/chromium"

When I went to that website, it seems that Alex Shkop is doing it and it says "untrusted PPA".

So I'm not sure I should rely on one person. What if he goes on holidays? And how can one person maintain a project like this?

This all started because an Gooogle message popped up saying I might not be protected because my browser was outdated or something.

Is there another good open source browser?

---

### Post by monkeybrain2012 on 2012-10-30
Well then use Firefox. I always find it works better than Chrome/Chromium. Lubuntu is usually installed on old machines. Contrary to the common perception. I find Firefox a lot lighter actually. Chromium may start up faster but uses a lot of memory and after opening a few tabs it becomes a resource hog and gets sluggish. If you are the kind of person who have many tabs open and your machine is a few years old FF is definitely best in terms of performance. On weaker machines where I install Lubuntu I always remove chromium and install Firefox instead. 

BTW I actually don't see much point of Chromium, many people on Linux install Chrome because of updated flash but that is not going to happen in chromium anyway.

---

### Post by AlexDudko on 2012-10-30
Midori is a lightweight browser.

---

### Post by screaminj3sus on 2012-10-30
> **monkeybrain2012 said:**
> Well then use Firefox. I always find it works better than Chrome/Chromium. Lubuntu is usually installed on old machines. Contrary to the common perception. I find Firefox a lot lighter actually. Chromium may start up faster but uses a lot of memory and after opening a few tabs it becomes a resource hog and gets sluggish. If you are the kind of person who have many tabs open and your machine is a few years old FF is definitely best in terms of performance. On weaker machines where I install Lubuntu I always remove chromium and install Firefox instead. 

BTW I actually don't see much point of Chromium, many people on Linux install Chrome because of updated flash but that is not going to happen in chromium anyway.

Firefox is lighter on memory (ironically its known for being the memory hog, but thats not really true these days, chrome definitely uses way more memory than firefox). But I find chrome performs much better on modern machines. Chrome has opengl acceleration that actually works for example (firefox's opengl layers barely work atm, at least on intel), opengl rendering for flash, and opengl decoding and rendering for html5 video. Chrome's smooth scrolling also works much better on my machine (this has a nice ivy bridge cpu, and sometimes on certain sites firefox's smooth scrolling will take up a lot of cpu and lag, while chrome's is always smooth). In addition I find chrome's ui is generally more responsive and less prone to hangs under load.

Its really a mileage may vary type of thing, I'm sure firefox is better on some machines, and chrome on others. Depends on the hardware. In my personal experience if your machine has the memory to spare chrome tends to perform better.


Anyway, regarding the update situation, I just use google's chrome rather than chromium, having a few closed source bits doesn't bother me (actually quite the contrary, the extra codecs and integrated pdf reader are quite nice).

---

### Post by I2k4 on 2012-10-30
I "silo" Google's own services in Chrome, because they run better on it than competing browsers and Snoople tracks you through them anyway.  For general use I'd suggest Firefox or Opera, which is surprisingly good and in the Lubuntu repositories.  Opera is even updating in my expired Lubuntu 10.10 installation.

---

### Post by monkeybrain2012 on 2012-10-30
> **screaminj3sus said:**
> Firefox is lighter on memory, but I find chrome performs much better on modern machines. Chrome has opengl acceleration that actually works for example (firefox's opengl layers barely work atm, at least on intel), opengl rendering for flash, and opengl decoding and rendering for html5 video. Chrome's smooth scrolling also works much better on my machine (this has a nice ivy bridge cpu, and sometimes on certain sites firefox's smooth scrolling will take up a lot of cpu and lag, while chrome's is always smooth).

Its really a mileage may very type of thing, I'm sure firefox is better on some machines, and chrome on others. Depends on the hardware. In my personal experience if your machine has the memory to spare chrome tends to perform better.


Anyway, regarding the update situation, I just use google's chrome rather than chromium, having a few closed source bits doesn't bother me (actually quite the contrary, the extra codecs and integrated pdf reader are quite nice).

Well I regularly have over 100 tabs open in Firefox and Chrome just can't handle it (up to maybe 40 is fine with the addon tabmemfree) I see no difference in terms of scrolling speed, both are fast and smooth (even though FF has a lot more tabs open) I guess that may be hardware related. The only thing that Chrome is 'faster' is on start up, but even then it takes its time to load all the tabs so it is not really that much faster (In FF tabs are loaded on demand) 

FF also has better multi-media support through gecko-mediaplayer (which is kind of broken or not working well in Chrome) Everyone is talking about flash but what about non flash content? In Linux gecko-mediaplayer is probbaly the best if not the only way to access a lot of those contents (Totem has codecs problems often) So that leaves flash. Well flash 11.2 still works very well on Firefox and I have not encountered one site which requires me to have higher version. But best of all, I don't even need flash to access most flash videos thanks to two amazing greasemonkey scripts (ViewTube and Linterna Magica) They renders videos in mplayer or totem and works much better and smoother than flash anyway.so for me, I just keep chrome around in the unlikely event that I need flash absolutely and the system one no longer works.

---

### Post by AlexDudko on 2012-10-30
> **I2k4 said:**
> I "silo" Google's own services in Chrome, because they run better on it than competing browsers and Snoople tracks you through them anyway.  For general use I'd suggest Firefox or Opera, which is surprisingly good and in the Lubuntu repositories.  Opera is even updating in my expired Lubuntu 10.10 installation.

Opera doesn't work correctly with some css and javascript - this browser is not often a web developer's target.

---

### Post by monkeybrain2012 on 2012-10-30
Op asks for free browser and opera is not free. Opera is not in Lubuntu's repository by default, you have to add it (or maybe installing the deb would automatically add the repository)

---

### Post by CaptainMark on 2012-10-30
Its not the responsibility of the chromium developers to package it for Ubuntu. If it were they would spend all their time packaging it for every different DE and architecture. If canonical wanted Ubuntu to ship with the latest build of chromium then they should package it so, clearly they either aren't fussed or have a good reason to maintain an older version. Thankfully some kind person spends time packaging the most up to date version in the previously mentioned ppa

---

### Post by Kevin McCready on 2012-10-30
thanks again. Lots of food for thought. But Comments above seem to be talking more about chrome than chromium. 

Now I understand that "packaging" has to be done for each different linux distribution (I guess that means "building"?)

I don't mind an old version as long as it is doing what I want and is "safe". When Captain Mark said they were "maintaining" an old version. Does that mean it's regularly automatically updated for security?

---

### Post by BBQdave on 2012-10-30
No [Seamonkey]("http://www.seamonkey-project.org/") fans?  :D

---

### Post by Kevin McCready on 2012-10-31
I tried midori - when I increased the minimum size font it overwrote other fonts on the screen. So purged that.

I tried firefox but it doesn't seem easy to restore your tabs when you reopen. So I purged that.

I imagine the last post was a joke, so I didn't try seamonkey-browser.

Back to the drawing board.

---

### Post by CaptainMark on 2012-10-31
> **Kevin McCready said:**
> thanks again. Lots of food for thought. But Comments above seem to be talking more about chrome than chromium. 

Now I understand that "packaging" has to be done for each different linux distribution (I guess that means "building"?)

I don't mind an old version as long as it is doing what I want and is "safe". When Captain Mark said they were "maintaining" an old version. Does that mean it's regularly automatically updated for security?
Yes packaging is taking the source code and turning into a program that your computer will be able to run, and no the version in the ubuntu/lubuntu software centre is old complete with any bugs and security vulnerabilities that have been discovered since it was last packaged, I would recommend not to use the version in the repos if its more than one or two versions old, im running version 22

---

### Post by ArminasAnarchy on 2012-10-31
Just wanted to throw in a +1 for switching to Firefox. I'm currently running the Aurora build from this ppa: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/firefox-aurora](https://launchpad.net/~ubuntu-mozilla-daily/+archive/firefox-aurora)

I've seen someone has already posted on how to add ppa's to your system.

What I like about Firefox is the speed and stability - I can testify to to it being able to have loads of tabs open (which I've noticed other browsers lag with). KDE integration is far from perfect though - for instance, I've had to manually point it towards the Dolphin executable in /usr/bin/ in order to use the (right click)>Open File Location option on Downloads, and to get it to run files via double clicking (thankfully Dolphin has the sense to be able to find the required program automatically once the file's opened with Dolphin).

Just as a note on Aurora too - it's nice to be at the bleeding edge and (personally) I've not noticed any problems with the builds in terms of stability/incompatibility with plugins etc

Magnet links are the only thing I still have trouble with, and I don't know how to associate Ktorrent with them. At the moment I'm copying and pasting the link from Firefox into Ktorrent manually, if anyone knows how to get around this, suggestions would be appreciated?

---

### Post by ArminasAnarchy on 2012-10-31
> **ArminasAnarchy said:**
> Just wanted to throw in a +1 for switching to Firefox. I'm currently running the Aurora build from this ppa: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/firefox-aurora](https://launchpad.net/~ubuntu-mozilla-daily/+archive/firefox-aurora)

I've seen someone has already posted on how to add ppa's to your system.

What I like about Firefox is the speed and stability - I can testify to to it being able to have loads of tabs open (which I've noticed other browsers lag with). KDE integration is far from perfect though - for instance, I've had to manually point it towards the Dolphin executable in /usr/bin/ in order to use the (right click)>Open File Location option on Downloads, and to get it to run files via double clicking (thankfully Dolphin has the sense to be able to find the required program automatically once the file's opened with Dolphin).

Just as a note on Aurora too - it's nice to be at the bleeding edge and (personally) I've not noticed any problems with the builds in terms of stability/incompatibility with plugins etc

Magnet links are the only thing I still have trouble with, and I don't know how to associate Ktorrent with them. At the moment I'm copying and pasting the link from Firefox into Ktorrent manually, if anyone knows how to get around this, suggestions would be appreciated?

Firefox sync is also really handy since I move between a University and home computer fairly regularly. I'm not sure if this feature is present in other browsers?

---

### Post by amjjawad on 2012-10-31
19 posts? and there is nothing about what version/release the OP is using?

@OP
Could you PLEASE tell us what version of Lubuntu are you using? I'm a member of Lubuntu Team and I've been with Lubuntu for some years now and I have never faced any issue with Chromium. But yes, it is dead for you as the title of your thread is saying.

Let's make it as simple as possible and I would really appreciate if you enlighten me with the version of your system.

I will do what I can to help :)

Many thanks!

---

### Post by vasa1 on 2012-10-31
> **amjjawad said:**
> 19 posts? and there is nothing about what version/release the OP is using?

@OP
Could you PLEASE tell us what version of Lubuntu are you using? I'm a member of Lubuntu Team and I've been with Lubuntu for some years now and I have never faced any issue with Chromium. But yes, it is dead for you as the title of your thread is saying.

Let's make it as simple as possible and I would really appreciate if you enlighten me with the version of your system.

I will do what I can to help :)

Many thanks!
There **is** a problem with Chromium. It has been discussed several times in the forum.
People occasionally do the job of making more recent builds available but these are available via ppas and not from the default software sources.

FYI, [https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002641.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002641.html)

BTW, I find it interesting that people repeatedly refer to **Evil Google** but still want to use its products.

---

### Post by amjjawad on 2012-10-31
> **vasa1 said:**
> There **is** a problem with Chromium. It has been discussed several times in the forum.
People occasionally do the job of making more recent builds available but these are available via ppas and not from the default software sources.

FYI, [https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002641.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002641.html)

BTW, I find it interesting that people repeatedly refer to **Evil Google** but still want to use its products.

> **amjjawad said:**
> I've been with Lubuntu for some years now and **I** have never faced any issue with Chromium. **But yes, it is dead for you** as the title of your thread is saying.


But thanks for the information :) now, I know there is some problems with Chromium.

For me, it was always working fine. I also have Firefox. I can't live without both. I always have two, Chromium and Firefox. Both work fine.

Thanks :)

---

### Post by vasa1 on 2012-10-31
> **amjjawad said:**
> But thanks for the information :) now, I know there is some problems with Chromium.

For me, it was always working fine. I also have Firefox. I can't live without both. I always have two, Chromium and Firefox. Both work fine.

Thanks :)
While Chromium from the Software Center works fine, nowadays people are very sensitive about "security" and Evil Google makes a point of how they make their browser more secure with each iteration. For example, you can see this page: [http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/)

So although a browser may work just fine, people want the latest in the belief that the latest is safer.

To that extent, not being in a position to offer  the latest version is a negative.

I've read enough to convince me that building Chromium is not a trivial task. If it's not possible because of manpower or hardware issues, it would be better to just not offer outdated browsers.

---

### Post by amjjawad on 2012-10-31
> **vasa1 said:**
> While Chromium from the Software Center works fine, nowadays people are very sensitive about "security" and Evil Google makes a point of how they make their browser more secure with each iteration. For example, you can see this page: [http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/)

So although a browser may work just fine, people want the latest in the belief that the latest is safer.

To that extent, not being in a position to offer  the latest version is a negative.

I've read enough to convince me that building Chromium is not a trivial task. If it's not possible because of manpower or hardware issues, it would be better to just not offer outdated browsers.

Perhaps I'm wrong and mistaken but as long as you are connected to the internet, you are not safe nor secure.

If you prevent Google from tacking your moves, you can't prevent other websites, etc.

This is off topic I guess so I won't go further but this is what I think and I don't believe when they say this is secure, etc. 

Anyway, it's always good to be around and discuss some stuff ;)

---

### Post by Linuxisfast on 2012-10-31
If you are worried about privacy which in itself is a misnoner while on net, use Ghostery and Easy Privacy filter with Adblock, you would be surprised how much gets blocked. You can always opt out for Google's privacy intruding aspect by unchecking in the Chrome settings.

---

### Post by Kevin McCready on 2012-10-31
For unsophisticated users like me, isn't that rather dangerous of ubuntu.com to leave old versions lying around?

---

### Post by Kevin McCready on 2012-10-31
I use: 
Ubuntu 11.10
Chromium (NOT GOOGLE CHROME) 18.0.1025.168 (Developer Build 134367 Linux)

---

### Post by Kevin McCready on 2012-10-31
I forgot to say in relation to using Google while also criticising them that there is no logical problem. In software, as in politics, it's a question of choosing the least worst option.

---

### Post by amjjawad on 2012-10-31
> **Kevin McCready said:**
> I use: 
Ubuntu 11.10
Chromium (NOT GOOGLE CHROME) 18.0.1025.168 (Developer Build 134367 Linux)

Don't you think you should have mentioned that on your first post? :) and Why have you used [lubuntu] tag if this is Ubuntu?

As far as I remember, version 18 is the default that comes with 11.10 and I can't really remember if that was updated to a newer version? I don't have 11.10 on any of my Test Machines right now.

Just one Q:
Is the browser working and you just can't upgrade it?

Thanks!

P.S.
Can anyone with version 11.10 please confirm whether he/she has a new version rather than 18?

---

### Post by Kevin McCready on 2012-10-31
I installed Lubuntu which I think uses some Ubuntu components. Chromium is working but I can't update it. 

I have been warned again by the same person who has accused me of  trolling. Let me say for the record that all my comments are genuine and I am not a troll. I have been asked to go the the Resolution Centre. Does anyone know how to do that?

---

### Post by CharlesA on 2012-10-31
> **Kevin McCready said:**
> 
I have been warned again by the same person who has accused me of  trolling. Let me say for the record that all my comments are genuine and I am not a troll. I have been asked to go the the Resolution Centre. Does anyone know how to do that?

Post here:
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by amjjawad on 2012-11-01
> **Kevin McCready said:**
> I installed Lubuntu which I think uses some Ubuntu components. Chromium is working but I can't update it. 

When I started to use Linux, I have learned that if something (system or program) is working fine, there is NO need to upgrade it OR in another word, it is NOT a must to upgrade it.

I'm not 100% sure but again, as far as I remember, by default, 11.10 is using Chromium version 18.

If it is a big issue for you (just assuming it is) and you really need the newer version badly, you can install Lubuntu 12.04 or 12.10.

What people really need to understand:
1- The newer version doesn't mean necessarily it is better than the previous one.
2- If it is not broken, why to fix it?

Just sharing my thoughts and experience :)

YES indeed, the difference between Lubuntu and Ubuntu is here:

[https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu](https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu)

---

### Post by CharlesA on 2012-11-01
> **amjjawad said:**
> What people really need to understand:
1- The newer version doesn't mean necessarily it is better than the previous one.
2- If it is not broken, why to fix it?

When it comes to browsers, it is usually a good idea to have the latest version, as it may plug security holes that existed in previous versions.

The same applies to other software too - Ubuntu does this by pushing security updates, which should include the browsers too.

---

### Post by amjjawad on 2012-11-01
> **CharlesA said:**
> When it comes to browsers, it is usually a good idea to have the latest version, as it may plug security holes that existed in previous versions.

The same applies to other software too - Ubuntu does this by pushing security updates, which should include the browsers too.

You are right, thanks for correcting me. My notes were very much general or perhaps wrong too!

---

### Post by monkeybrain2012 on 2012-11-01
> **amjjawad said:**
> 
If it is a big issue for you (just assuming it is) and you really need the newer version badly, you can install Lubuntu 12.04 or 12.10.


Sorry man, this doesn't make a lot of sense because as long as Lubuntu doesn't update its Chromium package the versions in 12.04 or 12.10 will be outdated soon as well (if not already because feature freeze months before release) I am not adverse to upgrading to a new release, but to go through the risks and the troubles to get the updated browser just isn't worth it. PPA is definitely the best route.

I have Lubuntu 11.10 on one machine, just checked synaptic, chromium version is 11.80.1025.168. But like I said, I got rid of Chromium and installed Firefox which works a lot  smoother  on my ancient Dell Inspiron 8500 and I always get the latest version (16.0.2). On top of lacking regular maintenance, I don't understand why the Lubuntu team considers Chromium "light weight". On this machine with 512 mb of ram opening up a few tabs will kill it.

---

### Post by amjjawad on 2012-11-03
> **monkeybrain2012 said:**
> Sorry man, this doesn't make a lot of sense because as long as Lubuntu doesn't update its Chromium package

I'm sorry but this is not correct. If I do remember correctly, I do get updates/upgrades on my Lubuntu System for Chromium. I will keep a close eye on this the next time an update/upgrade is there.

> I have Lubuntu 11.10 on one machine, just checked synaptic, chromium version is 11.80.1025.168. 
How come it is version 11? 
I'm on the LiveCD of Lubuntu 11.10 on my test machine and the version of Chromium by default is: 14
And I'm sure last time I was on 11.10 before I formatted and installed Lubuntu 12.04, my Chromium was 18.


> I got rid of Chromium and installed Firefox which works a lot  smoother  on my ancient Dell Inspiron 8500 and I always get the latest version (16.0.2). 
Of course, everyone is using what he/she finds it better for him/her :)
Above all, Linux gives you more freedom and more options.

> On top of lacking regular maintenance, I don't understand why the Lubuntu team considers Chromium "light weight". 

I understand you are not a developer but you can have a look at this:
[https://wiki.ubuntu.com/Lubuntu/Developers#Roadmap](https://wiki.ubuntu.com/Lubuntu/Developers#Roadmap)

We do have a discussion before each and every release to decide what App to keep or what to remove. Feel free to join us and start that discussion yet again ;)
We do have this every release. You can check the threads on the Archive of the mailing list and you will find it.

[https://lists.ubuntu.com/archives/lubuntu-users/](https://lists.ubuntu.com/archives/lubuntu-users/)


Don't blame the system :)
Beside, usually, what goes for Ubuntu, goes for Lubuntu as well: [https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu](https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu)

---

### Post by vasa1 on 2012-11-03
FWIW, view 6:40 here [http://www.youtube.com/watch?v=Sp4E5iuGJl4](http://www.youtube.com/watch?v=Sp4E5iuGJl4)

---

### Post by SWGraphics291 on 2012-11-03
You can always use firefox and get firebug if you are a developer.

---

### Post by phillw on 2012-11-03
> **monkeybrain2012 said:**
>  .... Lubuntu doesn't update its Chromium package the versions in 12.04 or 12.10 will be outdated soon as well (if not already because feature freeze months before release) I am not adverse to upgrading to a new release, but to go through the risks and the troubles to get the updated browser just isn't worth it. PPA is definitely the best route....



Hi, 

That the Ubuntu Chromium PPA is not being updated is a simple case of not enough volunteers to keep it so. It seems oft forgotten that all the people are volunteers.

Alex has offered to keep a set of updates on his PPA (they were for 12.04), discussions had been started to restart the Ubuntu-Chromium PPA, as it is a hope that Alex well be liasing with the luubntu team on maintaining this and having used his PPA area for quite some time, you could far worse than add it in order to get updates. 

[http://askubuntu.com/questions/177207/is-chromium-in-ubuntus-repository-safe-to-use-since-its-so-out-of-date](http://askubuntu.com/questions/177207/is-chromium-in-ubuntus-repository-safe-to-use-since-its-so-out-of-date)

The -release team did include the most up to date release available for Lubuntu in the 12.10 release. But, with no active PPA it is already out of date.

I will chase up as to what is happening for 12.10 and as to if alex will upkeep the ubuntu Chromium PPA area. 

In the meantime... [https://launchpad.net/~a-v-shkop/+archive/chromium](https://launchpad.net/~a-v-shkop/+archive/chromium) It holds many versions for older releases.

Regards,

Phill.

---

### Post by Kevin McCready on 2012-11-03
Thanks again everyone. It looks like I might try firefox again. BUT how do you make it reload all your tabs at each startup?

---

### Post by critin on 2012-11-03
> **Kevin McCready said:**
> Thanks again everyone. It looks like I might try firefox again. BUT how do you make it reload all your tabs at each startup?

Under History there is Restore Previous Session and at Recently Closed Tabs there's  Restore All Tabs.  

It's probably not automatic so you'll have to do some clicking.  There may be another way but I haven't looked further.

---

### Post by doorknob60 on 2012-11-05
> **Kevin McCready said:**
> Thanks again everyone. It looks like I might try firefox again. BUT how do you make it reload all your tabs at each startup?

Go to Firefox menu -> options -> general -> "When Firefox starts" -> Show my windows and tabs from last time. I didn't try it (I don't want to restart my browser right now), but that sounds like it should work.

---

### Post by amjjawad on 2012-11-06
> **critin said:**
> Under History there is Restore Previous Session and at Recently Closed Tabs there's  Restore All Tabs.  

It's probably not automatic so you'll have to do some clicking.

+1
See attached screenshot.

---

### Post by vasa1 on 2012-11-06
Coming soon ...
[https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003006.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003006.html)
> I hope to get official PPAs running in the next few weeks for all
supported releases of Ubuntu (L,O,P,Q), with Stable channel first,
perhaps even within 7 days, and beta and dev soon thereafter.
and this is from a person with a Canonical e-mail address.

---

### Post by amjjawad on 2012-11-06
> **vasa1 said:**
> Coming soon ...
[https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003006.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003006.html)

and this is from a person with a Canonical e-mail address.

You beat me to it.

This Email from my mentor Phill Whiteside who is a Lubuntu Member as well and the first person who accepted me to the team and showed me the way. So, HUGE YES, he knows what he is doing.
Julien is the main developer of Lubuntu and LXDE.
Chad MILLER is our guy :D

We were discussing here:
[https://www.facebook.com/groups/lubuntu.official/](https://www.facebook.com/groups/lubuntu.official/)

And I was about to come and update this thread but you beat me to it.

So, hope in the coming weeks/days, we will get updates :D

---

### Post by NadirPoint on 2012-11-06
> **vasa1 said:**
> If it's not possible because of manpower or hardware issues, it would be better to just not offer outdated browsers.
This^^.  I liked Chrome(ium) and for a couple years had no issues until recently probably starting around springtime IIRC, when I began getting random lockups and crashes for no apparent reason.  This continued even after at least one Chromium update offered through the normal 12.04 repository.  I finally gave up and went back to Firefox.

Oddly, the Chrome browsers (even older versions) I use on some Windows PCs at work never skipped a beat.  Makes you wonder...

---

