---
title: "aptitude or apt-get??? Again..."
date: 2009-12-16
forum: Recurring Discussions
---

### Post by switch10 on 2009-12-16
I've switched between apt-get and aptitude so many times I can't remember.  I've finally settled on apt-get, until the other day..  I just found out that aptitude removes all of the dependent packages along with the program you are removing.  Why doesn't apt-get do this??  Should I switch back to aptitude? 

Thanks

Dave

---

### Post by diesch on 2009-12-16
There's ```
apt-get autoremove
```> autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

---

### Post by jamieleshaw on 2009-12-16
aptitude has alot more functions like search & reinstall etc.
but I don't know Synaptic And Software Centre use apt-get

---

### Post by n0glu3 on 2009-12-16
Yes, aptitude is better.

---

### Post by slakkie on 2009-12-16
They all use the same, apt.

I prefer aptitude because I don't have to type in two command just to remove dependencies. Although apt-get has some features aptitude doesn't have (apt-get source for example).

---

### Post by humphreybc on 2009-12-16
I suggest using aptitude, it's newer and has more features than apt-get. And, you answered your own question - it automatically removes unused dependencies when you remove a program, which can be quite useful.

One thing I have noticed however is that when downloading updates, if the internet connection is interrupted and either time out, apt-get will continue off where it stopped (eg. 56%) whereas aptitude starts again from 0% - which can be a pain if you're on an unstable connection.

---

### Post by darkestfright on 2009-12-16
Apt-get removes all programs that depend on an uninstalled program.
If you want to remove uneeded dependencies for an uninstalled program, use

`apt-get autoremove'

Works like a charm.

I was under the impression, that aptitude was all but abandoned a while ago, and the apt-get is now the preferred way to manage packages on a debian-like system now.

---

### Post by switch10 on 2009-12-16
> **diesch said:**
> There's ```
apt-get autoremove
```

I removed audacity with both commands, for example.  aptitude was going to free up several megabytes, while apt-get autoremove, would only free up several hundred kilobytes.  There were also more packages being removed with aptitude....

---

### Post by baddog144 on 2009-12-16
I use apt-get and apt-cache. *shrug* They work fine for me.

---

### Post by wojox on 2009-12-16
> **slakkie said:**
> They all use the same, apt.

I prefer aptitude because I don't have to type in two command just to remove dependencies. Although apt-get has some features aptitude doesn't have (apt-get source for example).

I would of figured you of all people would have written a bash script for that:

```

#!/bin/bash

echo -e "Cleaning apt cache..."
sudo apt-get autoremove
apt-get autoclean
apt-get clean
echo -e "Script Finished!"

```

---

### Post by northern lights on 2009-12-16
[google: aptitude apt-get site:ubuntuforums.org]("http://www.google.de/search?q=aptitude+apt-get+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")
[http://ubuntuforums.org/showthread.php?t=846659]("http://ubuntuforums.org/showthread.php?t=846659")
[http://ubuntuforums.org/showthread.php?p=8510072]("http://ubuntuforums.org/showthread.php?p=8510072")
[http://ubuntuforums.org/showthread.php?t=790141]("http://ubuntuforums.org/showthread.php?t=790141")
etc. pp.

---

### Post by SlugSlug on 2009-12-16
$aptitude --help
                  This aptitude does not have Super Cow Powers.




$apt-get --help
                       This APT has Super Cow Powers.




:popcorn::popcorn::popcorn:

---

### Post by jamieleshaw on 2009-12-16
I think aptitude is better, just to add to my previous comment.

---

### Post by chillyomi on 2009-12-16
Well I use aptitude never used apt-get

---

### Post by slakkie on 2009-12-16
> **wojox said:**
> I would of figured you of all people would have written a bash script for that:

```

#!/bin/bash

echo -e "Cleaning apt cache..."
sudo apt-get autoremove
apt-get autoclean
apt-get clean
echo -e "Script Finished!"

```

I have ;)

```

purge_pkg() {
    sudo aptitude purge $(dpkg -l | tail -n +6 | grep -v '^ii' | awk '{print $2}')
    sudo aptitude clean
}      

```

---

### Post by lisati on 2009-12-16
What about this? 
```
apt-get moo
```

---

### Post by MooPi on 2009-12-16
I've used apt-get for so long It's second nature for me. I know aptitude has more features but feels awkward to me. If I'm really searching for something new or unknown I pop open Synaptic.

---

### Post by ubudog on 2009-12-16
> **diesch said:**
> There's ```
apt-get autoremove
```

Yeah should work.

---

### Post by Guitar John on 2009-12-16
> **lisati said:**
> What about this? 
```
apt-get moo
```

moo?

---

### Post by lisati on 2009-12-17
> **Guitar John said:**
> moo?

It's an Easter Egg.

---

### Post by ubudog on 2009-12-17
> **SlugSlug said:**
> $aptitude --help
                  This aptitude does not have Super Cow Powers.




$apt-get --help
                       This APT has Super Cow Powers.




:popcorn::popcorn::popcorn:

Super Cow Powers?

---

### Post by lisati on 2009-12-17
> **ubudog said:**
> Super Cow Powers?

The following examples will illustrate the super-cow powers.
```
apt-get moo
aptitude moo

