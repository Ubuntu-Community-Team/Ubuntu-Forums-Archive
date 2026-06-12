---
title: "Keyboard Issue with Ubuntu 24.04: Caps Lock Reversed After Login"
date: 2024-05-06
forum: New to Ubuntu
---

### Post by imaginary.duck on 2024-05-06
I recently installed Ubuntu 24.04 and am experiencing a peculiar keyboard issue. In the login screen, my keyboard behaves normally. 
However, once I log in, the behavior of the Caps Lock key is reversed: typing defaults to uppercase letters and toggling Caps Lock switches to lowercase.

Here's what I've tried so far:

[LIST]
[*]Tested with different keyboard layouts and languages; the issue persists.
[*]Used both an external keyboard and the internal laptop keyboard, with no difference.
[*]Installed Ubuntu 24.04 on a different computer, but encountered the same problem.
[/LIST]

This consistent behavior across different systems suggests it might be a bug with the new release. 
Has anyone else faced this issue or does anyone know of a potential fix? Any help or suggestions would be greatly appreciated!

---

### Post by Claus7 on 2024-05-06
Hello,

1) I would remove entirely the languages in question and add them again via settings -> keyboard
2) I would check if any keyboard shortcut is enabled that leads to this behavior (during my upgrade a couple of them were changed and reverted them back)
3) check if you have different behavior between xorg and wayland (there were same strange behaviors between the two and the reason was a bug in mutter)

These are some I suppose easy suggestions for you to try and check.

Regards!

---

### Post by rasmusjs on 2024-05-13
I am having the same issue. If lock my laptop most keys are reversed but not some special characters like ØÆÅ (I am using a Norwegian keyboard). The capitalization is correct in gnome-shell but not in applications such as Firefox and LibreOffice. The only non solution I have found is to restart the wayland session with [FONT=courier new]fuser -k $XDG_RUNTIME_DIR/$WAYLAND_DISPLAY[/FONT] but this closes all the programs running.

---

### Post by amodra on 2024-06-15
I just had the same thing happen to me.  On the login screen capslock behaved as usual, then once the screen unlocked it was reversed in everything, terminal, emacs, firefox...  This wasn't on the initial login but unlocking after auto screen lock.  Logging out and back in again restored normal behaviour.

---

### Post by brimurray2 on 2024-06-19
Exactly the same for me on an MS Surface Laptop 5 (running surface-2 kernel).
Log out then back in and defaults restored!

---

### Post by niamotullah99 on 2024-07-07
I'm facing the same problem after i resumed from suspend. in gnome application search it works as normal but on `Firefox`, `gnome terminal`, `Files` this issue persist.
OS: Ubuntu-24.04 (clean install)

---

### Post by ifedan on 2024-09-07
Check compose key settings in keyboard settings

---

### Post by mereshow on 2024-09-27
I'm having a similar issue on a Dell XPS 13 (9320), but only on some apps the behavior is reversed, ubuntu UI works normally and some apps reversed (Chrome, for instance).

---

### Post by kempy on 2024-09-30
hey guys i was having this issue also, and i may have a solution, let me know if it works for you. not sure if it has something to do with using a VPN, but somehow my Region and Language settings were in metric system, etc and after switching to US, the issue is resolved. good luck! [https://i.imgur.com/CTyB2xq.png](https://i.imgur.com/CTyB2xq.png)

---

