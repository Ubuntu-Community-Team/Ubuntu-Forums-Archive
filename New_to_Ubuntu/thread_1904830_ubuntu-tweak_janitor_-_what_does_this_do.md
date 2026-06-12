---
title: "ubuntu-tweak janitor - what does this do?"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by Geoff16W on 2012-01-05
Hi everybody.
I've just installed ubuntu-tweak and I'm looking at this new janitor feature. A lot of people seem to be happy with this feature, but I don't understand what's going on. It's listing about 500 mb of stuff to clean. 

About 300 mb from "apt-cache" about 200 mb of "old-kernel" as well as a few other things. The apt-cache lists a lot of .deb files of programs that I use. 

Do I need these files and what is "janitor" doing when it cleans --just deleting, I assume?

Can anyone explain to me what the "apt-cache", "thumbnail cache" and "old-kernel" are?

Obviously, I'm a bit of newbie at Ubuntu, but I like to know what's going on. Thanks for any thoughts you have.

---

### Post by cortman on 2012-01-05
> **Geoff16W said:**
> Hi everybody.
I've just installed ubuntu-tweak and I'm looking at this new janitor feature. A lot of people seem to be happy with this feature, but I don't understand what's going on. It's listing about 500 mb of stuff to clean. 

About 300 mb from "apt-cache" about 200 mb of "old-kernel" as well as a few other things. The apt-cache lists a lot of .deb files of programs that I use. 

Do I need these files and what is "janitor" doing when it cleans --just deleting, I assume?

Can anyone explain to me what the "apt-cache", "thumbnail cache" and "old-kernel" are?

Obviously, I'm a bit of newbie at Ubuntu, but I like to know what's going on. Thanks for any thoughts you have.

Apt-cache is the actual lists both of the software repositories and packages in the repositories. Clearing out old cache files probably won't do any harm. If you run

```
sudo apt-cache gencaches
sudo apt-get update
```

I don't think you have anything to worry about.

The old-kernel is just what it sounds like- old kernel versions. You've apparently upgraded the kernel at least once. Unless you keep the old kernels for development or bug tracking you can have janitor delete them.

---

### Post by Frogs Hair on 2012-01-05
Unlike computer janitor  , Ubuntu Tweak Janitor has never removed any needed packages . Whether you want to keep an extra kernel is up to you . I have not needed the option since 9.10 , but some users suggest keeping one kernel besides the one in use. 

When you update a kernel the old one is not removed automatically , so over time you can end up a lot of extra kernels .

Apt cache would be files that remain in the cache after software installation including updates . 

The link is dated but still applicable . [http://embraceubuntu.com/2006/02/15/clean-up-old-thumbnails/](http://embraceubuntu.com/2006/02/15/clean-up-old-thumbnails/)

---

### Post by Geoff16W on 2012-01-05
Thanks everybody, very helpful.
jw

---

