---
title: "Can't Download From Repositories"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by azurepancake on 2008-04-25
I have just installed Hardy and I would like to say that I am very impressed. Every piece of hardware seems to be functioning perfectly and required no configuration at all!

But I am having one issue that I'd like to resolve. It appears I cannot download from any repositories. It just doesn't work either through apt-get or Synaptic.

When trying to download with apt-get, it just seems to freeze when connecting: 

[I]Do you want to continue [Y/n]? y
0% [Connecting to us.archive.ubuntu.com (91.189.88.31)][/I]

And when I try to download something through Synaptic, I get the following errors:

[I]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-core_0.2DrJekyll-4ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-core_0.2DrJekyll-4ubuntu4_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-alsa_0.2DrJekyll-4ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-alsa_0.2DrJekyll-4ubuntu4_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-id3v2_0.2DrJekyll-4ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-id3v2_0.2DrJekyll-4ubuntu4_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-mad_0.2DrJekyll-4ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-mad_0.2DrJekyll-4ubuntu4_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-vorbis_0.2DrJekyll-4ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-vorbis_0.2DrJekyll-4ubuntu4_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2_0.2DrJekyll-4ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2_0.2DrJekyll-4ubuntu4_all.deb)[/I]

And the same problems when Firefox tries to download a plug-in such as Gstreamer.

Is this just the result of the repositories beings swamped with downloads or is this perhaps something I can fix?

Any advice would be much appreciated. Thank you!

---

### Post by rickycodie on 2008-04-25
i'm having the same problem, so you're not alone.

---

### Post by ptcbus on 2008-04-25
I think it is due to jammed servers.

---

### Post by ShodanjoDM on 2008-04-25
I do think it's because of the huge amount of download requests. It'll be a lot less congested in the next few days ahead.

---

### Post by bhursey on 2008-04-25
I had the same issue.  It took me 3 times of doing sudo apt-get update to update the list. Then it took me like 12 min to download firestarter. This happens ever time there is a new release. Give it a week.

---

### Post by 4partee on 2008-04-27
I am getting 404's on that IP.  I am trying to add xubuntu-desktop to the 7.10 server in 32 bit virtualbox running in 64bit 7.04 Ubuntu desktop.

---

### Post by nofrendo on 2008-04-27
Ahh, I have a solution for you! Yes, the repositories get extremely slow around the time of a new release. But to fix that somewhat, you can set Ubuntu to use the fastest server.

Navigate to System>Administration>Software Sources and pull down the "Download From" menu and click "Other." Then click "Select Best Server"

This speeds up the process a lot for most people

---

