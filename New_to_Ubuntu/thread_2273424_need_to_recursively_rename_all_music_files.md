---
title: "need to recursively rename all music files"
date: 2015-04-13
forum: New to Ubuntu
---

### Post by nick180 on 2015-04-13
Excuse my ignorance but i need to use the rename command to remove all instances of 1_000 & _000 that were added to my music tracks after being recovered from a dead hard drive.

Will this point the search to my external hard drive named Crwsaders2...?

$ cd /media/nick/Crwsaders2

On this HDD is a folder named Music and standard layout within that are all the sub-folders titled by artist then sub-folders to album and in each album are the tracks.

Can I then use this...?

find Music -depth -name '*_000' -exec rename _000 '' {} \;

---

### Post by Lars Noodén on 2015-04-13
Check the manual page for **rename** to get the details.  It uses normal [perl regular expressions](http://manpages.ubuntu.com/manpages/trusty/en/man1/perlre.1.html).  But here is one guess:

```

find . -name '*1_000' -exec rename -n 's/[color=blue]1_000$[/color]//' "{}" \;

```

Then remove the -n if that does what you need.

---

### Post by philinux on 2015-04-13
I had a similar situation and used eyed3.

[http://ubuntuforums.org/showthread.php?t=1516744&](http://ubuntuforums.org/showthread.php?t=1516744&)

---

### Post by nick180 on 2015-04-13
can someone just verify if my first question is correct please...?

That using this :

nick@base1268-ubuntu:~$ cd /media/nick/Crwsaders2

[COLOR=#000000]which when entered returns this :

[/COLOR]nick@base1268-ubuntu:/media/nick/Crwsaders2$[COLOR=#000000]

means that the terminal is now performing whatever I ask within my drive named Crwsaders2...? ... and therefore I can go ahead and perform the 'rename' surgery on my Music folder which is of course on that very same drive...?[/COLOR]

---

### Post by Lars Noodén on 2015-04-13
It should.  'cd' will move you to the directory you specify after 'cd'  You can see which directory you are currently working in by using 'pwd'

---

### Post by nick180 on 2015-04-13
Thanks Lars... gotta start somewhere learning the cmds for Debian based arguments.... hope I got that right.... Ubuntu is a Debian distro right...?

Can you point me to a good easy to follow manual that will allow me to look up expressions and arguments to have a go at working out how to use the terminal to make things happen without having to ask a trillion questions here please....?

Also while i have your attention I ran 'sudo apt-get update' to ensure I have packages up-to-date and got the following error list at the end:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DF9B28CA252A784
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)

My guess is... obviously I have no 'PUBKEY' and I need one......? 
And secondly It looks like I've managed to download chrome from 2 sources in 64 and 32 bit.....?

Fixes for both and an explanation of what the fixes are doing so I can learn.... if you can spare the time to do so it would be much appreciated... :guitar:

Nick

---

### Post by papibe on 2015-04-13
> **nick180 said:**
> Can you point me to a good easy to follow manual that will allow me to look up expressions and arguments to have a go at working out how to use the terminal to make things happen without having to ask a trillion questions here please....?
Here are some useful links: [Command line resources]("https://help.ubuntu.com/community/Links#Command_Line").
Regards.

---

### Post by nick180 on 2015-04-13
BTW.... just playing around learning about the single 'tree' as a maze and how to navigate with 'cd' and 'pwd' to confirm where you are although that's surely a bit unnecessary as whatever is shown before the $ is where you are currently....???

Anyway.... I entered this cmd line :

'$ cd /media/nick/Crwsaders2/Music/U2/All That You Can't Leave Behind' doing so to gain root to put me at this U2 album...to then list all it's files with 'ls'

but.... it has taken me to this :

>blinking cursor

and I can't seem to get out of it... I've tried to look it up and even google it.... all to no avail... what is it and how did i get there by mistake..? must be the /All followed by a space...? I'm just guessing at the syntax but interested to know so I can avoid it

---

### Post by papibe on 2015-04-13
It looks like there's a quote missing so bash is still waiting for you to finish entering the command.

Press Ctrl+C to cancel what you were typing and getting a prompt again.

Try using "s to encapsulate 's:
```
cd "/media/nick/Crwsaders2/Music/U2/All That You Can't Leave Behind"
```
Let us know how it goes.
Regards.

---

### Post by nick180 on 2015-04-13
@ papibe.... Many thanks... that did the trick.... so if I'm guessing right here I'd say that if there is a space in a filename (as was the case with the music track name having several words) it needs the entire command string encased in quotes...? I also note that everything is case sensitive.

So... now I should be able to move onto working out how to remove all the additional 1_000 and _000 instances that were added by the recovery process with a single line of cmd.

If we change directory root to a given folder (Directory) will the next command line perform what we choose on everything inside that folder including all sub-directories... unless we specify of course...?

---

### Post by Lars Noodén on 2015-04-14
> **nick180 said:**
> Thanks Lars... gotta start somewhere learning the cmds for Debian based arguments.... hope I got that right.... Ubuntu is a Debian distro right...?

Yes, Ubuntu is derived from Debian, but I hope that in the future it is based on Devuan.  ;)  

Rename follows the usage pattern       *rename [ -v ] [ -n ] [ -f ] perlexpr [ files ]*  
where *perlexpr* is a [plain old perl regular expression](http://perldoc.perl.org/perlre.html) telling what you want to do to the file names.  To see the details for 'rename' try entering 'man rename' to see the manual page.  All programs have manual pages and are worth looking at, but they do vary in quality.  

The pattern *s///* substitutes what is between the first and second slashes with whatever is between the second and third slashes.  So *s/A/B/* will substitute the first A found with a B. To get all the A's you'd modify it a little to apply the search and replace to the whole line: *s/A/B/g*.  Here is a concise summary of perl patterns (aka PCRE) with some examples: [https://www.cs.tut.fi/~jkorpela/perl/regexp.html#ex](https://www.cs.tut.fi/~jkorpela/perl/regexp.html#ex)

---

### Post by user_of_gnomes on 2015-04-14
You could also consider using [Easytag]("https://wiki.gnome.org/Apps/EasyTAG") to batch-rename music and movie files.

---

### Post by nick180 on 2015-04-14
> **user_of_gnomes said:**
> You could also consider using [Easytag]("https://wiki.gnome.org/Apps/EasyTAG") to batch-rename music and movie files.

So I've grabbed Easytag but of course I will need to learn HOW to use the expressions to rename just as I'm doing with the terminal.... but thanks for the tip... I'm sure it'll come in handy somewhere along the line.... ;)

I'm concentrating on learning my way around the power of the Terminal for now and trying to use 'rename' with regular perlexp seems like a good place to begin to understand the syntax of this language... and clean up these recovered filenames in the process.

---

### Post by HermanAB on 2015-04-14
There is a nice photo batch processor called phatch.  It can probably do what you want, plus a whole lot more.

---

### Post by haplorrhine on 2015-04-14
> **nick180 said:**
> Can you point me to a good easy to follow manual that will allow me to look up expressions and arguments to have a go at working out how to use the terminal to make things happen without having to ask a trillion questions here please....?

I liked this article on regex.
[http://www.zytrax.com/tech/web/regex.htm](http://www.zytrax.com/tech/web/regex.htm)

---

### Post by Keith_Helms on 2015-04-14
> **nick180 said:**
> @ papibe.... Many thanks... that did the trick.... so if I'm guessing right here I'd say that if there is a space in a filename (as was the case with the music track name having several words) it needs the entire command string encased in quotes...? I also note that everything is case sensitive.

So... now I should be able to move onto working out how to remove all the additional 1_000 and _000 instances that were added by the recovery process with a single line of cmd.

If we change directory root to a given folder (Directory) will the next command line perform what we choose on everything inside that folder including all sub-directories... unless we specify of course...?

An alternative to enclosing filenames in quotes is to escape the spaces.   If you have a file named **A File** you could either reference it with **"A File"** or **A\ File**.  The backslash is the escape character which tells the shell that the next character is to be treated as is and not used as a pattern character or delimiter.

Your statement about the next command performing what we choose on sub-directories is not correct.  Most commands operate just on the current directory and you have to explicitly use a -r or -R option to tell it to also look in subdirectories.   Use **man *command*** to see what the options are for a given command.

---

### Post by nick180 on 2015-04-14
Thanks very much lovely people.... I've got loads to read and learn about this new language of ERE's and BRE's

Back in the day... 1981 to be precise... I started to do a 'distance' Uni course in basic programming using Pascal on an Apple IIe with twin floppy's (the 128k model :rolleyes:).... loved it and passed my end-of-year exams.... however, combination of circumstance took me down a different fork in life's road after the first year (girl... it's always a girl) and Uni stopped right there

Now I really wish it hadn't.... 1981 was a prime time to enter the field of Computer programming.... like a first prize lottery ticket if you were good at logic....

---

