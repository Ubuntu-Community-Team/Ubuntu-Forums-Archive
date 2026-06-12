---
title: "MediaWiki problems"
date: 2009-06-30
forum: Programming Talk
---

### Post by geek_of_doom on 2009-06-30
I'm trying to set up MediaWiki on my machine, and apparently something has gone wrong.

Every time I try to visit a page that is intended to be a part of the wiki, I receive the following error:


**Warning**:  require_once(./includes/WebStart.php) [function.require-once]: failed to open stream: Permission denied in **/usr/share/mediawiki/index.php** on line **38**

**Fatal error**:  require_once() [function.require]: Failed opening required './includes/WebStart.php' (include_path='.:/usr/share/php:/usr/share/pear') in **/usr/share/mediawiki/index.php** on line **38**

These messages began after I set "$wgEnableUploads" to true in LocalSettings.php, but now it will not operate regardless of $wgEnableUploads' value.

Have I made a mistake while configuring the software, or is there some secret hidden step that I have missed?

---

### Post by s.fox on 2009-07-01
Hi,

[This]("http://www.mediawiki.org/wiki/Project:Support_desk/Archives/PHP/001") hints that the error is now outdated.  What version are you trying to get running?

-Ash R

---

### Post by geek_of_doom on 2009-07-01
I'm afraid I have no idea how to check that. All I know is that I have installed MediaWiki with sudo apt-get install mediawiki. Technically speaking, this should be the latest version, but I'm not sure.

---

