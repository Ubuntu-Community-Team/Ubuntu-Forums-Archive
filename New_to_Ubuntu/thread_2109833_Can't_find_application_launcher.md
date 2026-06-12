---
title: "Can't find application launcher"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by Fibie on 2013-01-28
I am running Ubuntu 12.04 as a complete newbie. I have been reading various guides which say that to run applications you need the application launcher, ie as shown ion this diagram.

I have tried alt + F2, but this keyboard shortcut is disabled in my distro. I then tried to enable the shortcut, by going to system settings/keyboard/shortcuts and enabling it from there but even after designating & enabling a shortcut, I can't seem to access the application launcher, as pictured in my attachment.

I have looked all over the system and various forums for another way to start the application launcher to no avail.

Perhaps stupidly, I installed Ubuntu today as the sole operating system and I now feel like a complete idiot!

Please could someone tell me where & how to search for and find the application launcher?

Many thanks!

Fibie

---

### Post by deadflowr on 2013-01-28
Those icons on the left side are application launchers.

To find more click the icon at the top(the one with the Ubuntu logo in it), then either type the name of the application you wish to run or look at the bottom area of the now opened dash and locate the various icons(one looks like a house)the second icon will show you applications.
Also you can either right-click on the Ubuntu icon to you the quicklist to choose what you want to find, be it files or apps.
Another thing is the keyboard shortcut superkey(windows key) + A.

For an overview of default Ubuntu keyboard shortcuts, press and hold down the super key, and a window will appear showing you list of shortcuts.

If this doesn't help, it would be nice to know what applications you are trying to launch.

---

### Post by Fibie on 2013-01-28
Hi Deadflowr

Thanks for the prompt reply :-) I then attached the application (Everpad, an Evernote client for Linux)  to the launcher. When I click on the application, nothing happens....by that I mean "nothing happens" in the sense that i was used to in windows, ie my notebooks appear (or don't in this case!). However when I right click its icon on the launcher, Everpad DOES give me the option to "create a note", so it seems the app is "working" but just not in the way that I expected. All the write-ups of Everpad extol it as being a fantastic Evernote client, which I find hard to reconcile with the limited functionality it appears to be giving me. 

I have also just now tried to install a couple of other apps: AVG anti virus via the command line, as per these directions: [https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)

and both VLC media player and Clam Antivirus via the software centre. Neither were able to successfully install, receiving this error message: screenshot

At the risk that I have so many issues right now that I'm confusing my own thread, I will summarise:

1) I installed 12.04 today, with a root partition, and swap partition and a home partition. The install was actually over a previous attempt of installing the same version , which gave various error messages when I tried to mount a USB drive....and that previous installation was yesterday, over the top of (and deleting) Windows 7.

2) I seem to have some fundamental problem with my installation (likely my own fault) as I am either unable to install software either via command or software centre, receiving an error message. I need to repair it somehow perhaps?

3) The one item of software which I have been ab;le to install and attach to the launcher (Everrpad) appears to give very limited functionality.


I KNOW I should NOT have deleted Windows 7....I should have tried to go for a dual boot until I had more knowledge. However on my HP laptop, it was shipped with all 4 partitions already used so I couldn't do a dual boot love the philosophy and testimonials of Ubuntu, so I took the risk. and am now in a sticky spot!

Fibie The Idiot

---

### Post by Fibie on 2013-01-28
Sorry, my screenshot was missing:

---

### Post by Fibie on 2013-01-28
OK, the plot thickens: despite the error message on VLC media player it does appear tro have installed.

So my issues are now:

1) the error messages I get on attempted installation of software. Subsequernt to the error message in the case of VLC media player, it DOES appear to have installed. But I find the error messages a worry as I'm not sure if I'm getting full functionality of the applications. In the case of Everpad I don't think I am, as I can't find the interface with my notebooks anywhere.


2) I still can't access the run applications dialogue box as pictured, either via alt F2 or any other way.

---

### Post by nns2006 on 2013-01-28
> **Fibie said:**
> 

