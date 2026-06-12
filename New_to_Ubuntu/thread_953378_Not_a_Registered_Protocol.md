---
title: "Not a Registered Protocol"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by kjbox on 2008-10-20
I am in the process of migrating from Windows to Ubuntu and have come up against a problem.

I play a lot of online backgammon usually at a site called World Gaming Center ([www.wgcenter.com](www.wgcenter.com)). To use the site requires a download of a .exe file (client.exe). I intend to run this either through WINE or using a virtual PC.

I have successfully installed WINE but when I go to wgcenter I can login using my usual username and password but as soon as I try to enter one of the gaming rooms (which should trigger the download) or try to go to their download page, I get the following alert:

WGC is not a Registered Protocol.

I have tried to search for a solution but have only found: 'Registering Applications for MIME Types'. This did not appear to apply in my case.

Any help in how to register WGC would be much appreciated.

Thanks.

---

### Post by eternalnewbee on 2008-10-20
> **kjbox said:**
> I am in the process of migrating from Windows to Ubuntu and have come up against a problem.

I play a lot of online backgammon usually at a site called World Gaming Center ([www.wgcenter.com](www.wgcenter.com)). To use the site requires a download of a .exe file (client.exe). I intend to run this either through WINE or using a virtual PC.

I have successfully installed WINE but when I go to wgcenter I can login using my usual username and password but as soon as I try to enter one of the gaming rooms (which should trigger the download) or try to go to their download page, I get the following alert:

WGC is not a Registered Protocol.

I have tried to search for a solution but have only found: 'Registering Applications for MIME Types'. This did not appear to apply in my case.

Any help in how to register WGC would be much appreciated.

Thanks.

If I can help you, I can only do that by following your steps. So, I'm at mentioned site now. Guide me.

---

### Post by kjbox on 2008-10-20
Hi,

Thanks for helping.

I think you will have to register there to get any further so you can login.

Once logged in click on the 'Backgammon' link.

Then either try to enter a room (Doubling Cube would be a good one) or click the 'Downloads' link.

You should then get the same message (WGC is not a Registered Protocol) that I get.

Sorry for late reply, I had to go out, hope you are still online.

---

### Post by eternalnewbee on 2008-10-20
> **kjbox said:**
> Hi,

Thanks for helping.

I think you will have to register there to get any further so you can login.

Once logged in click on the 'Backgammon' link.

Then either try to enter a room (Doubling Cube would be a good one) or click the 'Downloads' link.

You should then get the same message (WGC is not a Registered Protocol) that I get.

Sorry for late reply, I had to go out, hope you are still online.

I am. Hold on..

---

### Post by Rhubarb on 2008-10-20
It may not be much of a help, but you can download backgammon from the Ubuntu repositories:
```
sudo aptitude install gnubg
```
Then you will need to make a bearoff database for it (don't know what it is, it just prompts me to make one when starting backgammon for the first time):
```
makebearoff -t 6x6 -f gnubg_ts0.bd
```
Then to run the game, press Alt + F2, then type in:
```
gnubg
```

It's quite a polished game, you could try this if wine doesn't solve your problem.

---

### Post by kjbox on 2008-10-20
Hi,

Thanks for that. However, GNU Backgammon is indeed a backgammon programme but is used to analyse matches. That is to say, after playing a match you can save the log for that match (the log is a record of all your and your opponents dice rolls and subsequent moves)and then import it into gnubg for analysis. gnubg will check each move made against the optimum move for that dice roll.

I have used it for many years. It is an extremely powerful programme. Indeed it is far superior to other programmes that cost a fortune!!! You can also play against the programme for experience and tuition but using it does not overcome my problem of getting to play live online at wgcenter.

Thanks again for your reply.

---

### Post by eternalnewbee on 2008-10-20
> **kjbox said:**
> Hi,

Thanks for helping.

I think you will have to register there to get any further so you can login.

Once logged in click on the 'Backgammon' link.

Then either try to enter a room (Doubling Cube would be a good one) or click the 'Downloads' link.

You should then get the same message (WGC is not a Registered Protocol) that I get.

Sorry for late reply, I had to go out, hope you are still online.

One question:
Have you installed "wine"?

---

### Post by kjbox on 2008-10-20
Yes.

I did that first of all, hoping that I could then just download wgc's client.exe and run it using wine.

---

### Post by kjbox on 2008-10-20
I should add that a couple of years ago I had a pc with Linspire installed and did manage to use the wgcenter site using codeweaver's crossover, allbeit with a few minor features not working.

So I do know that it can be run on Linux, I did not get the Protocol Registration problem with Linspire as far as I can remember.

---

### Post by eternalnewbee on 2008-10-20
> **kjbox said:**
> Yes.

I did that first of all, hoping that I could then just download wgc's client.exe and run it using wine.

file:///home/bird/Desktop/Screenshot.png
Comments?

---

### Post by kjbox on 2008-10-20
errr, sorry, comments on what?

---

### Post by kjbox on 2008-10-20
I assume that the screenshot was a view of how far you got, but it was not as an attachment that I can open.

Did you manage to download and install client.exe?

---

### Post by eternalnewbee on 2008-10-20
I did...

---

### Post by kjbox on 2008-10-20
May I be so bold as to ask........How?? :))

---

### Post by eternalnewbee on 2008-10-21
Sorry for my late reply, but I just downloaded the executable, double clicked it and it opened with wine. That's it.

---

### Post by Rhubarb on 2008-10-21
Are you running the latest version of wine there?
You can grab it from: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

