---
title: "Help my 9 year old fooled around with stacer and now NO security downloads."
date: 2019-03-30
forum: New to Ubuntu
---

### Post by chowchowmann on 2019-03-30
Hello im having a problem, my child was on my computer and opened Stacer ,the system program and he said that he went to part of stacer with red and green switches. Then he said he switched all of them to green, now i get no security downloads. I tried to switch them on and off but couldnt put it back the way it was. So i figured id uninstall it and everything would go back to normal nope lol. Then i restarted my computer and still no updates from any of the many places i have checked off for updates. Can someone please help, and yes from now on im not giving him my password lol. Any help would be greatly appreciated. Thanks in advance.P.S. i keep getting when i try to update it says failed to download repository information. I dont want to use the computer if i cant do security updates im in trouble. He only fooled around in the APT repository manager all are now green and from what i remember some were red and some green. Sorry i keep posting but i have alot of work to do and i dont feel secure online without updates.

---

### Post by DuckHook on 2019-03-31
[LIST=1]
[*]Had to use some Google-Fu to even figure out what this "Stacer" is.
[*]If you install obscure, unvetted, non-repository (and therefore potentially dangerous) apps into your system, there's little that even the veterans here can do to help you. In the Linux ecosphere, even veteran power-users rarely go outside the repos. When they do, they know exactly what risk they are taking and know how to deal with the consequences.
[*]Therefore, you may have to wait for help from the unicorn who has installed this app, used it and has an inkling of what switches you are talking about.
[/LIST]
I note from [this thread]("https://ubuntuforums.org/showthread.php?t=2414390") that you have recently started with Ubuntu and are worried about malware. If so, then the worse thing you can do is install apps from outside the repos. That will just about guarantee that you will eventually install something really nasty. This is an awful Windows habit that many Windows users haul over with them to Linux. Windows is a malware cesspool at least in part because its users don't practice good security habits. Years ago, I wrote [this post]("https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") in response to a similar concern. It's somewhat dated now, but you may find the contents useful.

Can't help you with your immediate problem. I haven't the foggiest idea what Stacer does and how it monkeys around with your system. Even if you got updates working again, what other little ticking time bombs did your 9-yr-old leave behind? Are you prepared to take that chance? You may have to reinstall the OS after backing up your data.

As to your more general problem:

[LIST]
[*]I strongly advise you to stick with the repos and nothing else until you are well-versed in Linux and Ubuntu (at which point, you will likely naturally refrain from installing outside apps anyway due to better understanding their inherent dangers).
[*]Create another account for your 9-yr-old. S/he shouldn't be on your system with anything remotely approaching superuser privileges. Linux was built from the ground up as a multi-user OS for exactly this reason.
[*]After you reinstall and get everything back on an even keel, you may find the two threads in my sig worth readiing: "Linux is Not Windows" and "Security Basics"
[/LIST]

---

### Post by Rubi1200 on 2019-03-31
Just to reiterate what DuckHook wrote above, best to stick with official and approved repositories.

