---
title: "Black screen when auto-launching Firefox in Kiosk mode"
date: 2024-06-30
forum: New to Ubuntu
---

### Post by Ulf_Dunkel on 2024-06-30
Hi all,
I have set up a new Ubuntu 24.04 machine with some simple adjustments:

- 1 User only, auto-login
- Firefox starts automatically after Ubuntu has launched, set up with [Alt][F2]: "gnome-session-properties", launching Firefox with the command "/usr/bin/firefox -kiosk".
- Firefox is set up to launch a defined local start page on that machine: "http://localhost/index.php".

When I boot the machine, everything's fine until Firefox launches. I see a black screen immediately, while the white mouse cursor is still visible and moveable.

When I quit Firefox with [Alt][F4] and relaunch Firefox from the Dock, the defined local start page is shown properly.

What do I have to do so Firefox won't show a black screen when auto-launched?

Any hint is appreciated.
Best, Ulf

---

### Post by #&amp;thj^% on 2024-06-30
This seems to work on my end.
```
firefox -kiosk  http://localhost/index.php
```
But I'll use a different site than you when it opens. (Not [http://localhost/index.php](http://localhost/index.php))

---

### Post by Ulf_Dunkel on 2024-06-30
[QUOTE=1fallen;14195644]```
firefox -kiosk  http://localhost/index.php
```

Excellent, thank you. It was the difference between "/usr/bin/firefox" and just "firefox". Thank you so much.

Best, Ulf

---

### Post by #&amp;thj^% on 2024-06-30
Happy to help :)

---

### Post by jasonma1984 on 2024-07-25
Hi,

Last week this feature was working, but after updating yesterday it no longer works. It appears that the update recently broke something with firefox. I run the following on startup and am now getting a black screen with a mouse cursor icon. The page never loads. 

I run the following command on startup.
firefox --kiosk [http://localhost:8000](http://localhost:8000)

Removing "--kiosk" works, but I need this to run in kiosk mode.

I am also getting the following errors:

gtk_window_set_titlebar() on a realized window
Not loading module "atk-bridge": The funcationality is provided by  GTK natively. Please try to not load it.

---

### Post by #&amp;thj^% on 2024-07-25
All below still works here:
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> firefox -kiosk  http://localhost/index.php
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;>  firefox --kiosk http://localhost:8000

```
Is firefox a .deb?
```
apt policy firefox
firefox:
  Installed: 128.0.2~build1
  Candidate: 128.0.2~build1
  Version table:
     1:1snap1-0ubuntu6 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages
 [COLOR="#FF0000"]*** 128.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages[/COLOR]
        100 /var/lib/dpkg/status
     128.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     127.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     127.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     127.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     126.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     126.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     125.0.3~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     125.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     125.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0.2~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     124.0~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     123.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     123.0~build3 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     122.0.1~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     122.0~build2 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages

```

---

