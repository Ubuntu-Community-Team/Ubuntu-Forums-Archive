---
title: "One thing I dislike about Ubuntu (password authentication requests)"
date: 2009-11-14
forum: Recurring Discussions
---

### Post by lakersforce on 2009-11-14
/*DISCLAIMER*/ If you are looking for a flamewar please go somewhere else! If you are a non-critical Ubuntu-fanboy or Microsoft-loather, not open for suggestions, I suggest you stop reading here, before you get carried away./*DISCLAIMER*/

Even after you have positively identified yourself at login you still have to keep providing the password every time you do something that affects your system.

Since I have already provided it once, it is really a bad idea. It encourages bad passwords like "1". In this regard it should work like Windows Vista or 7. I mean, in the end the system is not safer than the user anyway. So why all the hassle?

---

### Post by Monotoko on 2009-11-14
You login to your own account, which is a very limited account, which means if someone hacks it, or jus uses your machine while your not there, they cant get anywhere.

It requires your password when you do a command involving sudo (or click something on the GUI which needs to invoke root)

You only need to give your password when you go from your very limited user to the root superuser.

---

### Post by kio_http on 2009-11-14
That's like saying "I want viruses in Ubuntu."

---

### Post by lakersforce on 2009-11-14
I am not asking from a security perspective (I already know), I am asking from a user-perspective (from which it makes no sense). Nobody wants to keep supplying their password. Users get the sense that developers do not trust them.

All I am saying is that you should have the option to configure it the way it works in Windows NT kernel build v. 6.0 and up (by "giving" your "password" by the press of a button, instead of having to type it out.)

As stated above, the current model encourages users to use bad passwords, for the sake of simplicity.

---

### Post by mihaiv on 2009-11-14
How exactly does protect you the fact that you are giving password all the time? What are the threats and how does it mitigate them?

---

### Post by Monotoko on 2009-11-14
Thats like saying "to switch accounts, i should not have to give my password"

In Windows, you are already in the admin account, jus have to press the button to do anything...


In linux, you are in a completly differant account, your own account, which has very very limited permissions, so if anything was to ever get in, it would also have very limited permissions and wouldnt be able to do much damage at all.

In order to switch to the root account, you must give the password, surely that makes sense? you are switching to a completly diff account

---

### Post by lakersforce on 2009-11-14
> **mihaiv said:**
> How exactly does protect you the fact that you are giving password all the time?

Could you rephrase that, please.

---

### Post by lakersforce on 2009-11-14
> **Monotoko said:**
> 
In order to switch to the root account, you must give the password, surely that makes sense?

Of course the above should only apply to users who are part of the superuser group, not to just anybody.

> **Monotoko said:**
> Thats like saying "to switch accounts, i should not have to give my password"


If you are part of the superusers, you already have access to other peoples account in Ubuntu by default.

And I am not suggesting this with use of sudo, only gksudo.

---

### Post by mihaiv on 2009-11-14
> **lakersforce said:**
> Could you rephrase that, please.

You are giving the password for every administrative action. How does that protect you more than not giving the password and just being asked whether to allow the administrative action?

---

### Post by lakersforce on 2009-11-14
> **mihaiv said:**
> You are giving the password for every administrative action. How does that protect you more than not giving the password and just being asked whether to allow the administrative action?

Monotoko gave the answer to that:

> **Monotoko said:**
> You login to your own account, which is a very limited account, which means if someone hacks it, or jus uses your machine while your not there, they cant get anywhere.

Now I am far from an expert in Windows, but from my understanding only the user sitting physically in front of the computer is allowed to allow the action, so that migate hacks.

As to the other threat, people sitting in front of your computer while you left it unprotected (e.g by not locking it while leaving): just don't leave your computer open if you are in an environment with people you know you can't trust.

---

### Post by QLee on 2009-11-14
[QUOTE=lakersforceAs] to the other threat, people sitting in front of your computer while you left it unprotected (e.g by not locking it while leaving): just don't leave your computer open if you are in an environment with people you know you can't trust.[/QUOTE]

Well, some people have their system connected to a LAN accessible from more than just their keyboard in front of the unit. Although, you could set up to limit even from a trusted LAN.

Personally, I don't mind at all having to authenticate before doing system tasks, but that's just my feeling.

