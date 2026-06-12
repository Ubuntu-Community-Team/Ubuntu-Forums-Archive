---
title: "Quick and dirty back up for mp3s using xargs, find, and sed"
date: 2007-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by morphet on 2007-01-02
Quick and dirty Howto: How to back up your mp3s and ONLY your .mp3s, while still preserving their directory structure. The use of this method will not copy any directory that does not contain an mp3.

Before we start, please know that this is my first tutorial, and it is unnecessarily convoluted, and will screw your system up if you are not careful and/or don't know more than I do. Please read through it first so you know that it does what you need. I tested it in an iMac g5 (ppc64). I will be happy to answer any questions, but I am a noob, so don't expect any serious support. The way to undo the changes is to delete the directories you create, so keep those in mind, and experiment with a dummy location first.

I searched the forums and the net at large for a method to back up my mp3s and I found many interesting ones. However, none really did what I needed. So, over the course of the last 20 hours or so, I pieced many excellent pieces of advice into this, my first HOWTO. It goes without saying that the substitution of mp3 for any other filename fragment is trivial.

Let's assume "/originalPath/" is where your files currently are. They are mixed with every other type of file, which makes this difficult right? Fret not.

This guide will treat "/destinationPath/" as the path you want the files to go to. 
Type in "mkdir /destinationPath/" if you haven't done so. Remember not to type in "destinationPath", but use the path you want instead. 

There are two systems of backing up. The first, and simplest, will pool all the mp3s into a single directory. While this can be useful for some situations, it will lead to some losses if your mp3's happen to share names.

The following line was blantantly stolen from hod139, in his excellent advice [http://ubuntuforums.org/showthread.php?t=308349&highlight=%7C+xargs+cp+.%2F%7B%7D]("http://ubuntuforums.org/showthread.php?t=308349&highlight=%7C+xargs+cp+.%2F%7B%7D")
```
find /originalPath/ -name *.mp3 -print0 | xargs -0 -i cp ./{} /destinationPath/
```

For those curious about this: The "find /originalPath/ -name *.mp3 -print0" part finds every file that ends with .mp3, and passes it (via the -print0 argument) to "xargs", which replaces the "{}" with the filename. So. practically, you are telling your computer to "cp /originalPath/filewhatever.mp3 /destinationPath/"

This might take hours. You can add a " -v" after the "cp" to see your computer do the magic. The result is a huge dir filled with your mp3s, minus those unfortunate enough to share a name with the most recent who got copied. It might be very informative, but less useful than the next method:


Now, if you are interested in a tree structure like the one you had, minus everything that is not an mp3, and without the dirs that do not contain mp3s, read on.

Thanks to HadroLepton, whose excellent advice [http://ubuntuforums.org/showthread.php?t=328097&highlight=moveuptwodir]("http://ubuntuforums.org/showthread.php?t=328097&highlight=moveuptwodir") I blantantly stole this next part from.

First you type this into the terminal:
```

find ./originalPath/ -name *.mp3 -fprintf YourCopyingScript.sh 'mkdir -p "/destinationPath/%h" \n cp "%h/%f" "/destinationPath/%h/"\n'
```

This will create a file called YourCopyingScript.sh. This text file contains two lines for each matching file found. The first line says mkdir -p "/destinationPath/originalPath/". This will create the directory structure you had, but inside of the /destinationPath/ you specify. The second line will simply copy the file to that new compounded path. There is an error, though. Each line has a nasty "/./" where a "/" should go. We replace them by typing:

```
sed 's/\/.\//\//' YourCopyingScript.sh > YourCopyingScript2.sh
```


This will produce a script called YourCopyingScript2.sh, where the paths have a clean format that cp can understand. Now, for the moment of truth. Type:

```
sh YourCopyingScript2.sh
```

This instructs the computer to execute every line in YourCopyingScript2.sh

This should leave you with a neat directory structure under the path you chose, filled only with your mp3s and their directories. I know anyone with more than a couple of weeks experience in Linux will laugh at the unnecessary steps, but hey, it worked for me. Thanks for reading, and contribute a better method if you have one!

---

### Post by r0cks0ul on 2010-08-21
darn glad I found this I've been trying so many samples i found on the internet and this made my day. 

Ton of Thanks to you!!!! :KS

---

