---
title: "Oneiric unity/lightdm logout script"
date: 2012-01-03
forum: Programming Talk
---

### Post by dsjstc on 2012-01-03
I'm looking for any way to run a script on logout or shutdown, before the gui is closed.  Something analagous to gdm's PostSession/default.  Ultimately, I need to execute a VirtualboxManage SaveState early in the logout process.

It seems as though this should properly be part of Unity, rather than Gnome or LightDM, but it doesn't seem to exist in any of the three.  Any suggestions or direction for research are welcome.

---

### Post by peyu on 2012-01-12
Hi dsjtc, did you find a solution ?
I am also looking for a way to run a backup script at the end of the unity session. With gnome 2 I was using the "session_save_yourself" event, but it's not working anymore in gnome3/unity.

---

