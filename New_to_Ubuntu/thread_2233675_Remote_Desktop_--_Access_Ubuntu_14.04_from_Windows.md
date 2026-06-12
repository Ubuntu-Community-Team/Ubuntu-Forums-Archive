---
title: "Remote Desktop -- Access Ubuntu 14.04 from Windows 7"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by quadrplax on 2014-07-10
I have gone to Desktop Sharing, checked the "Allow users to view and control your desktop boxes". I've tried wit with and without a password. My problem is that I can't get a windows client to access this from. TigerVNC gives me an error message "No matching security types" and TightVNC says "No security types are supported". I would use xrdp, but I would like to keep the unity interface. Help?

---

### Post by TheFu on 2014-07-10
Don't know the answer, but Win7 (and Vista+) have added another layer of network authentication trying to make RDP more secure. Turns out that isn't really a solution, just a hassle.  On the Windows side, enable legacy RDP support and try again.

[http://www.ubuntututorials.com/remote-desktop-ubuntu-12-04-windows-7/](http://www.ubuntututorials.com/remote-desktop-ubuntu-12-04-windows-7/) might be helpful - main issues seem to be running to too-high resolutions on the connection.

VNC and RDP security is a joke unless a strong VPN or ssh are used to tunnel all traffic and the traffic on both those desktop protocols isn't possible over any public interface.  Do NOT open up any other router ports, especially not 59xx or 3389 - all traffic needs to go through a VPN or ssh tunnel to be secure.

---

### Post by quadrplax on 2014-07-10
I'm not going for security here, it's hard enough just to get it to work at all. I forgot to mention in my original post this will all be done over intranet. Anyway, you're saying it's possible to get xrdp to work with Unity? The resolution is 1280x800. I can't find this so-called "legacy RDP support" option anywhere in Windows. I like how the time I post in "Absolute Beginners Section" I get one of the harder to understand responses lol (if I think something should be really trivial and easy to do, I post here).

---

### Post by steeldriver on 2014-07-11
As a workaround, try opening a terminal on the Ubuntu machine and entering

```

gsettings set org.gnome.Vino require-encryption false

```

or (equivalently, I think)

```

dconf write /desktop/gnome/remote-access/require-encryption false

```

See [https://bugzilla.gnome.org/show_bug.cgi?id=728267](https://bugzilla.gnome.org/show_bug.cgi?id=728267)

---

### Post by quadrplax on 2014-07-12
Forgot to post back, but that first command worked out great. Marking as Solved.

---

### Post by oldfart101 on 2014-07-31
I am having the same problem
I tried 'a load' of solutions proposed on the internet - still no connection from vnc (Windows) to Ubuntu 14.04
there seems to be an issue I can't find a solution to:
```
:~$ vino-preferences
error: XDG_RUNTIME_DIR not set in the environment.

(vino-preferences:29061): Gtk-WARNING **: cannot open display:
```
anyone??

---

### Post by quadrplax on 2014-07-31
Oh, well it seems to work now consistently, so I guess I should mark this as solved, and you should start your own thread? I think that's how you're supposed to do it.

---

### Post by quadrplax on 2014-08-10
Well something weird happened now, it won't let me connect, but now as I have physical access to the laptop, I went over and opened it, and nothing showed up on the screen. I was still able to use PuTTY just fine but could not access any of the tty terminals (Ctrl+Alt+[F1-F6]) on the physical machine.

---

### Post by steeldriver on 2014-08-10
Well if the X server or session has terminated for some reason, then no you will not be able to connect to it remotely

If you're curious, you can use 'ps' over the SSH connection to see what processes are still running

---

