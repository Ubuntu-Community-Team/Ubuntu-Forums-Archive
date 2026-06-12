---
title: "Going nuts with Anjuta"
date: 2006-10-29
forum: Programming Talk
---

### Post by ankushrjf on 2006-10-29
Hello there.
I am new and switched from Windows to Linux only because of Ubuntu.
I have this 6.06 LTS (I reckon they call it Edgy Eft).

Well, I can't find anjuta in my applications menu, nor in Alacarte.

$sudo apt-get install anjuta
says it can't find anjuta

and there is no mention of anjuta in Synaptic package manager.

I read some stories of buggy anjuta 2.02.
Has anjuta been withdrawn??
What alternatives do I have now? I need an IDE and am scared about building from source.

---

### Post by meng on 2006-10-29
It's in the universe repositories, you need to enable extra repositories in order to install anjuta.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
This link describes how to enable the extra repositories with Synaptic Package Manager.
6.06 is Dapper Drake, 6.10 is Edgy Eft.

---

### Post by FyreBrand on 2006-10-29
ankushrjf another good place to read is the [**Ubuntu Customization Guide**]("http://www.ubuntuforums.org/forumdisplay.php?f=159") forum area.

There is a lot of good info there for getting some of the small details working.  Included in there is [**ubuntu-demon's recommend Dapper(6.06) sources.list**]("http://www.ubuntuforums.org/showthread.php?t=185758").  There is also a thread for an Edgy(6.10) sources.list.

Just a quick note about versions.  If you are running Dapper(6.06) then the Anjuta version is pretty stable, but the version in Edgy isn't quite as stable and if you are doing production work you might want to download and install the cvs version.

Other alternatives to Anjuta:
_**Geany**_ -- It's alot more lightweight and more like Notepad++ on steroids.  It's in extra repos (universe or multiverse) if you have those enabled. I like this one especially for smaller tasks.  It also supports multiple languages.
[_**Code::Blocks**_]("http://www.codeblocks.org/") -- I love this one.  You must download the nightly for it to work and it's not in the repos.  Don't install the stable version it's old and broken.  Some cool people make an easy to install .deb out of the nightly builds.  This one is burly and full featured.
_eclipse_ -- it's in the repos as well.  It runs on java and has a c++ plug-in.  I don't really like it because I think it's slow and kind of jiggy.  It does work though and is fully featured.

---

