---
title: "How to fully secure and harden a Ubuntu 20.04 laptop?"
date: 2021-12-07
forum: New to Ubuntu
---

### Post by bhubunt on 2021-12-07
Hi,
I am trying to secure my Ubuntu 20.04 laptop to make sure it does not connect to the internet, either by accident or through an attack. (I use another computer for research on the internet).

So far I have done the following:
-I have disabled ethernet, wifi, Bluetooth in the bios and only have the USB port enabled for my USB sticks
-I have activated the uncomplicated firewall using the command sudo ufw enable 
-I thought it might be a good idea to generate logs, using sudo ufw logging on
-I don't want any ports to be open and wonder if I need to execute any particular commands to ensure no port can be accessed?
-I encrypted the hard drive when I installed Ubuntu 20.04
-What kind of passwords do I definitely need to set up?
-Is there anything else I need to adjust in the bios?

Thanks for the tips.

---

### Post by TheFu on 2021-12-07
Don't want to connect to the internet?
a) Don't plug in any ethernet cable.
b) Disable wifi in the BIOS.
c) Disable bluetooth in the BIOS.
d) Don't connect any USB devices of any sort, since they *might* have extra network features.

Enabling ufw only enables the default rules ... which is typically "deny incoming".  It does nothing for outbound traffic.

**netstat -tun** will show ports.  There are other commands - like **ss**.  Don't worry about 127.x.x.x/8 ports/listeners. That's just the lo device and Unix systems use it to talk to themselves.

Stay patched.
Have daily, automatic, versioned, backups - that are "taken when off-line.

But this doesn't guarantee security.  Someone with physical access and 5 seconds could change many of those settings.

There is no absolutes when it comes to computer security.  It is about risk mitigation based on the attack surface.  A 16 yr old trying to protect his laptop from a 7 yr old little brother has a vastly different attack surface than someone helping an organization with billions of USD on the line ... or lives on the line.  The probable attackers matter.

You didn't mention 2FA for the encrypted HDD. Do you take security serious?

---

### Post by grahammechanical on 2021-12-07
Have you set a password for the UEFI/BIOS settings utility? How easy is it to reset the machine back the manufacturer's hardware defaults? Open the case; remove a lithium coin battery; wait a few minutes and replace the coin battery? Is it that easy? Are you going to glue the case parts together?

Regards

---

### Post by psychohermit on 2021-12-08
```
 sudo ufw default deny outgoing 
```  then restart the firewall  ```
 sudo ufw disable && sudo ufw enable 
```

---

### Post by Impavidus on 2021-12-08
Only slightly joking, but does your laptop have microphone and speakers? Those could be set up to create a com link to a different device, even from inside a Faraday cage, with a range of several meters and completely bypassing all bluetooth security or firewalls.

---

### Post by TheFu on 2021-12-08
> **Impavidus said:**
> Only slightly joking, but does your laptop have microphone and speakers? Those could be set up to create a com link to a different device, even from inside a Faraday cage, with a range of several meters and completely bypassing all bluetooth security or firewalls.

That's true.  Remember reading about a printer being forced to make specific noises so a fax machine in the same room could dial out reproducing the saved pages at a remote spying location. Both the printer and fax were hacked.  

