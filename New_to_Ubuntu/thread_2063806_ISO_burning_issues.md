---
title: "ISO burning issues"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by Arcturus582 on 2012-09-27
I have an ISO that I'm attempting to burn to a dvd.  I know the ISO isn't dead since I am able to run it in both WINE and VIRTUALBOX, but every time I try to burn it, it is no longer recognized when I put it in the drive. I've gone into the software center and downloaded every ISO archive in every language just in case, and have tried a few different burning programs. Some don't even recognize it.  So far nothing works. It is supposed to be a boot disk...instead I have made several great frisbees. Any help would be wonderful.

---

### Post by newb85 on 2012-09-27
It's an .iso of what?

Which burning programs have you used?

Have you successfully burned other DVDs?

---

### Post by agillator on 2012-09-27
First, when you burn it are you certain you are telling the burner to burn it as an image, not as a file? Easy to confuse and get the wrong product. 

Second, mount the iso directly with 'sudo mount -o loop <iso file path> <mount point> and then see if you can list a directory or something.

---

### Post by Metallion on 2012-09-28
what happens when you type this in a terminal?

wodim -v /path/to/your/iso/file.iso

---

