---
title: "Installation query.....reformatting?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by groeswenphil on 2008-05-24
Hi group.

I've a feeling that my Ubuntu guru set up my system thusly.
3 partitions........one for xp, one for Ubuntu and one for my Ubuntu data. He explained that he did this so that he could perform clean installs in the future and not lose any data.

Now, following my attempt to upgrade from Dapper to Hardy, my Ubuntu side is broken.
I've a working Hardy disk......upon installation, will it give me the option to re-format or install over then now defunct system?
Or, should I re-format that sector of the disk  through the BIOS?

Strangely, I haven't been using Ubuntu of late, but came back to it a couple of weeks ago....after remembering how good it was I wanted to upgrade.
Thanks,
Phil

---

### Post by shifty_powers on 2008-05-24
well, for a start you can't format anything through your bios ;)

secondly, what it sounds like he has done is given you a / partition, i.e. root with all of your programs, and /home, with all your personal data.

when you reinstall, do a maunl partitioning, and just format and set up the / partitin as / again.

DO NOT FORMAT THE OTHERS

;)

---

### Post by groeswenphil on 2008-05-24
And if I format the partition where my broken Ubuntu resides, then install Heron, I'll have just one Ubuntu system working on my computer......sorry if I sound stupid, but I've never done this by myself before. I've a feeling that it will be a 'can do' job, but I need re-assuring.
Thanks,
Phil

---

### Post by shifty_powers on 2008-05-24
basically yes.

load up the live cd, click on install, go to manual partitioning.

then, all you ned to do is find the ubuntu partition, set the mount point as / and format. don't format the other ones.

also, he should have set you a swap partiton....

---

### Post by lswest on 2008-05-24
also, be sure to find your data partition and set the mountpoint as "/home" (without the quotes), and be sure to **NOT** format it.

---

