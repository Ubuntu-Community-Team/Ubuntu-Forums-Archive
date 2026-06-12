---
title: "Recommend a tiling WM/Distro?"
date: 2011-10-07
forum: Recurring Discussions
---

### Post by IWantFroyo on 2011-10-07
I've been using Debian 6 for a while, but I don't think it fits my needs anymore.
Here are my requirements:
-I use vim for a lot of my work now. So I have to have a good way to quickly open it.
-Switching between full screen apps.
-Light.

I've been looking into "tiling" window managers like evilwm, but I'm not sure which one to try.

---

### Post by ninjaaron on 2011-10-07
> **IWantFroyo said:**
> I've been using Debian 6 for a while, but I don't think it fits my needs anymore.
Here are my requirements:
-I use vim for a lot of my work now. So I have to have a good way to quickly open it.
-Switching between full screen apps.
-Light.

I've been looking into "tiling" window managers like evilwm, but I'm not sure which one to try.

evilwm isn't tiling.  Scrotwm is.  That's what I'm using, and I love it. you can hit super+shift+enter to open a terminal, and type vim. You could also make a custom command to launch a terminal with vim already open (ie: `whatever-terminal -e vim`).  There are several helpful folks around here that helped me with it when I started, and I know how to do it now too, so I can also help. If you want gvim, you can launch it with the dmenu by pressing  super+p and starting to type `gvim.`  There is a package for it in Debian.

'awesome' is another popular tiling window manager, but it's configuration file is a lua script, which puts some people off (though it's not so terrible to learn).  Other popular tiling window managers with a more difficult learning curve, but also more options are DWM and Xmonad, both of which are configured by editing and recompileing their source code. Scrotwm was inspired by these two window managers, but attempts to make them easier to configure.

If you want things like a taskbar, Awesome is probably a little easier.  You can get a lot of task-bar type information in your bar via bash script or conky, however, in scrotwm. It just isn't interactive.  Simplicity is the keyword with scrotwm, so it's quite bare-bonesb.  It's not as bare-bones as evilwm.  It manages an info bar, launching apps and keybindings. Of course, it also manages your windows.  Evil just manages windows, and that's it.  Awesome, on the other hand, is approaching a more complete DE, which you may like.  If you think you'd like to try DWM or Xmonad, you'll have to ask someone else.  I run away screaming whenever anyone mentions them.  Too l33t for me.

[edit]
I don't think there is such a thing as a 'tiling distro,' though I hear that Kwin, the wm for KDE, has built in tiling features, so I guess any KDE distro would be a 'tiling distro,' like OpenSUSE or Chakra.

As far as distros where a lot of people use tiling wm's, It's really poplular with at lot of users of the BSD's (where a lot of this stuff originally comes from).  They are also popular with Arch users, like me, but Arch is basically Linux wishing it was BSD.  As such, the Arch Wiki is helpful for setting up tiling window managers.

---

### Post by ilovelinux33467 on 2011-10-07
i3, awesome and Xmonad are my favourites.

---

### Post by m_duck on 2011-10-07
I'd probably recommend DWM first because its pretty simple and has quite sane defaults IMHO, so doesn't really *need* reconfiguring straight away. Having said that it isn't difficult to configure per se, but one must edit its source code (in C) to modify it, but that really isn't as daunting as it sounds.

My personal favourite tiler is WMFS. OOTB the keybinds are a bit strange but the configuration files are simple and flexible. Additionally it comes with a statusbar/tray (which can be disabled separately) and extra information can be added to it easily.

Of course if you want the most flexibility and power Awesome or XMonad are the direction to head but take more effort to configure - the former is configured in Lua (as ningaaron said) and the latter in Haskell. Of the two, I prefer XMonad.

I'd certainly recommend installing at least a few of them to see which you like best. I hated tiling WMs when I first tried them but after coming back to them a few times and trying different ones I enjoy using them now.

EDIT: I've only mentioned dynamic tilers here - some people prefer manual tiling. I am not one of them...

---

### Post by dniMretsaM on 2011-10-07
KDE (Kwin window manager) has built in tiling (full, left, right, left up, left down, right up, right down). Each position has it's own keyboard shortcut. And it's customizable in about a 1000 other ways, so it's pretty awesome. As for quickly opening Vim, I would suggest creating a custom launcher for it. Or Alt+F2 -> vim -> Enter. For switching between windows, use a task bar or a keyboard shortcut to switch between windows (default is Alt+Tab). I would also suggest using multiple desktops.

