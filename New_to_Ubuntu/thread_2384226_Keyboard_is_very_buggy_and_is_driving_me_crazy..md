---
title: "Keyboard is very buggy and is driving me crazy."
date: 2018-02-04
forum: New to Ubuntu
---

### Post by matyd918 on 2018-02-04
Hopefully I can explain this clearly and accurately. When I am typing the cursor is very erratic. The line will move as I'm typing and my letters will begin typing in a new location so I will then have to delete the letters say (for example, as I'm typing it will move to the line above and if I'm not careful I will begin typing letters in the middle of a previously typed word etc.). This also happens frequently when the browser will suggest a string to search, like when I'm typing in a search bar with google in chrome. It happens when I'm typing in LibreImpress as well. This isn't application specific and there is no rhyme or reason as to why it's happening, that I've noticed. I guess I can check if there are drivers that I need to update but I don't believe that is the issue. Any help would be greatly appreciated.

[U]uname -a
[/U]Linux matthew-15-3567 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
Dell Inspiron 15 3567

I've taken Windows 10 completely off this machine and am only running Ubuntu.

---

### Post by matyd918 on 2018-02-04
So apparently if you disable Tap to Click in the settings then you won't have this problem...

---

### Post by coffeecat on 2018-02-04
> **matyd918 said:**
> So apparently if you disable Tap to Click in the settings then you won't have this problem...

Yes. As I was reading your first post, I was wondering if you were using a laptop. Most likely, your wrist was setting off the touchpad. Anecdotal evidence suggests that your wrist doesn't even have to touch or brush the touchpad for this to happen. I was plagued with this in Ubuntu with one laptop I had once.

Here are a couple of askubuntu links that contain some fixes and workarounds for this issue:

[https://askubuntu.com/questions/483707/14-04-touchpad-is-too-sensitive](https://askubuntu.com/questions/483707/14-04-touchpad-is-too-sensitive)

[https://askubuntu.com/questions/886092/how-do-i-disable-the-touchpad-while-typing](https://askubuntu.com/questions/886092/how-do-i-disable-the-touchpad-while-typing)

I like the sound of the libinput solution - better explained in the second link - but I have no experience of it. Hopefully, there is something in one of those links that will suit you and obviate the need to completely disable tap to click.

---

### Post by matyd918 on 2018-02-05
I'm super happy that I check back in on this thread! The installation of libinput has solved the issue, so far at least!

I literally installed it through the terminal and re enable tap to click. No more issues thus far! Thank you!

---

### Post by matyd918 on 2018-02-05
> **coffeecat said:**
> Yes. As I was reading your first post, I was wondering if you were using a laptop. Most likely, your wrist was setting off the touchpad. Anecdotal evidence suggests that your wrist doesn't even have to touch or brush the touchpad for this to happen. I was plagued with this in Ubuntu with one laptop I had once.

Here are a couple of askubuntu links that contain some fixes and workarounds for this issue:

[https://askubuntu.com/questions/483707/14-04-touchpad-is-too-sensitive](https://askubuntu.com/questions/483707/14-04-touchpad-is-too-sensitive)

[https://askubuntu.com/questions/886092/how-do-i-disable-the-touchpad-while-typing](https://askubuntu.com/questions/886092/how-do-i-disable-the-touchpad-while-typing)

I like the sound of the libinput solution - better explained in the second link - but I have no experience of it. Hopefully, there is something in one of those links that will suit you and obviate the need to completely disable tap to click.

Okay, so it worked for a while with libinput installed but I ended up having to disable tap to click again because it was beginning to move the cursor around again and select things etc. Technically this thread is solved because the issue is no more, ah well. Thank you though.

---

