---
title: "The checking for errors"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by rima on 2012-01-08
Hello! Well, I unplugged the laptop from the power supply and just left it there *didn't shut the system properly*. When I turned it on, and chose on dual boot Ubuntu, suddenly I had &quot;checking the disk drive for errors&quot; below the ubuntu logo. I was surprised, since I never had any problems with widnows OR ubuntu before...i skipped it since I found no problem and usually things like this take ages. Is there anything to worry about? thank you, rima

---

### Post by bodhi.zazen on 2012-01-08
If you loose power like that, or if when you boot it is time to check the file system, it is far better to let it run as a part of 'routine maintance".

If everything is working you are probably "OK", but I would  let these things run.

---

### Post by Jay Car on 2012-01-08
> **rima said:**
> Hello! Well, I unplugged the laptop from the power supply and just left it there *didn't shut the system properly*. When I turned it on, and chose on dual boot Ubuntu, suddenly I had &quot;checking the disk drive for errors&quot; below the ubuntu logo. I was surprised, since I never had any problems with widnows OR ubuntu before...i skipped it since I found no problem and usually things like this take ages. Is there anything to worry about? thank you, rima

I don't remember the number exactly, but Ubuntu will do a disk check after a certain number of boot-ups (25, maybe?), and I know that those disk-checks in Windows used to take a long time (especially when you really needed to get started on a task), but I've never seen the disk-checks in Ubuntu take very long at all...maybe a minute or so, tops.  

So if it starts the check again the next time you boot, let it go and see how long it takes.  My guess is that you'll be lookin' at your desktop very shortly. Plus, it's much better to let the disk-check finish after a bad shut-down.

:)

---

### Post by CharlesA on 2012-01-08
If I remember right, fsck runs after 30 mounts. Just let it run as it will only take a few minutes.

If the machine lost power, the drive is marked as "dirty" and forces fsck to run to make sure there are no errors in the file system.

---

### Post by rima on 2012-01-08
Thank you :) So I guess if i'm not experiencing any serious problems, I shouldn't worry but let it run next time, just to make sure?   BTW i really like the idea of ubuntu maintaining the system. and since it's short, then I guess I shouldn't have an excuse not to let it run.

---

### Post by CharlesA on 2012-01-08
> **rima said:**
> Thank you :) So I guess if i'm not experiencing any serious problems, I shouldn't worry but let it run next time, just to make sure?   BTW i really like the idea of ubuntu maintaining the system. and since it's short, then I guess I shouldn't have an excuse not to let it run.
If it didn't report any errors, you should be fine. :)

---

### Post by rima on 2012-01-10
OK guys. I have discovered something. The checking for errors thing said that I have some errors with drive :/ or something like this I chose to ignore, since it's likely a false positive *as I have not experienced any problems* and I'm not really an expert on these sort of things.  Any help would be appreciated *i don't really want to mess my system up...*

---

### Post by CharlesA on 2012-01-10
You should attempt to fix any errors if they are detected.

Run this:

```
sudo touch /forcefsck
```

And reboot, and let the scan run again.

---

### Post by rima on 2012-01-10
I have no idea what's wrong, but every time the terminal prompts me for a password and I type it in, nothing would get typed up. And so, when I go onto the next line, I get the same "Sorry, try again" in the middle of when I write it. WHat should I do? Is it something to do with me being a Limited user/A standard user?

---

### Post by oldos2er on 2012-01-10
It's normal not to see anything echoed to the screen when you type your password into a terminal. [http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by rima on 2012-01-10
Oh, I see XD   But now I get:  &quot;*my name* is not in the sudoers file. this incident will be reported*  what on earth...?  ..EDIT: looks like i broke my sudo. great. Should I make myself an admin?

---

### Post by rima on 2012-01-10
I think the actual boor error is that I removed myself from the Admin group (stupid me...)

---

### Post by Elfy on 2012-01-10
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

2 links to the same site - I'd make sure to bookmark that one :)

---

### Post by rima on 2012-01-10
Yeah, I was just reading that link *incidently* XD So, is it okay for me to boot into recovery and run as root?  BTW psychocats is awesome.

---

### Post by Elfy on 2012-01-10
It is ok to boot recovery mode - that is what it's for :)

Just be aware that you can break things if you aren't careful.

