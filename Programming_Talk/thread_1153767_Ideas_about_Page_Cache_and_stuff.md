---
title: "Ideas about Page Cache and stuff"
date: 2009-05-09
forum: Programming Talk
---

### Post by JohnLM_the_Ghost on 2009-05-09
Hello!
On first note I should say that this ain't exactly actual programming questions and ideas... not yet at least. These are rather abstract ideas and concepts for potentially upcoming software.

So after buying my new rig and using it for a quite while, I started to wonder that it doesn't fully use it's resources (RAM specifically)... and it sometimes feels it doesn't use cache the way I wanted to...

And then I came with an idea for a cache manager software.
In short it would
[LIST]
[*]Assist user and system (kernel) to better utilize cache.
[*]Allow user to manually manage cache (with front-end)
[*]Relieve some stress from storage devices (by using more aggresive cache rules)
[/LIST]

Now what actual manual operations it would provide...
[LIST]
[*]View cache contents (What files are cached)
[*]On-demand file caching (for quick access later)
[*]On-demand dumping of write cache
[*]Edit caching rules for file transfer operations (like copying)
[/LIST]
What good would it do?
Imagine you could make your box cache your favourite apps on startup for rapid access (like firefox or OpenOffice maybe?). The Manager should probably recursively discover associated files along with the binary.
Also you could cache very often read (but not written) files, let's say your homepage on your webserver, and likes. Of course Manager would also provide tools to free or at least demote cache priority.
Also dumping write cache is useful. For example there is quite aggressive caching rules for memory cards (and USB flash drives?) already. Often files you copy on it are not physically written on it until you try to unmount the drive and it makes unmounting quite time expensive (and dangerous for long-time Windows users, who like to remove the cards without unmounting). So with Manager you could manually make it dump the cache on device (and you could watch the actual progress!) and then have it unmounted swiftly whenever you feel like it.
Then I also thought something similar could be applied for hard drive. Not the unmounting part really, but more aggressive caching and queueing on file transfers. Let's say when you try to copy more than one big file at the same time, it starts to race for drive access, what definitely doesn't make it any faster, and it also leads to file fragmentation.
The Manager would queue the transfer sequentially, to make most of device's writing capacity (and reducing fragmentation on-the-way).
If the transferred files are fully cached, they also could be accessed by other programs, even before actual transfer is complete (meaning transfer should be transparent for other programs), with all operations done on cache. (or cache/actual mixture when all part of file is not cached anymore and application has it's own reading buffer). I also imagine writing operations to be available on cache, so already edited data is written without overwriting it once again (this would be a special case, cause to use most of the cache it's priority should be promoted, and transfer priority demoted, to minimize required disk access)
Anyway hard drive caching will be especially important for same-device operations. You can imagine how bigger cache buffer would benefit move and copy operations between different partitions on same disk.
Here also the rules configuration would come in. By specifying caching global rules, per-device and maybe even per-application rules you could get the most of your cache and performance.

That all said, I know the target audience will NOT be general public, but advanced computer users, cause the program will not be simple, well at least it won't be usual. Casual users hardly care about caching, but I believe for advanced users (like myself) it only benefits for cache to be revealed instead of being abstracted (this meant in visual sense not in implementation).

Now there are few thing I wanted to know.
Firstly I know my proposed program would need some interaction with kernel... is it possible to do this with current kernel, or would it require to write a module specifically for this purpose?
Secondly I want to know what is actual caching policy for current kernel, and whenever tools exist to alter them?

And also good insights, ideas, comments... maybe some critique too (I don't mind critique, just be constructive)!
I'm not the best programmer ever, but I consider start developing such program.
Also if anyone is up to take initiative for developing this (or if something like this exist) I want to be in it! :)

p.s. I might do a little mockup of front-end when I feel like it.
I might also post this idea in Ubuntu brainstorm site and/or open new Lauchpad project later on.

**EDIT**:
So on-demand buffer/cache dumping is already implemented by **sync** command. No need to reinvent that at least!

---