```

---

### Post by ubudog on 2009-12-17
Oh, I see.

---

### Post by ubudog on 2009-12-17
:lolflag:

---

### Post by realzippy on 2009-12-17
aptitude help 
aptitude moo 
aptitude moo -v 
aptitude moo -vv 
aptitude moo -vvv 
aptitude moo -vvvv 
and so on..

---

### Post by FuturePilot on 2009-12-17
> **slakkie said:**
> They all use the same, apt.

I prefer aptitude because I don't have to type in two command just to remove dependencies. Although apt-get has some features aptitude doesn't have (apt-get source for example).

No, they all use the same dpkg.

Aptitude doesn't have an equivalent of "apt-get source" so, bye aptitude.

---

### Post by RiceMonster on 2009-12-17
Last time I used either, I preferred apt, as I really hated the way aptitude puked output all over the terminal.

---

### Post by Xbehave on 2009-12-17
> No, they all use the same dpkg.
aptitude will autoremove depreciated dependancies
say you install firefox, then remove firefox, apt will not remove xulrunner, but aptitude will

Aptitude handles breakages much better, the tui is great for complex setups.

If i am doing something simple or on a basic install with no ppas then i tend to use apt, but whenever i have ppas or multiple repos and am doing anything that involves packages from the ppas i go to the aptitude to make sure nothing goes wrong.

aptitude: 
[LIST]
[*]better conflict resolution
[*]handles downgrades/pinning easily
[*]reinstall packages easily
[*]purges uninstalled packages
[/LIST]

apt-get:
[LIST]
[*]source - Download source archives 
[*]build-dep - Configure build-dependencies for source packages
[/LIST]

I don't think there is much of a conflict between them, it would be nice if aptitude could install build-dep and source (maybe its possible), but for now aptitude is a more powerful tool for most stuff while apt is simpler but still needed in some cases. Aptitude is also bigger (10M v 5M) and has a lot more dependencies (10 v 3), so it will never replace apt.

---

### Post by Hallvor on 2009-12-17
I choose aptitude because of superior dependency handling, and if you type ```
aptitude
``` in the terminal you get a nice little surprise. ;)

---

### Post by ubudog on 2009-12-17
> **Hallvor said:**
> I choose aptitude because of superior dependency handling, and if you type ```
aptitude
``` in the terminal you get a nice little surprise. ;)

Yeah, cool.

---

### Post by NoaHall on 2009-12-17
> **jamieleshaw said:**
> aptitude has alot more functions like search & reinstall etc.
but I don't know Synaptic And Software Centre use apt-get

apt-cache search name

I use apt, aptitude is a bit... weird?

---

### Post by sertse on 2009-12-17
Personally It's silly in the the first place, that much a fundamental action (package management) is a recurring discussion. Linux devs are a bit silly in introducing this sort of situation.

It really should be a tech support issue, with a clear "official" directive imo...

---

### Post by Xbehave on 2009-12-17
> **sertse said:**
> Personally It's silly in the the first place, that much a fundamental action (package management) is a recurring discussion. Linux devs are a bit silly in introducing this sort of situation.

It really should be a tech support issue, with a clear "official" directive imo...
Both have their purposes and advantages, there is no 1 right answer.
1) apt is more lightweight, so probably marginally faster vs aptitude is bigger but has more features
2) apt has less features so if you tell it to do something it will pass or fail, this is good when giving support vs aptitude deals with errors for you or prompts you to solve them easily.

These are mutually exclusive options and which choice you make comes down to the usage case and personal preference.

If there is a directive it would be to use aptitude over apt (i think there is a 'directive' stating as much somewhere) because it fixes more problems, however nobody cares that much. Hell I'm a big fan of aptitude for most usage as it would avoid a lot of issues people complain about, however I'm not going to waste my time trying to convince people to use it over apt.

---

### Post by switch10 on 2009-12-18
I guess I'm going to switch back to aptitude then.  I do like the fact that it removes dependencies, and it's slightly easier to type :)

thanks for the replies..

Dave

---

### Post by l-x-l on 2009-12-18
Aptitude for me all the way. Much more feature packed.

---

### Post by ratcheer on 2009-12-18
I have read several articles and blog pages and have been convinced to use and stick with aptitude.

Tim

---

### Post by Guitar John on 2009-12-19
> **lisati said:**
> It's an Easter Egg.

Never knew about the Easter Eggs.
A quick Google [search]("http://blog.fasttracksites.com/index.php?p=viewentry&id=5")....

Hit Alt + F2 on my wife's computer
Type in:
```
free the fish
```

I expect that sometime tomorrow, I'll be hearing "...why is there a fish swimming across my screen?"  :-\"

---

### Post by CharlesA on 2009-12-20
I've always used apt-get since aptitude seems a bit clunky to me.

I can see how aptitude would be easier to use, but I'll just stick with apt-get. ;)

---

### Post by ubudog on 2009-12-20
> **Guitar John said:**
> Never knew about the Easter Eggs.
A quick Google [search]("http://blog.fasttracksites.com/index.php?p=viewentry&id=5")....

Hit Alt + F2 on my wife's computer
Type in:
```
free the fish
```

I expect that sometime tomorrow, I'll be hearing "...why is there a fish swimming across my screen?"  :-\"

:lolflag::lolflag:  Looks pretty cool with the compiz rain effect.

---

### Post by ubudog on 2009-12-20
> **Guitar John said:**
> Never knew about the Easter Eggs.
A quick Google [search]("http://blog.fasttracksites.com/index.php?p=viewentry&id=5")....

Hit Alt + F2 on my wife's computer
Type in:
```
free the fish
```

I expect that sometime tomorrow, I'll be hearing "...why is there a fish swimming across my screen?"  :-\"

How do I kill the process?

---

### Post by Guitar John on 2009-12-20
> **ubudog said:**
> How do I kill the process?

```
pkill gnome-panel
```

[Your bars will disappear and then come back later]("http://blog.fasttracksites.com/index.php?p=viewentry&id=5").

Follow the link, and look under the heading:
5. Gnome Fun

By the way, it was as funny as I thought it would be.

---

### Post by ubudog on 2009-12-20
OK, thanks.  It's fixed now.

---

