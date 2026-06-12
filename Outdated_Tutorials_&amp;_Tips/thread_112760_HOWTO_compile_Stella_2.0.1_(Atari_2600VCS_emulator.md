---
title: "HOWTO compile Stella 2.0.1 (Atari 2600/VCS emulator)"
date: 2006-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Galoot on 2006-01-05
This is a simple HOWTO. Anyone who's ever compiled anything before likely won't need to read it. Anyone who hasn't compiled something from source, though, will see how easy the task can be.

[INDENT][COLOR="Red"]**WARNING**: It is illegal to use ROM images of games that you do not actually own. These games are still copyrighted.[/COLOR][/INDENT]

[**Stella**]("http://stella.sourceforge.net/") is an Atari 2600 emulator currently at version 2.0.1. The version available through the Ubuntu (multiverse) repositories is 1.4.1. I don't think the updated version is acceptable to the Backports team because of dependency issues (please correct me if I'm wrong!).

The most obvious differences in the 2.x version are:[LIST][*]Added integrated GUI (you don't have to fiddle with the command line anymore)[*]Added ROM launcher (you don't have to quit/restart Stella every time you want to play a different game)[*]Added ZIP support (you can keep your ROMs zipped up tight)[*][But wait! There's more!]("http://stella.sourceforge.net/stellanews.html")[/LIST]
Converting the available RPM to DEB using Alien didn't work for me. Luckily, I didn't run into any problems compiling Stella from source.

Disclaimer: I am a total newb when it comes to compiling software. If this HOWTO doesn't work for you I doubt if I'll be able to help much. All I know is that these steps worked *for me*. If they work for you, too, let us know. If not let us know that, too, and maybe someone more experienced can help out.

(Note: You could always spend $30 for 40 games and buy the [Atari Flashback 2]("http://www.atari.com/us/games/atari_flashback2/7800"). I love mine! And the fact that I actually have a chance at kicking my 14-year-old's butt appeals to me, too. But my wife occasionally needs the TV, so...)
================================================

Here we go.

First you need to download [the source code]("http://stella.sourceforge.net/downloads.html").

Now, fire up a terminal window. Henceforth, each line is a separate command.

Navigate to the directory where you saved the just-downloaded package. Unpack it using the following command:

```
tar zxvf stella-2.0.1-src.tar.gz
```

Your next step is to ensure you have the tools needed to actually compile something. To do this you must install the build-essential package.

```
sudo apt-get install build-essential
```

You now have the basic tools you'll need to compile stuff. But you will run into dependency issues while compiling Stella unless you also install the "libsdl1.2-dev" package. So do that next:

```
sudo apt-get install libsdl1.2-dev
```

This package itself also depends on other packages, but apt-get handles all that for you. Don't worry about it.

Now that you have the unpacked source code and the tools to compile with, it's simple. Change to the directory where you unpacked the Stella sources.

```
cd stella-2.0.1/
```

It's time to compile.

```
./configure
```

```
make
```

```
sudo make install
```

Ubuntu will complain if you don't prefix "make install" with "sudo."

That's it. You've now got Stella installed. Type "stella" at the command line (or hit [ALT]+[F2] and type it there) and follow the prompts to point it at the directory where you keep your ROMs.

If you don't have ROMs to use, I can't help you. The Stella site has [some pointers]("http://stella.sourceforge.net/docs/stella.html#Games"). Hopefully you are aware of the legal issues involved before using [Google to find some]("http://www.google.ca/search?hl=en&q=%22atari+2600%22+ROMS&btnG=Google+Search&meta=").

---