Please could someone tell me where & how to search for and find the application launcher?

Many thanks!

Fibie

First search it. Open terminal (Ctrl+Alt+T) and type[HTML]locate XYZ[/HTML] 
[replace XYZ by application name]}
you will see a lot of diretories.like this
> nityanand@nityanand-Vostro-1500:~$ locate Nitro
/usr/lib/python2.7/dist-packages/nitrotasks/NitrotasksWindow.py
/usr/lib/python2.7/dist-packages/nitrotasks/NitrotasksWindow.pyc
/usr/share/nitrotasks/ui/NitrotasksWindow.ui
/usr/share/pyshared/nitrotasks/NitrotasksWindow.py

So, you will see which file you need to open. This may not be precise method but it will help to search :P . 
Once you decided where is you file. You can make a shortcut for it. For it you may like to install Ubuntu Tweak form [here]("http://ubuntu-tweak.com/"). Adding [PPA]("http://ubuntu-tweak.com/source/ubuntu-tweak-stable/") is better option.Once installed open Ubuntu Tweak and in Admin section, you will see disabled scripts,which also contains create launcher. Move it to left by dragging. close it and right click on desktop you will see an option of Scripts>>create launcher. 
create you launcher.

Hopefully this will help you.

Nitya

---

### Post by nns2006 on 2013-01-28
> **Fibie said:**
> OK, the plot thickens: despite the error message on VLC media player it does appear tro have installed.

So my issues are now:

1) the error messages I get on attempted installation of software. Subsequernt to the error message in the case of VLC media player, it DOES appear to have installed. But I find the error messages a worry as I'm not sure if I'm getting full functionality of the applications. In the case of Everpad I don't think I am, as I can't find the interface with my notebooks anywhere.


2) I still can't access the run applications dialogue box as pictured, either via alt F2 or any other way.

Please reinstall VLC and I would suggest to do a system update to see everything is updated. Don't panic everything will be smooth.

WHEN DONE PLEASE MARK THE THREAD SOLVED.

---

### Post by Fibie on 2013-01-28
[LEFT]Hi Nitya

I did as you suggested:

locate Everpad

locate VLC

Both times the terminal returned a blank with no directories listed at all. I then decided to reinstall the whole OS, as there seemed to be so many issues. As before I installed kn 3 partitions: root, swap, home. The installation appeared to go smoothly, although a notification came up that some applications had failed to install however it did not specify what these were.

So now I've booted into my new installation and the first thing I have tried to open - the Gwibber client - has no functionality. I have attempted to attach my facebook account but it just presents with a white screen (see screenshot).

I am aware that the focus of my thread keeps changing and I am worried I may annoy the moderators, as there have now been so many different issues with both installations that I no longer really know what works anymore :(  First it was an issue with installing software (on my previous posts) and now it seems to be Gwibber :( The only thing which appears to work is the browser, where I am typing this.

I will go to bed now and try and look at it with fresh eyes in the morning. I will update in the morning, attempt to install some apps and either mark the thread as solved, possibly opening a new one for the Gwibber issue.

Really downhearted about this, as I love the interface and philosophy and would love to get some functionality.

Thanks for your help so far!

Fibie 
[/LEFT]

---

### Post by Fibie on 2013-01-28
Hey guys

Absolutely at my wits end as I can't seem to launch any applications.

1) The application launcher which most users can access by alt -F2 seems to be missing from my system.

2) I have and installed various applications (Everpad, Jfbchat) and placed them on the application launcher but when I click on them they won't open. I can also see those apps when I go to dash home but they won't open from there either.

3) I have reinstalled ubuntu 12.04 twice to try and remedy but no luck

