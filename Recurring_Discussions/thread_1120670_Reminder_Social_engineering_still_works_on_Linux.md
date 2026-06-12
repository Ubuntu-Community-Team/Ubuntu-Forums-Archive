---
title: "Reminder: Social engineering still works on Linux"
date: 2009-04-09
forum: Recurring Discussions
---

### Post by conphara on 2009-04-09
I just searched for some of the latest Ubuntu clips on Youtube and this one caught my eye.

[http://www.youtube.com/watch?v=9HxFGQ8OpYw]("http://www.youtube.com/watch?v=9HxFGQ8OpYw")

This guy shows a demo of successfully getting hold of a user's personal data from Firefox (by saving an attached file from a mail in Evolution to the desktop and clicking on it) and later getting root access to delete everything on the partition all done in a Virtualbox session.

The title for this video is: _The Linux desktop is not much more secure than Windows_

The morale of the story is easy. Producing malware for Linux is apparently possible. Avoiding it comes down to the user himself. Don't download and run anything that you shouldn't. But how can you know?

---

### Post by Eisenwinter on 2009-04-09
Yeah, I can only see an Ubuntu user getting infected like that, haha.

(given the fact that the user himself has to save the strange attachment, then run it, in this particular case)

---

### Post by dasunst3r on 2009-04-09
There are people out there who will do ANYTHING and make up ANYTHING in their attempt to discredit something they don't like (e.g. conspiracy theorists, people who think President Obama is Muslim, etc.).  I'd start asking questions: What Firefox version is this person using?  Is this person fully patched?  Can this be reproduced in a similarly-configured version of Windows (same Firefox version, fully patched)?  Ultimately, the user is the weakest link as that worm required user intervention to trigger.  Still, I've seen worms in Windows that did not require user intervention.  What does that say about security in Windows compared to Linux?  QED

---

### Post by samjh on 2009-04-09
> **conphara said:**
> The morale of the story is easy. Producing malware for Linux is apparently possible. Avoiding it comes down to the user himself. Don't download and run anything that you shouldn't. But how can you know?

"The price of freedom is eternal vigilance." - Thomas Jefferson

Linux users would do well to remember it.  Don't get complacent.  Linux is not magically more secure than Windows.  It has weaknesses like any operating system, and the biggest weakness is a complacent user.

---

### Post by SomeGuyDude on 2009-04-09
Guys, deal with it. Ubuntu isn't invincible, nor Linux at large. If it's a computer, it can be broken. Linux may be harder, but let's not kid ourselves: we're benefiting from Linux's relative lack of popularity and "computer geek" image right now. The people who make worms that are built to steal personal info know that if they want it to work it'll be better to write one for 85% of the user base than the <5% that are likely very computer savvy.

---

### Post by Barrucadu on 2009-04-09
Isn't it common sense to not just run any file you get via email?

---

### Post by Skripka on 2009-04-09
> **Barrucadu said:**
> Isn't it common sense to not just run any file you get via email?

If common sense is so uncommon that we are always asking where it went, why do we call it "common sense"?

---

### Post by samjh on 2009-04-09
> **Barrucadu said:**
> Isn't it common sense to not just run any file you get via email?

Only for security-savvy users, which 99% of computer users are NOT.

Common sense is not common. ;)

---

### Post by TheLions on 2009-04-09
> **dasunst3r said:**
> There are people out there who will do ANYTHING and make up ANYTHING in their attempt to discredit something they don't like (e.g. conspiracy theorists, people who think President Obama is Muslim, etc.).  I'd start asking questions: What Firefox version is this person using?  Is this person fully patched?  Can this be reproduced in a similarly-configured version of Windows (same Firefox version, fully patched)?  Ultimately, the user is the weakest link as that worm required user intervention to trigger.  Still, I've seen worms in Windows that did not require user intervention.  What does that say about security in Windows compared to Linux?  QED


Someone should fix this...

Don't fix security holes as MS! (if there is a hole, don't fix it just sell some AV software):lolflag:

---

### Post by bekind2thenoob on 2009-04-09
How does this get around AppArmour?

---

### Post by LowSky on 2009-04-09
how does it originally install without knowing the sudo password?
That part I don't get.

---

### Post by tjwoosta on 2009-04-09
you would have to be an idiot to download the .desktop file!


seriously the file is called wow.png.desktop

we all know if this was a real picture it would just end with .png


.desktop is just gnomes was of making desktop launchers


for instance if you make a new launcher to open firefox it would be called firefox.desktop except  gnome hides the .desktop extension so it just becomes a launcher named firefox


this guy is simply exploiting this by making his own launcher disguised as a picture and emailing it to himself


it would be very easy for developers to fix this if it became that big of a problem  (actually im pretty sure ive already heard something about how gnome is already working on it)


also this wont work with any alternative DE's like fluxbox or openbox with thunar or pcmanfm for example


and i dont see how the launcher could possably get root permissions, but i suppose one can do enough damage to make people mad without having root permissions


EDIT: ahh, nvm i see how he gets root

the launcher simply changes the commands in his gnome menu  

then when the user opens something else on his own, the altered command will run and the user will unknowingly submit his root password, thinking that the program he is trying to open is using it


basically the security hole here is the user being oblivious to file extensions, which is one more reason why people should smarten up and learn how to use a computer instead of making the computer as dumbed down as the users

---

### Post by TheLions on 2009-04-09
> **LowSky said:**
> how does it originally install without knowing the sudo password?
That part I don't get.

probably keylogging while he was opening synaptic

---

### Post by Therion on 2009-04-09
There is no operating system made by man that can not "hacked" by man.  

This being the case there is no anti-virus application now, nor will there ever be, that can effectively replace the one between your ear's.

---

