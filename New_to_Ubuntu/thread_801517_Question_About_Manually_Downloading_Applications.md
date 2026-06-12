---
title: "Question About Manually Downloading Applications"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by lisar915 on 2008-05-20
Hi everyone,

I recently downloaded the RSS Owl newsreader manually. And it's working. But I'm just curious as to why it's not showing up under "Applications" or under the Synaptic Package Manager.  

Thanks.

---

### Post by anfractuosities on 2008-05-20
try
sudo update-menus

---

### Post by anfractuosities on 2008-05-20
if that doesnt work try this

[http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html](http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html)

If you donot know the command for the program, open the containing folder for the app and find the program file.  

It maybe a hidden folder in your home directory.  

Open it up and hit ctrl+h to show hidden files

---

### Post by lisar915 on 2008-05-20
Thank you.  I followed the instruction on the site you recommended.  RSS Owl now shows up under "Applications."  However it's still not showing in the Synaptic Package Manager when I did a search for installed programs.  Would you know why that is?

Thanks again.

---

### Post by anfractuosities on 2008-05-20
I don't believe it is in the synaptic...try searching through all available apps and see if it appears.  If it does and is correctly installed, the check box will be colored in.

---

### Post by y-lee on 2008-05-20
RSS Owl is a java application the OP downloaded to his or her desktop it will not show up in synaptic because it was not installed that way and is not as far as I know in the repos.

---

### Post by lisar915 on 2008-05-20
So are you saying it's normal for RSS Owl to be listed under "Applications" but not in the Synaptic Package Manager?

Thanks.

---

### Post by shifty_powers on 2008-05-20
pretty much. synaptic can only show programs from the repositories fo software that are set up for ubuntu, though you can tell it of extra repositories....

---

### Post by lisar915 on 2008-05-20
> RSS Owl is a java application the OP downloaded to his or her desktop it will not show up in synaptic because it was not installed that way and is not as far as I know in the repos.

Thanks.  Now just out of curiosity, how would I un-install a manually downloaded application?  Would going to "Applications" then "Add/Remove Programs" do the trick?  Or is there something else I need to do?

---

### Post by Maestro23 on 2008-05-20
> **lisar915 said:**
> Thanks.  Now just out of curiosity, how would I un-install a manually downloaded application?  Would going to "Applications" then "Add/Remove Programs" do the trick?  Or is there something else I need to do?

No, because you installed a program that was outside of the Ubuntu Repositories.  Synatpic and Add/Remove are for dealing with program from the Repositories.

What kind of file was the program you installed?  .tar, .deb, .bin?

---

### Post by lisar915 on 2008-05-20
Well I manually removed RSS Owl.  However, on their download page, its says the Linux version is gtk.

---

