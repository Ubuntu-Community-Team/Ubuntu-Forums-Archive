---
title: "safe-rm installed by default."
date: 2011-05-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ikt on 2011-05-23
> This package provides a tool intended to prevent the accidental deletion of important files by replacing rm with a wrapper, which checks the given arguments against a configurable blacklist of files and directories that should never be removed. Users who attempt to delete one of these protected files or directories will not be able to do so and will be shown a warning message instead. Protected paths can be set both at the site and user levels. (dpkg package description)

[https://launchpad.net/safe-rm](https://launchpad.net/safe-rm)

20KB's but provides an extra layer of protection against not only accidental deletions but social engineering as well, the error message could be a bit more clear about how important the directory is.

---

### Post by MacUntu on 2011-05-23
Personally I think this kind of over-protection is counter-productive as it will lead to less caution when performing critical tasks.

Would you let a safe-rm user do command-line stuff on your Ubuntu box w/o safe-rm?

---

### Post by ikt on 2011-05-23
> **MacUntu said:**
> Would you let a safe-rm user do command-line stuff on your Ubuntu box w/o safe-rm?

huh?

I'm saying it should be installed by default, therefore my ubuntu box would have it?

Also yes, by the same argument would you let a 'sudo' user have root access on your ubuntu box?

---

### Post by xebian on 2011-05-23
> **ikt said:**
> [https://launchpad.net/safe-rm](https://launchpad.net/safe-rm)

20KB's but provides an extra layer of protection against not only accidental deletions but social engineering as well, the error message could be a bit more clear about how important the directory is.

alias rm='rm -i' is all you need

---

### Post by MacUntu on 2011-05-23
> **ikt said:**
> Also yes, by the same argument would you let a 'sudo' user have root access on your ubuntu box?

That's not exactly comparable as 'sudo' isn't a wrapper for anything. With safe-rm your 'rm' command gets replaced, so you always use the little magic. There's a good chance of forgetting about it - that's not possible with something you need to add like 'sudo'.

> **xebian said:**
> alias rm='rm -i' is all you need

Good luck with using scripts. :P

---

### Post by xebian on 2011-05-23
> **ikt said:**
> huh?

I'm saying it should be installed by default, therefore my ubuntu box would have it?

Also yes, by the same argument would you let a 'sudo' user have root access on your ubuntu box?

Why would one (1) user thinks he/she needs it forces all others to have it when they don't have need for it?

---

### Post by xebian on 2011-05-23
> **MacUntu said:**
> That's not exactly comparable as 'sudo' isn't a wrapper for anything. With safe-rm your 'rm' command gets replaced, so you always use the little magic. There's a good chance of forgetting about it - that's not possible with something you need to add like 'sudo'.



Good luck with using scripts. :P

What scripts?  That is just an alias reimplementation of rm to always prompt.  Just 1 line addition to .bashrc or .bash_aliases

---

### Post by ikt on 2011-05-23
> **xebian said:**
> alias rm='rm -i' is all you need

prompting doesn't work it annoys, a better solution would be an alias which moves all data to the trash.

---

### Post by arpanaut on 2011-05-23
Thank you, NO, I will be responsible for my own system.

---

### Post by ikt on 2011-05-23
> **arpanaut said:**
> Thank you, NO, I will be responsible for my own system.

I'm not thinking of you when I suggest this, I'm thinking of users who are unaware of what rm -rf means and does.

> **xebian said:**
> Why would one (1) user thinks he/she needs it forces all others to have it when they don't have need for it?

All users have a need for it, it's useful in preventing the accidental deletion of important files, in addition it can boost security. I don't see a downside.

---

### Post by MacUntu on 2011-05-23
> **xebian said:**
> What scripts?
Scripts that you run in a bash using that alias. They will stall whenever they remove something. That would certainly drive me crazy.

---

### Post by ikt on 2011-05-23
> **MacUntu said:**
> Scripts that you run in a bash using that alias. They will stall whenever they remove something. That would certainly drive me crazy.

If you can make a script, I'm sure you can edit a text file.

---

### Post by arpanaut on 2011-05-23
Train and educate new users, don't constrain and limit the computing experience for ALL users.
Safe computing, like safe sex is a personal responsibility!

Offer it, advise about it, don't make it a default at the expense of other users.
IMHO too much nanny crap creeping into Ubuntu/Linux as it is.

---

### Post by ikt on 2011-05-23
> **arpanaut said:**
> Train and educate new users

And what do you think the script/safe-rm is doing?

> **arpanaut said:**
> 
 don't constrain and limit the computing experience for ALL users. Safe computing, like safe sex is a personal responsibility!

The "contain and limit" is no more than the fact root user is disabled in favour of sudo.

> **arpanaut said:**
> 
Offer it, advise about it, don't make it a default at the expense of other users.
IMHO too much nanny crap creeping into Ubuntu/Linux as it is.

Ubuntu isn't going to get to no.1 by appealing to linux users, I think your princess might be in the other castle?

---

### Post by arpanaut on 2011-05-24
Hey, my apologies, I woke up in a bad mood this morning.
After doing treble service calls today, and making some good money...

Well, do whatever,  lame users are my moneymaker.
I try to inform, I try to educate but I will not be reluctant to  profit from those that won't  listen.

Yes, I am referring to windows users in general, but users who continue to exhibit poor computing habits, sorry I have no sympathy,   

My question is... Are the distributors of an OS responsible for the protecting  users from their own stupidity  and unwillingness to educate themselves about the environment they are operating in?

Linux offers, at defaults. a very safe computing experience. Stick to supported repositories and you are very much good to go.
If, as with any other OS,  you bring in any "unofficial" sources. Buyer Beware. ( Personally I have had almost ZERO problems with official repositories)

I guess what I'm saying, is that trying to protect the system from users that "don't have a clue" is a futile effort and an encumbrance to serious users. 

Ubuntu's goals are admirable, good luck. Trying to change the "average"  users behaviour is IMHO  "pie in the sky", 

Ain't gonna happen.

Maybe I'm right, Maybe I'm wrong: I'm done with this discussion!
In the end the user is responsible for themselves.

---

### Post by meborc on 2011-05-24
this reminds me of the ctrl+alt+backspace discussion a while back... (i still keep hitting those keys expecting to restart X)

one of the things about linux that i like is the fact that i am in full control. it gives me freedom and also responsibility.

I would rather not have safe-rm on my machine, but that is just my personal opinion. I can see how it could help to save some data for someone, but for me it would only be a reminder of "clippy" :)

BTW - people who are used to clicking YES-YES-YES in windows, will no doubt just proceed without reading the warnings anyway

---

### Post by ssam on 2011-05-24
i thought ubuntu's rm already had a bit of protection, though i don't want to test it.

> **meborc said:**
> this reminds me of the ctrl+alt+backspace discussion a while back... (i still keep hitting those keys expecting to restart X)


try alt+sysrq+k (not right now). it is more reliable than ctrl+alt+backspace.

---

### Post by ikt on 2011-05-24
> **meborc said:**
> this reminds me of the ctrl+alt+backspace discussion a while back... (i still keep hitting those keys expecting to restart X)

Yes exactly.

> **meborc said:**
> 
one of the things about linux that i like is the fact that i am in full control. it gives me freedom and also responsibility.


You're not losing anything, you can edit the config file so you can rm -rf all you want.

> **meborc said:**
> 
BTW - people who are used to clicking YES-YES-YES in windows, will no doubt just proceed without reading the warnings anyway

Which is why I think even an alias which moves all the data to the trash/recycle bin first would be as good as if not better than safe-rm, you can't stop people from running commands, but you can inform people and warn them about potentially dangerous situations.

---

### Post by cariboo on 2011-05-24
rm is not easily discoverable for a new users on their own, they may run into the command on a forum or in documentation. On this forum any one suggesting rm -f will immediately be reported, and most people posting in that thread will warn against using the command.

Personally I don't see the need for safe-rm.

---

### Post by meborc on 2011-05-25
> **ikt said:**
> ...

Which is why I think even an alias which moves all the data to the trash/recycle bin first would be as good as if not better than safe-rm, you can't stop people from running commands, but you can inform people and warn them about potentially dangerous situations.

I see your point. 

But just as an example: I generate huge files. Neutronic calculations result in output of hundreds of megabytes of binary files. I really don't want to move them to trash. After I have done necessary operations, I just want to permanently delete them.

I guess I can always change conf files to get the system to operate to my needs, BUT it seems that more and more tweaks are needed with each release.

I hope shift+delete will still be there by 11.10 :D

---

### Post by coffeecat on 2011-05-25
> **arpanaut said:**
>  I guess what I'm saying, is that trying to protect the system from users  that "don't have a clue" is a futile effort and an encumbrance to  serious users. 

In the history of Unix/Linux there have been several experienced sysadmins who have...

> **arpanaut said:**
> woke up in a bad mood

... or perhaps who were just tired and ran, as root, 'rm -rf /path/to/unwanted/directory'. Except that they accidentally inserted a space between '/' and 'path' and guess what happened? :( Even 'serious' users need protecting from themselves at times.

On a slightly related note, and slightly off-topic, I sometimes wonder if it would be possible to have something similar for the chmod command, so that 'sudo chmod 777 -R /etc' would return the message, "you really don't want to do that!" Not necessary? Oh, yes! Threads where the OP has chmod 777'd or similar a system directory or the whole filesystem pop up with monotonous and depressing regularity.

---

### Post by Framli on 2011-05-25
> **coffeecat said:**
> ... or perhaps who were just tired and ran, as root, 'rm -rf /path/to/unwanted/directory'. Except that they accidentally inserted a space between '/' and 'path' and guess what happened? :( Even 'serious' users need protecting from themselves at times.

Luckily for the tired user, rm has --preserve-root by default.
```
$ rm --help | grep root
      --no-preserve-root  do not treat `/' specially
      --preserve-root   do not remove `/' **(default)**

$ #let's hope this really works, I'm testing this at work on my production machine :S

$ rm -rf /
rm: it is dangerous to operate recursively on `/'
rm: use --no-preserve-root to override this failsafe

$ #Yay :P

```

---

### Post by meborc on 2011-05-25
> **Framli said:**
> Luckily for the tired user, rm has --preserve-root by default.
```
$ rm --help | grep root
      --no-preserve-root  do not treat `/' specially
      --preserve-root   do not remove `/' **(default)**

$ #let's hope this really works, I'm testing this at work on my production machine :S

$ rm -rf /
rm: it is dangerous to operate recursively on `/'
rm: use --no-preserve-root to override this failsafe

$ #Yay :P

```

Dude... that was WAY scary... my heart-rate went up :D

---

### Post by coffeecat on 2011-05-25
> **Framli said:**
> Luckily for the tired user, rm has --preserve-root by default.

I'm glad to hear it. :)

---

### Post by arpanaut on 2011-05-25
> ... or perhaps who were just tired and ran, as root, 'rm -rf  /path/to/unwanted/directory'. Except that they accidentally inserted a  space between '/' and 'path' and guess what happened? :sad: Even 'serious' users need protecting from themselves at times.

Okay, I see your point.
I stand corrected!

So, Ignorance is not Bliss
Better Safe than Sorry...

---

### Post by teh603 on 2011-05-25
> **ikt said:**
> 20KB's but provides an extra layer of protection against not only accidental deletions but social engineering as well
The social engineering protection is my big concern right now. My parents have an AspireRevo running either 10.04 or 10.10, and my mom encountered a social engineering "virus warning" redirect script that tried to install windows malware. Thankfully, she asked me how she was supposed to set up antivirus protection.

We had a good laugh about it, but I'm still a little worried about what could happen...

---

### Post by TerminX on 2011-05-25
> **Framli said:**
> Luckily for the tired user, rm has --preserve-root by default.
```
$ rm --help | grep root
      --no-preserve-root  do not treat `/' specially
      --preserve-root   do not remove `/' **(default)**

$ #let's hope this really works, I'm testing this at work on my production machine :S

$ rm -rf /
rm: it is dangerous to operate recursively on `/'
rm: use --no-preserve-root to override this failsafe

$ #Yay :P

```
Next time you do something like that, you might consider doing it in a chroot.  You know, just in case it doesn't work.  Heh.

---

### Post by Framli on 2011-05-25
Nobody has noticed I wasn't root for that "dangerous" experiment :P

---

### Post by seeker5528 on 2011-05-25
> **coffeecat said:**
> ... or perhaps who were just tired and ran, as root, 'rm -rf /path/to/unwanted/directory'. Except that they accidentally inserted a space between '/' and 'path' and guess what happened? :( Even 'serious' users need protecting from themselves at times.

I would expect serious users/admins would accept that it was their fault for being careless, and I suspect may have looked to find where the real rm gets stashed and been using it directly even if safe-rm was installed.

But then again I would expect the serious user would more commonly be using tab completion, so mistyping, having an extra space, etc... should not be an issue.

Then there is always the ```
cd /to/the/place/the/directory/actually/lives/
rm -rf directory
```
option or ```
cd /to/directory/
rm -rf *
cd ..
rmdir directory
```

And if safe-rm was installed by default how many packages would need removal scripts to be updated to point to the real 'rm' so *they* can delete the files they need.

Later, Seeker

---

### Post by Mr. Picklesworth on 2011-05-25
I think the social engineering angle is a little dubious. Okay, you have griefers, but a serious social engineering attack is *not* interested in destroying the target system. A serious social engineering attack wants the target system in working order so either the system or the user can be exploited. Deleting root isn't going to help.

And on a different note, rm was kind enough to warn me when I did a recursive delete on a deep collection of files just recently. It may have been an alias that came with zsh, though; I didn't investigate ;)

---

### Post by ronacc on 2011-05-25
all in all its just another brick in the wall , or another step in the dumbing down of ubuntu .

---

### Post by sisco311 on 2011-05-25
> **ikt said:**
> [https://launchpad.net/safe-rm](https://launchpad.net/safe-rm)

20KB's but provides an extra layer of protection against not only accidental deletions but social engineering as well, the error message could be a bit more clear about how important the directory is.

Why do we need a wrapper for this? An Apparmor profile could do the same thing. Or do I miss something?

---

### Post by Telengard C64 on 2011-05-25
[trash-cli](http://manpages.ubuntu.com/manpages/lucid/en/man1/trash.1.html) has been in the repos since Lucid. Why isn't this incorporated as the default handler for **rm**?

---

### Post by teh603 on 2011-05-25
> **Mr. Picklesworth said:**
> I think the social engineering angle is a little dubious. Okay, you have griefers, but a serious social engineering attack is *not* interested in destroying the target system. A serious social engineering attack wants the target system in working order so either the system or the user can be exploited. Deleting root isn't going to help.

And on a different note, rm was kind enough to warn me when I did a recursive delete on a deep collection of files just recently. It may have been an alias that came with zsh, though; I didn't investigate ;)You underestimate the immaturity of some of these people. Its like trade chat on WOW; it doesn't matter that they didn't gain control, but that someone was actually gullible enough to run their script.

---

### Post by meborc on 2011-05-26
i think we are still concentrating on the wrong issue here. the suggestion was that people with no knowledge about cli commands or people who are careless can be saved with this tool.

at the same time, Ubuntu is constantly reminding us that cli is not necessary any more. everything can be done with point-click gui. so why are we worried about "rm" again? 

the number of people that will be affected by safe-rm in a positive way would not outnumber the people who would consider it an extra nuisance. (my estimate, probably incorrect)

basically it is saying "you are not smart enough to use your own system so we will not give you full rights to do what you want"

... before you kill me - i understand that it is not that drastic and we have conf files to change that and etc... i just don't want to be handled like a spoiled brat :D

---

### Post by teh603 on 2011-05-26
> **meborc said:**
> i think we are still concentrating on the wrong issue here. the suggestion was that people with no knowledge about cli commands or people who are careless can be saved with this tool.

at the same time, Ubuntu is constantly reminding us that cli is not necessary any more. everything can be done with point-click gui. so why are we worried about "rm" again? 

the number of people that will be affected by safe-rm in a positive way would not outnumber the people who would consider it an extra nuisance. (my estimate, probably incorrect)

basically it is saying "you are not smart enough to use your own system so we will not give you full rights to do what you want"

... before you kill me - i understand that it is not that drastic and we have conf files to change that and etc... i just don't want to be handled like a spoiled brat :DFor that to work, we need to get people using the GUI more. I've seen too many people giving advice based on the command prompt, and not enough for the GUI. We also don't always have people giving advice for the right GUI; people for Ubuntu trying to give advice to someone running Kubuntu, for instance.

It'd also go a hella long way to solving Bug #1, too. One of the more common complaints I hear is "ZOMG command prompt! No way!"

---

### Post by ronacc on 2011-05-26
> **teh603 said:**
> For that to work, we need to get people using the GUI more. I've seen too many people giving advice based on the command prompt, and not enough for the GUI. We also don't always have people giving advice for the right GUI; people for Ubuntu trying to give advice to someone running Kubuntu, for instance.

It'd also go a hella long way to solving Bug #1, too. One of the more common complaints I hear is "ZOMG command prompt! No way!"

as much as I love GUI's they are NOT the best tool for everything . Keep in mind that neither MS nor Apple has done away with it completely . Those who refuse the cmd line totally  doom themselves to having less than complete control over their systems . GUI's and the CLI are not mutually exclusive they are compliments for each other not replacements .

---

### Post by ikt on 2011-05-26
> **cariboo907 said:**
> rm is not easily discoverable for a new users on their own, they may run into the command on a forum or in documentation.

I take it you didn't see this?

[http://i.imgur.com/qlVdK.png](http://i.imgur.com/qlVdK.png)

I'm just saying it's potentially a cause for much headache, and I think a small step could make a difference.


> **meborc said:**
> I see your point. 

But just as an example: I generate huge files. Neutronic calculations result in output of hundreds of megabytes of binary files. I really don't want to move them to trash. After I have done necessary operations, I just want to permanently delete them.

Yeah but I'm saying you can just change 1 line in a file and then everything runs like you're used to, you can delete files like normal, and joe average is 1 step further away from accidentally deleting his entire home directory.

> **meborc said:**
> 
I guess I can always change conf files to get the system to operate to my needs, BUT it seems that more and more tweaks are needed with each release.


I've had less and less tweaks tbh(not necessarily a good thing), but if you do have many conf files you need to change, why not make a script? When you install ubuntu just run the script and it copies all the conf files to the right locations. That's one of the great things about linux :D

> **coffeecat said:**
> Threads where the OP has chmod 777'd or similar a system directory or the whole filesystem pop up with monotonous and depressing regularity.

Really? I don't remember chmoding to 777 for a while now or recommending people to do so, especially since I'm aware of "chmod a+rwX".

In fact the only post I can find where I mention chmod at all is:

[http://ubuntuforums.org/showpost.php?p=6007116&postcount=9](http://ubuntuforums.org/showpost.php?p=6007116&postcount=9)

way back in 2008, it's not a system directory and I even preface it with "It's not good to use this often", I'd really like to see where I have because I'll be fixing that right away.

> **meborc said:**
> at the same time, Ubuntu is constantly reminding us that cli is not necessary any more. everything can be done with point-click gui. so why are we worried about "rm" again? 

false dilemma :P

---

### Post by coffeecat on 2011-05-26
> **ikt said:**
> Really? I don't remember chmoding to 777 for a while now or recommending people to do so, especially since I'm aware of "chmod a+rwX".

@ikt, I didn't mean you, although I can see how you misunderstood what I was trying to say.  There have been many threads where the **OPs of those threads** have chmodded system directories.

---

### Post by ikt on 2011-05-26
> **coffeecat said:**
> @ikt, I didn't mean you, although I can see how you misunderstood what I was trying to say.  There have been many threads where the **OPs of those threads** have chmodded system directories.

*phew* I get you!

---

### Post by ronacc on 2011-05-26
kindly explain to me exactly what is wrong with chmoding ANY directory on MY system to anything I darn well please . It is MY system , to be operated in the manner I desire . I installed it and I will wipe it and install something else at any time it pleases me to do so . That being the case how is adjusting the permissions "wrong" .

---

### Post by coffeecat on 2011-05-26
> **ronacc said:**
> kindly explain to me exactly what is wrong with chmoding ANY directory on MY system to anything I darn well please . It is MY system , to be operated in the manner I desire . I installed it and I will wipe it and install something else at any time it pleases me to do so . That being the case how is adjusting the permissions "wrong" .

You are, of course, entitled to run 'sudo chmod -R 777 /etc' (as I have seen, or similar, in more than one thread) on your own system. It's yours to do with what you want. It's not my place to tell you what you should or should not do on your own system. But if you want a **working** system, you might want to think twice before doing so.

---

### Post by seeker5528 on 2011-05-26
> **ikt said:**
> Yeah but I'm saying you can just change 1 line in a file and then everything runs like you're used to, you can delete files like normal, and joe average is 1 step further away from accidentally deleting his entire home directory.

It's not like typing this stuff in at the command line is all that quick and instant compared to doing a couple of clicks in a file manager, so combined with the factor that "Joe Average" probably isn't using the command line much anyway, it doesn't seem like Joe Average accidentally deleting his entire home directory would be a very common thing.

But on the other hand I don't understand why people need a warning telling them that wrapping the cord of the window blinds around your neck is a bad idea.:P

Later, Seeker

---

