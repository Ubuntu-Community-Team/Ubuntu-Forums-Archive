---
title: "Bash Scripts weirdness"
date: 2008-09-28
forum: Programming Talk
---

### Post by Npl on 2008-09-28
I cant figure out how bash invokes external programs. Im trying to call unzip with a filename (which might contain spaces in its path), but nothing works so far. To illustrate the point:
```
#! /bin/bash
unzip \"~/a b c.zip\" ;
```
This result in the output:

unzip:  cannot find or open "~/a, "~/a.zip or "~/a.ZIP.

I tried with single-quotaion mark aswell, with the same result. Cant find anything in the documentation.

---

### Post by howlingmadhowie on 2008-09-28
what's the name of the file you're trying to unzip?

you can escape a space using a backslash. for example, if i wanted to unzip a file called "file a.zip" i could do so by typing:

```
unzip file\ a.zip
```

---

### Post by Npl on 2008-09-28
yeah i know, the problem is doing that **from within scripts** (save the above code into test.sh and run it). The above example is simplified, I want to have a variable for the path then do
```
unzip ${mediadir}/Data_linux.zip;
```
I cant guarantee the mediadir variable has no spaces. If it has spaces, then I get the problem above. 
```
#! /bin/bash
test1=\~/a\ b\ c
# FAILS
echo unzip ${test1}/file.zip;
unzip ${test1}/file.zip;

# FAILS
echo unzip \"${test1}/file.zip\";
unzip \"${test1}/file.zip\";

# FAILS
echo unzip \'${test1}/file.zip\';
unzip \'${test1}/file.zip\';
```

---

### Post by Sub101 on 2008-09-28
to execute from within a script:

```
exec unzip "file name"
```

That what your after?

---

### Post by Npl on 2008-09-28
Well, unzip "file name" works... I dont have an idea why I dint try this, I was sure I did :oops: . Guess I started to escape everything while I still had echos before the commands for testing.

---

### Post by Npl on 2008-10-03
Good Lord, why is it that everytime I try doing something productive in Linux I got to deal with weird bugs?

Seems to me that unzip and/or bash is the culprit, it sometimes works from the shell and then doesnt again... it somehow depends on using the "set -e -f" command in bash and even if I run the script as root or not (no problems with privileges)

I get some garbled error-messages if it breaks like : ".ZIP.or /mnt/data/XP1.zipen /mnt/data/XP1.zip". Seems like some heap or stack corruption.

```
#! /bin/bash

set -e -f
read -p "target: " installdir
readonly installdir

mediadir=/mnt
mediadirLinux=/media/Volume/NeverWinter\ Nights
readonly mediadir
readonly mediadirLinux


mkdir -p ${installdir}
cd ${installdir}


echo "Unpacking Game Data"

unzip -q "${mediadir}/Data_Shared.zip"
unzip -q "${mediadir}/Data_linux.zip"

unzip -oq "${mediadir}/data/XP1.zip"
unzip -oq "${mediadir}/data/XP2.zip"

echo "Unpacking Linux-Client"
tar -xzf "${mediadirLinux}/nwclientgold.tar.gz"
tar -xzf "${mediadirLinux}/nwclienthotu.tar.gz"
echo "Unpacking Linux-Update"
tar -xzf "${mediadirLinux}/English_linuxclient169_xp2.tar.gz"

echo "Writing CD-Keys"
echo >./nwncdkey.ini ';These are your CD Keys for Neverwinter Nights.
;DO NOT share these CD Keys with ANYONE.
;Apart from this installation, or when registering with the Official Neverwinter Nights Community Site [http://nwn.bioware.com], BioWare and Infogrames will NEVER ask you for this CD Key.

[CDKEY]
Key3=<snip>
Key2=<snip>
Key1=<snip>'
chmod 644 ./nwncdkey.ini

echo "Fixing nwn startup-script"
echo >./nwn '#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
# export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@'
chmod 755 ./nwn

echo "Running Biowares fixinstall"
./fixinstall

echo "Listing missing 32-bit libraries (eventually incomplete)" 
if ! LANG=C LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH ldd nwmain | grep "not found"
then
    echo ""
fi

echo "Installation is done
If you are missing libraries you need to find and install them"
```

---

