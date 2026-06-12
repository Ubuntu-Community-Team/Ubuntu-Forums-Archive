---
title: "Reading from sound card in linux"
date: 2009-03-03
forum: Programming Talk
---

### Post by roccivic on 2009-03-03
Hi all,

I have a **very basic** understanding of how I can read from the sound card in linux. I know I can read it directly from /dev/dsp (after configuring it through ioctl() ). There probably are other ways though....

My question is:
Can I read/record 3 channels at the same time?
For example, can I record Line-in in stereo and at the very same time record Mic-in in mono to 1,2 or even 3 separate files/buffers?

Many thanks,
Rouslan

---

### Post by roccivic on 2009-03-04
bump

---

### Post by Zugzwang on 2009-03-04
> **roccivic said:**
> My question is:
Can I read/record 3 channels at the same time?
For example, can I record Line-in in stereo and at the very same time record Mic-in in mono to 1,2 or even 3 separate files/buffers?


Most sound cards do not support this. If yours does, you will need to switch to a more complex way of addressing the sound card anyway, like for example using the JACK library.

---

### Post by Krupski on 2009-03-05
> **roccivic said:**
> Hi all,

I have a **very basic** understanding of how I can read from the sound card in linux. I know I can read it directly from /dev/dsp (after configuring it through ioctl() ). There probably are other ways though....

My question is:
Can I read/record 3 channels at the same time?
For example, can I record Line-in in stereo and at the very same time record Mic-in in mono to 1,2 or even 3 separate files/buffers?

Many thanks,
Rouslan

As far as I know, the answer to your question is "no".

You can set /dev/dsp to record mono or stereo, set the sample rate and the bit size, etc... but all the data reads from "/dev/dsp".

Even with simple 2 channel stereo you have to split up the data stream yourself if you want to send each channel to a separate buffer.

You can use the analog MIXER to also include a third channel like mike-in, but that data will just be superimposed onto one, the other or both stereo channels.

Remember, you get ONE data stream and if it's stereo information, YOU have to split it up accordingly. And that's it. You don't get 3, 4 or more channels.

The best you can do is analog mix in more channels.

Hope this helps.

---

