---
title: "How do I get applications to open PDf documents in other than evince"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2008-06-17
I have set acroread is default pdf document reader (right click>properties>open with...); but when I use e.g. google desktop search, or firefox, or galeon downloads, pdf documents open in evince. I wish to change this behavior and requests apps to open pdf docs in anything else but evince (preferred app: acroread).

The reason for using acroread, is that fonts show up better than in evince (even though it is a resource hog).

Many thanks for the help,
S

---

### Post by diaa on 2008-06-17
I believe this can be done from the *Applications *tab in the *Edit* > *Preferences* dialog, change the default application for PDF to */usr/bin/acroread*

---

### Post by shuttleworthwannabe on 2008-06-17
what application are you referring to? Google desktop search does not have this preference; neither does galeon browser. Firefox has file types handling mimes.

thanks for the reply

---

### Post by diaa on 2008-06-17
> **shuttleworthwannabe said:**
> what application are you referring to? Google desktop search does not have this preference; neither does galeon browser. Firefox has file types handling mimes.

thanks for the reply

I'm referring to Firefox, sorry for not being clear, I missed the fact that your problem exists with several applications not only Firefox... it's strange

---

### Post by aktiwers on 2008-06-17
Right-click any PDF file, go to Properties.
Pick the "open with" tab and pick your app.

Then PDF's will open in this app by default afterwards..

---

### Post by shuttleworthwannabe on 2008-06-17
not aktiwers; I have done that; no joy. When I do this, double click on the pdf document, only then it open is preferred app; but not so using pther applications: they are not "trained" in handling pdf natively; seems they are hard coded into the app.

---

### Post by diaa on 2008-06-17
Just curious, may not be the solution for your problem:
what does the command
```
xdg-mime query default application/pdf
```
print?

---

### Post by fatality_uk on 2008-06-17
Try and make sure you remove the old selected app so that only the application you want to launch is left in the list. I had the same issue in Gutsy.

---

### Post by shuttleworthwannabe on 2008-06-17
> **diaa said:**
> Just curious, may not be the solution for your problem:
what does the command
```
xdg-mime query default application/pdf
```print?

```

```~$ xdg-mime query default application/pdf
evince.desktop

---

### Post by diaa on 2008-06-17
> **shuttleworthwannabe said:**
> ~$ xdg-mime query default application/pdf
evince.desktop
well great, the following should fix your problem
```
 xdg-mime default acroread.desktop application/pdf
```

UPDATE: oops, it's acroread.desktop not evince.desktop

---

### Post by diaa on 2008-06-19
Just curious, did it work?

---

### Post by philinux on 2008-06-19
This might help explain.

[http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/](http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/)

---

### Post by 8086 on 2008-06-24
Sorry, but that xdg-mime command does not work for me. Which is not surprising considering that it just overwrote 
application/pdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop with 
application/pdf=acroread.desktop. Basically the same thing.

Have to say that xdg-mime gave me the "right" output to begin with: 
$ xdg-mime query default application/pdf
/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop

Yet it has never worked. Always evince starting up.

---

### Post by cariboo on 2008-06-24
Wouldn't it be easier to open up Edit-->Preferences-->Applications in Firefox and change how it opens PDF files there? I personally don't like opening PDF files in firefox so I just use the pdf download add-on.

Jim

---

### Post by harunoyo on 2008-07-04
Did anyone ever work out how to deal with this problem? I'd be happy to remove evince completely, but for some reason ubuntu-desktop depends on it, so that's not possible. I've tried removing /usr/bin/evince and replacing it with a link to /usr/bin/acroread, but then instead of evince I just get acrobat opening up with an error instead of loading the PDF file correctly.