### Post by geirha on 2008-10-03
The error message you mention sounds like the error unzip gives when it can't find the archive you tell it to decompress. Try adding a sanity check in front of each unzip to figure out which one it is:
[php]
[ -f "${mediadir}/Data_Shared.zip" ] && echo "Unzipping ${mediadir}/Data_Shared.zip" || exit 1
unzip -q "${mediadir}/Data_Shared.zip"
[/php]

---

### Post by Npl on 2008-10-03
I dunno what unzip is doing, but the files are definitly there. The script works if I remove "set -e -f" and run it as user, the script never worked as root.. and just for the fun of it, if I add your lines between unzip-commands it works aswell(as user or root). Seems like a pretty weird bash-bug to me.

Im pretty pissed right now, wasting hours to get this simple script working.. Might get back to it tomorrow to see if I can narrow this issue down.

---

### Post by Sub101 on 2008-10-03
What i often find useful is adding -v to the #!/bin/bash ie. 

```
#!/bin/bash -v
```

I would expect it would tell you exactly where the problem is if you run it from within a terminal. (start in terminal not double click)

---

### Post by Npl on 2008-10-03
OMG, I think I found the weirdness - seems like a carriage return found its way into the textfile.. :(
I only used gedit and some copy and paste, now im using a ******* hexeditor to find carriage returns.. **** gedit just DIED for me. it hasnt even an option to force specific Linefeeds

---

### Post by mssever on 2008-10-03
> **Npl said:**
> ```
#! /bin/bash
test1=\~/a\ b\ c
# FAILS
echo unzip ${test1}/file.zip;
unzip ${test1}/file.zip;

# FAILS
echo unzip \"${test1}/file.zip\";
unzip \"${test1}/file.zip\";

# FAILS
echo unzip \'${test1}/file.zip\';
unzip \'${test1}/file.zip\';
```
I don't know why you're trying to escape the quotes, when you need their special function to protect you from spaces. This works: ```
unzip "$test1/file.zip"
# or
unzip "${test1}/file.zip"
```Both options above are equivalent. Also, notice that the only time you need to terminate lines with a semicolon is if you want to put multiple logical lines on one line.

---

### Post by Npl on 2008-10-03
mssever: using "just" quotes was the first thing I tried and it dint work(for other reasons), theres the complete script in one of my posts a bit below.

Anyway, the script works fine now... lessons learned:
[LIST][*]Dont expect Gedit to use consistent Linefeeds[*]Hell breaks lose if you have carriage-returns in bash-scripts[*]GHex calls itself a hex-editor and cant search for Hex-Values[/LIST]

---

### Post by mssever on 2008-10-03
> **Npl said:**
> mssever: using "just" quotes was the first thing I tried and it dint work(for other reasons)I'm curious what those other reasons were, because I can't think of any reason why it wouldn't work--with the possible exception of the variable containing unescaped double quotes.

> 
[LIST]
[*]Dont expect Gedit to use consistent Linefeeds
[/LIST]
I've used gedit for a long time, and I've never seen it terminate lines with anything other than \n. I can say with certainty that your problem had nothing to do with gedit, unless you had some buggy plugin installed.
> 

[LIST]
[*]Hell breaks lose if you have carriage-returns in bash-scripts
[/LIST]
That's not surprising. Smart OSes use \n to terminate lines, not \r and certainly not \r\n. And why shouldn't shell scripts expect smart behavior? :)
> 

[LIST]
[*]GHex calls itself a hex-editor and cant search for Hex-Values
[/LIST]

Bless is the hex editor I use for those rare occasions when I have use for one. It can search for hex values. But there are easier ways to remove \r characters from files. Vim shows them directly as ^M characters. You can delete them, or search and replace them just like you can any other character, with the caveat that you have to hit ^V before typing ^M to prevent ^M from being interpreted as a control sequence.

---

