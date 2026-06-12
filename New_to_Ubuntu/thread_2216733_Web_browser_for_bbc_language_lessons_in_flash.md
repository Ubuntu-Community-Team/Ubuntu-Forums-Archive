---
title: "Web browser for bbc language lessons in flash"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by fangorn2 on 2014-04-13
Hello.

The bbc.co.uk website stores very interesting and well crafted language video lessons.
The lessons are made in Flash, so in theory they would be watchable using Firefox or Chrome, but I have installed Adblock Plus in both these browsers and for this reason (verified before installing Adblock Plus in Windows' Internet Explorer) I will not be able to load any lesson into the player anymore. Disabling Adblock Plus would not change anything. I do not understand this behaviour though... The only options I have is to remove Adblock Plus from Firefox or Chrome, or try another browser. Under Windows the latter option works with Comodo Dragon. Anyway I do not want to remove Adblock Plus or switch to Windows any time I want to learn some spanish and then return to Linux for anything else.

I tried Konqueror but it seems to have limitations in providing multimedia contents. No spanish lessons with Konqueror.

What browser would you recommend? I found there are many, and I would not like to install and try all of them before discovering that none of them will be able to satisfy my needs.

I would appreciate your advice on the matter.
The following is a useful link to verify what I said:

[http://www.bbc.co.uk/languages/spanish/mividaloca/](http://www.bbc.co.uk/languages/spanish/mividaloca/)

Thanks in advance for your help

---

### Post by tea for one on 2014-04-13
Good evening

Please confirm if you have already installed the package "Ubuntu Restricted Extras" from the software centre?

I use Firefox in Ubuntu 12.04 with the Restricted Extras package so that Flash content works.

I also have Adblock plus enabled and I navigated to the Spanish videos on the BBC site and did not encounter any difficulty in listening to/watching the lessons?

Have you received any sort of error message?

---

### Post by peter d on 2014-04-13
+1 to the above. I have Firefox with Adblock enabled and everything works just fine.

---

### Post by fangorn2 on 2014-04-13
Hi.
I have Ubuntu 12.04 LTS and Adobe Flash plugin is installed: Flash contents generally work in Firefox and Chrome, but they do not work for the language lessons. 
Same behaviour in Windows: I am unable to watch Flash from bbc (both in my notebook and in my desktop computer). 
This is the error message I receive:

"Sorry! The connection seems to be running below the minimum speed required. Please try again later."

I am able to watch the lessons with Comodo Dragon (and with Internet Explorer before installing adblock plus) in Windows.
So it should not be a connection speed issue. I have a good 7 Mbps connection.

I am glad you are able to watch and listen to the lessons. This means that I might be able to do it myself with some adjustment.

The package "Ubuntu Restricted Extras" is not installed. I tried to install it and I received the following warning:

To install Ubuntu restricted extras these items must be removed:
Libav codec library
libav codec53

Libav utility library
libavutil51

As I said Adobe Flash plugin is already installed and I do not have any problem in watching and listening to multimedia contents. Would it be safe and worth trying to proceed with removing the above libraries and installing 'Ubuntu Restricted Extras'?

---

### Post by tea for one on 2014-04-13
I am on uncertain ground when various libraries are quoted.

However, Ubuntu Restricted Extras has been around for years and invariably solves the difficulties of enjoying multimedia content.

Make a note of the libraries that you are considering to remove, remove them via Synaptic and install the Restricted Extras package.

You can always return to where you started if you proceed carefully.

Do you have Synaptic installed?

Synaptic is a more extensive software installer/remover with a GUI.

---

### Post by monkeybrain20122 on 2014-04-13
Works for me on both Firefox and chrome and I have adblock installed and activated for both. See screenshot.

> **fangorn2 said:**
> 
To install Ubuntu restricted extras these items must be removed:
Libav codec library
libav codec53

Libav utility library
libavutil51

As I said Adobe Flash plugin is already installed and I do not have any problem in watching and listening to multimedia contents. Would it be safe and worth trying to proceed with removing the above libraries and installing 'Ubuntu Restricted Extras'?

Yes, these will be removed because they are the 'stripped' versions and installing restricted extras will replace them with the 'unstripped' ones with names like liavutil-extra-51 (these are the versions with all the goodies which may be legally problematic for canonical to distribute but ok for you to download yourself, hence 'extras')

---

### Post by buzzingrobot on 2014-04-13
Firefox with Flash on 14.04 here.  I, too, see that "Sorry! The  connection seems to be running below the minimum speed required. Please  try again later." several seconds after a lesson begins, but Flash is  clearly working before that.

I have seen that same message trying  to view other Flash video at other BBC sites. I'm offered a BBC speed  test and the results always show more than adequate bandwidth. 

I also have access to a VPN. The results are the same when I use that with a London entry point.

This  may be Flash-related.  Flash consumes bandwidth.  It might also be that  the way the BBC sites measure bandwidth available to users is broken.

---

### Post by monkeybrain20122 on 2014-04-13
> **buzzingrobot said:**
> Firefox with Flash on 14.04 here.  I, too, see that "Sorry! The  connection seems to be running below the minimum speed required. Please  try again later." several seconds after a lesson begins, but Flash is  clearly working before that.

I have seen that same message trying  to view other Flash video at other BBC sites. I'm offered a BBC speed  test and the results always show more than adequate bandwidth. 

I also have access to a VPN. The results are the same when I use that with a London entry point.

This  may be Flash-related.  Flash consumes bandwidth.  It might also be that  the way the BBC sites measure bandwidth available to users is broken.

Which version of Firefox? I use FF28 on two computers  connected through two different networks (home earlier and starbucks now) Both worked perfectly. Ubuntu 13.10.

Now the only 'unusual' thing in my setup is I always set flash to activate when asked instead of automatically load (kind of works like flashblock). Not sure that makes any difference though.

---

### Post by buzzingrobot on 2014-04-13
FF28 here, too.  I checked with Flash set to ask to activate:  Same results.  Curious.

---

### Post by buzzingrobot on 2014-04-13
Well...  curiouser:

When I disable (not remove, just disable) AdblockPlus in Firefox, the videos load and run.  

Now, Adblock puts a red "ABP" logo in the toolbar.  You can click on it to disable Adblock.  When I am on that BBC page and click on the logo, there are options to disable on bbc.co.uk, on "this page" only, or "everywhere".  Selecting any of the three options allows the video to load. (And the logo changes from red to black.)

---

### Post by monkeybrain20122 on 2014-04-13
Hmm. I am using adblock edge instead of adblock plus. Don't know if that makes a difference.

---

### Post by buzzingrobot on 2014-04-13
> **monkeybrain20122 said:**
> Hmm. I am using adblock edge instead of adblock plus. Don't know if that makes a difference.

I've done a quick Google and found this:

1.  Right click on a empty space on that BBC page.

2. A FF menu pops up, with "Adblock Plus: Block Image" at the bottom.  Click on it.

3. A panel opens displaying some filter patterns based on the site's URL. The "Blocking Filter" is pre-selected. If I deselect that, and select the "Exception Rule" at the right, and then check one of the BBC filters below, and click the save button, the videos load without otherwise disabling Adblock Plus.

Since I have not told Adblock Plus to block any BBC sites, I'm at a loss to understand why it did, short of a bug or misinterpreting a Flash element on the page as an ad.

But, at least I know how to get rid of that annoying problem, and, hopefully, it works for the OP.

---

### Post by fangorn2 on 2014-04-13
I already tried to disable Adblock Plus, all the options you listed, but the problem still persists.
Morover, as I said, it happens not only in Ubuntu, but also in Windows. In Windows only with a lighwheight browser like Comodo Dragon I am able to quickly load the lesson, that's why I was wondering if any of you know any browser different from Firefox or Chrome to suggest.

---

### Post by monkeybrain20122 on 2014-04-13
Well you can test firefox with a fresh profile. 
1)Close Firefox. 
2)Open the file browser, press ctrl+h (or from the menu choose "show hidden files"), find the folder .mozilla and rename it to something like .mozilla-old
3) restart Firefox and go to bbc
After finish testing revert to the old profile
4) close Firefox
5) delete .mozilla
6) rename .mozilla-old back to .mozilla

---

### Post by fangorn2 on 2014-04-13
It did not work.
Even with a fresh profile I was unable to load any lesson and received the same error message :(

---

### Post by buzzingrobot on 2014-04-13
Midori, which bills itself as a lightweight browser, is in the repos.  I've used it for about ten minutes, but it worked fine. The Gnome folks have Epiphany, which is in the repos as "epiphany-browser". I don't know how much of Gnome it would want to pull in.

---

### Post by fangorn2 on 2014-04-13
Same problem with Midori. 
I don't know what to do now... 
Anyway I think I will love Midory.

---