Here's the situation for me, at least:
- Nautilus is set up to open PDFs with acrobat, no problem there
- Firefox is also set up to open PDFs with acrobat (you can't delete evince, because it is "default", but you can add acroread and tell it to always use that)
- regardless, when you click on a Google Desktop link in Firefox, it opens in evince, without even asking which program you want to use

any ideas?

---

### Post by binnaeus on 2008-07-16
Hi. I have a related problem, I've tried the solutions proposed in this thread and a couple of others suggested elsewhere, but the problem is still there. Here's the situation: after upgrading to Firefox 3 (at least I think that's when it started), PDFs inside Firefox no longer open with acroread but using evince. Outside Firefox, there's no problem. As I said, the suggestions provided here did not work, any help would be appreciated. Thanks.

---

### Post by WrathofthePenguin on 2008-07-18
Do you have the acroread mozilla plugin installed?

Try running the following command:

sudo apt-get remove mozplugger && sudo apt-get install acroread acroread-plugins mozilla-acroread

---

### Post by mastergunner on 2008-07-18
subscribe

---

### Post by binnaeus on 2008-07-18
> **WrathofthePenguin said:**
> Do you have the acroread mozilla plugin installed?

Try running the following command:

sudo apt-get remove mozplugger && sudo apt-get install acroread acroread-plugins mozilla-acroread

That was one of the ideas I had tried earlier. Did not work, thanks though. Any more suggestions?

---

### Post by WrathofthePenguin on 2008-07-18
> **binnaeus said:**
> That was one of the ideas I had tried earlier. Did not work, thanks though. Any more suggestions?

I would make sure that the Plugin is enabled. Go to:

Tools->Add-ons

Go to the Plugins section, and look at Adobe Reader 8.0 and make sure it's enabled. On the bottom right of that you'll see a little button, either Enable or Disable. If it says Enable then the Plugin is disabled. I tested and found that if it's disabled they open in Evince, if it's Enabled they open in the plugin version of Acrobat.

---

### Post by shuttleworthwannabe on 2008-07-19
> **philinux said:**
> This might help explain.

[http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/](http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/)

Fantastic, it works fine. In Opera and other browsers!
Thanks

---

### Post by binnaeus on 2008-07-19
> **WrathofthePenguin said:**
> I would make sure that the Plugin is enabled. Go to:

Tools->Add-ons

Go to the Plugins section, and look at Adobe Reader 8.0 and make sure it's enabled. On the bottom right of that you'll see a little button, either Enable or Disable. If it says Enable then the Plugin is disabled. I tested and found that if it's disabled they open in Evince, if it's Enabled they open in the plugin version of Acrobat.

No, it says Disable.. which means acrobat plugin is enabled :confused:

---

### Post by harunoyo on 2008-09-16
Bumping this thread, because it is still driving me crazy. Did anyone fix the google desktop PDF problem? To recap:

- every time you click a PDF link in Firefox, it opens in Acrobat (or rather, you get a dialog asking what to open it with, which is set to Acrobat by default)...
- ... EXCEPT in Google Desktop search, which just goes ahead and open it in Evince (which is a largely broken app right now, it only seems to even load properly about 50% of the time)

I've followed all the suggestions on this thread, and nothing makes any difference whatsoever. Can I get Firefox to just *always* ask me what program to open a PDF in, even?

---

### Post by 8086 on 2008-12-23
The reason why this is happening is explained here in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-vfs/+bug/264309") I posted some months ago. You will also find a solution there.

---

### Post by jARLAXL on 2009-03-27
Have found me a workaround for replacing evince with kpdf since 8086's solution doesn't work for my FF extensions to use kpdf

```
sudo gedit /usr/share/applications/evince.desktop 
```

and then change the following line:
```
Exec=evince %U
```
to:
```
Exec=kpdf %U
```

IMPORTANT: Applying this will have the following side effect: When you right click a pdf and choose open with evince document viewer it will nevertheless open with kpdf.

---

### Post by ben2talk on 2011-05-04
any solutions?

I have a similar problem - but not only with PDF's.

The problem isn't the Nautilus 'open with' options - my files open correctly from Nautilus.

However, when I open ANY file from the downloads section of any browser (tested with Chrome, Chromium, firefox, Opera, Epiphany) or other softwares (first I had a problem with Miro, trying to open video or audio files)

My applications open all files with a Nautilus browser... I cannot work out how to persuade them to follow the mime for Gnome.

This occurred since I upgraded to Natty... not a fresh install, but with several major problems.

---

### Post by 5149.5 on 2011-05-04
Go to Firefox preferences and click the applications tab.

---

