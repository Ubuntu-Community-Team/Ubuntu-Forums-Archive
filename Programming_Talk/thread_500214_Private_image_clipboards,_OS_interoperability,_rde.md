---
title: "Private image clipboards, OS interoperability, rdesktop, and shell glue."
date: 2007-07-13
forum: Programming Talk
---

### Post by psych787 on 2007-07-13
I moved to Linux mainly to take advantage of Metisse (I can't stand oversized windows taking up all my space). Since then I have used VMWare Server, rdesktop, and some shell glue to translate fileparameters. However, I have recently hit a little roadblock with this strategy: **images on the clipboard**.

Consider the following scenario: OpenOffice Draw is running natively in Linux. MS Word is running through rdesktop however, which does not support image clipboard formats. I need to cut and paste my OpenOffice Draw flowchart into MS Word. When I try to do so, nothing happens. The same probelm obviously happens when trying to copy an image from MS Word to OpenOffice.

My idea to fix this is to write a script for the VM (batch, Monad, or bash) which detects clipboard changes, saves those to a file on Z: (the Linux filesystem), and sends an SSH command to Linux when they occur. Linux would then either copy the text to clipboard, or convert the image to an acceptable format before copying it to the clipboard.

Unfortunately, I can't find a program to dump non-text clipboard data from the command line in windows OR linux. I also cannot find a program to write that data. However, that isn't the least of my worries. Additionally, Linux programs including the GIMP, OpenOffice, and GNU Paint seem to use private clipboards for images - images cannot be coppied/pasted between them.

On a final note, is there a better way to script SSH commands than expect?

---

### Post by cwaldbieser on 2007-07-14
> **psych787 said:**
> 
On a final note, is there a better way to script SSH commands than expect?

I don't know about any of the clipboard-related questions, but if you use key-based SSH authentication, you should be able to just use a shell script without having to use expect.

---

### Post by psych787 on 2007-07-14
Yes, you're right - I just realized that you could send commands through ssh by placing the desired command afterwards like this:
```

ssh user@site.com "echo test ; echo test2"

```
I should have looked at the man page for that before now, but sometimes these computer problems are too frustrating to think straight... :confused:

Now I still have to fix my clipboards. That issue is still looking pretry grim - mabye I'll just have to shift even more programs to the VM....

Note: If there were some kind of package-based installer for open-source programs in Windows, similar to APT, that would make shifting the few rich-clipboard intensive programs like GIMP and OpenOffice much more feasible.

---

