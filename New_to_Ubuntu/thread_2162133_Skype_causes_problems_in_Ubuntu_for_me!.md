---
title: "Skype causes problems in Ubuntu for me!"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by Ludowicus on 2013-07-13
[B][SIZE=2][FONT=arial][SOLVED]
Skype sounds stops media player or other sound sources 
[/FONT][/SIZE][/B]

[SIZE=2]
I can't talk with people on skype and at the same time have sound from other sound sources. I have tried using [these]("https://wiki.archlinux.org/index.php/Skype#Problem_with_Audio_Playback_on_x86_64") solutions for the problem, but nothing worked.
I am using Ubuntu 12.04 64-bit, I just started using GNU/Linux for the first time so if you could help me with my move to Linux it would be great :) I don't want to go back to Windows, but if I can't solve these problems I might have to go back.

Q. What happens when you try calling someone while sound is coming from another sounds source?
A. Skype just returns [/SIZE]"Problem with Audio Playback".

Q. Can you have multiple sound sources at all?
A. Yes!

Q. Have you PulseAudio installed?
A. Yes!

Q. Are you using PulseAudio as output source for skype?
A. I am using a output source called "pulse", so I guess I am using PulseAudio.

[SOLUTION]

 ```
sudo apt-get lib32-libpulse
```

---

### Post by dannyboy79 on 2013-07-13
where did you install skype from?

---

### Post by Ludowicus on 2013-07-14
Skype was installed with the latest deb package from the official website.
btw, I have now tried the things on [this]("https://wiki.archlinux.org/index.php/Skype#Problem_with_Audio_Playback_on_x86_64") site but it did not work. If I try calling someone when I am listening to music or something skype just returns "Problem with Audio Playback".
Maybe I am not using PulseAudio correctly, I don't know.

---

### Post by newb85 on 2013-07-14
I don't seem to have a problem with it on my 13.04 system.  But I installed the latest version from the repositories.  (In 12.04, I think you have to enable the Partners repository to do this.)

---

### Post by _0R10N on 2013-07-14
@Ludowicus I just want to say that the first link you provided solved my problem of crackling noise. Thanks!

---

### Post by Ludowicus on 2013-07-14
@_0R10N I am glad that someone got his problem fixed ^^

@newb85 Ok! I will try to install from the repositories and see if it works. Otherwise I guess I could try to upgrade to 13.04 and see if that solves the problem.

---

### Post by newb85 on 2013-07-14
Out of curiosity, what specific application are you using to listen to music when this happens?

---

### Post by Ludowicus on 2013-07-14
I am using Rythmbox to play music. But just as I said before, I can't hear sound from any audio source while I am in a skype conversation.
And if I have music on, or if I am watching a video or whatever that makes sounds before I try to enter a skype conversation, skype just returns "Problem with Audio Playback".

---

### Post by Ludowicus on 2013-07-14
Oh! how could I miss that? Could [this]("https://wiki.archlinux.org/index.php/Pulseaudio#Skype_.28x86_64_only.29") be the solution?
I tried ```
sudo apt-get install lib32-libpulse
``` but it could not find the package.
How do I install that?

---

### Post by _0R10N on 2013-07-15
Weird! I never needed to install any 32-bits library... but cool it worked for you!

---

### Post by newb85 on 2013-07-15
> **Ludowicus said:**
> Oh! how could I miss that? Could [this]("https://wiki.archlinux.org/index.php/Pulseaudio#Skype_.28x86_64_only.29") be the solution?
I tried ```
sudo apt-get install lib32-libpulse
``` but it could not find the package.
How do I install that?

I could be wrong, but I think that package is bundled under the name libpulse0 in Ubuntu.   On my system, the i386 package is also installed. I think this was done automatically when I installed Skype from the repos.

---

