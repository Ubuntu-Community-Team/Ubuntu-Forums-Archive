---
title: "issues with firefox, do i have to reinstall?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by jonaphant on 2008-05-02
hello, i'm having problems with embedded videos, everytime i want to see one, my cpu goes to 100%, i tried to uninstall the flash plugins and install the gnash ones, but everything remained the same, i've read in other post about a guy who upgraded from version 7.10 instead of making a clean 8.04 install, he now could choose from different kernels (.22 and .24) saying that .22 works best with his 8.04 installation and that it solved a lot of issues, my answer is, do i have to install 7.10 and upgrade to 8.04 to select the old .22 kernel or is there another solution to this problem????

thanks in advance

---

### Post by c4v3m4n on 2008-05-02
You could use the gnash flash plugin for firefox, it's not that great but it gets the job done.  You could install a different browser, firefox 3 has been causing quite a few problems with the flash player.  I use swiftweasel.

---

### Post by jonaphant on 2008-05-02
where can i find swiftweasel??? i looked for it using synaptic but nothig was found

---

### Post by markekeller on 2008-05-02
Swiftweasel can be found [here]("http://swiftweasel.tuxfamily.org/").

And if you want to try using the older kernel, I *think* you can just install the package **[COLOR="DarkSlateGray"]linux-image-2.6.22-14-generic[/COLOR]**, if that's available in 8.04 (I'm still a Gutsy user).  Should show up in GRUB, then.

---

### Post by jonaphant on 2008-05-02
> **markekeller said:**
> Swiftweasel can be found [here]("http://swiftweasel.tuxfamily.org/").

And if you want to try using the older kernel, I *think* you can just install the package **[COLOR="DarkSlateGray"]linux-image-2.6.22-14-generic[/COLOR]**, if that's available in 8.04 (I'm still a Gutsy user).  Should show up in GRUB, then.

nope. it couldn't find it:(

---

### Post by Tomatz on 2008-05-02
**R click** on the flash video you are trying to watch

Click **settings**

Disable **hardware acceleration**

Reload the page and flash should be less choppy ;)

---

### Post by jonaphant on 2008-05-02
> **Tomatz said:**
> **R click** on the flash video you are trying to watch

Click **settings**

Disable **hardware acceleration**

Reload the page and flash should be less choppy ;)

i just got properties and that option is not appearing

---

### Post by Tomatz on 2008-05-02
> **jonaphant said:**
> i just got properties and that option is not appearing

Try doing it on a youtube video to change it as it should give you a settings option.

Are you sure it is embedded flash you are trying to view.

Can you send me a link?

---

### Post by jonaphant on 2008-05-02
but the hardware accelerator stuff is not there :( i'm using both firefox 2 and 3

---

### Post by c4v3m4n on 2008-05-02
[This link]("http://linux.softpedia.com/get/Internet/HTTP-WWW-/Swiftweasel-27709.shtml") should get you Swiftweasel.

---

### Post by jonaphant on 2008-05-02
> **Tomatz said:**
> Try doing it on a youtube video to change it as it should give you a settings option.

Are you sure it is embedded flash you are trying to view.

Can you send me a link?

it happens with any youtube video, my cpu goes to 100%, that didn't happen to me in the 7.10 release

---

### Post by Tomatz on 2008-05-02
> **jonaphant said:**
> it happens with any youtube video, my cpu goes to 100%, that didn't happen to me in the 7.10 release

[B]r click on the flash video
[/B]

then enter the flash settings it will definatly give you a hardware acceleration option unless you are not using adobe flash.

---

### Post by jonaphant on 2008-05-02
oh i remember uninstalling flash and installing gnash, let me revert it and tell you what happened

---

### Post by jonaphant on 2008-05-02
i did it and i'm getting this: [IMG]http://comunidad.uach.mx/a189596/Pantallazo-http:--www.youtube.com-player2.swf.png[/IMG]

---

### Post by Fatal Equinox on 2008-05-02
I would install firefox 2 and see if you still have the same problems.   You have to go to the synaptic manager to uninstall firefox 3, and start with a fresh copy of firefox 2.   3 being a beta still has some unusual quirks.

---

### Post by jonaphant on 2008-05-02
> **Fatal Equinox said:**
> I would install firefox 2 and see if you still have the same problems.   You have to go to the synaptic manager to unistall firefox, wont work from add/remove.

it happens with both firefox 3 and 2 :(

---

### Post by Tomatz on 2008-05-03
If turning off hardware acceleration didn't work then i think you are stuck with buggy old flash 9 linux till the next flash update.

See here:

[http://ubuntuforums.org/showthread.php?t=769906](http://ubuntuforums.org/showthread.php?t=769906)

Sorry all i can suggest is trying to watch your flash videos either under ie in wine (*[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)*) or in xp.

:(

---

