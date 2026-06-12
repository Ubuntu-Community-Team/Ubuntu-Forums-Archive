---
title: "&quot;isolate-workspaces&quot; dock option doesn't work with Nautilus"
date: 2022-04-27
forum: New to Ubuntu
---

### Post by paydu8 on 2022-04-27
Hello, I have just installed Linux for the first time. I am using Ubuntu 22.04 LTS and I have installed all the latest updates.

When the setting "Include applications from the current workspace only" is enabled, (in Settings > Multitasking > Application Switching, a google search showed me that this is the same as the terminal command "gsettings set org.gnome.shell.extensions.dash-to-dock isolate-workspaces true") it seems to work as intended for every application except the nautilus file manager. Here is a video that shows what I'm talking about, but I'll explain it below too: [https://gfycat.com/menacingreflectingfrenchbulldog](https://gfycat.com/menacingreflectingfrenchbulldog) (watch in HD so you can see better)

If nautilus is open on one desktop and I switch to a different desktop, the little orange circle to the left of the nautilus icon in the dock stays there, and when I click on the dock icon nothing happens. I have to open a new window for it to open on the second desktop. Then, if I close the window and switch back to the first desktop where the original nautilus window is, it thinks that no nautilus windows are open and clicking the icon in the dock opens a new window.

I've never used linux before and I can't find anything on the internet about this. Is it a bug? Does anyone here get the same issue if you enable this setting?

---

### Post by vanadium on 2022-04-27
You are certainly seeing buggy behavior specifically related to nautilus. Only thing I cannot reproduce is that a new window is spawned when returning to the workspace where the first nautilus window was opened. But indeed, erroneous behaviour is that the orange "dot" remains active on another workspace, and clicking the icon does do nothing.

If you are interested in another bug, opening a Writer window for the first time frequently makes the waiting cursor spin for a long time, and it may take up to 30 seconds after the window is open before the icon appears on the dock. That is a long outstanding bug.

---