4) Gwibber does not work for Facebook either, although this seems to be a common problem. I tried a workaround shown here: [http://www.webupd8.org/2013/01/fix-facebook-not-working-with-gwibber.html....but](http://www.webupd8.org/2013/01/fix-facebook-not-working-with-gwibber.html....but) it didn't work for me. Hence I installed Jfb chat...which won't open.

When I try to open those apps from the launcher, the icon flashes a few times but nothing else.

Totally dejected but no choice other than to try again tomorrow....especially as I don't have windows any more!

Thanks guys and apologies for posting so many times about this!

---

### Post by Fibie on 2013-01-29
Firstly an apology: I started a thread for this issue yesterday (title: can't find application launcher) but the issue was not resolved so I have started a new thread, and tried to refine/clarify my question. I hope in doing this I am not violating forum rules....I am really at my wits end over this issue and desperately need some advice :( 

_My set-up_:

I am running 12.04 on an HP laptop. I have now installed the distro 3 times, in the hope that reinstalling it would fix my issue, but to no avail.

_My problem:_

Many applications will not run, particularly ones that I have installed. Most of the pre-installed stuff like firefox and thunderbird works fine (Gwibber doesn't work for facebook but that seems to be an established bug). However stuff I really need that I have installed- namely Everpad, VLC media player, and Jfb chat will not run although I have placed them on the launcher AND tried to run them from the dash. When I click on them, dash simply closes/disappears.
[U]
Attempted solutions:[/U]

[LIST]
[*]Reinstalling the apps in question and the distro itself.
[*]Searching a multitude of forum threads for applications that won't run and following the workarounds, to no avail.
[*]Alt + F2 does NOT open the application launcher.
[/LIST]

My final attempt was to run them from terminal, by using the whereis command and then copying the launcher command, as per this tip [http://www.addictivetips.com/ubuntu-linux-tips/find-commands-to-run-applications-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/find-commands-to-run-applications-in-ubuntu-linux/)

The interesting thing is when I do this "whereis" for firefox and thunderbird I get an output of the launch command. But when I do this for Everpad, VLC player, and jfb chat, I get no output. 

I am attaching the "whereis" terminal screenshot for these apps. On the left of the screenshot you can also see Everpad and VLC. Weird thing is I can create notes in Everpad so it must have installed & has some limited functionality....just can't get to my notebooks :-(

Please help! I installed Ubuntu as the sole OS and really need this functionality.

Thanks in advance :-)

Fibie

---

### Post by howefield on 2013-01-29
Linux is case sensitive, try using gwibber instead of Gwibber, vlc instead of VLC ect ect ect.. typing the name of the application in terminal is usually enough to load it, eg gwibber

Post any errors you get when trying to run from terminal.

Finally, one thread per issue is really sufficient, if no reply is received within around 24 hours, feel free to "bump" your thread back up to the top of the pile.

---

### Post by Fibie on 2013-01-29
Thanks for the reply!

You were right about the case sensitivity - now at least I do get a launch command from my "whereis"....but for both Everpad AND VLC media player, the lauch command does not work.

I have copied the output:fibie_whitchelo@fibie-pc:~$ whereis gwibber
gwibber: /usr/bin/gwibber /usr/bin/X11/gwibber /usr/share/gwibber
fibie_whitchelo@fibie-pc:~$ whereis vlc media player
vlc: /usr/bin/vlc /etc/vlc /usr/lib/vlc /usr/bin/X11/vlc /usr/share/vlc /usr/share/man/man1/vlc.1.gz
media:
player:
fibie_whitchelo@fibie-pc:~$ whereis everpad
everpad: /usr/bin/everpad /usr/bin/X11/everpad /usr/share/everpad
fibie_whitchelo@fibie-pc:~$ everpad: /usr/bin/everpad /usr/bin/X11/everpad /usr/share/everpad
everpad:: command not found
fibie_whitchelo@fibie-pc:~$ whereis everpad
everpad: /usr/bin/everpad /usr/bin/X11/everpad /usr/share/everpad
fibie_whitchelo@fibie-pc:~$ everpad: /usr/bin/everpad /usr/bin/X11/everpad /usr/share/everpad
everpad:: command not found
fibie_whitchelo@fibie-pc:~$ whereis vlc media player
vlc: /usr/bin/vlc /etc/vlc /usr/lib/vlc /usr/bin/X11/vlc /usr/share/vlc /usr/share/man/man1/vlc.1.gz
media:
player:
fibie_whitchelo@fibie-pc:~$ vlc: /usr/bin/vlc /etc/vlc /usr/lib/vlc /usr/bin/X11/vlc /usr/share/vlc /usr/share/man/man1/vlc.1.gz
No command 'vlc:' found, did you mean:
 Command 'vlc' from package 'vlc-nox' (universe)
vlc:: command not found
fibie_whitchelo@fibie-pc:~$ media:
media:: command not found
fibie_whitchelo@fibie-pc:~$ player:

So I still can't run these apps :-(

Fibie

---

### Post by howefield on 2013-01-29
What happens when you simply type vlc in the terminal and press enter ?

Post the screenshot.

---

### Post by Fibie on 2013-01-29
OK...the vlc media player seems to partially work when I did just what you said. But there is only sound and no images. I have attached the screenshot.

I think I have to accept at this stage where vlc is concerned the problem is with the type of file I am playing....so I will find a workaround (windows in a virtual box, or wine) to try and play that file, and as for the vlc part of my thread, we could say that it is "solved", even though I wish the outcome had been different, ie that I could play those videos!

HOWEVER when I did what you suggested with Everpad, there was no output, even though Everpad is showing as installed on the launcher. For jfbchat, there was an error message...I have also attached that screenshot showing both jfb and everpad.

Everpad is one of the ones I really need. I can live without jfb BUT I'm also worried that there is some issue with my distro that will cause issues with other apps that I try and install in future. 

Thanks also for tidying up my thread!

---

### Post by Fibie on 2013-01-29
Woah, Howefield you're in Ayrshire?? I'm in Glasgow, adopted city rather than born but there's no part of the Uk I'd rather be in :-)

---

### Post by howefield on 2013-01-29
Have you installed the codecs required to play the video ?

An easy way round that would be to install the package ubuntu-restricted-extras.

As for everpad, I don't think that is part of the Ubuntu repositories, how did you install it ? It isn't an application I am familiar with but will attempt to help you get it up and running.

---

### Post by Fibie on 2013-01-29
I think I installed the codecs...that is kind of an idiotic reply - "I think I did?!" What I mean is, once I got vlc to run by typing "vlc" into terminal as you suggested, I was asked for & gave permission to the system to install a whole bunch of other stuff, which I guess included the codecs (is there any way to check?) 

This is really hard to articulate properly in clear language, but what I seem to be getting are applications which work "a little bit", i.e. vlc works but doesn't show images; everpad allows notes to be created but doesn't seem to launch the interface.

Everpad is a Ubuntu client for Evernote, a note-taking app widely used in Windows. It has only recently been developed for Ubuntu and I installed it using the instructions contained here: [http://www.webupd8.org/2012/12/evernote-linux-client-everpad-available.html](http://www.webupd8.org/2012/12/evernote-linux-client-everpad-available.html)

Then, when I started to have issues and I reinstalled my distro, I tried to install everpad again, using this: [http://www.omgubuntu.co.uk/2012/09/use-evernote-in-ubuntu-with-everpad](http://www.omgubuntu.co.uk/2012/09/use-evernote-in-ubuntu-with-everpad)

My entire life, studies etc are contained within 30 or so notebooks in Evernote, or Everpad as the ubuntu version is called ;-) From the dash, I can even see some of the notebooks (see screenshot) but I just can't seem to launch the app, either from dash (it disappears) or from terminal (see previous screens)

Thanks so much for taking the time over this!

---

### Post by howefield on 2013-01-29
> **Fibie said:**
> Woah, Howefield you're in Ayrshire?? I'm in Glasgow, adopted city rather than born but there's no part of the Uk I'd rather be in :-)

Indeed, born and bred :)

Nice to see someone so close by in the forums.

> **Fibie said:**
> I think I installed the codecs...

There are a multitude of codecs available, what is the file extension of the video in question ? I would be pretty sure that the blank video is a result of a missing codec.

>  snip the everpad explanation...

I'll install into a vm, see how I get on.

---

### Post by howefield on 2013-01-29
That wasn't so nice :)

Installed everpad via the ppa in our link, it errored half way through..

```
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
```

Rebooted, found the everpad icon in the dash, wouldn't load application.

Ran the following commands..

```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get update
sudo apt-get install everpad
```

Rebooted and have evernote icon in top panel, through which I can authorise (create account) synchronise then load application.

---

### Post by Fibie on 2013-01-29
Hey again!

thanks for going to the trouble of installing that Everpad....in a way it makes me feel a wee bit better, as though it's not just me being dense and missing something ;-D When you're a newbie, you tend to think any problem is just....well, me!

Btw, is it ****-pouring with rain in Ayrshire?? 'Cos Glasgow is submerged, and I've just been out on my bike....:-/ Sat.Ur.Ated...

So as for Everpad, it seems like the jury is still out? Shame, because it's such a great app in Windows, and I still can't but help think it must be something I'm doing wrong, as the other apps (Vlc, Jfbchat etc.) aren't working great for me either. What is your opinion of Wine for running Windows apps? Also, do you use/rate any of the social networking clients, Gwibber and suchlike? Sorry - a bit OT there!

The videos I'm trying to play are the Cisco Nuggets CCNA series, which are wmv files. I've attached 2 screens to show the error messages.

I am so tempted to reinstall the whole distro....that would be #4 attempt...and I think I'm in blind desperation rather than logically thinking here!

Thanks again for putting so much effort into this. Even though my Precise Pangolin is somewhat less than precise right now, the camaraderie and help off this forum makes  me glad I've ditched Bill Gates and his Corporate Minions :-D

Fibie

---

### Post by howefield on 2013-01-29
> **Fibie said:**
> thanks for going to the trouble of installing that Everpad....in a way it makes me feel a wee bit better, as though it's not just me being dense and missing something ;-D When you're a newbie, you tend to think any problem is just....well, me!

I'd be sure of you getting this to work, however unlikely that seems right now.

> Btw, is it pouring with rain in Ayrshire?? 'Cos Glasgow is submerged, and I've just been out on my bike....:-/ Sat.Ur.Ated...

Yep, bad enough with the thawing snow, but coming down in bucketloads ;-)