Also if you have a new version of ubuntu - you will probably need to run the Mount Drives or Remount drives before you will be able to fix your sudo. The menu will change once you have done so.

---

### Post by rima on 2012-01-10
I will be careful :) But how do you Mount Drivers? Please, I'm a complete n00b to Ubuntu...please help. I don't wanna fail my system. "I'm only a grammar school teenage kid" I don't want to run screaming back to Windows.

---

### Post by CharlesA on 2012-01-10
If you are using recovery mode, you can just fix the sudoers file. You don't have to mount anything. ;)

---

### Post by Elfy on 2012-01-10
In the new version recovery mode starts read only - there is an option in the first menu to mount them - use it then press enter when prompted and you will be back at the menu - then you can use the root terminal

---

### Post by CharlesA on 2012-01-10
> **forestpiskie said:**
> In the new version recovery mode starts read only - there is an option in the first menu to mount them - use it then press enter when prompted and you will be back at the menu - then you can use the root terminal
I didn't know that. Thanks!

---

### Post by rima on 2012-01-10
OK, now two people tell me different things...but I do guess it'll be a good idea to mount it. Thank you! I shall do so in a sec

---

### Post by CharlesA on 2012-01-10
> **rima said:**
> OK, now two people tell me different things...but I do guess it'll be a good idea to mount it. Thank you! I shall do so in a sec
forestpiskie is right. I've not used the newer versions of Ubuntu much. ;)

---

### Post by rima on 2012-01-10
I see XD I guess let's just pray to God I don't screw things up :D  BUt I really like the idea that even if I screw it up with such a simple thing, I can still uninstall Ubuntu from Windows and reinstall it again. Such an excellent OS

---

### Post by Elfy on 2012-01-10
Oh - is this wubi?

I assume it uses the same options - only used it once a long time ago. Please make sure in future to use the wubi prefix not the ubuntu one - changed to suit now.

---

### Post by rima on 2012-01-10
Guys, I went into the recovery mode and it did automatically did a forced drive check. It corrected the errors with my prompt *which weren't really that serious* and rebooted. it doesn't check for errors on boot so far anymore and the computer seems to run x132343828 times FASTER! XD so I guess it's good. so the problem nr1 is solved. I think it was something to do with the &quot;orphaned loops&quot; or something.it was in Polish, so I don't know.  DO I still need to make myself an Admin though?  as with regards to Wubi, I'm sorry :( I wasn't quite sure what to use &quot;told you I was a n00b! XD but I guess everyone has to start from somewhere)

---

### Post by Elfy on 2012-01-10
Glad that bit is done, now for the admin :)

> I guess everyone has to start from somewhereAbsolutely - this was the first forum I ever bothered with - my second thread was how do you bump ...

---

### Post by rima on 2012-01-10
Yeah, have to sort the admin bit out.   I guess I just follow the instructions on mounting and do the "adduser username admin" thing?

---

### Post by CharlesA on 2012-01-10
You'd have to add your user to the admin group.. but if you are using the same user you installed as, it should already be in the admin group.

---

### Post by rima on 2012-01-10
So I guess it's unneccesary to add myself into the admin group, since I'm already one?  If so, why does the Terminal refuse to work, with "user is not listed in the sudoers file, incident will be reported?"  Would going into System Setting > User Accounts and changing my status from 'standard' to 'admin' work?

---

### Post by CharlesA on 2012-01-10
> **rima said:**
> So I guess it's unneccesary to add myself into the admin group, since I'm already one?  If so, why does the Terminal refuse to work, with "user is not listed in the sudoers file, incident will be reported?"  Would going into System Setting > User Accounts and changing my status from 'standard' to 'admin' work?
You could try that.

---

### Post by rima on 2012-01-10
Nope. It wouldn't let me change it.  I guess you can go on from "admin" to standard but not the other way around.  Hmm... in that case I have to play around with the recovery mode then....  Is it still necessary for me to mount the drive?

---

