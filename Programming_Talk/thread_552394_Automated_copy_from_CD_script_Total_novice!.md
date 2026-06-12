---
title: "Automated copy from CD script? Total novice!"
date: 2007-09-16
forum: Programming Talk
---

### Post by Wildscot on 2007-09-16
Hi,

I'm very new to Linux and Ubuntu but I'm fascinated and very keen to learn.
However, at the moment I really need some help to finish up a project that's way beyond where my learning curve is at right now.

What I'm after is a script that will recognise when a CD is placed in the drive and automatically copy the data to a specified folder with as little user interaction as possible, ideally none! I get the impression that a simple bash script would be able to do this but I don't even know enough of the terminology to know where to look.

If anyone can help I'd greatly appreciate it. I'll say again that I'm *very* new to Ubuntu and have no scripting experience so I'm afraid this is going to have to be explained quite clearly. I am very keen to learn though so any annotation to help explain what the code is doing would be very helpful.

Thanks in advance...

---

### Post by ssam on 2007-09-16
a first step would be using system -> preferences -> removable drives and media to trigger your script.

the program abcde may be what you need for doing the ripping.

it might be possible to put an abcde command into the removable drives preferences. however a script would let you do something like eject the disk afterwards (there is a command eject)

---

### Post by Wildscot on 2007-09-16
Thanks,

While abcde looks interesting I should maybe have said that these will be data cd's, not music.

I can see what you are getting at with the System>Preferences>Removable drives and media. Do you think that an easier approach might be to put the code on the disk itself and have that execute when the cd is inserted with the 'autorun programs on new drives and media' setting?

---

