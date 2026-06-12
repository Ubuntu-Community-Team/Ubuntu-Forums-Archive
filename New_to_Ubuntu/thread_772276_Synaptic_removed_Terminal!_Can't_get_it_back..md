---
title: "Synaptic removed Terminal! Can't get it back."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by shelbyvision on 2008-04-28
Hi,
I used synaptic to download and install Thunderbird. I liked Thunderbird so much better than Evolution that I decided to remove Evolution, so I used Synaptic's search for Evolution and had it remove the Evolution stuff. I didn't notice that it listed a bunch of other seemingly unrelated stuff for removal, including Gnome Terminal! Why would it do this? When I tried to get it to re-install Gnome Terminal, it listed a bunch of other unrelated things for removal, including Firefox! The same thing happens if I try to re-install  Evolution. How can I get my terminal back without losing Firefox and a lot of other things I need?
Thank you,
Steve

---

### Post by kpkeerthi on 2008-04-28
Press ALT+F2 and type **xterm**. Now run this command
```
sudo apt-get install gnome-terminal
```

---

### Post by kpkeerthi on 2008-04-28
To get everything back as it was when you initially had ubuntu installed, run this command in xterm
```
sudo aptitude install ubuntu-desktop
```

---

### Post by Nano Geek on 2008-04-28
> **kpkeerthi said:**
> Press ALT+F2 and type **xterm**. Now run this command
```
sudo apt-get install gnome-terminal
```I think that the **xterm** command is unnecessary. 

You should just have to log-in and type the **apt-get** command.

---

### Post by shelbyvision on 2008-04-28
Thanks for the replies. Unfortunately, they don't really address the problem, which is the automatic removal of programs that I don't want removed. I tried using xterm, as suggested, and it still was going to remove Firefox and a lot of other things I don't want removed. (see the attached screenshot) I don't really want to re-install gnome-desktop, since that would mean I'd have to download and re-install all the programs I've installed.
Steve

---

### Post by gardara on 2008-04-28
What about setting up another terminal client? For example konsole from kde

alt+f2 and then:

```
sudo apt-get install konsole
```

---

### Post by stchman on 2008-04-28
> **shelbyvision said:**
> Hi,
I used synaptic to download and install Thunderbird. I liked Thunderbird so much better than Evolution that I decided to remove Evolution, so I used Synaptic's search for Evolution and had it remove the Evolution stuff. I didn't notice that it listed a bunch of other seemingly unrelated stuff for removal, including Gnome Terminal! Why would it do this? When I tried to get it to re-install Gnome Terminal, it listed a bunch of other unrelated things for removal, including Firefox! The same thing happens if I try to re-install  Evolution. How can I get my terminal back without losing Firefox and a lot of other things I need?
Thank you,
Steve

In the future use the autoremove command in the terminal.  To remove Evolution use this:

```
sudo apt-get autoremove evolution
```

The autoremove command removes all UNUSED dependencies.  Then clean up the residual config in Synaptic.

---

