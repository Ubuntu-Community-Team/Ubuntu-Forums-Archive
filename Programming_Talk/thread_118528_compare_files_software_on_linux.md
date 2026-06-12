---
title: "compare files software on linux"
date: 2006-01-17
forum: Programming Talk
---

### Post by lanchen on 2006-01-17
Hi all,

could you please recommend a good software to compare two files of source codes? I prefer graphical one.

Many thanks,

Lan

---

### Post by frodon on 2006-01-17
i use tkdiff.

---

### Post by joselin on 2006-01-17
You can use meld ([http://meld.sourceforge.net/]("http://meld.sourceforge.net/"))

Regards

---

### Post by lanchen on 2006-01-17
tkdiff is working. thx

---

### Post by kperkins on 2006-01-17
Kompare
Why doesn't gnome have a diff gui?

---

### Post by ardchoille on 2006-01-17
open a terminal and do:

```

diff /path/to/file-one /path/to/file-two

```

diff will spit out the differences, or diff will return nothing if there are no differences.

---

### Post by frodon on 2006-01-18
[QUOTE=kperkins]Kompare
Why doesn't gnome have a diff gui?[/QUOTE]it has one, but i don't rmember the name ... maybe gdiff.

---

### Post by kperkins on 2006-01-18
[QUOTE=frodon]it has one, but i don't rmember the name ... maybe gdiff.[/QUOTE]
Nope gdiffis an emacs macro.  I did find meld, but the version in breezy won't open any files for me.  It freezes at the open file dialog when browsing.  (with a glibc error.  Might need a newer version--the newest is 1.1.2 and the one in breezy is 1.0.0.  I may try upgrading it later--looks like they use the Debian package without any changes.

---

### Post by purpleturtle on 2006-02-02
Winmerge on Windows in the best differ I've ever used (and it's free..) I'd be happy if I could find one as good on Linux (I wonder if it works under Wine....? ) although to be fair I haven't spent much time looking yet...

---

### Post by frodon on 2006-02-03
all of them are as good as winmerge i think, try them and see ;)

---

### Post by Greg2 on 2006-02-03
[QUOTE=kperkins]I did find meld, but the version in breezy won't open any files for me.  It freezes at the open file dialog when browsing.  (with a glibc error.  Might need a newer version--the newest is 1.1.2 and the one in breezy is 1.0.0.  I may try upgrading it later--looks like they use the Debian package without any changes.[/QUOTE]
I’ve been using meld 1.0.0-1 from the breezy-backports without any problems.

---

### Post by dpm on 2006-02-05
I had been using KDiff3 and WinMerge in Windows. As a matter of personal taste, I preferred KDiff3 (faster and more flexible), even though I found the Winmerge GUI better.

When I switched to Linux, I found I could still use KDiff3, or even better, Meld.

I remember having a couple of problems with version 1.0.0, but those have since long been corrected by the 1.1.2 version available from the backport repositories.

A *very* nice thing that Meld has got (apart from the nice GUI and GNOME integration) is syntax highlighting. It is also very easy to set it up to ignore CVS keywords, comments, etc.

The only thing in which KDiff3 might be superior is in the merging capabilities.

I'd just give all options a try and use the one you're feeling more comfortable with.

---

### Post by entangled on 2006-02-05
gvim also gives a good view of diffs, when you open a second file with the 'Split Diffs with ...' option. 
Has the advantage of using syntax highlighting. 
Has the disadvantage (AFAIK) that it is always case-sensitive.

---

### Post by joselin on 2006-02-05
[QUOTE=kperkins]Nope gdiffis an emacs macro.  I did find meld, but the version in breezy won't open any files for me.  It freezes at the open file dialog when browsing.  (with a glibc error.  Might need a newer version--the newest is 1.1.2 and the one in breezy is 1.0.0.  I may try upgrading it later--looks like they use the Debian package without any changes.[/QUOTE]

I have the same problem too. What i do is, in the choosen file dialog i select file or folder comparison and the press ok. After that, you can change both paths or files in the main screen.

Regards.

---

### Post by kperkins on 2006-02-05
I did download meld 1.1.2 (debian) and installed it, and it works great.  Sorry I didn't get back before this, but I forgot. :(

---

### Post by dpm on 2006-02-05
[quote=joselin]I have the same problem too. What i do is, in the choosen file dialog i select file or folder comparison and the press ok. After that, you can change both paths or files in the main screen.

Regards.[/quote]

As I said on my last post, Meld 1.1.2 is available in the breezy-backports repositories. The problem you're referring to with your workaround is fixed on that version.

You may want to give it a try.

BTW, I did not know you could view diffs with gvim, I'll give it a go tomorrow...

Cheers.

---

### Post by joselin on 2006-02-06
I just download from the backports and works fine.

Thanks.

---

### Post by schickm on 2008-05-28
Yep, meld hands down!  I can't speak for it's merging capabilities, but it's display is far superior to tkdiff.

---

### Post by kaligus on 2008-07-18
I tried meld for two weeks... winmerge still wins (in wine) sadly.

The ability to save "projects" and remerge them tomorrow or next week without remembering the directories to find everything in etc. is most awesome... 

If someone knows software that hits the best of meld *AND* winmerge that is native I would love to hear about it

---