Actually, you would probably hate my recommendation which adds another step. Run your system as a non-admin user and switch to an admin user to do root tasks, then switch back. There is always the tradeoff between security and ease-of-use. Example: It would be easier to enter your house with groceries if you did not lock the door when you went shopping, but there could be problems with that method.

---

### Post by arashiko28 on 2009-11-14
I remember once I read all of the steps that a virus has to do to activate in windows and linux in a very short way comparison goes like this:

1. windows: just get into internet and disaster comes up...
2. linux: after the virus gets in, has to find a program that executes it, ie. wine, run and affects only the wine files, but to go further and damage the system has to do operations which levels are alike trying to hack inside pentagon's computer, steal gold from fort Knox or cheat a Switzerland's bank to transfer money... 

So... I'll stay with my password, besides, the damage you can cause to your computer it's minimum, you have to be very sure about what you're doing before typing your password.

---

### Post by Shazaam on 2009-11-14
I can go for a very long time without using sudo or su while doing normal linux tasks (even with a limited account). Except when updating or adding/configuring apps.
"Users get the sense that developers do not trust them". I feel quite the opposite. It tells me that someone considers security and stability as being more important than so-called "user friendly".

Have you seen this?...
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by falconindy on 2009-11-14
Y'all got trolled.

---

### Post by QLee on 2009-11-14
[QUOTE=falconindy]Y'all got trolled.[/QUOTE]

It can and does happen frequently here, and frequently Ubuntu users patiently respond to a poster just in case the question was asked by someone who just didn't understand. I, for one, don't mind as long as everyone is respectful and honest.

---

### Post by arnab_das on 2009-11-14
well at least the keyring pasword notifications can be silenced by keeping the keyring password blank. but cant do anything for the terminal sudo commands.

in jaunty one could run it as root, but its not possible in karmic.

---

### Post by lakersforce on 2009-11-14
> **falconindy said:**
> Y'all got trolled.

Gawd, I hate trolls.

All I am saying is, if you are the user of your pc on your own private network, there is no reason you are required to enter passwords all the time. Authentication-by-a-click would suffice.

I think it would be nice to have a easy way to configure it, for example from the installer.

---

### Post by lakersforce on 2009-11-17
> **falconindy said:**
> Y'all got trolled.

Nothing stops a good discussion like a trolling comment like that.

But I admit that the chosen category might not have been the best for this kind of post.

---

### Post by Cheesemill on 2009-11-17
> **lakersforce said:**
> All I am saying is, if you are the user of your pc on your own private network, there is no reason you are required to enter passwords all the time. Authentication-by-a-click would suffice.

I think it would be nice to have a easy way to configure it, for example from the installer.

If you know what you're doing you can alter the behaviour of sudo to not require a password for specific users or commands. I'm not going to tell you how but googling for visudo should get you the answer.

---

### Post by t0p on 2009-11-17
lakersforce: If you don't want to give your password to use sudo, you can quite easily reconfigure your Ubuntu system to allow that.  I won't tell you how to do it - forum rules forbid it - but I *can* tell you, a very simple Google search will very quickly find the info you need.

When I say "easy", I don't mean pointing-a-mouse-in-a-GUI easy.  But it is a very simple act nevertheless.

The Ubuntu security model is there for a good reason.  Just because *you* don't like it, doesn't invalidate it.  But feel free to alter your own computer.  It's yours, as is your Ubuntu installation.  That's one of the great things about Linux: it allows you to screw up your system any way you choose.

---

### Post by Nostoc on 2009-11-17
> **arnab_das said:**
> well at least the keyring pasword notifications can be silenced by keeping the keyring password blank. but cant do anything for the terminal sudo commands.

in jaunty one could run it as root, but its not possible in karmic.

You can use a root terminal by typing *sudo bash* and providing your password.

That's not a good thing to do most of the time though.

---

### Post by Vaphell on 2009-11-17
> **lakersforce said:**
> Gawd, I hate trolls.

All I am saying is, if you are the user of your pc on your own private network, there is no reason you are required to enter passwords all the time. Authentication-by-a-click would suffice.

I think it would be nice to have a easy way to configure it, for example from the installer.

autentication by a click is proven not to work well, because people don't even try to read the confirmation messages and are trained to OK anything that's thrown their way.

Besides you know what would happen if people would be able to give them root or privilege elevation trivial to use at install time? 99% of noobs coming from the windows world would of course grant themselves these powers permanently bacause this is what they know. And there goes the security out the window.

