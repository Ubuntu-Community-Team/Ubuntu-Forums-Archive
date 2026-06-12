---
title: "Ubuntu Notify: notifies you of a new message in TB via notify-osd"
date: 2009-04-05
forum: Programming Talk
---

### Post by rubenverweij on 2009-04-05
Hello all,
I created this addon to notify the user of a new mail message in Thunderbird via notify-osd, but I don't know if I have done it right. It works all right, but I have a couple of issues: I use javascript to run a compiled C file, will that work on all different Ubuntu Jaunty computers or is there a better way to do it?
Also, in C I use the libnotify library, is this the correct library for the new notification system?
Your feedback is very welcome.
Cheers,
Ruben
P.S.: you can download the addon via: [This link]("https://addons.mozilla.org/en-US/thunderbird/addon/11340")
To view the source of the C file use [This link]("http://ubublogger.wordpress.com/2009/04/04/using-ubuntu-jauntys-new-notification-system-notify-osd/")

---

### Post by tbone7 on 2009-04-07
Hi Ruben, 

I grabbed your nifty little add-on via the Thunderbird add-ons-page, and added to ThunderBird v 2.0.0.21 in 64-bit Ubuntu 9.04. However, after installing it, no changes in notify-OSD is seen. It doesn't notify when new mails arrive. Perhaps we could figure out why?

If this code is programmed correctly it is bound to have a place in future versions of thunderbird, as this is on the [to do-list for notify-OSD]("https://wiki.ubuntu.com/NotifyOSD#Thunderbird").

---

### Post by rubenverweij on 2009-04-08
Thanks for your reply!
Well, I think I know exactly what the problem is ;). You are using 64-bit Ubuntu, while I'm using 32-bit Ubuntu. And the application uses a compiled C program.
I'm not too sure how to fix this though - should I create separate 32 and 64 bit versions?

---

### Post by tbone7 on 2009-04-08
That sounds like the most probably cause, yes. I'm by all means not a programmer, however, I've seen several other add-ons and applications that come in separate 32-bit and 64-bit versions. This makes me think that the same solution would be appropriate for your add-on.

If you're able to create a 64-bit version, I hereby volunteer as a crash-test dummy ;)

---

### Post by rubenverweij on 2009-04-10
Could you help me in creating this 64-bit version then?
You have a 64-bit Ubuntu machine, so it will be easier for you to compile a 64-bit executable than it will be for me. I will attach a zipped c source file, and if you want to help, here is how to compile it:
Go to a terminal and type:
```
sudo apt-get install libnotify1
```
When it is installed, browse to the directory where you have saved my attachment (cd ~ if you have saved it in your home folder) and type the following in the terminal:
```
gcc -o ubuntu-notify-amd64 ubuntu-notify.c `pkg-config --libs libnotify --cflags gtk+-2.0`
```
Then please zip the resulting executable file and post it here as an attachment so I can include it in the addon.
Thanks in advance! ;)
Ruben

---

### Post by Joeb454 on 2009-04-10
I'm hoping that the 64 bit version works because I'd love thunderbird to display it's notifications through libnotify :D

---

### Post by tbone7 on 2009-04-10
Ruben, please see the attached file.

The command you told me to run resulted in erroneous output:

```
Package libnotiy was not found in the pkg-config search path.
Perhaps you should add the directory containing `libnotiy'
to the PKG_CONFIG_PATH environment variable
No package 'libnotiy' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
```
 
So I read the man pages for gcc, and then more importantly pkg-config, as well as searching the net for answers. I knew that I had both the required packages installed, but I thought that I was missing some other dependencies. Build-essentials was there, but not the development-packages. So I installed libnotify-dev and libgtk2.0-dev, and the gcc-cmd with the source code you provided worked out fine. It should be ok for build and install now. Hopefully :)

---

### Post by johnl on 2009-04-10
You need the package 'libnotify-dev'.

It looks like you also might need some GTK dev packages.

---

### Post by tbone7 on 2009-04-10
Thanks for wanting to help, johnl, but I figured it out. Did you even read what I wrote? :)

---

### Post by johnl on 2009-04-10
> **tbone7 said:**
> Thanks for wanting to help, johnl, but I figured it out. Did you even read what I wrote? :)

Apparently not quite enough of it. Whoops.

Glad you figured it out :)

---

### Post by Lorag on 2009-04-10
This add-on is simply awsome. Thanks :)

---

### Post by remu on 2009-04-11
I'm very excited for this. I have been waiting for something like this. Thanks Ruben. I'm running a 64bit system, I can't wait untill the 64bit version of this plugin is available!

---

### Post by remu on 2009-04-11
Okay...I really couldn't wait. I added the compiled file uploaded by tbone7 to the extension folder, then changed the javascript line relating to the file, and created an .xpi file. The attached zip archive contains the .xpi file which works with 64bit systems.

rubenverweij: I hope you don't mind that I took the liberty to do so. I was thinking (and I don't know if this is possible with javascript) is to have an if/else statement to determine what architecture the person is using, and then have instantiate file to the appropriate program. And the other suggestion I had was to add which mailbox the new e-mail is in. I have 5 different mailboxes in Thunderbird and I think it would be helpful to be told in the notification what account the e-mail is in.

It works well so far, and I'm looking forward to test this out. If you need any help, let me know.

---

### Post by rubenverweij on 2009-04-11
@remu: Thanks for your suggestions. I will look at your code and I will figure out if I can add the functionality you suggest (maybe tunable in the preferences?). I will post back again after it is done. :p

@tbone7: Okay, cool you figured that out. I completely forgot. Thanks for your help!

---

### Post by remu on 2009-04-11
Well, its your code, I just added "-amd64" to the end of the file name, lol.
One other thing I just realized, the popup says "Mail Subject, Send to you by so and so" where it should say Sent.

But overall, I am loving it! Great work!

---

### Post by tbone7 on 2009-04-11
Once again the community-based collaborative software development shines :) Thanks guys. Looking forward to your updates, Ruben.

---

### Post by Vadi on 2009-04-11
Should get a Ubuntu PPA up, so you wouldn't worry about architectures - it'll compile both for 32bit and 64bit for you.

Let me know if you'd like help with that.

---

### Post by rubenverweij on 2009-04-11
@vadi: Yes, I would appreciate your help, I have no experience whatsoever with a Ubuntu PPA. If you could help me with it it would be very appreciated.

I will update the addon package too - I will let you know when it is ready.
Thank you all for your positive reactions! ;)

---

### Post by rubenverweij on 2009-04-11
Updated the addon to support amd64 and fix the typo. You can either wait for it to become available on [https://addons.mozilla.org/en-US/thunderbird/addon/11340](https://addons.mozilla.org/en-US/thunderbird/addon/11340) or download the attachment. (rename it to ubuntunotify.xpi)
Could someone please test whether the amd64 version works?

---

### Post by remu on 2009-04-11
I tried it. Works perfectly here on Ubuntu Jaunty amd64!

---

### Post by rubenverweij on 2009-04-11
Okay, cool! ;)

---

### Post by Sam Lars on 2009-04-11
This is great!  I've been using the Mailbox Alert plugin, but this is much better.  Thanks for getting it working on 64-bit, too.

---

### Post by tbone7 on 2009-04-11
I can confirm, works like a charm on my x64 Jaunty :)

---

### Post by Vadi on 2009-04-11
Oh, so it can be fully installed via an .xpi?

In that case I guess a PPA isn't needed so much, I think thunderbird does updates too :)

---

### Post by remu on 2009-04-11
It did for me, I agree, no need for a PPA.

---

### Post by rubenverweij on 2009-04-13
I've uploaded version 1.2 which makes it possible to display the folder in which the email is received. I'm not sure if it's the ultimate way yet, so any feedback would be welcome. (BTW: it's turned off by default, so go to Tools->Add-ons->Ubuntu Notify->Preferences to turn it on)

---

### Post by Sam Lars on 2009-04-13
One annoying thing... I get a lot of email sometimes, and when I do, it sits there displaying notices for like 5 minutes.  Is there a way to clear the queued notifications when I switch to Thunderbird or something like that?

---

### Post by remu on 2009-04-13
Works well with the folder information. However, I was wondering if it is possible to say which account as well. Or just the account. I have a few different accounts set up in thunderbird, and they all have their own Inbox folder, currently if any one of them recieves a new e-mail, the notification says that there is a new e-mail in the inbox, without mentioning which inbox. Do you know what I mean?

---

### Post by Vadi on 2009-04-13
I think the "mail indicator applet" is supposed to help with the tons of notifications problems.

*ruben, maybe you should think about allowing the merging of notifications? See "Merging notifications" in [https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)

---

### Post by rubenverweij on 2009-04-13
@remu: Yes, I was afraid that would happen. I will look for another approach then.

@Sam Lars: I will look into this also, don't really know a solution though as of yet.

---

### Post by rubenverweij on 2009-04-18
Hello everyone,
I have created a new version that has the following new features:
[LIST]
[*]Display the account name instead of folder name
[*]Don't notify of junk mail
[*]Correctly display non UTF-8 strings
[/LIST]
I only don't know whether the new features work on your thunderbird setup too...
Could someone please help me and test the new features before I upload it to addons.mozilla.org?
Any help would really be appreciated! :D
P.S.: See the attachment for the .xpi file. Just unzip and install.

---

### Post by Vadi on 2009-04-18
Uh oh. possible duplicated effort: [https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla)

---

### Post by cywhale on 2009-04-18
Hmm...
works fine as did the previous version, using this add on with thunderbird3 results in popups for all mails including sorted out spam mails - i know this is developed for tb2* only so do you know a website where I can read about notifying/extension developement for tb3? 

Id like to help here as there is *no* notify add on which works with thunderbird3 right now, tried everything I found (MozTrayBiff, Notify execute, new mail alert,thunderbird-dbus,...).

[Thunderbird-dbus]("https://addons.mozilla.org/de/thunderbird/addon/5617") was the only extension (besides yours) which works with tb3 somehow (having working dbus notifications would be great as we could use custom scripts to execute whatever we want, popups, sounds, led-blinking,...), sends dbus messages but as your addon does this for *all* incoming mails...

---

### Post by remu on 2009-04-22
The latest version doesn't seem to be working for me.

---

### Post by keithr on 2009-04-23
I just downloaded and installed the extension, and it works, but I'm getting two popups for every message.  Is that a known problem?

---

### Post by tbone7 on 2009-04-24
That happened to me once after I had been fiddling with the preferences. A reboot solved it then.

---

### Post by ngc2997 on 2009-04-24
Hej,

is there a chance of 'queueing' unread mail in the message stack (*), as with pidgin contacts / messages? Otherwise, the notification would pop up, disappear, and there would be no visible trace left of the new mail.

Example:
[IMG]http://i253.photobucket.com/albums/hh73/ngc_2997/OSD.png[/IMG]

Best wishes,
Karsten

(*) i.e. indicator-applet

---

### Post by keithr on 2009-04-24
I figured out what's going on with the multiple notifications when I got three of them - because I had opened a third folder window.  It appears that the extension runs for every open window, and each instance sends a notification when a new message comes in.  I'll go diving into the code to see if I can figure out the best way to make it only send one notification regardless of the number of open windows.

---

### Post by hasol on 2009-04-28
> **rubenverweij said:**
> Hello everyone,
[*]Correctly display non UTF-8 strings
[/LIST]

The plugin does not display special characters like æ, ø, å correctly on my setup, it only shows the UTF8 string. In ~/.cache/notify-osd.log it is shown correctly.

I also think that if one gets more than one email at the same time, it would be better to show them in a single notification. Mark Shuttleworth suggests showing details for up to 3 emails:
[https://bugs.launchpad.net/evolution-indicator/+bug/353007/comments/2](https://bugs.launchpad.net/evolution-indicator/+bug/353007/comments/2)
I like the behaviour of libnotify-mozilla better here. 

It would also be nice to see integration with the indicator-applet using libindicate. This way your plugin could give better integration with the new notification system in Ubuntu than what is presently possible with Evolution.

---

### Post by Sam Lars on 2009-05-02
> **hasol said:**
> I also think that if one gets more than one email at the same time, it would be better to show them in a single notification. Mark Shuttleworth suggests showing details for up to 3 emails:

Definitely +1 for that, maybe even an option for how many emails it would show at once.  Maybe break them down by folder.

---

### Post by stan5001 on 2009-05-12
This plugin is very useful, however is there a way to get it to display the envelope icon in the notification area after the notification?  Seems to be in the screenshot but I can't get it to work...

---

### Post by macvr on 2009-06-10
I think this is the best among all the notify-osd addons, for thunderbird.

But is there a way that all the mails are displayed in just **1** bubble, rather than several consecutive bubbles. , [similar to how thunderbird does]?  what mark has said as 3 is not nice,max 5 would be a better target. and the rest in the second bubble, and so on...  a max of 3 bubbles at a time would be good.
for beyond 15mails the 3rd bubble should say "+ X new mails have arrived" in the last line of the third bubble

if that is done this would be perfect :)

---

### Post by Umang on 2009-07-11
@rubenverweij: Great plugin. Why don't you register it at Launchpad for bugs/development, etc and post on addons.mozilla.org?

If it is not included in the repos in Ubuntu (with thunderbird recomending/requiring it) or not incorporated into Thunderbird itself, atleast we can use download and use it from the official site.

Thanks!

Umang

---

### Post by rubenverweij on 2009-07-15
Thanks for your compliment. I have stopped working on this version of the plugin, since it has been merged with another plugin. You can visit our Launchpad project at [https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla). I'm still contributing to the project, so if you have any suggestions, feel free to register a blueprint or drop me an email!

---

