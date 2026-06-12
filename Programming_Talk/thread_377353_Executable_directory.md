---
title: "Executable directory?"
date: 2007-03-06
forum: Programming Talk
---

### Post by Cirdan7 on 2007-03-06
In C++, how do I get the directory that the executable is located in, and get the user's home directory? I noticed that any directory from the program is in the directory that the user runs it in. so if the user runs the program from the home directory all the ./ in the program is the home directory...not the same directory as the executable, correct?

---

### Post by j_g on 2007-03-06
> how do I get the user's home directory?

I think that you call the standard C library and query the "$HOME" environment variable. But if you're using Gnome's GLib, it has a function called g_get_home_dir() that you can call to return a nul-terminated string that is the path to the user's home directory.

> how do I get the path of my executable

I do this in C:

```
/******************* get_exe_name() ******************
 * Gets the path name where this exe is installed
 *
 * buffer = Where to format the path. Must be at least
 *                 PATH_MAX in size.
 */


static void get_exe_name(char * buffer)
{
  char                                  linkname[64];
  register pid_t                  pid;
  register unsigned long offset;

  pid = getpid();
  snprintf(&linkname[0], sizeof(linkname), "/proc/%i/exe", pid);
  if (readlink(&linkname[0], buffer, PATH_MAX) == -1)
    offset = 0;
  else
  {
      offset = strlen(buffer);
      while (offset && buffer[offset - 1] != '/') --offset;
      if (offset && buffer[offset - 1] == '/') --offset;

  }
  buffer[offset] = 0;
}
```

---

### Post by Mr. C. on 2007-03-06
The solution provided here is not portable.  There is no /proc on other Unix variants, and may not exist in various Linux distros.  Use portable constructs.

The user's HOME directory may be available via the environment variable $HOME.

Obtaining the executables path is not always possible.  You code may have been called as PROG, ../bin/PROG, etc. and this may have crossed symlinks, NFS mounts, etc.  You can obtain the current working directory, and open ".." to reconstruct *a* path, but this might not be the canonical path.

MrC

---

### Post by j_g on 2007-03-06
Ah, who cares about Unix. It's dead. Just ask SCO.

And as far as oddball Linux distros go, I say "Don't support them". As far as I'm concerned, if it works on Ubuntu, Suse, and Fedora, that's good enough. We need to start thinning out the plethora of distros out there.

---

### Post by pmasiar on 2007-03-06
> **j_g said:**
> Ah, who cares about Unix. It's dead. Just ask SCO.

And as far as oddball Linux distros go, I say "Don't support them". As far as I'm concerned, if it works on Ubuntu, Suse, and Fedora, that's good enough. We need to start thinning out the plethora of distros out there.