On a forum where responsibility and security are promoted you are asking for a rope to hang yourself and expect people to actually provide you one :-) If you really want to modify your system to be less restrictive you can just use google. After all if you can find the information by yourself and use it in practice to achieve what you want, then probably you know what you are doing and that rope won't squeeze your neck too hard ;-)

---

### Post by lukeiamyourfather on 2009-11-17
> **lakersforce said:**
> Gawd, I hate trolls.

All I am saying is, if you are the user of your pc on your own private network, there is no reason you are required to enter passwords all the time. Authentication-by-a-click would suffice.

I think it would be nice to have a easy way to configure it, for example from the installer.

Unfortunately for you, Ubuntu is developed for everyone else. By everyone else I mean people that use the internet and are around other people. If you don't care about security and don't want to be nagged with a password prompt to protect your system then you might like Windows 95.

Sound like a jerk, don't I? I'm actually a nice guy that likes to help people, but this is a dumb thread that comes up in similar forms all the time. Take a few hours to research why Linux is built the way it is and you'd probably be thanking everyone instead of complaining about typing a password.

Aside from the security the password prompt also reminds new users that what they are doing could potentially damage the system. I can assure you this has saved me many times. This is by no means a comprehensive guide but its a good starting place to understand behind the scenes.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you really want to have Linux do whatever you ask then you can enable the root account and use that all the time instead of a standard user account, though this is not recommended at all and if you do a little research I think you'll agree. Cheers!

---

### Post by SunnyRabbiera on 2009-11-17
Well the OP forgets the main reason why windows still has security issues is because of the lack of passwords for installing apps, instead Vista/7 uses the UAC but its still not foolproof.
I think passwords are a necessary evil.

---

### Post by lakersforce on 2009-11-17
Thanks for all your comments! Here are some feedback:

> **SunnyRabbiera said:**
> Well the OP forgets the main reason why windows still has security issues is because of the lack of passwords for installing apps

Not at all. And of course a weak design (and widely used system) is arguable more open for attacks. But in the end it comes down to the users.

> **lukeiamyourfather said:**
> 
If you really want to have Linux do whatever you ask then you can enable the root account and use that all the time instead of a standard user account, though this is not recommended at all and if you do a little research I think you'll agree. Cheers!

I *do* agree on that. And I would never use my distro that way. God forbid I would ever make a mistake, but if I did I would be screwed not having the added security of authentication.

> **Vaphell said:**
> autentication by a click is proven not to work well, because people don't even try to read the confirmation messages and are trained to OK anything that's thrown their way.


It does not have to be an 'ok' button. It could for example be a big exclamation marks on red background.

> **Vaphell said:**
> 99% of noobs coming from the windows world would of course grant themselves these powers permanently bacause this is what they know.

I am not talking about permanently enabling/disabling anything. My idea is to make the ad hoc authentication "keyboard-less".

> **t0p said:**
> If you don't want to give your password to use sudo, you can quite easily reconfigure your Ubuntu system to allow that.

I do not want not to give a authentication, or to be logged on to sudo longer, I would like the authentication process to be some what simplified. But I want it to be there!

---

### Post by doas777 on 2009-11-17
would you click ok to this message?
[IMG]http://media.arstechnica.com/news.media/malware_warning.png[/IMG]