> So as for Everpad, it seems like the jury is still out? Shame, because it's such a great app in Windows, and I still can't but help think it must be something I'm doing wrong, as the other apps (Vlc, Jfbchat etc.) aren't working great for me either.

I'm sure you can get it working.

> What is your opinion of Wine for running Windows apps?

I use Wine (actually Crossover) to run one windows application and it runs perfectly, although it isn't the current version of the said application.

Wine is great for applications which work with it, sounds a bit obvious but browsing the app database at winehq can give you an idea of how well a particular program will run.. or not.
 
> Also, do you use/rate any of the social networking clients, Gwibber and suchlike? Sorry - a bit OT there!

Seems to work well enough yes, but my needs are simple, a bit of empathy or pidgin is more than enough. If I need twitter I'll load up the web page.

> The videos I'm trying to play are the Cisco Nuggets CCNA series, which are wmv files.

Should play fine, but as I said I would install ubuntu-restricted-extras from the software centre and also w64codecs from medibuntu.org (or w32codecs if it is a 32 bit system).

If they are not confidential, mail me a small one and I'll try to play it.

> I am so tempted to reinstall the whole distro....that would be #4 attempt...and I think I'm in blind desperation rather than logically thinking here!

Once you are sorted I would :)

But then image the pristine install so it is easy to get back to your starting point.

