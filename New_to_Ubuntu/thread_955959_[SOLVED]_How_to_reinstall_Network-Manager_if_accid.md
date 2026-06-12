---
title: "[SOLVED] How to reinstall Network-Manager if accidently removed?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by DThurman on 2008-10-22
I was using Synaptic and after selecting items
I wanted to install, at the end of my selections,
I proceeded to install and realized that 3 Network-Manager
components were slated to be removed, so I hit 'Cancel'
while it was downloading, then it prompted me if I really
wanted to cancel, I said "yes", then it proceeded to remove
the 3 Network-Manager components and install whatever was
successfully downloaded!

So...  now my system is without a Network-Manager and no
access to the Internet, how can I proceed to restore it
in order to get it working again?

1) Can I restore it via Live-CD?
2) Can I manually configure the Network and then proceed
   from there and if so, then how please?

I am really a noob to Ubunto so I need details, step-by-step
how I can restore Network-Manager.  I am used to Fedora as
I can start the Network service, configure it by hand and all
that but I could not find it in Ubunto, sadly.

Thanks!
Dan

---

### Post by drs305 on 2008-10-22
You can reinstall network-manager via LiveCD. Insert the cd and boot to the livecd desktop. Select System, Administration, Synaptic Package Manager. Make sure in Settings, Repositories the CD ROM source in the lower window is ticked and that it is inserted. Hit Close and Reload.

In the Ubuntu Software tab's right window, tick 'network-manager' and 'network-manager-gnome'.  If you know the name of the third package that was uninstalled you can select that also, although it will probably be selected. Click on apply to install it.

---

### Post by wolfen69 on 2008-10-22
.

---

### Post by DThurman on 2008-10-22
Thanks for the information!
Very Helpful!

Dan

---