in recent studies (small ones, no doubt), more than 50% of people would, particularly if the warning was preceded by one or more other warnings.
[http://arstechnica.com/security/news/2008/09/study-confirms-users-are-idiots.ars](http://arstechnica.com/security/news/2008/09/study-confirms-users-are-idiots.ars)

this is why.

I would also add, that at work we have reconfigured uac to prompt for username and password, since process isolation killed lots of runas functionality in vista (appears to be fixed in win7). as a result, to organize folders in the Allusers\startmenu folder, I have to confirm (by uname/passwd) for creating a folder, renaming one, moving files into it (once to paste, another to delete). now That, is an annoyance.

---

### Post by lakersforce on 2009-11-17
Before anyone says "lakersforce just fundamentally does not understand the unix-like security model" (again), let me be (almost) perfectly clear: it (might/might not) be a trade-off! Better usability for a little bit of security!

Users are idiots(!), but they do not appreciate being treated like one!

I am not a hacker (yet), but sure there must be some way to deny this kind of authentication if it comes from a network connection and only allow it if the computer can confirm it comes from local I/O devices (not sure about the local I/O devices, but the network part sounds feasible.) That way you would still have todays security model when accessing the computer remotely.

In the grand scheme of things nothing would be lost, but some would be gained!

---

### Post by Barrucadu on 2009-11-17
What privileged thing are you doing so frequently that entering your password is a significant irritation?

---

### Post by slumbergod on 2009-11-17
if I was a moderator I'd just remove silly troll threads. Then I'd ban the user who did it. Then I'd go to their house and smash their computer.

---

### Post by JBAlaska on 2009-11-17
If you don't like sudo'ing...just turn it off. If you don't know how to do that in Karmic..I suggest you DO need sudo

---

### Post by Philip Gray on 2009-11-17
Hi I agree that having passwords is good for security. I also agree that having to continuously enter yr password is also a huge nuisance. I am the only one that uses my pc at home so it becomes extremely frustrating. I am setup with admin rights. I have also changed the admin settings to allow me to login as root. I find that this is more acceptable to me than continuously having to use sudo. However when I am connected to the internet I always use my own account and not the root account for the security reasons mentioned in this post

---

### Post by lakersforce on 2009-11-17
> **Barrucadu said:**
> What privileged thing are you doing so frequently that entering your password is a significant irritation?

It is just a general thing. But for example accessing Synaptic. Or accessing my partitions. Some of those thing I could customize, but that would require me to enter my password...

> **slumbergod said:**
> if I was a moderator I'd just remove silly troll threads. Then I'd ban the user who did it. Then I'd go to their house and smash their computer.

And I suggest users stop posting irrelevant comments in random threads. /note-to-self: I got to change my picture!

> **JBAlaska said:**
> If you don't like sudo'ing...just turn it off. If you don't know how to do that in Karmic..I suggest you DO need sudo

Please read the entire thread (or at least all my comments) before posting.

---

### Post by JBAlaska on 2009-11-17
> **"lakersforce"]Please read the entire thread (or at least all my comments) before posting. [/quote]
I did **unfortunately**