> Thanks again for putting so much effort into this.

No worries, it is just as big a learning curve than when you sat down in front of your first windows machine.

---

### Post by Fibie on 2013-01-29
Hey Howefield

Awww, thanks, man :-) I'm really grateful for the calm and confident way you have of letting this newbie know (or at least kid herself) that you have faith in me and the whole Ubuntu project that I seem to have embarked on....despite the...shall we say.. mishaps I  am encountering on the journey! In all seriousness, it could so easily be a case of "I never realised how much I missed my water until my well ran dry"; however instead of an overarching sense of loss ("as person & OS are dramatically ripped apart from each other"; bring on the violins he he he ;-) I feel that I am at the beginning of a journey :-)

How should I mail you the Cisco videos - I think they may be too big to attach to these messages?

My feet are soaked....this rain is something else ;-/ I left the UK for warmer climes for close on a decade and now, in wet and grey Glasgow, I am in saturated shock! 


Fibie

---

### Post by howefield on 2013-01-29
> **Fibie said:**
> Awww, thanks, man :-) I'm really grateful for the calm and confident way you have of letting this newbie know (or at least kid herself) that you have faith in me and the whole Ubuntu project that I seem to have embarked on....despite the...shall we say.. mishaps I  am encountering on the journey! In all seriousness, it could so easily be a case of "I never realised how much I missed my water until my well ran dry"; however instead of an overarching sense of loss ("as person & OS are dramatically ripped apart from each other"; bring on the violins he he he ;-) I feel that I am at the beginning of a journey :-)