There have been proof of concept demonstrations of wired keyboards and mice events (keypresses) being captured 50m away from the keyboard.  With wireless versions, the range is much farther. [https://www.theatlantic.com/technology/archive/2016/07/hackers-can-spy-on-wireless-keyboards-from-hundreds-of-feet-away/492962/](https://www.theatlantic.com/technology/archive/2016/07/hackers-can-spy-on-wireless-keyboards-from-hundreds-of-feet-away/492962/)  Some POC demonstrations were with smartphones "listening" to the typing.  After a short time of listening, heuristics can be applied to figure out the sound of each key.

Be careful using USB: [https://www.reuters.com/article/us-cybersecurity-usb-attack/hackers-can-tap-usb-devices-in-new-attacks-researcher-warns-idUKKBN0G00K420140731](https://www.reuters.com/article/us-cybersecurity-usb-attack/hackers-can-tap-usb-devices-in-new-attacks-researcher-warns-idUKKBN0G00K420140731)  This has been a known issue for years. USB devices can contain their own driver and self-install that driver with root privileges and no user knowledge.

But we're off in super-secret-squirrel-spy land now.

---

### Post by bhubunt on 2021-12-08
> **TheFu said:**
> 
1 -Don't connect any USB devices of any sort, since they *might* have extra network features.


2 - Stay patched.
Have daily, automatic, versioned, backups - that are "taken when off-line.

3 - But this doesn't guarantee security.  Someone with physical access and 5 seconds could change many of those settings.

4 - You didn't mention 2FA for the encrypted HDD. Do you take security serious?


Thanks so much for these great comments. I have numbered the points I'll reply to, with more questions. The computer, just to clarify, is always off-line.

1 - I had a feeling that USBs might be a problem as I read somewhere that they could also function as antenna's? So I won't be using USBs anymore but then how do I save my LibreOffice docs? They're on the hard drive but I'd like to have separate backups on another device, as well. How to do this since I do not want to go online? Would an external hard drive not offer a similar security risk?

2- Pardon my newbie status, but I am not sure what staying patched means and how I would activate those backups off-line. 

3- I carry my lightweight computer in my backpack and never leave it at home or out of sight.

4- How do I install 2FA on a computer that is always offline?

Regards

---

### Post by bhubunt on 2021-12-08
> **grahammechanical said:**
> Have you set a password for the UEFI/BIOS settings utility? How easy is it to reset the machine back the manufacturer's hardware defaults? Open the case; remove a lithium coin battery; wait a few minutes and replace the coin battery? Is it that easy? Are you going to glue the case parts together?

Regards

Thanks so very much for the reply. Yes, I have set a password for a UEFI/BIOS settings utility. I always carry the laptop with me, never leave it out of sight, but thanks for letting me know about the battery replacement loophole...

Regards

---

### Post by bhubunt on 2021-12-08
> **psychohermit said:**
> ```
 sudo ufw default deny outgoing 
```  then restart the firewall  ```
 sudo ufw disable && sudo ufw enable 
```

Super!  I will definitely block all outgoing traffic as well. Thanks so much.

---

### Post by bhubunt on 2021-12-08
> **Impavidus said:**
> Only slightly joking, but does your laptop have microphone and speakers? Those could be set up to create a com link to a different device, even from inside a Faraday cage, with a range of several meters and completely bypassing all bluetooth security or firewalls.

Yes, the laptop has microphone and speakers. Are you suggesting it's best to have those removed if you want a totally secure off-line laptop? 

Thanks so much for the reply.

---

### Post by bhubunt on 2021-12-08
> **TheFu said:**
> 

Be careful using USB: [https://www.reuters.com/article/us-cybersecurity-usb-attack/hackers-can-tap-usb-devices-in-new-attacks-researcher-warns-idUKKBN0G00K420140731](https://www.reuters.com/article/us-cybersecurity-usb-attack/hackers-can-tap-usb-devices-in-new-attacks-researcher-warns-idUKKBN0G00K420140731)  This has been a known issue for years. USB devices can contain their own driver and self-install that driver with root privileges and no user knowledge.



Hi TheFu, Thanks for this extremely helpful article about how hackers can put code on your USB stick, which you then infect your laptop with. The article says the firmware can be infected? Here's my follow-up question: can you then subsequently get rid of the malicious code by reinstalling Ubuntu? 

Another related problem: I am using a USB stick to (re)install Ubuntu, so what else should I use, if I don't want to go online? Are you suggesting one should not install Ubuntu using a stick?

And another question about potentially infected USB sticks:
suppose there's malicious code on a USB stick yet the stick also contains docs that I really need. If I copy the docs one by one on another stick using a computer that is not mine, do I then avoid transfering the code to the new stick or is the whole thing hopeless to begin with? Sorry if this sounds like an uniformed question. I am still learning...

And if there is malicious code on a stick, can you detect it by running the stick through a very basic mal-ware program or would you need something more sophisticated? And can windows computers that have, say McAfee, detect such code on a stick even if the code might be intended for a Ubuntu laptop?

---

### Post by TheFu on 2021-12-08
> **bhubunt said:**
> Yes, the laptop has microphone and speakers. Are you suggesting it's best to have those removed if you want a totally secure off-line laptop? 

Thanks so much for the reply.

I think you are missing the point.  There isn't any things that is "totally secure".   There are just ways to make a system less hack-able, up to a point.  The amount of effort involved depends completely on the attackers.  It doesn't make sense to spend effort and lose convenience if the attacker is a 10 yr old.

If the attacker is a govt with unlimited resources, don't use Ubuntu. Don't use i86-64 or amd64. Use an odd OS with odd hardware.  For most things that really need to be secure and off line, a computer from 2008 that never became popular would be more secure - provided it is 100% offline and portable.

You have to leave a computer alone at some point.  Shower?  Sleep?

If you are worried about being killed due to the content on the computer, then that's where you need to engage someone professional for all the tiny things.  Us posting here leaves out all the detailed stuff you need to do.  ***_How_*** you do something is often more important than checking the box and enabling that security feature.  HDD encryption with a password of 123456 isn't very secure.  Neither is using your first and last name with L33T characters.  Some 2FA is required.  There are lots of hardware tokens that work offline.  I know that yubikey supports challenge-response  passphrases. I use that.

Have you seen the movie Citizenfour?  Do you know WHY he only used a computer hidden under the bed covers? There are multiple reasons.  There are books written on this and reading about 5 of those will help much more than us throwing out 2 paragraph answers.  The WHY and the HOW matter.

---

### Post by bhubunt on 2021-12-08
> **TheFu said:**
> 

Have you seen the movie Citizenfour? 

Hi TheFu, yes, I saw the movie when it came out.  I am trying to learn basic technical security steps and all of the answers I have received so far have been very helpful.

---

### Post by TheFu on 2021-12-08
> **bhubunt said:**
> Hi TheFu, yes, I saw the movie when it came out.  I am trying to learn basic technical security steps and all of the answers I have received so far have been very helpful.

I fear you are trying to jump to the end of the book, without reading the introduction and basics first.
Are you good at networking?
Are you good at C programming?  Almost all computer OSes today are based on C.
Do you understand that bugs exist and there are probably 50K bugs in every non-trivial OS out there?
No matter how much any document says, or claims, there are bugs and they can be from nuisance to critical levels. 

You haven't said who the attacker is.  Who is it?

---

### Post by Impavidus on 2021-12-09
> **bhubunt said:**
> Yes, the laptop has microphone and speakers. Are you suggesting it's best to have those removed if you want a totally secure off-line laptop? 

Thanks so much for the reply.

There's a reason why I wrote "slightly joking". Theoretically, an attacker can keep a link to your computer alive via the microphone and the speakers once there's some malware on your computer that supports communication via that channel. Some proof-of-concept malware for that has been written. So if you want absolute security, you have to close off that channel. But I'm not aware of any real attacks that worked like that.

The point is, you have to find a balance between security and convenience. Absolute security will make your computer unusable. You can put your computer in a sound-proofed safe, where only you have physical access, working as a Faraday cage, with no networking or even power cable going in (power it using a dumb car battery), but that will be unusable.

So think about it. Who might want to attack you? Someone with vast resources, like the US/Chinese/Russian government, or the boy next door? Is this attacker targeting you specifically, or is he just looking for any random person with a poorly secured computer? In the latter case, if you make sure your computer is better secured than that of most people, the attacker will give up and look for easier targets.

---

### Post by bhubunt on 2021-12-09
> **TheFu said:**
> 
Are you good at networking?
Are you good at C programming?  Almost all computer OSes today are based on C.


No, I am a newbie, have no knowledge of coding or programming but am trying to learn how to best protect my Ubuntu laptop. It's my hope to learn coding at a later point. But I definitely appreciate all the tips I have received so far.

---

### Post by bhubunt on 2021-12-09
> **Impavidus said:**
> There's a reason why I wrote "slightly joking".

Got it. It was more of a theoretical question on my part as I don't plan to have the speakers and such removed. I'm actually looking for more hands-on technical tips and command lines, like the ones I got at the beginning of this thread. 

As I indicated, some of the manuals on Ubuntu I have tried to read are a bit too technical for my level, which is why I appreciate the tailored answers you guys provide on this platform pitched at my level and that of other newbies reading this thread...

---

### Post by T6&amp;sfpER35% on 2021-12-09
> How to fully secure and harden a Ubuntu 20.04 laptop? or any pc...
unplug at the mains and leave it at that 
:lolflag:

---

### Post by bhubunt on 2021-12-09
> **3nd said:**
> or any laptop ...
unplug at the mains and leave it at that 


I know this is supposed to be a joke but, unless I am mistaken, unplugging a computer to secure it is not enough, as it can still be activated remotely if the battery is still operative. 

A good laptop to have is one from which you can remove the battery. 

This based on my reading...

---

### Post by TheFu on 2021-12-13
> **bhubunt said:**
> No, I am a newbie, have no knowledge of coding or programming but am trying to learn how to best protect my Ubuntu laptop. It's my hope to learn coding at a later point. But I definitely appreciate all the tips I have received so far.

For almost all normal people, running Ubuntu, staying patched, not being stupid online and having automatic, periodic (daily/weekly), off-line backups is sufficient security.  It is extremely unlikely you'd ever hacked doing those things.

Now, because it is a laptop, there are other risks. Every time it connects to a foreign wifi network, that's a risk.
Every USB device (mouse, keyboard, storage, penlight, whatever) is connected, there is a chance of having "bad stuff" placed/installed on the system.
For example, I was running an InstallFest at a local University - it was the first one and about 20 people came.  I'd brought a USB flash drive with 5-10 different, popular, flavors of Linux and we passed that flash drive around the huge conference table so everyone could copy the .ISO files they wanted to their system.  About 15 people used the flash drive ... and when I got it back, it had 3 viruses on it.  My flash drive had never been connected to Windows - ever.  That's the risk of a student environment. Passing things around is just like COVID and can lead to becoming infected.

Don't connect USB stuff that you don't know where it came from or who could have altered it. There is always a risk, so we can only mitigate the risks by ... not sharing USB devices with random people. Knowing how security conscious the other person actually is. And we getting a new flash drive, I prefer going to a real store where they sell real hardware and randomly pulling the flash device from the stock myself. That makes it nearly impossible for someone trying to use USB storage as an attack vector from gaining access. Too many random aspects for them to know my plans and plant modified storage.

AV software is only 50% effective. It can never replace a smart user.  As said before, there isn't a checkbox. There is a security process and the attacker matters for what is actually needed for defense.  There are lots and lots of different attacks on computers and against Linux. There are common things routinely done which address 99% of those, so we don't really need to worry too much, unless our computer is actually a target by a specific attacker. Then it becomes about specifics of everything involved in your use of technology.  Brand and model of smart phone, OS being run, which router and router software, wifi, bluetooth uses. Do you live alone? Does **anyone** else have access to the location that they can modify the router or other network equipment?  Is there a maid?  Look up "evil maid attack".

Being completely paranoid isn't effective use of our time. Knowing and properly assessing the risks is useful. That takes years of experience and understanding what happens below the GUI. How networks really work, how routing works. How poor security is for all RF connectivity compared to wired security. (about 100-10000x worse).

There is an entire attack method around CPU and RAM issues that has only been know the last 5-10 yrs.  "Row hammer" and the AMD/Intel CPU bugs. These take a more sophisticated attacker ... not your 8 yr old.  Honestly, I don't worry about any of these attack methods. They seem to be less about accessing information than corrupting data.

There's always something to know and learn. I can promise that will be the situation 50 years from now too.

For basic security, there are sticky threads at the top of the Ubuntu Security sub-formum. Read those. Start there.

---

### Post by nginmu on 2021-12-14
Is this a good time to mention the Intel Management Engine?

---

### Post by bhubunt on 2021-12-19
> **nginmu said:**
> Is this a good time to mention the Intel Management Engine?

Interesting comment.

Can you elaborate?

---

