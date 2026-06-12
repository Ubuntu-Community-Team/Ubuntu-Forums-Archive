---
title: "[SOLVED] VLC player-you can't stop the music"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by cjv8888 on 2008-10-05
When I use vlc player to see a Video_TS file using the Open Directory tab, the file will play ok, but if I close the player, the sound of the movie continues and there is no way to stop the sound unless I do a ctrl-alt-backspace.

Is this a bug in the vlc?

---

### Post by billgoldberg on 2008-10-05
> **cjv8888 said:**
> When I use vlc player to see a Video_TS file using the Open Directory tab, the file will play ok, but if I close the player, the sound of the movie continues and there is no way to stop the sound unless I do a ctrl-alt-backspace.

Is this a bug in the vlc?

Could be.

When you have this happening, open up a terminal and do

```
killall vlc
```

That should fix it.

---

### Post by fballem on 2008-10-05
> **cjv8888 said:**
> When I use vlc player to see a Video_TS file using the Open Directory tab, the file will play ok, but if I close the player, the sound of the movie continues and there is no way to stop the sound unless I do a ctrl-alt-backspace.

Is this a bug in the vlc?

I personally think it's a bug, but there is a workaround of sorts. Assuming that you are using GNOME, you can put the System Monitor application on one of your panels. (see below if you don't know how to do this).

If you stop the video playing in VLC before you close it, then you will have no issue.

If you forget to stop the video playing in VLC before you close it, then you will have the issue. In this case, start the System Monitor and select the Processes tab. I've attached a screenshot, including an executing version of vlc. Highlight the line that has vlc on it, then select the End Process button. You will get another dialog to confirm that the process should be ended - answer OK.

**Adding System Monitor to a Panel:**

[LIST=1]
[*]Right-click on the panel to which you want to add the System Monitor. This will give you a list of applications.
[*]Scroll through the list until you see System Monitor.
[*]Highlight the line that says System Monitor, then select the Add button.
[*]Select the Close Button, which will close the menu.
[*]An Icon for System Monitor should appear on the panel.
[*]To use this, left-click on it and have a look at the various tabs to become familiar with it.
[/LIST]

Hope this helps,

---

### Post by cjv8888 on 2008-10-05
Thanks for the replies.

I will give these a try next time.

Don't have a video_TS file to practise on at the moment.

---

