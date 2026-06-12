---
title: "OpenGeu problem"
date: 2008-02-19
forum: Other OS Talk
---

### Post by IceReaver75 on 2008-02-19
I wanted to try out OpenGeu so I downloaded the 7.10 version off the website.  After the download I checked the Mdsum to make sure it was a good download and everything checked out fine.  I burned the iso to a cd at 8X speed since thats the lowest my burner would go.  I did a restart to boot into the live cd and now its getting stuck in a 

buffer I/0 error fd0

loop it keeps doing it until i alt-ctrl-delete to restart.  I thought maybe a bad burn so i burned another copy at the same speed......same problem.  Does anyone know why this is happening and how I can try to fix it to boot into the live cd?  Thank you for any help you may have.

---

### Post by r4ik on 2008-02-19
.At the first Opengeu screen upon booting from LiveCD, press F6. Add 'irqpoll' to the list of parameters. 

Hope this helps,

Good luck !

---

### Post by IceReaver75 on 2008-02-19
I tried what you suggested and it still get stuck in the buffer loop.  I just can't seem to get this live cd to boot for anything.  This is the only live cd i have ever had problems with.

I found what the problem was.  It was a problem with my floppy A drive.  I disabled it in BIOS and the live cd booted right up.  Thanks for the suggestion though.  Maybe others with the same problem will benefit with this option of disabling the floppy drive.

---