[QUOTE=lakersforce said:**
> /*DISCLAIMER*/ If you are looking for a flamewar please go somewhere else! /*DISCLAIMER*/

Even after you have positively identified yourself at login you still have to keep providing the password every time you do something that affects your system.

Since I have already provided it once, it is really a bad idea. It encourages bad passwords like "1". **In this regard it should work like Windows Vista or 7**. I mean, in the end the system is not safer than the user anyway. So why all the hassle?

 You mean when you try to do something it should ask: Do you want to do that?..do you really want to do that...no seriously..do you really want to do that..ok then.. lol's

---

### Post by lakersforce on 2009-11-17
I am not praising Windows (although I assume some posters think I am, thus all the "You're a troll!" comments). And I am by no way saying that GNU/Linux security should be like Windows.

What I am saying is: superusers on private networks should not provide passwords by keyboard when doing administratively tasks. The input of the password should be eased, because the current model encourages bad passwords.

@JBalaska: Please stop injecting your own thoughts into my words. Go back to the start and actually read the thread this time.

---

### Post by JBAlaska on 2009-11-17
@lakersforce, Please stop injecting your words into my thoughts..

So your trying to say that sudo is a bad idea because it "encourages bad passwords"?

and your proposed fix is: "In this regard it should work like Windows Vista or 7"

In that case, please see my remark above.

---

### Post by kk0sse54 on 2009-11-17
> **lakersforce said:**
> /*DISCLAIMER*/ If you are looking for a flamewar please go somewhere else! If you are a non-critical Ubuntu-fanboy or Microsoft-loather, not open for suggestions, I suggest you stop reading here, before you get carried away./*DISCLAIMER*/

Even after you have positively identified yourself at login you still have to keep providing the password every time you do something that affects your system.
Nobody is stopping you from running as root

> Since I have already provided it once, it is really a bad idea. It encourages bad passwords like "1". In this regard it should work like Windows Vista or 7. I mean, in the end the system is not safer than the user anyway.

Not really, a password is a password and it's only as strong as the user wishes it to be. Please stop  making the assumption that sudo encourages bad password since there's no evidence and you haven't offered any supporting arguments.

---

### Post by The Funkbomb on 2009-11-17
I sorta like it.

---

### Post by doas777 on 2009-11-17
> **The Funkbomb said:**
> I sorta like it.
agreed. much more elegant than uac.

---

### Post by alphaniner on 2009-11-17
I'm somewhat inclined to agree with the OP.  At work I have NOPASSWD enabled in my sudoers file, and the only reason I don't do the same at home is network security.  For me, the notion of escalation protecting me from myself is just silly.

On the other hand, I think not running X as root makes a whole lot of sense.  Actually, it would be more appropriate to say that running X as root makes no sense.

---

### Post by zagz on 2009-11-17
IMO asking for the password to critical system actions is a respectable way of going about things. :D

Microsoft Vista/Seven UAC way is to treat the user as if they have dementia, it just seems a dreadfully mind numbing process.

---

### Post by lakersforce on 2009-11-17
> **C!oud said:**
> 
Please stop  making the assumption that sudo encourages bad password since there's no evidence and you haven't offered any supporting arguments.
> **JBAlaska said:**
> 
So your trying to say that sudo is a bad idea because it "encourages bad passwords"?

Wrong. It is the way the security model is implemented on the desktop that encourages bad passwords.

I am not a fancy science guy, but when I ask my friends and colleges why they do not use GNU/Linux, one of the top responses (besides the usual responses like "Can't live witout Word", "I game" and "What's linux??") is "too many passwords!!!" I have no evidence of this claim, but it is one of the things I hear when talking to people. That counts for something in my mind!

> **C!oud said:**
> Nobody is stopping you from running as root

But I do not want to run from root. Who wants to run from root except newbies? I already said this earlier in the thread, quoting myself:

> **lakersforce said:**
> 
I do not want not to give a authentication, or to be logged on to sudo longer, I would like the authentication process to be some what simplified. But I want it to be there!

> **JBAlaska said:**
> 
and your proposed fix is: "In this regard it should work like Windows Vista or 7"

Not at all. Just for you, I will again quote myself:

> **lakersforce said:**
> ...there must be some way to deny this kind of authentication if it comes from a network connection...That way you would still have todays security model when accessing the computer remotely.


...just a thought.

---

### Post by The Funkbomb on 2009-11-17
The main thing I like about asking for a password is it makes you think before you do things.

Take a look at Vista's UAC.  It's actually a great idea.  The implementation fails hard.  Clicking a button does not make a user think.  Most people I know don't even read popups they click it.  They don't read EULAs or anything.  They're just looking for the next place to click.

By having to enter a password, it keeps you in the game.

---

### Post by lakersforce on 2009-11-17
I agree upon that. And how that could be solved is open for discussion, one solution being a button that does not entice users to click it.

---

### Post by The Funkbomb on 2009-11-17
> **lakersforce said:**
> I agree upon that. And how that could be solved is open for discussion, one solution being a button that does not entice users to click it.

Uhh...  Such as?

Entering your password is the most convenient way.  It works in CLI.  It works in the GUI.  Choose a password that is easily typed by you but cryptic enough that it can't be guessed.

---

### Post by alphaniner on 2009-11-17
> **The Funkbomb said:**
> By having to enter a password, it keeps you in the game.

For people who don't need to elevate often, I guess it makes sense.  But I really can't relate to this.  If one understands what is and what isn't 'administrative' it is 100% unnecessary; and even entering a pw can become reflexive.

---

### Post by The Funkbomb on 2009-11-17
> **alphaniner said:**
> For people who don't need to elevate often, I guess it makes sense.  But I really can't relate to this.  If one understands what is and what isn't 'administrative' it is 100% unnecessary; and even entering a pw can become reflexive.

I think the password is a great middle ground.  If one understands what is and what isn't administrative, then disable it.

It should be there by default for new users.  Experienced users should have an understanding of why it's there and how to disable it.  Can you imagine what the Absolute Beginners Forum would be like without it?  It would be 15 pages of people complaining about messing up their systems with terrible command lines and having their security compromised.

Yes, typing my password is reflexive now too but it's not as reflexive as clicking a button.  What do you suggest then?  Perhaps Ubuntu should use a captcha system?

Take the Firefox add-on NoScript for example.  I installed it on both of my parents computers because they're constantly getting infected.  I dial in to the windows PC and I'm doing updates and running malwarebytes.  A ton of malware is popping up.  I expected some but not this much.  I go into Firefox and I look at the no-script symbol.  It's a plain S.  No big deal, it's on google.com.  I right click and "Allow Scripts Globally (Dangerous)" is enabled...  I was like, "What the heck?  Who enabled this?"  My mom said, "Well, I got tired of enabling it on every site I go to so I just set it to allow globally and it works great!"  Users often times don't know what they're doing but they do it anyway.

---

### Post by Tipped OuT on 2009-11-17
> **JBAlaska said:**
> 
You mean when you try to do something it should ask: Do you want to do that?..do you really want to do that...no seriously..do you really want to do that..ok then.. lol's

Way to be bias. Windows Vista/7 doesn't prompt for a confirmation like that. It prompts once, and you're done.

You can easily disable it too.

---

### Post by alphaniner on 2009-11-17
> **The Funkbomb said:**
> Yes, typing my password is reflexive now too but it's not as reflexive as clicking a button.  What do you suggest then?  Perhaps Ubuntu should use a captcha system?

Like I said, I can't relate to the need so I'm not in a position to make suggestions.  Nor do I mean to be judgmental: I'd probably be better off with 'protection from myself' in some aspects of life, but my use of root power is not one of them.  So I disable the system when it's doing only that, and I tolerate otherwise.

---

### Post by The Funkbomb on 2009-11-17
> **alphaniner said:**
> Like I said, I can't relate to the need so I'm not in a position to make suggestions.  Nor do I mean to be judgmental: I'd probably be better off with 'protection from myself' in some aspects of life, but my use of root power is not one of them.  So I disable the system when it's doing only that, and I tolerate otherwise.

I know quite a few people who spend a lot of time rooted.  These guys are pretty good at computers.  I wouldn't say I'm bad with computers but I'm nowhere near these guys.  

To each his own.  Think of it this way.  Would you toss the keys to a Ferrari to a 16 year old who just got his license?  I know I wouldn't.  They just haven't developed the skill to keep it on the road.

---

### Post by alphaniner on 2009-11-17
> **The Funkbomb said:**
> To each his own.  Think of it this way.  Would you toss the keys to a Ferrari to a 16 year old who just got his license?  I know I wouldn't.  They just haven't developed the skill to keep it on the road.

That's the thing.  If someone had given me the keys to a Ferrari when I was 16, if anything I would have driven more carefully than I did.  For a good while at least.

Yes, I'm that boring.

---

### Post by The Funkbomb on 2009-11-17
> **alphaniner said:**
> That's the thing.  If someone had given me the keys to a Ferrari when I was 16, if anything I would have driven more carefully than I did.  For a good while at least.

Yes, I'm that boring.

lol, not me.  Pedal, meet metal.  VROOOM!

Fortunately, I've grown up since then and I only muck with things that aren't likely to get me killed.

---

### Post by dyslexia on 2009-11-17
Oh boy, how the incestuous world of computers gets messed up.

The irritating "everything requires confirmation" "feature" of vista (I don't know if it was "fixed" in windows 7) was a classic case of the 

"Bill Gates / Microsoft DISPROOF of an idea"  (take an idea and implement it really badly, then say "look, it doesn't work!")

 This idea works really, really (really) well in Mac OSX and Linux.

if you don't like it, you just have to log in as root on the login screen!

What is happening here is that you are transferring your irritation with Windows to another Operating system, which PROVES another idea:

It is NOT always a good idea to copy Microsoft!

---

### Post by alphaniner on 2009-11-17
> **dyslexia said:**
> if you don't like it, you just have to log in as root on the login screen!

Thankfully, it's even better than that.  You can put a line in the sudoers file to disable most prompts, avoiding the [99.99999999999% of the time unnecessary] act of logging into the X-server as root.

---

### Post by mamamia88 on 2009-11-17
can someone please explain this root password thing?  i know it is meant to protect me but it just seems unnecessary for certain tasks like installing packages from sources i trust like synaptic.  how does entering a password keep you safe?

---

### Post by alphaniner on 2009-11-17
> installing packages from sources i trust like synaptic.

Installing packages requires you to write to root owned directories.  **sudo** is an indiscriminate tool by default; it is required for *anything* that root would need to do, regardless of how trivial the action may be.  AFAIK you can turn it off for individual programs if you choose.

---

### Post by dyslexia on 2009-11-18
On a perfectly configured system ( which is extremely rare in the linux world, unfortunately) you would almost never, ever need to do any of the system-oriented tasks which would require authorization.... you are free to concentrate on CAD or Music or whatever it is that you actually DO with the system.

So it doesn't protect you at all - it protects the system, which shouldn't really needs endless configuration, because it is very easy to mess up that perfectly configured system, if users are constantly issuing priviledged commands....

and saving that perfectly configured system helps you,  because (in theory) you have real, possibly important things you need to do so the system is always there, in that usable state, never crashes, never has to be rebooted... etc.

I was somewhat frustrated, like the OP .. I wanted some filesystems mounted by default read only, and putting them in fstab messed up suspend... so I have to enter the passwords each time.

Not the biggest issue.

---

### Post by alphaniner on 2009-11-18
> **dyslexia said:**
> On a perfectly configured system ( which is extremely rare in the linux world, unfortunately) you would almost never, ever need to do any of the system-oriented tasks which would require authorization...

Unless the very purpose of your system is to test devices which require authorization to interact with...

But this situation is just another example of the awesomeness that is **sudo**, because even this is practical without the need to enable root!

---

### Post by Barrucadu on 2009-11-19
> **lakersforce said:**
> What I am saying is: superusers on private networks should not provide passwords by keyboard when doing administratively tasks.

You see, there's your problem. You're not a superuser, root is.

---

### Post by Mornedhel on 2009-11-19
Although I'm all for sudo'ing etc., if it disturbs the OP that much, let it be known that Fedora 12 allows unprivileged users to install signed packages by defaults, and that I recommend {s,}he switch to it.

(This policy has apparently been implemented a bit under the radar and a lot of people -- sysadmins, devs and users alike -- are not happy with it at all.)

---

### Post by slakkie on 2009-11-19
> **lakersforce said:**
> 
Even after you have positively identified yourself at login you still have to keep providing the password every time you do something that affects your system.


If I login and leave my box open and someone can do stuff as root without having to identify himself... No, I shouldn't even bother.

Go ahead, sudo passwd root, enter a new password, login as root and do whatever you want. Enjoy.

---

### Post by hoppipolla on 2009-11-19
To me, just, to me... it makes perfect sense. I am elevating my rights to admin, because I want to do admin-y things. Its how I know my system is secure, because a virus, basically, doesnt know my password :)

Im glad its like this, but I suppose I do understand why people can find it irritating... but there's nothing to change it TO... fingerprint authentication? o.O lol

If we got rid of it or made it more like windows, we would save ourselves that couple of seconds inputing a password every time, but the security hit would be pretty high. Im not sure if the Ubuntu team have any plans to change anything.

---

### Post by hoppipolla on 2009-11-19
> **slakkie said:**
> Go ahead, sudo passwd root, enter a new password, login as root and do whatever you want. Enjoy.

It doesnt work like that, they need to have your current password to get the sudo permissions to run "passwd root". Geddit? :)

