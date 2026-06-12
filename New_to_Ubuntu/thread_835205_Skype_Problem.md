---
title: "Skype Problem"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by JohnSearle on 2008-06-20
I am currently having a problem with Skype and Pulseaudio. Basically the problem is that if any program is simultaneously using the audio along side Skype, then one of them won't work. For instance, if I'm listening to music in Aramok when I get a call on Skype, then Skype reports an audio problem. Otherwise, both applications work fine separately.

I have made shallow attempts a number of times to fix this problem, which included following some posted tutorials on (supposedly) related problems, but nothing have fixed it. Does anyone have a guide to a fix for THIS specific problem? Or better yet, can some inform me on how to go about fixing this?

Thanks,

- John

---

### Post by JohnSearle on 2008-06-21
anyone?

---

### Post by lemmy999 on 2008-06-21
AFAIK there is a known issue with Skype and all sound apps in linux. I am not aware of anyone who has actually fixed this one. Unfortunately Skype is a proprietary ( closed source) app so no-one has been able to look at the code.

---

### Post by JohnSearle on 2008-06-21
> **lemmy999 said:**
> AFAIK there is a known issue with Skype and all sound apps in linux. I am not aware of anyone who has actually fixed this one. Unfortunately Skype is a proprietary ( closed source) app so no-one has been able to look at the code.

Thanks for the reply.

I do realize that Skype is closed source, but my thought is that someone might have solved the issue through techniques other than looking at the code... such as emulating the alsa sound for Skype only. I'm sure there has to be a way to temporarily fix this without altering Skype.

I do hope, however, that the Skype crew fix the app eventually.

- John

---

### Post by viciouslime on 2008-06-21
That known issue was only in old 1.x versions as they used OSS instead of alsa, the new 2.x versions should work fine...

---

### Post by JohnSearle on 2008-06-21
> **viciouslime said:**
> That known issue was only in old 1.x versions as they used OSS instead of alsa, the new 2.x versions should work fine...

That's what I would've hoped, but I'm running the 2.x version, and I still have the same problems. It gives me an audio error when another app is running sound.

- John

---