### Post by CharlesA on 2012-01-10
> **rima said:**
> Nope. It wouldn't let me change it.  I guess you can go on from "admin" to standard but not the other way around.  Hmm... in that case I have to play around with the recovery mode then....  Is it still necessary for me to mount the drive?
Probably. If the install was so messed up from a hard shutdown (which it shouldn't have been), it would probably be easier to just back everything up and reinstall.

---

### Post by rima on 2012-01-10
No, I think there's no need to reinstall XD I installed Ubuntu 4 weeks ago and the installation was very successful. It's just that I need to change into Admin again XD Psychocats tutorial pretty explained it all to me...I was stupid thinking that changing myself to standard will "limit" me too and so if I get hacked the hacker won't get me. "Kind of windows way of thinking..." BUt i guess everyone makes mistakes. ALl i need to do is just type in "adduser username admin" and that's it XD  To be honest, reinstalling doesn't really bother me that much, I never had any files on Ubuntu anyway except for a couple of old photos.

---

### Post by CharlesA on 2012-01-10
Gotcha.

You'd have to add yourself back to the admin group. Boot to recovery mode, mount the drives and drop to a root prompt and run this:

```
usermod -a -G admin username
```

[http://linux.die.net/man/8/usermod](http://linux.die.net/man/8/usermod)

---

### Post by rima on 2012-01-10
Will try that.  Thanks for help guys!  I've just got a small question: shall I use   usermod a- G- admin username  OR   adduser username admin  ?  Confused.  Some people told me the other one, others said above.  In times like this I wish I had Linux friends~  It's just that I really want to use the Terminal you know. Eventhough I'm relatively new to Linux, I'm not that scared of it....as long as I don't type in random commands everything will be fine, I tell myself :D

---

### Post by CharlesA on 2012-01-10
adduser create a new user, usermod modifies an existing user, so use usermod.

---

### Post by rima on 2012-01-11
OK thanks :)  EDIT: I was just wondering; what's the difference between the Admin and the Standard (except for the obvious Sudoers)? Standard users still download programs...

---

### Post by rima on 2012-01-11
// deleted post

---

### Post by rima on 2012-01-11
OK, this is getting frustrating. I didn't get into the &quot;graphical&quot; sort of user interface, only straight to the actual terminal. I used the &quot;usermod -a -G admin username&quot;, did it but the terminal said something among the lines of &quot;unable to set up a password for myusername. try again later&quot; or something like this.   It's not that I'm actually THAT keen to use the terminal, but setting myself up as an Admin again is frustrating. I didn't to mount the drives. Maybe that's why it's in &quot;read only?&quot; any code for mounting?    EDIT:. I changed my User Account from Admin into Standard somehow, and I'm unable to SUDO in Terminal. it's not like I care too much, as I said I only use computer for this one or two websites and drawing, and nothing much beside that, except for occassional typewriting.  I think I'll just give up and use Standard...or make another admin account or something.

---

### Post by rima on 2012-01-11
bump bump bump  D'you know what? Since everything is fine, I don't really need to use the Terminal and nothing's going strange *i feel so lucky* shall I just add another user as an admin with adduser username admin?   When one day I won't feel tired XD So basically I just give up

---

### Post by CharlesA on 2012-01-11
You'd still need sudo access to add a user, so if you still don't have it, you would need to go back into recovery mode to use it:

```
adduser -G admin username
```

I'd really suggest backing your stuff up and reinstalling since something is definitely wrong with the install.

---

### Post by cryptotheslow on 2012-01-11
> **rima said:**
> I didn't to mount the drives. Maybe that's why it's in &quot;read only?&quot; any code for mounting?

You need to mount the filesystem as read/write when entering the recovery console mode. As previously explained there is a menu option to do so.

If the filesystem is in read-only mode the **usermod** command cannot make the necessary changes to the required files - hence the error message you get.

If you still can't figure it out, just shout and I'll grab some screenshots of the process and post them up. Are you using v11.10?

---

### Post by cryptotheslow on 2012-01-11
I got bored so did a walkthrough anyway :D Hope it's not too much information for these forums!

So we begin. rima has somehow become a Standard user. Uh-ohhh...
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/useraccountsstart.png[/IMG]

Reboot and Select Recovery Mode from the GRUB menu:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/grubmenu1110.png[/IMG]

From the Recovery Menu select the remount option to mount the / filesystem read/write - press ENTER when prompted:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryremount2.png[/IMG]

You are then presented with a slightly different menu - select the bottom option to drop to a root shell:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryconsolerootprompt.png[/IMG]

Add rima back into the admin group using the command CharlesA provided:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/addusertoadmingroup.png[/IMG]

Then simply enter the command **exit** to get back to the Recovery Console - select the option to resume normal boot:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoverymenuresume.png[/IMG]

Once booted up login as normal and YAY:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/useraccountsyay.png[/IMG]

---

### Post by theDaveTheRave on 2012-01-11
I found this to be an interesting thread.

I always thought that on Debian based systems you logged in as a 'standard' user and that user was able to administer the system by use of sudo .

The users that where allowed to sudo where kept in the /etc/sudoers file

So I just had a look at the sudoers file on my system

```

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

```

So I guess Rima could have edited this file directly whilst in recovery mode.

which has raised 2 questions for me.

If I was to add a user specifically to the file, such as the following

```

%rima ALL=(ALL) ALL

```

I guess that the user rima would now be able to do all the functions that the root user can do. is that correct?

The second question is, what do the options 
```
ALL=(ALL) ALL
```
do in terms of changing the functionality of the user (i'm guessing you can add in the option to enable the user to have control of the network interface, printers etc, but not be able to install new software.

I just started to RTFM for sudoers, and as yet I haven't come across the explanation.... ;)

it reads fairly easily, but doesn't seem to answer my question at first glance....


David

---

### Post by CharlesA on 2012-01-11
The % means "group," so if you wanted to add a normal user, you'd exclude the %.

---

### Post by jmate24 on 2012-01-11
> **Jay Car said:**
> I don't remember the number exactly, but Ubuntu will do a disk check after a certain number of boot-ups (25, maybe?), and I know that those disk-checks in Windows used to take a long time (especially when you really needed to get started on a task), but I've never seen the disk-checks in Ubuntu take very long at all...maybe a minute or so, tops.  

So if it starts the check again the next time you boot, let it go and see how long it takes.  My guess is that you'll be lookin' at your desktop very shortly. Plus, it's much better to let the disk-check finish after a bad shut-down.

:)

The number of disk checks varies with the size and type of filesystem.

---

### Post by rima on 2012-01-14
I dont really want a reinstall.  Please.  I just...I can't. Nothing's wrong with the install... I'll be fine without adding any users.    Please, I don't want this to be complicated.  I'm a real  n00b. I screw things up easily.  the thing is, since i'm a wubi user, i could unistall ubuntu in 5 minutes, reinstall, and everything have running fine again.  the thing is, i don't want to mess around with it too much.  i'll be leaving guys, thanks for help :) but since I'm able to draw on GIMP and surf the web and do everything i need it to do, i'm not an uber computer geek to find stuff fun like that XD i'm sorry :( Maybe one day if I gain more confidience and experience in ubuntu i'll motivate myself and do it, you know......mark my words, i bet i'll be laughing at all my posts in this thread in a couple of years' time XD