---

### Post by Mornedhel on 2009-11-19
> **hoppipolla said:**
> Im glad its like this, but I suppose I do understand why people can find it irritating... but there's nothing to change it TO... fingerprint authentication? o.O lol

Actually, fingerprint authentication is supported on my Dell. At sudo/gksudo prompts, you can swipe your finger on the reader or enter your password. The packages for this are all on the repositories last time I checked, although I was still using Gutsy or Hardy at the time.

---

### Post by slakkie on 2009-11-19
> **hoppipolla said:**
> It doesnt work like that, they need to have your current password to get the sudo permissions to run "passwd root". Geddit? :)

Darn, you are right. But sudo visudo and setting the NOPASSWD directive is also not possible then.. DAMMIT!

---

### Post by Keyper7 on 2009-11-19
My opinion: if someone is not a system admin and is doing root tasks frequently enough to be annoyed by the password prompt, something is fundamentally wrong in the way this person uses the computer. I do a massive amount of root tasks when I'm polishing my machine after a clean install, but after that stage is over I can count on my fingers the number of times I need sudo per week.

Honestly, in my opinion, the same goes for UAC. I don't really understand the reason of so much backlash against it. I use UAC in Vista pretty much like I use gksudo in Ubuntu (e.g. rarely, mainly for system updates).

---

### Post by RabbitWho on 2009-11-20
> **kio_http said:**
> That's like saying "I want viruses in Ubuntu."

This. 

I don't see how it could be annoying. maybe his password is 12 random digits that he can't remember.

---