### Post by SlickRick on 2009-05-09
This does look quite interesting. I don't consider myself to be an advanced user but I would find something like this very useful. I don't know if there is already something like this available but if there is, it shouldn't be hidden away and people should know about it including me.

After 5 minutes of research on google, I couldn't find anything so I assume that nothing similar exists. I'll be sure to stay tuned to this thread to see what other people have to say.

---

### Post by slavik on 2009-05-09
> **JohnLM_the_Ghost said:**
> So after buying my new rig and using it for a quite while, I started to wonder that it doesn't fully use it's resources (RAM specifically)... and it sometimes feels it doesn't use cache the way I wanted to...

Please explain this piece.

As for the rest ... kernel hack much?

---

### Post by JohnLM_the_Ghost on 2009-05-09
> **slavik said:**
> Please explain this piece.

That's a one-liner background story.

I meant I have 4GiB RAM and I have usually around 1GiB used... 
I was wondering if that includes the cache? (whatever gnome system-monitor reports)
And if it does - I have 3 GiBs doing nothing when it could hold cache... And I do lots of file transfers, and it always slows my computer down (I can feel slowdown for Linux more than Windows, for some obscure reason).
And it really turns to hell when I try more than one file transfer and/or when free space is getting really low!

I can't really say if my hypothetical program would speed up my computer on actual file transfers, but it would surely make my workday easier with transfer queuing, reduce some daily wear and tear from HDD and make my apps start up faster.
Pretty much all I want from it!

---

### Post by lloyd_b on 2009-05-09
> **JohnLM_the_Ghost said:**
> That's a one-liner background story.

I meant I have 4GiB RAM and I have usually around 1GiB used... 
I was wondering if that includes the cache? (whatever gnome system-monitor reports)
And if it does - I have 3 GiBs doing nothing when it could hold cache... And I do lots of file transfers, and it always slows my computer down (I can feel slowdown for Linux more than Windows, for some obscure reason).
And it really turns to hell when I try more than one file transfer and/or when free space is getting really low!

I can't really say if my hypothetical program would speed up my computer on actual file transfers, but it would surely make my workday easier with transfer queuing, reduce some daily wear and tear from HDD and make my apps start up faster.
Pretty much all I want from it!

Open a terminal window, and run "free -m" - this will give you a decent picture of memory utilization, showing definitively how much is being used for buffers/cache.

By default, Linux will attempt to use every bit of physical RAM, filling it with cache if it has no other use for it.  The kernel hackers have put a LOT of effort into the cacheing system, so I suspect a manual application messing with the cache would make things *less* efficient, rather than more...

Lloyd B.

---

### Post by JohnLM_the_Ghost on 2009-05-09
> **lloyd_b said:**
> Open a terminal window, and run "free -m" - this will give you a decent picture of memory utilization, showing definitively how much is being used for buffers/cache.

By default, Linux will attempt to use every bit of physical RAM, filling it with cache if it has no other use for it.  The kernel hackers have put a LOT of effort into the cacheing system, so I suspect a manual application messing with the cache would make things *less* efficient, rather than more...

Lloyd B.
Thanks!
Apparently I have pretty much all my RAM allocated for cache after all.
Well I still want to know inner workings and policies of caching and buffering on Linux.

Hmmm.... any way to see what exactly is in there?

---

### Post by lloyd_b on 2009-05-10
> **JohnLM_the_Ghost said:**
> Thanks!
Apparently I have pretty much all my RAM allocated for cache after all.
Well I still want to know inner workings and policies of caching and buffering on Linux.

Hmmm.... any way to see what exactly is in there?

I don't know if there is a way to see exactly what's in the cache.

Here's a link to some [further info on the cache]("http://www.westnet.com/~gsmith/content/linux-pdflush.htm") that explains what tuning parameters are available, and has additional links that may help you understand exactly what's going on "under the covers".

Lloyd B.

---

### Post by JohnLM_the_Ghost on 2009-05-10
> **lloyd_b said:**
> I don't know if there is a way to see exactly what's in the cache.