---

### Post by rima on 2012-01-25
Okay guys, it seems the only problem is

me

Yes, that's right. It's me.

I'm really scared of booting into recovery mode, after not-so-nice experiences last time (can't even remember what was wrong, but still...the idea of me, 13-year old grammar schoolgirl sitting in front of a root terminal doesn't seem appealing) 

I know, I know.

Another problem. I can't seem to update now.

It's not like I actually care on a serious level (eventhough I should...? You know, installing to be secure and all that?...). It asks me for a root password. Doesn't seem to accept anything, and a couple of minutes later, it says: something like background daemon crashed? You know, the apt-daemon one? 

One stupid move, and I crashed my software update
I crashed my mentality of ubuntu too

Please tell me recovery mode isn't scary. Don't even bother trying to say "Let your Dad do it" because he won't. He has no idea that Linux does that. He would probobaly screw up the system worse

And I know no IT technician, so that sucks too...

Seems like you have to get me out of my "RECOVERY MODE IS SCARY" mentality

---

### Post by CharlesA on 2012-01-25
Well recovery mode is a bit scary because you are at a root prompt and that would allow you to do anything to your system - both good and bad.

As for being unable to update, what happens when you run this:

```
sudo apt-get update
```

---

### Post by rima on 2012-01-25
Again. Same thing.

"xxx is not listed in the sudoers file. this incident will be reported.

I guess it's just a privilage thing and nothing else

But stil...i'm still scared of recovery mode

Thanks to cryptotheslow for walkthrough, it clears stuff up a bit ^^''

---

### Post by CharlesA on 2012-01-25
OK, let's do this. Run these:

```
grep admin /etc/group
```

If you are still in recovery mode and at a root prompt, you can run this:

```
tail /etc/sudoers
```

