---
title: "The best way to go about this task?"
date: 2008-08-13
forum: Programming Talk
---

### Post by Igtenio on 2008-08-13
I'm developing a little personal Ubuntu-based distro, and I'm wanting to add the ability to apply different "templates" to it; essentially, you can type one command and a certain setup of packages gets installed.

The problem is...I'm not sure what the best method is to go about it.

At first, the easiest solution seems to be a bunch of Shell Scripts that can be run depending on what the user wants. Which is functional...but doesn't seem very pretty.

Then, I figured that maybe I could just use one shell script that calls on different functions depending on what options are chosen when it's run. Something like "tool -e"...except I'm not completely sure that's possible.

The third option I could think of was to make a command-line program. This is, quite frankly, likely the best option for what I want done. The problem is, well, I know jack and **** about anything besides shell scripts. I wouldn't need a complex language, but I also doubt there's an AutoIt equivalent for Linux.

So, what do you all think? Would shell scripts be good enough, and even capable of using command-line flags when called, or would the best bet to be to invest in learning a light programming language? If the latter, which would you suggest?

---

### Post by LaRoza on 2008-08-13
> **Igtenio said:**
> I'm developing a little personal Ubuntu-based distro, and I'm wanting to add the ability to apply different "templates" to it; essentially, you can type one command and a certain setup of packages gets installed.

So, what do you all think? Would shell scripts be good enough, and even capable of using command-line flags when called, or would the best bet to be to invest in learning a light programming language? If the latter, which would you suggest?

Shell scripts could do this easily. I suggest you start out with [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) and other guides (my wiki has more)

You can even use a GUI (zenity) to do this, so you could have a check list of options and a user can check one and it will be applied.

[php]
#!/bin/bash

if [ $1 == "--python" ]
then
	echo "Python!";
elif [ $1 == "--c" ]
then
	echo "C!";
else

	ans=$(zenity  --list  --text "Packages" --radiolist  --column "Pick" --column "Option" TRUE "C_Development" FALSE "Python_Development");

	if [ $? -eq 1 ] 
	then
		echo "Cancelled";
	elif [ $ans == "C_Development" ]
	then
		echo "C!";
	elif [ $ans == "Python_Development" ]
	then
		echo "Python!";
	else
		echo "Unknown option";
	fi
fi
[/php]

(Run script with --python or --c options to get it to echo those blocks, or run it without any options to get the GUI. Replace the echo's with what you want.)

---

### Post by Xealot on 2008-08-13
Hi.

Its perfectly possible to check what arguments was supplied in a bash script, as for other possible languages. Perhaps python ?.

Anyway, It would be nice if you could provide some simple concrete samples of your idea :)

 - X

---

### Post by Igtenio on 2008-08-14
LaRoza;

I'm sure you regularly hear it, but thank you *so* much. Just the little glancing I've done over your Wiki and the Bash-Scripting guide has given me a whole new idea of what a shell script can do. I've been using them for a while now, but merely to automate normal command-line tasks.

I think for the moment I'll stick to command-line only, mostly 'cause I'm beginning and for ease of debugging, but the GUI seems an interesting option...

Xealot;

Well, the best way I can think to describe it, which is also horridly loaded for obvious reasons, is to compare it to Automatix. Except...well, not sucking.

Instead of different packages that people need, it's for people who're experienced enough to easily put in a set of packages. All it does is send commands directly to apt-get, which does the actual installation and configuration.

The distro/remix I have going has two main setups; a KDE-based one which is vanilla KDE, a lite-desktop which is IceWM and some programs with certain settings, and a command-line one, which is basically just a Command-line installation of Ubuntu.

Instead of a person having to find the actual packages to install for a certain setup, they can just do "tool --u", for instance, and have the ubuntu-desktop metapackage installed. Something like "tool --ur" would get you ubuntu-desktop plus the restricted-extras. If you want Kubuntu in addition or instead, you run "tool --kr" for kubuntu-desktop or "tool --kr" for kubuntu-desktop and restricted-extras.

Of course, that isn't just it, or else there'd be little point. It'd also store custom setups. If you wanted the KDE-based setup on the CD, you could run "tool --i" and have it installed. Same for IceWM.

I'm looking for a decent method to also strip all packages from a installation except for one(ubuntu-standard, in this case), but I haven't quite found it. When I do, that'll be in there too.

I also don't see what would keep me from making other configurations available, possibly through a personal repository of some kind.

It isn't a tool you'd be using on a regular basis, but it'd be awesome for configuration of machines. One CD or DVD and you could put every flavor of Ubuntu onto a machine, plus some custom setups.

---

### Post by slavik on 2008-08-14
for options, use getopt :)

---

### Post by Igtenio on 2008-08-15
Thank ya kindly. :)

Woo, I have tons to read about. :P

---

