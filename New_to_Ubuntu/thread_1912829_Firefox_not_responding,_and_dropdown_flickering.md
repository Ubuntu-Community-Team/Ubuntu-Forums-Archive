---
title: "Firefox not responding, and dropdown flickering"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by brigadier on 2012-01-21
Hi!

Over about the last week or so, Firefox will throw up a message about "not responding", when you close it then try to reopen it straight away. The pointer does the "waiting" circling - once that stops you can go back in.

Additionally, when searching in google images, if you try to select the "larger than" (for file size) option, the dropdown menu appears, but flickers when you put the pointer over it, making it unusable.

I'm on 10.04, keep upgrading as I'm prompted, and virus scan (with KlamAV) regularly.

Just installed Chromium, and problem is not there - would go completely over to chromium, but for all of the shortcuts plastered all over my desktop that I don't know how to do in chromium!

Help would be appreciated!

---

### Post by 2F4U on 2012-01-21
Firefox takes some time until it is really terminated. Just because the firefox windows disappears doesn't mean that it is terminated and there may still be processes belonging to firefox.

---

### Post by ubudog on 2012-01-21
You could add this to your launcher item, replacing the "command" field with:
```
firefox; killall firefox
```

That might help.  Note: it would kill the Firefox process after it is closed.  

- ubudog

---

### Post by brigadier on 2012-01-21
Thanks for taking the time to help :-)
FireFox has never taken time to fully shut down before, so  I am curious as to why the change.

To ubudog - I don't know how to do your killall command - i am very much a novice!

---

### Post by ubudog on 2012-01-21
> **brigadier said:**
> Thanks for taking the time to help :-)
FireFox has never taken time to fully shut down before, so  I am curious as to why the change.

To ubudog - I don't know how to do your killall command - i am very much a novice!

Ah, no problem.  Click on System>Preferences>Main Menu.  Then, click on Internet>Firefox.   Change the stuff in the 'command' field to the stuff I posted.

On newer Ubuntu releases, click on the "Dash" and search for "Main Menu".  The rest of the procedure should be the same.

Hope that helps,
ubudog

---

