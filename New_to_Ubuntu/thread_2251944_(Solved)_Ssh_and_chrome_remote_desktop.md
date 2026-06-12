---
title: "(Solved) Ssh and chrome remote desktop"
date: 2014-11-07
forum: New to Ubuntu
---

### Post by dawn5 on 2014-11-07
Good evening, (A long read, apologies)

<When initially writing this, it was only mean to be the ssh and remote desktop enquiries, but as its took an hour to type in total, errors started flooding back to me>

Im new to the community, theres no denying that, and although i love to figure things out for myself, im in a bit of a bind here.. 
You see, whilst still only breaking the surface of what seems to be a neverending yet infinately intreguing journey, i do know my way around multiple areas due to previous experience before recently installing Ubuntu14.04, i didnt know which section to place this question in, and when it comes to ssh, im somewhat in the dark
So last week i had a bit of time on my hands, so i decided to wipe everything and start again, having only uses linux in virtual machines, it was time to set up dual boot
everything went perfectly, or so i thought, i had chrome remote desktop working on my Nexus 7 2013 WIFI, and openssh-server with JuiceSSH and SSHTunnel, long story short, i tried to run Kubuntu on dual monitors with an unfortunate Nvidea 570 Graphics card, it couldnt handle it so i decided to wipe everything again,
This time, when i redid the system, for some reason my ssd had 3gb worth of files specifically the boot manager, so that was taking priority over grub, microsoft eh...  
So i had to disable the partition (regretebly as it i could no longer boot my system, had to plug the optical drive back in reinstall windows 7 from disk, but i removed all hdd minus the ssd, as the windows repair didnt work the first time, the partition with boot mgr was peristent. 
so i did some formatting when ubuntu was being loaded, merged relevant partitions, and created majestically sized logical drives. 

Now its all working great, and im very happy with the overall setup, cant believe i didnt get around to it sooner, but it comes to getting ssh and remote desktop back and i just cant. ive been stuck on this for a week now,  give or take around work etcetera
Something is persisting from the old working Win/Ubu v1.0 and i cant figure out whats going wrong. Ive tried purge, auto remove, clean and reinstalling the openssh-server aswell as reinstalling juicessh and sshtunnel on the nexus,,

<also new to android, dont get me wrong, i enjoyed my iphone, but androids playing a whole different ballgame>

For the android applications, juice is asking for a password, which ive only really got a couple i would use for this sort of thing, and theyre all being rejected. Its never asked for a pass before, including on v1.0, and ive checked the /sshd.config, even unhashed the require password authentication no. Ive tried a multitude of passwords which it shouldnt be but may have, all resulting the same. Ive had a look at the verbose during  i think either trying to internally connect to the ssh server, or whilst doing something with the keyfile copy, youll have to forgive me i cant quite remember. But juice was throwing out a RSA keyfile error, 

As far as the Windows side goes, chrome remote desktop, despite being on the same network naturally, now the only thing different is my local network ip, from xxx.xxx..x.13 to xxx.xxx.x.16 but the tablet is getting not even a whiff that theres a host listening, and its frustrating, these apps are perfect, especially when i start playing around with some of the ideas in my head with the raspberry pi. 

Any help what so ever would be greatly appreciated, just point me in the direction and im more than happy to go off and research, im just a person whos a mix between frustrated and desperate right now. 

One last thing incase someone stumbles upon this who has vast knowledge of Ubuntu, Ive set up a media server using mediatomb, all my media is on my windows machine, as its ntfs, ubuntu can access it which is fantastic, it connects to my ps3 i can play some movies, but not others, these have sound but no picture,
everything is the same bar the codex on the videos is (i think) 1.9 (or 2.2) and 2.4 on the other, im clueless when it comes to playstation formats, frankly ive had it for what seems like ever and never touched it.
Also any suggestions for an improved media server would be fab, to be honest with you i didnt look too much into any other packages, i told myself it would be my first task after the 3 days of loading screens and telling myself that would be the last time id have to partition ever again

one last thing, im sorry, whilst im here i may as well ask, ive been doing a hell of a lot of debugging over the last few days, but this last one has popped into mind thats persisted through infinite research. 
i have a steel series siberia v2 headset, before the revamp, i would run it in my sound/microphone jacks, but now, theyre not recognised with the headset, and when plugging in via usb, the drivers are only displaying as a usb pnp device, giving skype/teamspeak windows side, and then the sound side of ubuntu a lot of compatibility issues.  Also internet is very unstable ubuntu side, but then again, my ISP have been shocking lately anyway

I realise im asking a lot of perhaps basic questions, but these are just ones i cannot manage on my own. I would be extremely grateful for even one section of this answered. Im diving head first into all this, and dont get me wrong im loving every second, but a lot of this is still all new to me, ive had the ideas for a long time, but finally putting them into play has proven trickier than i imagined, until just over a week ago ive never taken notes about debugging, now im feeling like im going to have to start planting some new trees. 

Anyway, i ramble a lot, but ive tried to give you all the information i can remember whilst typing this, please, dont hesitate to ask for more information, it would be great to hear from some of you. Like i said folks im more than happy to read any useful documents you can send my way, and thank you in advanced

Take care
Dawn

<Edit : I should mention that the ubuntu side of things does have its home directory encrypted, which could be the ssh rsa local keyfile issue, but im unsure>
<Update> Found that could connect to ssh server via terminal on Nethunter tablet, looked into the identity - found it wasnt configured correctly in Juicessh, so that problems out of the way now>
<Update>

Solved, take care
Dawn

---

### Post by HermanAB on 2014-11-08
I cannot tell what is connected to what, or which server is running where...

---

### Post by dawn5 on 2014-11-08
Hiya mate,

The windows 7 side is pretty much all fine bar the headset and chrome remote desktop, the SSH and media-tomb servers are all within ubuntu with an encrypted home directory, 

For Windows : 60gb ssd (OS) + 350gb partition + 1tb partition,
For Ubuntu : 100gb "/" 1tb "/home" and 50gb swap space
The media server is connected to the ps3 through wireless connection

Unsure if this clarifies what you're asking fella, but many thanks for the response!

---

