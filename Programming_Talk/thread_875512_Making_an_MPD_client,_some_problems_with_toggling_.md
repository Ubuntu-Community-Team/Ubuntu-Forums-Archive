---
title: "Making an MPD client, some problems with toggling pause/play"
date: 2008-07-30
forum: Programming Talk
---

### Post by Yes on 2008-07-30
I'm making an ncmpc clone for fun, and I'm having some trouble with toggling pause/play.  It's supposed to run in an infinite loop, and when the user presses 'p' it checks if it's paused or playing and do the opposite with the mpd_sendPauseCommand method.  It knows when 'p' is pressed, and it knows what state MPD is currently in (paused/playing), but it doesn't play/pause it.  When I put mpd_sendPauseCommand in the beginning of the loop by itself it works.

Here's what I think the relevant code is:

```
if (key == 'p') { 
	if (status->state == MPD_STATUS_STATE_PLAY) {
		mvprintw (7, 1, "playing");
		refresh ();
		mpd_sendPauseCommand (conn, 1);		
	}
	else {
		mvprintw (8, 1, "paused");
		refresh ();
		mpd_sendPauseCommand (conn, 0);
	}
}
```

I've looked around at the source code for some other clients, and it doesn't seem like they do anything different from what I'm doing.  Can anyone help?

Thanks!

---

### Post by henchman on 2008-07-31
i just googled for "mpd_sendPauseCommand" and found the following on google code :>

```

mpd_sendPauseCommand(m_mpd, 0);
mpd_finishCommand(m_mpd);
```

the documentation not clearly says that it's needed..

```
/* after executing a command, when your done with it to get its status
 * (you want to check connection->error for an error)
 */
void mpd_finishCommand(mpd_Connection * connection);
```

give it a try :P

---

### Post by Yes on 2008-07-31
Dang, I knew I was missing something in that code segment.  I do have that, after the last closing brace of the if statement.

Thanks, though.

---

