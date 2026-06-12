---
title: "[SOLVED] First experience with Bit Torrent - need some additional explanations"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by fballem on 2008-09-19
I am getting towards the end of my first download with Bit Torrent - after 4 days. It is a big file, so I expected that it would take a while, but I do have some questions.

I have a high speed link to the internet. I have noticed, often, that the upload speed is much higher than the download speed - numbers higher than 50KBs up, and lower than 20KBs down at the same time are very common. In one extreme case, I noticed 75KBs up and 5KBs down. Is there something that I can do to make the balance a little more fair?

I'm using Transmission from the repos. Is there a program that I should try that might result in a better balance. I think I understand the basic concept of being part of a swarm, but this particular member of the swarm is probably being punished for having a high-speed link and I'm not sure that's fair.

So that I can understand it better, is there a basic tutorial on Bit Torrent, are there settings that I can use in Transmission, or should I be using a different program?

Thanks,

---

### Post by k33bz on 2008-09-19
Try deluge, it is easier to customize and configure that one.

---

### Post by Therion on 2008-09-19
When torrenting your download speed is relative to your total upload amount.  Having uploaded more (more bits uploaded) translates to faster downloading.  

This is done to *encourage* sharing across the board.

---

### Post by madsmeg on 2008-09-19
Thrion; I always find my speed increases if i lower my upload and matters not how much i have uploaded.

I agree with k33bz Deluge is a great tool.

---

### Post by fballem on 2008-09-19
Thanks, I'll give deluge a try. Are there any configuration issues that might make it a bit fairer.

Thanks,

---

### Post by Paqman on 2008-09-19
It also varies hugely from torrent to torrent.

Your download speed will be largely dependent on the number of people seeding the torrent (a seed is someone who has 100% of the file being shared) A typical download speed would be 25KB/s, but on a torrent with a lot of seeds (such as a new version of Ubuntu!) you might see 1000KB/s.

Having a good upload speed is a good thing. It helps other people out, and contributes to the health of the torrent. If you find it's slowing your system down too much, you can always cap the upload speed.

---

### Post by El Conquistador on 2008-09-19
yes i also agree with Deluge ive tried a couple clients and i like this one by far.

now as far as the upload and download fairness. as a rule of thumb, the more you upload the slower you download. however this does not mean that you should not upload as this would be unfair to the community. what i mean is that try different upload cap settings (limit the upload speed) until you find one that doesnt affect your download too much (or at all) then what i usually do is seed at full speed once im done downloading. so try different setting. but just remember 

if you max out your lines upload speed it WILL cripple your download speed.

---

### Post by sleepingdragon on 2008-09-19
I expect you're going to receive some confusing info on this, but here's mine.

For example, imagine you've only downloaded 5% of the complete file at an average of 50Kb/s. Now, that 5% might be needed by 20 people. They all upload  from you at 5Kb/s. You might be only downloading at 50Kb/s, but 20x5Kb/s is 100Kb/s, which would explain why your upload is higher than your download. It's nothing to do with your download speed, but rather how fast you can supply to everyone else.

Restricting your upload limits can affect your download limits, but as a simple rule-of-thumb, one tenth of your download capacity should be met by your upload capacity. If your ISP can give you 500Kb/s, then 50Kb/s on your upload settings should be perfectly adequate.

---

### Post by fballem on 2008-09-19
Thanks to you all. On Transmission, I'm seeing a note that I am downloading from 6 of 22 connected peers.

Can someone explain what that means, and what is the impact to me?

Thanks,

---

### Post by linkmaster03 on 2008-09-19
Try Ktorrent (GUI) or rtorrent (needs configuration, terminal based).

---

### Post by fballem on 2008-09-19
Interesting experience this Bit Torrent - I've been at it since Tuesday, I'm almost done, but the time remaining ranges anywhere from 6 days to a little less than 3 hours. I am hoping that the 3 hours is the more accurate.

---

### Post by Paqman on 2008-09-19
> **fballem said:**
> Thanks to you all. On Transmission, I'm seeing a note that I am downloading from 6 of 22 connected peers.

Can someone explain what that means, and what is the impact to me?

Torrents are a collaborative way of getting a file. The torrent software identifies everybody else who wants that share or download the file. These people are your peers. Some may have the whole file and are purely sharing it with others (seeds), while some are still downloading it (leechers)

The cool thing about torrents is that you can download from someone who doesn't have the whole file(s). If they have a piece of the torrent that you don't, your client will connect to them and start downloading that chunk. Vice verse, you will start uploading to others before you've got the whole torrent. That's what makes torrents work, people are forced to share, and can't just download the file and dash.

So saying you're d/ling from "6 of 22 peers" means that there are 22 of you in total in the torrent's swarm. Personally, at that moment, you are d/ling from 6 of those. It's worth noting that ADSL broadband lines can't upload anywhere near as fast as they can d/l, so you're limited by your peers upload speeds. That's why a) throttling your upload speed top much is unfriendly and b) connecting to lots of different peers is good.

---

### Post by fballem on 2008-09-20
Thanks to all of you - I know a little bit more than I did before.

I will try Deluge for my next torrent (I have already installed it), I will limit the upload speed to 50KBs and see if that works, and the Torrent that I was downloading is now complete.

Many thanks again!

---

