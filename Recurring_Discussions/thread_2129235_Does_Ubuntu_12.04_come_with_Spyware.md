---
title: "Does Ubuntu 12.04 come with Spyware?"
date: 2013-03-25
forum: Recurring Discussions
---

### Post by Psil0cybin on 2013-03-25
I recently read this article [http://askubuntu.com/questions/226575/ubuntu-with-spyware](http://askubuntu.com/questions/226575/ubuntu-with-spyware)

I ran the command, [FONT=Ubuntu Mono]sudo apt-get remove unity-shopping-lens
[/FONT]I was than told I do not have this package on my Ubuntu.
Does this mean im clean of the spyware? OR do i have to remove the Unity panels and go back to gnome3?

Like it says here
[https://sites.google.com/site/howtomakeubuntu1204notterrible/](https://sites.google.com/site/howtomakeubuntu1204notterrible/)

Thanks in advance

Psil0

---

### Post by mc4man on 2013-03-25
No. you don't have any spyware in 12.04, nor very much 'online' from the Dash, the only 2 that show online results are - 
unity-scope-musicstores
unity-scope-video-remote

As far as your 2nd link, well,  idiots are plentiful on the web.

---

### Post by papibe on 2013-03-25
Hi Psil0cybin.

The first concern is related to version 12.10 and above. 12.04 does not have that issue.

Regarding zeitgeist, I would recommend further reading. Start with this:[ Ubuntu 12.04 will bring OS-level privacy options]("https://www.eff.org/deeplinks/2012/03/ubuntu-1204-will-bring-os-level-privacy-options"), and [Got privacy? Ubuntu Linux 12.04 will help ensure it]("https://www.eff.org/mention/got-privacy-ubuntu-linux-1204-will-help-ensure-it") (points to [this]("http://www.itworld.com/software/257368/got-privacy-ubuntu-linux-1204-will-help-ensure-it") article). 

Regards.

---

### Post by stinkeye on 2013-03-25
Online searches can be turned off System Settings > Privacy.

...and if your of the belief that it's spyware just remove the offending packages.

Don't think the shopping lens is in 12.04.

The info from Zeitgeist is only used locally in the dash and you can determine what it logs.
You can turn logging off completely if you want.
> Zeitgeist is a service which logs the user's activities and events (files
opened, websites visited, conversations held with other people, etc.) and
makes the relevant information available to other applications.

---

### Post by ManamiVixen on 2013-03-25
Unity Shopping isn't Spyware or Adware. It Canonical's equvilent of ad-assisted software like seen on free Android apps. It's meant to help Canonical keep going. Zietgeist (Watching Ghost), Only allows for data sharing on your own PC and dosen't send the data anywhere. In fact, Zeitgiest has been used since Oneric for the original Unity. It didn't become an issue untill Shopping came about.

Anyways, I remember reading somewhere that a Canonical Employee was giving thoughts on Unity and its supposed spyware/adware to a linux news article. Unfortuantly I can't remember where, but he did say something along the lines of "If you are concerned about Ubuntu sending your data over the internet in the form of helpfull search queries, Ubuntu might not be for you."

---

### Post by Psil0cybin on 2013-03-25
> **ManamiVixen said:**
> Unity Shopping isn't Spyware or Adware. It Canonical's equvilent of ad-assisted software like seen on free Android apps. It's meant to help Canonical keep going. Zietgeist (Watching Ghost), Only allows for data sharing on your own PC and dosen't send the data anywhere. In fact, Zeitgiest has been used since Oneric for the original Unity. It didn't become an issue untill Shopping came about.

Anyways, I remember reading somewhere that a Canonical Employee was giving thoughts on Unity and its supposed spyware/adware to a linux news article. Unfortuantly I can't remember where, but he did say something along the lines of "If you are concerned about Ubuntu sending your data over the internet in the form of helpfull search queries, Ubuntu might not be for you."

(SO is what you are saying, that Ubuntu cannot be trusted? - or that it is becoming more lenient to giving out information?)

If I remove the following packages in Unity would i Break it in any way shape or form
"[COLOR=#000000]unity-scope-musicstores[/COLOR]
[COLOR=#000000]unity-scope-video-remote"

[/COLOR]Also Could I turn off the Zeitgeist feature using settings > privacy ?
Or do I need to do something else.
Thanks in advance
I just wish Ubuntu would not integrate this stuff into the desktop, any tracking of any kind that goes publicly uploaded, is not good..
If someone breaches into the server, they would be able to copy all that data! I Love Ubuntu and dont want to switch to another distro...but I dont like this one bit..
I switched away from Windows 7 to stay as far away from logging as possible.
I wont mind the changes as long as it is easy to ensure, that I can turn it off and it is not running. 
psil0

---

### Post by ManamiVixen on 2013-03-25
Removing those packages are safe, but the music and video lens won't be of much use afterwards. Also it is advised to leave zeitgeist alone as Unity really can't function without it. In fact the the switch in the privacy window just stops it from recording, but keeps it running in the background. Also, all the lenses will stop either stop working or will be terribly impared if that switch is thrown or zeitgeist is removed since they all get their data from it. Have you though about using Xubuntu?

---

### Post by cortman on 2013-03-25
You can be certain you're not being logged or having your data sent to Canonical by simply not using Unity- try Xubuntu, Gnubuntu, Kubuntu or Lubuntu.
While I no longer recommend vanilla Ubuntu because of this policy being opt-out, the folks behind the other versions (Lubuntu in particular) are turning out some first class distros with all the great hardware support and software availability of standard Ubuntu.

---

### Post by Psil0cybin on 2013-03-25
I use Xubuntu on my smaller laptop,
but I am wondering if I remove** all those packages**..Could I trust that I am not being logged?
Or could this be deeper in the O.S than I am aware of ?
Or should I lose trust in Ubuntu all together?
Im just shocked, that they are planning to add all these things 12.10...
Its so sad, I really really really really loved Ubuntu
as it is the only Linux Distro that came with installed drivers for my computer.
I wish they could make Two Different O.S based on the needs you want.\
I Could see how some people could find it usefull, I personally do not...nor do I want people to know what im using my desktop for...
so sad
:mad:
Would I be able to switch to gnome classic? Sticking to gnome but removing the Unity out of it?

---

### Post by mc4man on 2013-03-25
> **ManamiVixen said:**
> Removing those packages are safe, but the music and video lens won't be of much use afterwards. 
That is totally incorrect - those 2 packages only enable online search results for the music & video lens, in no way affects the use of those lens for local files.

---

### Post by ManamiVixen on 2013-03-25
[**[COLOR=#000000]mc4man[/COLOR]**]("http://ubuntuforums.org/member.php?u=320715")  I never said they would be useless, just that they will be almost pointless. The Music Lens would only acces your Music Libray and the Video lense will only show free over the internet streams from sites Like Youtube. The Lenses were meant for more than that.

---

### Post by Psil0cybin on 2013-03-25
Sigh sorry guys, so if i wanted to avoid all these problems..
Could i Just move back to Gnome 3, and purge unity?
What do you guys think?
I downloaded Xubuntu, Just id prefer to stay on Gnome on this machine...
If i do sudo apt-get install xubuntu-desktop
would that solve my problem? Or do i need to completely remove Unity in order to get the security I desire?
What are you thoughts...
(I might just still with Xfce.. but at the moment Id prefer to have Gnome)
Im thinking of installing gnome-shell?

What do you guys think? Would this solve my problems? 
Or only make me believe I solved all my problems?
Thanks guys for your support! Much appreciated!
Psil0

---

### Post by ManamiVixen on 2013-03-25
Here, Ubuntu Gnome Remix just became an official member of the Ubuntu familly. I personally don't suggest installing Gnome-Shell over Unity. It causes all sorts of hell.
[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

---

### Post by deadflowr on 2013-03-25
The answer is NO.

---

### Post by mc4man on 2013-03-25
> **ManamiVixen said:**
> [**[COLOR=#000000]mc4man[/COLOR]**]("http://ubuntuforums.org/member.php?u=320715")  I never said they would be useless, just that they will be almost pointless. The Music Lens would only acces your Music Libray and the Video lense will only show free over the internet streams from sites Like Youtube. The Lenses were meant for more than that.

Again maybe you should try before commenting. The video lens will show all local content stored in Videos & all recently played even in other locations
I don't think that makes them pointless at all (as implemented in 12.04

(- pointless to the OP as he/she desires something else

---

### Post by ManamiVixen on 2013-03-25
I could never get the video lens to show a video stored on my PC. I might have a bug on my hand. Thanks for pointing that out mc4man!

P.S - I never used Ubuntu 12.04. I was using Fedora through out the taht time untill Ubuntu 12.10 came out. So was unaware as to how the Video lens in 12.04 worked.

---

### Post by 3rdalbum on 2013-03-25
I think people are being alarmist about Ubuntu's "spyware".

Spyware is sneaky, designed to steal financial information wherever it is on your computer. The shopping lens is not sneaky and only performs Amazon searches on search queries you type in.

Zeitgeist only knows when you opened files, and does not send that information on.

If you knew how much was logged on an ordinary conservative Linux system, your hair would turn white. The logging is for your benefit, not malicious purpose.

---

### Post by stinkeye on 2013-03-25
> **Psil0cybin said:**
> Sigh sorry guys, so if i wanted to avoid all these problems..
Could i Just move back to Gnome 3, and purge unity?
What do you guys think?
I downloaded Xubuntu, Just id prefer to stay on Gnome on this machine...
If i do sudo apt-get install xubuntu-desktop
would that solve my problem? Or do i need to completely remove Unity in order to get the security I desire?
What are you thoughts...
(I might just still with Xfce.. but at the moment Id prefer to have Gnome)
Im thinking of installing gnome-shell?

What do you guys think? Would this solve my problems? 
Or only make me believe I solved all my problems?
Thanks guys for your support! Much appreciated!
Psil0
Why do you think Unity breaches your security?
Zeitgeist logs activities as do all computers.
It's for your user experience...no info is sent out anywhere.
I like that I can just hit the super key to find a recently used app, file or whatever.

The issue many have is not with Zeitgeist but with online searches being on by default.
> Searching in the dash - When you enter a search term into the dash Ubuntu will search your Ubuntu computer and will record the search terms locally. Unless you have opted out (see the &#8220;Online Search&#8221; section below), we will also send your keystrokes as a search term to productsearch.ubuntu.com and selected third parties so that we may complement your search results with online search results from such third parties including: Facebook, Twitter, BBC and Amazon. Canonical and these selected third parties will collect your search terms and use them to provide you with search results while using Ubuntu.
Some may like to search online through the dash, say to purchase music or whatever.
I don't want online searches mingled with my local searches so I turn online search off. Simple eh?

PS. The issue your bringing up is over a year old and has been done to death.

---

### Post by Psil0cybin on 2013-03-26
Sorry about that Just wasn't sure, Im new to Linux, and therefore thought any question would be valid..
As I am learning.
Thanks again guys! Guess this is solved!

---

### Post by craig10x on 2013-03-26
On Ubuntu 12.10 and the upcoming 13.04, amazon lens, as well as the others that will be introduced, can easily be turned off in the "privacy settings" section of the system settings...you will find 2 off buttons there, once you hit those buttons, no ad lenses will appear on your searches in the unity dash...

No need to dump unity to avoid the ad lenses, if you like unity (as i and many others here do) enjoy it! 

By the way, it isn't really spyware...but as i said, easily turned off...

---

### Post by MadmanRB on 2013-03-26
There is no spyware, period.
All the spyware talk is just false alarms being sent out by Richard Stallman who thinks that you should be locked up in jail or something if ytou charge more then 0 cents for software.

---

### Post by Psil0cybin on 2013-03-26
Alright guys thanks for helping me get this sorted out :) I really appreciate it.
With much research, I have found that anything that you want to remove is easily removable.
Thanks for the advice, I really really appreciate it.

---

### Post by tartalo on 2013-03-26
> **MadmanRB said:**
> All the spyware talk is just false alarms being sent out by Richard Stallman who thinks that you should be locked up in jail or something if ytou charge more then 0 cents for software.
That is incorrect, Richard Stallman has often explained that he is in no way against charging for software. He is for freedom as defined in the famous 4 freedoms and the GPL license, not for gratis.

And call it what you want, but Ubuntu 12.10 and later sends your private searches to third parties.

---

### Post by Psil0cybin on 2013-03-26
> **tartalo said:**
> That is incorrect, Richard Stallman has often explained that he is in no way against charging for software. He is for freedom as defined in the famous 4 freedoms and the GPL license, not for gratis.

And call it what you want, but Ubuntu 12.10 and later sends your private searches to third parties.

Well that is what I am honestly worried about, but I removed those packages in 12.04, and hopefully I can feel a little more at ease. 
But 12.10 and on sounds like a bad idea for what I want out of my machine.
I'm going to stick with 12.04
or move to Xubuntu.

---

### Post by craig10x on 2013-03-26
Why? In 12.10 and 13.04 you can turn it off completely in 5 seconds...too much effort, eh? ;) :D

And again...not spyware anyway...it's just a small way for ubuntu to get some money back which they certainly deserve considering all the money that is put into by Mark Shuttleworth...
All it does is send some information to amazon so they can add some "targeted" amazon shopping suggestions for items you might be interested in...in return, ubuntu gets some revenue back...

And if you desire not to participate, you hit 2 off buttons in "privacy settings" and it is totally gone...

I think you are really making too big a deal of this...this isn't like the famous novel "1984"  big brother is NOT watching you :rolleyes:

---

### Post by matt_symes on 2013-03-26
> [FONT=arial][SIZE=2]Does Ubuntu 12.04 come with Spyware? 				[/SIZE][/FONT]

> **deadflowr said:**
> The answer is NO.

The short and sweet answer is this ^^^^. Anything else is FUD.

---

### Post by 3rdalbum on 2013-03-28
> **tartalo said:**
> That is incorrect, Richard Stallman has often explained that he is in no way against charging for software. He is for freedom as defined in the famous 4 freedoms and the GPL license, not for gratis.

And call it what you want, but Ubuntu 12.10 and later sends your private searches to third parties.

No, it doesn't. It sends your search queries to third parties IF you search Dash Home, Music or Videos, or any other lens/scope with an online component AND online searches are turned on.

Ubuntu 12.04 and below do the same, except not with Dash Home and there's no way of turning off "online searches".

They are not "private searches" if you keep online searching enabled; for the same reason as this message not being a "private message". If I wanted this message to be private, I would have used a private means of communication. If you want your search to be private, then turn off online searches or use a lens with no online component.

---

### Post by KingSombra on 2013-03-28
"Anything else is FUD."

I'm sorry. I have been a long time reader of these forums and until recently a fan of Ubuntu, but when I read this I had to create an account.

I can understand that you think its trivial.

But as a moderator I would expect you not to post a trivialization of what others think is a legitimate concern.

(Me for one, and obviously RMS.)

And GROKLAW agrees as well:

[http://www.groklaw.net/article.php?story=20130324114340352](http://www.groklaw.net/article.php?story=20130324114340352)

Canonical says "Oh we give users clear notice and they can turn the shopping lens off."

To me that sounds a lot like Microsoft saying "Oh we give notice in our clickwrap EULA."

[http://en.wikipedia.org/wiki/EULA](http://en.wikipedia.org/wiki/EULA)

( I escpecially liked the "imortal soal" bit in Criticism. :P )

The GPL is an entire different matter. I have read through it and I know that every time I see it I can accept it without fear of there being something nasty within its pages. That is serious empowerment.

But now along comes Canonical and the "shopping lens". Yes the notice of it, might not be in the GPL notice itself, but it still destroys that confidence for people who take their privacy seriously, and it feels like a betrayal.

Yes I know we can turn it off. Once again we should not have to do so. We should turn it on if we want (OPT-IN).

You may feel that RMS categorizing the shopping lens as spy-ware is unfair, but by some definitions it is exactly that.

[http://en.wikipedia.org/wiki/Spyware](http://en.wikipedia.org/wiki/Spyware)

The shopping lens can fit very nicely in the first paragraph in that WIKI, if you take the above argument about "notice" to heart. So yes the shopping lens CAN be considered to be spy-ware.

I can hear the next line already. "But Canonical encrypts the query."

But they still have to hand out the IP address so that Amazon can serve up the icons. It is trivial for Amazon to get other data about you if they have this. (You even note in the code of conduct that you use IP addresses, which is laudable. But yes IP addresses can be abused as well.)

No, I reject this concern as being trivial and FUD. There are principled people who believe it is legitimate.

And as a forum moderator, even though the concern goes against the very OS that the forums are about, I think you should'nt trivialize it.

Its even right in the forum code of conduct that you should at least be respectful of others views.

And lastly if you tell me that I can always use another distro, that would be a shame since I have been a fan of Ubuntu, but at least I could agree with that.

I am sorry if this rubs some people in these forums the wrong way. But it is how I feel about this.

---

### Post by matt_symes on 2013-03-28
> Me for one, and obviously RMS.

Argument from authority eh ?

There are many things RMS says that i think are wrong.

I'm just a Ubuntu user like you, but because of that i'm not allowed to disagree ?

As i  stated before, "anything else is FUD!"

But don't take my word for it, you have the source code and tools; go check yourself.

---

### Post by haqking on 2013-03-28
> **matt_symes said:**
> Argument from authority eh ?

There are many things RMS says that i think are wrong.

I'm just a Ubuntu user like you, but because of that i'm not allowed to disagree ?

As i  stated before, "anything else is FUD!"

But don't take my word for it, you have the source code and tools; go check yourself.

+1

Your Japanese Proverb fits well ;)

And for the record saying "anything else is FUD" is not trivialising others concerns it is an opinion, neither is it disrespectful of others views or opinions and wasnt targeted at an individual post.


Peace

---

