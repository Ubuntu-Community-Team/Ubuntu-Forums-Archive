---
title: "Linux installation on Acer Aspire One D270"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by ranveer5289 on 2012-05-31
I was planning to buy **Acer Aspire One D270** within a few days and as everybody installs linux on their netbook I was also planning to do that.

Now, my question is how is Acer's hardware compatibility with linux and specifically in respect to the new Acer Aspire One D270.

Has anybody tried installing linux on these new netbooks. It will be a great help if a D270 user can share his/her experience with linux usage.

I read on some forums that there is some linux driver issue with **Intel GMA 3600** and that people are not able to adjust their brightness and screen resolution. So, as I am a linux noob is this a major issue or not.

Specs:
RAM : 2Gb DDR3 Processor: Intel N2600(Cedar Trail) Graphics: Intel GMA 3600 HardDisk: 320Gb 5400 rpm

---

### Post by gene simmons on 2012-05-31
i recently bought one of the acer d270 netbooks,they were on sale and with hdmi i fugured a good deal,i have been runninng linux for 3 years now on all my stuff andd for the most part it works great,{not so good on my alienware mx11 dual graphic cardd}and i consider myself a novice within linux,i found that linux doesnt play well with the d270 at all,i tried many distros that wouldnt boot and gave errors or wouldnt recognize the hardware,i finally got ubuntu 12 to load and run but as u already know the graphics card isnt suported yet,also hdmi woundnt work for me,on some tvs as i coulndt change the resolutions,theres a gma 500 thread on here that gave some great tips and pointers i folowed thier instructions and now i have the brightness working and the hdmi works well but the rest is still glitchy,theres also meego distro that does work well with the d270 but the wireless wouldnt work,theres a fix for it but its complicated and i didnt like the meego look,im pretty happy with the d270 now with the fixes i have on it,battery lasts about the same as windows,i can get 7hours depending on what im doing,i did upgrade the ram to 2 gig and i got rid of wi 7 starter and installed profesional,much better,i mainly wanted it for hdmi to watch movies,i have lots of movies stored on it for the kids to watch camping as battery life iss great and at home on big tv,hope this helps

---

### Post by ranrag on 2012-05-31
Gene I was also thinking of purchasing D270, so can you point me out to the correct **GMA500 thread** or is it **GMA600 thread** you are talking about that solved your problem.

So, if I understand you correctly it seems that you are able to get everything(except HDMI) working on your ubuntu 12.04 I mean you solved the resolution problem. So, would you suggest me to go on with the D270 purchase then.?

And what do you exactly mean by the statement **but the rest is still glitchy.**

---

### Post by gene simmons on 2012-06-01
hey,yes it is the gma 3600 thread,the fix was to install the gma 500 drivers,i got them mixed up haha,the rest being glitchy,well it seems kinda slugish,sorta slow to open windows and things,i dont recall it being like thaat before i did the fixes,the hdmi does work with the driver and the brightness too,ive had 3 acer netbooks and they all run linux fine,this one works good but it took alot of work to get it there,i read magiea 2 is suposed to work well with the gma 3600,havent tried it yet,its a decent netbook for the price and like i said it will run linux well just needs a few tweaks haha

---

