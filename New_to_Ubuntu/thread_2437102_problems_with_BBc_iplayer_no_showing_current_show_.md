---
title: "problems with BBc iplayer no showing current show ( do I need any further software)"
date: 2020-02-18
forum: New to Ubuntu
---

### Post by bazwilson on 2020-02-18
Hi just attempted to change from Windows and installed Ok, using firefox i opened BBC iplayer and logged in Ok but was unable to view the current program playing, 
Do I need to install any further software other than what is on the installation 

thanks
Barry wilson

---

### Post by ajgreeny on 2020-02-18
Let's check first; are you using a UK IP address?
BBC iPlayer works in the UK only.

If you are in the UK try the following links to see what happens.
[https://www.bbc.co.uk/iplayer/live/bbctwo](https://www.bbc.co.uk/iplayer/live/bbctwo)
[https://www.bbc.co.uk/iplayer/live/bbcone](https://www.bbc.co.uk/iplayer/live/bbcone)

Both are working fine for me using Xubuntu 18.04 and either Firefox or Chromium work fine.

However, you may find it is better still to use the following links listed at [https://gist.githubusercontent.com/random-robbie/e56919b5603ecc87af885391e7331657/raw/65661a4e6fa8c706cc8fe1cf7c553927e5cf62a7/BBC.m3u](https://gist.githubusercontent.com/random-robbie/e56919b5603ecc87af885391e7331657/raw/65661a4e6fa8c706cc8fe1cf7c553927e5cf62a7/BBC.m3u)
Ignore the lines starting with [COLOR="#FF0000"]#EXTINF:[/COLOR] and copy the http links which play in vlc, mpv or player of your choice, generally using fewer machine resources if compared with the BBC iPlayer.

---

