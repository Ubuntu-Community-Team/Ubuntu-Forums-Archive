---
title: "how do i down load gimp 2.6.2"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by blake7 on 2008-11-19
i have tryed synapatic manger but i not thier

 ardour 2.5 is not thier to so how can i doewn load this to 

thank you

---

### Post by drs305 on 2008-11-19
An easy method is to use GetDeb: [http://www.getdeb.net/](http://www.getdeb.net/)

You register and can then download the Gimp 2.6.2 .deb file. Once downloaded, you can either click on it to install or use "sudo dpkg -i *packagename*.deb"

You can also go to the Gimp site and get the tar.gz file: [http://gimp.org/downloads/](http://gimp.org/downloads/)

Of course, the standard disclaimer about the versions in the official repositories being the 'approved' versions...

---

### Post by blake7 on 2008-11-19
why does it not show up in my sypactic down load list

---

### Post by drs305 on 2008-11-19
> **blake7 said:**
> why does it not show up in my sypactic down load list

Are you referring to 2.6.2 or earlier versions? The latest version often takes a while to make it into the official repositories. This is because the ubuntu team will thoroughly test the newest release to ensure compatibility with the existing OS. Additionally, if you are using Hardy, a long term support (LTS) version, updates are rarely made except for security issues. Users can manually add updated packages but do so with the understanding that compatibility issues may arise.

---

### Post by blake7 on 2008-11-19
how do i sown load up dates??? or find out if they exstest

---

### Post by drs305 on 2008-11-19
For supported packages, make sure you have updates enabled:
Synaptic, Repositories, Updates tab. Normally you would have the security and recommended updates ticked. These are the updates that should be reasonably safe to use. Proposed and backports, the other two update options, are less well tested and have a bit more chance of causing conflicts with the existing OS. 

In the second section of the Updates tab is the Automatic Update settings. Tick how often and if the system should automatically check for updates. If you have one or more of the top section ticked, and select auto-updating in the lower section, you will be notified when updates become available. This is shown on your panel with the 'update notifier' icon. When it appears, you can click on it to see what updates are available. 

You can also manually check for updates via the menu system: System, Administration, Update Manager. It will check for any updates that may be available. It will check only those sources you have enabled in your sources.list

For updates to packages you have manually installed, you would have to return to that package's download site and update it manually unless the app itself had an update method built into the application.

---