---

### Post by IWantFroyo on 2011-10-07
> **ninjaaron said:**
> evilwm isn't tiling. Scrotwm is.

:facepalm:

I suppose that shows how little I really know about this stuff.
Thanks for all your replies, though! Especially thanks to ninjaaron. Installing scrotwm over my Debian right now. If I like it I'll probably switch from Debian to something more barebones, and install on that.

---

### Post by ninjaaron on 2011-10-07
> **IWantFroyo said:**
> :facepalm:

I suppose that shows how little I really know about this stuff.
Thanks for all your replies, though! Especially thanks to ninjaaron. Installing scrotwm over my Debian right now. If I like it I'll probably switch from Debian to something more barebones, and install on that.

Tip.  All those times when I said "super+[...]" will be alt+[...] by default in Debian.  It's a little bit older version than what I have, and the default has been changed.  You can change it super if you wish (Mod4) by editing the config file.  There is a line above all the keybindings that says something like...

```
modkey = Alt
```

... and you can change it to Mod4 or Ctrl (a bad idea) or even shift (a really bad idea), or a combination.  It's sort of a law that applications don't use super for anything, so it's often used by window managers, and I would recommend it, though Alt doesn't usually pose a big problem either.

Scrotwm also comes with vim-related bindings by default, so that will be nice for you.  Most of these WM's do, as they are sort of universal bindings known by most *nix heads.

---

### Post by matthew.ball on 2011-10-07
Hehehe, although ninjaaron is a definitive source on this matter (as is gutterslob), I'll just throw "stumpwm" into the mix.

It's written in common lisp (and modifications can be done "on-the-fly"), which is probably a foreign language to most people, but is rather easy to pick up (at least for small customisations).

I've found it works really nicely with Ubuntu (I would imagine, from the looks my .stumpwmrc file, it would work equally nicely for any Debian-spin though, including Debian).

---

### Post by krapp on 2011-10-07
Arch seems to have the greatest number of available WMs.
Debian has a fair number as does Ubuntu.

Most tiling WMs are easy to use, but a pain in the *** to set up. And they're far too bare-bone. I need a systray!

---

### Post by ninjaaron on 2011-10-08
> **matthew.ball said:**
> Hehehe, although ninjaaron is a definitive source on this matter (as is gutterslob), I'll just throw "stumpwm" into the mix.

Don't you DARE call me the definitive source and then put gutterslob in parentheses! ;)  Serously, that guy is in another league altogether.  He taught me everthing I know about scrotwm (well, mostly him, and some from the man page, and some from el_koraco).

I'm probably just the loudest user of scrotwm on the board, but there are plenty of other people who know as much and more than I do about it, and certainly much more about other tilers.

I might be able to tell some things about herbstluftwm soon, however, which not too many other people can do, if it doesn't defeat me first (it's a beast, but it gives almost infitite tiling options... which I'm not totally sure I want).  The config file for that is written in Bash, which makes it pretty simple, but the design is insanely complex and precise.  You can really feel how German it is when you use it (and I say that as an admirer of German craftsmanship).

---

### Post by IWantFroyo on 2011-10-08
I tried scrotwm on Debian, and although this seems pretty stupid, I couldn't figure out how to close my programs. Other than that, it looks and acts really nice. I would love this type of functionality in Openbox.

---

### Post by el_koraco on 2011-10-08
> **IWantFroyo said:**
> I tried scrotwm on Debian, and although this seems pretty stupid, I couldn't figure out how to close my programs. Other than that, it looks and acts really nice. I would love this type of functionality in Openbox.

You hit MOD + X
Don't figure it out on your own, the man page has everything, BSD manpages are known for thoroughness,

You can get tyling in Openbox with [pytyle ]("http://pytyle.com/wiki/Main_Page")

But really, the tilers are pretty similar once you get started, I think you only notice the differences later on. I use scrotwm, and I've tried ratpoison and dwm, both of which are good. I have scrot set up to my liking, which is why I'm really sticking with it.

If you want a distro set up with a tiler, there's Salix Ratpoison Edition.

---

### Post by IWantFroyo on 2011-10-08
> **el_koraco said:**
> You hit MOD + X
Don't figure it out on your own, the man page has everything, BSD manpages are known for thoroughness,

You can get tyling in Openbox with [pytyle ]("http://pytyle.com/wiki/Main_Page")

