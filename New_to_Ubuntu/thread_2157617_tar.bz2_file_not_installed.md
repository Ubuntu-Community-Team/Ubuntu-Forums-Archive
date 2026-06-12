---
title: "tar.bz2 file not installed?"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by hotuserl on 2013-06-26
i was just download firefox22.0.tar.bz2 file....after extract to a folder, i was run a command in terminal "./configure'...but it shows configure file doesnot exist......then how to install tar.bz2 files...any other way is there? plz help me..i am completly newbie to ubuntu....

---

### Post by Paqman on 2013-06-26
On Linux we don't usually install or update software by downloading bundles from websites. Your system has a package manager built-in that can handle all this automatically with no mess or fuss.

Ubuntu includes Firefox by default, so all you need to do to keep updated is open Update Manager and let it do its thing. If you're on an older version of Ubuntu and don't think the version of Firefox it's giving you is up-to-date then try going into Software Sources and ticking the "backports" option, then run Update Manager again.

---

### Post by monkeybrain2012 on 2013-06-26
I don't understand. How did you download the tar ball if not using Ubuntu's default browser, which happens to be Firefox?? (unless you use Kubuntu, but that is not what your tag says) Anywho, even if FF is not installed (say you're on Kubuntu) it can be easily installed from the repository and it will get regular updates (FF22 just came out, I expect updates in the next day or so, or maybe it already arrives, haven't checked)

As for your question why the tar file doesn't install. FF doesn't need installation if you download from Mozilla. You just extract the tar ball. Open the folder and click firefox, or firefox-bin and Frefox will open.  A tar file is just an archive (like zip or rar), it can contain anything. Programs distributed through tar balls may contain source codes that need to be compiled, precompiled binaries, an install script or a bunch of .debs (like LibreOffice if you download from document foundation),  in this case it is a binary which has already been compiled.

---

### Post by asifnaz on 2013-06-26
Use software center to install apps or use apt-get

for example go to terminal and type

```
sudo apt-get install firefox
```

give password and it will be installed

---

### Post by nerdtron on 2013-06-26
> **hotuserl said:**
> i was just download firefox22.0.tar.bz2 file....after extract to a folder, i was run a command in terminal "./configure'...but it shows configure file doesnot exist......then how to install tar.bz2 files...any other way is there? plz help me..i am completly newbie to ubuntu....

I think the OP wanted the latest the latest firefox version. 
Don't worry, the windows version was just released, give it a few days and the Ubuntu Update Manager will show the upgrade. No need to download directly from the mozilla website.

EDIT: Just run the update manager. Firefox 22 is already in! :)

---

### Post by newb85 on 2013-06-26
But to answer the specific question you asked (for future reference), that "configure" file should have been located inside the directory you extracted from the tarball.  You would first need to navigate to that directory before running that command, or else run it like this:
```
~/Downloads/Firefox22/configure
```
or whatever the actual path is.

But the other posters are spot on: using the built-in package management system is the best approach in almost all situations, including this one.

---

### Post by snowpine on 2013-06-26
.tar.bz2 is simply an archive file format (like .zip in Windows).

There could be a configure file and some source code in there, or there could be something else: an executable binary, pictures of your summer vacation, etc.

I happen to know that Firefox is distributed as an executable binary (like .exe in Windows) so just extract it and double-click it.

Except you **don't need to do this** because you can install Firefox through the Software Center with a couple of mouse clicks! (If it's not installed already by default?)

---

### Post by hotuserl on 2013-06-26
thank you so much friends who have given reply.....

---

