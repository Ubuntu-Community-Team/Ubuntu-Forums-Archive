---
title: "Desktop Effects Could Not Be Enabled"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by ruthy_gg on 2008-06-02
Hi,i Installed Ubuntu 8.04 
I Have An Ati Radeon R100 Graphic Card
I Am Totally New To Ubuntu. 
I Want To Enable The Cool Effects By Pressing System >> Preferences >> Appearance >> Visual Effects  "normal" 
However The Following Message Appears : "desktop Effects Could Not Be Enabled"
I Tried Something Before By Changing Something In The Compiz File.it Allowed Me To Press The "normal" Option But The Desktop Got Crazy... It Damaged Things. I Had To Install Ubuntu Again.
If Somebody Can Help Me Get This Right I Will Be Very Thankful.

---

### Post by SunnyRabbiera on 2008-06-02
Fair warning:
ATI is a pain in the @#$%^ in linux, as ATI does not provide us with good drivers.
did you try the restricted drivers application or envy?

---

### Post by spiderbatdad on 2008-06-02
If your screen display gets crazy again after experimenting, try this command in a terminal or from recovery mode to fix your display without re-installing```
sudo dpkg-reconfigure -phigh xserver-xorg
```If you boot into recovery to use the command, you can leave out 'sudo.'

Not sure how to help you with compiz on that card. Maybe try installing xserver-xgl via synaptic. Reboot, then try to enable 'custom' under the visuals tab. If it doesnt work, run the above command, and remove the package, xserver-xgl.

---

### Post by ruthy_gg on 2008-06-03
> **SunnyRabbiera said:**
> Fair warning:
ATI is a pain in the @#$%^ in linux, as ATI does not provide us with good drivers.
did you try the restricted drivers application or envy?

Hi thanks FOR YOUR ANSWER.I WENT TO SYSTEM >> HARDWARE DRIVERS  and typed my password. THERE IS NOT PROPRIETARY DRIVERS IN USE. 
WHAT DO YOU MEAN BY ENVY?

---

### Post by ruthy_gg on 2008-06-03
> **spiderbatdad said:**
> if Your Screen Display Gets Crazy Again After Experimenting, Try This Command In A Terminal Or From Recovery Mode To Fix Your Display Without Re-installing```
sudo Dpkg-reconfigure -phigh Xserver-xorg
```if You Boot Into Recovery To Use The Command, You Can Leave Out 'sudo.'

Not Sure How To Help You With Compiz On That Card. Maybe Try Installing Xserver-xgl Via Synaptic. Reboot, Then Try To Enable 'custom' Under The Visuals Tab. If It Doesnt Work, Run The Above Command, And Remove The Package, Xserver-xgl.

How Do I Install It? 
Can You Provide The Steps?
Alli Want For Now Is To Activate The Cool Effects.i Want It To Allow Me To Press "normal" In Visual Effects And That The Effects Can Be Enabled.-....

---

### Post by spiderbatdad on 2008-06-03
System>>Administration>>Synaptic Package Manager.

You can use the search tool for: xserver-xgl or for envy.
Also try google for envy 8.04 if you want to try envy. Try only one method at a time.

---

### Post by Xiong Chiamiov on 2008-06-03
> **ruthy_gg said:**
> How Do I Install It? 
Can You Provide The Steps?
Alli Want For Now Is To Activate The Cool Effects.i Want It To Allow Me To Press "normal" In Visual Effects And That The Effects Can Be Enabled.-....
[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by oedha on 2008-06-03
have you try to install xorg-driver-fglrx ?
open terminal and type :==> sudo apt-get install xorg-driver-fglrx
or 
go to [http://ati.amd.com](http://ati.amd.com) to get the latest driver

---

### Post by overdrank on 2008-06-03
HI and please correct me if I am mistaken but the Ati Radeon R100 Graphic Card is the same as the 7000 and 7500. Maybe look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

