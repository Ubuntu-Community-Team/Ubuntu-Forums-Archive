---
title: "Sabayon themes?"
date: 2007-10-08
forum: Other OS Talk
---

### Post by happysmileman on 2007-10-08
I'm running KDE3.5.7 and Compiz-fusion, can someone tell me where I can get the themes that are used on Sabayon in the screenshots [here]("http://www.sabayonlinux.org/mod/screenshots/").

There appears to be two themes, one for 3.3 and one for 3.4, either would be appreciated.

---

### Post by mips on 2007-10-09
Sabayon overlay in portage should have it.

---

### Post by ThinkBuntu on 2007-10-09
The window border is also used for PC-BSD, and I think you can track down its name in reviews of the latest release. I doubt you want the wallpaper since you're not running Sabayon. The actual button theme is Plastik I think.

---

### Post by happysmileman on 2007-10-09
> **ThinkBuntu said:**
> The window border is also used for PC-BSD, and I think you can track down its name in reviews of the latest release. I doubt you want the wallpaper since you're not running Sabayon. The actual button theme is Plastik I think.

Thanks, found the theme, though now I'm considering getting Sabayon... I do like Gentoo though, but since it's basically just Gentoo with some more stuff installed then it should be fine.
I'm assuming once it's installed I can just keep using portage and then gradually my updates will all become compiled, or do i have to upgrade some stuff using binaries?

---

### Post by mips on 2007-10-09
> **happysmileman said:**
> Thanks, found the theme, though now I'm considering getting Sabayon... I do like Gentoo though, but since it's basically just Gentoo with some more stuff installed then it should be fine.
I'm assuming once it's installed I can just keep using portage and then gradually my updates will all become compiled, or do i have to upgrade some stuff using binaries?

Updating sabayon is not as easy as gentoo because of its overlays. If you do like gentoo then why not install gentoo & kde, add the sabayon overlay and install the theme then remove the overlay again ?

---

### Post by happysmileman on 2007-10-09
> **mips said:**
> Updating sabayon is not as easy as gentoo because of its overlays. If you do like gentoo then why not install gentoo & kde, add the sabayon overlay and install the theme then remove the overlay again ?

I thought it was just "emerge --sync", "layman -S" and then a regular "emerge -avuND world"
And the same for installing packages and stuff.

Also I want to try it out anyway, my Ubuntu install is unused and might as well do something with that space, Gentoo is on external drive so it's still there if I don't like Sabayon as much

---

### Post by mips on 2007-10-10
> **happysmileman said:**
> and then a regular "emerge -avuND world"


That will break things!!!

This will work however:
[http://wiki.sabayonlinux.org/index.php?title=Unoffical_Guide_To_World_Update](http://wiki.sabayonlinux.org/index.php?title=Unoffical_Guide_To_World_Update)

---

### Post by happysmileman on 2007-10-10
> **mips said:**
> That will break things!!!

This will work however:
[http://wiki.sabayonlinux.org/index.php?title=Unoffical_Guide_To_World_Update](http://wiki.sabayonlinux.org/index.php?title=Unoffical_Guide_To_World_Update)

Hmmm... Will look into it, it seems possible to have a shell script containing pretty much everything here, and then just "sudo ./update.sh", and if it fails you can fix it manually?

Other than that i could just use some of the binary packages, as in the ones that arre installed as binary by default and upgrade the rest, keeping Gentoo to fall back on until i'm comfortable enough to switch completely

Edit: According to a post on Sabayon forums (in the topic about that script) [This]("http://www.gentoo.org/news/en/gwn/20061204-newsletter.xml#doc_chap3") script should work, so why not use that?

---

