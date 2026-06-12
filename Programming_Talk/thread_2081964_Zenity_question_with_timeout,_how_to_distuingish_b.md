---
title: "Zenity question with timeout, how to distuingish between OK and time out?"
date: 2012-11-08
forum: Programming Talk
---

### Post by fvdnabee on 2012-11-08
I'm writing a backup script that when completed prompts the user whether or not the system should be suspended. However, when the user is AFK the prompt should time-out and the system should be suspended automatically.

This is what I've got so far:
```

#!/bin/bash
# run backup (omitted)

# suspend system
zenity --question --timeout 60 --text="Backup completed. Suspend the system? \nThis dialog will timeout in 60 seconds, after which the system will suspend."

if [[ $? -eq 1 ]] ; then
    # user clicked Cancel
    exit $rc
else
    # user clicked Ok or dialog timed out ($? equals 5 in both cases)
    # Lock screen and go into suspend (hybrid)
    gnome-screensaver-command -l && sudo pm-suspend-hybrid && exit $rc
fi
```This is working, however there is one issue: by default the Yes button in the dialog is highlighted. When the user is typing some text and doesn't notice the dialog then the system will be suspended when the user hits enter. Reversing the question doesn't solve this because the return code of zenity is the same for Ok and the time-out; i.e. i'm unable to distinguish between the dialog timing out and the user clicking Ok.

My question: how do I distinguish between these two cases. Is this possible with zenity or should i switch to an other similar library for displaying Ok/Cancel dialogs from bash? If so, are there any suggestions?

P.S.: I know I could write a simple Qt c++ application that achieves the same, but I would like the script to be as portable as possible...

---

### Post by Vaphell on 2012-11-08
look at yad, it's a fork of zenity (unfortunately not in main repos, but there are PPAs available)

```
$ yad --timeout=5 --button=OK:1 --button=CANCEL:2; echo $?
70
$ yad --timeout=5 --button=OK:1 --button=CANCEL:2; echo $?
2
$ yad --timeout=5 --button=OK:1 --button=CANCEL:2; echo $?
1
```
timeout seems to get its own exit code (70) and the codes of buttons are customizable

---

### Post by fvdnabee on 2012-11-08
> **Vaphell said:**
> look at yad, it's a fork of zenity (unfortunately not in main repos, but there are PPAs available)

timeout seems to get its own exit code (70) and the codes of buttons are customizable

Thanks, the following snippet will actually make CANCEL the default highlighted button and will also achieve what I want (without reversing the question):
```
# suspend system
yad --image "dialog-question" --title "Suspend system?" --text="Backup completed. Suspend the system? \nThis dialog will timeout in 60 seconds, after which the system will suspend." --timeout=60 --button=CANCEL:1 --button=OK:2

if [[ $? -eq 1 ]] ; then
    # user clicked Cancel
    exit $rc
else
    # user clicked Ok or dialog timed out ($? resp. equals 2 and 70)
    # Lock screen and go into suspend (hybrid)
    gnome-screensaver-command -l && sudo pm-suspend-hybrid && exit $rc
fi
```Marked the thread as solved.

---

