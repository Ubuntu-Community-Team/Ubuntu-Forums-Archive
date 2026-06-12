---
title: "How much ram is a reasonable assumption?"
date: 2007-09-02
forum: Programming Talk
---

### Post by DMills on 2007-09-02
I am a contributor to a project (The Rivendell broadcast automation system - [http://www.rivendellaudio.org](http://www.rivendellaudio.org)), part of which involves the reliable playback/recording of multiple .wav files over a LAN (NFS mounted shared drive array). 

I am in the throws of refactoring the main audio playback/recorder engine. Now, given that I can handle up to 16 files playing and 8 being recorded per sound card on a given machine (and we support up to 8 cards per machine), and given there may be multiple machines on the network, the question comes up as to how large I need to make the ring buffers to ensure reliable operation... 

The simple answer is as large as possible, and anecdotal reports from the Ardour crowd indicate that 5 seconds is about the minimum for really reliable operation (= 48 * 4 *2 *5) = ~2MiB per stream (The 4 is because I am working in FP at that point) . Physically locking down this much memory for a reasonable quantity of streams becomes the interesting question as it would put well over a hundred MB of physical ram out of use for any other application (and this could rise to the thick end of a half a GiB in the worst case).

Given that not much else will be running (these are special purpose boxes), and that the playout engine is a daemon started at boot  how far is it reasonable to push this?

I am tempted to work on the assumption that ram is cheap (compared to dead air), and give the playout engine say 10s of buffering per stream, for a minimum spec of ~512 - 1 GiB per fully loaded box (Less if you only fit a single card). 

Thoughts appreciated (especially from other multimedia developers). 

Regards, Dan.

---

### Post by aks44 on 2007-09-02
> **DMills said:**
> I am tempted to work on the assumption that ram is cheap (compared to dead air), and give the playout engine say 10s of buffering per stream, for a minimum spec of ~512 - 1 GiB per fully loaded box

I'm not much into multimedia myself, but provided your target audience it looks like demanding at least 1GiB of RAM is quite reasonable.

Just a thought: your bottleneck being network traffic, I'd tend to suggest to use local disk buffers as well since they are faster than network and way cheaper than RAM ; it may allow more tolerance on the network side. But again, I have virtually no experience in multimedia (not to speak about real time streaming) so I may well be totally off the tracks with this one, performance-wise.

---

### Post by DMills on 2007-09-02
> **aks44 said:**
> I'm not much into multimedia myself, but provided your target audience it looks like demanding at least 1GiB of RAM is quite reasonable.

Yea, you are probably right, means I have to make it configurable for people who are just testing, not difficult but a little boring.
> 
Just a thought: your bottleneck being network traffic, I'd tend to suggest to use local disk buffers as well since they are faster than network and way cheaper than RAM; 

Thruput is not a problem, latency is, and local disks can have latency just as bad as the disks on the server. Further I am planning some custom hardware for studio use that will have no local storage (maybe PXE Boot and load system from network, or failing that, boot from R/O flash). I am still trying to solve the thermal problems of passively cooling a low end C2D in a 1 or 2U rack box. Ideally, I want no moving parts, but that is proving a tough engineering problem (Involving lots of copper blocks and heatsinks). Underclocking helps, but I still need to dump ~40W with less then a 20 degree temperature rise, surprisingly tricky to pull off reliably. Unfortunately the Via stuff just does not quite cut it when using affordable audio hardware.

Regards, Dan.

---