### Post by sydbat on 2009-04-09
First off, anyone who keeps that much personal info on their computer is, IMHO, stupid.

Second, if you do things like online banking (or anything else online), just set FF to clear everything when it closes - nothing for anyone to steal.

Third, also notice that sparky was using OSX, which explains alot.

Fourth, as stated already, most people know little about computers and will click on anything.

Last thing, no OS is invincible. Education is the only way to reduce malware propagation. However, people will only want to be educated AFTER something happens, so all the info out there about prevention is "useless" to J. Average because "it will never happen" to them.

---

### Post by zmjjmz on 2009-04-09
How is this supposed to prove that Windows is more secure? If someone did something similar on Windows, the same thing would happen.

Anyways, a proper AppArmor or SELinux configuration could stop this.

---

### Post by Methuselah on 2009-04-09
What's the point?
Destructive programs can be written for gnu-linux and if the user unwittingly runs them and gives them root access they'll do damage.

Duh

---

### Post by _Pipo_ on 2009-04-09
Well, of course, Linux isn't invulnerable against trojans. If someone is stupid enough to save a file called "wow.png.desktop" (even though images can normally be opened from Evolution), then open it himself, no operating system in the world will ever be able to prevent the user from being infected. That said, the trojan shouldn't be able to gain root privileges so easily, but it's easily fixable, and if that kind of malwares starts to appear, the default settings of Ubuntu will be not to remember the password.

---

### Post by riza hylviu on 2009-04-09
As for every os you can write malware and infect but the difference is that  infecting gnu-linux is like shooting a jackalope and windows is like shooting a cow...

---

### Post by Newuser1111 on 2009-04-09
Is that email one the only one known?

---

### Post by Martje_001 on 2009-04-09
> **zmjjmz said:**
> How is this supposed to prove that Windows is more secure? If someone did something similar on Windows, the same thing would happen.

Anyways, a proper AppArmor or SELinux configuration could stop this.
It cannot. If you give a program root acces, it can do everything.

