---
title: "Computer wont shut down"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by Socinus on 2012-04-30
I seem to be having a problem whereby my machine wont shut down completely. It goes through the shutdown process; the monitor, keyboard, and mouse all shut down but the CPU itself stays on. at that point, I have to yank the plug to turn it off because it wont accept input from any other button or control. It cant be turned off manually any other way and no other button will turn it back on fully.
 

This is a problem that has manifested after installing Ubuntu.

---

### Post by audiomick on 2012-04-30
I don't know what might be wrong, sorry.

You could try the command

```
sudo shutdown -P now
```

Firstly, this should turn your computer off. If it doesn't work, then I would be looking for some BIOS option or something outside the OS for the reason that it is not shutting down properly. As far as I know, this should always work.

Secondly, until you figure out what is wrong, and assuming this does work, you can shut down your system cleanly with this command.

Sorry I can't be of more help.

---

### Post by RJARRRPCGP on 2012-04-30
The default BIOS setting are set to allow the OS to shut down the PC. Has been that way, at least since 1998.

---

### Post by livewire94 on 2012-04-30
Mine locks up on shutdown sometimes.  I think its related to the video driver and 3d Unity.  I read that if you logout first then shutdown, it works.  I tried it and works for me.

---

### Post by Socinus on 2012-05-02
> **audiomick said:**
> I don't know what might be wrong, sorry.

You could try the command

```
sudo shutdown -P now
```

Firstly, this should turn your computer off. If it doesn't work, then I would be looking for some BIOS option or something outside the OS for the reason that it is not shutting down properly. As far as I know, this should always work.

Secondly, until you figure out what is wrong, and assuming this does work, you can shut down your system cleanly with this command.

Sorry I can't be of more help.
The sudo command worked, but it only worked once :(

---

### Post by CharlesA on 2012-05-02
> **Socinus said:**
> The sudo command worked, but it only worked once :(
?

How are you trying to shutdown the machine?

---

### Post by Socinus on 2012-05-04
> **CharlesA said:**
> ?

How are you trying to shutdown the machine?
I selected Shut Down from the dropdown menu in the top right corner of the screen.

With the Terminal, I open the terminal, type the command in, and the computer shut down. At least it did once.

---

### Post by CharlesA on 2012-05-04
> **Socinus said:**
> I selected Shut Down from the dropdown menu in the top right corner of the screen.

With the Terminal, I open the terminal, type the command in, and the computer shut down. At least it did once.
Yeah, it's probably due to the graphics drivers.

---

### Post by Socinus on 2012-05-05
So what would I do to see if that's the case and to remedy it?

---

### Post by CharlesA on 2012-05-05
Just shutdown from the terminal for the time being.

Have you submitted a bug report?

---

### Post by Jacobonbuntu on 2012-05-09
> **Socinus said:**
> I seem to be having a problem whereby my machine wont shut down completely. It goes through the shutdown process; the monitor, keyboard, and mouse all shut down but the CPU itself stays on. at that point, I have to yank the plug to turn it off because it wont accept input from any other button or control. It cant be turned off manually any other way and no other button will turn it back on fully.
 

This is a problem that has manifested after installing Ubuntu.

Are you using precis already?
I had that with my laptop ocasionally with Oneiric, not once since I switched to Precise

---

