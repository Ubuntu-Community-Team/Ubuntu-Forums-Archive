---
title: "Disableing double tapping Alt hotkey"
date: 2016-09-01
forum: New to Ubuntu
---

### Post by Nargluj on 2016-09-01
Hello!

I would like to get some help with removing the search/command window (in the top left) that shows up when you double tap Alt. It's incredibly annoying in a program where you sometimes alt-click in quick succession.

I've searched and I haven't been able to find it anywhere. Thanks in advance. :)

Ubuntu 16.04 LTS

Best Regards
Lukas

---

### Post by yetimon_64 on 2016-09-02
**Edit:** You may not need to even install ccsm as noted below: Go to the cog icon at the far right on the top panel and go to System Settings > Keyboard > Shortcuts tab > Launchers  and click the "Key to show the HUD" entry then press the backspace key on your keyboard. This is an even easier way than installing ccsm as I first noted.

[s]Try installing ccsm (compizconfig settings manager) with the code below in terminal (or from the Ubuntu Software application if you prefer the GUI) if you don't already have installed. You may also be able to disable the HUD from other utilities like Ubuntu Tweak etc, ccsm is what I use here.

```
sudo apt-get install compizconfig-settings-manager
```

Open it from dash by searching for "compiz", then clicking on the compiz config settings manager icon below the search box.

Find and open the "Ubuntu Unity Plugin" and on the "General" tab click on the pencil icon beside the "Key to show the HUD when tapped" entry.

The edit window will pop up with the <Alt> entry highlighted, press the delete key on your keyboard, then click on OK in the edit window. This will then disable the HUD entry which responds to tapping the Alt key.[/s]

Cheers, yeti.

---

### Post by Nargluj on 2016-09-02
I must have missed it when I was in there looking for it earlier this week. Thank you. :)

---

### Post by yetimon_64 on 2016-09-02
> **Nargluj said:**
> ... Thank you. :)

You're welcome :). Could you please mark the thread as [SOLVED] with the thread tools drop down menu at the top of your browser window? A guide to how to do so is [[COLOR=#0000ff]--here--[/COLOR]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") (blue lettering is a link) if needed. 

Regards, yeti.

---