### Post by idoitprone on 2012-06-01
there is no stable linux driver for intel gma 3600 because it is not a intel graphic chip
[http://en.wikipedia.org/wiki/Intel_GMA#GMA_3600](http://en.wikipedia.org/wiki/Intel_GMA#GMA_3600)

its power VR and they never release any decent linux driver

I say do not install linux of any distro because there will be no graphic support and it will be an issue as you will be stuck at 800x600 resolution

---

### Post by ranrag on 2012-06-01
So, it seems that by default I will be stuck with 800X600 resolution until and unless I follow the instructions given on the **GMA3600 thread** and than also it is not a guarantee that I will achieve 1024X600 resolution.

One more problem is that all the latest netbooks having Intel Cedar Trail are shipped with Intel GMA 3600, even Asus Eee PC 1015cx has this chipset. So, what should one do wait to buy a new netbook or install Meego on it.

---

### Post by gene simmons on 2012-06-01
out of the box with ubuntu 12 i got 1024x600 which is standard,it looks fine,things worked ok but no brightess,there is a command to change brightness manuall via terminal and i was using that,it worked fine,the fixes are easy if you folow the thread,im pretty happy with it now,hdmi and the brightmess helped alot for me to like it more,get one and try a few distros,maybe you will like meego,it worked great but i didnt like it much,looked like it was meant for kids,also megiea is supposed to have support for the gma 3600.check it out,

---

### Post by ranrag on 2012-06-01
Gene, thanks for the reply now I feel relieved. 

Yes I checked that mageia 2 has claimed to support Intel GMA 3600 and also some other user have installed fedora 17 with the latest linux kernel and got the perfect resolution.

I looked at [**ubuntu kernel 3.3 changelog**]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/CHANGES") and found out that support for GMA500 has already been added and it also provide experimental support for GMA600.

So, it seems I am going to buy this machine after all and will get back to you if I face any problem. Hope you don't mind. :)

---

### Post by gene simmons on 2012-06-01
no problem,i think you will be happy with the unit,the battery life is geat in windows or ubuntu,i turn the brightness down and the battery lasts longer,i love having over 100 avi movies on it and i can use hdmi to connect it to my tv,its also small enough to take anywhere,i may try fedora,i have always liked fedora,i have a alienware laptop with a nvidia graphics card and let me tell you its a chore to get linux to work well on that one,it works but battery life isnt near as good as in windows,i alsways have a dual boot system just in case,i use linux 90%of the time but for some things wondows is needed,i have a wireless printer that just wont work on ubuntu,always a chalenge haha,hope all this helps,

---

### Post by jagdefalke on 2012-06-02
I got the D270 a few weeks ago and almost immediately split it in half and installed 10.04 (because that's what's on my desktop) and haven't had any problems until just a few days ago when win7 crashed, but that's a new thread...  :P

---

### Post by kuni on 2012-06-10
Hi,

here is my workaroung for the brightness issue. Not exactly a clean or safest one but it works.. if someone finds a better way I would happily learn how.

1. SUID the executable /usr/bin/setpci:

```
sudo chmod 4755 /usr/bin/setpci
```

2. Create a ~/.backlight directory and copy the contents of the included archive into it.

3. Copy the contents of profile_added_lines.txt to the end of your ~/.profile (you can then delete the txt file). 

In the file current_value.txt there is a hex value for the actual brightness setting which range from 00 to ff. The scripts up.sh and down.sh actually increase or decrease the currently set value and update the brightness level via the setpci command. This way can be stored any desired value of brightness and it is even held after reboot.

4. add two custom shortcuts in your keyboard setting with the following commands:

```
bash -c "$HOME/.backlight/up.sh"
```
```
bash -c "$HOME/.backlight/down.sh"
```

5. Associate keyboard shortcuts with the newly created ones. Warning: the standard FN+[LEFT] and FN+[RIGHT] do not work, I use CTRL+SHIFT+[LEFT] and CTRL+SHIFT+[RIGHT] instead, but whatever.. 

Hope this helps to someone.

---

### Post by m4y0r on 2012-07-26
danke kuni! hat mir sehr geholfen.
allerding musste ich den code modifizieren. ging bei mir nicht so

```
bash "/home/benutzername/.backlight/up.sh"
```

```
bash "/home/benutzername/.backlight/down.sh"
```

---

### Post by nemoskull on 2012-08-04
i got ubunt 12.04 running on acer d270. slower than my old D250 on every operating system (ubuntu 10.04, windows xp) have not tried the hdmi port. sd card works fine under 12.04 but random permenet cut out under 10.04. most things worked out of the box. (i think. cant remember)

---

### Post by RTPDr on 2012-10-21
I am a new to linux. I removed the Linpus linux that came along with  ACER AOD270 Atom N2600, Intel GMA3600. It runs on Cedar Trail platform (I am not a  techee) and intel has incorporated the drivers with their own linux  distro Meego 1.2. I ve tried Ubuntu 12.04 and after installing couldn't  adjust the brightness. But after updating it showed to install  additional drivers and installed the Cedarview drivers. Those crashed  after some time, without much problems and Now I am very happy with  Linuxmint13. Searched the synaptic for cedar and installed 4 softwares  for cedartrial and cedarview and I played a movie 1920x800 nicely. For  adjusting brighness , the Fn+ arrow keys worked well. Additional  brighness reduction was achieved with RedshiftGUI

---

### Post by forumsuser234784 on 2013-01-05
Just as a short info. The following link solved the brightness problem for me nicely (Aspire One D270 with Kubuntu 12.10):

[http://www.refreshit.info/2012/08/solved-brightness-increase-and-decrease.html](http://www.refreshit.info/2012/08/solved-brightness-increase-and-decrease.html)

PS: The registration process of this forum sucks...

---

### Post by fantab on 2013-01-05
> 
**I was planning to buy [B]Acer Aspire One D270** within a few days and as everybody installs linux on their netbook I was also planning to do that.

Now, my question is how is Acer's hardware compatibility with linux and specifically in respect to the new Acer Aspire One D270.[/B][B]


GMA3600[/B] and **PowerVR** sucks and not just with Linux. I have ASUS 1015CX. Getting the 'perfect' resolution is not an issue with Linux default open source drivers (mesa, fbdev etc). The problem is when you need to or want to use **Hardware Acceleration**. 

Playing HD video is out of the question. Well to tell you the truth, even in Windows 7, for which the drivers are available, is not at all a great experience to watch HD video, to say the least. 

So if you are not keen to play HD videos on this machine (Acer/Asus), then I'd say it a nifty little machine. 

Oh, by the way, Acer D270 and Asus 1015CX have exact same specifications except that Asus has a "non-glare" LED display.

---

### Post by gerecter on 2013-04-01
In fact, there were some Intel GMA 3600 problems. What I learned from my experience is Ubuntu 12.04 is the best option at the moment. Anything newer than 12.04 was not good enough. And upgrading all the modules and installing recommended additional video driver seem to be bad choices. I just upgraded only things not related to hardware. But, anyway, I still can not use 3D acceleration, and I don't think external video output is working well either.

There are brightness problem and suspend/sleep/wake problem, too. The brightness was too weak and I couldn't control with my keyboard. I had to type a command(sudo setpci -s 00:02.0 F4.B=40) to adjust the brightness. I put this command in a script for automation. And the waking up the system from a sleep did not work at first. I had to type a command(sudo pm-suspend --quirk-dpms-on) to make it sleep properly. I made a file to add a code to do this whenever I close my computer.

---