---

### Post by rima on 2012-01-25
Oh, d'you know that you asked me to do;

sudo apt-get update?

I typed in it just now in terminal....not at the recovery mode root command, if that's what you wanted

And the other two commands. I'm just curious, what do they do?

---

### Post by CharlesA on 2012-01-25
The first one shows who is in the admin group.

The second displays the last few lines of the sudoers file.

---

### Post by rima on 2012-01-25
Okay thanks.

WIll do so tommorrow *i feel a bit tired today*....

but first, i'll try the usermod -a -G user admin command, see what it shows up with.

Thanks for the help! It doesn't seem that complicated...but i'm very talented at screwing up things, so XD

---

### Post by CharlesA on 2012-01-25
That's the way we learn. :D

---

### Post by rima on 2012-01-26
Now, the thread title should say "This is what happens as a result of a 13 year old, inexperienced Linux user trying out new stuff in Linux."

Ok, ok, i'll stop XD

The thing is, I love Ubuntu and eventhough I can switch perfectly fine to Windows, I don't want to. I just don't. Not cos there's anything wrong with Windows, it's just that I accept it as "failure" and proving that I destroy everything I ran into. (on the other hand, I heard people screwing up their systems pretty bad and 1000 times worse then me....and they're all adults....)

So i went and booted into recovery mode. But I said - nearly the same error. The colourful purple screen with prompts doesn't come up. 

Instead, something like "blah blah blah remainder is 247? Can't remember" and it automatically drops me down to a root prompt.

What do I do guys?! Help me! Now

a) I don't want it to be complicated, please, PLEASE....
b) I don't want to uninstall *only when the push comes to shove....*
c) is there a graphical user tool that would allow me to be an Administrator?
d) since i'm automatically at the root prompt, what would you like me to run? like a command for mounting the drives and then "usermod" command? Or something else?

Thanks in advance.

---

### Post by CharlesA on 2012-01-26
Run these from the root prompt and post the output.
```
grep admin /etc/group
```

Also run this:

```
tail /etc/sudoers
```

Just want to make sure sudoers is set up correctly and that you are a member of the admin group before doing anything else.

---

### Post by rima on 2012-01-27
Okay guys

I decided

I'll uninstall and reinstall

Yea, because I gave up like that :(

Eventhough I did not want at first (since I think you should uninstall when you have a failing drive, not just when you 'feel like it'....) but I'm just not bothering anymore.

So, I have a couple of *stupid* questions. *just to make sure*

1) Since I'm a wubi user, all I need to do is uninstall the Ubuntu file from Windows and that's it? It will remove itself SAFELY and COMPLETLEY and from the boot script at startup?

2) If I reinstall, is there a chance of the previous system files screwing up and crossing with the new ones?

3) Will I have to manually remove the Ubuntu partition from my drive? And if so, how do I do it?

4) If I successfully installed Ubuntu the first time, is there a chance it will successfully install the second time? 

5) I don't really like the 6 month releases, and want to try a different Linux distro. If so, what would you recommend?

Thanks in advance, just want to clean up some doubts and sleep well at night *puts a few files on her memory stick*

---

### Post by CharlesA on 2012-01-27
1) Since it is a Wubi install, you can just remove it from inside Windows.

2) Since it's Wubi and you uninstalled it, there should be no files left to mess up a new install.

3) The whole install is on an image file on the hard drive, a Wubi install does not add a partition.

4) Yes.

5) You could try Debian or Fedora (or CentOS, even), or just stick with a LTS release as they are supported for 5 years now (as of 12.04).

---

### Post by rima on 2012-01-27
Thank you so much for all who helped me. Cookies for you! :D

(but won't the boot script mess up? or will it be OK? just because i want to go safely into Windows XD)

Just a comment - I'm actually pretty impressed with Ubuntu. 8 million users with completly different hardware, system, mentality - and it seems to be successful. So cookies for Ubuntu, too~

I'll come back to Ubuntu in April, for the LTS. (you know, it's only 2 months...) So, see ya in Precise Pangolin!

rima

PS. i'll mark the thread as "solved"....for now."

---

### Post by CharlesA on 2012-01-27
It shouldn't mess anything up since Wubi just adds an entry to the windows bootloader. :)

---

### Post by rima on 2012-01-27
Oh, I see. Since wubi adds an entry, it will also be able to remove it?

