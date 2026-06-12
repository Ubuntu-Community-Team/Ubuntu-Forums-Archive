---
title: "Comprehensive command list by distro?"
date: 2011-12-20
forum: Programming Talk
---

### Post by HadrianKross on 2011-12-20
(full OR comprehensive OR all)+linux+command+list+reference+"by dist"

web search came up dry

only other option is to try and find out how to dump all the "man" pages and then do a "diff" on each, for all the 100+ distributions.

that would mean installing each of them to do so, which is rather prohibitive at this time, though might be kind of interesting to do now that i think of it

any reference to other comprehensive type sites/info would be appreciated as well

this has programming relevance

---

### Post by hansdown on 2011-12-20
Welcome to the forum, HadrianKross.

The first two links can be printed.

The third, is quite handy, also.

[http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)

[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

[http://www.linuxscrew.com/2009/12/21/best-of-linux-cheat-sheets/](http://www.linuxscrew.com/2009/12/21/best-of-linux-cheat-sheets/)

These are good for ubuntu.

---

### Post by trent.josephsen on 2011-12-20
Okay... so you want a list of all the commands available in a given distribution?  That might work for Ubuntu, and maybe half a dozen others that have a pretty consistent default install.  What about Debian, or Slackware, which give you options about what software groups to install, and there is no real "default"?  What about Arch and Gentoo, and other distributions that drop you to a bare-bones system and expect you to install everything beyond the package manager yourself?

Even without addressing those issues the problem is still ill-defined.  Do Xubuntu, Kubuntu, etc. count as Ubuntu?  What about Server?  What about Natty?  Maverick?  Lucid?  Do you include commands that aren't in your $PATH unless logged in as root?  Furthermore, few people use the default without installing something extra (Dropbox, perhaps, or Chrome), so the *comprehensiveness* of your list is going to be questionable no matter where you draw the line.

Perhaps it would be better if I ask for exactly what reason could you possibly want a "comprehensive" list of commands.

---

### Post by Telengard C64 on 2011-12-20
> **trent.josephsen said:**
> the problem is still ill-defined.

Indeed, because at some point your list grows to include every Linux program ever written.

You're better off focusing your attention on the programs you work with regularly than looking for some kind of list.

Start reading [The Bash Reference Manual](http://www.gnu.org/software/bash/manual/html_node/index.html), then continue on with [GNU Coreutils](http://www.gnu.org/software/coreutils/manual/html_node/index.html).

You'll certainly want more than those, but the question is what? What problem are you trying to solve? If you want to know what programs might be related to your problem then try this:

```
apropos topic
```

---

### Post by Habitual on 2011-12-21
[The Common denominator]("http://ss64.com/bash/")

---

### Post by Lars Noodén on 2011-12-21
If you are looking for a list of the programs that are installed on your machine you could do something like the following:

```

for i in $(ls /bin /sbin /usr/bin /usr/sbin /usr/local/bin /usr/local/sbin | sort); do
   man  "$i" 2>/dev/null \
 | head -9|awk '/ - / {print $0} '\
 | sed -e 's/^ *//;s/ - /\t/';
done

```

On Precise Pangolin there are close to 2000.

---

### Post by HadrianKross on 2011-12-21
@hansdown
thanks and thanks for the links

@trent.josephsen
my search was quite well defined, but perhaps the search engine simply wasn't quite up to the task? or the list simply wasn't available...

all distros means all distros--to include subsets/sub-versions thereof that have differing sets of commands at install; when they are available for use may be a matter for categorization later, but I am looking for an authoritative "macro" list at some point.

may even look into deprecated commands--if they exist--over the course of linux/unix commands later on. also, after the current, regularly updated distributions are included, then may look into those that have not been updated in some time or those that very few people know about.

to start, the "recognized" distributions of linux will suffice:
[http://upload.wikimedia.org/wikipedia/commons/f/f6/Gldt1106.svg](http://upload.wikimedia.org/wikipedia/commons/f/f6/Gldt1106.svg)

more specifically, and to begin with, the harddrive installation dvd/cd sets (live disks as well--perhaps with priority to start). these being the stable current/latest iterations of the distributions.

for the barebones flavors, then assume just the basic "at install" commands to start.

later, all available commands/programs cross referenced by distro including the differences in arguments of the same command.

primary goal is for this to be used as a teaching tool while going over the timeline of various distributions (historically) as well as a quick reference guide (cross referenced in an intuitive manner) for any number of uses when working between various distros, to serve the linux community at large--esp. those new to command-line linux. (a free, dynamic, self-updating tool)

@Telengard C64
not so much, as that could be one of the end results
thanks for the reference info

@Habitual
thanks

@Lars Noodén
great, now how to get that piped from every current/stable distro to a storage location :P:confused:


easy access to "man" page archives per distro and any programatic/scripting options will help

other options that come to mind to solve this would be most helpful as well

since mitigating complexity over large amounts of data is one of the goals of computer programming, I thought this would be the place to pose this question

considering the vast amounts of raw data we deal with at any given time, a simple (auto updated) list of commands should not seem all that prohibitive

---

### Post by trent.josephsen on 2011-12-21
> **HadrianKross said:**
> stable current/latest

Stable, current, or latest? :roll:  You're not supporting your "well-defined" argument.

Even assuming you could come up with an unambiguous definition of what should and should not be included that works for every distro, current technology is incapable of doing what you describe programmatically.  It's simply impossible to determine what commands will be available after boot without (a) installing it manually and finding out the hard way, or (b) reading extensive documentation (where available) about where binaries are stored and unpacking whatever kind of packaging each distro uses to look at what gets stored there.

Note that not all commands have manpages even in distributions that provide them, so you'll have to come up with some other way to list commands.  Things occasionally get dropped in /opt/whatever or (under some distros) some more bizarre directory, so you can't just run `find` on the usual suspects even supposing you went ahead and installed the entire thing.  If you want to include shell built-ins that's a whole new can of worms, so I'll ignore that even though I suspect you probably do.  Furthermore, many distributions, maybe most of the big ones, can have several different packages that provide a binary of the same name -- sometimes they're the same, but usually they're at least a little different.  In Debian-and-derivatives at least this is further complicated by the fact that a symlink like /bin/sh can direct to any of several "alternative" binaries, and which one depends on user input at install time.

But, you know, maybe I'm just a pessimist.

---

### Post by Lars Noodén on 2011-12-22
> **HadrianKross said:**
> @Lars Noodén
great, now how to get that piped from every current/stable distro to a storage location :P:confused:


One way would be to download the CDs for each and install them in a VM.  If you have a fast machine with a good amount of RAM, that will go quickly.

I'd modify the script a little now that I've tried it some more:
```

for i in $(ls /bin /sbin /usr/bin /usr/sbin /usr/local/bin /usr/local/sbin | sort); do
   man  "$i" 2>/dev/null \
 | head -9 \
 | grep ' - ' \
 | sed -e 's/^ *//;' ;
done  | sort -u ;

```

It's slower that way because of the big sort but it will eliminate all duplicates.

---

### Post by slavik on 2011-12-22
How about:
```

echo $PATH | tr ':' '\n' | while read line; do ls $line; done

```

As already had been stated, doing this for _every_ Linux distribution (do you intend on every version of ever distribution, too?) is not a very good idea. This is a HORRIBLE teaching solution.

---

### Post by HadrianKross on 2011-12-22
@trent.josephsen
(stable current/latest) == (the latest stable version)

any more areas/options to look into for unique commands and/or arguments?

@Lars Noodén
thanks again

wondering how many terabytes it would take to store them all...

@slavik
just the latest stable version(s)

that depends on what you're trying to teach, though its primary  application will more than likely be as a centralized reference  (hopefully a quick reference) source

though the linux/unix terminal/shell is not an actual programming  language, isn't it usually better to learn the vocabulary--as well as  the grammar--first, before trying to speak the language? while one  wouldn't expect someone to simply memorize the dictionary, having a  dictionary is no less important.


btw [TAB] in zenwalk (live) came up with:
 2159

looks like most of the newer distros (or newer versions of distros) may  be sitting around 2k in terms of readily available commands

even if it's not one of the better tools used to learn command line linux, thinking this might be fun to do in terms of getting in to old, less used distributions and checking them out

---

### Post by Lars Noodén on 2011-12-23
> **HadrianKross said:**
> wondering how many terabytes it would take to store them all...



Each CD image is up to 700MB in size.  Most are somewhat smaller others are much smaller.  If you err on the side of caution, budget 700MB each.  Here are some of the Ubuntu distros that I have in my cache:

```

700M  ubuntu-11.04-alternate-amd64.iso
698M  ubuntu-11.04-desktop-amd64.iso
697M  ubuntu-11.04-alternate-amd64+mac.iso
697M  kubuntu-11.04-alternate-amd64.iso
695M  kubuntu-11.04-alternate-i386.iso
694M  ubuntu-11.04-desktop-amd64+mac.iso
689M  xubuntu-11.04-desktop-i386.iso
687M  precise-server-i386.iso
685M  ubuntu-11.04-desktop-i386.iso
680M  lubuntu-11.04-desktop-i386.iso
658M  lubuntu-11.10-desktop-i386.iso
620M  linuxmint-12-gnome-cd-nocodecs-32bit.iso
124M  puppy-slacko-5.3-MAIN.iso

```

---

### Post by HadrianKross on 2012-01-16
thanks

---

### Post by devinwhite717 on 2012-03-16
This is a nice collection of the most used commands: [http://commands.tips-linux.net]("http://commands.tips-linux.net/")

---

