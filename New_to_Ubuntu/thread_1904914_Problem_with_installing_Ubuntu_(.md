---
title: "Problem with installing Ubuntu :("
date: 2012-01-05
forum: New to Ubuntu
---

### Post by Agusia on 2012-01-05
Hi all. :)

I've got a problem with installing Ubuntu 11.10. I've done everything as it is said in the tutorial on official page, but when I want to boot it, it doesn't boot, instead the light on the pendrive is blinking for the whole time. I've got Acer Aspire One 772 netbook.

Can anyone help me? :(

---

### Post by psychotix on 2012-01-05
Did you set up your laptop BIOS to boot from USB?  Try going into the BIOS on startup.  You usually have to press a "F" key like F2 to do so.

---

### Post by KdotJ on 2012-01-05
I'm assuming you've made a bootable USB stick and want to install Ubuntu from the USB onto your netbook?

Two questions to start:

1) How long are you waiting while the USB pendrive is flshing?

2) Have you checked your netbook BIOS to see that booting from USB is top priority?

---

### Post by Agusia on 2012-01-05
Yes, I've set up to boot from the USB, I press F12, and then choose USB and then the screen goes black, there is a blinking line, like i wanted to write some text and the pendrive is blinking.

I've been waiting for some minutes one time and nothing happened.

---

### Post by KdotJ on 2012-01-05
OK, so the netbook's built in startup screen shows then it goes black? You should only need to setup to boot from USB just once then restart with the USB stick left plugged in.

How did you create the USB?

---

### Post by Agusia on 2012-01-05
I turn on my computer, then shows the Acer logo, and down of the screen there is written something like: "Press F2 for BIOS, press F12 to choose booting device. I press F12, choose USB, and then it's like I said before.

To create USB I've used "Universal-USB-Installer-1.8.7.5".

---

### Post by KdotJ on 2012-01-05
Hmmm, difficult one really. Sometimes it can take a few minutes for it to do anything. The USB stick is flashing you say, which shows that it is at least doing something. My suggestion from here (although not great) is to try again and leave it for a few more minutes are see if anything happens. After that, maybe create the USB stick again just in case something went wrong last time.

Hopefully someone has better idea on what to do..

---

### Post by Agusia on 2012-01-05
Ok, thanks for the help. :) I will try again and leave it untill something will happen. Maybe there is something wrong with the pendrive, does it have to be some special one or something?

---

### Post by KdotJ on 2012-01-05
No not a special one, just a normal pendrive. The only thing is that it has to be big enough to have the Ubuntu iso on it (So anything over 800mb really). I am assuming yours is big enough or the USB installer program would have gave you an error.

Another program that can create USB installers is UNetbootin (link [here]("http://unetbootin.sourceforge.net/")), the download links are at the top. This is a similar program to what you used, but perhaps something went wrong while it was creating the USB... :/

---

### Post by Agusia on 2012-01-05
I've got Lexar JD FireFly 4GB. I will try that other program. ;)

Update: I've used that other program and even upadted BIOS but still the same. :(

---

### Post by KdotJ on 2012-01-05
Odd... well I'm stumped to be honest. The last thing I can suggest is to download the Ubuntu ISO again and have another stab... other than that I'm not sure why it won't work.

Hopefully installation guru will be able to shed light on the situation.

---

### Post by Agusia on 2012-01-06
I have installed Windows 7 from pendrive and I didn't have any problems. :(

Update: I have tried it on the other computer and it's still the same. Maybe there is something wrong with the pendrive. :(

---

### Post by Agusia on 2012-01-19
I've bought a new pendrive and it boots without any problems, but when I want to install Ubuntu I've got an error: ubi partman error 141. Can somebody help me?? :(

---

### Post by sandyd on 2012-01-19
> **Agusia said:**
> I've bought a new pendrive and it boots without any problems, but when I want to install Ubuntu I've got an error: ubi partman error 141. Can somebody help me?? :(
After crash, upload /var/log/syslog .
Theirs a multitude of issues related with errror 141.

---

### Post by Agusia on 2012-01-20
I can't find this on my pendrive. :(

---

### Post by mastablasta on 2012-01-20
How are you trying to install it? Side by side or overwrite windows?
Where/when exactly does the error pop up?
 
you can boot normally in to Ubuntu desktop?! if so does everyhting work normally in live session?

---

### Post by Agusia on 2012-01-20
I have somehow installed Ubuntu but now I have another problem. Videos in HD don't play smooth. I've installed additional drivers, but now I have a sign" AMD Unsupported hardware. :(
I have found more problems. When I press buttons to sleep computer, it doesn't get up and when I open .txt files it doesn't show some special letters like euro sign or trademark sign. Does anyone know how to solve this?

---