Here's a link to some [further info on the cache]("http://www.westnet.com/~gsmith/content/linux-pdflush.htm") that explains what tuning parameters are available, and has additional links that may help you understand exactly what's going on "under the covers".

Lloyd B.

Thanks a lot!
This will keep me busy for a little while!

---

### Post by SlickRick on 2009-05-10
I remember reading in a different thread that you can somehow mount your RAM as a storage media and basically put anything you want in there. If, for example, you want a game to run faster, you just put all the game files manually into the RAM. I'm not sure if you can make it do this automatically or whether or not linux already does when running a game or application. I suspect that this method would only make an application boot up faster but run at the same speed since an active application or game is put into RAM anyway.

Correct me if none of that made any sense :P

---

### Post by JohnLM_the_Ghost on 2009-05-10
> **SlickRick said:**
> I remember reading in a different thread that you can somehow mount your RAM as a storage media and basically put anything you want in there. If, for example, you want a game to run faster, you just put all the game files manually into the RAM. I'm not sure if you can make it do this automatically or whether or not linux already does when running a game or application. I suspect that this method would only make an application boot up faster but run at the same speed since an active application or game is put into RAM anyway.

Correct me if none of that made any sense :P

Well you're correct! It's possible to put files in RAM by using **tmpfs** file system.
But copying apps in tmpfs is not a smart idea.
Firstly, it takes precious RAM away from cache (and it might sometimes copy data from tmpfs to cache making two copies in RAM)
Secondly, any boost for program's startup is still paid with moving data to tmpfs... so in reality it will take the same time (if not more) than starting up from disk.
Main reason for this being: tmpfs IS NOT cache and they're handled differently by system.

However, there's been a discussion whenever mounting /tmp to tmpfs is smart idea.
Well probably it doesn't really matter, since files written to /tmp are cached either way, only difference being whenever those files are dumped to hard disk. (But if you have little RAM they become dumped to HDD either way... difference being either on partition or swap space)

Also my idea of on-demand caching would be different in the sense that user could request an application to be (pre)cached before request to run that particular is made.
Since it would cache it in both situations, there's a slight advantage caching it earlier - it will make the app start up faster.

---

### Post by lloyd_b on 2009-05-10
> **SlickRick said:**
> I remember reading in a different thread that you can somehow mount your RAM as a storage media and basically put anything you want in there. If, for example, you want a game to run faster, you just put all the game files manually into the RAM. I'm not sure if you can make it do this automatically or whether or not linux already does when running a game or application. I suspect that this method would only make an application boot up faster but run at the same speed since an active application or game is put into RAM anyway.

Correct me if none of that made any sense :P

What you are describing is called (appropriately) a "ramdisk".  By default, Ubuntu installs a type of ramdisk (using the "tmpfs" filesystem) at /dev/shm.  This is a bit different from a traditional ramdisk in that it uses no RAM until you copy something into it.

Since Linux does its best to cache everything in RAM, there really isn't that much use for a ramdisk, except for special cases.  For instance, you could download files to a ramdisk, and then copy them to the hard drive, which results in the copying being done all in one burst rather than a bit at a time.  But for the most part, ramdisks don't really solve anything anymore.

Lloyd B.

Edit: Looks like you beat me to it :)

---

### Post by MadCow108 on 2009-05-10
> **JohnLM_the_Ghost said:**
> ...
What good would it do?
Imagine you could make your box cache your favourite apps on startup for rapid access (like firefox or OpenOffice maybe?). The Manager should probably recursively discover associated files along with the binary.
Also you could cache very often read (but not written) files, let's say your homepage on your webserver, and likes. Of course Manager would also provide tools to free or at least demote cache priority.
...

Isn't this pretty much what preload does?

---

### Post by JohnLM_the_Ghost on 2009-05-10
> **MadCow108 said:**
> Isn't this pretty much what preload does?

Cool! Never knew of such program!
[http://sourceforge.net/projects/preload](http://sourceforge.net/projects/preload)

I should look into it a bit more, too!
Though it is masked on Gentoo (what I'm currently running). A shame!

---