This IS a big security hole. We should warn the user when downloading a .desktop file (I've never downloaded a desktop file in my 2-years-of-Linux).

---

### Post by aysiu on 2009-04-09
> **Martje_001 said:**
> 
This IS a big security hole. Yes, users randomly clicking on email attachments is a big security hole. We should patch those users.

---

### Post by Bios Element on 2009-04-09
> **aysiu said:**
> Yes, users randomly clicking on email attachments is a big security hole. We should patch those users.

Yes, We really need to do that. I vote we nuke their HD's every time they install an OS just to be on the safe side. :lolflag:

---

### Post by sisco311 on 2009-04-09
> **aysiu said:**
> Yes, users randomly clicking on email attachments is a big security hole. We should patch those users.

done.
```
apt-get install brain-v.1.0
```

brain-v.1.0:
[list]
[*]is small in size (just a little bigger than a brain of a chicken)
[*]protects against dangerous e-mail attachments 
[*]provides full protection against [evilmalware 0.6 (beta)]("http://www.gnu.org/fun/jokes/evilmalware.html") or higher
[/list]

---

### Post by niko7865 on 2009-04-09
Fixes:
- Outbound firewall
- Do not set downloaded items to execute by default
- Monitor changes made to gnome-panel menus, ask user for confirmation (maybe only if they are not made using the menu editor, do not ask for confirmation if the changes are made by apt/dpkg)

---

### Post by swoll1980 on 2009-04-09
So what? If you find somebody willing you can get them to do anything. This is not news. No computer can keep the administrator from doing dumb things. As a wise man once said"If you make something idiot proof, nature will produce better idiots."

---

### Post by FuturePilot on 2009-04-09
Well of course if you go around randomly clicking on email attachments from people you don't know. That's not really exploiting a vulnerability in the OS.

---

### Post by aysiu on 2009-04-09
I've retitled this thread and moved it to Recurring Discussions.

No matter how much you secure an operating system, if the user decides to open the gates, the gates are open.

And then the question is, how easy do you want to make it for the user to open the gates? The more convenience you have, the less security you have. The more security you have, the less convenience you have.

Right now, Ubuntu seems to have a pretty good balance between security and convenience. But even with a 15-minute sudo timeout, people are still complaining about having to enter their passwords "all the time." And in this YouTube video, you can already see that 1. Ubuntu shows all file extensions, so you can see this isn't a .png file right away, and 2. You can't even double-click the attachment straight out of the email--you have to save it to your desktop first.

Really, if you want social engineering at its best, just create a .deb file for a "cool program" and have people double-click it. If they really think it's a cool program and not malware, you don't even have to modify anything to capture passwords or use a false file extension. A .deb extension will be expected, and the user will give you the password right away through GDebi, and you totally have rooted the entire installation.

---

### Post by artir on 2009-04-09
This was patched in jaunty i think

---

### Post by sekinto on 2009-04-09
> **LowSky said:**
> how does it originally install without knowing the sudo password?
That part I don't get.

Because stage 1 doesn't NEED root privileges since it is only accessing personal files and not system ones. Stage 2 however needs root access, going by the video it looks like he used a keylogger to get the root password.

---

### Post by EnglishSparrow on 2009-04-09
> **sisco311 said:**
> done.
```
apt-get install brain-v.1.0
```

brain-v.1.0:
[list]
[*]is small in size (just a little bigger than a brain of a chicken)
[*]protects against dangerous e-mail attachments 
[*]provides full protection against [evilmalware 0.6 (beta)]("http://www.gnu.org/fun/jokes/evilmalware.html") or higher
[/list]

Exactly. No operating system can prevent a user's mistake. I once ran  
```

sudo chown user:user /

```
**_DO NOT RUN THE ABOVE CODE._**

Although some user probably will, like I did. 
But, making mistakes in C is not as bad, and funnier:
```

const ipated;
case closed:
double or_nothing;
short sighted;
void if_removed;  
volatile buggy_code;
unsigned anonymous;
int erbreed;   

```

---

### Post by cardinals_fan on 2009-04-09
> **tjwoosta said:**
> 
we all know if this was a real picture it would just end with .png

I wish this were true...

Anyway, the vast majority of so-called security issues stem directly from user incompetence.  Nothing new here.

The only real security flaw I have seen in Ubuntu is the default 15-minute sudo timeout, which I consider extremely dangerous.

---

### Post by Sealbhach on 2009-04-10
This looks quite alarming as .desktop files are executed by Gnome & KDE and the malware has free access to the SQLite Firefox database. The malware also reconfigures the Gnome  menu so that root access is granted to the malware when the password is entered for Synaptic.

[http://www.youtube.com/watch?v=9HxFGQ8OpYw](http://www.youtube.com/watch?v=9HxFGQ8OpYw)

Some commenters say that it's fixed in Jaunty.


.

---

### Post by cdenley on 2009-04-10
[http://ubuntuforums.org/showthread.php?t=1073765](http://ubuntuforums.org/showthread.php?t=1073765)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153438](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153438)

It looks like they had the same idea I did, requiring launchers to be executable.

---

### Post by Therion on 2009-04-10
> **Sealbhach said:**
> This looks quite alarming...
I like how the proponent of this points out that the infectious email comes from a trusted source, so of course I open both the email and its suspicious payload...  

Excuse me?  As if getting emails from my friends with suspicious attachments that contain malware is an everyday occurance.  This whole thing is, IMO, just so much FUD; predicated on the user doing SOOO many things wrong and utterly contorted logic.  "Trusted sources" sending me malware in the first place for instance.

---

### Post by cdenley on 2009-04-10
> **Therion said:**
> I like how the proponent of this points out that the infectious email comes from a trusted source, so of course I open both the email and its suspicious payload...  

Excuse me?  As if getting emails from my friends with suspicious attachments that contain malware is an everyday occurance.  This whole thing is, IMO, just so much FUD; predicated on the user doing SOOO many things wrong and utterly contorted logic.  "Trusted sources" sending me malware in the first place for instance.

It requires a user to save a file, then double-click a file. The saved file can even have the same icon and appear to have the same filename as an audio or video file. The only stupid things the user has to do is download what they believe to be a media file or document from an untrusted source, then not realize the file they are saving has no extension, while when they see it in nautilus, it has an extension, or whatever filename the attacker chose.

I am glad they fixed this security hole.

---

### Post by bodhi.zazen on 2009-04-10
> **Sealbhach said:**
> This looks quite alarming as .desktop files are executed by Gnome & KDE and the malware has free access to the SQLite Firefox database. The malware also reconfigures the Gnome  menu so that root access is granted to the malware when the password is entered for Synaptic.

[http://www.youtube.com/watch?v=9HxFGQ8OpYw](http://www.youtube.com/watch?v=9HxFGQ8OpYw)

Some commenters say that it's fixed in Jaunty.


.

Moved to recurring discussions. This has been discussed over and over.

The information you posted is nothing but FUD and misinformation. This is an example of social engineering , not a virus. I moved this thread to recurring discussions because of this - ie you are misusing the term virus and do not seem to understand social engineering.

[http://en.wikipedia.org/wiki/Social_engineering_(security](http://en.wikipedia.org/wiki/Social_engineering_(security))

The solution is educating users and as always DO NOT download or execute code for untrusted sources.

---

### Post by cdenley on 2009-04-10
> **bodhi.zazen said:**
> Moved to recurring discussions. This has been discussed over and over.

The information you posted is nothing but FUD and misinformation. This is an example of social engineering , not a virus. I moved this thread to recurring discussions because of this - ie you are misusing the term virus and do not seem to understand social engineering.

[http://en.wikipedia.org/wiki/Social_engineering_(security](http://en.wikipedia.org/wiki/Social_engineering_(security))

The solution is educating users and as always DO NOT download or execute code for untrusted sources.

You are the only one who used the word "virus" in this thread. The problem is that the user doesn't know they downloaded code, and isn't aware they are executing anything when they double-click what appears to be a non-executable file. That is what was fixed in Jaunty. It seems odd that the developers thought it was serious enough to fix, yet you think it is FUD and not worth discussing. Is the bug report and released fix FUD?

---

### Post by frodon on 2009-04-10
cdenley, it was not meant like this.

bodhi.zazen meant this topic has been discussed many times already and therefore this discussion better fit the recurring discussion forum. There's a lot of misinformation around this issue but as often there's a small part which is true, it surely explains why the devs did something.
However the way the OP posted it makes the thread falling in the FUD category.

---

### Post by cdenley on 2009-04-10
> **frodon said:**
> cdenley, it was not meant like this.

bodhi.zazen meant this topic has been discussed many times already and therefore this discussion better fit the recurring discussion forum. There's a lot of misinformation around this issue but as often there's a small part which is true.
However the way the OP posted it falls in the FUD category.

I guess there are some people who exaggerate this bug, and the youtube posting which was linked to in the first post may be an example of this although I didn't actually look at it since I was already aware of the problem. It seemed to me like any discussion about this bug was banned and denied being an actual security problem, while the actual developers realized it was a problem and fixed it. Since it was in fact a bug, and it is security-related, it seems to warrant some discussion in the Security section, even if there may be some related FUD.

---

### Post by Sealbhach on 2009-04-10
> **cdenley said:**
> You are the only one who used the word "virus" in this thread. ......... It seems odd that the developers thought it was serious enough to fix, yet you think it is FUD and not worth discussing. Is the bug report and released fix FUD?

Exactly, thank you.

I got an infraction for this which I would like to have revoked. 


.

---

### Post by Tibuda on 2009-04-10
removed

---

### Post by cdenley on 2009-04-10
> **danielrmt said:**
> Looks like you already know how to post, what else do you want to know?

Considering the thread topic, I think he wants your e-mail so he can try sending you a malicious launcher.

---

### Post by Therion on 2009-04-10
> **cdenley said:**
> ... The only stupid things the user has to do is download what they believe to be a media file or document from an untrusted source, then not realize the file they are saving has no extension, while when they see it in nautilus, it has an extension, or whatever filename the attacker chose.

Ooooh. Is THAT all?  Just download, save and subsequently open an attachment - that I've not bothered to examine in any way, shape or form - and received from an unknown source. 

Gotcha.  

I'd call that a gaping stupidity hole sooner than a gaping security hole.

---

### Post by Sealbhach on 2009-04-10
> **Therion said:**
> Ooooh. Is THAT all?  Just download, save and subsequently open an attachment - that I've not bothered to examine in any way, shape or form - and received from an unknown source. 
.

Did you watch the video? It's from a known source. Watch the video, then comment.

.

---

### Post by cdenley on 2009-04-10
> **Therion said:**
> Ooooh. Is THAT all?  Just download, save and subsequently open an attachment - that I've not bothered to examine in any way, shape or form - and received from an unknown source. 

Gotcha.  

I'd call that a gaping stupidity hole sooner than a gaping security hole.

I didn't say anything about an e-mail attachment. People do occasionally download music, video, or PDF's from untrusted sources. I wouldn't call that a gaping stupidity hole. I call that using the internet. Haven't you ever needed a file from a website you weren't 100% sure you can trust?

---

### Post by Therion on 2009-04-10
> **Sealbhach said:**
> Did you watch the video? It's from a known source. Watch the video, then comment.
I did. Read my first comment.

---

### Post by bodhi.zazen on 2009-04-10
> **cdenley said:**
> I guess there are some people who exaggerate this bug, and the youtube posting which was linked to in the first post may be an example of this although I didn't actually look at it since I was already aware of the problem. It seemed to me like any discussion about this bug was banned and denied being an actual security problem, while the actual developers realized it was a problem and fixed it. Since it was in fact a bug, and it is security-related, it seems to warrant some discussion in the Security section, even if there may be some related FUD.

It is not this issues that is problematic, it is the way it is presented. If you, or anyone  else, chose to discuss security it needs to be done in an appropriate fashion.

This is clearly outlined in the sticky at the top of the security section :

[http://ubuntuforums.org/showthread.php?t=1070309](http://ubuntuforums.org/showthread.php?t=1070309)

---

### Post by ashmew2 on 2009-04-10
Well I agree , the way in which the problem is presented needs to be proper But it SHOULD have been a serious/not so serious but still a problem nonetheless because the devs took some time out to go after the bug/security hole/stupidity hole/<insert derogatory words here> hole.
So , bottom line , people should be aware about things they download and run even on a linux system and not be "Bah , No one can even touch my Linux baby <3" :P.

Sealbach , You really got an infraction for discussing this  ? :lolflag:

---

### Post by Therion on 2009-04-10
> **ashmew2 said:**
> 

... /**stupidity hole**/<insert derogatory words here> hole.

Did that come off as inflammatory?  It certainly wasn't *meant* to and I apologize if it *did*.

---

### Post by ashmew2 on 2009-04-10
> **Therion said:**
> Did that come off as inflammatory?  It certainly wasn't *meant* to and I apologize if it *did*.

No No , it wasnt and no need to apologize..I just did it for the fun of it , i think i was a bit sarcastic there , I'll edit it if you want..

---

### Post by Therion on 2009-04-10
> **ashmew2 said:**
> No No , it wasnt and no need to apologize..I just did it for the fun of it , i think i was a bit sarcastic there , I'll edit it if you want..
Oh, no... No need to edit anything.  I was just hoping I wasn't coming off as an a-- without meaning to with that remark.  

Sometimes I mean to but this wasn't one of those times.

---

### Post by cardinals_fan on 2009-04-10
Entering your password out of habit is BAD, okay kids?

---

### Post by aysiu on 2009-04-11
This is ridiculous.

Are the developers also going to decide that .deb files need to be made executable before you can double-click-install them using GDebi?

Users are responsible for vetting what they run on their systems.

---

### Post by ComputerHermit on 2009-04-11
Is Ubuntu really that vulnerable? To attack's from hackers I been watching all this stuff on you tube of people writing melware. That can hack ubuntu why use it I ask myself? I been a Ubuntu user since Dapper. I learned alot with Ubuntu I used it at work in my home on my laptop playing open arena at work ;p Anyway if it has that many security holes and you got to make a 6 page iptables script why use it. I'm looking for more input from you on my thought's about what has been posted around You Tube and in these forums.):P

---

### Post by Tibuda on 2009-04-11
What are you talking about? Linux is a lot safer than Windows, for sure.

What YouTube video have you watched?

EDIT: this should be everything you need to know about Ubuntu security: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Berserker v7 on 2009-04-11
> **danielrmt said:**
> What are you talking about? Linux is a lot safer than Windows, for sure.

What YouTube video have you watched?

EDIT: this should be everything you need to know about Ubuntu security: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Ya, i sure would love to watch those videos!! please post the links...

---

### Post by Therion on 2009-04-11
OP is, most likely, referring to this vid: [http://www.youtube.com/watch?v=9HxFGQ8OpYw](http://www.youtube.com/watch?v=9HxFGQ8OpYw)  

It's been discussed to death in other threads. Success depends on the user ignoring numerous, basic, safe-computing habits and requires the user to download, save and execute an infectious email attachment.

The issue has been fixed in Jaunty in any case, so I see this as a rather moot issue.

---

### Post by WatchingThePain on 2009-04-11
What is the point of this thread?, to suggest that Ubuntu is unsafe?.
Find some real statistics.

---

### Post by 3rdalbum on 2009-04-11
If the user downloads and runs a program that they downloaded from the Internet or from e-mail without carefully vetting it first, then it's not "hacking" or "a crack attack". It's a social engineering attack.

An analogy: If you convince a man to put a hoover to his ear and turn it on, that's not a safety issue with the machine, it's an issue with the man's common-sense. It's not like any vaccumn cleaners have been recalled "due to risk of ruptured eardrums if the tube is placed up to the ear".

---

### Post by Tibuda on 2009-04-11
> **3rdalbum said:**
> If the user downloads and runs a program that they downloaded from the Internet or from e-mail without carefully vetting it first, then it's not "hacking" or "a crack attack". It's a social engineering attack.

An analogy: If you convince a man to put a hoover to his ear and turn it on, that's not a safety issue with the machine, it's an issue with the man's common-sense. It's not like any vaccumn cleaners have been recalled "due to risk of ruptured eardrums if the tube is placed up to the ear".
Yes, and the ".desktop" extension is visible when the user downloads it in the video.

---

### Post by Therion on 2009-04-11
> **danielrmt said:**
> Yes, and the ".desktop" extension is visible when the user downloads it in the video.
He makes mention that the user just ignores the curious extension.  How convenient.  One of the many faults I find in that FUD filled video.  

My fav, though, is at :57s where he specifically states the email is from a trusted source.  Because, you know how your best buddy is ALWAYS trying to get your credit card number via an infected email attachment...  That vid is so full of fail it makes my eye's bleed.

---

### Post by Invincible23 on 2009-04-11
That youtube video looks more like MS new FUD filled ad than a real hack showoff.

---

### Post by sgosnell on 2009-04-11
Ubuntu is easily hackable.  The user can always open a terminal and type "sudo rm /*".  Very insecure.  Of course, a Windows user can type "format C:".  There is simply no way to protect against all idiots, because idiots are so inventive.

:rolleyes:

](*,)

:popcorn:

---

### Post by rplantz on 2009-04-11
The most common user error is ID "ten" T. (Write "ten" in numeral format.)

---

### Post by Dejavou42 on 2009-04-11
Just for clarification, rm / is not a hack.

I would say that Ubuntu is extremely safe compared to windows. I have never had a virus on my Ubuntu box. I have never seen a malicious website that would infect Ubuntu without user confirmation.

 I commonly have to remove viruses from Windows computers (which is usually a pain). From what I can tell Ubuntu has a much better fail safe mode. I can't say from experience, but I can imagine that it would be a lot easier to remove a virus from Ubuntu than it would to remove one from Windows.

---

### Post by FrankT-Qc on 2009-04-11
Well, it does highlight that trojans are a pretty easy way to infect a machine... 

Haven't this hole (in gnome) have already been patched ???

---

### Post by jwbrase on 2009-04-11
> **Dejavou42 said:**
>  but I can imagine that it would be a lot easier to remove a virus from Ubuntu than it would to remove one from Windows.

Linux malware makers tend to be more thoughtful than Windows malware makers:

```
bliss --bliss-uninfect-files-please
``` :p

Bliss includes a command line option to disinfect. Virus and anti-virus, all in one package.

---

### Post by jwbrase on 2009-04-11
> **ComputerHermit said:**
> Is Ubuntu really that vulnerable? To attack's from hackers I been watching all this stuff on you tube of people writing melware. That can hack ubuntu why use it I ask myself? I been a Ubuntu user since Dapper. I learned alot with Ubuntu I used it at work in my home on my laptop playing open arena at work ;p Anyway if it has that many security holes and you got to make a 6 page iptables script why use it. I'm looking for more input from you on my thought's about what has been posted around You Tube and in these forums.):P

Windows can get infected just by the user visiting a site, without having to personally run anything. And a virus doesn't have to wait for the user to enter his password and find some way to intercept it to install botnet software, format the hard drive, or any other such thing. Windows doesn't require a password for such things. But the user will always be a security hole on any system, because a user, especially an administrator, has the power to give the system permission to do or allow things that it wouldn't do or allow without permission.

---

### Post by aysiu on 2009-04-11
> **FrankT-Qc said:**
> Well, it does highlight that trojans are a pretty easy way to infect a machine... Trojans rely on **social engineering**, so, yes, trojans can always easily infect machines run by users who are easily tricked, and this is true for any OS (Ubuntu, Mac OS X, Windows).

Unfortunately, users cannot be patched as security holes. They can be only educated.

---

### Post by cmay on 2009-04-11
> **aysiu said:**
> Trojans rely on **social engineering**, so, yes, trojans can always easily infect machines run by users who are easily tricked, and this is true for any OS (Ubuntu, Mac OS X, Windows).

Unfortunately, users cannot be patched as security holes. They can be only educated.

after i started using linux fulltime i was still used to getting my programs on random places on the internet. once i downloaded a basic compiler and i untared it and then there was nothing in the folder. i only discovered that almost all the programs in /usr/bin was gone since i wanted to compile a littel hello world program and i knew gcc was fully functional just two minuttes ago. so i looked in the /usr/bin and there was only a few programs there and there should be a lot more. my home folder was also deleted. 

so now i only use the package manager and if the applications i want is not there i just dont use them. only at some few rare occations i fetched something like unetbootin since i know it is considered to be "safe"  from reputation. 

i guess a good smack on the head like this is a valuable experience to get the user "patched" but now i done it and i am sure others did too so there should be no need for anyone to repeat the same mistake over and over again.  

i think your right when you say education is the only way. 

btw:
after this i have never used a firewall or any rootkit checkers or the like but then again never no more downloaded anything from random places and i get no spam and i think now that linux is the most secure system there is . if only you stick to the safe respotories and use just common sence everything should be alright. it was also years ago that happend. something like four or five years.

---

### Post by GreyGeek on 2009-04-11
I first saw this "hole" a few months ago while I was using Mandriva 2009 PWP.   I didn't believe it was that easy so I decided to try it by taking one of my *.desktop files and emailing it to my self using Thunderbird. (I never included the use of FireFox, which isn't really necessary for this attack but the video narrator, wanted to include an unprotected FireFox history for a better effect).  I couldn't get that exploit to work in Mandy.

In Kubuntu if I click on a *.desktop entry in the Desktop directory while using Dolphin it fires as if I had clicked on the desktop icon, because that is what mime's do.  What the user has to do is save the *.desktop file to a directory (not necessarily the Desktop directory).

Of course, if you are willing to save an attachment, add execute permissions (in place of mime) and then execute it, you have effectively circumvented one aspect of Linux security.  But, you still haven't opened an avenue where a bad guy can AUTOMATICALLY  convert thousands of Linux boxes to bots with a single email because very few Linux users would save an desktop attachment and execute it without first looking inside and seeing what it contains. (It is a text file.)

HOWEVER, before you go off on a rant about how Linux is no more secure than Windows consider this:  The video showed that it takes a User's interaction to fire the malware, which requires social engineering.  Windows, on the other hand, DOESN'T need social engineering to fire an attachment.  **Windows has ActiveX controls which do that task AUTOMATICALLY WITHOUT USER INPUT.**   That's why you see bot farms made entirely of compromised Windows boxes.   On Linux the user STILL needs to manually active the mime capability by clicking on the file, and that assumes that a mime entry has been added for that kind of file.

---

### Post by cmay on 2009-04-11
on the other hand i once tried to rm my minix installation to see what would happen. it was very very stupid to do that.

 however in dos it is possible to have a .com file execute instead of the .exe by same name and by exploiting that one can make a bad_program.com that executes disguised as "DIR.EXE" which all dos users knows and loves to use. so it is on windows with alot of things that does things by it self and needs no users to do stupid things to get malware up and running except plug in a cable for the internet and browse a bit. 

 on linux you have to at least have to let the evilmalware.sh have executable flags set on and open a terminal and run it.  moral is that it is very easy to install a .deb or execute a script that can do damage but not if you just stick to the package management system provided with your distribution and be happy about all the free stuff you can get from it that has no malware in it instead of wanting and needing a lot of stuff from elsewhere.

---

### Post by bashveank on 2009-04-11
> **cmay said:**
> on the other hand i once tried to rm my minix installation to see what would happen. it was very very stupid to do that.

 however in dos it is possible to have a .com file execute instead of the .exe by same name and by exploiting that one can make a bad_program.com that executes disguised as "DIR.EXE" which all dos users knows and loves to use. so it is on windows with alot of things that does things by it self and needs no users to do stupid things to get malware up and running except plug in a cable for the internet and browse a bit. 

 on linux you have to at least have to let the evilmalware.sh have executable flags set on and open a terminal and run it.  moral is that it is very easy to install a .deb or execute a script that can do damage but not if you just stick to the package management system provided with your distribution and be happy about all the free stuff you can get from it that has no malware in it instead of wanting and needing a lot of stuff from elsewhere.

Because so many people have DOS on their computers?

---

### Post by cmay on 2009-04-11
> **bashveank said:**
> Because so many people have DOS on their computers?
point was rather that windows did not move itself very long from dos in terms of security.

---

### Post by cardinals_fan on 2009-04-11
> **GreyGeek said:**
> 
HOWEVER, before you go off on a rant about how Linux is no more secure than Windows consider this:  The video showed that it takes a User's interaction to fire the malware, which requires social engineering.  Windows, on the other hand, DOESN'T need social engineering to fire an attachment.  **Windows has ActiveX controls which do that task AUTOMATICALLY WITHOUT USER INPUT.**   That's why you see bot farms made entirely of compromised Windows boxes.   On Linux the user STILL needs to manually active the mime capability by clicking on the file, and that assumes that a mime entry has been added for that kind of file.
ActiveX was a bad idea in the first place and is the primary reason that I never condone the use of Internet Explorer.  A limited user account can still mitigate most of the danger.

---

### Post by bashveank on 2009-04-11
> **cmay said:**
> point was rather that windows did not move itself very long from dos in terms of security.

There aren't any .COM files on Windows... the only files that can be executed are EXEs (except for oddball macros and such that run in various programs)

---

### Post by lisati on 2009-04-11
Speaking of DOS programs, I've seen EXE-format files with .COM extensions - unless I'm mistaken, the program loader looks at more than just the file name.

---

### Post by bashveank on 2009-04-11
> **lisati said:**
> Speaking of DOS programs, I've seen EXE-format files with .COM extensions - unless I'm mistaken, the program loader looks at more than just the file name.

In Windows only EXEs get executed.

Other formats, however, can be named incorrectly. A JPG will open as a JPG even if it's marked as a TXT, or GIF, or is even missing an extension.

---

### Post by lisati on 2009-04-12
> **bashveank said:**
> In Windows only EXEs get executed.

Other formats, however, can be named incorrectly. A JPG will open as a JPG even if it's marked as a TXT, or GIF, or is even missing an extension.

What I was thinking of was an EXE file that was masquerading as a COM file - the copy of Windows I was checking it out with was happy to run it as an EXE file at the command line even though it had a .COM extension. Doesn't the .EXE header for Windows executables have some extra information that is usually ignored by MS-DOS (e.g. which version of Windows it's written for)?

I think we're getting side-tracked here......

---

### Post by ashmew2 on 2009-04-12
People need to see what they open.
Security flaws can be patched , not the dumb-end-user.

I've read so many times : 

"If someone tells you to sudo rm -rf , DONT DO IT!"

Now , that's not a security issue for the ubuntu devs..nor is it their fault..they must have put it there for something useful...now if the "end-user" is smart enough to execute that command on system files...Will you call it a bug or a security loophole ?

---

### Post by cmay on 2009-04-12
> **lisati said:**
> What I was thinking of was an EXE file that was masquerading as a COM file - the copy of Windows I was checking it out with was happy to run it as an EXE file at the command line even though it had a .COM extension. Doesn't the .EXE header for Windows executables have some extra information that is usually ignored by MS-DOS (e.g. which version of Windows it's written for)?

I think we're getting side-tracked here......

back in the dos days many people knew that  a .com file would always be executed first if a .com file and a .exe file had the same name. so then you could play a evil trick on your freinds and have a dir.com that shows the same information as dir does but also erases a random file each time the freind types dir. so suddenly after typing dir a lot there is no more files left in parts of the directories and your freind types dir a lot more to find the files again. (the files could be notes for exam or schoolwork) 

my point is that even today most people on a windows computer that is getting infected they almost never find out someting is wrong before it is to late. and then they ignore the problem because they can just run a vira scan and all should be alright then. 

one of the old tricks i read about (some)people would play on each other in dos was to make a littel hack so  all programs that start with a certain letter was prevented from executing. 

i cant remeber how it was done but the same trick is still in use as today many virus for windows make sure that known vira products does not work after the vira infected the computer. 

if you look at the story about virus it was actually in the beginning not more than practical jokes but  it became more than just that. rootkits has its origin in UNIX but is still most effective in windows today. in any case the amount of virus and evilmalware for windows is not getting smaller or less dangerus since the days of dos. 

as in dos there is no real protection for the user which runs in admin mode all the time (there is no concept of ownership /userights like in unix in dos) and today still windows uses the default admin-mode where it also does not really matter so much if a user that is not admin gets a virus on the machine since in any case it needs to be reformatted. 

still a user can do silly things on a linux machine but one must not forget to think about the fact that linux is a lookalike of a UNIX-system which is used as a computer that many users use and the admin has knowlegde and rights to do the admin work and the other many users on the system dont. they cant compromise a unix system same as on a windows machine shared between many user accounts. 

 when we use linux today on a singel computer that is used for a singel person as desktop we are therefor also adminstrators of a unix-lookalike and that is a resposibility that i think having the sudo feature and proper education about what to do and not to do can help overcome but any time there is something needs to be done on the system you need to be aware that you use the powers that originaly was granted to a administrator which knows what he/she is doing.  at least this is what i get from readin maybe one too many UNIX books.

---

### Post by bodhi.zazen on 2009-04-12
+1 to education on sudo :twisted:

IMO too often we advise new users to run sudo or gksu to "fix" problems of permissions for example without explaining permissions.

Commands such as chmod -R 777 /foo get thrown around all too often.

---

### Post by Sealbhach on 2009-04-12
> **Therion said:**
> He makes mention that the user just ignores the curious extension.  How convenient.  One of the many faults I find in that FUD filled video.  

Lol !!! Do you not know what a regular windows user is like?  

> **Therion said:**
> My fav, though, is at :57s where he specifically states the email is from a trusted source.  Because, you know how your best buddy is ALWAYS trying to get your credit card number via an infected email attachment...  That vid is so full of fail it makes my eye's bleed.

A few months back I got three emails from a friend's mailbox whose email account had been hacked. Has it never happened to you?


.

---

### Post by bashveank on 2009-04-12
> **lisati said:**
> What I was thinking of was an EXE file that was masquerading as a COM file - the copy of Windows I was checking it out with was happy to run it as an EXE file at the command line even though it had a .COM extension. Doesn't the .EXE header for Windows executables have some extra information that is usually ignored by MS-DOS (e.g. which version of Windows it's written for)?

I think we're getting side-tracked here......

Windows NT isn't supposed to run anything other than an EXE, even if the headers say it's executable.
Seems odd that your version of windows would run a COM, unless it's a very old version, say 98 or 95.

---

### Post by bashveank on 2009-04-12
> **Sealbhach said:**
> Lol !!! Do you not know what a regular windows user is like?  


That attitude becomes a problem if Linux ever grows to a reasonable size user base...

---

### Post by Sealbhach on 2009-04-12
> **bashveank said:**
> That attitude becomes a problem if Linux ever grows to a reasonable size user base...

Exactly. If people's emails gets hijacked and churns out millions of messages to hundreds of millions of Linux users who just don't know stuff, then a vulnerability like this would have some success. At least with a .deb file it asks for sudo powers - which would set alarm bells ringing if you thought you were just opening a .jpg.....


.

---

### Post by mkrahmeh on 2009-04-12
> **Therion said:**
> I like how the proponent of this points out that the infectious email comes from a trusted source, so of course I open both the email and its suspicious payload...  

Excuse me?  As if getting emails from my friends with suspicious attachments that contain malware is an everyday occurance.  This whole thing is, IMO, just so much FUD; predicated on the user doing SOOO many things wrong and utterly contorted logic.  "Trusted sources" sending me malware in the first place for instance.

actually i've noticed that receiving such emails from trusted sources like friends..i've tried to address the problem in this [_thread_]("http://ubuntuforums.org/showthread.php?t=1108892") but ddnt get a sufficient answer for this..

a user receiving suspicious emails from trusted sources is not an everyday occurrence..but cmon..its a single point of failure, once an adversary succeeded, the cost is huge.

i agree that there is a lot of FUD in this, but maybe it stems from the apprehensions of the issue, like what is addressed in the youtube video. however, users are required to do some effort in educating themselves, at least to a minimum level, about safe habits

---

### Post by lisati on 2009-04-12
> **bashveank said:**
> Windows NT isn't supposed to run anything other than an EXE, even if the headers say it's executable.
Seems odd that your version of windows would run a COM, unless it's a very old version, say 98 or 95.

I haven't tried it in Vista (yet) but think it works in a dos box on XP, and definitely works in 98SE. 

(waits a few minutes for another machine to start up XP..... aaargh "unable to load shell notification icon", no big deal, I'll get round to fixing it eventually....yawn while waiting for everything to load...looks for a suitable file to run)

EDIT: An informal test done with one of my own programs in ".COM" file format showed that both XP Home and Vista Home premium are able to run it. Attachment removed since I've lost track of some the source code (I wanted to include the source to help allay fears that it might be malware and to provide knowledgable people with a laugh at my rough-and-ready programming style!)

---

### Post by bashveank on 2009-04-12
> **lisati said:**
> I haven't tried it in Vista (yet) but think it works in a dos box on XP, and definitely works in 98SE. 

(waits a few minutes for another machine to start up XP..... aaargh "unable to load shell notification icon", no big deal, I'll get round to fixing it eventually....yawn while waiting for everything to load...looks for a suitable file to run)

EDIT: An informal test done with one of my own programs in ".COM" file format showed that both XP Home and Vista Home premium are able to run it. Attachment removed since I've lost track of some the source code (I wanted to include the source to help allay fears that it might be malware and to provide knowledgable people with a laugh at my rough-and-ready programming style!)

Did it run in the command line through NTVDM, or did it run as a native Windows app?

---

### Post by Ichtyandr on 2009-04-14
Hello to everyone, my first post here,

first of all I really thanks to everyone for their extremely helpful discussions on many issues concerning ubuntu, without you my switch would be improbable.

concerning the topic of .desktop malware/social engineering:
a file appeared (itself?) on my desktop saying it was a picture (.png), but in fact a .desktop file (when looking into properties for complete name). having read this thread the other day I deleted it of course. note however that I never downloaded it or saved it as an attachment or anything, but was just browsing the web in the meanwhile. It still remains mystery to me how it actually appeared there. I run chkrootkit and rkhunter just in case, but nothing apart from couple of false positives (according to google).
However I must say that Ubuntu (I use Jaunty beta) is indeed very safe, my xp system used to get infected from usbs (autorun.inf thing even got on the digital camera once) and internet malware rather quickly and things were getting out of control (with consequent reformats). Ubuntu is incomparably better in this respect (and many others).

---

### Post by Roasted on 2009-05-02
Viruses are basically scripts that have a list of commands to do certain things. Am I right?

Isn't it possible that you could write an auto-run script to rm -rf /?

I mean, it sounds easy in theory (in my theory at least) but is that pretty much impossible to do? I just wasn't sure if it was even likely to happen or if this was just my mind thinking of impossible things.

---

### Post by cariboo on 2009-05-02
The command won't do anything, as you have to convince someone to run it as root in order for it to do any damage.

A normal user doesn't have read/write permissions to any directories other then the ones in their home directory.

This subject has been beaten to death here and in other forums. Have a look at the [thread=510812]Ubuntu Security[/thread] sticky.

---

### Post by bodhi.zazen on 2009-05-02
That command does nothing at all no , period.

Try it if you do not believe me ```
bodhi@entropy:~$ sudo rm -rf /                                

[sudo] password for bodhi: 
[color=darkred]rm: cannot remove root directory `/'[/color]

bodhi@entropy:~$   
```:twisted:

---

### Post by Bodsda on 2009-05-10
> **bodhi.zazen said:**
> That command does nothing at all no , period.

Try it if you do not believe me ```
bodhi@entropy:~$ sudo rm -rf /                                

[sudo] password for bodhi: 
[color=darkred]rm: cannot remove root directory `/'[/color]

bodhi@entropy:~$   
```:twisted:

Wow, hmm, im not sure whether I like that feature for protecting peoples machines or despise it for telling me i cant do something that I wont to do!

Is the stopping you from rm -rf'ing / built into rm or sudo?

---

### Post by sisco311 on 2009-05-10
> **Bodsda said:**
> Wow, hmm, im not sure whether I like that feature for protecting peoples machines or despise it for telling me i cant do something that I wont to do!

Is the stopping you from rm -rf'ing / built into rm or sudo?

The --preserve-root flag is the default for rm.
```
man rm
```

EDIT: By default, rm also refuses to remove any file that names a directory.

---

### Post by Bodsda on 2009-05-10
> **sisco311 said:**
> The --preserve-root flag is the default for rm.
```
man rm
```

```
alias rm='rm --no-preserve-root'
```

Much better, thankyou

---

### Post by sisco311 on 2009-05-10
> **Bodsda said:**
> ```
alias rm='rm --no-preserve-root'
```

Much better, thankyou

Do you really use the rm command to delete the / partition so often that you need that alias? 

The --preserve-root flag protects your system from typos and wrongly written scripts. 

On the other hand the --no-preserve-root flag can be useful in chroot jails or other types of virtualization,

EDIT: but the alias is futile, you can't run that command twice. :evil:

EDIT2: oh well, you can if you have decent AppArmor or SELinux policies.

---

### Post by albinootje on 2009-05-10
> **conphara said:**
> [http://www.youtube.com/watch?v=9HxFGQ8OpYw]("http://www.youtube.com/watch?v=9HxFGQ8OpYw")


A bit of a weak example in the video imho, it's all based on the linux-virus-in-5-minutes, which is about a Gnome and KDE dot desktop files problem.
See here : [http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

---