But really, the tilers are pretty similar once you get started, I think you only notice the differences later on. I use scrotwm, and I've tried ratpoison and dwm, both of which are good. I have scrot set up to my liking, which is why I'm really sticking with it.

If you want a distro set up with a tiler, there's Salix Ratpoison Edition.

Thanks. I really liked scrotwm, but I'll probably end up trying pytyle at some point.
I'm going to use Arch for this. scrotwm on Debian seemed a little weird.

---

### Post by sffvba[e0rt on 2011-10-08
Well, Salix 13.37 Ratpoison uses Ratpoison. No need to ever touch your [s]rat[/s] mouse again :p


404

PS - IWantFroyo, congrats on the Ubuntu Membership...

---

### Post by IWantFroyo on 2011-10-08
> **not found said:**
> Well, Salix 13.37 Ratpoison uses Ratpoison. No need to ever touch your [s]rat[/s] mouse again :p


404

PS - IWantFroyo, congrats on the Ubuntu Membership...

I was thinking of trying out ratpoison. Thanks. I suppose I'll be using Arch, however.

Thanks for the congratulations! :)

---

### Post by matthew.ball on 2011-10-08
> **ninjaaron said:**
> Don't you DARE call me the definitive source and then put gutterslob in parentheses! ;)  Serously, that guy is in another league altogether.  He taught me everthing I know about scrotwm (well, mostly him, and some from the man page, and some from el_koraco).

I'm probably just the loudest user of scrotwm on the board, but there are plenty of other people who know as much and more than I do about it, and certainly much more about other tilers.

I might be able to tell some things about herbstluftwm soon, however, which not too many other people can do, if it doesn't defeat me first (it's a beast, but it gives almost infitite tiling options... which I'm not totally sure I want).  The config file for that is written in Bash, which makes it pretty simple, but the design is insanely complex and precise.  You can really feel how German it is when you use it (and I say that as an admirer of German craftsmanship).
Hehehe, well I *would* have said gutterslob was the definitive source, and I was kind of surprised he hasn't posted anything here - but it appears that on UF he really only posts in the screenshot thread?

Anyway, I see what you mean, but you're both pretty knowledgeable on the subject :p

---

### Post by gutterslob on 2011-10-08
Someone PM'ed and pointed me here, so....
     
     > **IWantFroyo said:**
