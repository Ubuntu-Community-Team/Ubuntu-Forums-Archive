---
title: "What is fastest/best way to use ubuntu vps via rdp/vnc with win/linux os?"
date: 2016-02-27
forum: New to Ubuntu
---

### Post by raman07 on 2016-02-27
Hi, I have set up my ubuntu vps and installed lubuntu-core desktop in it. Now i want to access this vps via my home machine. So i installed tightvnc server in ubuntu vps and got connected with it but the connection is pathetically slow. My latency to the VPS is less than 195ms and with same latency if i use any window rdp machine then the connection is quit smooth to use but linux are pathetic. I also tried one rdp server in my ubuntu vps and connection was still slow.

With a quick google search i found that its the problem with many people and look like problem rely in linux vnc and rdp server. They are not sending frames with good speed or not optimized to work smoothly.

So please tell me what is the best way to use my linux vps. How i can access my linux vps smoothly. Currently its so slow that i can count frames. Window vps are quite fast compare to linux vps while making rdp connection with them.

Please suggest me what to do.

---

### Post by raman07 on 2016-02-27
No one replied :(

Fine

I found x2go server preety good.

I followed this guide and its work fine : [https://vpsboard.com/topic/4241-running-a-lightweight-gui-on-your-vps-via-x2go/](https://vpsboard.com/topic/4241-running-a-lightweight-gui-on-your-vps-via-x2go/)

I also found a guide on wiki link but that did not work for me but above guide worked for me.

If anyone know any other better way let me know.

---

### Post by yetimon_64 on 2016-02-27
Have a look at Qlll's response [[COLOR=#0000ff]--here--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2314629&p=13446061#post13446061"), the suggestion in that thread is for "NoMachine NX". It would probably be best if you read the whole thread and see if it suits your situation. Cheers, yeti.

---

### Post by raman07 on 2016-02-27
> **yetimon_64 said:**
> Have a look at Qlll's response [[COLOR=#0000ff]--here--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2314629&p=13446061#post13446061"), the suggestion in that thread is for "NoMachine NX". It would probably be best if you read the whole thread and see if it suits your situation. Cheers, yeti.
I tired installing NoMachine before i install x2go and i failed to make it work. Do not know what i was doing wrong then i read some comments and everyone stating that NoMachine do not support ubuntu 14+ versions so i gave up and the thread you suggested. There OP using 14.04 so might be NoMachine support 14.04 

Do you have any guide of how to install it on 14.04?

---

### Post by yetimon_64 on 2016-02-27
> **raman07 said:**
> ...Do you have any guide of how to install it on 14.04?

Sorry, no idea about that, I just remembered seeing that other thread yesterday on the same subject. I'll keep my eyes open for anything regarding that though and will post back if I do come across any info.

---

### Post by oldos2er on 2016-02-27
> **raman07 said:**
> No one replied :(

Please be patient. We have members from all over the world, and it takes time for your post to be seen by everyone (a minimum of 24 hours). The person who can answer your question possibly hasn't seen it yet.

---

### Post by raman07 on 2016-02-27
@yetimon_64 I successfully installed NoMachine in 14.04 but i think i will stick with x2go. I find x2go better than NoMachine.

@oldos2er hmm okay

---

### Post by sandyd on 2016-02-27
Despite not being linux native, TeamViewer may be an option as well. Just tested it out to see if the lag was as bad as VNC, which it doesn't seem to be. Scrolling in FF actually does not stutter, and displaying the main menu only lags a bit.

Tests done on a standard LUbuntu installation.

---

### Post by X-RED_Tech on 2016-02-28
I too use TeamViewer and it's fine but apparently it comes with Wine?!? Is it a Windows software wrapped with an emulator or what?

---

### Post by HermanAB on 2016-02-28
The best method is to use SSH.

Things like VNC and Nomachine all suffer from this basic rookie mistake:
Your local machine already has a perfectly fine desktop system.  So it is totally redundant and a complete waste of time to send the whole gawddamm remote desktop system over the wire and overwrite your local desktop, when you only need to send the remote *application* that you want to use over the wire and run it on your local desktop.

---

