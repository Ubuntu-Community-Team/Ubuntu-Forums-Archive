---
title: "Music streaming services does not work in Chromium"
date: 2017-04-25
forum: New to Ubuntu
---

### Post by exigoss on 2017-04-25
I have a newbie question. I'm just starting my adventure with Ubuntu, but I encountered a small but annoying problem. While using Chromium Spotify Web Player just does not work. The only thing I receive is error on the top of the web page on pink background saying: "Unfortunately there was an error while playing song, load again" or something like this (I'm not using English version, so I'm not sure how exactly translate this error). Then I even can't click one Pause/Play button becouse nothing happens. Also one of my favourite online radio does not work. It is loading forever and buttons also does not work. Do I have to install any specific plugin to make it work? I would like to mention that in Firefox everything works perfectly fine but I want to stick with Chromium becouse of sync with my second PC. I know there is Spotify app for Linux but working radio is still important for me. Thanks in advance!

---

### Post by howefield on 2017-04-25
Seems to be know problem, not sure if it is Spotify or Chromium but I'd suspect a change in Chromium with regards flash.

There will be a new version of Chromium coming through the repositories shortly, possibly this week if you can hang off and try it.

---

### Post by exigoss on 2017-04-25
Great! I'll wait and check if the bug is fixed. Thanks for advice.

---

### Post by howefield on 2017-04-26
> **exigoss said:**
> Great! I'll wait and check if the bug is fixed. Thanks for advice.

Seems not, still the same issue.

Might be worth reporting at the Spotify community forums although there have been [reports]("https://community.spotify.com/t5/forums/v3_1/forumtopicpage/board-id/001/thread-id/184644/page/1") for a few weeks with no apparent workaround other than use another browser (not chromium based).

---

### Post by KenUBF on 2017-04-27
If you'd like I found an official Spotify app for Ubuntu: [https://www.spotify.com/int/download/linux/](https://www.spotify.com/int/download/linux/)  Though according to OMGUbuntu support stopped about a year ago... [http://www.omgubuntu.co.uk/2016/03/spotify-linux-no-development](http://www.omgubuntu.co.uk/2016/03/spotify-linux-no-development)  But there may still be unofficial apps you can use, rather than having to rely on the browser.

---

### Post by ra7411 on 2017-04-27
>[COLOR=#000000]While using Chromium Spotify Web Player just does not work. <

I tried using Chromium on Hoopla's site for audio and got a message re. needing to upgrade my browser. I have Lubuntu and Ub 14.04 as dual boots on that machine, so I just  got 14.04 up and used Chrome w/ no probs. Hope that helps or clarifies.


[/COLOR]

---

### Post by howefield on 2017-04-28
> **ra7411 said:**
> I have Lubuntu and Ub 14.04 as dual boots on that machine, so I just  got 14.04 up and used Chrome w/ no probs. Hope that helps or clarifies.

Chrome does work fine with Spotify web player but Chromium doesn't.

---

### Post by HermanAB on 2017-04-28
YMMV...  many things are simply not tested with Linux based clients.

You should try internet-radio.com and streamtuner for tens of thousands of online radio stations that work.

$ sudo apt install streamtuner

Streamtuner also includes streamripper.  I use streamripper once or twice a year to download ten or twenty radio stations for a week, to give me stuff to listen to in my car.  Over here is only one radio station that is audible - Abu Dhabi Classic - it gets a wee little bit trying after a while.  So I'm an expert on internet streaming radio...

---

### Post by exigoss on 2017-04-28
Thanks all for help and advices. Although Chromium seems not to work with these sites I still stck to it. I managed to replace those sites with apps. For Spotify I use official app and for internet radio I found app called GRadio ([https://github.com/haecker-felix/gradio](https://github.com/haecker-felix/gradio)). It covers all my needs so I think that my problem is solved. Thanks again for help :)

---

