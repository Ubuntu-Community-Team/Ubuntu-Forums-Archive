---
title: "Run python script in terminal window periodically"
date: 2015-07-14
forum: Programming Talk
---

### Post by Nostigex on 2015-07-14
Hi, I tried finding a way to do this using cron, but apparently it's only designed for doing jobs in the background and not for interacting with the UI/display. I would like to run a python script in a terminal window automatically every X amount of time. How would I go about doing this?

---

### Post by papibe on 2015-07-14
Hi Nostigex.

You can launch a terminal instead, and tell the terminal to run a script. Something like this should work:
```
*/1 * * * * DISPLAY=:0 /usr/bin/gnome-terminal -x /path/to/script.sh
```
For debugging purposes, this would launch a terminal running the script every minute.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Nostigex on 2015-07-14
I tried that before and it didn't work, but now it does. Go figure.

I'm curious as to what difference it makes to put "env" before "DISPLAY=:0" or not, and if it's redundant. I'm also curious if there would be any other way of doing this.

In any case, solved. Thanks.

EDIT: Is there a way to send every instance of the script to the same terminal window, whether as a separate tab, overwriting output in the window, appending output to the same window, etc? This would be useful to prevent situations of getting up to leave the computer and coming back to dozens of open terminals.

---

### Post by Nostigex on 2015-07-14
I found that it's possible to open a new tab in the previously opened window using the --tab option, though I found a better solution for my case. I can simply use the time.sleep() function in python to wait for a period of time before closing the window, before the next cron job starts.

---

### Post by papibe on 2015-07-14
> **Nostigex said:**
> I can simply use the time.sleep() function in python...
Like a loop that's always running?

If so, I'd recommend running it inside a GNU screen, or a tmux session.

Just a thought.
Regards.

---

