---
title: "Don't know how to revert back to GUI boot"
date: 2014-11-01
forum: New to Ubuntu
---

### Post by Gloris_Ian on 2014-11-01
After using ubuntu for a few days I managed to flesh out most of the issue, but I once had to make it boot with console (text) mode without a real GUI. After I solved the issue that way, now I cannot get it back to boot regularly with the GUI or interface, how do I do that? Everytime I boot my pc I get these huge walls of texts and it's nothing that I can't handle, it's just annoying, so any suggestions please? Thanks in advance, And love ubuntu

---

### Post by steeldriver on 2014-11-01
It depends how you made  it boot into text mode (there are several ways... via grub, via /etc/init/lightdm.override, ...) - can you remember what exactly you changed?

---

### Post by whitesmith on 2014-11-01
If you got into a tty (terminal or command line in Winspeak) by doing an Alt+Ctrl+Fx, you can get back to the familiar GUI by doing Ctrl+Alt+F7. Try that out. Regards.

---

### Post by Gloris_Ian on 2014-11-01
whitesmith: I'm pretty sure that's not the way I got into it, don't recall using any app named "Winspeak", but I tried those shortcuts and it's not working

steeldriver: I remember editing a text of some sorts, Pretty sure that's the way I made it boot into console, how do I revert back to regular GUI boot?

Also, a noob question, how do I find my personal messages here?

---

### Post by sudodus on 2014-11-01
Did you add the boot option **text**?

In that case, remove it from the file
```

/etc/default/grub
``` save the change and run ```
sudo update-grub
```

---

### Post by whitesmith on 2014-11-01
Then open a terminal by doing Ctrl+Alt+1. Type```
startx
```Where, if anywhere, does this take you? By the by, I was being facetious in using the term Winspeak -- I simply meant how the terminal is so styled in that Other Operating System. Best of luck to your efforts in digging out of this hole. **This** is the way to learn Linux, a little tough at times, but a thorough and memorable teacher. Warmest regards.

---

### Post by Gloris_Ian on 2014-11-01
Okay, the problem is solved now, but not in a regular fashion. I screwed up the entire system and had to reinstall the entire ubuntu. Thank God I postponed the transfer of my work and other sensitive files, otherwise, they would now be lost. Because of that I do not have to worry about how to get back the GUI boot, I now have it by default. Well, if you are wondering what happened feel free to read on (but don't laugh please).






Tried "startx" command and it wouldn't work. I thought it was because of permissions. So I thought It would be a good idea to use "sudo startx". :) Guess I was wrong, I was using windows since win 95, just recently started using ubuntu and I obviously have a LOT to learn. Got used to the idiot-proof design of windows, this thing actually demands you to learn it to use it, I like that, since windows treats you like a retard. Anways off topic sorrry, tried to log back in after that command but couldn't, and couldn't solve it reading other peoples solution so reinstalled. Thanks anyways! :)

---

### Post by Bashing-om on 2014-11-01
Gloris_Ian; Hello;

All good that ends well.

All a process of learning -> greatest operating system - IMHO - the world has ever known. Hang in there.
No one will laugh at you here, we know what that learning curve is. We were all beginners at one time.
Ask and thou shalt receive .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]Happy trials to you
[/INDENT][/INDENT]

---

