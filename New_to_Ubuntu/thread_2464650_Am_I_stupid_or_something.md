---
title: "Am I stupid or something?"
date: 2021-07-08
forum: New to Ubuntu
---

### Post by adam165 on 2021-07-08
Has been using Linux for years, but has been a  long time not touch official flavor of Ubuntu.
Installed as a VM today, after I got in to desktop, went through initial setup.
Then I clicked on the "Activities" button at the top left corner.
Now I'm stuck in this view, spent 5 mins, tried all things that make sense.


Which includes:
1. just click on one Window, it should allow me to switch to it right? Nope, nothing happened.
2. ctrl/alt+tab, it should allow me to switch around? Nope, nothing happened.
3. esc button, it should close this view right? Nope, nothing happened.
4. drag the window to the top which closed this view. BUT, whenever I open a window, it back to this view.


It feels like my IQ is not enough to use GNOME3 or my common sense is not common at all.

---

### Post by scorp123 on 2021-07-08
Frozen VM maybe? Or some weirdness going on with the keyboard + mouse mapping? I'd try a different variant without Gnome 3, e.g. Xubuntu or Ubuntu-Budgie maybe? If those work OK then the previous weirdness was because of Gnome 3. If these behave weird too then there must be a problem with your hypervisor ...

---

### Post by adam165 on 2021-07-08
no im sure it's not a VM issue, it is running fine, i can ctrl+alt+f3 switch to console, then kill gnome and start it again.
it seems like just gnome bug, and seems fixed in new version since it go away after "apt upgrade" with a restart.
but ubuntu should really update their iso to not include a faulty but important component.

---

### Post by Impavidus on 2021-07-08
The iso's aren't updated, but for the latest LTS release a new iso is released every 6 months, with all the bugfixes until then. That is, 3, 9, 15, 21 and 27 months after the initial release. Only if there's a severe bug in the live disk, an additional iso can be released.

---

### Post by TheFu on 2021-07-08
Gnome3 is weird.

It really wants direct access to the GPU, which a VM doesn't support.
Try touching the "super" key.  That other OS might call is something else that starts with a "w".
Getting a quick overview by watching some short youtube videos could be very helpful.

Don't feel bad. Not all crazy new desktops click for everyone.  I'm not a Gnome fan at all either, but for many people, it lets them be more productive.

If the VM isn't performing well, post the hypervisor and someone might be able to help with suggestions.  I use KVM + libvirt + spice to access my main desktop (which is a VM).  Spice is very fast - faster than all the other VM access methods except direct hardware passthru with a dedicated GPU.

The current 20.04 LTS should be 20.04.2.

---

### Post by ActionParsnip on 2021-07-08
Did you install the guest additions?

---

### Post by mastablasta on 2021-07-09
> **adam165 said:**
> 
but ubuntu should really update their iso to not include a faulty but important component.

there is an option to download and install updates during OS install (actually it will do it just after base install). i usually do the install first then first thing i do is manually update, reboot to get latest patched kernel loaded, then install GPU drivers etc. i think the reboot can be avoided if you are using live patch (patches/updates kernel while OS is running), bu tin any case that is how i would go about.

---

### Post by QIII on 2021-07-09
While this thread indicates the user is using a VM, the issue appears to be with the DE -- regardless of the platform.  

Let's look at that before we consider moving it to Virtualization.

Thanks.

---

### Post by monkeybrain20122 on 2021-07-09
If it is not a VM problem just click activities again should get you out of it.

---