### Post by Npl on 2008-10-03
> **mssever said:**
> I'm curious what those other reasons were, because I can't think of any reason why it wouldn't work--with the possible exception of the variable containing unescaped double quotes.Like... having a \r (carriage return) right after the enclosing quote, causing the filename to be wrong... but hey even better it **sometimes** worked, but not always.
> **mssever said:**
> I've used gedit for a long time, and I've never seen it terminate lines with anything other than \n. I can say with certainty that your problem had nothing to do with gedit, unless you had some buggy plugin installed.I`ve used **good** Texteditors for a long time and I never thought about a **good** Texteditor to add an \r into the text. I dont use plugins, the trick is to copy and paste. If a \r is in the clipboard Gedit will just silently add it, I taken a few commands from a forum-thread so there you go.
> **mssever said:**
> That's not surprising. Smart OSes use \n to terminate lines, not \r and certainly not \r\n. And why shouldn't shell scripts expect smart behavior? :)You mean they are so smart that the first moron they encounter completely freaks them out so they roll over and die. Sounds like inverted darwinism to me :)
Seriously though, can you explain why the same script works as user, but not as root... (access priviledges werent a concern). I would expect atleast consistency in failure, or even better just ignore damn whitespaces.> **mssever said:**
> Bless is the hex editor I use for those rare occasions when I have use for one. It can search for hex values. But there are easier ways to remove \r characters from files. Vim shows them directly as ^M characters. You can delete them, or search and replace them just like you can any other character, with the caveat that you have to hit ^V before typing ^M to prevent ^M from being interpreted as a control sequence.UEdit is the one I typically use.

---

### Post by mssever on 2008-10-03
> **Npl said:**
> Like... having a \r (carriage return) right after the enclosing quote, causing the filename to be wrong... but hey even better it **sometimes** worked, but not always.That mostly makes sense, since \r is a legal character in a filename (every character except / and \0 is legal). But I don't understand why it worked as a normal user nut not root.
> I`ve used **good** Texteditors for a long time and I never thought about a **good** Texteditor to add an \r into the text. I dont use plugins, the trick is to copy and paste. If a \r is in the clipboard Gedit will just silently add it, I taken a few commands from a forum-thread so there you go.So you're complaining that Gedit pasted in the text without corrupting it? It would be a bug for it to skip over the \r. I do think that it would be nice to provide some visual indication of the \r's presence, although the ability to see indications of spaces and tabs (and thus distinguish them) is only provided by a plugin.

---

### Post by Npl on 2008-10-03
> **mssever said:**
> So you're complaining that Gedit pasted in the text without corrupting it? It would be a bug for it to skip over the \r. I do think that it would be nice to provide some visual indication of the \r's presence, although the ability to see indications of spaces and tabs (and thus distinguish them) is only provided by a plugin.It corrupted it by changing the meaning (it corrupted the whole file at the same time), a \r\n means linefeed, its just another encoding for 1 character. There is no bold, italics or big letters in textfiles, and no \r if it has Unix-Linefeeds.
You wouldnt want to copy an ANSI-encoded text into a UTF8-File by numeric value either (ala Hex-Editor), but by character representation.

---

### Post by mssever on 2008-10-04
> **Npl said:**
> It corrupted it by changing the meaning (it corrupted the whole file at the same time), a \r\n means linefeed, its just another encoding for 1 character. There is no bold, italics or big letters in textfiles, and no \r if it has Unix-Linefeeds.
You wouldnt want to copy an ANSI-encoded text into a UTF8-File by numeric value either (ala Hex-Editor), but by character representation.
Um, gedit isn't designed to deal with the Windows world. Only in MS-Land does \r\n equate to a single character meaning 'end of line.' In the *nix world, \n marks the end of a line, and \r is Just Another Character. Since it's Just Another Character, deleting it would cause data corruption. So, since \r also happens to be nonprintable in *nix-land, gedit chooses not to print it. I happen to think that's suboptimal, but there's no reason why gedit should endow \r with special meaning it doesn't have.

You could ask for an editor that understands Windows, but don't expect to find something like that coming from the Gnome project.

And by the way, you say that gedit changed the meaning of your text. But it isn't human. How can it know the meaning?

---

### Post by yoda2031 on 2008-10-04
First off, spending a few hours solving something shouldn't be unexpected.  Even if it seems simple, in the world of computing it rarely is.

I had a "secondly" but just realised the guy above me already outlined all the problems with your "\r" complaints.

The script includes the "~" character in filenames, so I'm assuming you're putting the files the script wants to operate on in /root when attempting to run it as root?  Don't be offended by that question, either, it's an easy mistake to make to put the files in "/home/root" instead...

---

