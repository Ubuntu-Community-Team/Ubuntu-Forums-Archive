---
title: "Screen flickering between comand prompt and company logo while startup in ubuntu 22.0"
date: 2022-09-09
forum: New to Ubuntu
---

### Post by anupkrs on 2022-09-09
Details : OS : Ubuntu 22.04 Graphics : radeon Graphics Problem : while startup screen is flickring between logo and comand prompt. Screen is flickring while turning and between lenovo logo and this below compand pprompt

While turning on laptop it start happening

and also the letter D is printing automatically.
**PLEASE HELP**

---

### Post by MAFoElffen on 2022-09-09
Does it boot okay if you start is up on an Ubuntu Live Install disk if you do "TRY"? 

If so, please run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script so I can see your graphics hardware and settings,so I can come up with and informed solution.

---

### Post by anupkrs on 2022-09-10
No while booting also from live disk this happens .earlier everything was okay while i was on windows but after i installed ubuntu yesterday  it start happening .
I have radeon graphics and intel graphics.

---

### Post by anupkrs on 2022-09-10
[IMG]https://www.reddit.com/r/Ubuntu/comments/x9pltd/why_my_screen_is_flickring_while_startup_in/?utm_medium=android_app&utm_source=share[/IMG]
**This is video of screen flickering **
[https://www.reddit.com/r/Ubuntu/comments/x9pltd/why_my_screen_is_flickring_while_startup_in/?utm_medium=android_app&utm_source=share](https://www.reddit.com/r/Ubuntu/comments/x9pltd/why_my_screen_is_flickring_while_startup_in/?utm_medium=android_app&utm_source=share)

---

### Post by QIII on 2022-09-10
That makes me suspect a stuck key.  Is this a laptop?

---

### Post by anupkrs on 2022-09-10
Yes this is a laptop .what should i do earlier i was using windows but that was working fine .can you help me with this issue.

---

### Post by MAFoElffen on 2022-09-10
What happens if, at the Grub boot menu, you temporarily edit the Linux boot line by adding a 'nomodeset' boot parameter?

I asked if you could run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info"). Since then, you mention that you have both Intel and AMD Radeon graphics. From looking at your video, I see it's a Lenovo. (Which I am still certified as a Dell, HP and Lenovo Warranty Service Tech.) Running that report will tell us your hardware, to include the CPU, GPU, system settings... to include the graphics settings and graphics environment, and the Linux boot command line... This was written to help helpers on the Forum, to help users like you.

Oh... You haven't mentioned if it continues to flicker once you log in at the Graphical Login screen, and the Desktop comes up... Can you get to that at all?

---

### Post by MAFoElffen on 2022-09-10
@all.

User went to Reddit. There he explained that the problem is during the boot process. He posted 2 more photo's there. One looked like it loaded a Out of Memory (something) and lots of modules...

He said there that everything is fine in both Windows and Ubuntu, after he logs in and gets to the desktop. He doesn't have any problems in Ubuntu...

He listened to someone on Reddit, and is sending it to a shop... Where he (IMHO) will waste his money. It's not a hardware problem. It is a software config problem.

If he tries to start it will "nomodeset" it will probably fix it temporarily... from there, tweaking that for AMD Radeon GPU for a permanent fix. That and looking at his active drivers fro his AMD Radeon GPU.

---