Also, on another note; the only negative experience I had with Ubuntu was...the battery. It really, really uses a lot of my battery : I unplug it - nearly straight away it goes to suspend

Is there an "energy saving" version of Ubuntu? Just wondering. *sorry for the questions, but I have to say - I really learned a great deal about computers, OSs and Linux and picked up some great advice. Of course, I'll try not to repeat the same old silly mistakes XD*

Once again, thanks guys.

---

### Post by CharlesA on 2012-01-27
The entry should be removed when you uninstall it.

I'm not sure about power management since I don't run it on my laptop, but I know there have been reports that it eats batteries for lunch and that you have to configure the power settings or something.

---

### Post by rima on 2012-01-27
WIth the power thing - I heard that either lubuntu or xubuntu eat up less power or something, and starting from 12.04 lubuntu will be added "official" to the ubuntu family...Am I correct~

Plus, my battery hasn't been super strong anyway *just under an hour from unpluging* so yeah...

---

### Post by CharlesA on 2012-01-27
I'm not sure about those two since I don't use them but it would make sense because they are less "heavy" then the regular Ubuntu install.

---

### Post by MG&amp;TL on 2012-01-27
> **rima said:**
> WIth the power thing - I heard that either lubuntu or xubuntu eat up less power or something, and starting from 12.04 lubuntu will be added "official" to the ubuntu family...Am I correct~

Plus, my battery hasn't been super strong anyway *just under an hour from unpluging* so yeah...

Lubuntu has been official from 11.10, and yes, it does use up less power. I believe the power issue is mainly a  kernel power bug, though, and I also believe it's fixed in 12.04, currently at least. (Alpha releases are intended to break). So you may wish to give your laptop battery until April to prove itself.

Feel free to open a new thread or PM me if you need help; if you go down that road, and definitely read the links in my signature about Lubuntu. 

Oh, and I'm 15. 'Cookies!' for teenagers, especially nerdy ones like ourselves. :P

---

### Post by rima on 2012-01-27
Ok, I see XD 

I'll read up on other Linux distros. In times like this, I wish I had computer geeks in my area. NOT the ones with big black glasses, with colourful hair and shoes and "geek" scribbled on their faces. Nope, not those ones. Looks like me myself and I have to go the "alone" way (much like most of people).

I really like the sound of lubuntu, it seems very nice actually.

Oh, and Debian sounds cool

But I think I'll stick with Ubuntu *for now* and since Lubuntu will added to the official list, I might try it too. So, get ready my 4 year old, Windows XP netbook! Let's see what you can do :)

---

### Post by rima on 2012-01-27
Sorry to bump but this will be quick and 80% chance I won't be bothering you anymore 

1) So, does Wubi actually support Lubuntu? And so, if I successfully ran ubuntu from Wubi is there a chance I'll successfully run Lubuntu?

The reason I'm asking because apart from Wubi, there's no way I can set up dual boot. 
And then you ask
Memory stick - don't have one, and if so, it's full of important files *cough*filledwithGBsofrubbish*cough*
And my netbook's got no CD drive. 

and

[quote="MG&TL"] Oh, and I'm 15. 'Cookies!' for teenagers, especially nerdy ones like ourselves. :razz: [/quote]]*High fives* Not sure if you're telling the truth, but still :D Us Linux teens have to stick together

---

### Post by CharlesA on 2012-01-27
I don't think that Lubuntu can be installed via Wubi.
[https://answers.launchpad.net/wubi/+question/171767](https://answers.launchpad.net/wubi/+question/171767)

---

### Post by MG&amp;TL on 2012-01-27
Lubuntu 12.04 will apparently have wubi support.

Geez, what makes you think I'm not a teen? :P

---

### Post by rima on 2012-01-27
That's what I meant!

Not that it will be added to "officials," I meant it will have wubi support.

And yes, I do rely on Wubi as I've said, so this makes me very happy indeed. :P

[quote="MG&TL"] Geez, what makes you think I'm not a teen? :) [/quote]

Too high rank on the forums XD XD

---

### Post by Elfy on 2012-01-28
There are no high or low ranks on the forum - just a bunch of people - of all ages - trying to help to the best of their abilities :)

While wubi is good for testing and seeing if you like what you find - it's not a long term solution nor was it intended to be.

You might like to start thinking about dealing with a proper dual boot.

---

