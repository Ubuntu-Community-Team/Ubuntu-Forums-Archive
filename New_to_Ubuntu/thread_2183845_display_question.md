---
title: "display question"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by blightedagent on 2013-10-26
I'm using Ubuntu 12.04 on a laptop with a monitor attached. I don't want two views so I went to display options and switched to mirrored mode. It only has two resolutions. Is there a way to get more resolutions? Perhaps a package to download?

---

### Post by TheFu on 2013-10-26
Open a terminal, run xrandr to see all the resolutions available.
To set the resolution, read more instructions with **man xrandr**. Every system is a little different, so I can't tell you the exact thing to type.

There are GUI ways to handle this too - but the answer depends on which DE you are using, if any.  For example, **lxrandr** works for LXDE-based DEs. Sorry, don't know the tool for others. On a full, default, ubuntu desktop, look in monitor preferences.

If your laptop has nvidia or ATI drivers, then those include a resolution tool.

---

### Post by superduper2 on 2013-10-27
If it does happen to be Nvidia (which is the case with my puter) and you have the recommended display driver installed via the Synaptic Package Manager then:

Alt + F2 -> type nvid -> Click on nvidia-settings -> Try to adjust from there as TheFu has previously advised.

(The above applies assuming you are using Unity)

---

### Post by blightedagent on 2013-10-27
Thanks for the help everyone, but I think I'm just going to go back to dual screens. Its only a minor inconvenience and I don't have the technical skill
in the terminal to do anything useful.

---

