---
title: "How to send the message box generated to background"
date: 2013-08-22
forum: Programming Talk
---

### Post by bkpsusmitaa on 2013-08-22
We are aware that an "&" at the end of each command executes it in background.
How can I send the message box generated from the following code to the background:
```
 title=$(gettext ‘SCANNING DEVICE’)
 text=$(eval_gettext ‘Looking for PPPoE Access Concentrator on $iface…’) &
 if test -n “$mmm” ; then
 mmode=$(gettext ‘(multi-modem mode)’)
 fi
```

---

### Post by Bucky Ball on 2013-08-22
Hi. Please use [code] tags around code. Makes it easier to read. Thanks. ;)

---

### Post by ofnuts on 2013-08-22
This code (the 5 lines posted) doesn't generate a message box?

---

### Post by bkpsusmitaa on 2013-08-23
The code is from pppoeconf script file. I have modified the file to suit a particular purpose of mine. Everything works fine, but can't send the message boxes to the background. The popping up of the boxes are so irritating!

---

### Post by ofnuts on 2013-08-24
That doesn't answer my question. You post 6 lines, none of them producing a message box so it's hard to tell what to change.

OTOH if you don't want the messages, replace the calls (zenity?) by plain "echo" or else... The "background" in which a line command runs when suffixed by "&" isn't the '"background" of your desktop anyway... These are two quite unrelated concepts that just happen to share the same name. Just adding "&"s will create dialogs on your desktop foreground controlled by process in your execution background.

---

### Post by bkpsusmitaa on 2013-08-31
My apologies for delayed response...
> **ofnuts said:**
> That doesn't answer my question. You post 6 lines, none of them producing a message box so it's hard to tell what to change.
Actually, the question mark you put at the end of your post confused me. I will attach the modified pppoeconf script file. I have removed the execution permissions and renamed it with .txt extension.

> **ofnuts said:**
>  OTOH if you don't want the messages, replace the calls (zenity?) by plain "echo" or else... The "background" in which a line command runs when suffixed by "&" isn't the '"background" of your desktop anyway... These are two quite unrelated concepts that just happen to share the same name. Just adding "&"s will create dialogs on your desktop foreground controlled by process in your execution background.

In the context of the six lines - how do I modify them?

[ATTACH]245864[/ATTACH]

---

### Post by ofnuts on 2013-08-31
The only way you can modify these lines to prevent a message box is to replace them by "exit" to kill the script, because the message box isn't produced there. What makes these boxes appear is the various calls to "$DIALOG" (for instance in line 195) whihc is substituted by "whiptail" (see line #13). These are the calls you want to remove or replace by "echo".

---

### Post by bkpsusmitaa on 2013-08-31
> **ofnuts said:**
> ... replace them by "exit" to kill the script, ...  That is not a reasonable solution ;) because I need the script to run iteratively ...  > **ofnuts said:**
> because the message box isn't produced there. What makes these boxes appear is the various calls to "$DIALOG" (for instance in line 195) whihc is substituted by "whiptail" (see line #13). These are the calls you want to remove or replace by "echo".  Okay! Thank you. But how did you arrive at the conclusion?! Could you give me a hint or two? that is, why not the lines I posted but the $DIALOG? The issue provides me with a great opportunity to learn. And at present I believe I am in contact with a highly experienced mind! So it would be foolish of me to let go of this opportunity. I will try the necessary modifications and get back.

---

### Post by ofnuts on 2013-09-01
> **bkpsusmitaa said:**
> But how did you arrive at the conclusion?! Could you give me a hint or two? that is, why not the lines I posted but the $DIALOG?

"man gettext" doesn't menton any window... so I return the question. how did you reach the conclusion that the windows were created by these commands?

---

### Post by bkpsusmitaa on 2013-09-01
> **ofnuts said:**
> "man gettext" doesn't menton any window... so I return the question. how did you reach the conclusion that the windows were created by these commands? Because the message boxes showed precisely those messages like SCANNING DEVICE, Looking for PPPoE Access Concentrator on... and multi-modem mode... So I guessed... turns out they were wrong guesses!

---

### Post by ofnuts on 2013-09-02
There is a difference between creating the text and displaying it..

---

### Post by bkpsusmitaa on 2013-09-02
> **ofnuts said:**
> There is a difference between creating the text and displaying it..
True! It appears that I did not have the capability to pinpoint the function $DISPLAY. Maybe I will improve with experience.
Now the main issue: 
[B]How to send any popups to the background?
[/B]

---