> I've been using Debian 6 for a while, but I don't think it fits my needs anymore.
     Here are my requirements:
     -I use vim for a lot of my work now. So I have to have a good way to quickly open it.
     -Switching between full screen apps.
     -Light.
     
     I've been looking into "tiling" window managers like evilwm, but I'm not sure which one to try.
     Based on your previous screenshots and my assumption of your preferred  workflow methods, I'd have to recommend Awesome. Sure, it's configured  in Lua which isn't everyone's favorite language (it's actually pretty  easy to grasp, just very tedious to type out), but it's somewhat sane  with its defaults and comes with a systray.
     
     Try this:
     [http://zenix-os.net/index.html](http://zenix-os.net/index.html)
     Debian based and comes with both Openbox and AwesomeDE, so you can switch about.

Also some links that might help you narrow down:
[https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers](https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers)
[http://crunchbanglinux.org/forums/topic/10101/beginners-tiling-wm/](http://crunchbanglinux.org/forums/topic/10101/beginners-tiling-wm/)
    
    Contrary to what ninjaaron and matthew say, I'm not some sort of 'guru'  when it comes to tiling (Daisuke_Aramaki is the "Real McCoy" in that field, as are many other top blokes on the Gentoo and FreeBSD forums/mailing-lists). In fact, I've pretty much given up on my WM  hopping habits and just alternate between ScrotWM, Openbox and CWM  these days, depending on machine. I have tried others in the past and  still have some old configs for  tilers like Dwm (heavily patched to the  point of breakage), AwesomeDE (older version, might not be compatible  with newer versions), Musca, Xmonad, Ratpoison (my first WM, actually), Sawfish, SubtleDE and WMFS, so feel free  to ask if you need em. 

The reason I use ScrotWM these days is mainly it's elegance. Yes, the  easy config is a plus, but I used DWM and Xmonad prior to Scrot, so it's  not that alone that won me over. Check the source code and you'll see  that everything is so clean and well audited. Scrot's beauty doesn't  really come from it's simplicity or it's easy config, but it's design. 

**NOTE:**If you think a tiling WM is gonna help you get the most out of Vim for your work, then I'm afraid you're mistaken. Tilers help, but the key here is your actual Vim configuration and how you manage the plugins (Pathogen, for example).
   
   
   
   > **matthew.ball said:**
> I'll just throw "stumpwm" into the mix.
   Stump has gotten very stable over tha past year or so. It's  definitely a candidate. Problem is, I run out of the room screaming and  crying like a rape-victim whenever I see anything Lisp-related (I'm not a  pro-programmer). I don't agree on the "successor to Ratpoison" moniker,  however. They're almost two entirely different beasts. Still, it's  definitely a WM you should look at. Matthew can probably get you  started. He seems quite a capable bloke.
  
  
  
  > **krapp said:**
> 
  Most tiling WMs are easy to use, but a pain in the *** to set up. And  they're far too bare-bone. I need a systray!Try AwesomeDE or  WMFS.
 
 
 > **ninjaaron said:**
> 
 I might be able to tell some things about herbstluftwm soon, however,  which not too many other people can do.... No need, mate. Doom's  always there for you.
 [http://crunchbanglinux.org/forums/topic/15226/herbstluftwm-thread-herbstluftwm-thread/](http://crunchbanglinux.org/forums/topic/15226/herbstluftwm-thread-herbstluftwm-thread/)



> **not found said:**
> Well, Salix 13.37 Ratpoison uses Ratpoison. No need to ever touch your [s]rat[/s] mouse again My first ever Linux experience was with Ratpoison on Slackware, mainly due to owning a laptop with a wonky touchpad at the time... it saved my job, btw.

But as much as I adore Ratpoison, I'd have to say that it's more "anti-mouse" than "pro-tiling".

---

### Post by ninjaaron on 2011-10-08
> **gutterslob said:**
>  No need, mate. Doom's  always there for you.
 [http://crunchbanglinux.org/forums/topic/15226/herbstluftwm-thread-herbstluftwm-thread/](http://crunchbanglinux.org/forums/topic/15226/herbstluftwm-thread-herbstluftwm-thread/)

Thanks for the great link! What I really need to do is just sit down and read the man page, but it's like a small book... well, not too small.

---

### Post by IWantFroyo on 2011-10-09
> **gutterslob said:**
> Someone PM'ed and pointed me here, so....
     
     
     Based on your previous screenshots and my assumption of your preferred  workflow methods, I'd have to recommend Awesome. Sure, it's configured  in Lua which isn't everyone's favorite language (it's actually pretty  easy to grasp, just very tedious to type out), but it's somewhat sane  with its defaults and comes with a systray.
     
     Try this:
     [http://zenix-os.net/index.html](http://zenix-os.net/index.html)
     Debian based and comes with both Openbox and AwesomeDE, so you can switch about.

Also some links that might help you narrow down:
[https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers](https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers)
[http://crunchbanglinux.org/forums/topic/10101/beginners-tiling-wm/](http://crunchbanglinux.org/forums/topic/10101/beginners-tiling-wm/)
    
    Contrary to what ninjaaron and matthew say, I'm not some sort of 'guru'  when it comes to tiling (Daisuke_Aramaki is the "Real McCoy" in that field, as are many other top blokes on the Gentoo and FreeBSD forums/mailing-lists). In fact, I've pretty much given up on my WM  hopping habits and just alternate between ScrotWM, Openbox and CWM  these days, depending on machine. I have tried others in the past and  still have some old configs for  tilers like Dwm (heavily patched to the  point of breakage), AwesomeDE (older version, might not be compatible  with newer versions), Musca, Xmonad, Ratpoison (my first WM, actually), Sawfish, SubtleDE and WMFS, so feel free  to ask if you need em. 

The reason I use ScrotWM these days is mainly it's elegance. Yes, the  easy config is a plus, but I used DWM and Xmonad prior to Scrot, so it's  not that alone that won me over. Check the source code and you'll see  that everything is so clean and well audited. Scrot's beauty doesn't  really come from it's simplicity or it's easy config, but it's design. 

**NOTE:**If you think a tiling WM is gonna help you get the most out of Vim for your work, then I'm afraid you're mistaken. Tilers help, but the key here is your actual Vim configuration and how you manage the plugins (Pathogen, for example).
   
   
   
   Stump has gotten very stable over tha past year or so. It's  definitely a candidate. Problem is, I run out of the room screaming and  crying like a rape-victim whenever I see anything Lisp-related (I'm not a  pro-programmer). I don't agree on the "successor to Ratpoison" moniker,  however. They're almost two entirely different beasts. Still, it's  definitely a WM you should look at. Matthew can probably get you  started. He seems quite a capable bloke.
  
  
  
  Try AwesomeDE or  WMFS.
 
 
 No need, mate. Doom's  always there for you.
 [http://crunchbanglinux.org/forums/topic/15226/herbstluftwm-thread-herbstluftwm-thread/](http://crunchbanglinux.org/forums/topic/15226/herbstluftwm-thread-herbstluftwm-thread/)



My first ever Linux experience was with Ratpoison on Slackware, mainly due to owning a laptop with a wonky touchpad at the time... it saved my job, btw.

But as much as I adore Ratpoison, I'd have to say that it's more "anti-mouse" than "pro-tiling".

I have an older computer running 10.04 that I can install whatever I want on (my critical files aren't on it). I'll try awesome and ratpoison on it, and maybe see the Lucid side of scrotwm. One of the reasons I was considering a tiling wm was because I tend to do stuff in two windows at a time, and it would be nice to be able to see both at the same time.
Thanks for dropping in!

---

### Post by matthew.ball on 2011-10-09
> **gutterslob said:**
> Stump has gotten very stable over tha past year or so. It's  definitely a candidate. Problem is, I run out of the room screaming and  crying like a rape-victim whenever I see anything Lisp-related (I'm not a  pro-programmer). I don't agree on the "successor to Ratpoison" moniker,  however. They're almost two entirely different beasts. Still, it's  definitely a WM you should look at. Matthew can probably get you  started. He seems quite a capable bloke.
Hehe, well thank you :)

If you remember though, I actually sent you a message regarding stump, just before I started using it!

I'm not a programmer (I'm actually a PhD candidate in philosophy), I just wanted a window manager which suited my workflow - seeing as I do everything in emacs, I have become somewhat familiar with lisp, and emacs' style of key-chord commands (that's probably something I neglected to write in my original post here - the stumpwm design philosophy is heavily emacs-inspired), so being already somewhat comfortable with lisp, my options were stumpwm or sawfish - I chose stumpwm just because of the relationship with emacs.

I understand that most people can't stand lisp, but coming from a non-programming background (i.e. lisp was my first language) I found it quite easy to grasp - I certainly don't know the intricate details of lisp, but I know enough to write some customisations for my text-editor/window manager.

If anyone is interested in using stumpwm, I would gladly help out, but taking into account what I just said, I'm not really a programmer, so I can't offer much help beyond what I already know (which isn't a lot!)

---

### Post by gutterslob on 2011-10-09
> **ninjaaron said:**
> What I really need to do is just sit down and  read the man page, but it's like a small book... well, not too  small.You talking about "man herbstluftwm" and "man  herbstclient"? ... Not that long, really. I've seen much, much longer  man pages. Just combine all the various manuals for git or bash or  zsh... or just do "man screen" in your term.



> **IWantFroyo said:**
> ....and maybe see the Lucid side of  scrotwm.It's best to compile the latest 0.9.34 snapshot from  source, or sync with CVS or Git (if you know how). The version in the  Ubuntu repos (regardlessof version) is pulled from what's in the Debian  repos, which means it's pretty old. Though in Debian's defence, the  version they carry is extremely stable. 



> **matthew.ball said:**
> Hehe, well thank you :)

If you remember though, I actually sent you a message regarding stump, just before I started using it!
Yes, I do remember, which is why I referred to you as a "capable bloke", since you seemed to be more experienced with Common-Lisp than I was.




[quote=atthew.ball]I'm not a programmer (I'm actually a PhD candidate in philosophy), I just wanted a window manager which suited my workflow - seeing as I do everything in emacs, I have become somewhat familiar with lisp, and emacs' style of key-chord commands....[/quote]TBH, Lisp isn't something I gave enough time to. It's probably not as daunting as some make it out to be. Thing is, I've only ever been somewhat comfortable with C (and maybe Python and Ruby). I suppose being a heavy emacs user does make Lisp a whole lot easier, and Stump a lot more natural to get into as a result.

Programmer or Philosopher, you've still got Permanent Head Damage (PhD) in my book, mate. :P

---

### Post by el_koraco on 2011-10-09
> **gutterslob said:**
> Though in Debian's defence, the  version they carry is extremely stable. 


About three months running the D version of scrot as primary here WM, not a single hiccup.

---

