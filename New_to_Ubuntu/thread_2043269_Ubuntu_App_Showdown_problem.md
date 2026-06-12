---
title: "Ubuntu App Showdown problem"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2012-08-16
Hope this is the right place to post this.

I have been trying a few of the Apps in the Ubuntu App Showdown. One of them FOGGER is great, letting you run websites, services and utilities in a dedicated, WebKit-based window on the desktop.

I created one for Facebook, which ran alot faster.

Carrying on through the Apps in the competition, i actually found an entry called Facebook.  I thought i would compare them. So through terminal i installed it.

BUT i already have an Fogger App called Facebook. So had no idea what would happen.

I managed to delete the Fogger Facebook App in the end (when i found the option).

Then i went back to Terminal to instal this new complete Facebook App:
sudo add-apt-repository ppa:folke-schwinning/personal
sudo apt-get update
sudo apt-get install facebook  

At the instal stage, it said there was no need to as i already had the latest one.

When i search in Dash for Facebook, all it picks up is the old Icon for the Fogger Facebook App (which isnt the one i need, and does nothing anyway).

Hope someone can understand what is happening here. Any help would be great :p

---

### Post by albandy on 2012-08-16
The packages of this ppa are wrong:

[https://launchpad.net/~folke-schwinning/+archive/personal/+packages](https://launchpad.net/~folke-schwinning/+archive/personal/+packages)

see build status

---

### Post by MadMonkey1966 on 2012-08-16
> **albandy said:**
> The packages of this ppa are wrong:

[https://launchpad.net/~folke-schwinning/+archive/personal/+packages]("https://launchpad.net/%7Efolke-schwinning/+archive/personal/+packages")

see build status

Many Thanks for your quick reply :)

I am lost when we talk about things like that, i am very much a learner when it comes to Terminal etc... (but trying my best).

I see following your link that that build from the 20th July Failed. 

Does this mean it can not be installed and tested ? 

I wonder why its in the list of finalists ?

Not to worry, i will try out a few others from the final, just the screenshot of this Facebook one looked very good.

Many Thanks again :P

---

