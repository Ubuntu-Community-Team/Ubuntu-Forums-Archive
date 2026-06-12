---
title: "Ubunto 16.4: cannot authenticate cannot update. Have no audio"
date: 2016-10-09
forum: New to Ubuntu
---

### Post by ron223 on 2016-10-09
Hi, Absolute beginner here!

I took the plunge to UBu8ntu (tested out Zorin, Mint and elemental, but I liked Ubuntu better (Mint 18 crashed bad during live install) I love the set up and while it does not look as fast as Mint, i like it. I am running and AMD Quad Athlon II 645 AMD (64bits) Its not  the most recent machine, it still has internal audio and graphics (Radeon audio , but I am not sure about the graphics) I have 2 issues right now. 1. Ubunto does not let me authenticate using my user pass word, so I cannot update anything and 2. I don't have any audio For what I have been able to find on line I need a Catalyst  but that is about it I am  a total beginner coming from Windows, where i was not exactly a power user either. Basically only email, browsing, FB, some family photos a little video. Want to use my web cam, which I don't even know if it will be recognized, to do some videos and post them in you tube. Finally I want to get text to speech. Will never do anything more than that.  So can any one help? Its a bit frustrating. O before I forget I tried to see if something like this was posted already I searched and did not find this, and I used that check if already posted button aand it searched once but after that it sort of froze.

---

### Post by veddox on 2016-10-09
Well, that sounds like a bucketful! (And welcome to the forums, by the way.) Let's see if we can help.

So, first things first: have you ever gotten an error message, either  while installing Ubuntu or while using it? If yes, do you remember what  it was? (Pro tip: if you get an error message that you don't understand,  write it down! It could contain vital information.)

Next: could  you tell us a little more about how your computer is set up? Do you  still have Windows installed? What partitions do you have? Since  installing Ubuntu, have you made any changes to the operating system?  Have you installed extra programs?

Now to the actual issues:
1)  If Ubuntu doesn't recognize your password, how can you log in? Did you  set it up to log you in automatically? Are you sure you are entering the  exact password that you chose during installation? What type of account do you have? (For the last question: go to System Settings -> User Accounts and click on your account. Does it say "Account type: Administrator" anywhere?) How are you trying to update?
2) In what ways have you tried to play back audio? Rhythmbox? Internet (YouTube)? VLC? Is it possible that the sound has been muted? Go to System Settings -> Sound and check the volume and whether or not the 'mute' box has been checked. While you're there, is there any output device listed in the 'Play sound through' box? Click on the test button and do a sound test. Can you hear anything from there?
3) Your webcam shouldn't be a problem. If you want so see whether it works, open the program 'Cheese Webcam Booth' from the dash.
4) For text to speech, Ubuntu comes preinstalled with the Orca screen reader. Go to System Settings -> Universal Access and toggle the Screen Reader switch (if that's what you want).

Some final remarks: 
Have you discovered the wiki yet? ([https://help.ubuntu.com/community/CommunityHelpWiki](https://help.ubuntu.com/community/CommunityHelpWiki)) It has lots of good articles that are really useful to Linux beginners.
Secondly: in future, remember to start a separate thread on the forum for each issue that you have. That makes it easier for those of us giving support. So for instance, your post probably should have been at least two: one on the authentication issue and another on the sound.

Anyway, those were a lot of questions for now. Try and answer as many as possible of them in your next post, because we need the information to figure out what's going wrong with your system.

Cheers :-)

---

### Post by Impavidus on 2016-10-09
> **ron223 said:**
> ... from Windows, where i was not exactly a power user either.
That's good news, as Windows power users typically have more trouble transitioning to Linux than ordinary users.

Let's take a look at issue 1. There are several places where you authenticate using your password: at login (unless you configured automatic login), at the graphical password prompt when using the package manager (Ubuntu software, update manager etc.), when using sudo in the terminal. Which one doesn't work? Does it give you an error message, does it tell you the password is incorrect, can't you type? The password prompt in the terminal doesn't give any visual feedback, just type the password and hit enter. That confuses some new users.

---

### Post by ron223 on 2016-10-09
Hi Veddox

Thanks for answering to your questions:
1)Yes I did set up so that it would log me automatically. Unless I misspelled it, is the same same PW. i went to systems and it is th an administrator account. As to how i try to update it doesn't matter. I tried in the app following the commands, I tried in terminal , you name it. in terminal every time i use sudo in a query it  asks me for the PW and the it says am not authorized.. Oh, I forgot, when installing me it asked me whether I wanted to continue as a Super User and i said yes.
2)  I have tried all the ways i can think of to play the audio, I went to you tube and played music videos, no good, I tried online radio, no good, I tried to download some music i couldn't i dig go on system settings and I check the volume it is not muted there are three options in the  play sound through box a) Digital Output (S/PDIF) b) Analog Output (USB AUDIO) c) HDMI/Display Support, Built-in Radio. I did a sound test in all three, no sound.
3) Yes the Wecam seems to be good.
4) Orca seems perfect as well
I been to some wikis but I will go to the Ubuntu one as well. Yes I I understand about a thread per issue I apologize , I know you guys have a lot on your plate.

Once again thanks! I truly appreciate it,

---

### Post by ron223 on 2016-10-09
Hi Impavidus!

Thanks a lot for answering and having patience with a newbie I can't authenticate on any of those, none work. It tells me after several tries I am not authorized. In terminal it just says try again. I can type and i know that the pass word in the terminal is hidden with nothing to see.  Like i said to Veddux the only thing strange about the Install was when it asked whether I wanted to continue as a Super User, that and a couple of  x cannot be installed.
Thanks again.
[URL="https://ubuntuforums.org/member.php?u=1417721"][B][COLOR=#000000] 

[/COLOR][/B][COLOR=#000000][/COLOR][/URL]

---

### Post by veddox on 2016-10-10
Hi Ron,

> the only thing strange about the Install was when it asked whether I  wanted to continue as a Super User, that and a couple of  x cannot be  installed.

Could you elaborate on that please? Do you remember what it was that couldn't be installed? Oh, and you haven't told us yet how your computer is set up partition-wise.

1) How many accounts do you have on your computer? Only yours? Or is there another that also has root privileges? Also, please run the following command in terminal: ```
groups
``` and tell us what output it gives you.

2) Just a shot in the dark, but try disconnecting the HDMI device and then do another sound test.

I'm beginning to think that a complete reinstall might be called for here. I suspect something went awry during the last install...

---

### Post by Impavidus on 2016-10-10
It seems the systems thinks your password is wrong. There's a way to reset the password: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The password might be different from what you think it is. This can occasionally happen for example when the keyboard layout when you created the password is different from your current keyboard layout. I'm not sure it will help in your case, but it's simple to try.

I've never seen questions about continuing as superuser during installation.

---

