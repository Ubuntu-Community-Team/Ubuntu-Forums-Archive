---
title: "Feedback on entering password in the terminal?"
date: 2006-07-12
forum: Recurring Discussions
---

### Post by aysiu on 2006-07-12
Many times I've heard users complain that Ubuntu isn't accepting their password in the terminal. This is because Ubuntu's terminal doesn't give any visual feedback.

Is that a terminal thing fundamental to Linux/Unix/etc.? Or is that something that could be changed in Ubuntu?

It can't be a policy thing, right, seeing as you do get black dots for the passwords you type in the graphical user interface?

Any thoughts? Should I file a bug report on this?

**Edit (12 July, 2006)**: I've added two images to show the difference. The terminal shows you nothing when you type your password. The GUI shows you black dots or asterisks.

[Here's an example of a confused user](http://www.ubuntuforums.org/showthread.php?t=217876)

**Edit (14 April, 2007)**:
And some more examples of confused users:
[http://ubuntuforums.org/showthread.php?t=569316](http://ubuntuforums.org/showthread.php?t=569316)
[http://ubuntuforums.org/showthread.php?t=408924](http://ubuntuforums.org/showthread.php?t=408924)
[http://ubuntuforums.org/showthread.php?t=405602](http://ubuntuforums.org/showthread.php?t=405602)
[http://ubuntuforums.org/showthread.php?t=404770](http://ubuntuforums.org/showthread.php?t=404770)
[http://ubuntuforums.org/showthread.php?t=402968](http://ubuntuforums.org/showthread.php?t=402968)
[http://ubuntuforums.org/showthread.php?t=396549](http://ubuntuforums.org/showthread.php?t=396549)
[http://ubuntuforums.org/showthread.php?t=362619](http://ubuntuforums.org/showthread.php?t=362619)
[http://ubuntuforums.org/showthread.php?t=333799](http://ubuntuforums.org/showthread.php?t=333799)
[http://ubuntuforums.org/showthread.php?t=146781](http://ubuntuforums.org/showthread.php?t=146781)
[http://ubuntuforums.org/showthread.php?t=96768](http://ubuntuforums.org/showthread.php?t=96768)
[http://ubuntuforums.org/showthread.php?t=410219](http://ubuntuforums.org/showthread.php?t=410219)

It is a *real* problem, folks. I know the developers have already rejected my wishlist item to change this, but please don't imagine it's not still a real problem.

One thing I did do to help alleviate the problem is create a page for it on Psychocats explaining with screenshots the difference between password in the GUI and password in the terminal:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

**Edit**: Now there's a Brainstorm idea about this: [Idea #11118: Display *** for password in the terminal](http://brainstorm.ubuntu.com/idea/11118/)

Unfortunately, even if it gets voted up, it'll still be rejected by the developers.

---

### Post by BuffaloX on 2006-07-12
It's not a big issue to me, but it has happened, that my password was not accepted. Which is of course 100% my own fault, for failing to activate the window, or mistyping. :rolleyes:

---

### Post by aysiu on 2006-07-12
Just to be clear on what the issue is--it's not the terminal not accepting your password.

It's the perception of some new users--based on the fact that there's no visual feedback--that the terminal isn't accepting the password.

For example, look at [this thread](http://www.ubuntuforums.org/showthread.php?t=214372).

---

### Post by Brunellus on 2006-07-12
there should be asterisks for newbies, I guess.  It never bugged me, but it freaks the newbies out.

---

### Post by jayemef on 2006-07-12
I vote on no feedback on anything.

The way I see it, not displaying any feedback prevents others from looking over your shoulder or what-have-you and seeing how long of a password you have. Yes, that information doesn't necessarily help them in determining what your password is, but why provide that information if you don't have to?


Useful tip: Ctrl+U clears any characters you typed at a password prompt. So if you know you made a mistake, but you don't know how many characters to erase, you can use Ctrl+U to clear the whole thing and start again.

---

### Post by aysiu on 2006-07-12
I don't know if I agree with you there, jayemef. Anyone looking over my shoulder would be able to see what keys I'm typing--far more useful to the password-stealer than looking at asterisks.

Thanks for the tip about Control-U, though!

---

### Post by bruce89 on 2006-07-12
It did worry me the first time I saw the no feedback thing, but I am used to it now.  Indeed passwords aren't safe if somebody is looking over your back, feedback(!) or not.  

There must be a reason for there not being any feedback.

---

### Post by aysiu on 2006-07-12
The only thing I can think of is it possibly being defined by the Linux kernel and not necessarily something Ubuntu-related. As I said before, it can't be policy; otherwise, they wouldn't include asterisks in the *gksudo* and *kdesu* GUI dialogues...

---

### Post by bruce89 on 2006-07-12
> **aysiu said:**
> The only thing I can think of is it possibly being defined by the Linux kernel and not necessarily something Ubuntu-related. As I said before, it can't be policy; otherwise, they wouldn't include asterisks in the *gksudo* and *kdesu* GUI dialogues...

Does anyone know why they use bullet points for passwords instead of *'s?

---

### Post by BuffaloX on 2006-07-12
Actually if things should be in line with the Ubuntu policy.
That is Linux for humans, Linux should be easy(er)
there should be some sort of feedback.
If it helps some people.

I guess beginners are humans too.
I hope so, because I'm a beginner at Linux. :p

---

### Post by kabus on 2006-07-12
> **aysiu said:**
> Many times I've heard users complain that Ubuntu isn't accepting their password in the terminal. This is because Ubuntu's terminal doesn't give any visual feedback.

Is that a terminal thing fundamental to Linux/Unix/etc.? Or is that something that could be changed in Ubuntu?

It can't be a policy thing, right, seeing as you do get black dots for the passwords you type in the graphical user interface?

Any thoughts? Should I file a bug report on this?


Not giving visual feedback when entering a password is just the traditional Unix style. I don't think there's an easy configuration option to change that behaviour, but I'd be very surprised if it couldn't be changed in the source. I guess all you have to do is convince the devs this is worth the trouble.

---

### Post by aysiu on 2006-07-12
So far, 9 are in favor, 1 against, and 1 indifferent. I'll give it a couple of days. If it continues this way, I'll file a bug report or tack on to an existing one if it already exists.

---

### Post by Polygon on 2006-07-12
the first time i tried to enter my pass in the termina, i too was like "where the hell is my password? its not letting me enter it" until my linux using friend told me it doesnt show up in the terminal. after that ive had no problem with it.

its just an extra layer of security, i just say leave it the way it is.

---

### Post by Kvark on 2006-07-12
> **aysiu said:**
> The only thing I can think of is it possibly being defined by the Linux kernel and not necessarily something Ubuntu-related. As I said before, it can't be policy; otherwise, they wouldn't include asterisks in the *gksudo* and *kdesu* GUI dialogues...
I doubt the Linux kernel has anything to do with what the executable /usr/bin/sudo prints in the bash terminal. I'm pretty sure the sudo program turns off the bash terminal's automatic echoing of pressed keys before asking for a line of input. To display dots instead of the normal echoed text that sudo turned off you'd need to reprogram sudo to fetch the password one character at a time instead of waiting for the whole line and add a command that prints a dot each time it gets a character.

IMO this is an Ubuntu bug since it adds inconsistency to Ubuntu as a whole by behaving differently from other programs (gksudo & kdesu) in Ubuntu.

---

### Post by PhilipsHead on 2006-07-12
There are probably thousands of things to complain about, THIS is not one of them.

---

### Post by aysiu on 2006-07-12
> **PhilipsHead said:**
> There are probably thousands of things to complain about, THIS is not one of them.
Why not?

---

### Post by PhilipsHead on 2006-07-12
> **aysiu said:**
> Why not?

Do you have vision? watch the cursor blink as you type.

Besides, if you don't like it, use CSH and set the options, it's not THAT hard now is it?

---

### Post by aysiu on 2006-07-12
> **PhilipsHead said:**
> Do you have vision? watch the cursor blink as you type.

Besides, if you don't like it, use CSH and set the options, it's not THAT hard now is it?
It's not for me. It's for new users.

Creating a consistent interface that doesn't confuse new users is a worthy goal. Why make something confusing? It has nothing to do with easy or difficult.

---

### Post by PhilipsHead on 2006-07-12
It's probably possible to do it in BASH too, but i don't really care because i don't use it.

In all probability it's in your .bashrc  or the global bashrc...

---

### Post by prizrak on 2006-07-12
> **aysiu said:**
> The only thing I can think of is it possibly being defined by the Linux kernel and not necessarily something Ubuntu-related. As I said before, it can't be policy; otherwise, they wouldn't include asterisks in the *gksudo* and *kdesu* GUI dialogues...
Actualy GUI is very different. Back when I used VB there was an option for the text box called "Password" if you turned it to true it would give you the asterisks for anything entered. I think when I used RedHat there was an option to turn echo for passwords on in the terminal. 

I never had a problem with it until something screwed up in my desktop and one of the keys on the kbd didn't work (it worked after a reinstall). I didn't know that the key wasn't working and the password kept not being accepted because I didn't know I had one character less. As far as security goes as been said it's easy enough to see a kbd if you are standing behind someone. 

The whole password system is flawed anyways, since SD cards are pretty cheap and just about any new laptop will have an SD slot it makes more sense to create keys that are coded onto a card and use that for authentication. I'm actually using that system for my password manager :)

---

### Post by aysiu on 2006-07-12
> **PhilipsHead said:**
> It's probably possible to do it in BASH too, but i don't really care because i don't use it.

In all probability it's in your .bashrc  or the global bashrc...
I'm talking about default settings.

Anyone who has the wherewithal to edit the .bashrc or global bashrc to change the behavior probably already knows that the password is being accepted despite the lack of visual feedback (based on the posts of read from new users, apparently a blinking cursor isn't enough for them--even though they can see).

---

### Post by PhilipsHead on 2006-07-12
> **aysiu said:**
> It's not for me. It's for new users.

And new users are more stupid than us? Way to belittle new users. jk ;)

> Creating a consistent interface that doesn't confuse new users is a worthy goal. Why make something confusing? It has nothing to do with easy or difficult.

A consistent interface... LMAO, gnome? You have to be kidding!

KDE is a consistent WM, gnome is at best an inconsistent non optional print it out as standard text right now pos.

I didn't belittle anyone with my aforementioned statemet, it's just that you feel that way.

Linux isn't hard at all, in fact windows is a lot harder, unless you are using gnome, then both of them are an endless search for not finding what you want.

---

### Post by PhilipsHead on 2006-07-12
> **aysiu said:**
> I'm talking about default settings.

Anyone who has the wherewithal to edit the .bashrc or global bashrc to change the behavior probably already knows that the password is being accepted despite the lack of visual feedback (based on the posts of read from new users, apparently a blinking cursor isn't enough for them--even though they can see).

Look, i was set in front of a Xenix system 15 years ago, "solve this" and i'm pretty stupid, i figured it out.

If you are going by beginners problems this is the last place to start, just let them know that there is no visual feedback but the cursor blinking.

I don't really get the problem.

---

### Post by Christmas on 2006-07-12
> **BuffaloX said:**
> It's not a big issue to me, but it has happened, that my password was not accepted. Which is of course 100% my own fault, for failing to activate the window, or mistyping. :rolleyes:
A little offtopic but very funny. I typed my password once, and the response "Incorrect password; please type again". So I type it twice, this time more careful. The same response. I say what the hell? And give it another try, looking at the keyboard this time. The same response. I was on the way of thinking my password was cracked 'till I realised... that my Caps Lock key was pressed. ](*,)

LE: Forgot to say, I chose the 4th option "There shouldn't be. But it's okay to be inconsistent--no terminal feedback, yes GUI feedback." I think it is OK the way it is now.

---

### Post by PhilipsHead on 2006-07-12
> **Christmas said:**
> A little offtopic but very funny. I typed my password once, and the response "Incorrect password; please type again". So I type it twice, this time more careful. The same response. I say what the hell? And give it another try, looking at the keyboard this time. The same response. I was on the way of thinking my password was cracked 'till I realised... that my Caps Lock key was pressed. ](*,)

LE: Forgot to say, I chose the 4th option "There shouldn't be. But it's okay to be inconsistent--no terminal feedback, yes GUI feedback." I think it is OK the way it is now.


LMAO, it should state "capitalization matters" or something...

Thanks for giving an overtired old man a laugh. :)

---

### Post by Christmas on 2006-07-12
> **aysiu said:**
> 
It's the perception of some new users--based on the fact that there's no visual feedback--that the terminal isn't accepting the password.

I know I had the exact same problem. When I was prompted for the password and I began to type it, nothing appeared on the screen as I was used and it gave me the impression that the terminal had froze. It is just a basic thing that everyone learns first time using Linux. I think it is good the way it is, because the stars indicating the number of characters are a security risk (for example if someone looks over your shoulder while at work). Maybe just for a character typed, 2 or 3 stars, but this can be interpreted almost as easy as the first one.

As for GUI, it's fancy with the dots. In KDE wasn't there an option to make the GUI pass prompt act like the Konsole one?

---

### Post by aysiu on 2006-07-12
This may bear repeating, but someone who's looking over your shoulder isn't going to be counting how many dots or asterisks appear when you type your password.

If she wants to steal your password, she's far more likely to be looking at your fingers to see what keys you're pressing!

---

### Post by Christmas on 2006-07-12
Maybe, if you're a slow typist. But if you are a fast one, typing with both hands using the blind-typing method, then your hands cover the keyboard and the fingers move too fast to be followed. I think, I'm not sure, I never watched somebody else typing its password and mine was never stolen. Anyway if this is correctly, than counting the asterisks would be more relevant.

However this doesn't explain your good observation made a couple of posts above, when you said that GUI prompts are not protected with the same method. It really doesn't make sense to be one way in the shell and the other way in GUI. Or wait, maybe the input method from the shell is intended to be used only on servers, where (probably) there's a need for higher security than a desktop PC.

---

### Post by aysiu on 2006-07-12
Yes, the second point is more relevant, Christmas. I didn't mean to keep harping about the security issue. If you never get feedback, you should never get it. If you get feedback, you should always get it.

That's probably what confuses new users the most. When they type their passwords into the password dialogue for Synaptic or Adept, they can see the asterisks or black circles. That's then what they expect for the terminal, too.

P.S. I've seen some really fast typists (I'm not that slow myself), and I can usually see what they're typing. I've never stolen any passwords, but I probably could if I wanted to.

---

### Post by PhilipsHead on 2006-07-12
> **aysiu said:**
> This may bear repeating, but someone who's looking over your shoulder isn't going to be counting how many dots or asterisks appear when you type your password.

If she wants to steal your password, she's far more likely to be looking at your fingers to see what keys you're pressing!

If Ubuntu had a firewall, then all of these threats would have to be local.

NO1 flaw is not any default firewall.

---

### Post by richbarna on 2006-07-12
I just type the password and press enter, if I make a mistake I do it again. Seems easy to me. Are the new users so lacking in common sense that after the first attempt and not seeing dots for the password they won't try "enter" ?

I am all for helping the new users but in my opinion this is going a bit far. Give them some credit, let them learn something for a change.
What happened to good old "trial and error"?

It would be better if every time they booted Ubuntu, a little message popped up that said "Did you try anything for yourself today?" "Did you READ anything today?" or did you go directly to the beginners section on ubuntuforums and ask where the password asterisks were?

Just my 2 centimos, and no offense to aysiu once again trying to help the new users.

You have got "in my opinion" the best partition and install guide on the net. Now go and look at the "beginners section" and see how many partitioning and installation questions there are.

New users don't need asterisks, they need to stop whinging and do some reading for a change.

---

### Post by aysiu on 2006-07-12
> **richbarna said:**
> Are the new users so lacking in common sense that after the first attempt and not seeing dots for the password they won't try "enter" ? Apparently some are, because I've seen that question more than once on these forums (seems to appear at least once a month) and goes something like > I tried to type my password in the terminal, but Ubuntu won't recognize it.

Then I or another forum member usually responds, > Did it say "Sorry, wrong password"? [quote=new user]No, it doesn't say anything[/quote] [quote=volunteer]It's okay. Just type your password and press Enter. It's taking your password, it's just not giving you any visual feedback[/quote] Having to explain this is annoying, and it's really the lack of consistency that's bothering me. If the asterisks are there, they should be everywhere. If we don't need asterisks, don't put them in the GUI, either. Just my opinion.

---

### Post by PhilipsHead on 2006-07-12
> **aysiu said:**
> Apparently some are, because I've seen that question more than once on these forums (seems to appear at least once a month) and goes something like 

Then I or another forum member usually responds,    Having to explain this is annoying, and it's really the lack of consistency that's bothering me. If the asterisks are there, they should be everywhere. If we don't need asterisks, don't put them in the GUI, either. Just my opinion.


Ok, this is how it is, Linux is based on Unix, you know that and i am fully aware that you know that.

And you know what, there are about 10 000 other compatible distros out there that also use the Unix way, beyond that there are a few BSD's that also use it.

You are asking to change something for less than 1/100'th of the users and just because they can't get used to an age old standard?

Weeeelllll, how about no?

Serioualy we don't care about newbies, no one does, they will lern the ropes or go back to windows, nobody else cares, why do you?

---

### Post by manicka on 2006-07-12
> **PhilipsHead said:**
> 

Serioualy we don't care about newbies, no one does, they will lern the ropes or go back to windows, nobody else cares, why do you?

Please refrain from comments like this. This forum exists to **help** users of all levels of ability.

---

### Post by prizrak on 2006-07-12
> **PhilipsHead said:**
> Ok, this is how it is, Linux is based on Unix, you know that and i am fully aware that you know that.

And you know what, there are about 10 000 other compatible distros out there that also use the Unix way, beyond that there are a few BSD's that also use it.

You are asking to change something for less than 1/100'th of the users and just because they can't get used to an age old standard?

Weeeelllll, how about no?

Serioualy we don't care about newbies, no one does, they will lern the ropes or go back to windows, nobody else cares, why do you?
I think you are missing the point, whether it is friendly to newbies or not it's simply inconsistent. GUI == feedback, CLI == no feedback, also there is very little reason for the terminal to not have the dots/asterisks. It was done in Unix years upon years ago for a reason and the reason was password stealing because there wasn't much in the way of internet threats back in the day, so physical pwd stealing was a concern. It's something that has stuck beyond it's useful life like the QWERTY keyboard that was originally designed to slow typists down so that typewriters don't get jammed. I've mentioned before how a key on my kbd was not working and I had no idea that I wasn't typing the entire password since I couldn't count the asterisks to make sure I got the whole thing in.

---

### Post by richbarna on 2006-07-12
> **PhilipsHead said:**
> Ok, this is how it is, Linux is based on Unix, you know that and i am fully aware that you know that.

And you know what, there are about 10 000 other compatible distros out there that also use the Unix way, beyond that there are a few BSD's that also use it.

You are asking to change something for less than 1/100'th of the users and just because they can't get used to an age old standard?

Weeeelllll, how about no?

Serioualy we don't care about newbies, no one does, they will lern the ropes or go back to windows, nobody else cares, why do you?

I see the first point and kind of agree, I think your second point was a bit harsh.

I do care about new users, the fact that the beginners section exists proves that the majority of us do.

I am a father, and I think that new users are like children (analogy, no offense intended). Yes they need guidance and support, but you also have to let them make their own mistakes and to learn from them.

---

### Post by PhilipsHead on 2006-07-12
> **richbarna said:**
> I see the first point and kind of agree, I think your second point was a bit harsh.

I do care about new users, the fact that the beginners section exists proves that the majority of us do.

I am a father, and I think that new users are like children (analogy, no offense intended). Yes they need guidance and support, but you also have to let them make their own mistakes and to learn from them.

I'm a father of six children, two girls, (much too pretty for my liking, i really should get that shotgun) and four boys (who are kung fu all hours of the day)

I have NO idea where you got anything of that from, where did i claim anything against it?

You ASSUME things, bad ninja!

---

### Post by richbarna on 2006-07-12
> **PhilipsHead said:**
> I'm a father of six children, two girls, (much too pretty for my liking, i really should get that shotgun) and four boys (who are kung fu all hours of the day)

I have NO idea where you got anything of that from, where did i claim anything against it?

You ASSUME things, bad ninja!

I ASSUMED this was harsh :-
> Serioualy we don't care about newbies, no one does, they will lern the ropes or go back to windows, nobody else cares, why do you?
 ....bad ninja!:)

PS: I've got a daughter, Shotgun will be bought.

---

### Post by Christmas on 2006-07-12
[quote=PhilipsHead]Serioualy we don't care about newbies, no one does, they will lern the ropes or go back to windows, nobody else cares, why do you?[/quote]
I don't know about you but I personally care about newbies, hell I'm still one right now! Ubuntu is intended to be a friendlier and newbie accessible distribution, so actually we do care about newbies :)

I myself tried to convert a couple of friends to Kubuntu (I'm not recommending Ubuntu because I think GNOME lacks configuration tools and is slow) and told them I will help them with everything I know, from installing software to using multimedia players with their proprietary packages. I think we should be more respectful to a total newbie, actually nobody enforces you to be kind, but one thing I didn't like on Debian's official IRC channel was a person who "knew" too much and managed to try looking smart and made me leave.

---

### Post by aysiu on 2006-07-13
Well, now we have 17 in favor, 12 against, and 6 indifferent.

Anyone know, if I did propose it as a bug to the developers, what package it would be filed under...? *sudo*? Or something else?

---

### Post by prizrak on 2006-07-13
> **aysiu said:**
> Well, now we have 17 in favor, 12 against, and 6 indifferent.

Anyone know, if I did propose it as a bug to the developers, what package it would be filed under...? *sudo*? Or something else?

I don't think it could be filed as a bug, it's technically not an error in the program the behavior is by design. You should submit it as a feature request. The package affected I would guess would be gnome-terminal.

---

### Post by aysiu on 2006-07-13
> **prizrak said:**
> I don't think it could be filed as a bug, it's technically not an error in the program the behavior is by design. You should submit it as a feature request. The package affected I would guess would be gnome-terminal.
In that case, where would be the best place to put in a feature request? I'm assuming this would be for Edgy+1?

---

### Post by o_fortuna on 2006-07-13
I definitely think there should be feedback. For one, as a security measure, it's essentially useless, considering if you use the graphical programs someone can see how many letters your password is anyway. That doesn't really matter anyway, as aysiu has mentioned several times that someone trying to steal your password would probably simply look at the keyboard.

I remember when I first installed Ubuntu 5.04, Hoary Hedgehog. At that time, the text installer did not give any feedback on the password. It took me several minutes to realize that it was working, just not giving feedback. As of the 5.10 installer, it shows asteriks when asking for your password. If the ancient text-based installer can do it, surely the terminal can do it too. It's just another example showing how possible it is.

There's no good reason for making new users jump through hoops. Most people trying linux *want* to "learn the ropes." In my opinion, there's no reason NOT to tear down unnecessary barriers to making life easier for people. One simple change, and one less burden on the backs of people trying to switch to linux.

Besides, it makes logical sense, even from an experienced user's perspective, to show what you're typing on screen. Not everyone is a perfect typer. Sometimes my finger slips and I hit two keys at the same time. It's just easier to realize that I've typed too many letters by looking at the screen than pressing enter and waiting a moment for the system to tell me my error.

It's time for a change. :D

---

### Post by kabus on 2006-07-13
> **aysiu said:**
> In that case, where would be the best place to put in a feature request? I'm assuming this would be for Edgy+1?

A good way to get some quick feedback/advice where to put a feature request from a developer would be to post to one of the mailing lists.
Gnome-Terminal is definitely not the right package.

---

### Post by wrtrdood on 2006-07-13
> **aysiu said:**
> 
Is that a terminal thing fundamental to Linux/Unix/etc.?


Yes.  It's a *nix standard.  No other flavors echo back and I doubt there'd be much buyin for changing it on Linux.

  If it's really an issue set the xterm to local echo.  Of course you'll then see the password as it's typed.  Not a good solution but you'll at least know that it's working...

---

### Post by prizrak on 2006-07-13
> **aysiu said:**
> In that case, where would be the best place to put in a feature request? I'm assuming this would be for Edgy+1?
I believe you can post feature requests in Launchpad you just label it as a feature request. The mailing list idea is a good one as a dev would most likely know the absolute best way of doing it.

---

### Post by prizrak on 2006-07-13
> **wrtrdood said:**
> Yes.  It's a *nix standard.  No other flavors echo back and I doubt there'd be much buyin for changing it on Linux.

  If it's really an issue set the xterm to local echo.  Of course you'll then see the password as it's typed.  Not a good solution but you'll at least know that it's working...

It's about the defaults not what we can change. Anyone experienced enough knows that password is not displayed at all :)

---

### Post by aysiu on 2006-07-13
> **prizrak said:**
> I don't think it could be filed as a bug, it's technically not an error in the program the behavior is by design. You should submit it as a feature request. The package affected I would guess would be gnome-terminal.
I tried to enter it as a specification (I didn't see anywhere on Launchpad to enter feature requests), but I was missing some important information, I think.

So I ended up just reporting it as a bug:
[https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914](https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914)

Would it make sense to duplicate the "bug" report for Konsole, too?

---

### Post by bruce89 on 2006-07-13
> **aysiu said:**
> Would it make sense to duplicate the "bug" report for Konsole, too?

I think it is more of a *bash* issue, but mabye I'm stupid.

---

### Post by aysiu on 2006-07-13
> **bruce89 said:**
> I think it is more of a *bash* issue, but mabye I'm stupid.
No, it probably is a bash issue. This goes beyond me...

---

### Post by ahaslam on 2006-07-13
If you want visual feedback, use **gksudo** instead of **sudo**.

Tony.

---

### Post by aysiu on 2006-07-13
Tony.

I know.

That's the whole point of this thread. It's not consistent, and it confuses some new users who--seeing the visual feedback in *gksudo*--also expect it in the terminal... and don't get it.

I'm not speaking for myself. I'm speaking on behalf of new users I've had to help over the past year.

---

### Post by ahaslam on 2006-07-13
> **aysiu said:**
> I'm not speaking for myself. I'm speaking on behalf of new users I've had to help over the past year.
I thought you'd know, I was just pointing it out to those that may stumble across this thread.

Personally I like the visual feedback from the GUI's but when it comes to the terminal, I'm not really bothered. Having the choice of using either sudo or gksudo is good for those that are.


Tony.

PS. I greatly appreciate your 'pure gnome' guide ;)

---

### Post by prizrak on 2006-07-13
> **aysiu said:**
> I tried to enter it as a specification (I didn't see anywhere on Launchpad to enter feature requests), but I was missing some important information, I think.

So I ended up just reporting it as a bug:
[https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914](https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914)

Would it make sense to duplicate the "bug" report for Konsole, too?

I think you should just add it to the bug as a comment.

> I think it is more of a bash issue, but mabye I'm stupid.
A terminal emulator has certain control over the display so it could be able to change the output. Well we got developers to figure out details like that ;)

---

### Post by aysiu on 2006-07-13
> **prizrak said:**
> I think you should just add it to the bug as a comment. Done.

---

### Post by ubuntu_demon on 2006-07-13
I think it's better for security if no black dots / asterisks wheren't shown in the GUI (nor in the terminal). 

Users get confused because they are used to windows. But if you explain that is a security thing (policy) I think most of them will understand.

Although I don't think it's a very big deal.

---

### Post by aysiu on 2006-07-13
> **ubuntu_demon said:**
> I think it's better for security if no black dots / asterisks where shown in the GUI (nor in the terminal). 

Users get confused because they are used to windows. But if you explain that is a security thing (policy) I think most of them will understand.

Although I don't think it's a very big deal.
But then why show asterisks in the GUI? If it's a security issue, turn the asterisks off altogether.

---

### Post by RAV TUX on 2006-07-13
I have never had any problems entering my password in the terminal, I just installed wine via the terminal and it "just works"

---

### Post by cleverselfreferentialname on 2006-07-14
While I'm more of the absolute paranoid security sort who would edit his .bashrc and turn it off, I do think it would be a good idea to provide visual feedback.

---

### Post by atezun on 2006-07-14
I think terminal does it as a security feature, but it really doesn't matter to me either way. Personally, I've never had a problem with it.

---

### Post by ubuntu_demon on 2006-07-14
> **aysiu said:**
> But then why show asterisks in the GUI? If it's a security issue, turn the asterisks off altogether.
That was a typo :-D. Thank you for noticing. I meant : "**wheren't** shown"

So yeah I voted for turning them off altogether and explaining to the user that it's a security policy.

---

### Post by angkor on 2006-07-14
> **aysiu said:**
> It's not consistent

I really don't see this as an issue. Maybe a couple of new users will be confused at first but they'll get it fairly quickly imo. I think this will only happens once for a new user and I also don't think a lot of new users will have this problem.

I don't consider it being inconsistent. Where talking about gui vs terminal here. Nearly *everything* is different between them. It seems logical that a graphical user interface gives some graphical feedback. Why does the terminal have to do the same? 

About the security side. I really doubt you'd be able to repeat my password after looking at my fingers once when I type my password. I do believe you can count the dots however. I agree this is not a big issue but still.

---

### Post by 3rdalbum on 2006-07-14
Rather than have asterisks printed, I'd prefer it if it printed "User is typing password" when characters have been input. That way, it's no kind of security risk, yet there is visual feedback for the new users.

---

### Post by Malac on 2006-07-14
Let's just face it the feedback from an Xterminal isn't set because it would take that bit of extra coding.
Whereas just redirecting the output to NULL or not "printf" it to the screen is quicker to code.

Mind you in console only Linux apps perhaps the code needed to get the asterisks to show would somehow be logged, then you're password would be available by scanning your logs.

Security or laziness?

---

### Post by kabus on 2006-07-14
> **3rdalbum said:**
> Rather than have asterisks printed, I'd prefer it if it printed "User is typing password" when characters have been input. That way, it's no kind of security risk, yet there is visual feedback for the new users.

I'm not convinced there is much of a security risk here:
If the user has a strong password knowing the number of characters shouldn't be of much use to an attacker.
If the user has a weak password he's in trouble anyway.

---

### Post by adam.tropics on 2006-07-14
Both or neither, but consistant. Configurable by gconf-editor, and for the benefit of new-Ubuntees, on by default.

---

### Post by aysiu on 2006-07-14
> **angkor said:**
> I really don't see this as an issue. Maybe a couple of new users will be confused at first but they'll get it fairly quickly imo. I think this will only happens once for a new user and I also don't think a lot of new users will have this problem. Why confuse them the first time, though? I myself was not confused, but I have seen a number of confused users over the past year.

> 
I don't consider it being inconsistent. Where talking about gui vs terminal here. Nearly *everything* is different between them. It seems logical that a graphical user interface gives some graphical feedback. Why does the terminal have to do the same? I don't know why in theory. I just know in practice that it *does* confuse people. 

> 
About the security side. I really doubt you'd be able to repeat my password after looking at my fingers once when I type my password. I do believe you can count the dots however. I agree this is not a big issue but still. You may be the fastest typist around the block, then. That doesn't discount the fact that most of the time when I see people typing, I can see what they're typing if I wish to pay attention. And seeing only six out of eight keys pressed is a lot more helpful than counting up that there were eight keys pressed.

---

### Post by bruce89 on 2006-07-14
It is disconserting for new users to not have feedback (I'd know, as I was there once), but if it is a long-standing policy which has a good reason behind it, then that's fine.

---

### Post by aysiu on 2006-07-14
Just to clarify a bit--this is **not** a big deal.

It is a **deal**, though. I think it's an issue. If it's too much trouble to get it resolved, then it's too much trouble, and I can understand that.

But to say that for new users it shouldn't be an issue is just ignoring the fact that for some new users... it is an issue.

---

### Post by Mathias-K on 2006-07-14
> **aysiu said:**
> Any thoughts? Should I file a bug report on this?

That's really a good point. I've been stuck myself thinking the terminal was broken somehow. Great idea for newcomers.

You've actually made a whole lot of great idea threads lately. Keep that up :KS

---

### Post by ciscosurfer on 2006-11-16
I'm all for asterisks at the password prompt from within a terminal session.

Control-U is nice, but Backspace or Delete (albeit multiple clicks) has the same effect.

---

### Post by argie on 2006-11-16
I was wondering about this the first time when I did a "su", but I typed it in anyway :D

I think there should be asterisks, or atleast an extra line that says "Password will not be printed on screen as you type" before "Password:"

---

### Post by ciscosurfer on 2006-11-16
> **argie said:**
> I was wondering about this the first time when I did a "su", but I typed it in anyway :D

I think there should be asterisks, or atleast an extra line that says "Password will not be printed on screen as you type" before "Password:"That's also a good idea! :)

---

### Post by hotbrainz on 2006-11-16
I did type the password , even when i could not see it the first time. But i reckon there could be a message with "su". Taht way the new user will become aware and the experienced user will have the "whatever" claimed benefits there are.

---

### Post by Malac on 2006-11-16
How about terminal shows the asterisks by default, for new users, etc, but the truly paranoid can turn it off with an option like "Hide Password Entry" in the terminal menus if they want.
Seems the best of both worlds to me.

---

### Post by red_Marvin on 2006-11-16
A reason for not showing it in terminal might be to make it impossible to pipe the "output" to [something] whereas the gui prompts are hidden behind layers and layers of gtk widget relations. Another thing might be that there is no standardized function (scanf() equivalent etc) that inputs from stdin and outputs to stdout -not what whas inputted but the corresponding number of stars...

---

### Post by engla on 2006-11-16
so we've found some small ideas.

Would putting a warning/explanation in that message that appears the first time you use sudo be sufficient? Isn't that the time when 90% of the users see this prompt for the first time?

Is there an issue with the ttys? Should we put a permanent explanation/warning in the issue file (/etc/issue is the text displayed above the logins in the ttys)

---

### Post by EdThaSlayer on 2006-11-16
I personally prefer it this way because it kind of hides your password, making it seem like its impossible to copy it(as in get asteriks and paste them into some program that can decode them). But then again, I could be wrong about that(I just think my security is better). They should add a option to the terminal, such as with or without asteriks.

---

### Post by Dual Cortex on 2006-11-16
There is no such program that can decode passwords from asterisks!
They are just outputted symbols, copying and pasting doesn't carry any values.

---

### Post by EdThaSlayer on 2006-11-16
> **Dual Cortex said:**
> There is no such program that can decode passwords from asterisks!
They are just outputted symbols, copying and pasting doesn't carry any values.

](*,) 
I imagine too many things!
:???: 
Thanks for informing me.
Now I'm not that crazy anymore about security and such.
:-k 
But they can still find out the length of the string you typed in.

---

### Post by aysiu on 2006-11-16
I know some of you are joining this thread for the first time, so I thought I'd sum up some stuff for you.

My original objection to lack of feedback when you enter your password in the terminal comes from many threads I've seen in which users get confused when they don't see any asterisks in the terminal but they do see them in the GUI.

It's a consistency issue as well as a general usability issue.

It is not a security issue for the following reasons:

1. If asterisks or dots were a security issue, they should not appear at all when you enter your password in the GUI, but they *do* appear in the GUI.

2. If someone is standing behind you, she would be better off trying to steal your password by looking at what keys you're pressing instead of how many asterisks she sees on the screen, and she can actually hear how many keys you're pressing anyway, even if she just wanted to count.

I've already filed a bug report on this, and the developers rejected it:
[https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914](https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914)

If you have anything else to add (a new bug report on a more appropriate package than *gnome-terminal*, for example), please do, but let's not pretend there's any security in having no visual feedback. If you really believe that, you should be advocating for getting rid of the visual feedback in the GUI, too!

---

### Post by Dual Cortex on 2006-11-16
Yes, I went through that too my first day on Ubuntu.

Got confused for a min... but I noticed the cursor blinked when
 
I pressed a key... Typed my password and it worked.

For some reason, people, including myself, don't just type the 

actual password at least to see what happens... we notice there's 

no GUI feedback and we just type garbage and wonder why there are 

no asterisks.

---

### Post by Malac on 2006-11-16
> **red_Marvin said:**
> A reason for not showing it in terminal might be to make it impossible to pipe the "output" to [something] whereas the gui prompts are hidden behind layers and layers of gtk widget relations. Another thing might be that there is no standardized function (scanf() equivalent etc) that inputs from stdin and outputs to stdout -not what whas inputted but the corresponding number of stars...
Try piping the console entry of passwords to a file and you'd just get the ************ not the letters typed. Keylogging apps are whole separate issue, this has absolutely nothing to do with security it is purely that a new set of functions would have to be written just for the password entry instead of just "switching off" the feedback of existing functions.
Not enough demand or no programmers willing to spend the time on the vte code, take your pick of the reasons why it hasn't been done.

---

### Post by Toontwnca on 2006-11-17
I say leave it.
I once thought that my password was not being accepted.
Took me all of 45 seconds to figure it out.
And I'm not exactly one of the smarter ones around.
It's not rocket science.

---

### Post by aysiu on 2006-11-17
> **Toontwnca said:**
> I say leave it.
I once thought that my password was not being accepted.
Took me all of 45 seconds to figure it out.
And I'm not exactly one of the smarter ones around.
It's not rocket science.
A lot of things aren't rocket science, by why make things confusing to new users for even 45 seconds?

---

### Post by ciscosurfer on 2006-11-17
> **Toontwnca said:**
> I say leave it.
I once thought that my password was not being accepted.
Took me all of 45 seconds to figure it out.
And I'm not exactly one of the smarter ones around.
It's not rocket science.Visual feedback is always nice :D

---

### Post by aysiu on 2006-11-17
I understand that this may be too much trouble to change, but the idea that people can figure out in 45 seconds inconsistent behavior in an interface doesn't mean the behavior is good or can't be improved.

And a lot of people can't figure it out in 45 seconds, which is why they post threads here saying Ubuntu isn't accepting their passwords!

---

### Post by shining on 2006-11-17
> **aysiu said:**
> 
It's a consistency issue as well as a general usability issue.


I agree it's a consistency issue.
It isn't a general usability issue to me, but well, I can understand it is for some users.
So I also think it would be nicer if something was done about it, so that * are displayed in every place you write a password.

---

### Post by Toontwnca on 2006-11-19
> **aysiu said:**
> A lot of things aren't rocket science, by why make things confusing to new users for even 45 seconds?

Good point.

---

### Post by BWF89 on 2006-11-19
I voted **There shouldn't be. I like it the way it is. In fact, take away the black dots from the GUI**

I'm a new Linux user and it doesn't bother me in the least bit. It didn't freak me out or anything. The first time I entered my password and I saw there was no black dots I just made sure the window was activated and hit enter. After it accepted my password I thought "oh, that's a nice security feature". After seeing that work in the terminal I think that same concept should be applied to all situations where you have to enter a password. On websites too.

Ofcourse if someone standing behind you wanted to know your password he could always look at what keys you were typing or if he wanted to know how many letters just count the keystrokes. But it just seems like a smart idea for some reason. Not that it matters to me, I use Freespire. But Ubuntu being the huge distro it is should set a good example for the others to follow.

---

### Post by coder_ on 2006-11-19
It's good how it is.  Don't change it.  I like Ubuntu, and don't want it to be changed to make it more separated from "regular" Linux distros more than it already is (Due to the root user password thing already, which I dislike).

Although I highly doubt it would get changed.

---

### Post by arnieboy on 2006-11-20
Its a traditional unix feature. Linux inherited it.

---

### Post by shining on 2006-11-20
> **coder_ said:**
> It's good how it is.  Don't change it.  I like Ubuntu, and don't want it to be changed to make it more separated from "regular" Linux distros more than it already is (Due to the root user password thing already, which I dislike).

Although I highly doubt it would get changed.
> **arnieboy said:**
> Its a traditional unix feature. Linux inherited it.

The fact that it's a traditional unix feature doesn't make it any better. These traditions are the cause of several weird and inconsistent behavior.
I also doubt it'll be changed, but I don't think it's right.
Or otherwise, I would change the gui instead, so that it behaves the same way (no outputs when writing password).
Then the users who complain will probably complain even more, because they will think that all password box are broken.
But it would be consistent and I would be happy :)

---

### Post by neoflight on 2007-01-07
i need "password accepted"  or "access denied" message flashing on my entire screen in bold-red thick letters as in those movies :mrgreen: 

PLUS... i refuse to bite on to a pencil or grow my hair sideways or sit on a low-back revolving chair or talk jargons or wear ultra-thick glasses or clap my hands if some smart guy gets something done my office and finally get shot by the bad guys...

anyway...i think  its the unix thing...all the linux distros i tried exhibit the same phenomenon.

---

### Post by Tomosaur on 2007-01-08
I'm not really bothered either way, but I guess for new people, the experience is a little confusing. I think it should be optional, but switched on by default. I can see no reason why not showing anything is useful. If there's someone looking over my shoulder, then there's nothing to stop them just rebooting into safe mode and taking control anyway.

HOWEVER:
I think the 'not showing you type' thing is not to do with sudo, but to do with vulnerabilities in the terminal itself. It is possible to listen to input and output into the terminal as plaintext. Normally, the terminal would give you feedback while you type. When you use sudo however, it 'sits on top', so to speak, so your input goes straight to sudo rather than passing through the terminal. I think it is a combat against keyloggers and such, rather than stopping people looking over your shoulder.

---

### Post by KernelKen on 2007-01-12
I learned how to type along time ago and do not use the hunt and peck method.  Because I type fast and hit enter I don't have a need for it.  

But when I do try and help friends and family with computer problems I find that they type slower, read everything, and look for visual cues.  So I vote for dots or something.

---

### Post by Lord Illidan on 2007-01-12
I agree that it can be a problem for new users, yet I am also aware of the security issues involved.

The solution:

A message saying that the password will not be echoed to the screen should be sufficient.

---

### Post by truthfatal on 2007-01-12
I don't think it matters too much. If a person doesn't remember their password dots on the screen probably won't help much.

---

### Post by aysiu on 2007-01-12
> **truthfatal said:**
> I don't think it matters too much. If a person doesn't remember their password dots on the screen probably won't help much.
It's not about remembering your password. It's about getting reassurance that the computer's actually acknowledging your input.

If such acknowledgement isn't important, then the dots shouldn't appear in GUI authentication either (Synaptic, for example)--but they *do*.

---

### Post by kd7swh on 2007-01-12
> **Brunellus said:**
> there should be asterisks for newbies, I guess.  It never bugged me, but it freaks the newbies out.

This is right on the money.

---

### Post by kd7swh on 2007-01-12
> **aysiu said:**
> It's not about remembering your password. It's about getting reassurance that the computer's actually acknowledging your input.

Or acknowledgment that it is not  freezing or crashing on you, I have told people things like this:

"In the terminal, when typing a password the cursor stops blinking, if it doesn't start blinking again when you stop typing than you know something is wrong."  

Mind that was on a 386 back in the day.

---

### Post by truthfatal on 2007-01-14
> **aysiu said:**
> It's not about remembering your password. It's about getting reassurance that the computer's actually acknowledging your input.


I must not hove understood the original post. I'll admit the first time I encountered the password dialog on the CLI I was confused that I didn't see any *s, and I though that something went wrong. When I hit "enter" in frustration and I was told by the computer that my password is incorrect, I realized that passwords on the CLI are invisible. I hav'n't thought of it since.

Thinking further, since Ubuntu seems to try to attract 'new' users, perhaps a feature request *is* in order. The confusion may just be "the straw that breaks the camels back" for a new user considering giving up on Linux.

---

### Post by STREETURCHINE on 2007-01-14
i dont think it matters if i cant remember to type my password correctly ,it dosnt matter if i can see a line of asterixes or not if it is wrong it is wrong...:D

---

### Post by sloggerkhan on 2007-01-14
I like being able to count the characters I've typed to make sure I didn't type any extra ones, so I am a fan of black dots or asteriks.

---

### Post by Belyel on 2007-04-10
My thought on this is that it is difficult for anyone to see what password I am typing by watching my fingers on the keyboard.  I usually practice my passwords until I can type them very quickly to avoid such a situation.  I think that having a placeholder for the letters in my password as I type them makes my system less secure, especially if I have to supply my password while my computer is hooked up to a projector, so I would prefer to have no indication as I type letters.  I'm smart enough to figure out if I typed it wrong.

---

### Post by aysiu on 2007-04-10
> **Belyel said:**
> My thought on this is that it is difficult for anyone to see what password I am typing by watching my fingers on the keyboard.  I usually practice my passwords until I can type them very quickly to avoid such a situation.  I think that having a placeholder for the letters in my password as I type them makes my system less secure, especially if I have to supply my password while my computer is hooked up to a projector, so I would prefer to have no indication as I type letters.  I'm smart enough to figure out if I typed it wrong.
And my thoughts on this are

1. that if anyone is bothering to count how many dots appear on the screen, she can also listen for how many times the keys on your keyboard click as you type your password. Even if she knew your password is eight characters long, it would take an extremely long time to guess what your password is if it's not a dictionary word.

2. if that's the **real** reason for the lack of visual feedback, *there should be no visual feedback for graphical applications' password prompts either*, but there **are**.

The behavior, as I've said many times in this thread, is inconsistent. If it is really a security issue, the feedback should never appear--not in the terminal and not in the GUI. If, however, visual feedback makes sense in the GUI, then it should also make sense in the terminal, for consistency's sake.

But, as you can see from this thread and the bug report I filed, the developers are not going to change this, unfortunately for many, many new users who get confused.

---

### Post by karellen on 2007-04-10
I like things as they are now. terminal - no feedback, gui - black dots

---

### Post by aysiu on 2007-04-10
Okay, In case some people missed it, the developers have already rejected the proposal. 

All the people who love inconsistency and think they're secure by getting no visual feedback from the terminal but getting visual feedback from the GUI: you win.

Case closed. You win. I lose. I think I have a point, but the developers aren't going to budge on this, so no point in discussing it further.

---

### Post by aysiu on 2010-07-08
There seems to be some renewed interest in this:
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

**8 July 2010** - A few recent instances of confusion:
[http://ubuntuforums.org/showthread.php?t=1523820](http://ubuntuforums.org/showthread.php?t=1523820)
[http://ubuntuforums.org/showthread.php?t=1508934](http://ubuntuforums.org/showthread.php?t=1508934)
[http://ubuntuforums.org/showthread.php?t=1490700](http://ubuntuforums.org/showthread.php?t=1490700)
[http://ubuntuforums.org/showthread.php?t=1316266](http://ubuntuforums.org/showthread.php?t=1316266)
[http://ubuntuforums.org/showthread.php?t=1445921](http://ubuntuforums.org/showthread.php?t=1445921)
[http://ubuntuforums.org/showthread.php?t=1380365](http://ubuntuforums.org/showthread.php?t=1380365)
[http://ubuntuforums.org/showthread.php?t=1384749](http://ubuntuforums.org/showthread.php?t=1384749)
[http://ubuntuforums.org/showthread.php?t=1328613](http://ubuntuforums.org/showthread.php?t=1328613)
[http://ubuntuforums.org/showthread.php?t=1312708](http://ubuntuforums.org/showthread.php?t=1312708)
[http://ubuntuforums.org/showthread.php?t=1113222](http://ubuntuforums.org/showthread.php?t=1113222)
[http://ubuntuforums.org/showthread.php?t=1103014](http://ubuntuforums.org/showthread.php?t=1103014)
[http://ubuntuforums.org/showthread.php?t=1084200](http://ubuntuforums.org/showthread.php?t=1084200)
[http://ubuntuforums.org/showthread.php?t=1043585](http://ubuntuforums.org/showthread.php?t=1043585)
[http://ubuntuforums.org/showthread.php?t=1002113](http://ubuntuforums.org/showthread.php?t=1002113)
[http://ubuntuforums.org/showthread.php?t=992510](http://ubuntuforums.org/showthread.php?t=992510)
[http://ubuntuforums.org/showthread.php?t=888062](http://ubuntuforums.org/showthread.php?t=888062)
[http://ubuntuforums.org/showthread.php?t=865199](http://ubuntuforums.org/showthread.php?t=865199)
[http://ubuntuforums.org/showthread.php?t=840315](http://ubuntuforums.org/showthread.php?t=840315)
[http://ubuntuforums.org/showthread.php?t=805800](http://ubuntuforums.org/showthread.php?t=805800)
[http://ubuntuforums.org/showthread.php?t=672178](http://ubuntuforums.org/showthread.php?t=672178)
[http://ubuntuforums.org/showthread.php?t=639982](http://ubuntuforums.org/showthread.php?t=639982)

---

### Post by cariboo on 2010-07-08
This is really a non-issue, if there several posts per week about the problem, then it could bear looking at. 

I'm all for making it easier for new users to use Ubuntu, but there really isn't a need for a new user to use the terminal at all, almost everything they need to do can be done using a gui. By the time they need to start using a terminal, they have probably used Ubuntu for a while, and have learned many of the differences between it and their previous os.

---

### Post by McRat on 2010-07-08
It's time for Ultra Secret Special Screen to retire.

The reason "password hiding" came on the scene was that you didn't have a monitor.  Your password was typed on a teletype.  You HAD to hide it or destroy the printout constantly.

Does anyone realize why a monitor's dimming knob will hide the screen and a TV won't?  Because with a monitor, you might want to hide a password.

When you have a lot of passwords to deal with, in an internally safe environment, hiding passwords is really destructive, and it forces users to either write down passwords, or use the same password for multiple uses.

---

### Post by McRat on 2010-07-08
PS - There is even a stinking password on my MICROWAVE OVEN!  How weird is that????

I have at least 100 devices and apps that use passwords.  Sound like alot?  Think about it a bit.  Every router, PC, TV (childproofing routines), cellphone, email account, CC, website, etc, etc, etc.

I have a strong password that is changed routinely, and a medium one that seldom changes, and a trash one for stuff I don't care about that never changes.  Most PC's get the trash one.

I can tell which password is which if I know how many letters it uses.  If it's X, it's trash, if it's X+2 it's medium, if it's more, it's strong.  If I can't tell how many letters, I need to do some guessing.

Passwords are easy to crack because many IT professionals today think making stuff hard to use == security.  It doesn't.  It makes people defeat the security instead.

---

### Post by Frogs Hair on 2010-07-08
When I first used the terminal , I thought " cool my password is hidden " I never thought that it was abnormal.

---

### Post by cariboo on 2010-07-08
Passwords are only going to keep casual users out, the reason for blanking the password in a terminal is to keep shoulder surfers from knowing what the password is.

---

### Post by aysiu on 2010-07-08
> **cariboo907 said:**
> Passwords are only going to keep casual users out, the reason for blanking the password in a terminal is to keep shoulder surfers from knowing what the password is.
Which is ineffective anyway, because someone behind your shoulder can see at least some of the letters you're typing on your keyboard or at least count the number of clacks the keyboard.

---

### Post by McRat on 2010-07-08
Unnatural passwords are the most secure, like Q23sxrPi19

These are the hardest to type with zero feedback (and also the hardest to remember if you're a shoulder surfer).

So naturally, selecting a strong password for systems with zero feedback is not desirable.

Test it.

Turn off your monitor and type it 5 times, then look.

You are better off using something like duckbill25.  Try that one 5 times.

Even if somebody sees how many letters are in a strong password, it's not a lot of help.  Anything that discourages strong passwords is counterproductive.

---

### Post by TheWeakSleep on 2010-07-08
> **cariboo907 said:**
> This is really a non-issue, if there several posts per week about the problem, then it could bear looking at. 

I'm all for making it easier for new users to use Ubuntu, but there really isn't a need for a new user to use the terminal at all, almost everything they need to do can be done using a gui. By the time they need to start using a terminal, they have probably used Ubuntu for a while, and have learned many of the differences between it and their previous os.

Though I don't mind not having the password echo in the terminal, I disagree with this. If the new user's install was less than perfect, they may need to use the terminal. For instance, when I had first installed ubuntu, my wireless internet wasn't working at all. going to help.ubuntu.com, it specifically told me to enter a few commands into the terminal. I'm not saying it should be changed, cause after a "Sorry, try again" I figured it out, just that avoiding the terminal isn't always possible, even for new users, especially if they visit support sites.

---

### Post by donkyhotay on 2010-07-09
People expect to get visual feedback because that is the way GUI's (including windows and osX) do things. If people stopped expecting the feedbacks then it wouldn't be an issue. I was one of those that was confused the first time I tried typing a password into the CLI however once I found out what was going on I realized that it made sense and my next thought was "why don't other systems do this?". I would much prefer to eliminate all visual feedback on passwords, including typing passwords into web page fields. Many people who are used "the old way" of doing things would of course howl and complain and think it "broken forever" however it would provide better security all around.

---

### Post by aysiu on 2010-07-09
> **donkyhotay said:**
> People expect to get visual feedback because that is the way GUI's (including windows and osX) do things. If people stopped expecting the feedbacks then it wouldn't be an issue.
It's a matter of consistency. The lack of consistency is what confuses new users. The GUI dialogues **in Linux** (not Windows and OS X) give visual feedback. The CLI ones don't.

---

### Post by gnomeuser on 2010-07-09
I do quite like what my phone does, as you enter the password it displays the current single character for about a 1 sec then turns it into a dot. 

This gives you feedback and ensures that you typed the password correctly, while maintaining a reasonably secure environment.

---

### Post by Penguin Guy on 2010-07-09
I personally think asterisks or something should appear, but the people who make the decisions disagree.

---

### Post by aysiu on 2010-09-23
Once again they've decided not to fix this bug:
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

---

### Post by user1397 on 2010-09-23
> **aysiu said:**
> Once again they've decided not to fix this bug:
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

That's a shame.  The devs are so scared of changing sudo, even though something as easy as adding that line like in comment #60 of the launchpad page, would be easy enough without risking anything.

I'm all for consistency.  sudo, gksudo, and kdesu all have to be consistent about this; I don't care if that means showing nothing, showing bullets, showing asterisks, or just showing a symbol to note that the person is typing (like [...] or something)...it doesn't matter.  As long as it is the same for all 3 programs I'm fine with it.  As long as it is inconsistent then it is embarrassing to me as an ubuntu user...

---

### Post by Bachstelze on 2010-09-23
Can this go to Recurring discussions, please? Also I've seen a lot of threads bumped after more than 3 months of inactivity and then closed for necromancy.

---

### Post by aysiu on 2010-09-30
> **ubuntuman001 said:**
> That's a shame.  The devs are so scared of changing sudo, even though something as easy as adding that line like in comment #60 of the launchpad page, would be easy enough without risking anything.

I'm all for consistency.  sudo, gksudo, and kdesu all have to be consistent about this; I don't care if that means showing nothing, showing bullets, showing asterisks, or just showing a symbol to note that the person is typing (like [...] or something)...it doesn't matter.  As long as it is the same for all 3 programs I'm fine with it.  As long as it is inconsistent then it is embarrassing to me as an ubuntu user... Definitely a shame. See? [Another confused new user.](http://ubuntuforums.org/showthread.php?p=9904727#post9904727) And the usual perpetuation of the myth that it's for security reasons.

---

### Post by jwbrase on 2010-09-30
> **aysiu said:**
> Once again they've decided not to fix this bug:
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

Not really a *bug*, per se, considering that it is intended behavior. It would be nice if the intended behavior for the GUI and at the terminal matched though...

---

### Post by wkhasintha on 2010-09-30
I have used to it now hence it doesn't make any difference but for newbies it could be convenient to add some placeholders ...

---

### Post by psusi on 2010-09-30
It's always been that way.  Even ancient netware logins under dos did not show any feedback.  I guess for that reason I'm used to it and don't really care one way or the other.  Of course, I can see the argument that it would be nice and there doesn't seem to be a compelling reason NOT to do it.

Bring it up to the technical board.

---

### Post by Spyderkid on 2011-05-10
is it against forum rules so make a thread where i say to comment 'yes' if you want 11.10 to have astericks when you type in sudo password in terminal?

 because at the moment you just type and press enter, nothing comes up. and i see millions of questions about why the keys don't show up.

So would you have a problem with this?

---

### Post by SavageWolf on 2011-05-10
The best option would be to suggest it on launchpad and such.

Also, this has come up numerous times, and the answer has always been "no"...

---

### Post by Spyderkid on 2011-05-10
Personally i don't see what the big problem is of just adding in astericks or something? just put it in an update, or create a new terminal app for ubuntu and use that instead?

---

### Post by WorMzy on 2011-05-10
Just enable the pwfeedback option in visudo.

e.g.

```
Defaults timestamp_timeout=0,editor=/usr/bin/vim:/usr/bin/vi:/usr/bin/nano,**pwfeedback**
```

[IMG]http://img36.imageshack.us/img36/5050/screenshot100511192752.png[/IMG]

---

### Post by uRock on 2011-05-10
Moved to forum feedback and help.

---

### Post by lisati on 2011-05-10
If memory serves correctly - there might be a thread that mentions it somewhere - the reason it's currently done this way (blanks) is largely historical.

---

### Post by Habitual on 2011-05-10
> **lisati said:**
> If memory serves correctly - there might be a thread that mentions it somewhere - the reason it's currently done this way (blanks) is largely historical.

Prevents "shoulder surfing".
Nothing historical about that unless you're a youngster. :)

---

### Post by WorMzy on 2011-05-10
> **lisati said:**
> If memory serves correctly - there might be a thread that mentions it somewhere - the reason it's currently done this way (blanks) is largely historical.

I think you're probably thinking of this thread from 2006: [http://ubuntuforums.org/showthread.php?t=214393](http://ubuntuforums.org/showthread.php?t=214393)

---

### Post by lisati on 2011-05-10
> **WorMzy said:**
> I think you're probably thinking of this thread from 2006: [http://ubuntuforums.org/showthread.php?t=214393](http://ubuntuforums.org/showthread.php?t=214393)

Quite likely...... :D

---

### Post by aysiu on 2011-05-11
> **Habitual said:**
> Prevents "shoulder surfing". I think I've already thoroughly debunked this myth. Please read the thread.

---

### Post by Bandit on 2011-05-14
I am used to their not being and visual feedback for terminal passwords as I see this as a added security feature. But the feed back in the GUI shows dots, which my self like most people are accustomed to. 

To be honest, these issues can be changed by the user if he or she really has that much of an issue with it. There are more pressing matters to be worked out in Unity then to worry about PW feedback. IMHO

- Exo

---

### Post by Tibuda on 2011-05-14
> **WorMzy said:**
> Just enable the pwfeedback option in visudo.

e.g.

```
Defaults timestamp_timeout=0,editor=/usr/bin/vim:/usr/bin/vi:/usr/bin/nano,**pwfeedback**
```

[IMG]http://img36.imageshack.us/img36/5050/screenshot100511192752.png[/IMG]

hey, thanks for that!

---

### Post by adroitster on 2012-04-14
There is a solution here : [http://whyareyoureadingthisurl.wordpress.com/2010/05/16/sudo-and-password-feedback/](http://whyareyoureadingthisurl.wordpress.com/2010/05/16/sudo-and-password-feedback/)

---

### Post by aysiu on 2012-04-14
> **adroitster said:**
> There is a solution here : [http://whyareyoureadingthisurl.wordpress.com/2010/05/16/sudo-and-password-feedback/](http://whyareyoureadingthisurl.wordpress.com/2010/05/16/sudo-and-password-feedback/)
Unfortunately, that's not the solution, because part of the problem is the confusion it causes new users. New users won't change the default. The solution is to make the default show visual feedback and then allow people who believe it to be a "security feature" (it isn't, as I've explained multiple times) to turn the visual feedback off.

---

