---
title: "Can't access my installs"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by pheasant golf on 2012-02-28
Hello.  I have downloaded some packages (Thunderbird Lightning, the Ubuntu updates with accessories) and they do not appear anywhere other than the list of downloaded (installed) items from the ubuntu software center.  They are not to be found anywhere I can access them.  I have had success installing items in the past (last 2 days).  How can I view all my downloads and how do I activate them?  I quit windows for my business 2 days ago and need to get up to speed.  Please help.  Linux rocks.  I'm the shaky one.

---

### Post by baumanno on 2012-02-28
Did you download them from a webpage? Because if so, you should find a *.deb-file somewhere in your /home-directory (most likely is 'Downloads') and installing those is as simple as clicking on the file.

If you installed via the SoftwareCenter, this should have done all the magic for you, so have you tried typing the application's name into the starter? (I'm talking about the input-field that appears when you click in the top left corner)

I believe 'Lightning' can be installed via the Thunderbird Add-On-Interface "Extras --> AddOns".

---

### Post by audiomick on 2012-02-28
Which version of Ubuntu are you on? Are you using the Unity desktop? If not, which one?

It makes a bit of a difference with where you have to look for installed applications.

---

### Post by pheasant golf on 2012-02-28
I am not sure  I am using Unity.  Is Unity preloaded?

---

### Post by pheasant golf on 2012-02-28
Is the starter the "Terminal"?

---

### Post by audiomick on 2012-02-28
> **pheasant golf said:**
> I am not sure  I am using Unity.  Is Unity preloaded?
That depends on which version of Ubuntu it is.
Unity is the default in 11.04 (the last version) and 11.10 (the current versions. Earlier versions used the Gnome desktop environment.

I don't understand your question about whether the terminal is the "starter". Which starter?

---

### Post by baumanno on 2012-02-28
If you haven't knowingly changed your Window Manager your probably working with Unity.

No, the starter is what appears when you hit the Windows-Key on your keyboard (or click in the top left corner).

But if you know a little about the Terminal, these are the commands used for installing software:

Update software repositories (do this prior to anything but deleting software, as it supplies you with fixes, etc):
```
$sudo apt-get update
```

Install software <NAME>:
```
$sudo apt-get install <NAME>
```

Delete software <NAME> and all of its config:
```
$sudo apt-get purge <NAME>
```

Update your packages:
```
$sudo apt-get upgrade
```

Or use
```
$sudo apt-get --help
```

for, erm... help...
BTW, apt-get is what's essentially behind Synaptic, the Ubuntu packet-manager.

---

### Post by pheasant golf on 2012-02-28
thank you.  I wish I could see the names of the downloads in one place.  The folder downloads on the "home " screen says "0" contents.  Not sure what that is about.

---

### Post by audiomick on 2012-02-29
I think you are mixing up terminology a bit. You seem to be saying "download" when you mean you have installed something with the software centre. Whilst it is true that something gets downloaded, common practice is to refer to the process of adding a program via the software centre as "installing".

By "download", what is generally meant is when you go to a web site with your browser and transfer a file to your computer from there. This may be a file to install a program, but must not always be.

If, as I believe, you have installed programs via the software centre, they will not appear in the downloads folder. That folder is where files land when you load down something from the internet with firefox.

---

### Post by Tyggna on 2012-02-29
I think I see the problem.  There's a very difficult shift in software install mentality between Windows and Linux--and if you miss that difference can cause a lot of problems.

Here's a brief synopsis of the difference:
Windows -- find a program you like, go to its website, download an executable, go through an installer, run your new program.

Linux -- go through your installer to find the program in a repository, and then run it.  

You installer is called a package manager, in the case of ubuntu it's called aptitude.  Ubuntu makes it very easy to use, just go the add/remove programs and search in a list for the program you want.  Select it, and it'll install.

You can still do the windows method of install, but I wouldn't recommend it, the package manager does so much of the difficult and behind-the-scenes work that it's always best to go through it.

The rare exceptions are some proprietary stuff (usually Adobe and Oracle products), and they'll give you step-by-step linux install guides, and then applications developed by your company internally.

For everything else, use the package manager and repository.

---

### Post by baumanno on 2012-02-29
Tyggna has put it nicely. If you want to actually see what is installed on your system, or if you're wondering, 'Gee, did I install <fancy-open-source-program> or not?', you could do

```
$ dpkg --get-selections | less
```
to list, or 
```
$ dpkg --get-selections | grep <fancy-open-source-program>
```

It takes a while for the 'click' to happen regarding the different procedures, but once you're used to it, you'll never want to miss it again!

Are you a little wiser now? If so you could mark this thread as solved.

Cheers

---

### Post by audiomick on 2012-03-01
> **baumanno said:**
> ... but once you're used to it, you'll never want to miss it again!

Indeed. I had to install a CAD Viewer on my Vista install last night. What with one thing and another and "you need .Net 4" but no offer to provide it and what have you, it took me nearly 40 minutes. ](*,)

I think the longest that a program install on Linux has ever needed was about 3 or 4 minutes. Maybe 5. ;)

---

### Post by pheasant golf on 2012-03-02
I appreciate that.  Thank you

---

### Post by pheasant golf on 2012-03-02
Thank you.

---

