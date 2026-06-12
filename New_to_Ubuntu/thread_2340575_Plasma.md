---
title: "Plasma"
date: 2016-10-19
forum: New to Ubuntu
---

### Post by misswham2 on 2016-10-19
Hi there everyone, I just discovered Plasma and I loved it.  I downloaded Kubuntu, Linux Mint KDE and Neon and I see that the desktops are the same on all the distros I tried.  I'm just a regular web surfer,  edit a few pictures, video and listen to music/movies.     Is there an advantage of one over the other?

Also, I use winff, geary, unetbootin, synaptic, Sound Converter, brasero, terminal etc, will I be able to use those in KDE?

Thanks in advance.  Im not a novice to using GNOME and Unity with Ubuntu 16.04 but I have never used anything else.

---

### Post by T.J. on 2016-10-19
> **misswham2 said:**
> Hi there everyone, I just discovered Plasma and I loved it.  I downloaded Kubuntu, Linux Mint KDE and Neon and I see that the desktops are the same on all the distros I tried.  I'm just a regular web surfer,  edit a few pictures, video and listen to music/movies.     Is there an advantage of one over the other?



They are all based on the same software - KDE.  So there is no real advantage, except for which community you prefer and what support they offer: bug patches and so on.
> 

Also, I use winff, geary, unetbootin, synaptic, Sound Converter, brasero, terminal etc, will I be able to use those in KDE?


Yes. Many of them are GTK based, so they will not look like KDE without using themes. They will work exactly the same as they always have - as long as you understand that:

1.  You may have to start Gnome services in order for them to work.
2.  Cut and paste between GTK and Qt/KDE apps may not work as you expect because they use do not use the same toolkit.  You can sometimes fix that by using a clipboard manager such as gpaste. In most cases the KDE clipboard should work seamlessly, and you won't even notice.

---

### Post by misswham2 on 2016-10-19
Are there apps in KDE that function the same?

---

### Post by SeijiSensei on 2016-10-20
Most GTK apps will run fine in KDE.  You might want to play around with the themes used in System Settings > Application Appearance > GTK.

However there are some KDE equivalents to the programs you listed
brasero = K3b
terminal = Konsole 
synaptic = Software Center (Muon discover)
unetbootin = Startup Disk Creator

geary is apparently an email app.  KDE comes with KMail, but I have been using Thunderbird for two decades now and prefer it.

I use SMPlayer for videos with mpv as the engine.  It runs fine in KDE.

One KDE feature that you might find appealing if you rip CDs is its system of "kio-slaves".  If you open a music CD with Dolphin, you'll see it appear in a variety of formats depending on the codecs on your machine.  There will be a FLAC folder, an MP3 folder, etc.  You can then rip the songs by dragging and dropping them from the appropriate source folder.

---

### Post by misswham2 on 2016-10-20
Thanks for your help.  I have one more question.  If I download Kubuntu on my pc is there a way to upgrade to Plasma 5.8 or do I have to download Neon?

---

### Post by SeijiSensei on 2016-10-21
Even [16.10]("http://kubuntu.org/news/kubuntu-16-10-released/") only has Plasma 5.7.5.  However you can install 5.8 from a [PPA repository]("http://sourcedigit.com/21009-install-kde-plasma-5-8-on-ubuntu-16-04-and-linux-mint/").

---

### Post by misswham2 on 2016-10-21
I followed all the commands in the ppa repository and got an error report.  I sent the report and tried again but its a no go.  How can I UNinstall what I have already done and start over?  If you think that will work.

---

### Post by acheronuk on 2016-10-21
> **SeijiSensei said:**
> Even [16.10]("http://kubuntu.org/news/kubuntu-16-10-released/") only has Plasma 5.7.5.  However you can install 5.8 from a [PPA repository]("http://sourcedigit.com/21009-install-kde-plasma-5-8-on-ubuntu-16-04-and-linux-mint/").

Plasma 5.8 is not yet in the backports ppa, so that article is utterly wrong.

Once 5.8 is in Zesty 17.04, which hopefully should not be long, THEN it can be backported to stable releases.

---

### Post by misswham2 on 2016-10-21
Ohhhh ok Thanks.  So that means I would have to go to neon and if I do have to use neon, then how do I remove what I have done from the respositories because plasma ia an option on the login page but doesnt work (it tries to load but just hangs there and then goes to a dark screen) and is neon the only distro using Plasma 5.8?

---

### Post by SeijiSensei on 2016-10-21
> **acheronuk said:**
> Plasma 5.8 is not yet in the backports ppa, so that article is utterly wrong.
Sorry!  I'm quite happy with KDE4 and Kubuntu 14.04 and don't expect to change until maybe 18.04 rolls around.

Usually I expect if someone posts an article like that, it's because he or she has tried it, and it works.

---

### Post by misswham2 on 2016-10-21
Tried to install it on MINT now and it DID work but it isn't PLASMA, it's just the plain old KDE desktop.  I give up.  I guess I have to go with using NEON.  Thanks for your help anyway.

---

### Post by misswham2 on 2016-11-01
Just went ahead and installed NEON and everything's fine.

---