I found this article, [https://www.omgubuntu.co.uk/2017/01/stacer-system-optimizer-for-ubuntu](https://www.omgubuntu.co.uk/2017/01/stacer-system-optimizer-for-ubuntu), and it seems it is some kind of system optimizer. The author of the article warns in a number of places the potential damage that can occur with unsupervised usage shall we say.

I would recommend contacting the developers and asking for specific help with rectifying the problems because they would likely know best what to do in this specific case:
[https://github.com/oguzhaninan/Stacer](https://github.com/oguzhaninan/Stacer)

Hope this helps.

---

### Post by freemedia2018 on 2019-03-31
NOT to negate the points about software outside repos.

But Stacer is just a system configuration app. I say this as someone who doesn't just download things and run them without vetting, but as someone who puts together applications into a bootable distro.

The problem is that it lets you manage your startups and services, and that the OP doesn't know what their configuration was. Not that this forum is necessarily the best place for the answer-- the OP is probably better off talking to the maintainers of the app, and thought maybe (as it seems to be Ubuntu specific) that perhaps someone here was familiar with it. Reasonable enough.

---

### Post by Rubi1200 on 2019-03-31
@freemedia2018

I think part of the issue is that the mentality of needing what you call "just a system configuration app" is where many new users run into problems.

When you come to Linux from a Windows background where people have developed habits such as using antivirus or "cleaning/configuration" apps it is hard to break away from them.

Hopefully this will be a good learning experience for the OP and that, in the long run, they will learn to understand there is no need for these apps (especially those that can lead to unforeseen and unwanted side-effects).

Just my opinion on the matter and no disrespect intended towards your viewpoint.

---

### Post by chowchowmann on 2019-03-31
Thank you and everyone else in responding to my problem. Its called stacer and my son fooled around with the APT repository manager, thats it nothing else. This im assuming from my lack of updates, anybody who has this app i just need to know there default settings under this. Example some of the switches are set to green and some are set to red by default,and my son set them to all green. He thought he was doing a good thing by doing this and i couldnt get mad at him. But i am changing the password and computer time will be semi-supervised from now on. Anyways i did contact the software designer but im not going to hold my breath for that response lol. I contacted him 2 days ago before i came here to bother you good people with my petty problems. Anyway im lost and will continue to look around for someone that has this app Stacer and can just tell me their default settings under APT repository manager-example 1.green2.red3.green etc and so on. This way i can set it back to the way it was and then get rid of this app off my Ubuntu. It wont let me download from the repository until i set it all back to original specs. I deleted it, thought it might go back to original nope didnt work, so i had to download it again so i can reset it back when i find someone to give me that info. Ok great and thank you ALL for your responses.

---

### Post by Rubi1200 on 2019-03-31
Take a look at the page here [https://www.linuxlinks.com/stacer-system-optimizer-monitoring-software/9/](https://www.linuxlinks.com/stacer-system-optimizer-monitoring-software/9/)

This page also has a screenshot of what I assume are the default settings for APT in Stacer.

Let us know if this helped.

---

### Post by chowchowmann on 2019-03-31
Yes thats it but the persons system is loaded with different programs like virtual box and those are different. Mine are the original basic factory settings, that i need but yes thats the place where my son stuck his little paws lol. Oh man i was enjoying my Linux experience until this hic-cup happened. I just wish that someone who has this app already would read this and just let me know. But much thanks to all in this community it rocks. I will keep this post updated to let people know when i found out a solution to my problem,so this thread can be closed. I hate bothering everyone with this but im sooo stuck sorry.:(

---

### Post by Rubi1200 on 2019-03-31
Let's try a different approach.

On the keyboard enter Ctrl+Alt+T to open a terminal.

Type the following command exactly:

```
sudo apt-get update
```

If this fixes it fine, if not post back what the errors were.

Also, from the terminal run this command and post back the output:

```
cat /etc/apt/sources.list
```

Thanks.

---

### Post by chowchowmann on 2019-03-31
I saw online awhile back about virtual boxes which i know nothing about really. I was thinking if someone was so kind enough to load ubuntu 18.04 into a virtual box then install stacer on there maybe i can get the correct green,red,green etc switch settings. Just a thought i dont know im just throwing ideas into the universe lol. Thanks again guys.

---

### Post by chowchowmann on 2019-03-31
Ok i ran both lines and it still wont download updates sigh. But that was a good idea i dont know how to take a screen shot but it basically said it was unable to download from the repository because of stacer. Thank you Rubi.

---

### Post by kc1di on 2019-03-31
I have and use Stacer and what he most likely did was a was actually turn off the repositories not turn them on as they are engaged by default. 
To correct the issue go to Activities and type software - then go to software and updates and make sure the following items are checked
```
Conical-supported free .....
community maintained ....
(Restricted)
Software Restricted by ....
```

if you have added any ppa's go to the next tab (other software) make sure needed ppa's are checked and lastly go to updates tab and make sure all three box are checked and select the frequency of updates from dropdown boxes. 

When done it should reload automatically but if it does go to a terminal and type ```
sudo apt update
```
you should now receive updates and security fixes.  
And keep the youngster away from Stacer :) At least make sure he is supervised :) 
Stacer is a good overall program and runs well on ubuntu but you do have to be careful with it. Cheers!

---

### Post by chowchowmann on 2019-03-31
I have to go out for the rest of the day but i will be back and thanks to ALL who wrote their ideas and tried to help me through this problem.

---

### Post by Rubi1200 on 2019-03-31
@kc1di 

thanks for jumping in and helping out.

@chowchowmann

I installed Stacer on a test partition and I believe if you follow the advice given above you should be back in business.

Please let us know what happens and please consider whether you really need something like this.

Thanks.

---

### Post by oldos2er on 2019-03-31
I'd consider creating a separate user account (very locked down) for your nine year old.

---

### Post by chowchowmann on 2019-03-31
Thanks KC my kid turned them all green and i vaguely remember some being in the red position and some in the green. So im assuming green is on? I must fix it on the end of stacer. I followed everything you said KC and it still wont let me update security. I have to turn all the green switches in Stacer back to what it was beforehand some green some red. This is very frustrating and yes my child will have a different computer with linux on it. I'm loosing work because i dont really feel safe without updates. Thanks guys i really appreciate all your time and effort.

---

### Post by chowchowmann on 2019-04-01
If anybody out there can help me i would be forever grateful im loosing a lot staying offline on my computer. I'm using my gf's computer for now till i get back to my security updates. So its back to windows for the time being (sigh). I tried running ubuntu on my gf's computer in a virtual box but that didnt go very well, im not the most computer literate person in the world, i know big shocker lol. I truly appreciate everyones input into this matter, and i know it may seem trivial but its very important to me and my family. I'm shocked that im unable to change this setting through the terminal. I just have to wait til someone reads this who has has stacer, who can tell me the correct APT repository manager settings, to change it back or about the idea of a virtual machine and someone can just run it, then download stacer and get the correct settings. Until then im proverbially screwed. Again thank you to everybody who tried to help me i really appreciate it,thanks guys.

---

### Post by chowchowmann on 2019-04-01
KC i followed all your instructions but it MUST be turned off in stacer-(in the APT repository manager) not in the software updates because all boxes are checked in software updates, and then i did an update and it wouldnt let me change my settings i have to do it in the program stacer. This is soooo frustrating #-oThanks again guys i thank you for your time. P.S. Rubi as soon as i get my APT repository manager settings back this program is going to be deleted sooo fast my heads going to spin lol. Could someone tell me how to take a snapshot of my APT repository manager in Stacer, and to post it here,so everyone can get a better understanding of what im talking about? I tried putting some of the settings back to what i thought was original settings spent like 1 hour switching settings back and forth then trying to update but to no avail.

---

### Post by Rubi1200 on 2019-04-01
What Ubuntu version are you using?

---

### Post by kc1di on 2019-04-01
ok What happens when you go to a terminal and type this command ```
sudo apt update
```?
Any error messages?

---

### Post by chowchowmann on 2019-04-01
I'm using 18.04.2 with the Gnome desktop and my computer is 64x bit. Is there any way to get updates and bypass the stacer through the terminal? I had a copy of mint 19.1 i found and ran it on my computer and then downloaded stacer and tried to run it in mint but it said i already had it installed which was weird because i thought when i ran a live DVD it was like a virtual box? But that attempt failed,now im watching stacer you-tube videos to maybe find some answers.

---

### Post by chowchowmann on 2019-04-01
KC how do you take a screen shot of the terminal? I'm new to this terminal KC dont think it says any error codes.

---

### Post by chowchowmann on 2019-04-01
Be back a little later guys thanks again for all the support.

---

### Post by Rubi1200 on 2019-04-01
Just a thought, but based on everything that has gone before I suggest the etc/apt/sources.list has probably been corrupted and needs to be replaced with a "clean" version.

@kc1di what do you say?

---

### Post by DuckHook on 2019-04-01
My recommendation is less about the technical; more about the practical…

[LIST=1]
[*]You have now spent close to 2 days trying to fix this.
[*]A fresh install takes about 40 minutes (on my 12-yr-old underpowered laptop).
[*]Backing up /home first, then restoring, may add another hour.
[*]You already know that Ubuntu runs on this machine (which, on new installs, is already half the battle won).
[/LIST]
Seems to me that, from a purely practical perspective, it makes more sense to start over than to continue playing whack-a-mole.

Pros:

[LIST]
[*]You get a fresh install that works.
[*]You know that you will have no holes or security issues.
[*]You get peace of mind (provided you don't install any more stuff from outside the repos).
[/LIST]
Cons:

[LIST]
[*]You will have to invest &#8776;2 hrs.
[*]You will have to reconfigure whatever customizations and personalizations you made (though it seems your installation was pretty new, so how many could it be?).
[*]You will have to learn how to backup/restore (not a bad skill to have in any event—see my sig).
[/LIST]
As an aside: your nine-year-old seems like a clever and well-meaning lad. No blame attaches to him and he should, in fact, be encouraged to keep experimenting with computers. He keeps up such interest and he could be in a very decent career in 10+ years.

---

### Post by chowchowmann on 2019-04-01
I was thinking the same thing about a new install but couldnt we play whack a mole for a few more trys because thats the last resort. Like i said im not that good with the computer thing and with everything else in my day believe it or not 2-3 hrs is alot in my schedule. i'm sooo busy running around i have very few minuets in the day. But if worse comes to worse i will do a new install. Thanks alot. P,S. i was also thinking that if my son turned all the switches from green/red to ALL green wouldnt that allow more downloads to be open to go through? And not to stop all updates.Ok thanks again.

---

### Post by chowchowmann on 2019-04-01
You all have done a fantastic job trying to help my situation, but could you maybe recommend another place to post this question, if i get no more help in this area? Lol duck hes good now with the computer, i ordered him his own one from e-bay and im putting mint on it for him.

---

### Post by mc4man on 2019-04-01
Green is on, red is off. By default stacer would just show what is currently set on your or anyone's machine. In a fresh default Ubuntu install that would mean green for everything except 
deb-src repos
partner repos
deb-cdrom
(doesn't appear stacer is aware of the 'proposed' repo

So you likely don't have any real issue.
Run and post the results of 
```
sudo apt update
```

---

### Post by jdeca57 on 2019-04-01
I'm probably making it simple but why don't you uninstall that program Stacer and then put in a default /etc/apt/sources.list? As a matter of fact I have a sources.list.save in that directory, you might use that. If Stacer has a good uninstall program then there is no reason why security updates wouldn't work. Afterwards you can always reinstall Stacer. (If you really want it)

---

### Post by chowchowmann on 2019-04-01
MC4 im getting much closer with your help but im still not there quite yet. I changed all the things that you told me too but im still getting a message failed to download from repository. I did the update from the terminal and it did download some things i just dont know how to take a screen-shot of my terminal to show you. And when i learn how to do a screen-shot i can show you my APT repository manager in stacer. Thanks alot. And JDE i did uninstall stacer thinking that it might revert back to earlier but it didnt. The sources code you gave me do i run that in the terminal? Im totally computer illiterate lol.

---

### Post by jdeca57 on 2019-04-01
> **chowchowmann said:**
> And JDE i did uninstall stacer thinking that it might revert back to earlier but it didnt. The sources code you gave me do i run that in the terminal? Im totally computer illiterate lol.
No. Many configurations are made by simple text files and they decide how the system acts. Of course there are graphical interfaces like the stacer to make things easier but in fact they isolate users from the real decisions. The main driver of updates in Ubuntu is a simple text file and you can write in it and guide your system that way. Of course, you have to know what you want and that's where standard templates (the files that came with the installation) or backups, typically with an extension .save or .old can help to retrieve earlier information.

---

### Post by chowchowmann on 2019-04-01
Stacer has made my life way more complicated lol. When i get this fixed im getting rid of this program. I mean its an ok program just dont touch things you shouldnt. I just dont want to start all over from scratch im new to ubuntu about 2 months and it that time ive done alot on this computer and to do a fresh install im dreading the thought. But what your talking about JDE is way above my pay grade i wouldnt know where to begin with what youre talking about. You make it sound soo easy, but im sure its harder than youre making it out to be.

---

### Post by chowchowmann on 2019-04-01
This is what my block is when trying the software updater and i get the message cannot download the repositories.> E:The repository 'cdrom://Ubuntu 18.04 LTS _Bionic. Thats the message that also comes up dont know what it means?

---

### Post by CatKiller on 2019-04-02
> **chowchowmann said:**
>  im sure its harder than youre making it out to be.
And that's why you're in a pickle: you've assumed that it must be hard, so you've installed random stuff to make things "easier," without finding out whether it is actually hard. 
> **chowchowmann said:**
> This is what my block is when trying the software updater and i get the message cannot download the repositories.> E:The repository 'cdrom://Ubuntu 18.04 LTS _Bionic. Thats the message that also comes up dont know what it means?
The first release of Ubuntu, which was installed from a cd, had useful software included on the cd that wasn't installed by default. For example, the default Ubuntu user has no need of a compiler, but one who had no network access until they can compile a WiFi driver is scuppered without one.

By having the sources.list include a configured-but-commented-out line that would allow the cd to act as a local repository, enabling this only involves uncommenting that line or putting a tick in a box, and then the user can simply install *build-essential* from the cd. I don't expect that this facility is used as much as it once was, but it's still included just in case - much like the default wallpaper always being called warty-final.

You'll want to comment out the entry in sources.list that adds the entry to use the install medium as a local repository. It's usually the first one. From your description you'll probably also want to comment out the deb-src entries, which allow you to download packages as source code so you can compile them yourself, while you're there.

Where the package manager should download files from really is controlled by a collection of text files.

Edited to add: you should talk through what you're doing with the software sources with your child. They'll be able to follow it, and seeing the package manager get the list of available packages, and choosing which packages also need to be installed for the ones you've asked for, is fundamental to understanding how software is installed in Ubuntu.

---

### Post by Impavidus on 2019-04-02
I may be joining late, but as nobody gave a straight answer to this question yet...
> **chowchowmann said:**
> I did the update from the terminal and it did download some things i just dont know how to take a screen-shot of my terminal to show you. And when i learn how to do a screen-shot i can show you my APT repository manager in stacer.
There's a screenshot application. Where you can find it depends on your desktop environment, but it should be there somewhere. Try hitting PrtSc (the print screen button on your keyboard), although that may not give the option of making a screenshot of a single window.

But for terminal output that's the hard way, both for you and for us. It's text, you can select it and paste it in your post. Select, use the menu (or right-click menu) or ctrl+shift+c to copy, then the menu (or right click menu) or ctrl+v to paste in your web browser, or simply select the text and use the middle mouse button to paste. There are several ways to do this. Then put[noparse]```
code tags
```[/noparse] around it to make it easier to read.

A different note, not getting security updates doesn't instantly make your system unsafe to use. Yes, it will get insecure after a while, but there are plenty of people who only install updates once a week. After just two days there's no need to worry. It's just one layer of defence that's slightly degraded.

---

### Post by chowchowmann on 2019-04-02
Ok heres the screen shot of some of the terminal after i ran sudo update, couldnt get the whole thing is one shot. Damn i uploaded my screen shot but its not here. Lol im such a newb. Thanks my friends for all your positive and helpful input.

---

### Post by chowchowmann on 2019-04-02
I'm doing something wrong? I click on the add extension from the advanced reply button, then i upload my terminal pic but when i post reply its not there?

---

### Post by Rubi1200 on 2019-04-02
If the screenshot is saved on the desktop for example then click Go Advanced and then Insert Image and see if that works.

---

### Post by chowchowmann on 2019-04-02
Hi guys thanks for all your help in the end i went with what duck suggested i did a clean install with Mint 19.1. Little easier  looks like XP. Thanks again in the end it was the best option before i had a stroke lol.

---

### Post by Rubi1200 on 2019-04-02
Glad you managed to find a solution that works. I hope this has been a good learning experience, both with the Stacer adventures and with your kid.

We've all been there before, messed things up and had to reinstall so I hope you take the good things from this little experiment :-)

Please mark the thread Solved.

Thanks.

---

### Post by chowchowmann on 2019-04-02
Thanks to Rubi and all. ):P

---

### Post by kc1di on 2019-04-03
Glad you got a working machine again.  Mint is a good distro. Enjoy :)

---

### Post by chowchowmann on 2019-04-03
Thanks KC.

---