No worries, although the cold turkey method you have chosen to learn is rather unsettling on the nerves, yours that is, not mine ;-)

> How should I mail you the Cisco videos - I think they may be too big to attach to these messages?

I have pm'ed you an address. As long as it is one which is below 10 meg I think it will be under the attachment limit.

> My feet are soaked....this rain is something else ;-/ I left the UK for warmer climes for close on a decade and now, in wet and grey Glasgow, I am in saturated shock!

Makes you appreciate the tropical summer we are going to have....!!

---

### Post by mc4man on 2013-01-29
If your vid's happen to be mss2 (microsoft screen) then only a 32 bit mplayer with w32codecs will be able to decode in linux. (mss2 will have an ext. like other ms video - .wmv

---

### Post by Fibie on 2013-01-29
Unsettling....

I know! I am Quite Literally Scaring The Living Crap Out Of Myself ;-)

Okies. I have sent you a video. Embarrassingly enough, it's  CCNA....yeah, wish me luck! Wish me luck... and feel free to mock me :-(
  
The Rain Makes Bad  Reggae spring to mind: "Now I'm standing in the Rain In Vain.  Lorraine. Hoping to See you again (Lorraine) Tears fall from  me eyes  like Rain, Lorraine. A terrible Pain in Me Brain, Lorraine; you're  Driving Me Insane Lorraine" :-D


(I mean...seriously...did that girl just call you Lorraine??)

---

### Post by Fibie on 2013-01-29
Howefield and Mc4man, Just to let you know I am going to have to take a rain check for a few days on this, as my whole family is in complete shock; our nieghbour came over an hour ago to tell us our 6 month old kitten had been hit and killed outside our house. Stunned doesn't even begin to cover it. Will be back on in a few days.

---

### Post by AngJinhang on 2013-01-29
ok...i have not used everpad before...but there is something that you can try.
firstly, based on your printscreen, i found something really weird - your everpad is opening and running(i see the white arrow at the left of the icon) and there is a icon of everpad in your notifications bar... its just beside the wireless icon. just click on it and see what will happen. sometimes apps will just hide itself in your notification bar but you will never know it.
just try it, if it doesn't work just reply to me :)

edit: something i have missed out, the output is really ok and nothing is wrong. the command to open gwibber is 'gwibber' without the quotes but not 'Gwibber'. terminal are just case sensitive. vlc player maybe is just 'vlc' and everpad is just 'everpad'. everything is just undercase in the terminal...(i also remembered that i also did the same mistake when i am  a noob!)

---

### Post by howefield on 2013-01-30
> **Fibie said:**
> Howefield and Mc4man, Just to let you know I am going to have to take a rain check for a few days on this, as my whole family is in complete shock; our nieghbour came over an hour ago to tell us our 6 month old kitten had been hit and killed outside our house. Stunned doesn't even begin to cover it. Will be back on in a few days.

How sad. :(

There is no time limit on the forums. Just post when you are ready.

---