I disagree. This is attitude which separates a script kiddie from a real hacker. [Hacker](http://www.catb.org/~esr/faqs/hacker-howto.html) is interested in learning how system works, how to use it to full potential (and more). So 5 years from now, if someone will try to use this widget on mobile phone, and it will work (and other simillar will not), future hacker will get curious: "this is strange, why one works and other does not? Let me see how it is done correctly..." and can learn from it.

You are forced to cut corners sometimes to meet deadlines, but every problem can be approached as learning opportunity. If it is worth solving, it is worth solving right.

Otherwise, it is just a [cargo cult programming](http://en.wikipedia.org/wiki/Cargo_cult_programming) . 'I am not sure why it fails for you, but it works fine on my computer/browser". Willie from Dilbert cartoons can do that.

---

### Post by Mr. C. on 2007-03-06
> **j_g said:**
> Ah, who cares about Unix. It's dead. Just ask SCO.

And as far as oddball Linux distros go, I say "Don't support them". As far as I'm concerned, if it works on Ubuntu, Suse, and Fedora, that's good enough. We need to start thinning out the plethora of distros out there.

Don't be lazy.  Learn the approaches that work.  Educate yourself.  There's a world of fantastically gifted and educated computer programmers who will compete you right out of the market.

Guess what - all this Open Source software you are using to build your project... its all works on each Unix/Linux variety *because* their creators understand the value in importance of cross platform.  You reject the very principle upon which you stand so steadfast.

Be well,
MrC

---

### Post by j_g on 2007-03-06
You're free to support the oddball stuff. It isn't worth my time to do so. I'd rather expend my efforts toward targetting distros/etc that met my minimum standards of usability. That way I can concentrate upon giving my targetted endusers (ie, not people who use oddball stuff) better support. The people who do use my stuff have explicitly told me that they deliberately chose it because it offers them a better experience than the other, one-size-fits-all alternatives they've tried. And that's what I care about.

I don't use all of the GNU tools. I use only the GCC compiler/linker, and make. (And for the latter, I use only a very, very small subset of its features). The other stuff fails my minimum standards of usability. It's not worth my time to deal with those tools.

Contrary to your depiction of "lazy", I have no doubt that I've written at least as much software as you have, and worked just as hard at it. It's just that I choose to expend my efforts in other, what I consider to be more productive, ways, than supporting every distro written by Earl, Pete, and Johhny, and their pet dogs Fido, Spot, and Snoopy. You can do it if you'd like. I'd rather expend my time on what I, and my endusers, consider to be more important things.

---

### Post by Mr. C. on 2007-03-06
Your choice, do what you will.  However, if you GIVE advice to others, allow them the benefit of knowing your advice's limitations.

As far as you thing is bigger than my thing, I'll let you win that battle.

MrC

---

### Post by j_g on 2007-03-06
I presume someone asking a programming question on an Ubuntu forum is interested in knowing specifically about Ubuntu support (unless stated otherwise, and it wasn't in this case).

I certainly don't hide my perspective that I think the plethora of Linux distros are a bad and unnecessary thing, and that programmers should spend their time supporting only the major distros to help discourage rampant forking of yet more stuff that tries to be all things to all people, but ends up being yet another offering (read: support headache) that is not particularly good for no one in particular.

---

### Post by Mr. C. on 2007-03-06
Ubuntu is the Chosen One... Bow to Ubuntu!

---

### Post by g3k0 on 2007-03-06
Nevermind

---

### Post by Mr. C. on 2007-03-06
This does not resolve the OPs question.  Consider:

PATH=/bin:/usr/bin:/usr/local/bin

with the binaries:
/bin/MyProg
/usr/bin/MyProg
/usr/local/bin/MyProg

Now, from my $HOME, I type:

MyProg

What's the CWD?  It certainly isn't any of the above.

And now, if I CD into /usr/local/bin and I type:

../..bin/MyProg

what's that value of CWD ?

This is a VERY difficult problem, that may not have a single (canonical) answer.  Unix/Linux does not require a full path name to exec a program - the pathname can be relative.

Typically when this is required, shell script calling wrappers are used, with various trickery.

MrC

---

### Post by g3k0 on 2007-03-06
Good call.  Perhaps I should have tested it more lol.

---

### Post by j_g on 2007-03-06
Folks, just support Ubuntu (Debian), Fedora (RedHat), and SUSE. Forget about the rest. You don't need them. They're just also-rans with unnecessary tweaks/hacks. How many copies of Linux does a person need anyway?

And for god's sake, let Unix die already. It's been coughing up blood for years.

---

### Post by pmasiar on 2007-03-06
> **j_g said:**
> Folks, just support Ubuntu (Debian), Fedora (RedHat), and SUSE. Forget about the rest. You don't need them. They're just also-rans with unnecessary tweaks/hacks. How many copies of Linux does a person need anyway?

And for god's sake, let Unix die already. It's been coughing up blood for years.

So for example Gentoo is also-run? You just proved beyond reasonable doubt you have no idea what are you talking about. And you left out other promising distros. One of the cool ones on my radar is Damn Small Linux. [http://distrowatch.com/table.php?distribution=damnsmall](http://distrowatch.com/table.php?distribution=damnsmall)  and Frugalware. SystemRescueCd is also pretty cool and it saved my *** once. Every hacker should be delighted if her widget was included in such distro, IMHO. Maybe you are more into games, and these "frugal" systems are not important enough for you?

And you will be surprised how many Unixes is happily running in back rooms of many companies by experienced people who learned lesson you yet have to learn: if something is not broken, don't fix it - don't rewrite it or move to other platform. Old boxes with applications probably older than you :-)

---

### Post by Cirdan7 on 2007-03-06
I came here to get a answer for my programming question...not what distros to support.

I am working on a game and need to get to the game assets inside the program. I eather have the binary install to a bin directory (/usr/bin or /usr/local/bin) and just store the assets in a hidden file in the user's home directory. But that would mean each user would have to install the game assets.

My game will be portable to Windows, Mac, Linux, and maby Unix will be a free-be. Should I just use a filesystem like PhysicFS([http://icculus.org/physfs/)](http://icculus.org/physfs/)), instead of trying to do this stuff on my own? I am able to work on the Windows and Linux port, the mac port I will have to find someone else to help me with. But I want to at least get both of them working.


Thanks.

---

### Post by Mr. C. on 2007-03-07
Cirdan7,

I'm glad you asked, and requested bringing the thread back to the issue at hand.

There are a couple of common techniques.

One, is to place the assets in a well know location, definable by the user at install time (eg /opt/game/assets.  Your installer creates a little wrapper script that defines an environment variable with the same location (eg. GAME_ASSETS=/opt/game/assets).  Your program either must grab the environment variable to initialize itself.

Or the installer can create a wrapper/launching shell script that includes the location of the assets:

GAME_ASSETS=/opt/game/assets
exec game --assets=$GAME_ASSETS

Either way, your program now know where its goodies are stashed, it allows the user to specify their location (helpful for non-root users).

If you write your OS interfaces correctly, you will find your program will port almost trivially to the various *nix platforms, and Windows NT on up.

All this is much cleaner that trying to work out the various file systems and their issues.  Create portable interfaces, that abstract out the FS layer, and have lower level libs do the dirty work.

Hope this helps!
MrC

---

### Post by j_g on 2007-03-07
If you're making a game, obviously you're targetting new Linux installations. In that case, you can do things the way that I showed you. Linux versions suitable for playing games will support it.

---

### Post by bryan.taylor on 2007-03-07
However, it's much nicer to have a configurable path for the game assets.  You don't want to constrict the choices of your users (even your ubuntu, fedora, blah users).  Go with Mr. C.'s way of doing things.

---

### Post by Wybiral on 2007-03-07
> **j_g said:**
> Folks, just support Ubuntu (Debian), Fedora (RedHat), and SUSE. Forget about the rest. You don't need them. They're just also-rans with unnecessary tweaks/hacks. How many copies of Linux does a person need anyway?

And for god's sake, let Unix die already. It's been coughing up blood for years.

Every time I see you on this forum you're preaching against portability (whether it be windows-to-linux portability or distro-to-distro portability)

It's fine if YOU want to make your programs overly specific and stuck flopping around on one platform, but most of the programmers here are interested in portability...

I don't understand what your problem is. A little extra work and thousands of more people are able to run your program... And in most cases it isn't even that much work, but even if it were... The extra boost in userbase would be worth it.

---

### Post by Mr. C. on 2007-03-07
Wybiral,

You'll be having a battle of wits with an unarmed man...

MrC

---

### Post by j_g on 2007-03-07
> However, it's much nicer to have a configurable path for the game assets.

If the enduser has a choice of where to install the application, then he already has a "configurable path for the game assets". After all, they go where the executable goes, and he says where that goes. And the executable can easily ascertain that location on a decent Linux distro by the way I notated in a previous post.

There is no need to make this harder than it should be. That is actually a disservice to the majority of endusers. Most Windows (and new Linux) endusers already think that Linux is too difficult to configure and maintain. We need to simplify things, not perpetuate the very things that turn off potential Linux endusers.

---

### Post by j_g on 2007-03-07
> Every time I see you on this forum you're preaching against portability

That's a vast, and incorrect, oversimplification of my point of view. When it comes to "portability", what I preach against is writing software that is more difficult to deploy/use/maintain than it would be if it didn't take an excessive "lowest common denominator" approach. In this particular case, I think that worrying about whether you can do "proc" on a Linux distro, and consequently adopting more convoluted schemes to compensate, is an example of excessive "lowest common denominator" thinking. I'd rather that Linux programmers not do that sort of thing. What Linux programmers need to be doing is better supporting the major distros, making things easier for endusers on those distros, and thereby encouraging the migration of endusers who currently see Linux as being too difficult to setup/maintain (ie, Windows users).

> most of the programmers here are interested in portability

Linux needs more programmers who are more focused upon the major distros. This needs to be encouraged. Distros such as Ubuntu need these programmers. These are the people who will ultimately increase the enduser base beyond what it is. (The OS geeks already have their Linux distros and all the "configuration files" they ever want to play with. They're already "sold". We now need to sell the people who aren't already sold. Non-geeks don't want to be "configuring" software, much less compiling it. They simply want it to work upon the major distro they've chosen).

> thousands of more people are able to run your program

And yet, you could get many more people than that using your software if you'd standardize upon a higher level of support (ie, for example, forgetting about some oddball distro that doesn't have "proc"). There are probably more Ubuntu/Kubuntu users than there are total endusers for all of these also-ran distros. If you made a program that was really, really easy to use on Ubuntu, and took advantage of any particular features Ubuntu has to offer, not only would you get the Ubuntu users choosing it over other, lowest common denominator software, but you'd actually give non-Linux users an incentive to try the distro and your software. You could very well end up with a _LOT_ more endusers than if you tried competing against the plethora of "I'm the same thing as everyone else" offerings with... well... basically the same thing as everyone else.

I realize that this is an entirely foreign concept to many of the Linux geek-hobbyist programmers here, but it is a valid concept. One of the largest software companies in the world, Microsoft, has done really, really well this way. And Linux doesn't live in a vacuum. Your software isn't just competing against lots of other Linux software that suffers from what I call "lowest common denominator" syndrome. You're also competing against Windows software. The way to increase Ubuntu's userbase is not to make a program that an average Windows user is going to run and say "My <insert some Windows native app that does the same task> is so much better and easier to install/setup/use than this".

---

### Post by Cirdan7 on 2007-03-08
Ill just do what Mr. C recommended, I have a config file for settings anyway, I can just add an assets option to it.

As for portability, why would I want to limit my game to one platform? I know more people who use Windows then Linux, and in the future if I want to switch to Linux I want to still be able to run my game. Its a problem when programs aren't portable because then people who are used to using the program on one platform cant switch to the other because of it. Thus encouraging people to not switch platforms.

---

### Post by j_g on 2007-03-08
> why would I want to limit my game to one platform?

That's a question only you can answer.

But your game software is competing for the attention of endusers, and there are plenty of offerings (on Windows anyway) that limit themselves to one platform simply so that the software can tap into the potential of its given platform (ie, not be an example of the lowest common denominator).

Most game players will not use software that isn't fun nor clunky, and the surest way to quickly kill their sense of fun is to hassle them with installing, configuring, and just getting the thing up and running. I've actually seen these people quickly and brusquely toss software aside if it's too much "work" to get going. And then they tell other game players that it's "a piece of crap". They are not a particularly forgiving market segment.

If you make your configuration more difficult than it needs to be, you're asking for trouble. (Then again, if you're doing this for a hobby, perhaps you don't care if it turns out your approach alienates a significant percentage of gamers. That's something only you can determine).

---

### Post by kinson on 2007-03-08
> **j_g said:**
> 
And as far as oddball Linux distros go, I say "Don't support them". As far as I'm concerned, if it works on Ubuntu, Suse, and Fedora, that's good enough. We need to start thinning out the plethora of distros out there.

I realli don't mind many distro's out there. After all, diversity is part of life if you ask me, and all distro's start small.

But seriously, to each his own, I think everybody is entitled to their own opinion, lets not stray from the topic here :) "Portable/Not-portable" would probably be another thread(and it'll be a mighty long one that :p ).

Just my 2 cents :)

Cheers,
Kinson

---

### Post by Wybiral on 2007-03-08
> **j_g said:**
> That's a question only you can answer.

But your game software is competing for the attention of endusers, and there are plenty of offerings (on Windows anyway) that limit themselves to one platform simply so that the software can tap into the potential of its given platform (ie, not be an example of the lowest common denominator).

Most game players will not use software that isn't fun nor clunky, and the surest way to quickly kill their sense of fun is to hassle them with installing, configuring, and just getting the thing up and running. I've actually seen these people quickly and brusquely toss software aside if it's too much "work" to get going. And then they tell other game players that it's "a piece of crap". They are not a particularly forgiving market segment.

If you make your configuration more difficult than it needs to be, you're asking for trouble. (Then again, if you're doing this for a hobby, perhaps you don't care if it turns out your approach alienates a significant percentage of gamers. That's something only you can determine).

But you're making the assumption that portability means having a hassling or not full potential product, and that isn't the case. ESPECIALLY with games...

I'm going to assume you don't do much game development, and in the case that you're speaking on behalf of regular GUI based software development, true... Sometimes it's hard to achieve the effect that you want if you take the super-portable route (not impossible though, and it doesn't require a hassling install and poor interface)

But games are entirely different. The software involved in most games is really portable (with the exception of DirectX). A lot of games use OpenGL which is available for almost every platform I can think of...

> 
If you're making a game, obviously you're targetting new Linux installations. In that case, you can do things the way that I showed you. Linux versions suitable for playing games will support it.


I've seen plenty of smaller distros of linux, the ones you probably want to weed out...

> 
Folks, just support Ubuntu (Debian), Fedora (RedHat), and SUSE. Forget about the rest. You don't need them. They're just also-rans with unnecessary tweaks/hacks.


... That are capable of supporting SDL + OpenGL games, and not only capable... But just as capable as the above mentioned distros.

Like I said, I'm assuming you haven't done any game development, so you're excused from this conversation because average software development and game development are vastly different worlds with vastly different goals and needs.

If you think high-up games don't take portability into consideration when writing their products....

Doom 3 (available on: Mac, Linux, Windows, Xbox)
Quake 3 (available on: Dreamcast, IRIX, Macintosh, Linux, Windows, PlayStation 2)
Half-life 2 (available on: Windows, PlayStation 3, Xbox, Xbox 360)
Halo: Combat Evolved (available: Xbox, Windows, Apple)

They do. But portability in the graphics/engine/libraries isn't hard at all in the game world since there are already established libraries that work great on hundreds of platforms.

So, if this executable directory problem is the only thing holding someone back from creating a highly portable game... I would say to solve this problem for portability, it's probably going to be one of the few portability-related problems involved with writing the game, so even if it takes a little extra work... So what? It's worth it.

---

### Post by pmasiar on 2007-03-09
> **Mr. C. said:**
> You'll be having a battle of wits with an unarmed man...

MrC, you made my day with this quip! I can feel the confident power of calm mind of an old-school guru :-)

---

