---
title: "Update to 11.10 beta 2"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by gdonwallace on 2011-09-26
I tried this weekend to update to the latest beta of 11.10, and was not able to.  ](*,)

I have applied all updates through Muon, and still not getting prompted to update to the beta.  Not sure if Muon would prompt me or not.  

Tried a apt-get dist-upgrade; and nothing happened.  I can't do the update-manager -d, as Kubuntu does not use update-manager.  

Any ideas on how to get beta 2 installed, without having to to a complete re-install?

---

### Post by coffeecat on 2011-09-26
*Thread moved to **Ubuntu +1 (Oneiric Ocelot)**.*

---

### Post by Seq on 2011-09-26
> **gdonwallace said:**
> I tried this weekend to update to the latest beta of 11.10, and was not able to.  ](*,)

I have applied all updates through Muon, and still not getting prompted to update to the beta.  Not sure if Muon would prompt me or not.  

Tried a apt-get dist-upgrade; and nothing happened.  I can't do the update-manager -d, as Kubuntu does not use update-manager.  

Any ideas on how to get beta 2 installed, without having to to a complete re-install?

Were you previously on beta 1? If so, and you're up to date, you're already running beta 2.

---

### Post by gdonwallace on 2011-09-26
Yes I was running beta 1.

I had read that Firefox and Thunderbird where supposed to be on the betas for version 7.  However; when I check them, they are both on version 6.x.  

Was kubuntu supposed to update these two programs or are they waiting until the final release.  If they are ready, then I can assume that I am currently running beta 2.

---

### Post by Seq on 2011-09-26
> **gdonwallace said:**
> Yes I was running beta 1.

I had read that Firefox and Thunderbird where supposed to be on the betas for version 7.  However; when I check them, they are both on version 6.x.  

Was kubuntu supposed to update these two programs or are they waiting until the final release.  If they are ready, then I can assume that I am currently running beta 2.

Then something is wrong and you're not being kept up to date. The Oneiric repositories have had Firefox 7 betas for weeks, and the 7 release repository hit the repos over the weekend.

It could be possible you are using an out of date mirror. You would have to post the contents of your '/etc/apt/sources.list'

---

### Post by gdonwallace on 2011-09-27
I will get it posted later tonight.  I am at work and did not bring my laptop with me.

---

### Post by gdonwallace on 2011-09-28
Well it took a while because of work, but here is my sources_list

---

### Post by Seq on 2011-09-28
> **gdonwallace said:**
> Well it took a while because of work, but here is my sources_list

Looks fine. You're probably already up to date.

---

### Post by gdonwallace on 2011-09-29
After I uploaded my sources.list, I again ran the update && upgrade and it grabbed well over 200 upgrades.  When it was all said and done, I was up to date on Firefox, Thunderbird, and the most recent Kernel.

Not sure if it was my machine or the repos; but something seemed to be a little off.  Looks good now though.

Thanks for the help

---

