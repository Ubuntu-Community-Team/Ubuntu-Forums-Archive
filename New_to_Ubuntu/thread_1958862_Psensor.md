---
title: "Psensor"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by MonkWy on 2012-04-15
I have a question about an App called Psensor. what does it do and is it okay/safe to use with 12.04 LTS? I have read that Canonical doesn't support it, that it is supported by the community. Is that right? Thanks.

---

### Post by vasa1 on 2012-06-02
> **MonkWy said:**
> I have a question about an App called Psensor. what does it do and is it okay/safe to use with 12.04 LTS? I have read that Canonical doesn't support it, that it is supported by the community. Is that right? Thanks.
Bit late but ...
I've been using it for about a month. No complaints. The bit about Canonical not supporting it is a standard disclaimer and not a reflection on the software. That it is in the Software Center implies, to me, that it has undergone some extent of vetting.

---

### Post by Senior_Buckethead on 2012-06-04
Yeah lots of applications in software center Canonical don't support, that doesn't in itself make the software bad.
Ive installed Psensor as a test and looks innocuous to me.

Follow the instructions on the home page:
[http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/) 

It even has a ppa for 12.04
[https://launchpad.net/~jfi/+archive/ppa]("https://launchpad.net/%7Ejfi/+archive/ppa")

All you have to do to install it is:
```

[SIZE=2]sudo apt-add-repository ppa:jfi/ppa
sudo apt-get update
sudo apt-get install psensor
[/SIZE]
```[SIZE=2]

Take care.
[/SIZE]

---

### Post by MonkWy on 2012-06-14
Thanks I will look into that, sorry I haven't been on in awhile... Work and the like keeps me busy. I just solved (hopefully) my problems I have with my Windows computer. However, am thinking I am gonna wipe the HDD and put on Kubuntu 12.04 LTS. Will have 2 comps running a couple flavors of Ubuntu then. So far I love using Ubuntu. Is great. I do have a question, the comp I have I want to run Kubuntu on is an ASUS CM1630. How can I post the specs: mobo, ram cpu, hdd, video and sound card... chipset... all the info you guys need to say either YES or NO your system will/will not run Ubuntu. I want to make sure everything is copmatible. I was told to run Kubuntu from a live CD and open and use a varriety of programs and apps to see if get any errors or crashes. I was then told if I don't have any problems I could do a dual boot. Or should I go straight to erasing the hdd and do a clean install of Kubuntu? Thanks for the help and future replies.

---

### Post by afixane on 2012-06-15
> **MonkWy said:**
> Thanks I will look into that, sorry I haven't been on in awhile... Work and the like keeps me busy. I just solved (hopefully) my problems I have with my Windows computer. However, am thinking I am gonna wipe the HDD and put on Kubuntu 12.04 LTS. Will have 2 comps running a couple flavors of Ubuntu then. So far I love using Ubuntu. Is great. I do have a question, the comp I have I want to run Kubuntu on is an ASUS CM1630. How can I post the specs: mobo, ram cpu, hdd, video and sound card... chipset... all the info you guys need to say either YES or NO your system will/will not run Ubuntu. I want to make sure everything is copmatible. I was told to run Kubuntu from a live CD and open and use a varriety of programs and apps to see if get any errors or crashes. I was then told if I don't have any problems I could do a dual boot. Or should I go straight to erasing the hdd and do a clean install of Kubuntu? Thanks for the help and future replies.

Keep the Windows installation. The window's CHKDSK is very useful for repairing NTFS partition :p

---

### Post by alienus99 on 2012-06-30
amd athlon dual core 64 working in 32 bit mode
ubuntu 11.10
can anyone explain why my psensor displays obviously excessive lines


                                                       (current  ,   min ,   max)          
core0 temp  48 , 45  ,50                     
core0 temp( ? once more )       55      ,       54   ,    58

core1 temp                                    49      ,     47    ,  50
core1 temp ( ?  )                             50      ,     48     ,  53

thanks

---

### Post by jmfal on 2012-06-30
Welcome to Ubuntu

run this in a terminal

```
  sudo sensors-detect    
```

And answer yes  (press y, press enter) to all questions.

I'm not sure if you need to resstart and to view sensors :

```
 sensors    
```

---

### Post by alienus99 on 2012-06-30
I have run   ```
sensor-detect
```and and answered 'yes'to all questions except this  
```
Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
```no, I replied here and only here and then the program continued untill successful ending

then I restarted my pc and alas the problem persist 
command 
```
sensors 
```and response 
```

     <...>
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +47.0°C  
Core0 Temp:   +54.0°C  
Core1 Temp:   +48.0°C  
Core1 Temp:   +50.0°C 
```what perplexes me is this doubling of items core0 and again core0 and with the core1 the same strange thing
 we would have expected   rather
```
Core0 Temp:   +47.0°C  
Core1 Temp:   +54.0°C
only 
```wouldnt we ?

thanks

---

### Post by jmfal on 2012-06-30
Read post #1:

[http://ubuntuforums.org/showthread.php?t=2780&page=41](http://ubuntuforums.org/showthread.php?t=2780&page=41)

---

### Post by vasa1 on 2012-06-30
@alienus99, you could also ask over here: [https://answers.launchpad.net/psensor](https://answers.launchpad.net/psensor)

---

### Post by jmfal on 2012-06-30
Im sorry I gave you the wrong link:

[http://askubuntu.com/questions/155811/psensors-dont-detect-all-sensors](http://askubuntu.com/questions/155811/psensors-dont-detect-all-sensors)

---

### Post by alienus99 on 2012-06-30
> **jmfal said:**
> Im sorry I gave you the wrong link:

[http://askubuntu.com/questions/155811/psensors-dont-detect-all-sensors](http://askubuntu.com/questions/155811/psensors-dont-detect-all-sensors)

no,content pointed by your previous link [http://ubuntuforums.org/showthread.php?t=2780&page=41](http://ubuntuforums.org/showthread.php?t=2780&page=41)
 is relevant & very instructive , thanks

---

### Post by jmfal on 2012-06-30
If that fixes your problem please mark YouR thread  {SOLVED} using the forum tools.(after you click reply it will be above the reply box).

Your Welcome...

---

### Post by MonkWy on 2012-07-04
Directed at afixane. So I should leave windows 7 on and do a dual boot system on my ASUS? Is that what you mean?

---

### Post by MonkWy on 2012-07-04
Thanks to everyone for the information. I am checking out the link about PSensors. will try it out and get back to u guys if have any issues. Thanks again. :cool:

---

### Post by jeanfi on 2012-07-06
> I have a question about an App called Psensor. what does it doWhat does it do:
It is a UI for monitoring temperatures and fans speed offering temperature alerts and desktop integration. A better way to understand what is offered is to take a look at this screenshot:
[http://wpitchoune.net/psensor/screenshots/psensor-2011-06-16.png](http://wpitchoune.net/psensor/screenshots/psensor-2011-06-16.png)

You can see:
 - a graph of the temperatures/fan speeds
 - the higher temperature in the psensor launcher icon
 - an application indicator to view quickly the temperatures

Alerts are raised using the usual bubble notifications and application indicator of Unity.

> and is it okay/safe to use with 12.04 LTS?If okay/safe means that it is not a malware/virus/trojan... Using Sofware Centre (with default distribution repositories) is a good way to avoid installing 'bad' software, the Ubuntu community will surely report these kind of softwares quicky and request to remove them. 

If okay/safe means that it will not damage your computer... well, like any software there is a risk. Psensor only *reads* sensors and uses wellknown , widely used and tested libraries (main one is lm-sensors). Psensor does not modify the speed of fans or any other kind of hardware settings. So the risk that Psensor damage your computer is very low and I have never received such report.

> I have read that Canonical  doesn't support it, that it is supported by the community. Is that  right? Thanks.As already said in a previous response, that's a standard disclamer meaning that Canonical does not participate to the development and support of the project. Most of the softwares available in Ubuntu distribution are in this case except core softwares like for example Unity.

---

### Post by vasa1 on 2012-07-06
@jeanfi,
Please could you explain how you get %CPU usage?
Also, there's no axis/scale for %CPU usage, just for temp.

---

### Post by jeanfi on 2012-07-06
> **vasa1 said:**
> Please could you explain how you get %CPU usage?
[http://ubuntuforums.org/showthread.php?t=2002705](http://ubuntuforums.org/showthread.php?t=2002705)

> Also, there's no axis/scale for %CPU usage, just for temp.
Right, axis scale only for fan speeds and temperature. It allows to quickly know whether the cpu usage is high.

---