### Post by kknd on 2008-07-19
> **joselin said:**
> you Can Use Meld ([http://meld.sourceforge.net/]("http://meld.sourceforge.net/"))

Regards

+1

---

### Post by orange_roughy on 2009-08-16
None of the suggestions in this thread can BOTH:

* ignore whitespace
* compare all files in a two directories (i.e., specify two directories for diffing instead of two files)

As of 16-08-2009, Meld can do the latter but not the former. All other suggestions can't do either of these. WinMerge does both. Do I really have to boot up Windows for advanced GUI diffing?

---

### Post by Can+~ on 2009-08-16
> **orange_roughy said:**
> None of the suggestions in this thread can BOTH:

* ignore whitespace
* compare all files in a two directories (i.e., specify two directories for diffing instead of two files)

As of 16-08-2009, Meld can do the latter but not the former. All other suggestions can't do either of these. WinMerge does both. Do I really have to boot up Windows for advanced GUI diffing?

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-4.png[/IMG]

And if you still have trouble, you can write your own [regular expression]("http://docs.python.org/library/re.html").

---

### Post by rduke15 on 2010-01-19
Indeed, I found Meld to be the best in Linux, and as Can+ pointed out, it certainly can diff directories and ignore whitespace (and comments, or whatever you can find a regexp for)

One thing for which I had to install WinMerge in my XP VM today is the ability to save a clear html report of differences. Unfortunately, Meld cannot export. And raw diff output is unreadable for normal people. So without WinMerge, I would have had to produce a readable file with formatting and highlighting myself.

PS: I found that [WinMerge Portable]("http://portableapps.com/apps/utilities/winmerge_portable") seems to work fine under Wine, so for these special cases, you may not even need a Windows VM.

---

### Post by zippo_yp on 2010-02-25
> **rduke15 said:**
> Indeed, I found Meld to be the best in Linux, and as Can+ pointed out, it certainly can diff directories and ignore whitespace (and comments, or whatever you can find a regexp for)

One thing for which I had to install WinMerge in my XP VM today is the ability to save a clear html report of differences. Unfortunately, Meld cannot export. And raw diff output is unreadable for normal people. So without WinMerge, I would have had to produce a readable file with formatting and highlighting myself.

PS: I found that [WinMerge Portable]("http://portableapps.com/apps/utilities/winmerge_portable") seems to work fine under Wine, so for these special cases, you may not even need a Windows VM.


I used to use beyond compare in windows, and when I switch to ubuntu, I've been using it, it is also quite good, it also works fine with wine!

I have to use bitwise tunnelier as a ftp to sftp bridge, it also work fine in wine, but a bit slow, so if there's any nicer way which build a bridge between ftp and sftp in Linux? Guys...

---

### Post by Hellkeepa on 2010-02-25
HELLo!

A bit off topic, but why not just use "ssh" for it?

Happy codin'!

---

### Post by drevicko on 2010-05-18
> **rduke15 said:**
> Indeed, I found Meld to be the best in Linux, and as Can+ pointed out, it certainly can diff directories and ignore whitespace (and comments, or whatever you can find a regexp for)

One thing for which I had to install WinMerge in my XP VM today is the ability to save a clear html report of differences. Unfortunately, Meld cannot export. And raw diff output is unreadable for normal people. So without WinMerge, I would have had to produce a readable file with formatting and highlighting myself.

PS: I found that [WinMerge Portable]("http://portableapps.com/apps/utilities/winmerge_portable") seems to work fine under Wine, so for these special cases, you may not even need a Windows VM.

Another limitation of Meld I've found is it's (apparent, and I did look around..) inability to diff folders on fat32 partitions without comparing contents. With lots of big files (like music), this is problematic, to say the least! (though it didn't break anything permanently :o ). With winmerge, you tell it to just compare file sizes or dates or whatever.

I tried midnight commander - has a folder compare thingy, but it didn't seem to do anything. Didn't look too hard as to why.

Meld is nice though. For souce code management especially, with it's integrated version control diffing.

---

### Post by hil on 2010-08-23
I looked at meld's screenshot. It was impressive. I used [diffuse]("http://diffuse.sourceforge.net/") and found it was superior than windiff. It can compared even words or characters  on a line. Has anyone talked about diffuse in the thread or used it?

---

### Post by sitex on 2010-09-03
[SIZE=2]Hi all, :KS

There is a free and open source software for this job called Melt Diff  Viewer

Meld is a tool which allows the user to see the changes  in, and merge between, either two files, two directories, or two files  with a common ancestor.

you can install it with the terminal command : **sudo apt-get install meld**

and also you can install with Ubuntu Software Center by searching for "meld"

[click here see how it install on ubuntu with more details and screen shots]("http://solutionz.yolasite.com/linux.php")[/SIZE]

---

### Post by Hellkeepa on 2010-09-03
HELLo!

**sitex**: Yeah... That would be what was stated in the [second reply](http://ubuntuforums.org/showpost.php?p=663859&postcount=3) to this thread, and supported many times over in latter responses.

Don't misunderstand me: I love Meld as well. However, reading the thread before answering is generally looked upon as common courtesy. Plus, it's also a smart thing for do to for ones own sake too, as there could be lots of useful information one didn't know about on it.

Happy codin'!

---

### Post by James78 on 2010-09-03
> **orange_roughy said:**
> None of the suggestions in this thread can BOTH:

* ignore whitespace
* compare all files in a two directories (i.e., specify two directories for diffing instead of two files)

As of 16-08-2009, Meld can do the latter but not the former. All other suggestions can't do either of these. WinMerge does both. Do I really have to boot up Windows for advanced GUI diffing?
I use Kompare, and I don't know about the whitespace, but you can compare all files in a directory, even recursively. I think it might ignore whitespace too though.

---

